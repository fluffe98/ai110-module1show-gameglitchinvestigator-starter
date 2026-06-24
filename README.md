# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable. 

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ Your Mission

1. **Play the game.** Open the "Developer Debug Info" tab in the app to see the secret number. Try to win.
2. **Find the State Bug.** Why does the secret number change every time you click "Submit"? Ask ChatGPT: *"How do I keep a variable from resetting in Streamlit when I click a button?"*
3. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
4. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!

## 📝 Document Your Experience

- [ ] Describe the game's purpose. : The game is a number guessing game where the player tries to guess a secret number within a limited number of attempts. The game gives hints after each guess telling the player to go higher or lower.
- [ ] Detail which bugs you found.
1. Hints were backwards — Go Higher showed when should say Go Lower
2. Hard mode was easier than Normal (range 1-50 vs 1-100)
3. Secret number was being converted to text on even attempts 
   causing completely wrong hint comparisons
4. Score was going negative on wrong guesses
5. Decimal numbers were accepted silently
6. Secret number was visible in Developer Debug Info panel
- [ ] Explain what fixes you applied.
1. Removed the even/odd attempt logic that converted secret to text
2. Swapped Go HIGHER and Go LOWER messages in check_guess function
3. Changed Hard difficulty range from 1-50 to 1-200
4. Moved all game logic functions into logic_utils.py
5. Updated app.py to import functions from logic_utils.py

## 📸 Demo Walkthrough

Describe your fixed game in numbered steps so a reader can follow along without watching a video:

1. User opens the game in browser via streamlit run app.py
2. User selects difficulty — Easy (1-20), Normal (1-100), or Hard (1-200)
3. User enters a guess of 40 — game returns "Go HIGHER" correctly
4. User enters a guess of 70 — game returns "Go LOWER" correctly
5. Score updates correctly only when player wins
6. User guesses the correct number — game shows Congratulations
7. Player clicks New Game to reset and play again


**Screenshot** *(optional)*: <!-- Insert a screenshot of your fixed, winning game here -->

## 🧪 Test Results
## 🧪 Test Results

​```
(.venv) PS ...\ai110-module1show-gameglitchinvestigator-starter> pytest
=================================================================================================
test session starts
=================================================================================================
platform win32 -- Python 3.13.13, pytest-9.0.3
collected 5 items

tests\test_game_logic.py .....                                                            [100%]

============================ 5 passed in 0.04s ============================
​```
```
# Paste your pytest output here, e.g.:
# pytest tests/
# ========================= X passed in 0.XXs =========================
```

## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, describe the Enhanced UI changes here — a screenshot is optional]
