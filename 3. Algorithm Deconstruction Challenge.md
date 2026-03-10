# Algorithm Deconstruction Challenge – Task Priority Sorting

## Chosen Algorithm

I chose the **Task Priority Sorting Algorithm**.

The reason I chose this one is because it looked easier to follow than the parser or task syncing one, but it still had enough logic to break down and learn from.

---

# What the Algorithm Does

This algorithm gives each task a **score** based on different factors, then sorts the tasks from **most important to least important**.

So instead of only looking at priority like Low or High, it combines a few things:

- task priority
- due date
- task status
- tags
- last updated time

Then it uses the final score to decide which tasks should appear first.

---

# Main Functions

## `calculate_task_score(task)`

This function gives one task a number score.

It checks different parts of the task and adds or subtracts points.

### How it works step by step

### 1. Start with base priority
Each priority level has a weight.

- Low = 1
- Medium = 2
- High = 4
- Urgent = 6

That weight is multiplied by 10.

So for example:

- Low starts at 10
- Medium starts at 20
- High starts at 40
- Urgent starts at 60

---

### 2. Add points for due date
If the task has a due date, the algorithm checks how close it is.

- overdue = `+35`
- due today = `+20`
- due in 2 days = `+15`
- due in 7 days = `+10`

This means tasks due sooner get pushed higher.

---

### 3. Reduce points for status
If the task is already done or in review, the score goes down.

- Done = `-50`
- Review = `-15`

This makes sense because completed tasks should not stay near the top.

---

### 4. Add points for important tags
If the task has tags like:

- blocker
- critical
- urgent

it gets `+8`.

So the algorithm treats those tags as a signal that the task is important.

---

### 5. Add points if recently updated
If the task was updated very recently, it gets `+5`.

This seems like a way of saying the task is still active or relevant.

---

## `sort_tasks_by_importance(tasks)`

This function sorts all tasks using the scores from `calculate_task_score(task)`.

It calculates the score for each task, then sorts from highest score to lowest.

---

## `get_top_priority_tasks(tasks, limit=5)`

This function gets only the top few tasks.

So if the limit is 5, it returns the 5 highest scoring tasks.

---

# Simple Flow Diagram

```text
Task list
   ↓
Calculate score for each task
   ↓
Compare scores
   ↓
Sort highest to lowest
   ↓
Return sorted list or top N tasks
