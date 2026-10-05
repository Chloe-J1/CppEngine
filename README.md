# C++ Engine - Mrs Pacman

[![CMake](https://github.com/Chloe-J1/Prog4Engine/actions/workflows/cmake.yml/badge.svg)](https://github.com/Chloe-J1/Prog4Engine/actions/workflows/cmake.yml)
[![Emscripten](https://github.com/Chloe-J1/Prog4Engine/actions/workflows/emscripten.yml/badge.svg)](https://github.com/Chloe-J1/Prog4Engine/actions/workflows/emscripten.yml)
[![GitHub](https://img.shields.io/badge/GitHub-Prog4Engine-181717?logo=github)](https://github.com/Chloe-J1/Prog4Engine)

In this project, I build a game engine from the ground up and recreated *Mrs Pacman* with it. 
The game has three game modes:
1. Single player: standard game mode
2. Co-op: two players control their pacman and work together against the ghosts
3. Versus: one player is Mrs Pacman and the other can play as a ghost

The game supports both keyboard and controller input.

## Controls
### UI

| Action | Keyboard | Controller |
|---|---|---|
| Select different button | Arrow keys | D-pad |
| Press button | Space | South button |

### Gameplay

| Action | Keyboard | Controller |
|---|---|---|
| Move up | W | D-pad up |
| Move down | S | D-pad down |
| Move left | A | D-pad left |
| Move right | D | D-pad right |

### Hotkeys

| Action | Key |
|---|---|
| Skip level | F1 |
| Mute audio | F2 |

## Engine design choises
Most of the architecture choises are inspired by Bob Nystrom's book *Game Programming Patterns*. The most important ones I decided to implement are the following.

```Component``` The core structure of the engine relies on game objects to which you can attach components. The intent of this is as follows: Allow a single entity to span multiple domains without coupling the domains to each other. (Quote from Bob Nystrom's book *Game Programming Patterns*)<br>
```State``` Complex behavior is split into separate states rather than handled in one place. The state controls the needed behavior at that moment and has the possibility to switch to a new state.<br>
```Event queue``` A central event bus is used to send messages to the subscribed components, decoupling the sender from the receiver. Subscribers to the event queue can react to changes without direct dependency on the sender.<br>
```Command``` The command pattern is used to bind certain actions to an input event. This separates the executed behavior from the button that triggers the behavior.<br>
```Service locator``` The sound system is implemented as a service, making it easy to swap between different sound systems without having to change code that uses the sound system.
