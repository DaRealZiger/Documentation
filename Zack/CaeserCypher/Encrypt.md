# Encrypt Function
```c
void encrypt(char code[4095]){
    size_t len = strlen(code);
    while (i < len) {
        code[chr] += i;
        ovflow(code);
        chr += 1;
        i += 1;
    }

    printf("Encrypted Message:%s",code);
    escp(code);
    len = strlen(code);
    code[len-1] = code[len];
    sprintf(command, "termux-clipboard-set \"%s\"", code);
    system(command);
}
```
1. Get user [[#Input|input]]
2. Checks the length of the input
3. Runs the [[#Cypher|cypher]]
4. During the cypher process also runs `overflow(code)` 
5. Print's out the encrypted message
6. Checks the length of the newly cyphered code
7. Replaces the final `\n` of the array into `\0` to ensure the command work's correctly
8. Copies `termux-clipboard-set "{code}"` to `command` variable
9. `system(command)` runs `command` inside the terminal

# Cypher
```c
size_t len = strlen(code);
while (i < len) {
    code[chr] += i;
    ovflow(code);
    chr += 1;
    i += 1;
```
Uses [[Cyphers#Caeser Cypher|Caeser Cypher]] which shifts the ASCII of code\[n-1] up by n

# Input
Allows the user to input in multiple ways:
## Input via prompt
```c
if (argc < 2) {
    //Get User Input
    printf("Original message:");
    fgets(message, sizeof(message), stdin);
    encrypt(message);
// ...rest of code
```
1. Checks if `argc` is less than 2 
    > [!NOTE]
    >`argc` = 1 means only the binary was called
    >`argc` >= 2 means there are arguments

    > [!WARNING]
    > [[Changes#Encrypt|Change condition to 1]]
2. Prompts user input by printing `Original message:` and allowing user to input
3. Calls [[#Encrypt Function|`encrypt(message)` ]] 

## Input via argument straight from cli:
```c
//Encrypt with argument
} else if (strcmp(argv[1], "-e") == 0 || strcmp(argv[1], "e") == 0) {
    strcpy(message, argv[2]);

    size_t len = strlen(message);
    message[len] = '\n';

    printf("Original Message:%s", message);
    encrypt(message);
    // ...rest of code
```
1. User call binary with arguments
2. Check if `argv[1]` is `-e` or `e`
    > [!NOTE]
    > `argv[0]` is the binary
    > `argv[1]` is the argument
    > `argv[2]` is the message
3. Copies the argument into `message`
4. Checks the length of `message` and adds `\n` to the end
5. Prints out original message 
5. Calls [[#Encrypt Function|`encrypt(message)`]] 
