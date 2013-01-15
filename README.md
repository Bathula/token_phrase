# TokenPhrase

TokenPhrase is a simple gem that generates unique phrases for you to use in your app as tokens.

"Why?" you may be asking. Why not? Token phrases give your app a little personality and make support a lot easier.

TokenPhrase was built for [Sellmer](http://justsellstuff.com), a simple yet powerful way to sell your digital goods.

## Installation

Add this line to your application's Gemfile:

    gem 'token_phrase'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install token_phrase

## TokenPhrase.generate(separator = nil, dictionaries = {})

### Defaults
By default, TokenPhrase uses the included dictionaries and separates everything with a hyphen (-):

```ruby
TokenPhrase.generate
=> "ultimate-blue-glossy-lamp"

5.times { p TokenPhrase.generate }
"energetic-white-checked-book"
"genetically-modified-red-argyle-lego-set"
"strong-yellow-wavy-machine"
"sugarfilled-blue-glossy-jacket"
"sour-ultraviolet-plaid-sand"
```

### Separators
If you would like a different separator, just pass a string as an argument: 

```ruby
TokenPhrase.generate('$')
=> "exciting$taupe$glossy$lake"

TokenPhrase.generate('!!!eric!!!')
=> "splendid!!!eric!!!golden!!!eric!!!glossy!!!eric!!!flounder"
```

### Dictionaries
TokenPhrase combines words from four different dictionaries:

* :adjectives
* :colors
* :patterns
* :nouns

If you want to replace the dictionary, just pass a hash with an array as an argument:

```ruby
TokenPhrase.generate :adjectives => %w(glowing)
=> "glowing-tan-striped-sand"

5.times { p TokenPhrase.generate :nouns => %w(Mercury Venus Earth Mars Jupiter Saturn Uranus Neptune Pluto) }
"home-made-lime-plaid-Pluto"
"bluetooth-lime-wavy-Jupiter"
"sugarfilled-tan-pinstriped-Mars"
"magnetic-pink-polka-dotted-Saturn"
"grandmas-white-plaid-Pluto"
```
You can pass multiple dictionaries: 

```ruby
5.times { p TokenPhrase.generate :colors => %w(black white), :nouns => %w(cat dog) }
"spectacular-white-argyle-dog"
"wind-up-white-plaid-cat"
"glazed-white-polka-dotted-cat"
"bodacious-white-checked-cat"
"genetically-modified-white-pinstriped-dog"
```

And you can, of course pass a separator before the dictionaries:

```ruby
5.times { p TokenPhrase.generate '^^^', :patterns => %w(striped), :adjectives =>%w(great awesome) }
"great^^^brown^^^striped^^^door"
"great^^^silver^^^striped^^^carpenter"
"great^^^lime^^^striped^^^crane"
"great^^^taupe^^^striped^^^envelope"
"great^^^pink^^^striped^^^sand"
```

## Dictionary Methods

If you like the existing dictionaries, but want to add your own words, you can use get an array of each dictionary:

* TokenPhrase.adjectives(more_adjectives = nil)
* TokenPhrase.colors(more_colors = nil)
* TokenPhrase.patterns(more_patterns = nil)
* TokenPhrase.nouns(more_nouns = nil)

Each of these dictionary methods accept an array as an argument that will merge the existing dictionary with your array

```ruby
your_patterns = TokenPhrase.patterns %w(magic-eye)
TokenPhrase.generate :patterns => your_patterns
=> "awesome-mauve-magic-eye-giraffe"
```


## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
