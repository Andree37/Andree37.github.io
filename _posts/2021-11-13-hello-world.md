---
title: Hello World
date: 2021-11-13 22:00:00 +0000
categories: [Blogging, Writing]
tags: [writing]
---

## First post

Hello! Welcome to my **Pages**!

These **Pages** are a place for any person to keep tabs on what I've been doing in the past and am currently working on.
So if that interests you, welcome :D

I think about this website as an opportunity to share:
- `ideas` about programming, music or the overall world and things that I enjoy.
- `projects` that I've done in the past or am currently working on.
- `studies` on certain fields that I'm currently interested.


Not wanting to be too garrulous, I'll leave you with one of my favorite c++ code snippets:

```c++
int main () {
  int w = 40;
  while(1){
    for (int i=1;i<=w*(w+1);i++)
      printf(
        "%c",
         i % (w+1) == 0 ? '\n' :
        i % (w) == 0 || i % (w+2) == 1 ? '*' : ' ');
  }
}
```

Try it out on [this online compiler](https://onlinegdb.com/k1-HH4tZB){:target="_blank"} to check out what it does.
