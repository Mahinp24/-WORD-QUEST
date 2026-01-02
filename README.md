import random

# --- Create the Word Bank ---
word_bank = [
'stars', 'cat', 'chicago', 'tiktok', 'florida',
'animals', 'love', 'black', 'blue', 'mowgil',
'phone', 'apple', 'new-york', 'batman', 'monday',
'code', 'family', 'friends'
]

word = random.choice(word_bank)

# --- Game Setup ---
guessedWord = ['_'] * len(word)
attempts = 10
guessed_letters = []
score = 0

print("===================================")
print("🕹️ WORD QUEST")
print("Guess letters or the full word")
print("You have 10 attempts — choose wisely!")
print("===================================")

# ⭐ NEW OUTPUT: Show wording to player
print("\n📚 Possible Words:")
print(", ".join(word_bank))
print("===================================\n")
