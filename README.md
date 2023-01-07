For now, this will just document my findings.

# Todo
- [ ] Format of:
  - [ ] [email](#Email)
  - [ ] phone number
  - [ ] address
  - [ ] social profiles
  - [ ] notes
  - [ ] picture
  - [ ] urls
  - [ ] birthday
  - [ ] more later, these are the ones i care about
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
## social profiles
## notes
## picture
## urls
## birthday
