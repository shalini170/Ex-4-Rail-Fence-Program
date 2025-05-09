# Ex-4 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.
STEP-2: Arrange the plain text in row columnar matrix format.
STEP-3: Now read the keyword depending on the number of columns of the plain text.
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```
PROGRAM:
#include <stdio.h>
#include <string.h>
// Function to perform Vigenere encryption
void vigenereEncrypt(char *text, const char *key) {
    int textLen = strlen(text);
    int keyLen = strlen(key);
    for (int i = 0; i < textLen; i++) {
        char c = text[i];
        if (c >= 'A' && c <= 'Z') {
            // Encrypt uppercase letters
            text[i] = ((c - 'A' + key[i % keyLen] - 'A') % 26) + 'A';
        } else if (c >= 'a' && c <= 'z') {
            // Encrypt lowercase letters
            text[i] = ((c - 'a' + key[i % keyLen] - 'A') % 26) + 'a';
        }
    }
}
// Function to perform Vigenere decryption
void vigenereDecrypt(char *text, const char *key) {
    int textLen = strlen(text);
    int keyLen = strlen(key);
    for (int i = 0; i < textLen; i++) {
        char c = text[i];

        if (c >= 'A' && c <= 'Z') {
            // Decrypt uppercase letters
            text[i] = ((c - 'A' - (key[i % keyLen] - 'A') + 26) % 26) + 'A';
        } else if (c >= 'a' && c <= 'z') {
            // Decrypt lowercase letters
            text[i] = ((c - 'a' - (key[i % keyLen] - 'A') + 26) % 26) + 'a';
        }
    }
}
int main() {
    const char *key = "VAR"; 
    char message[] = "saveethaengineeringcollege";
    printf("Simulating Vigenere Cipher:\n");
    // Print the original plain text
    printf("Original Message: %s\n", message);
    // Print the key used
    printf("Key: %s\n", key);
    // Encrypt the message
    vigenereEncrypt(message, key);
    printf("Encrypted Message: %s\n", message);
    // Decrypt the message back to the original
    vigenereDecrypt(message, key);
    printf("Decrypted Message: %s\n", message);
    return 0;
}
```

# OUTPUT
![image](https://github.com/user-attachments/assets/cdc80906-ca49-4ef6-b0dc-09761dcb5ef4)


# RESULT
The program is executed successfully
