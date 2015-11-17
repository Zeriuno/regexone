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
