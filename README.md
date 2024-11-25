# esercizio_cifrari_2425  
Esercizio Programmazione Procedurale 24/25  
Scrivere  
Giacomo 
Tiacci
  


#include <stdio.h>
#include <string.h>
#include <ctype.h>

// Funzione per crittografare usando il cifrario di Vigenère
void vigenereEncrypt(const char *plaintext, const char *key, char *ciphertext) {
    int textLen = strlen(plaintext);
    int keyLen = strlen(key);
    int j = 0; // Indice della chiave

    for (int i = 0; i < textLen; i++) {
        if (isalpha(plaintext[i])) { // Se è una lettera
            char base = islower(plaintext[i]) ? 'a' : 'A'; // Differenzia maiuscole e minuscole
            char keyBase = tolower(key[j % keyLen]) - 'a';  // Calcola il valore numerico della chiave
            ciphertext[i] = (plaintext[i] - base + keyBase) % 26 + base; // Sposta la lettera
            j++; // Incrementa solo per i caratteri alfabetici
        } else {
            ciphertext[i] = plaintext[i]; // Mantieni i caratteri non alfabetici
        }
    }
    ciphertext[textLen] = '\0'; // Terminazione della stringa
}

int main() {
    // Messaggio e chiave predefiniti
    char plaintext[] = "ciao come stai";
    char key[] = "gatto";
    char ciphertext[256];

    // Mostra il messaggio e la chiave
    printf("Messaggio originale: %s\n", plaintext);
    printf("Chiave: %s\n", key);

    // Crittografa il messaggio
    vigenereEncrypt(plaintext, key, ciphertext);

    // Mostra il messaggio crittografato
    printf("Messaggio crittografato: %s\n", ciphertext);

    return 0;
}
