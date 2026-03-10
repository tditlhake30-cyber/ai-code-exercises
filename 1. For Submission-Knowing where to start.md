# Task Manager Codebase Exploration (Summary)

## Initial Understanding

When I first opened the project, I mostly looked at the file names. My first guess was that it is a **simple command line task manager written in Python**.

Some important files I noticed were:

- `models.py`
- `storage.py`
- `app.py`
- `cli.py`
- `tasks.json`

My early assumptions were:

- `models.py` defines what a task looks like
- `storage.py` saves and loads tasks
- `app.py` contains the main task logic
- `cli.py` handles commands from the terminal
- `tasks.json` stores the data

At this point I was mostly guessing based on the names.

---

## Final Understanding

After exploring more and using AI prompts, my understanding improved.

The project seems to be organized into simple layers:

**CLI Layer**  
Handles commands from the user.

**Application Logic**  
`app.py` manages creating, updating, and listing tasks.

**Domain Model**  
`models.py` defines the main entities like `Task`, `TaskStatus`, and `TaskPriority`.

**Storage Layer**  
`storage.py` saves and retrieves tasks from `tasks.json`.

This separation helped me understand how the parts of the system work together.

---

## Insights from the AI Prompts

### Project Structure Prompt
This helped me focus on the **roles of different files** instead of trying to understand every line of code.

### Feature Location Prompt
This helped me figure out **where new features should be added**, mainly in the application logic instead of directly in storage.

### Domain Model Prompt
This helped me identify the **main entities** used in the program:

- `Task`
- `TaskStatus`
- `TaskPriority`

Understanding these made the code easier to follow.


---

## Strategies for Understanding New Code

From this exercise I learned a few useful strategies:

- Start by looking at the **project structure first**
- Identify the **main models or entities**
- Search the code using **keywords**
- Use AI prompts to **clarify parts that are confusing**

These steps helped me go from not understanding the project at all to having a basic idea of how it works.
