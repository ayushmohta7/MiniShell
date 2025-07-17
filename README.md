# Buggy Workflow Engine

This project implements a **minimal configurable workflow engine** (state-machine API) in C# using ASP.NET Core minimal APIs. It allows defining workflows with states and transitions (actions), starting workflow instances, and moving them through allowed transitions.

---

## 📑 Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Quickstart](#quickstart)
- [API Summary](#api-summary)
- [Structure](#structure)

---

## 🧾 Overview

The workflow engine supports basic state machine operations such as:
- Defining states and actions (transitions)
- Starting workflow instances
- Executing actions to move instances between states

Each action has `fromStates`, a `toState`, and an enabled flag. A workflow must begin with an initial state.

---

## ✨ Features

- Add and retrieve **workflow definitions**
- Create **workflow instances** from definitions
- Transition workflow instances using defined actions
- In-memory storage (no DB)

⚠️ Some validation and edge cases may not be fully handled yet (e.g., action state mismatches, final-state checks).

---

## ⚙️ Quickstart

### Run the server:
```bash
dotnet run
