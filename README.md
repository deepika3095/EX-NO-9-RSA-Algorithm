# EX-NO-9-RSA-Algorithm

## AIM:
To Implement RSA Encryption Algorithm in Cryptography

## Algorithm:


Step 1: Design of RSA Algorithm  
The RSA algorithm is based on the mathematical difficulty of factoring the product of two large prime numbers. It involves generating a public and private key pair, where the public key is used for encryption, and the private key is used for decryption.

Step 2: Implementation in Python or C 
This algorithm can be implemented in languages like Python or C by performing large integer calculations for key generation, encryption, and decryption, utilizing libraries for modular arithmetic if necessary.

Step 3: Algorithm Description  
1. Key Generation:
   - Select two large prime numbers \( p \) and \( q \).
   - Calculate \( n = p \times q \), which will be used as the modulus.
   - Compute the totient \( \phi(n) = (p - 1)(q - 1) \).
   - Choose a public exponent \( e \) such that \( e \) is coprime with \( \phi(n) \).
   - Compute the private key \( d \), which is the modular inverse of \( e \) mod \( \phi(n) \).

2. Encryption:
   - Convert the plaintext message \( M \) into a numerical form \( m \) (such that \( 0 \le m < n \)).
   - Compute the ciphertext \( c \) using the formula: \( c = m^e \mod n \).

3. Decryption:
   - Use the private key \( d \) to recover \( m \) from \( c \) using: \( m = c^d \mod n \).
   - Convert \( m \) back into the original message \( M \).

Step 4: Mathematical Representation  
- Encryption: \( E(m) = m^e \mod n \)
- Decryption: \( D(c) = c^d \mod n \)

Step 5: **Security Foundation  
The security of RSA relies on the difficulty of factoring large numbers; thus, choosing sufficiently large prime numbers for \( p \) and \( q \) is crucial for security.

## Program:
```
#include <stdio.h>
#include <string.h>

long long power(long long base, long long exp, long long mod) {
    long long result = 1;
    while (exp > 0) {
        result = (result * base) % mod;
        exp--;
    }
    return result;
}

int main() {

    int p = 3, q = 11;
    int n = p * q;      // 33
    int phi = 20;
    int e = 3;
    int d = 7;

    char msg[100];
    printf("Enter lowercase message: ");
    scanf("%s", msg);

    int len = strlen(msg);
    long long enc[100];

    printf("\nEncrypted:\n");
    for (int i = 0; i < len; i++) {
        int m = msg[i] - 'a';    // convert to 0–25
        enc[i] = power(m, e, n);
        printf("%lld ", enc[i]);
    }

    printf("\n\nDecrypted:\n");
    for (int i = 0; i < len; i++) {
        int dec = power(enc[i], d, n);  
        printf("%c", dec + 'a');        // convert back to letter
    }

    printf("\n");
    return 0;
}

```



## Output:
<img width="1748" height="675" alt="image" src="https://github.com/user-attachments/assets/860779d8-9707-4b69-b5e7-01e109ad3bd8" />

## Result:
 The program is executed successfully.
