---
AUTOGENERATED: DO NOT EDIT FILE DIRECTLY
title: Put Near
---


# Put Near

### Description

The agent is instructed through a textual string to pick up an object and
place it next to another object. This environment is easy to solve with two
objects, but difficult to solve with more, as it involves both textual
understanding and spatial reasoning involving multiple objects.

### Mission Space

"put the {move_color} {move_type} near the {target_color} {target_type}"

{move_color} and {target_color} can be "red", "green", "blue", "purple",
"yellow" or "grey".

{move_type} and {target_type} Can be "box", "ball" or "key".

### Action Space

| Num | Name         | Action            |
|-----|--------------|-------------------|
| 0   | left         | Turn left         |
| 1   | right        | Turn right        |
| 2   | forward      | Move forward      |
| 3   | pickup       | Pick up an object |
| 4   | drop         | Drop an object    |
| 5   | toggle       | Unused            |
| 6   | done         | Unused            |

### Observation Encoding

- Each tile is encoded as a 3 dimensional tuple:
    `(OBJECT_IDX, COLOR_IDX, STATE)`
- `OBJECT_TO_IDX` and `COLOR_TO_IDX` mapping can be found in
    [gym_minigrid/minigrid.py](gym_minigrid/minigrid.py)
- `STATE` refers to the door state with 0=open, 1=closed and 2=locked

### Rewards

A reward of '1' is given for success, and '0' for failure.

### Termination

The episode ends if any one of the following conditions is met:

1. The agent picks up the wrong object.
2. The agent drop the correct object near the target.
3. Timeout (see `max_steps`).

### Registered Configurations

N: number of objects.

- `MiniGrid-PutNear-6x6-N2-v0`
- `MiniGrid-PutNear-8x8-N3-v0`