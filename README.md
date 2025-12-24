import random

# --- Create the Word Bank ---
word_bank = ['stars','cat','chicago','tiktok','Florida','animals',
'love','black','blue','mowgil','phone',' ]
word = random.choice(word_bank)
# --- Game Setup ---
guessedWord = ['_'] * len(word)
attempts = 10
guessed_letters = []
score = 0
