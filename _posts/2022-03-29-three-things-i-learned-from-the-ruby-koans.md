---
layout: post
title: Three things I learned from The Ruby Koans
---

Here are (at least) three things I learned from [The Ruby Koans](http://rubykoans.com/):


 **Single Quotes vs. Double Quotes vs. String-Literals**
 
 Single Quotes vs. Double Quotes vs. Alternate String Syntax:
 
 Single-quoted and double-quoted String objects in ruby have two key differences.
 1. Double-quoted String objects support string interpolation
 2. Double-quoted String objects support the full range of escape sequences
 
String Interpolation Example:
```ruby
irb(main):001:0> day = 'Sunday'
=> "Sunday"
irb(main):002:0> "Today is #{day}"
=> "Today is Sunday"
irb(main):003:0> 'Today is #{day}'
=> "Today is \#{day}"
```
With double-quoted strings, ruby objects are evaluated and returned directly into the string. Single quotes return the literal interpretation of the string with the esacped # symbol

Escaping Characters Example
```ruby
irb(main):007:0> puts 'Hello, \nWorld!'
Hello, \nWorld!
=> nil
irb(main):008:0> puts "Hello, \nWorld!"
Hello,
World!
=> nil
```
Single-quoted String objects don't support any escape charactoers except backslashes and single-quotes.

Alternate String Syntax
In the case where a string has quotes and/or interpolation, the "%Q{...}" format can be used for strings
```ruby
irb(main):009:0> "Ruby will throw an "error" if double quotes are used in a string"
(irb):9: syntax error, unexpected local variable or method, expecting end-of-input (SyntaxError)...
irb(main):010:0> %{Ruby will Ruby will NOT throw an "error" if double quotes are used in a string}
=> "Ruby will Ruby will NOT throw an \"error\" if double quotes are used in a string"
irb(main):011:0> %Q{Can also use to interpolate like double-quotes. "Today is #{day}"}
=> "Can also use to interpolate like double-quotes. \"Today is Sunday\""
```
**Symbols vs. Strings**
Symbols are immutable and always refer to the same object_id and the same place in memory. symbols are more effecient than strings if a string is constantly recreated in a program. (https://medium.com/@lcriswell/ruby-symbols-vs-strings-248842529fd9). 

**Calling Methods**
https://www.notonlycode.org/12-ways-to-call-a-method-in-ruby/

** send vs __send__ **
 https://stackoverflow.com/questions/4658269/ruby-send-vs-send