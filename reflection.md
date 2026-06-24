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

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
