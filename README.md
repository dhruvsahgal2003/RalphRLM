
We built an autonomous coding loop that stays effective on large codebases without blowing up context or cost.

Ralph (iteration loop) runs in short, repeatable cycles: it plans the next smallest step, executes it, commits progress, and repeats until the goal is reached. Each iteration is designed to be “stateless” from the model’s perspective—no long chat history needed.

RLM (Recursive Language Model) + external memory makes that possible by moving long‑term state out of the model context and onto disk. The system maintains persistent memory (architecture, progress, decisions, errors) and a lightweight code index, then rebuilds a constant‑size context for every iteration by pulling only the most relevant snippets. This keeps prompts small and predictable, so cheap models can iterate for hours or days.

To keep the loop reliable, we add guardrails (reject empty/touch‑only work) and an automatic verify step (auto‑detect tests/lint/build and fail the iteration if verification fails). The result is a cost‑effective, self‑correcting development workflow where small models can continuously improve their own outputs without running out of context.

Quick Start
Install the extension from the VSIX file
Create your PRD/spec file (see Task File Format below)
Use Planning mode in Antigravity to help create a proper PRD with discrete tasks
Open the Ralph Loop sidebar via the Activity Bar icon
Configure your session in the sidebar:
Select task file (default: PRD.md)
Set progress file (default: progress.txt)
Choose mode and model
Set max iterations
Start the loop using the play button in the sidebar


Task File Format
The task file is read-only - the agent never modifies it. Write a proper PRD or specification document, but organize it into discrete, actionable tasks so the agent can identify what to work on next by cross-referencing progress.txt.

# PRD: User Management System

## Overview
Build a user management system with authentication, profiles, and admin controls.

## Task 1: Authentication
Implement JWT-based authentication with login/logout endpoints.
- POST /api/auth/login
- POST /api/auth/logout
- Token refresh mechanism

## Task 2: User Profiles
Create user profile CRUD operations.
- GET/PUT /api/users/:id
- Profile picture upload
- Email verification

## Task 3: Admin Dashboard
Build admin interface for user management.
- List all users with pagination
- Suspend/activate accounts
- View user activity logs
