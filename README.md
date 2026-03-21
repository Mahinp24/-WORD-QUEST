import random
# --- Create the Word Bank ---
word_bank = [
    'stars', 'cat', 'chicago', 'tiktok', 'florida',
    'animals', 'love', 'black', 'blue', 'mowgil',
    'phone', 'apple', 'new-york', 
    'batman', 'monday', 'code', 'family', 
    'friends', 'computer']
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

# --- Game Loop ---
while attempts > 0:
    print('\nCurrent word:', ' '.join(guessedWord))
    print('Guessed letters:', ' '.join(guessed_letters))
    print('Score:', score)

guess = input('Enter a letter or the full word: ').lower()

# --- Full word guess ---
if len(guess) == len(word) and guess.isalpha():
        if guess == word:
            score += 50
            print('\n🎉 Congratulations!! You guessed the word:', word)
            print('🏆 Final Score:', score)
            break
        else:
            attempts -= 1
            score -= 10
            print('❌ Wrong word guess! Attempts left:', attempts)
            continue

# --- Single letter guess ---
if len(guess) != 1 or not guess.isalpha():
        print("⚠️ Please enter a single letter or the full word.")
        continue

if guess in guessed_letters:
        print("⚠️ You already guessed that letter.")
        continue

guessed_letters.append(guess)

if guess in word:
        for i in range(len(word)):
            if word[i] == guess:
                guessedWord[i] = guess
        score += 5
        print('✅ Great guess! +5 points')
    else:
        attempts -= 1
        score -= 5
        print('❌ Wrong letter! Attempts left:', attempts)

 # --- Win condition ---
if '_' not in guessedWord:
        score += 20
        print('\n🎉 Congratulations!! You guessed the word:', word)
        print('🏆 Final Score:', score)
        break

# --- Loss condition ---
if attempts == 0 and '_' in guessedWord:
    print('\n💀 You\'ve run out of attempts!')
    print('The word was:', word)
    print('🏆 Final Score:', score)
