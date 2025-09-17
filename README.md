# Ex-5 Rail-Fence-Program

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

``` C
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main() {
    int i, j, len, rails;
    char str[1000];

    printf("Enter a Secret Message:\n");
    fgets(str, sizeof(str), stdin);

    str[strcspn(str, "\n")] = '\0';
    len = strlen(str);

    printf("Enter number of rails:\n");
    scanf("%d", &rails);

    char code[rails][len];

    for (i = 0; i < rails; i++) {
        for (j = 0; j < len; j++) {
            code[i][j] = '\n';
        }
    }

    // Fill the rail fence zig-zag
    int row = 0, down = 1;
    for (j = 0; j < len; j++) {
        code[row][j] = str[j];

        if (row == 0) {
            down = 1;  // Go down
        } else if (row == rails - 1) {
            down = 0;  // Go up
        }

        row += (down ? 1 : -1);
    }

    // Print encrypted text
    printf("Encrypted Message: ");
    for (i = 0; i < rails; i++) {
        for (j = 0; j < len; j++) {
            if (code[i][j] != '\n') {
                printf("%c", code[i][j]);
            }
        }
    }
    printf("\n");

    return 0;
}
```

# OUTPUT

<img width="1105" height="227" alt="Screenshot 2025-08-18 135114" src="https://github.com/user-attachments/assets/89da593b-98c7-4098-a10c-41d94664b916" />

Enter a Secret Message: Weardiscovered

Enter number of rails: 2

Encrypted message: Wadsoeeericvrd

# RESULT
The program is executed successfully
