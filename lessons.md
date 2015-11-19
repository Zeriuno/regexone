1

match abcdefg
match abcde
match abc

.         - any character
abc       - 
\D        - any non digits character
\D{3,7}   - idem, repeating from three to 7 times
\w        - any alphanumeric character
\w{3,7}   - idem, repeating from three to 7 times
[a-g]*    - letters ranging from a to g repeating zero or more times
[a-g]+    - idem, repeating one or more times
^a        - starting with a
(.*)      - capture all

1 ½

match abc123xy
match define "123"
match var g = 123;

.
\w        - any alphanumeric character (with repetions, if you want {})
\D        - non digits characters
\d        - digits characters (eventually combined)
[a-z1-3]+ - characters ranging from a to z and 1 to 3, one occurence or more


2

match cat.
match 896.
match ?=+.
skip abc1


\.        - the dot
\.$       - ending with the dot
\W$       - ending with a non alphanumeric character
.{3}\.    - three characters and then a dot


3

match can
match man
match fan
skip dan
skip ran
skip pan

[cmf]     - in the cmf range
[cmf]an   - idem, followed by 'an'
[^drp]    - not in the drp range: isn't working but it should
[^drp]an  - not in the drp range, and followed by 'an'


4

match hog
match dog
skip bog

[^bog]     - not bog
[^b]og     - og, but not b


5

match Ana
match Bob
match Cpc
skip  aax
sky   bby
skip  ccz


[A-C]     - from everything in the interval A to C
[^x-z]$   - not having something in the interval x to z at the end
^[^a-c]   - at the beginning it should not be something in the interval from a to c


6

match wazzzzup
match wazzzup
skip wazup

z[2]      - z repeating twice
z{2,9}    - z repeating from twice up to 9 times     


7

match aaaabcc
match aabbbbc
match aacc
skip  a

a{2}     - a repeating twice
a{2,4}   - a repeating twice to four times
c        - having c
[b,c]    - in the range b and c
[^a]     - do not select a
c$       - with a c at the end
\w{2}    - any character repeating twice
c+       - c one or more repetitions


8

match 1 file found?
match 2 files found?
match 24 files found?
skip No file found.

\d file[s]* found? - a number, 'file' and the s optional, then 'found?'
\d      - a digit
\d+     - a digit or more
\?      - a question mark
\?$     - a question mark at the end
^[^N]   - at th beginning, not a capital N


9

match 1.   abc
match 2.	abc
match 3.           abc
skip  4.abc

\s      - a whitespace
\s+     - a whitespace or more
[ \t]   - in the range blanck space and tab
[ \t]+  - idem, one or more
