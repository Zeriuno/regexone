1

match abcdefg
match abcde
match abc

.         - any character
abc       - 
\D        - any non digits character
\D+       - any non digits character once or more
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
\D+\d+\D+ - non-digits character, one or more, digits, one or more, non-digits, one or more
[a-z1-3]+ - characters ranging from a to z and 1 to 3, one occurence or more


2

match cat.
match 896.
match ?=+.
skip abc1


\.        - the dot
\.$       - ending with the dot
.+\.      - any character, one or more, ending with a dot
.{3}\.    - any character, three times, ending with a dot
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
(c|m|f)an - c- or m- or d- -an


4

match hog
match dog
skip bog

[^bog]     - not bog
[^b]og     - og, but not b
(d|h)og    - d- or h- og
[dh]og     - d or h and og


5

match Ana
match Bob
match Cpc
skip  aax
sky   bby
skip  ccz


[A-C]           - everything in the interval A to C
[A-C][a-p]+     - in the interval A to C, then a to p, one or more
[^x-z]$         - not having something in the interval x to z at the end
^[^a-c]         - at the beginning it should not be something in the interval from a to c
[A-C][n-p][a-c]


6

match wazzzzup
match wazzzup
skip wazup

waz{2,4}up -
z[2]       - z repeating twice
z{2,9}     - z repeating from twice up to 9 times     


7

match aaaabcc
match aabbbbc
match aacc
skip  a

aa+b*c+
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
\d files? found\?  - better version of the above
\d         - a digit
\d+        - a digit or more
^\d+\D+\?$ - start with one or more digit, then one or more non-digits, and a question mark at the end
\?         - a question mark
\?$        - a question mark at the end
^[^N]      - at th beginning, not a capital N


9

match 1.   abc
match 2.	abc
match 3.           abc
skip  4.abc

\s         - a whitespace
\s+        - a whitespace or more
[ \t]      - in the range blanck space and tab
[ \t]+     - idem, one or more
\d\D\s+\D+ - a digit, a non-digit character, one or more blank spaces, one or more non-digits
\d\.\s+abc 

10

match Mission: successful
skip Last Mission: unsuccessful
skip Next Mission: successful upon capture of target

^M      - starting with a capital M
^[^LN]  - starting not with L nor with N
^Mission: successful$

11

capture file_record_transcript.pdf → file_record_transcript
capture file_07241999.pdf          → file_07241999
skip testfile_fake.pdf.tmp

(+)\.pdf$        - everything ending with the pdf extension, do not capture the extension
(.+)\.pdf$       - everything, one character or more, ending with the pdf extension, do not capture the extension
(\w+)\.pdf$      - every alphanumeric character, once or more, ending with the pdf extension, do not caputre the extension
(file_\w+)\.pdf$ - every 'file_' plus one or more alphanumeric character, ending with the pdf extension, do not capture the extension
(file.+)\.pdf$


12

capture Jan 1987  → Jan 1987, 1987
capture May 1969  → May 1969, 1969
capture Aug 2011  → Aug 2011, 2011

([A-Za-z]+\s(\d+)) - in the range A-Z and a-z, one or more characters, a blankspace a number or more. Capture the whole and the number(s)
(\w+\s(.+))        - alphanumerical character, one or more, a blankspace, any character, one or more. Capture the whole and the characters after the blankspace
(\w+)\b(\d{4})     - alphanumerical one or more characters, a boundary character, four digits. Capture the first characters and the last four
(\w+(\d+))
(.{4}(.{4}))       - any character, four, than any character, four. Capture the whole and the last four


13

capture 1280x720  → 1280,720
capture 1920x1600 → 1920,1600
capture 1024x768  → 1024,768

(\d{4}).(\d+)     - four digits, any character, then one or more digits. Capture the first four and the rest after the fifth character
(.{4}).(.+)       - four of any character, any character, then one or more of any character. Capture the first four and those after the fifth
(.{4})\D(.+)      - any four characters, a non-digit, one or more of any characters
((.+)x(.+)        - any character, one or more, then a 'x' and then any character, one or more of them. Capture the blocks before and after the 'x'
(\d+)\w(\d+) 


14

match I love cats
match I love dogs
skip I love logs
skip I love cogs

I love (cat|dog)s - 'I love ' then 'cat' or 'dog' then an 's'
.*(cat|dog).      - any character zero or more times, 'cat' or 'dog' then any character
.+(ca|do).+       - any character once or more, 'ca' or 'do' then any character once or more


15

match The quick brown fox jumped over the lazy dog.
match There were 614 instances of students getting 90.0% or above.
match The FCC had to censor the network for saying &$#*@!.

.                 - any character
.+                - any character, once or more
\D+\d{0,3}.+      - any non digit character, once or more, digits, zero to three, and any other character, one or more
\S+\s\S+\s\S+\s\S+\s\S+\s\S+\s\S+\s\S+\s\S+\s?\S+ - whitespace and non-whitespace characters (with optional characters at the end
