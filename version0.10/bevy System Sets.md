---
aliases:
 - bevy System Sets
 - System Sets
tags:
 - 
---

# [[bevy]] System Sets
- old version, possibly outdated https://bevy-cheatbook.github.io/programming/system-sets.html

# Creating
- source: https://github.com/bevyengine/bevy/blob/main/benches/benches/bevy_ecs/scheduling/schedule.rs

```rust
#[derive(SystemSet, Debug, Clone, Copy, PartialEq, Eq, Hash)]
struct NumSet(usize);

#[derive(SystemSet, Debug, Clone, Copy, PartialEq, Eq, Hash)]
struct DummySet;
```

# Adding [[bevy systems]] to sets

```rust
let mut app = App::new();
app.add_system(empty_system.in_set(DummySet));

let mut sys = empty_system.in_set(NumSet(1)).before(DummySet);
let mut sys2 = empty_system.in_set(NumSet(2)).after(DummySet);                    

app.add_system(sys);
app.add_system(sys2);
```