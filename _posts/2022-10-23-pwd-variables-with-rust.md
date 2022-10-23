---
title: pwd Variables with Rust
author: André Ribeiro
date: 2022-10-23 15:25:00 +0000
categories: [Programing, Project]
tags: [rust, cli]
image:
  src: /posts/pwd-variables-with-rust/cover.png
  width: 600
  height: 400
pin: false
---

> Remember to wrap your () with OK's, or they might feel lonely
{: .prompt-tip }

# Rust
Rust is a fairly new language for me, it has a certain a new view on how you produce code.
In Rust you have to think differently whenever you create a certain *Structure*, more specifically, what are the variants
of this *Structure* and how is their behavior.

You do not have invalid state, as the compiler doesn't allow it.
Rust does not have a garbage collector, it has a concept of ownership. You can move a value somewhere, making it totally gone
from your grasp. On the same way, you can borrow it, allowing the other part of the program to read it but not modify it.

Types are also infered easily by the compiler and even whenever you are writing the code, you always know what you are dealing with.
Meaning you will never be surprised to find out the thing you are actualy manipulating is a string instead of an array, for example.

It can get more complex than this, but this is what really draws me into Rust. The absolute certainty that whatever I am writing
is correct and will remain correct if I **follow the rules of the universe of which I have created**.

If you're interested in discussing or learn more about Rust, I would suggest [No Boilerplate][no boilerplate]{:target="_blank"} youtube channel.

# Why this project?

I believe that whenever we start with a new language, we should also start with a small project that you can do finish
in around 2 weekends.

For that I have followed [The Primeagen course][course]{:target="_blank"} and created a
very simple `Directory-Based-Variable-Map` which is inspired by the course above.

With this, I can easily:
1. add
2. remove
3. get

values of variables that are scoped to the directory we are currently at.

With the addition that if there is a variable that is created on a directory above **this** one, then that too will be
*inherited* and show on the map.

# Operations
As mentioned above, these are the current operations of the directory-map:
```rust
#[derive(Debug, PartialEq)]
pub enum Operation {
    Print(Option<String>),
    Add(String, String),
    Remove(String),
}
```
We can `Print` everything (not give a key), `Print` the value of the key, `Add` a key-value to the map and `Remove` a key
from the directory-map.

Details of the implementation can be found on my [Github Repo][github repo]{:target="_blank"}

But an important mention, I would like to give on this blog post is the testing.
A beautiful thing about languages such as rust and golang is that testing is integrated in the language itself which can
allow us to write tests in the same file, and with no real overhead, that we are writing our normal code.

```rust
#[test]
    fn get_value() {
        let proj = get_projector(PathBuf::from("/foo/bar"));
        assert_eq!(proj.get_value("foo"), Some(&String::from("bar3")));
        assert_eq!(proj.get_value("fem"), Some(&String::from("is_great")));
    }

    #[test]
    fn set_value() {
        let mut proj = get_projector(PathBuf::from("/foo/bar"));
        proj.set_value(String::from("foo"), String::from("bar4"));
        proj.set_value(String::from("fem"), String::from("is_better_than_great"));

        assert_eq!(proj.get_value("foo"), Some(&String::from("bar4")));
        assert_eq!(proj.get_value("fem"), Some(&String::from("is_better_than_great")));
    }

    #[test]
    fn remove_value() {
        let mut proj = get_projector(PathBuf::from("/foo/bar"));
        proj.remove_value("foo");
        proj.remove_value("fem");

        assert_eq!(proj.get_value("foo"), Some(&String::from("bar2")));
        assert_eq!(proj.get_value("fem"), Some(&String::from("is_great")));
    }
```

I mentioned that coding in Rust allows you to be always correct, but that still doesn't mean that you can make logical
assumptions about what you are writing unless you test it, just like every other language and application.

# CLI Application
As a CLI application, it requires you to use it through the console. This means that it is nice to have certain Command Line Arguments.
This in Rust can be easily done with the use of [clap][clap]{:target="_blank"}

```rust
use std::path::PathBuf;

use clap::Parser;

#[derive(Parser, Debug)]
#[clap()]
pub struct Opts {
    #[clap(default_value = "")]
    pub args: Vec<String>,
    #[clap(short = 'c', long = "config")]
    pub config: Option<PathBuf>,

    #[clap(short = 'p', long = "pwd")]
    pub pwd: Option<PathBuf>,
}
```

This is the whole code that we need to do to parse the command line arguements into our code so we can later utilize them
as our logic requires.

# Conclusion
This was a great simple project that allowed me to get more familiar with Rust and in the same time, allow me to create
something that I am currently using on my job.

It allows me to set up certain variables that I can easily access with the command:

`build /program-a $(pwd-map build-config)`

And it gets the correct configuration based on the *pwd* and gives me all the flags I would have to insert by hand or create
a more complex Environment for.

Remember to checkout the [Github repository][github repo]{:target="_blank"} if you're interested in seeing Rust code
and start oxidizing your codebases with Rust!!

[no boilerplate]: https://www.youtube.com/watch?v=4YU_r70yGjQ
[github repo]: https://github.com/Andree37/projector/tree/main/projector
[clap]: https://docs.rs/clap/latest/clap/
[course]: https://frontendmasters.com/courses/typescript-go-rust/

