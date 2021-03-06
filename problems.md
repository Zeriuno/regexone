#Problems

##Problem 1: Matching a decimal numbers

match 3.14529
match -255.34
match 128
match 1.9e10
match 123,1340.00
skip 720p

.+[^p]$
^-?\d+(,\d+)*(\.?\d+(e\d+)?)?$ - (it can start with a minus, then one or more digits, then zero or more of a comma and digit(s), then eventually a dot and one or more digits, then eventually e and one or more digits and nothing after that
^\W?\d+[\.,]?\d{0,5}[e\.]?\d{0,2}[^p]$


##Problem 2: Matching phone numbers

capture 415-555-1234
capture 650-555-2345
capture (416)555-3456
capture 202 555 4567
capture 4035555678
capture 1 416 555 9292

(\d\s?)\W?(\d{3}\W?\d+(-?\s?\d+)*$  - maybe a group with a digit, and maybe a whitespace in the group. Then maybe a non alphanumeric character, three digits which we capture, then maybe a non alphanumeric character, one or more digits, and eventually a group with maybe a dash, maybe a whitespace and then one or more digits, the group being repeated zero or several times, and it stops with that
 1?[\s-]?\(?(\d{3})\)?[\s-]?\d{3}[\s-]?\d{4} - copy paste of the website solution


 ##Problem 3: Matching emails

capture tom@hogwarts.com                  → tom
capture tom.riddle@hogwarts.com           → tom.riddle
capture tom.riddle+regexone@hogwarts.com  → tom.riddle
capture tom@hogwarts.eu.com               → tom
capture potter@hogwarts.com               → potter
capture harry@hogwarts.com                → harry
capture hermione+regexone@hogwarts.com    → hermione

^([\w.]*)  - website soution         - Capture a group of zero or more characters, at the start, and only alphanumeric one. But isn't the dot supposed to be escaped?
^([\w\.]+) - Capture a group of characters, from the start of the string, made of one or more among alphanumeric characters or dot.


##Problem 4: Matching HTML

capture <a>This is a link</a>                     → a
capture <a href='http://regexone.com'>Link</a>    → a
capture <div class='test_style'>Test</div>        → div
capture <div>Hello <span>world</span></div>       → div

(\w+)          - Capture one or more alphanumeric characters. '<' will be excluded, as well as whitespaces.
([a-z]+)       - Just letters.
<([a-z]+)[\s>] - Just letters captured. Those ust be preceeded by a '<' and followed by a whitespace or a '>'


-----------------------------

Comment

([\w\s]*)    - This would capture tag content

='([\w://.]*)' - And this one would capture attribute values

------------------------------

##Problem 5: Matching specific filenames

skip     .bash_profile
skip     workspace.doc
capture  img0912.jpg          → img0912 jpg
capture  updated_img0912.png  → updated_img0912 png
skip     documentation.html
capture  favicon.gif          → favicon gif
skip     img0912.jpg.tmp
skip     access.lock


(\w+_?\w*)\.(\w{0,2}g\w{0,2})$  - Capture a group that starts with one or more alphanumeric characters eventually followed by an underscore and then zero or more alphanumeric characters. Then comes a dot. Then we capture a second group which is composed by zero to two alphanumeric characters, a g, zero to two alphanumeric characters more. And this group is the end of the string.

##Problem 6: Trimming whitespace from start and end of line

capture 	The quick brown fox...   → The quick brown fox...
capture  jumped over the lazy dog. → jumped over the lazy dog.

\s*([\w+\s?]+\.+)   - zero or more whitespaces, then capture a group made of one or more blocks of alphanumeric characters and eventually a whitespace, then one or more dots.

##Problem 7: Extracting information from a log file

skip     W/dalvikvm( 1553): threadid=1: uncaught exception
skip     E/( 1553): FATAL EXCEPTION: main
skip     E/( 1553): java.lang.StringIndexOutOfBoundsException
capture  E/( 1553): at widget.List.makeView(ListView.java:1727)      → makeView ListView.java 1727
capture  E/( 1553):   at widget.List.fillDown(ListView.java:652)     → fillDown  ListView.java  652
capture  E/( 1553): at widget.List.fillFrom(ListView.java:709)       → fillFrom  ListView.java  709


.*at widget.List.(\w+)\((\w{8}\.\w{4})\:(\d+)\)

##Problem 8: Parsing and extracting data from a URL


capture  ftp://file_server.com:21/top_secret/life_changing_plans.pdf    → ftp file_server.com 21
capture  http://regexone.com/lesson/introduction#section                → http regexone.com
capture  file://localhost:4040/zip_file                                 → file localhost 4040
capture  https://s3cur3-server.com:9999/                                → https s3cur3-server.com 9999
capture  market://search/angry%20birds                                  → market search

(\w+)://(\w+[\.?\-?\w]*):?(\w+)?             - Capture one or more alphanumeric characters, followed by '://' then one or more alphanumeric characters and zero to more groups of '.' (optional) '-' (optional) and alphanumeric characters. Then ':' and, optional, one or more alphanumeric characters
(\w+)://(\w+[\.?\-?\w]*):?(\d+)?             - Capture one or more alphanumeric characters, followed by '://' then one or more alphanumeric characters and zero to more groups of '.' (optional) '-' (optional) and alphanumeric characters. Then ':' and, optional, one or more digits
