# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- the Hard difficulty was much easier than the medium difficulty, range of hard was 1-50 vs the range for medium was 1-100.
- in the same space teh max amount of tries are also different for each, easy has 8 attempts, medium has 8 tries and hard has 5 tries. 

**Bug Reproduction Log**

Document at least 3 bugs you found. Add rows as needed.

| Input | Expected Behavior | Actual Behavior | Console Output / Error |
|-------|-------------------|-----------------|------------------------|
| Input | Expected Behavior | Actual Behavior | Console Output / Error |
|-------|-------------------|-----------------|------------------------|
| Guessed 50, secret was 23 | Should say "Go Lower" since 50 is bigger than 23 | Said "Go Higher" — completely wrong direction | none |
| Typed 101 | Game should reject it, say "Enter between 1 and 100" | Game accepted 101 and kept playing normally | none |
| Typed 99.5 and 99.9 | Game should only accept whole numbers | Accepted decimals, caused impossible guessing loop | none |
| Opened Developer Debug Info dropdown | Should not reveal the secret number | Clearly showed "secret: 23" — player can see the answer | none |
| Clicked Hard difficulty | Should have bigger range than Normal, like 1 to 500 | Hard = 1 to 50, Normal = 1 to 100, Hard is actually easier | none |
| Kept guessing wrong answers | Score should stay positive | Score went into negative numbers | none |

---

## 2. How did you use AI as a teammate?
I used Claude (claude.ai) as my AI coding assistant throughout this project.

**Correct AI Suggestion:**
Claude correctly identified that the hints were backwards in the check_guess function. It suggested swapping "Go HIGHER" and "Go LOWER" messages so that when a guess is too high it tells the player to go lower and vice versa. I verified this by running the game and testing with a known secret number from the debug panel.

**Incorrect/Misleading AI Suggestion:**
Claude initially suggested using the echo command to create conftest.py which created a file with null bytes causing a SyntaxError. I caught this because pytest gave an error saying "source code string cannot contain null bytes." I had to reject that approach and use a Python command instead to create the file correctly.


---

## 3. Debugging and testing your fixes

I decided a bug was really fixed when two things happened — first the game behaved correctly when I played it manually, and second when all 5 pytest tests passed with no errors.
I ran pytest after writing 5 automated tests in test_game_logic.py. The tests checked that check_guess returns "Too High" when guess is bigger than secret, "Too Low" when guess is smaller, and "Win" when they match. All 5 tests showed green dots meaning they passed.
Claude helped me understand that check_guess returns two values (outcome and message) not just one. When I first wrote the tests they were failing because I was only checking one return value. Claude explained I needed to write outcome, message = check_guess() to capture both values.

---

## 4. What did you learn about Streamlit and state?

- Streamlit reruns means every time a user clicks a button or types something, the entire Python script runs again from top to bottom.This is different from normal programs that just wait for input.
Session state is like a notebook that Streamlit keeps between these reruns. Without it, every time the page reruns it would forget the secret number, the score, and the guess history. Think of it like a waiter writing your order down so they remember it even if they walk away and come back.

---

## 5. Looking ahead: your developer habits

One habit I want to reuse is running pytest after every fix to verify my changes actually work instead of just assuming they do. Writing tests first makes debugging much faster and more reliable.

Next time I work with AI on a coding task I would ask it to explain WHY it is making a suggestion, not just what to change. Sometimes Claude gave me code fixes without fully explaining the reason and I had to ask follow up questions to understand.

This project changed how I think about AI generated code because I used to assume AI code would just work correctly. Now I know AI can introduce subtle bugs like flipped comparison operators or wrong difficulty ranges that look correct at first glance but break the game completely.