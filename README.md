# MainStreet

A standard US address model for Rails

You get:

- geocoding
- standardization
- verification

## How It Works

[todo]

### Verification

MainStreet performs ZIP code verification by default.

```ruby
address = Address.new(street: "400 bryant st", zip_code: "94108")
address.valid?
# false
address.errors.full_messages
# ["Did you mean 94107?"]
```

## Installation

Add this line to your application’s Gemfile:

```ruby
gem 'mainstreet'
```

To create a new address model, run:

```sh
rails g mainstreet:address
```

This creates an `Address` model with:

- street
- street2
- city
- state
- zip_code
- latitude
- longitude
- verification_info
- original_attributes

To add to an existing model:

1. Use `alias_attribute` to map existing field names
2. Add new fields like `verification_info` and `original_attributes`
3. Add `acts_as_address` to your model

## Address Verification

MainStreet does ZIP code verification by default.

For complete address verification, sign up for a [SmartyStreets](https://smartystreets.com/features) account. The free plan supports 250 lookups per month.

Set:

```ruby
ENV["SMARTY_STREETS_AUTH_ID"] = "auth-id"
ENV["SMARTY_STREETS_AUTH_TOKEN"] = "auth-token"
```

To test it, run:

```ruby
address = Address.new(street: "122 Mast Rd", zip_code: "03861")
address.valid? # should get false
```

## Contributing

Everyone is encouraged to help improve this project. Here are a few ways you can help:

- [Report bugs](https://github.com/ankane/mainstreet/issues)
- Fix bugs and [submit pull requests](https://github.com/ankane/mainstreet/pulls)
- Write, clarify, or fix documentation
- Suggest or add new features
