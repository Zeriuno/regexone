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
