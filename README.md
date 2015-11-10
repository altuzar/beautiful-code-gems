# Beautiful Code Gems

Here is some beautiful code taken from everywhere, not only Ruby but also other languages. 



## !!nil != !!0

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

## Password Generator

```
('a'..'z').to_a.shuffle[0..7].join
```

## Ruby Inspect Inspect

What about the inspect of the inspect method for Ruby?

```
alias __inspect__ inspect
def inspect # :nodoc:
  array = []
  for ivar in instance_variables.sort{|e1, e2| e1 <=> e2}
    ivar = ivar.to_s
    name = ivar.sub(/^@(.*)$/, '\1')
    val = instance_eval(ivar)
    case ivar
    when *NOPRINTING_IVARS
      array.push format("conf.%s=%s", name, "...")
    when *NO_INSPECTING_IVARS
      array.push format("conf.%s=%s", name, val.to_s)
    when *IDNAME_IVARS
      array.push format("conf.%s=:%s", name, val.id2name)
    else
      array.push format("conf.%s=%s", name, val.inspect)
    end
  end
  array.join("\n")
end
alias __to_s__ to_s
alias to_s inspect
```