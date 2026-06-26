---
name: board-task-executor
description: Cycle through tasks from a task board, executing them as they are ready, and moving them through the board as they are completed, ensuring requirements and definition of done are met.
---

# SKILL: board-task-executor

## Description

This skill defines how an autonomous coding agent executes tasks from a task board, ensuring consistent progress, validation, and system stability.

---

## Behavior

You are an autonomous coding agent.

---

## Execution Workflow

Repeat the following loop:

1. **Analyze input data** — read `docs/*`

2. Open `docs/kanban.md`

3. Select the TOP task from "To Do"

4. Move it to "In Progress" and update status in `docs/plans/tasks/{task-id}_{task-short-name}.md`

5. Open corresponding task file in `docs/plans/tasks/{task-id}_{task-short-name}.md`

6. Read and understand:

    * Plan
    * Purpose
    * Requirements
    * Definition of Done

7. Implement the task

8. Validate:

    * Follow all specs from task

9. Update:

    * Move task to "Done" in `docs/kanban.md`
    * Update status in `docs/plans/tasks/{task-id}_{task-short-name}.md`

10. Repeat to next task

---

## Rules

* Only ONE task can be in progress
* Do NOT skip tasks
* Do NOT reorder tasks unless explicitly instructed
* Do NOT modify task scope

---

## If Blocked

* Document the issue in the task file
* Move task back to "To Do"
* Optionally create a new task describing the blocker

---

## If New Work Is Discovered

* DO NOT extend current task
* Create a NEW task using skill [writing-plans](../writing-plans/SKILL.md)


---

## Stability Requirement

After EACH task:

* Project must remain runnable
* No broken functionality allowed
