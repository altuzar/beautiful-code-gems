# Beautiful Code

Here is some beautiful code taken from everywhere, not only Ruby but also other languages. 


# !!nil != !!0

Taken from Michael Hartl https://www.railstutorial.org/book/rails_flavored_ruby#sec-objects_and_message_passing

It’s worth noting that the nil object is special, in that it is the only Ruby object that is false in a boolean context, apart from false itself. We can see this using !! (read “bang bang”), which negates an object twice, thereby coercing it to its boolean value:

```
>> !!nil
=> false
```

In particular, all other Ruby objects are true, even 0:

```
>> !!0
=> true
```
