---
title: "Mimir: Write Your Story, Map Your World, Own Your Data"
date: 2026-02-02 12:00:00 +0000
categories: [Programming, Project]
tags: [electron, react, python, ai, privacy, creative-writing, local-ai]
image:
  path: /assets/img/posts/mimir-editor/mimir.jpeg
pin: true
---

My friends and I have been working on something that combines two things we care about: writing and privacy. It's called **Mimir**, and it's an AI-powered writing tool that runs completely on your computer.

> **Want to try it?** Visit [mimir-editor.com](https://www.mimir-editor.com/) to join the waitlist and get updates on the beta release.

## The Problem

Most modern writing tools make you choose:

- **Traditional tools** (Word, Scrivener): Private, but no AI help
- **Cloud AI tools** (Sudowrite, NovelAI): Powerful AI, but your manuscript lives on their servers

We wanted both. AI assistance for story development without sending our work to the cloud.

## See Mimir in Action

Watch how Mimir works—from writing your manuscript to seeing your story world visualized automatically:

<iframe width="800" height="450" src="https://www.youtube.com/embed/TTz-LGa5uZo" title="Mimir Demo" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## What Mimir Does

Mimir is a desktop app with two main modes:

### Editor Mode
A clean writing interface where you work on your manuscript. Import Word documents, organize chapters, and write in a distraction-free environment.

### Creator Mode
This is where it gets interesting. As you write, Mimir helps you visualize your story through different views:

- **Canvas**: Visual map of characters, locations, and relationships
- **Timeline**: See events chronologically
- **Structured View**: Organized lists of story elements
- **Outline**: Hierarchical story structure

The idea is simple: write naturally, and see your story world emerge visually.

## The Privacy-First Approach

Here's what makes Mimir different: it uses a tiny **local AI** that runs on your machine.

The system has two parts:

1. **Mimir Editor** (Electron + React + TypeScript) - The desktop app you interact with
2. **Mimir Embedder** (Python backend) - The AI engine that processes your text locally

The embedder uses:
- **Sentence Transformers** for understanding your text semantically
- **Qdrant** (embedded vector database) for storing story elements
- **Local LLM** (Phi-3.5 via llama.cpp) for text generation and extraction (teeny tiny model that runs on your CPU)

Everything runs on your computer. Your manuscript never touches the cloud.

## How It Actually Works

When you write in Mimir, the local AI can extract story elements automatically. For example, if you write:

> "Sarah activated her telekinesis and lifted the ancient tome from the library shelf. She needed to master the Pyromancy spell before the Zorthian fleet arrived."

Mimir can identify:
- Character: Sarah (ability: telekinesis)
- Item: ancient tome
- Location: library
- Magic system: Pyromancy
- Faction: Zorthians

You don't tag these manually. The AI extracts them from your prose and makes them available in the different views.

## Custom Taxonomies

Every story is different. Fantasy novels need magic systems. Sci-fi needs technologies. Superhero stories need powers.

Mimir lets you define custom entity types for your world. The AI learns what matters in YOUR story and tracks it automatically.

## Import Your Existing Work

Already have chapters in Word? Mimir can import `.docx` files, convert them to Markdown, and process them through the AI to build your initial story universe.

## The Tech Stack

For the curious, here's what powers Mimir:

**Frontend (Electron App):**
- React + TypeScript
- TipTap for rich text editing
- ReactFlow for canvas visualization
- Yjs for optional collaboration (real-time editing with others coming soon)

**Backend (AI Engine):**
- Python 3.10+
- Sentence Transformers for embeddings
- llama.cpp for local LLM inference
- Qdrant (embedded) for vector storage
- Unix sockets for IPC between editor and AI

## Why Build This?

My friends and I are writers who code. We've tried every writing tool out there:

- Scrivener is great for organization, but has no AI
- Cloud AI tools are powerful, but we don't want our unpublished novels on someone else's servers
- ChatGPT is helpful, but copy-pasting scenes back and forth is clunky

We wanted the organizational power of Scrivener, the visual mapping of story planning tools, and AI assistance that respects our privacy.

So the three of us built Mimir together.

## Current Status

Mimir is in active development. The core features work:
- Writing and organizing documents
- Importing Word files
- Multiple story views (Canvas, Timeline, Outline)
- Local AI entity extraction
- Semantic search of your story

It's not perfect. The AI is slower than cloud services (because it's running on your laptop). The UI has rough edges. But it works, and it's private. We'll continue improving it over time based on feedback.

## What's Next

We're working on:
- Better consistency checking (catching timeline errors, character contradictions)
- Export to PDF, EPUB, DOCX
- Improved entity extraction accuracy
- Faster inference with GPU acceleration
- Plugin system for custom extractors

## Try It

Mimir is heading toward open beta. If you're a writer who values privacy and wants to try AI-assisted story development that runs locally, stay tuned.

The name "Mimir" comes from Norse mythology—the god of wisdom and knowledge. It felt fitting for a tool that helps you understand your own story world while keeping that knowledge private.

Your story stays yours. Your data stays on your machine. That's the promise.

---

**Learn More:**
- [Mimir Website](https://www.mimir-editor.com/)

**Tech References:**
- [Sentence Transformers](https://www.sbert.net/)
- [llama.cpp](https://github.com/ggerganov/llama.cpp)
- [Qdrant](https://qdrant.tech/)
- [TipTap Editor](https://tiptap.dev/)
