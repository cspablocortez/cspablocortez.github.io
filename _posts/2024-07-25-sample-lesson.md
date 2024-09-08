---
title: Sample Lesson
author: Pablo E. Cortez
layout: lesson
hidden: true
published: false
permalink: /test-lesson
---

This is a sample interactive lesson.

Write `print("Hello")` in the following input box to continue.

<div style="visibility: visible;" class="lesson" data-answer="print(&quot;Hello&quot;)">
<input type="text" class="userInput" placeholder="Enter your code here">
        <button class="checkBtn" onclick="checkAnswer(this)"></button>
        <p class="feedback">
        </p>

</div>

The previous command is used to print a message to the screen. 
Next, let's update it to say `print("Hello, World!")`.

<div class="lesson" data-answer="print(&quot;Hello, World!&quot;)">
<input type="text" class="userInput" placeholder="Enter your code here">
        <button class="checkBtn" onclick="checkAnswer(this)"></button>
        <p class="feedback">
        </p>

</div>

Now that it's getting repetitive, we'll try writing larger commands. We
are going to write a **function** that greets someone by name. To do this,
we need to create a function definition:

```python
def greet(name):
...
```

This is a function called `greet` that accepts one **parameter** called `name`. 
Whatever value we put inside `name`, we can greet it by adding the following
code to the **function body**.

```python
def greet(name):
    print("Hello, " + name + "!")
```

Using the `print()` function and the concatenation operator (`+`), we can link text characters, from words to symbols and even empty space, like the one after the comma. These text characters are known as the `String` value type. 

Write a function called `goodbye` that accepts one parameter called `name`. If the value of name was `Aiden`, 
the function should output `"Goodbye, Aiden!"`.


<div class="lesson" data-answer="def goodbye(name):&#10;    print(&quot;Goodbye, &quot; + name + &quot;!&quot;)">
<input type="text" class="userInput" placeholder="Enter your code here" style="height: 128px">
        <button class="checkBtn" onclick="checkAnswer(this)"></button>
        <p class="feedback">
        </p>

</div>









