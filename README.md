import random

# --- Create the Word Bank ---
word_bank = ['stars','cat','chicago','tiktok','Florida','animals',
'love','black','blue','mowgil','phone','apple',' ]
word = random.choice(word_bank)
# --- Game Setup ---
guessedWord = ['_'] * len(word)
attempts = 10
guessed_letters = []
score = 0

print("===================================")
print("🕹️  WORD QUEST")
print("Guess letters or the full word")
print("You have 10 attempts — choose wisely!")
print("===================================\n")

# --- Game Loop ---
while attempts > 0:
print('\nCurrent word:', ' '.join(guessedWord))
    print('Guessed letters:', ' '.join(guessed_letters))
    print('Score:', score)
guess = input('Enter a letter or the full word: ').lower()
    # --- Full word guess ---
    if len(guess) == len(word) and guess.isalpha():
