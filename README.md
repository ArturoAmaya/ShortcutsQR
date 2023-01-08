For now, this will just document my findings.

# Todo
- [ ] Format of:
  - [x] [email](#Email)
  - [x] [phone number](#phone-number)
  - [x] [address](#address)
  - [x] [social profiles](#social-profiles)
  - [x] [notes](#notes)
  - [x] [picture](#picture)
  - [x] [urls](#urls)
  - [x] [birthday](#birthday)
  - [x] more later, these are the ones i care about
- [ ] How to call in using a dict OR call a function isntead of just a script
- [ ] How to create new contact
- [ ] How to add details to contact
- [ ] How to remove contact

# Formats
## Email
Email is stored as a list. That is, `contact.email[0]` refers to the first possible email and `contact.email[1]` to the next and so on.

Each entry, i.e. email, is a 2-tuple. The contents in side the tuple are:
```
(label,contents)
```
The label format is a little strange - the "home" label appears as `_$!<Home>!$_`
The contents is fine.
They are both type `str`.

## phone number
Phone numbers are stored as a list. Each entry in the list is a 2-tuple, with label and contents. The label is like with email. The contents are different. The number is a string, and it is formatted like so:
```
(###) ###-####
```
The "()" are chars, as is the space and the "-". The string is 14 chars long.
## address
List, then tuples. The label follows the same format as the others. The contents is a `dict`. 
A standard one looks like this:
```
{
    'Street': '5185 Example Lane\n899',
    'ZIP': '44155',
    'City': San Fransisco',
    'CountryCode': us,
    'State': 'CA',
    'Country': 'United States'
}
```
Where "899" is the address line 2 contents.

## social profiles
Again, list then tuples. The label seems a lot more normal. For example, the label for the "Twitter" profile is `'Twitter'`, the label for "Facebook" is `'Facebook'`, "Slack" is `'Slack'` etc. Even the custom "Pokemon GO" shows up as `'Pokémon GO'`.

The contents is a little complicated. It is a dict. Rather than explain, here are two examples:

Twitter, with a profile name of "mytwitter", which shows up on the contact card as "@mytwitter":

```
{
    'url': 'http://twitter.com/mytwitter',
    'username': 'mytwitter',
    'service': 'twitter'
}
```

The custom Pokémon GO label with content "lmao ok"
```
{
    'url': 'x-apple:lmao%20ok',
    'username': 'lmao ok',
    'service': 'Pokémon GO'
}
```
The twitter one opens safari or the actual twitter app. Not sure what the x-apple ones do. Maybe I could replace them with my url but that's not a big deal.

Any future updates my occur here.

## notes
This one's interesting. It seems that the contacts package includes a `.note` attribute for contact objects. It is supposed to rreturn a string. However, used with a dummy contact with a notes section with multiple lines, it returns None, i.e. it found nothing. Attempting write to that field does not affect the notes field in the contact. Thus, this part should probably be done through the shortcuts section.
## picture
This a bunch of hex stuff, it's probably the literal file data. I don't want to mess with that, let's do it in shortcuts. Either way, I think it doesn't translate well in the QR code. 
## urls
The standard list of tuples. The label "homepage" is `'_$!<HomePage>!$_'`, and "home" is `'_$!<Home>!$_'`. Interestingly, the custom label "Custom haha" is `Custom haha`. Content that appears as "amazinga.com" is reported as "http://amazinga.com" in the contacts app, so it seems that is added in automatically (why not https?).
## birthday
This is a 'datetime.datetime' object. Thats YYYY-MM-DD HH:MM:SS (I think it defaulted to 05:00:00). Don't think there's a clear cut way to access other datetimes like anniversary.
## Other
### Nickname
nickname is just a string
### organization
also just a string
### vcard
Vcard seems to be a parameter that can be accessed but it just seems to be empty here. interesting.

# Call in using a dict
Totally doable, apparently its super easy in shortcuts... See the shortcuts example in your library TODO: update with public one

#
