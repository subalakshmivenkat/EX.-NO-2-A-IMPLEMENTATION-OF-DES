# EX.-NO-3-IMPLEMENTATION OF DES
## AIM:
  To write a program to implement Data Encryption Standard (DES).
## ALGORITHM:
  STEP-1: Read the 64-bit plain text.
  STEP-2: Split it into two 32-bit blocks and store it in two different arrays.
  STEP-3: Perform XOR operation between these two arrays.
  STEP-4: The output obtained is stored as the second 32-bit sequence and the original second 32-bit sequence forms the first part.
  STEP-5: Thus the encrypted 64-bit cipher text is obtained in this way. Repeat the same process for the remaining plain text characters.
## PROGRAM:
```
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#define BLOCK_SIZE 8
unsigned char key[BLOCK_SIZE] = {0x1A, 0x2B, 0x3C, 0x4D, 0x5E, 0x6F, 0x7A, 0x8B};
void simpleEncrypt(const unsigned char *plaintext, unsigned char *ciphertext, int length) {
    for (int i = 0; i < length; i++) {
        ciphertext[i] = plaintext[i] ^ key[i % BLOCK_SIZE];
    }}
void simpleDecrypt(const unsigned char *ciphertext, unsigned char *plaintext, int length) {
    for (int i = 0; i < length; i++) {
        plaintext[i] = ciphertext[i] ^ key[i % BLOCK_SIZE];
    }}
int main() {
    char inputMessage[1024];
    unsigned char encryptedData[1024];
    unsigned char decryptedData[1024];
    printf("Enter message to encrypt: ");
    fgets(inputMessage, sizeof(inputMessage), stdin);
    int inputLen = strlen(inputMessage);
    if (inputMessage[inputLen - 1] == '\n') {
        inputMessage[inputLen - 1] = '\0';  // Remove newline character
        inputLen--;
    }
    printf("Original message: %s\n", inputMessage);
    simpleEncrypt((unsigned char *)inputMessage, encryptedData, inputLen);
    printf("Encrypted message (in hex): ");
    for (int i = 0; i < inputLen; i++) {
        printf("%02x", encryptedData[i]);
    }
    printf("\n");
    simpleDecrypt(encryptedData, decryptedData, inputLen);
    decryptedData[inputLen] = '\0';  // Null-terminate the decrypted message
    printf("Decrypted message: %s\n", decryptedData);
    return 0; }
```
## OUTPUT:
![image](https://github.com/user-attachments/assets/0b0db44e-8475-42b1-b4c7-fd637de8e1ce)
## RESULT:
  Thus the data encryption standard algorithm had been implemented successfully.
