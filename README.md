import random

# --- Create the Word Bank ---
word_bank = ['stars','cat','chicago','tiktok','Florida','animals',
'love','black','blue','mowgil','phone','apple','gold',' ]
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
