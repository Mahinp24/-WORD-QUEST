import random
import time

# --- Word Bank ---
word_bank = [
    'stars', 'cat', 'chicago', 'tiktok', 'florida',
    'animals', 'love', 'black', 'blue',
    'mowgil', 'phone', 'apple', 'new-york',
    'batman', 'monday', 'code', 'family',
    'friends', 'computer',
    "firewall", "malware", "python", "linux",
    "network", "database", "packet", "cybersecurity",
    "exploit", "kernel", "router", "cloud"
]

word = random.choice(word_bank)

# --- Game Setup ---
guessedWord = ['_'] * len(word)
guessed_letters = []
attempts = 10

score_p1 = 0
score_p2 = 0

streak_p1 = 1
streak_p2 = 1

print("===================================")
print("🕹️ WORD QUEST")
print("Guess letters or the full word")
print("===================================")

# --- Mode ---
mode = input("\nChoose mode (1 = Single Player, 2 = Two Players): ").strip()
player1 = input("Enter Player 1 name: ").strip()

if mode == "2":
    player2 = input("Enter Player 2 name: ").strip()
else:
    player2 = None

# --- Timer (30–45 seconds) ---
base_time = 30
extra_time = min(len(word) * 2, 15)
time_limit = base_time + extra_time

start_time = time.time()

print("\n📚 Possible Words:")
print(", ".join(word_bank))
print("===================================")

current_player = player1


# ================= SCORE ENGINE =================
def apply_score(player, mode, player1, player2,
                score_p1, score_p2,
                streak_p1, streak_p2,
                base_points, streak_increase=True):

if mode == "2":
        if player == player1:
            multiplier = streak_p1
            score_p1 += base_points * multiplier
            if streak_increase:
                streak_p1 += 1
            streak_p2 = 1
else:
            multiplier = streak_p2
            score_p2 += base_points * multiplier
            if streak_increase:
                streak_p2 += 1
            streak_p1 = 1
else:
        multiplier = streak_p1
        score_p1 += base_points * multiplier
        if streak_increase:
            streak_p1 += 1

return score_p1, score_p2, streak_p1, streak_p2


# ================= GAME LOOP =================
while attempts > 0:

elapsed_time = time.time() - start_time
    remaining_time = int(time_limit - elapsed_time)

if remaining_time <= 0:
        print("\n⏳ TIME'S UP!")
        print("The word was:", word)
        break

 print(f"\n⏳ Time Left: {remaining_time} seconds")
    print("Current word:", ' '.join(guessedWord))
    print("Guessed letters:", ' '.join(guessed_letters))

if mode == "2":
        print(f"Score -> {player1}: {score_p1} | {player2}: {score_p2}")
        print(f"🔥 Streaks -> {player1}: {streak_p1} | {player2}: {streak_p2}")
        print("🎯 Current Player:", current_player)
else:
        print(f"Score: {score_p1}")
        print(f"🔥 Streak: {streak_p1}")

guess = input("Enter a letter or the full word: ").lower().strip()

 active_player = current_player
    
# --- FULL WORD ---
if len(guess) == len(word) and guess.isalpha():

 if guess == word:
            score_p1, score_p2, streak_p1, streak_p2 = apply_score(
                active_player, mode, player1, player2,
                score_p1, score_p2,
                streak_p1, streak_p2,
                50, True
            )
print("\n🎉 Correct! The word was:", word)
            break

else:
            attempts -= 1

if mode == "2":
                if active_player == player1:
                    streak_p1 = 1
else:
                    streak_p2 = 1
else:
                streak_p1 = 1

print("❌ Wrong word guess! Attempts left:", attempts)

 # --- INPUT VALIDATION ---
elif len(guess) != 1 or not guess.isalpha():
        print("⚠️ Enter a single letter or full word.")
        continue

elif guess in guessed_letters:
        print("⚠️ Already guessed that letter.")
        continue

# --- LETTER GUESS ---
else:
        guessed_letters.append(guess)

 if guess in word:
            for i in range(len(word)):
                if word[i] == guess:
                    guessedWord[i] = guess

 score_p1, score_p2, streak_p1, streak_p2 = apply_score(
                active_player, mode, player1, player2,
                score_p1, score_p2,
                streak_p1, streak_p2,
                5, True
            )

 print("🔥 Correct guess!")

else:
            attempts -= 1

if mode == "2":
                if active_player == player1:
                    streak_p1 = 1
                else:
                    streak_p2 = 1
            else:
                streak_p1 = 1

 print("❌ Wrong letter! Attempts left:", attempts)

 # --- WIN CONDITION ---
if '_' not in guessedWord:
        print("\n🎉 Word completed:", word)
        break

# --- SWITCH PLAYER ---
 if mode == "2":
        current_player = player2 if current_player == player1 else player1


# ================= END GAME =================
print("\n===================================")
print("🏆 FINAL SCORE")

if mode == "2":
    print(player1, ":", score_p1)
    print(player2, ":", score_p2)

if score_p1 > score_p2:
        print("🥇 Winner:", player1)
    elif score_p2 > score_p1:
        print("🥇 Winner:", player2)
    else:
        print("🤝 It's a tie!")
else:
    print(player1, ":", score_p1)

print("===================================")
