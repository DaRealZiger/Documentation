# Decrypt Argument
```c
    } else if (strcmp(argv[1], "-d") == 0 || strcmp(argv[1], "d") == 0) {

        sprintf(command, "termux-clipboard-get");
        char * message= getTermuxClipboard();
        size_t len = strlen(message);
        message[len] = '\n';
        printf("Encrypted Message:%s", message);

        dcrypt(message);
    // ...rest of code
```
1. Checks if `argv[1]` is `-d` or `d`
    > [!NOTE]
    > `argv[0]` is the binary
    > `argv[1]` is the argument
2. Copies `termux-clipboard-get` into variable `command` 
    > [!WARNING]
    > [[Changes#Decrypt|Useless Line]]
3. Point `message` to `getTermuxClipboard()`
4. Check the length of the `message`
5. Replace the end of the `message` with `\n` to ensure [[#Decrypt Function|`dcrypt()`]] works properly
6. Calls [[#Decrypt Function|`dcrypt(message)`]]

# Decrypt Function
```c
void dcrypt(char code[4095]){
    size_t len = strlen(code);
    while (i < len) {
        code[chr] -=i;
        ovflow(code);
        chr += 1;
        i += 1;
    }
    printf("Original Message:%s", code);
}
```
1. Check's the length of `code`
2. Runs the cypher in reverse 
3. During the cypher reversal also runs `overflow(code)`
4. Prints out the original message
