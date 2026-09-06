# ILA2, T9 spelling

## Pseudocode

Entire idea is to repeat a digit till it hits the correct character. If the next char uses the same digit, we need to leave a space. 

Easiest way is to hard code out all 27 char + space and its associated digit representation. Alternatively, initialise a 128 string array with a for loop or leverage of java char to ascii value behaviour.

```text
keys = "22233344455566677778889999"
rep  = "12312312312312312341231234"
prev char = '\0'
curr char = read.charAt(0)
if prev == curr then res = res.append(' ')
res = res.append(curr.repeat(rep.charAt(char - 'a')))
```

## Code

