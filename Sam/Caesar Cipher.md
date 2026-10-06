# Caesar Cipher Study Project in Termux

### Description 

In this project, i will be exploring how [caesar cipher] works (although it is incredibly obvious), by creating a command line tool that can encrypt and decrypt text

This tool will be able to receive input and output through clipboard or the terminal

### Core functions

##### Encryption and Decryption 

As the encoding and decoding process is fairly simple, which is substituing each letter with another along the ASCII table depending on the encryption formula. 

##### Clipboard interaction

To make inputting and outputting text easier, the tool is be able to access the clipboard in Termux.
This will allow us to encode and decode text from the android operating system in which termux lives on top.

### Program Flow

1. Interpretate command arguments from terminal execution
2. Determine whether input source (`clipboard` / `terminal`) and execution mode (`encrypt` / `decrypt`)
3. Get input from identified input source
4. Execute encoding and decoding
5. Output result via terminal and clipboard

### Implementation

##### Step 2
for loops are used to loop through arguments received from main in parameter `argv`

Each arguments are checked for key words for instruction on how to run the program

If the keywords are repeated or is not valid, the program `terminates`.

##### Step 3
Inputs are gather from terminal or user input depending on configuration received from execution arguments from [[#Step 2]]

##### Step 4
Encoding is carried out by increasing the ASCII number of the character by its index in the original text starting from 0.

Decoding reverses it.

Overflow and underflow of the ASCII value is handled by ensuring the value is within valid range.

### Bugs and Challenges

##### Accessing clipboard in Program

We are able to access clipboard in the terminal via `termux-clipboard-set` & `termux-clipboard-get`
we just need a way to access it in the program.

Solution
---------

We were able to access the terminal tools required using [[Terminal Access In Code#C|popen in C]].

This allowed us to run the command and get its input as a [FILE] type.

##### ASCII number overflow

As only a certain range of characters from the [ASCII] table can be used as stable text. 
The text risks getting corrupted during encoding and decoding

Solution
------

First we figure out the `Upper Range` and `Lower Range` of valid ASCII characters.

Then, a while loop is used to check if the encoded or decoded text is within the range.

The while loop runs until the character returns to the allowed range.

```
while (j < LOWER) {
            j = j + 95;
        }
        while (j > UPPER) {
            j = j - 95;
        }
```
