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

## The first

Only the *first* commit for Rails, made Nov 23, 2004. It was not the first first, as the first one was with CSV a year earlier and that source history is lost. But first for [git](https://github.com/rails/rails/commit/db045dbbf60b53dbe013ef25554fd013baf88134).

```
+*0.4* (5)
 +
 +* Consolidated the server configuration options into Base#server_settings= and expanded that with controls for authentication and more [Marten]
 +  NOTE: This is an API change that could potentially break your application if you used the old application form. Please do change!
 +
 +* Added Base#deliveries as an accessor for an array of emails sent out through that ActionMailer class when using the :test delivery option. [bitsweat]
 +
 +* Added Base#perform_deliveries= which can be set to false to turn off the actual delivery of the email through smtp or sendmail.
 +  This is especially useful for functional testing that shouldn't send off real emails, but still trigger delivery_* methods.
 +
 +* Added option to specify delivery method with Base#delivery_method=. Default is :smtp and :sendmail is currently the only other option.
 +  Sendmail is assumed to be present at "/usr/sbin/sendmail" if that option is used. [Kent Sibilev]
 +
 +* Dropped "include TMail" as it added to much baggage into the default namespace (like Version) [Chad Fowler]
 +
 +
 +*0.3*
 +
 +* First release 
```
