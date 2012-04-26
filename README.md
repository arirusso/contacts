## Welcome to Contacts

Contacts is a universal interface to grab contact list information from various providers including Outlook, Address Book, Hotmail, AOL, Gmail, Plaxo and Yahoo.

## Download

* `gem install contacts`
* `git clone git://github.com/cardmagic/contacts.git`

## Background

For a long time, the only way to get a list of contacts from your free online email accounts was with proprietary PHP scripts that would cost you $50. The act of grabbing that list is a simple matter of screen scrapping and this library gives you all the functionality you need. Thanks to the generosity of the highly popular Rails website MOG (http://mog.com) for allowing this library to be released open-source to the world. It is easy to extend this library to add new free email providers, so please contact the author if you would like to help.

## Usage

```ruby
Contacts::Hotmail.new(login, password).contacts # => [["name", "foo@bar.com"], ["another name", "bow@wow.com"]]
Contacts::Yahoo.new(login, password).contacts
Contacts::Gmail.new(login, password).contacts

Contacts.new(:gmail, login, password).contacts
Contacts.new(:hotmail, login, password).contacts
Contacts.new(:yahoo, login, password).contacts

Contacts.guess(login, password).contacts
```

Notice there are three ways to use this library so that you can limit the use as much as you would like in your particular application. The Contacts.guess method will automatically concatenate all the address book contacts from each of the successful logins in the case that a username password works across multiple services.

## Captcha error

If there are too many failed attempts with the gmail login info, Google will raise a captcha response. To integrate the captcha handling, pass in the token and response via:

```ruby
Contacts::Gmail.new(login, password, :captcha_token => params[:captcha_token], :captcha_response => params[:captcha_response]).contacts
```

## Examples

See the examples/ directory.

## Authors

* Lucas Carlson from MOG - http://mog.com
* Paperless Post

## Contributors

* [Contributors](https://github.com/paperlesspost/contacts/graphs/contributors)

This library is released under the terms of the BSD.

