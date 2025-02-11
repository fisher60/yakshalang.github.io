---
title: Additional features for structs
author: Bhathiya Perera
layout: '../../layouts/YamaPostLayout.astro'
---

# YAMA 0007 - Additional features for structs

- Author(s): Bhathiya Perera
- Status   : In Progress

Structures are at the moment can be created as follows

```yaksha
@onstack
class Banana:
    color: int
    origin: int

# Orange is a heap allocated class
class Orange:
    color: int
    origin: int
```

## Item 1 - Allocate single object on heap

```yaksha
a: Ptr[Banana] = make("Banana")

b: Orange = make("Orange")
```

## Item 2 - Create structures or classes ✅

```yaksha
a: Banana = Banana {color: YELLOW, origin: SRI_LANKA}
```

```c
struct Banana a = (struct Banana){.color = YELLOW, .origin = SRI_LANKA};
```

```yaksha
b: Orange = Orange {color: ORANGE, origin: SOUTH_AFRICA} 
```

```c
struct Orange* _temp = calloc(1, sizeof(struct Orange));
_temp->color  = ORANGE;
_temp->origin = SOUTH_AFRICA;

struct Orange* b = _temp;
```

## Item 3 - Introduce `struct` keyword, desugar to `@onstack class` ✅

```yaksha
struct Banana:
    color: int
    origin: int
```