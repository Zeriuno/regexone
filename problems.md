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
