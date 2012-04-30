# Proposed Addenda


### Symbols vs Strings:

* Identifiers should generally be strings


* Symbols should not escape from ruby land. A YAML file, for example, should express keys as strings, even when they are symbols in ruby land

## super, star-args (aka splat args), and delegation

From avdi grimm: 

> If we need to intercept an ActiveRecord-provided method, we can just intercept it. There are some exceptions, like after_find, which let us hook into Rails machinery that might otherwise be difficult to override. But for simple cases, we can do the simple thing and override the method we want to change. Following a few rules will keep us from inadvertently breaking things in the process:
> 
> Unless you care about the value of arguments, use a single * as the method parameters so that the override doesn't interfere with the original method's protocol.
> Always call super, unless you are intentionally canceling the default behavior.
> Always call super without parentheses, unless you want to explicitly change the arguments going to the parent method. Leaving out the parentheses tells Ruby to re-use the arguments which were passed into the current method.
> Remember to return the result of =super=, by either making super the last call in the method, writing return super, or saving the return value in a local variable and then returning the local at the end. If you need to do some processing after the call to super, but you don't want to save the return value in a local, you can use #tap:
>
>     def foo(*)
>       super.tap do
>         # ... after-super processing
>       end
>     end

