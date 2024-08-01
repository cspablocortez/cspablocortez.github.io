---
title: Web Development Review
author: Pablo E. Cortez
layout: lesson
published: true
permalink: /web-development-review
hidden: false
---

Some of the web development concepts we have reviewed in the past few lessons include:

- Static site generators
- Markdown
- YML
- CSS Flexbox
- Responsive Design


In the sections below you will find fill-in-the-blank text boxes. These will be **one word** responses.

<div style="text-align: center;">
        &mdash;&mdash;&mdash;
</div>

## Client Meeting

A client arrives at your web development firm asking if you can help him. His idea is to build a website where people can see his reviews of different video games.

The first thing you asked him is if he had a name for the site. He said not yet, but he definitely wants his `_______` to end with `.com`.

<div style="visibility: visible;" class="lesson" data-answer="domain">
<input type="text" class="userInput" placeholder="> ">
        <button class="checkBtn" onclick="checkAnswer(this)"></button>
        <p class="feedback">
        </p>

</div>

Next you want to know what kind of site he wants. You ask him what type of content he plans on hosting, and he says he needs a `_______` (*web* + *log*) where he will write reviews but also display game images, screenshots, maybe even upload walkthrough videos, guides, maps, and tutorials. He says he wants something like IGN but much lighter and faster.

<div style="visibility: visible;" class="lesson" data-answer="blog">
<input type="text" class="userInput" placeholder=">">
        <button class="checkBtn" onclick="checkAnswer(this)"></button>
        <p class="feedback">
        </p>

</div>

At this point you are pretty sure he wants a static site. Unlike a dynamic site, static sites have no databases or server-side processing. **A static site shows the same thing to every user.**

Since you have experience using the Jekyll static site generator, you tell the client you have just the right tool for the job, and after he thanks you for your time, you get to work. But first, you take the following quiz to review!

## Jekyll Quiz

Which command is used to create a new Jekyll site?

a) `jekyll new site_name`

b) `jekyll create site_name`

<div class="lesson" data-answer="a">
<input type="text" class="userInput" placeholder=">">
        <button class="checkBtn" onclick="checkAnswer(this)"></button>
        <p class="feedback">
        </p>
</div>

---

What does the command `jekyll serve` do?

a) Builds the site and outputs static files (this means converting Markdown to HTML)

b) Deletes the site

<div class="lesson" data-answer="a">
<input type="text" class="userInput" placeholder=">">
        <button class="checkBtn" onclick="checkAnswer(this)"></button>
        <p class="feedback">
        </p>
</div>

---

To build your site without serving it (this means making it available on an address like `localhost:4000`), which command should you use?

a) `jekyll start`

b) `jekyll build`

<div class="lesson" data-answer="b">
<input type="text" class="userInput" placeholder=">">
        <button class="checkBtn" onclick="checkAnswer(this)"></button>
        <p class="feedback">
        </p>
</div>

---

**True or False**

The command `jekyll doctor` helps you identify potential problems in your site configuration, namely for URL Conflicts, errros with your permalinks, and deprecation warnings.

a) True

b) False

<div class="lesson" data-answer="a">
<input type="text" class="userInput" placeholder=">">
        <button class="checkBtn" onclick="checkAnswer(this)"></button>
        <p class="feedback">
        </p>
</div>

---

The command `jekyll clean` removes the `_site` directory and temporary files.

a) True

b) False

<div class="lesson" data-answer="a">
<input type="text" class="userInput" placeholder=">">
        <button class="checkBtn" onclick="checkAnswer(this)"></button>
        <p class="feedback">
        </p>
</div>
