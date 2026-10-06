# Terminal Access in Code 


### C 
--------
Through popen function from `<stdio>`, we can access terminal outputs as a `FILE`

```
FILE* terminalOutput = popen("command", "r");
```
