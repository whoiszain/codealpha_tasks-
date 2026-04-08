import random

# ─────────────────────────────────────────
#  Predefined word list
# ─────────────────────────────────────────
WORDS = ["python", "hangman", "keyboard", "science", "programming"]

# ─────────────────────────────────────────
#  ASCII art for the gallows (0–6 wrong)
# ─────────────────────────────────────────
HANGMAN_STAGES = [
    # 0 wrong guesses
    """
  +---+
  |   |
      |
      |
      |
      |
=========""",
    # 1 wrong guess
    """
  +---+
  |   |
  O   |
      |
      |
      |
=========""",
    # 2 wrong guesses
    """
  +---+
  |   |
  O   |
  |   |
      |
      |
=========""",
    # 3 wrong guesses
    """
  +---+
  |   |
  O   |
 /|   |
      |
      |
=========""",
    # 4 wrong guesses
    """
  +---+
  |   |
  O   |
 /|\\  |
      |
      |
=========""",
    # 5 wrong guesses
    """
  +---+
  |   |
  O   |
 /|\\  |
 /    |
      |
=========""",
    # 6 wrong guesses — game over
    """
  +---+
  |   |
  O   |
 /|\\  |
 / \\  |
      |
=========""",
]

MAX_WRONG = 6


def display_state(wrong_count: int, guessed: set, secret: str) -> None:
    """Print the gallows, masked word, and wrong letters."""
    print(HANGMAN_STAGES[wrong_count])

    # Masked word: show guessed letters, underscore for the rest
    masked = " ".join(ch if ch in guessed else "_" for ch in secret)
    print(f"\n  Word: {masked}")
    print(f"  Wrong guesses ({wrong_count}/{MAX_WRONG}): {' '.join(sorted(guessed - set(secret)))}")
    print()


def get_guess(guessed: set) -> str:
    """Prompt the player for a valid, new single letter."""
    while True:
        guess = input("  Guess a letter: ").strip().lower()
        if len(guess) != 1 or not guess.isalpha():
            print("  ⚠  Please enter a single letter.")
        elif guess in guessed:
            print(f"  ⚠  You already guessed '{guess}'. Try another.")
        else:
            return guess


def play() -> None:
    """Run one full game of Hangman."""
    secret = random.choice(WORDS)
    guessed: set = set()
    wrong = 0

    print("\n" + "=" * 40)
    print("       W E L C O M E  T O  H A N G M A N")
    print("=" * 40)
    print(f"  The word has {len(secret)} letters. Good luck!\n")

    while wrong < MAX_WRONG:
        display_state(wrong, guessed, secret)

        # Check win condition
        if all(ch in guessed for ch in secret):
            print(f"  🎉 You won! The word was '{secret}'.")
            break

        letter = get_guess(guessed)
        guessed.add(letter)

        if letter in secret:
            print(f"  ✅ '{letter}' is in the word!\n")
        else:
            wrong += 1
            remaining = MAX_WRONG - wrong
            print(f"  ❌ '{letter}' is NOT in the word. {remaining} guess(es) left.\n")
    else:
        # Ran out of guesses
        display_state(wrong, guessed, secret)
        print(f"  💀 Game over! The word was '{secret}'.")

    print("=" * 40 + "\n")


def main() -> None:
    """Main loop — lets the player replay."""
    while True:
        play()
        again = input("  Play again? (y/n): ").strip().lower()
        if again != "y":
            print("\n  Thanks for playing! Goodbye. 👋\n")
            break


if __name__ == "__main__":
    main()
