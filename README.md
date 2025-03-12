# Python-Coding

### Count the Occurrences of Each Element in a List
```from collections import Counter

def count_occurrences(lst):
    return dict(Counter(lst))

print(count_occurrences([1, 2, 2, 3, 3, 3, 4]))  
# Output: {1: 1, 2: 2, 3: 3, 4: 1}
```
without Counter
```
def count_occurrences(lst):
  count={}
  for num in lst:
    count[num]=count.get(num,0)+1
    return count
```

### Regex to find all emails
```
import re
re.findall(r'[a-zA-Z0-9._%+-]+@[a-zA-Z0-9,-]+\.[a-zA-Z]{2,}',text)
```
```
[a-zA-Z0-9._%+-]+   → Matches the local part (before @) with letters, numbers, dots, underscores, etc.
@                   → Matches the @ symbol.
[a-zA-Z0-9.-]+      → Matches the domain name (e.g., "example", "mycompany").
\.                  → Matches the dot before the domain extension.
[a-zA-Z]{2,}        → Matches the domain extension (e.g., "com", "org", "net").

```

### Regex to find all text between quotes
```
import re
re.findall(r'["\'](.*?)["\']',text)
```
```
["']       → Matches either a single (`'`) or double (`"`) quote.
(.*?)      → Captures everything inside the quotes (non-greedy match).
["']       → Ensures the match ends with the same quote type.

```


