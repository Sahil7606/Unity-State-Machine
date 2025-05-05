# Unity-State-Machine
A modular hierarchical state machine I created in Unity that can be used for pretty much anything involving states

---

## 🎯 Overview

The system consists of:

### 1. `SMCore` — The Brain

- Abstract class that inherits from `MonoBehaviour`
- Meant to be attached to a GameObject
- Holds references to important components
- Owns the `StateMachine` object
- Implements Unity lifecycle methods: `Start()`, `Awake()`, `Update()`, `FixedUpdate()`
- Handles global behaviors that persist regardless of state

---

### 2. `State` — The Behavior Units

- Abstract class that defines individual behaviors
- Inherits from `MonoBehaviour`
- Each state must implement standard methods:
  - `Enter()`
  - `Exit()`
  - `Update()`
  - (Optionally: `FixedUpdate()`, `LateUpdate()`, etc.)
- The `SMCore` controls when these methods are called
- States access shared components via their owning core

---

### 3. `StateMachine` — The Controller

- Regular C# class (does **not** inherit from `MonoBehaviour`)
- Tracks:
  - `currentState`
  - `previousState`
- Handles transition logic using:
  - `Set(State newState)`
- Optional: can expose events for transition hooks

---

## ✅ Benefits

- Clean separation of concerns
- Easily testable and debuggable
- Encourages modular design
- Works with or without nested (hierarchical) states

---

## 🔧 Getting Started

1. Add `SMCore`, `State`, and `StateMachine` to your Unity project.
2. Create new states by inheriting from `State.cs`.
3. Attach a script inheriting from `SMCore.cs` to a GameObject.
4. In your core, override `GetInitialState()` and optionally define logic in `StateUpdate()`.

---

## 🔄 See It in Action

This state machine system is used in [Platformer-Metriodvania-Game](https://github.com/Sahil7606/Platformer-Metroidvania-Game), a large project that I am currently taking a break from due to mild burnout.

I used the state machine to implement movement for the player
- See Assets/Scripts/Player/State Machines/TraversalStateMachine.cs for implementation of the core
- See Assets/Scripts/Player/Behaviors for the implementation of the states
---

## 📜 License

MIT License — free to use and modify for personal or commercial projects.