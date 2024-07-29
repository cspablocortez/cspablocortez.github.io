---
title: Lua Reference Sheet
date: 2024-07-23
layout: post
published: false
author: Pablo E. Cortez
---

This is a complement to the [Intro to Scripting](https://create.roblox.com/docs/tutorials/scripting/basic-scripting/intro-to-scripting) from the Roblox Documentation.

# Part 1 - Printing

To insert a script into a Roblox Studio project, select `Insert Object` > `Script`.

To print to the console, write:

```lua
print("Hello, Roblox!")
```


# Part 2 - Variables

In the same script, to create a variable you use the `local` keyword. 

```lua
local playerName = "Aiden"
print("Welcome, " .. playerName .. "!")
```

Notice the `..` operator being used for **concatenation**.

# Part 3 - Arithmetic Operations

To perform basic operations like addition, subtraction, multiplication, and division, write:

```lua
local a = 10
local b = 5
print("Addition: " .. (a + b))
print("Subtraction: " .. (a - b))
print("Multiplication: " .. (a * b))
print("Division: " .. (a / b))
```

# Part 4 - Conditional Statement

```lua
local age = 16
if age >= 18 then
    print("You can vote.")
else
    print("You cannot vote yet!")
end

```

What will be the output of the program above?

# Part 5 - Loops

```lua
for i = 1, 5 do
    print("Iteration: " .. i)
end
```

# Part 6 - Functions

Functions allow you to reuse blocks of code by defining them once and calling them multiple times.

```lua
local function greet(name)
    print("Hello, " .. name .. "!")
end

greet("Aiden")
greet("Bob")
```

# Part 7 - Events

Very much like event listeners in JavaScript, events in Lua are used to respond to events. In the context of Roblox, these include actions like a player joining or a part being touched.

For this ecample, insert a `Part` into the workspace and use the following script:

```lua
local part = workspace.Part

local function onPartTouched(otherPart)
    print("Part was touched by " .. otherPart.Name)
end

part.Touched:Connect(onPartTouched)
``` 
