---
title: Building a Language Interpreter in Zig
date: 2025-10-29 20:25:00 +0100
categories: [zig, programming-languages]
tags: [zig, interpreter, learning]
image:
  path: /assets/img/posts/zig-interpreter/image.png
pin: false
---

I wanted to learn Zig, so I built an interpreter. Turns out building your own programming language is pretty addictive.

## The Project

Following "Writing an Interpreter in Go" by Thorsten Ball, I implemented the same language but in Zig instead of Go. It's a basic language that can handle:

- Variables: `let a = 5;`
- Strings: `"hello world"`
- Math: `a * 99`
- Comparisons: `a > 3`
- If statements: `if (condition) { value1 } else { value2 }`

Here's what it looks like in action:

```
>> let name = "André";
André
>> let age = 25;
25
>> let greeting = "Hello, " + name + "!";
Hello, André!
>> if (age > 18) { "You're an adult" } else { "You're a minor" };
You're an adult
>> age * 2;
50
>> let double_age = age * 2;
50
>> if (double_age > 40) { "Wow, that's old!" } else { "Still young!" };
Wow, that's old!
```

Nothing groundbreaking, but it's surprisingly satisfying to see your own language execute real logic.

## Why Zig?

I chose Zig because I wanted something different from Go. Zig has:
- No garbage collector (you manage memory yourself)
- Blazing fast compilation
- Simple, no-nonsense syntax
- Error handling that forces you to think about what can go wrong

Plus, Zig is still young and evolving, which makes it exciting to work with. There's something appealing about learning a language that doesn't have 20 years of baggage and weird historical decisions.

## What I Learned

I already knew how interpreters work from previous projects, but this was my deep dive into Zig. Following a familiar problem in an unfamiliar language taught me:
- Zig's allocator system (every allocation needs an allocator!)
- Manual memory management without being terrifying
- How explicit error handling changes your code structure
- The joy of compile-time guarantees without runtime overhead
- Why "no hidden control flow" is actually liberating
- The importance of unit testing EVERYTHING (I wrote tests for every single component)

The whole thing is pretty straightforward - you read code, break it into tokens, parse those into a tree structure, then walk the tree and execute it. The book does a great job explaining each step clearly.

Following along was smooth sailing. The concepts clicked pretty quickly, and implementing them in Zig felt natural. Operator precedence, parentheses handling, conditional expressions - all of it just worked as expected. Seeing the final REPL come together and being able to write `let x = if (condition) { 42 } else { 0 };` in my own language was satisfying. Thorsten's approach is really solid.

## The Journey

Following Thorsten Ball's book was great because he explains everything step by step without getting lost in academic jargon. The concepts are presented so clearly that I never felt stuck or confused. The book uses Go, but translating to Zig was straightforward - the concepts transfer well between languages.

Zig's explicit memory management actually made things cleaner in many ways. No hidden allocations, no surprise garbage collection pauses - everything is explicit and predictable. The translation from Go was mostly mechanical once I got comfortable with Zig's syntax and memory management patterns.

The testing story in Zig is fantastic too. I went overboard with unit tests - testing every tokenizer case, every parser rule, every evaluator branch. Being able to run `zig build test` and see hundreds of tests pass gave me confidence that things were actually working correctly. When you're dealing with manual memory management, having that safety net of comprehensive tests is invaluable.

## Try It

Want to run it? 

```bash
git clone https://github.com/Andree37/interpreter-zig
cd interpreter-zig
zig build run
```

That's it. Building your own language, even a simple one, gives you this weird sense of power. You start looking at other programming languages differently - "Oh, that's just syntactic sugar for..." or "I bet their parser handles that with..."

It's like learning how magic tricks work. Once you see behind the curtain, you can never look at code the same way again.

Now I'm ready to tackle the companion book "Writing a Compiler in Go" - also in Zig, of course. Because why stop at interpretation when you can compile to bytecode?

If you've ever been curious about how languages work, I highly recommend building your own interpreter. Start small, follow a good book, and prepare to have your mind slightly blown by how much is happening when you type `let x = 5;`.

---

*Source code: [GitHub](https://github.com/Andree37/interpreter-zig)*
