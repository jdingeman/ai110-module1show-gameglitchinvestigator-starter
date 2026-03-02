# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the secret number kept changing" or "the hints were backwards").

The game gives the hint that is opposite to what it should be - for example, if the secret is 19 and the input is 18, it will tell the user to "Go LOWER!". The history also does not keep properly keep track of the attempts made, nor do the attempts decrement correctly when submitting a guess. Clicking "New Game" does not actually reset the game, it says stuck on "Game over. Start a new game to try again." The number of attempts written under "Make a guess" does not match that provided under the difficulty settings.

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

I am using Claude Code integrated into VS code.

Correct: It was correct in that every odd attempt is being evaluated as an integer and every even attempt is being evaluated as a string.
Misleading: It's misleading in that it states every odd attempt the "game works fine" and evaluates correctly when it actually doesn't. The first attempt using a value will result in the hint telling the user to do the opposite of what they should do (i.e. if the secret is 77 and the user inputs 75 on the first attempt, it still hints to go lower).

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

I would decide whether a bug was actually fixed by acting as the user for the specific scenario that would cause the bug. For example, if the secret is 50, and I input 49, I check to make sure that the corrections made do indeed result in the app telling the user "Go HIGHER" instead of "Go LOWER". Claude helped me design the tests for checking the ranges based on the selected difficulty and in initializing the pytest requirements to allow me to run pytest in the terminal.

---

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.
- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
- What change did you make that finally gave the game a stable secret number?

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
