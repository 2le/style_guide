# README-README: A Style Guide for README files

## Contents

The `README.md` file and supporting documents should describe the following, in this order. If the file starts getting long, break it into pieces

* **Project Titles** as a level-1 heading
  - with descriptive tagline: I should be informed and intrigued. Examples:
    - "Sinatra is a DSL for quickly creating web applications in Ruby with minimal
effort"
    - "Rails is a web-application framework that includes everything needed to create
database-backed web applications according to the Model-View-Controller (MVC) pattern."
    - "Resque (pronounced like "rescue") is a Redis-backed library for creating
background jobs, placing those jobs on multiple queues, and processing
them later."

* **Overview**
  - what it does
  - why you might want to use it, and why you might not

* **Example Usage**: a basic example. Nothing fancy -- put rich examples in the detailed usage section

* **Getting Started**
  - installation & prerequisites 
  - how to run examples and tests
  - location of:
    - code
    - issue tracker
    - wiki
    - blog posts, screencasts, etc
    - compiled documentation (add the project to [rdoc.info](http://rdoc.info))
    - travis-ci results
    - mailing list
  
* **Design Goals**
  - lightweight or full-featured? 
  - performance, flexibility, expressiveness?

* **Detailed Usage**
  - models and interface
  - examples  
  - configuration 
  - middleware or plugins
  - how it works

* **Comparable Tools**

* **Developer info**
  - Important Components 
  - layout of internal code tree
  - Limitations and known issues
  - performance and benchmarking

* **Colophon**
  - References
  - How to contribute
  - Credits
  - Copyright

## Supporting Documentation

Include the following in your project:

* `README.md`    -- external description and documentation, as defined above.
  - This is the only support document in the code root. The rest go in the wiki (`notes/` folder). Don't make 'README-[subcomponent].md`, or `path/to/[subcomponent]/README.md`.
* `LICENSE.md`   -- we usually use the Apache 2.0 license. If the project is internal, it should state 'all rights reserved'.
* `CHANGELOG.md` -- update with changes before pushing a new version
* `TODO.md`      -- known issues and nitpicks.

* `notes/`       -- a `git submodule`d version of the project's wiki. If sections outlined above start to become lengthy, separate them into files named as follows:
  - `notes/INSTALL.md`
  - `notes/design_goals.md`
  - `notes/examples.md`
  - `notes/configuration.md`
  - `notes/code_components.md`
  - `notes/code_layout.md`
  - `notes/known_issues.md`
  - `notes/performance.md`
  - `notes/references.md`

## Formatting

* Call the file `README.md`.
* Write in markdown format. 
  - you may use triple backtick blocks for code, with the language prefixed.
  
        ```ruby
        def hello(str)
          puts "hello #{str}!"
        end
        ```
        
* Do not wrap lines.         