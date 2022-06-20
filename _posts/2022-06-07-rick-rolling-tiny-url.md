---
title: Rick Rolling Tiny URL
author: André Ribeiro
date: 2022-06-07 07:20:00 +0000
categories: [Programing, Project]
tags: [golang, frontend]
image:
  src: /posts/rick-roll-tiny-url/cover.png
  width: 600
  height: 400
pin: false
---

> I will keep this one short. But hopefully sweet :)
{: .prompt-tip }

# rickrolling
> "Rickrolling is when you troll someone on the internet by linking to the music video for Rick Astley’s 1987 hit song “Never Gonna Give You Up.” It is, by far, the most popular example of bait-and-switch linking."

*[source][rick dictionary]{:target="_blank"}*

If you know what rickrolling is, that means that one day you were the subject of this joke that is starting to disappear as people memorize more and more the link of the video.

But what if there was a way you could mask that?

# Tiny URL

[TinyURL][tinyurl]{:target="_blank"} is a website that allows you to easily shorten an URL and in certain ways, mask it. Whenever you click on a TinyURL link, you have no idea where you are going end up.

**This could be taken a step further.**

What if you could mask the URL you are sending and, why not, give it a percentage to go to a completely different website?

`that's what I created`

# Rlld

Rlld (short for Rolled) is a website that allows you to shorten your URL and give it a percentage to instead of directing you to the correct website, it redirects you to a Rick Roll video.

![rlld what is](/posts/rick-roll-tiny-url/who_created_rlld.png){: width="322" height="589" style="max-width: 60%" .right}

Is it usefull?
> No

Is it fun?

> Probably annoying

But it allowed me to learn more things about base62 conversion. As I believed it was a better solution to simply hash the URL and have a very long resulting URL. In this case, we have super short URL which maps to the database index of the original URL.

`These are some screens from the web application itself ->`


How to implement this? Here is an example I made in Go to quickly encode and decode the base62 string to and from base10:

```go
func base10ToBase62(id int) string {
  m := "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789"
	var shortURL []string
  for id > 0 {
    shortURL = append(shortURL, string(m[id%62]))
    id /= 62
  }
  return strings.Join(shortURL, "")
}

func base62ToBase10(shortID string) int {
  id := 0
  for i := len(shortID) - 1; i >= 0; i-- {
    val_i := int(shortID[i])
    if val_i >= int('a') && val_i <= int('z') {
      id = id*62 + val_i - int('a')
    } else if val_i >= int('A') && val_i <= int('Z') {
      id = id*62 + val_i - int('Z') + 26
    } else {
      id = id*62 + val_i - int('0') + 52
    }
  }
  return id
}
```
{: .nolineno}

# Website

The frontend was developed using React and [Chakra-UI][chakra]{:target="_blank"} for all the components that you see around :D

Here is a full view of the website in a gif format:

|                  Creating a new rlld                  |                  Accessing the link                   |
|:-----------------------------------------------------:|:-----------------------------------------------------:|
| ![overview](/posts/rick-roll-tiny-url/rlld_video.gif) | ![overview](/posts/rick-roll-tiny-url/rick_video.gif) |

So far you cannot see the website as it's still not fully deployed, but you can check [this repository][repo]{:target="_blank"} that allows you to run it locally with docker with a simple command.

I will update this post whenever the website is live!

[rick dictionary]: https://www.dictionary.com/e/slang/rickrolling/
[tinyurl]: https://tinyurl.com/app
[repo]: https://github.com/Andree37/rlld-backend
[chakra]: https://chakra-ui.com/

