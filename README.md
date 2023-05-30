#include <stdio.h>
#include <string.h>

int main() {
    char word[100], guess[100];
    int i, tries = 0, len, found = 0;

    printf("Enter the word to be guessed: ");
    scanf("%s", word);

    len = strlen(word);

    printf("The word has %d letters.\n", len);

    for (i = 0; i < len; i++) {
        guess[i] = '-';
    }
    guess[len] = '\0';

    printf("Guess the word: %s\n", guess);

    while (tries < 6 && !found) {
        char letter;
        int j, match = 0;

        printf("Enter a letter: ");
        scanf(" %c", &letter);

        for (j = 0; j < len; j++) {
            if (word[j] == letter) {
                guess[j] = letter;
                match = 1;
            }
        }

        if (!match) {
            tries++;
            printf("Incorrect guess. You have %d tries left.\n", 6-tries);
        } else {
            if (strcmp(word, guess) == 0) {
                found = 1;
            } else {
                printf("Good guess! The word now looks like this: %s\n", guess);
            }
        }
       if (found) {
        printf("Congratulations! You guessed the word: %s\n", word);
    } else {
        printf("Sorry, you ran out of tries. The word was: %s\n", word);
    }

    return 0;
}
