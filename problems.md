1

match 3.14529
match -255.34
match 128
match 1.9e10
match 123,1340.00
skip 720p

.+[^p]$
^-?\d+(,\d+)*(\.?\d+(e\d+)?)?$ - (it can start with a minus, then one or more digits, then zero or more of a comma and digit(s), then eventually a dot and one or more digits, then eventually e and one or more digits and nothing after that
^\W?\d+[\.,]?\d{0,5}[e\.]?\d{0,2}[^p]$


2

capture 415-555-1234
capture 650-555-2345
capture (416)555-3456
capture 202 555 4567
capture 4035555678
capture 1 416 555 9292

(\d\s?)\W?(\d{3}\W?\d+(-?\s?\d+)*$  - maybe a group with a digit, and maybe a whitespace in the group. Then maybe a non alphanumeric character, three digits which we capture, then maybe a non alphanumeric character, one or more digits, and eventually a group with maybe a dash, maybe a whitespace and then one or more digits, the group being repeated zero or several times, and it stops with that
 1?[\s-]?\(?(\d{3})\)?[\s-]?\d{3}[\s-]?\d{4} - copy paste of the website solution


3

capture tom@hogwarts.com                  → tom
capture tom.riddle@hogwarts.com           → tom.riddle
capture tom.riddle+regexone@hogwarts.com  → tom.riddle
capture tom@hogwarts.eu.com               → tom
capture potter@hogwarts.com               → potter
capture harry@hogwarts.com                → harry
capture hermione+regexone@hogwarts.com    → hermione

^([\w.]*)  - website soution         - Capture a group of zero or more characters, at the start, and only alphanumeric one. But isn't the dot supposed to be escaped?
^([\w\.]+) - Capture a group of characters, from the start of the string, made of one or more among alphanumeric characters or dot.


4

capture <a>This is a link</a>                     → a
capture <a href='http://regexone.com'>Link</a>    → a
capture <div class='test_style'>Test</div>        → div
capture <div>Hello <span>world</span></div>       → div

(\w+)          - Capture one or more alphanumeric characters. '<' will be excluded, as well as whitespaces.
([a-z]+)       - Just letters.
<([a-z]+)[\s>] - Just letters captured. Those ust be preceeded by a '<' and followed by a whitespace or a '>'

/*
>([\w\s]*)<    - This would capture tag content
='([\w://.]*)' - And this one would capture attribute values
*/


8


capture  ftp://file_server.com:21/top_secret/life_changing_plans.pdf    → ftp file_server.com 21
capture  http://regexone.com/lesson/introduction#section                → http regexone.com
capture  file://localhost:4040/zip_file                                 → file localhost 4040
capture  https://s3cur3-server.com:9999/                                → https s3cur3-server.com 9999
capture  market://search/angry%20birds                                  → market search

(\w+)://(\w+[\.?\-?\w]*):?(\w+)?             - Capture one or more alphanumeric characters, followed by '://' then one or more alphanumeric characters and zero to more groups of '.' (optional) '-' (optional) and alphanumeric characters. Then ':' and, optional, one or more alphanumeric characters
(\w+)://(\w+[\.?\-?\w]*):?(\d+)?             - Capture one or more alphanumeric characters, followed by '://' then one or more alphanumeric characters and zero to more groups of '.' (optional) '-' (optional) and alphanumeric characters. Then ':' and, optional, one or more digits
