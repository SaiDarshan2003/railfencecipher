## EX.NO:5 Rail Fence Cipher

## AIM:
To develop a simple C program to implement Rail Fence Cipher.

## DESIGN STEPS:
Step 1:
Design of Rail Fence Cipher algorithnm

Step 2:
Implementation using C or pyhton code

Step 3:
Testing algorithm with different key values. 

## PROGRAM:
```
#include <stdio.h>
#include <string.h>
void encryptRailFence(char *plaintext, int rails, char *ciphertext) {
    int len = strlen(plaintext);
    char rail[rails][len];
    memset(rail, '\n', sizeof(rail)); // Initialize rail matrix
    int row = 0, dir = 1; // dir=1 for down, -1 for up
    for (int i = 0; i < len; i++) {
        rail[row][i] = plaintext[i];
        row += dir;
        if (row == rails - 1 || row == 0) dir *= -1; // Change direction at edges
    }
    int index = 0;
    for (int i = 0; i < rails; i++)
        for (int j = 0; j < len; j++)
            if (rail[i][j] != '\n')
                ciphertext[index++] = rail[i][j];
    ciphertext[index] = '\0'; // Null terminate
}
int main() {
    char plaintext[100], ciphertext[100], decryptedText[100];
    int rails;
    printf("Enter plaintext: ");
    fgets(plaintext, sizeof(plaintext), stdin);
    plaintext[strcspn(plaintext, "\n")] = '\0'; 
    printf("Enter number of rails: ");
    scanf("%d", &rails);
    encryptRailFence(plaintext, rails, ciphertext);
    printf("Encrypted Text: %s\n", ciphertext);
    return 0;
}

```

## OUTPUT:
![image](https://github.com/user-attachments/assets/37a6e449-4dcf-48f8-8956-dd2c0e79abc3)


## RESULT:
The program is executed successfully.
