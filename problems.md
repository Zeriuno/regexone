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
