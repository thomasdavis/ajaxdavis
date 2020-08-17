todo

- finish my personal blog
- readmes
- plan checklist tags categories
- 1 finish theme
- clean up repo code
- blog build from remote source
- make example repo of using local sources
- favicon

# Introducing JSON Blog

> dcwr (don't care, won't read)
> This project aims to make your entire blog contained in a single file, of which you can do what ever you want via utilizing tools built in a community fashion. But not excluded to anyone who thinks that their propertiry softare that imports the file to make a sustainable and commodity for those seeking to build blogs.

## Getting Started

```sh
mkdir myblog && cd myblog
npm i -g jsonblog-cli
blog init
blog build
blog serve
```

## Overview

I feel like I don't speak just for myself but over the years maintaining a blog has been rather arduous. I hate setting them up, I suck at keeping them alive, I dislike buying into platforms, I cannot seem to back them up and they are always way more than I actually needed.

Just recently I happened to stumble upon a Hacker News [comment](a) by Jedberg where he also listed his pain points with personal blogging which largely mirroed my own gripes. His comment and seeing the other trends wishing to relive personal blogging era compelled me to attempt something.

Some readers might have realized already, but JSON Blog was inspired by another project that I started a few years ago called JSON Resume. Essentially your resume is defined as formatted data which you are free to take anywhere you want and use community built tooling to analyze, render and host.

JSON Blog is at core a schematic simply to describe a blog, and I've spent some time developing some initial tooling to make it rather seamless to get started.
Here is a simple example (that generates this site)

```json
{
  "site": {
    "title": "My Blog",
    "description": "I write my thoughts here"
  },
  "basics": {
    "name": "Thomas Davis"
  },
  "posts": [
    {
      "title": "Jean favaorite theme",
      "source": "https://gist.githubusercontent.com/thomasdavis/3654cb08bf728f23a96bf70a037e5817/raw/dd38c0fb1094159789cc980e20f0544b664ed3c1/nobody.md"
    }
  ],
  "pages": [
    {
      "title": "About",
      "source": "https://gist.githubusercontent.com/thomasdavis/3e7eed3648f3a3e3d7b9a84d99fa1da762c5b880/about.md"
    }
  ]
}
```

As with any schema, you might say the naming conventions are terrible, and I'd agree. The reasoning behind any individual property might be rather complex so I can just tell you by what principles I chose these initial ones.

First, once you add anything to a schema, it cannot be removed without difficulty from the ecosystem. So I've only started with the bare essentials. There are some obvious additions to be made such as tags and categories but I've yet to define them for the second reason.

Schema's are only valubable in so far as person's will agree with them. (all reality is justconsensus anyway jks). And to <something> that a schema is agreeable then you need to have a bunch of differing opinions. So there is a schema repo, where anyone can chime in and some people will be elevated to arbiters. And those who debate will complain about lack of change, can't blame them, but change should be slow. And I won't pretend, that Me, the programmatic surgeon dictator won't have a final say. All I can say on that is that I've been consistenly wrong and;

> We have two ears and one mouth so that we can listen twice as much as we speak - Epictetus

## Ecosystem

The tools I've built are Javascript only but as a schematic the language of a tool if agnostic.

`source` in the schema is meant to promote that a blog shouldn't care where you host your content, just make it a publically accessible URI, of which plenty of servies support Drive, Dropbox, Gist, pastbin

Essentially implying you can pass your jsonb.log to any function/company and they should be able to construct it. Which leads onto the concept of a `generator`;

### Generators

A `generator` so far envisioned is a function that simply takes a `blog.json` and outputs an array of files and their content e.g.

```json
{
  "files": [
    {
      "name": "index.html",
      "content": "<h1>I am a good person</h1>"
    },
    {
      "name": "assets/logo.svg",
      "content": "<svg version=\"1.1\"><text>Hello noob</text></svg>"
    }
  ]
}
```

The `generator` should then loop through the files, create directories and files where necessary and pipe in the `content`.

### Hosting / Deployment

user configured

github repo with github actions -> example

github repo with local references
