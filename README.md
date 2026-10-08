# CodeAlpha_Hangman
import random

def play_hangman():
    words = ["python", "codealpha", "developer", "program", "script"]
    word_to_guess = random.choice(words)
    guessed_letters = []
    max_attempts = 6
    incorrect_guesses = 0

    print("=== Welcome to Hangman Game ===")
    print(f"Guess the word! You have {max_attempts} incorrect attempts.")

    while incorrect_guesses < max_attempts:
        display_word = ""
        for letter in word_to_guess:
            if letter in guessed_letters:
                display_word += letter + " "
            else:
                display_word += "_ "

        print("\nWord: ", display_word.strip())
        
        # Check if player has won
        if "_" not in display_word:
            print("Congratulations! You guessed the word correctly!")
            break

        guess = input("Guess a letter: ").lower().strip()

        if len(guess) != 1 or not guess.isalpha():
            print("Please enter a single valid letter.")
            continue

        if guess in guessed_letters:
            print(f"You already guessed '{guess}'. Try another letter.")
            continue

        guessed_letters.append(guess)

        if guess in word_to_guess:
            print(f"Good job! '{guess}' is in the word.")
        else:
            incorrect_guesses += 1
            remaining = max_attempts - incorrect_guesses
            print(f"Wrong guess! '{guess}' is not in the word. Remaining attempts: {remaining}")

    if incorrect_guesses == max_attempts:
        print(f"\nGame Over! The word was: '{word_to_guess}'")

if __name__ == "__main__":
    play_hangman()
