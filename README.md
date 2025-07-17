# Workflow Engine

This is a minimal backend service for defining and executing configurable workflows using a finite state machine model. The service is built using C# and ASP.NET Core minimal APIs, and stores all workflow and instance data in memory.

The engine enables users to define workflows consisting of named states and actions (transitions), start instances from those workflows, and move those instances through transitions with basic rule validation.

---

## Table of Contents
- [Overview](#overview)
- [Key Concepts](#key-concepts)
- [Features](#features)
- [Quickstart](#quickstart)
- [API Summary](#api-summary)
- [Project Structure](#project-structure)
- [Limitations](#limitations)
- [Assumptions](#assumptions)
- [Future Improvements](#future-improvements)

---

## Overview

This project provides a lightweight service that behaves like a state machine engine. Users can:
- Define workflows consisting of states and transitions
- Start instances from those workflow definitions
- Execute transitions on instances while enforcing basic validity checks

Designed for simplicity, this version does not use a database or external storage, making it easy to run and test locally.

---

## Key Concepts

- **State**: Represents a position in the workflow. Each state has an ID and flags such as `isInitial`, `isFinal`, and `enabled`.
- **Action (Transition)**: Moves the instance from one or more allowed source states (`fromStates`) to a single target state (`toState`). Each action can be enabled or disabled.
- **Workflow Definition**: A collection of states and actions. Exactly one state must be marked as `isInitial`.
- **Workflow Instance**: A runtime entity tracking the current state of a workflow, along with a basic history of transitions.

---

## Features

- Add and retrieve workflow definitions with custom state-action configurations.
- Start new workflow instances that begin at the initial state.
- Transition instances from one state to another using defined and valid actions.
- In-memory data persistence (suitable for quick tests and demos).

Some validation (e.g., rejecting transitions from final states or checking for undefined target states) is partially implemented and may require further refinement.

---

## Quickstart

1. Ensure you have the .NET 8 SDK installed on your machine.
2. Clone the repository and navigate into the project directory.
3. Run the application:

```bash
dotnet run
## API Summary

| Method | Route                          | Description                              |
|--------|--------------------------------|------------------------------------------|
| POST   | `/flowcharts`                 | Create a new workflow definition         |
| POST   | `/sessions/{chartKey}`        | Start a new workflow instance            |
| POST   | `/sessions/{token}/move`      | Execute a transition on the given instance |

