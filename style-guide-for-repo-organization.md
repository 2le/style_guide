Your project should include the following:

## Documentation

* `README.md`    -- external description and documentation, as defined above.
  - This is the only support document in the code root. The rest go in the wiki (`notes/` folder). Don't make 'README-[subcomponent].md`, or `path/to/[subcomponent]/README.md`.
* `LICENSE.md`   -- we usually use the Apache 2.0 license. If the project is internal, it should state 'all rights reserved'.
* `CHANGELOG.md` -- update with changes before pushing a new version
* `TODO.md`      -- known issues and nitpicks.
* `notes/`       -- a `git submodule`d version of the project's wiki

* `examples/`
* `data/`
* `Guardfile`, `Procfile`


### Submodule the wiki into the `notes/` directory

The `notes/` a `git submodule`d version of the project's wiki. If the sections outlined in the [README README](https://github.com/infochimps-labs/style_guide/blob/master/style-guide-for-readme-files.md) become lengthy, separate them into files named as follows:
  - `notes/INSTALL.md`
  - `notes/design-goals.md`
  - `notes/examples.md`
  - `notes/configuration.md`
  - `notes/code-components.md`
  - `notes/code-layout.md`
  - `notes/known-issues.md`
  - `notes/performance.md`
  - `notes/references.md`




## Automation

### `Rakefile` for simple scripts

* ?? where to put rakefile includes?? ??how to name them: .rake or .rb??

### `Guardfile` automates iterative development 

### `Procfile` shows how to launch support daemons and longrunning apps

Supply a procfile that will start

Include the following in the header block:

    # Procfile -- supporting daemons
    #
    # * Ensure you've done a `bundle install`
    # * run `foreman start [process name]`

List each daemon, with no path (if it's typically a system-wide dependency) or a path relative to the top of the repo. Here's an example [goliath](http://goliath.io) Procfile:

    listener:   ./app/listener.rb -sv -p 9000 -c $PWD/config/app.rb
    mongod:     mongod

### `Gemfile` is a manifest for ruby gem dependencies

Gemfiles for appllications *should* be precise about their *direct* dependencies. 
Gemfiles and gemspecs for libraries *should not* be strict with version dependencies. For example:

    gem 'gorillib',      "~> 0.1.8"
    group :development do
      gem 'yard',        ">= 0.7"
      gem 'pry'
    end

As written, any version of `pry` will work -- it's included in the Gemfile so that we debug with `binding.pry`, but there are no code dependencies in the library. The documentation uses some modern features of `yard`, so we ask for a version newer than 0.7; but if other libraries specify some future `"~> 1.0"` version we would rather break our docs than your app.

A library with a strict Gemfile leads to conflicts that are nearly impossible to work around in current versions of bundler. A library with a too-generous Gemfile might break on an upgrade of some dependency, but it's straightforward to correct by pinning a version in my app.

If the repo is a standalone-deployable application (web app, wukong job) you *should* include the Gemfile.lock file: it says "I don't care what's on the machine, use this precise gemset".
If the repo is not a standalone-deployable application (most things) you *should not* include the Gemfile.lock file. Add it to your `.gitignore`.

### Pesky config files: `.yardopts`, `.rspec`, `{reponame}.gemspec` (yes), `.rvmrc` (hell no)

* You *should* create and version thes following where appropriate:
  - the repos' gemspec (if any)
  - `.yardopts` and `.rspec` files

You *should not* version the following:
* `.rvmrc`: I shouldn't have to install a crazy ruby version to read through some source files.
* `TAGS`
* textmate `.project` files, emacs autosaves, or any other editor droppings.
* anything auto-generated: it leads to messy, redundant diffs and heavy repos:
  - `doc` (documentation from yarddoc or otherwise)
  - `pkg` (generated gems)
  - `build` (compiled products for java, c, etc)

## Tests and examples

### `specs` holds RSpec test scripts

* put test helpers in `specs/support/whatever_test_helper.rb`. The `spec_helper.rb` file *should* add `specs/support` to the load path, but it *should not* load the contents of that directory.
* put custom rspec matchers in `specs/support/matchers`. The `spec_helper.rb` *should* load the contents of that directory: `Dir['spec/support/matchers/*.rb'].each{|f| require f}`

* place files in parallel with `lib`:
  - the spec for `lib/gorillib/record.rb` goes in `spec/gorillib/record_spec.rb`.
  - the spec for `examples/simple.rb` goes in `spec/examples/simple_spec.rb`
* Don't make separate directories for 'integration' and 'unit' and other test-jargon soup. I don't care about your test methodology, I care about seeing the fully-expressed API of a library component. You should mostly be writing integration tests anyway.
* It's fine to make integration tests that don't correspond with a single library file: `spec/gorillib/structures_spec.rb` tests various combined uses of `record`, `bucket`, etc.
* If the tests for a library component are quite too large for one file, pause to consider whether you're over-testing, over-thinking, under-helpering, or if you should be splitting the library component. If your muse concurs that this is necessary, preserve core tests in a file named for the component  (`spec/whatever/foo_spec.rb`), along with files named with an underscore-delimited decoration: `spec/whatever/foo_in_space_spec.rb`, `spec/whatever/foo_underwater_spec.rb`).


### `examples/` holds example apps or scripts

Your best be is to include
* a stupidly-simple example: do the least interesting thing you can.
* an example that serves as a test rig: Give an example that is fairly prolix -- a good starting point for someone trying to understand the internals of the app. Doesn't have to be pretty.
* an example that does something no other library can: if someone isn't impressed by this example, they're just not into this repo.

You should write tests for the examples, though they're typically as simple as 'its ran successfully and its output was what I expected'.

### `data/` holds example data (keep it small and interesting)

Place data files in `data/` with helpful, descriptive names. Use something fun and domain-interesting. For structured data, use YAML if possible, JSON if necessary (YAML is more readable). Do not use any of the fancy features of YAML (anchors, references, baked-in types). For tabular data, use the TSV (tab-separated values) format. TSV files *must not* use any quoting or escaping; unless it's as simple as 'one line per record, split on tabs for fields' fall back to JSON.  If at all reasonable, run TSV files through wukong's `wulign` script -- it pads with spaces to make the data readable.

Don't put anything larger than a few dozen KB in the directory -- if a larger payload is necessary, make a `{reponame}-data` repo and submodule it into the data directory.

The subdirectory `data/expected_output` should
Have your examples output to `tmp/actual_output`; its contents should exactly mirror that of the expected output directory (letting me `diff -ruw data/expected_output tmp/actual_output` to detect differences). You should .gitignore the contents of the `actual_output` directory, but `.gitkeep` the presence of that directory.