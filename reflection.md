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

The secret number wasn't changing in the original app. It only changes when the user refreshes the page or manages to start a new game. (TF Note: This might be a confusing question since the number doesn't just change for no reason.) Streamlit rerunning causes the script to be ran from top to bottom again when the user interacts with some part of the interface, but state data is preserved to avoid completely resetting data that's important for the browser sessions, such as maintaining a score within one browser session. This session data preserved by Streamlit is wiped when refreshing the page entirely, but not when interacting with a button.

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.

I'd certainly keep testing individual changes if I allow AI to write those changes by itself. While I prefer to ask questions and check its logic _before_ I go with the changes to decide whether I want to go through with them, I think that using AI in small chunks and letting it make changes on its own for isolated parts of the code is very useful. It makes things more efficient. I think that AI is good at isolating code rather than making entire applications easily. It should not be used for one-and-done development, and should always be double-checked. However, using AI as an assistant and collaborator can greatly increase quality of the code and project.

## TF Submission: Justin Dingeman

1. The core concept students needed to understand
   - Students should understand how to isolate parts of the code before asking AI to explain what is happening and/or why bugs are occurring. The students should be able to identify bugs in an application as a user, and then use AI as a collaborator to debug and figure out why a specific part of the code might be causing problems.
2. Where students are most likely to struggle
   - If students have never had to develop in multi-part applications, it may become overwhelming with several files, the terminal, and the chatbot all open at the same time to gather their bearings. They also may struggle to understand Streamlit syntax and how it translates into a front end. Navigating the codebase might get confusing if they don't know how the UI is made. They also may struggle with following along with the AI as it thinks because it does it so fast and will often give itself a lot of context to fix a problem, and then just ask the developer wants to allow changes to a file without obviously showing what it's deciding to do.
3. Where AI was helpful vs misleading
   - The AI does not have full context or a user story necessarily, so it'll say that something is working when it's not actually intended. An example is when the AI says that every other attempt is "correctly" evaluated despite the app not actually correctly working every other attempt. It was helpful in developing tests and explaining why certain bugs were occurring and how they should be addressed.
4. One way they would guide a student without giving the answer
   - First I'd ask the student where they're stuck, and then have them review what they understand before jumping into something they don't. For this project, they may be tempted to tackle the whole thing in one fell swoop but they will quickly get overwhelmed. So, I'd tell them to slow down and isolate 1 issue, have them explain what the app _should_ do, what the app is _actually_ doing, and where they think the error may be occurring. Then I'd remind them again to **isolate** the issue, especially when asking the AI to help.
