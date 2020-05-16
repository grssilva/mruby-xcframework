# MRuby iOS, tvOS and macOs Catalyst xcframework

Based on [ruby2d/mruby-frameworks](https://github.com/ruby2d/mruby-frameworks)

Run `rake` to cross compile and build the frameworks. To update the MRuby submodule, use `rake mruby_latest` to set to the latest release and `rake mruby_master` to set the master branch.

The prebuilt xcframework are located in `xcframework/`.

How to generate:
1. run 'rake mruby_latest' on folder to update MRuby
2. run rake to generate the xcframework
3. in 'Build Settings' add '--deep' to 'Other Code Signing Flags'
4. on the project 'Signing & Capabilities', check 'Disable Library Validation' on 'Hardened Runtime'
5. add the xcframework to your xcode project

Easy way to test:
Create an Objective-C project
In the class you want to test, add the includes:
```
#include <mruby.h>
#include <mruby/compile.h>
```
Then, where you want the code to run (like the viewDidLoad):
```
mrb_state *mrb = mrb_open();
char code[] = "5.times { puts 'mruby is awesome!' }";

printf("Executing Ruby code with mruby:\n");
mrb_load_string(mrb, code);

mrb_close(mrb);
```
And you should see 'mruby is awesome!' 5 times in the Output window.
