Optopus
=======

Yet another PHP CLI options parser.  Strives to be simple, robust, user-friendly, and adhere to GNU standards

Usage:

```php
$options = new Optopus\Options;

$options->add('--foo')
  ->alias('-f)
  ->description('Foo. Set description here.');
  
$options->add(--bar)
  ->alias(-b)
  ->acceptsArgument('required')
  ->description('Bar.  Set description here.  This option requires an additional argument.');
  
$options->add('--verbose')
  ->alias('-v')
  ->repeats()
  ->description('Verbosity.  You can amplify by adding again ie: -vvv or -v -v or --verbose --verbose');
  
$options->register();

print_r($options);
```

Option Arguments can be called with the following syntaxes:

`./script --bar foo`

`./script -b foo`

`./script --bar=foo`

`./script -b=foo`

It will also allow 'clustered' short options ie: `-asdf` is equal to `-a -s -d -f`.  In addition, option arguments can be provided with 'clustered' short options, ie:

`./script -asdf=bar`

`./script -asdf bar`


This will not work as of now:

`./script --barFOO` no spaces. assuming --bar acceptsArgument()  This will not work as expected.  Still not sure if this *should* be supported.


Supports "--" for end-of-options GNU pseudo-standard

`--help`, `-h`, `-?` will default to a help page generated from the `description()` method of options.

Also preserves script arguments (not captured by option arguments), by calling getArguments() method.
