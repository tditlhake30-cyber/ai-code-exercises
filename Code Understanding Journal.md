# Code Understanding Journal – Task Manager

## Overview

For this exercise I explored a Task Manager codebase without changing any code.  
The goal was to understand how the application works by reading the files and using AI prompts to guide my thinking.

At first the codebase looked confusing, but by focusing on one feature at a time I slowly started to understand how the system works.

---

# Part 1 – Understanding Task Creation and Status Updates

## Files I Found Important

While exploring the code, these files seemed most related to creating and updating tasks:

- `models.py`
- `app.py`
- `storage.py`
- `cli.py`

## What I Learned

Task creation mainly happens in the **TaskManager class** in `app.py`.

When a task is created:

1. The user enters a command in the CLI.
2. The CLI calls a function in `TaskManager`.
3. A `Task` object is created using the `Task` model.
4. The task is saved using `TaskStorage`.
5. The data is written into `tasks.json`.

### Execution Flow (simple view)

CLI command → TaskManager → Task model → Storage → JSON file

Status updates follow a similar flow, except the task is retrieved first and then updated before saving again.

---

# Part 2 – Understanding Task Priorities

## My Initial Understanding

At first I thought priority was just a number stored in the task.

After reading more, I realized it is handled using **TaskPriority**, which is an enum.

This means priorities are predefined values instead of random numbers.

Examples:

- Low
- Medium
- High

## What I Learned from the Guided Questions

The guided questions helped me notice that:

- Priority is converted into a `TaskPriority` object
- Tasks can be filtered by priority
- Priority is part of the task model and used throughout the system

One misconception I had was thinking priority was only used when creating tasks, but it is also used when listing or filtering tasks.

---

# Part 3 – Data Flow When Completing a Task

When a task is marked as complete, the following happens:

1. A CLI command triggers the action.
2. `TaskManager` retrieves the task from storage.
3. The task status changes to **DONE**.
4. The completion time is recorded.
5. The updated task list is saved back to `tasks.json`.

## Simple Data Flow

User Command  
↓  
CLI  
↓  
TaskManager  
↓  
Task Model  
↓  
Storage  
↓  
tasks.json

## Possible Points of Failure

Some possible problems could be:

- Task ID does not exist
- Storage file cannot be read or written
- Incorrect status value passed into the system

---

# Reflection

This exercise helped me understand how to approach an unfamiliar codebase.

Things that helped me the most:

- Looking at **file names first instead of reading all the code**
- Focusing on **one feature at a time**
- Using **AI prompts to confirm my understanding**

At first I felt lost, but once I understood the main components (Task, Storage, TaskManager) the rest of the system started making more sense.

If I were to continue exploring this project, I would try running the application locally and tracing how commands move through the system.

---

# What I Learned

From this exercise I learned that understanding a codebase does not require reading everything immediately.  
Breaking the system into smaller parts and asking focused questions made it much easier to understand how the application works.
