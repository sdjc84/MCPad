# MCPad — Persistent AI Notepad with Built-in MCP Server

[![License: Apache-2.0](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Stars](https://img.shields.io/github/stars/yourusername/mcpad?style=social)](https://github.com/yourusername/mcpad)

**A minimal, offline-first rich-text notepad whose entire content is exposed as an MCP server.**  
Close the app — your notes stay available to any local LLM (via Ollama + mcphost, Gemini CLI, Claude Desktop, etc.) forever.

Perfect for:
- Persistent memory across LLM sessions
- “Ask my notepad” workflows with zero token waste
- Privacy-focused AI journaling / knowledge base

https://github.com/user-attachments/assets/your-screenshot-or-gif-here

## Why mcpad?

| Feature                          | mcpad                              | Obsidian + plugins | Plain text files + RAG |
|----------------------------------|------------------------------------|--------------------|-------------------------|
| Rich text (bold, lists, etc.)   | Yes (TipTap)                           | Yes                    | No                  |
| Persistent MCP tools when app closed | Yes (independent server)          | No                     | No                  |
| Works with any Ollama model     | Yes (via mcphost)                       | Partial                | Partial             |
| <20 MB downloadable binary      | Yes (Tauri)                             | Electron bloat         | N/A                 |
| Zero external dependencies      | Yes                                     | Many plugins           | No GUI              |

## MVP Features (v0.1)

- Create, edit, delete rich-text notes
- Full-text + semantic search (optional embedding with Ollama/nomic-embed-text)
- Built-in MCP server exposing:
  - `list_notes() → List[NoteMetadata]`
  - `read_note(id: str) → str` (HTML or Markdown)
  - `write_note(title: str, content: str) → str` (returns id)
  - `update_note(id: str, content: str)`
  - `search_notes(query: str) → List[NoteMetadata]`
- Auto-start server on boot (optional tray icon)
- Works out-of-the-box with `mcphost` + Ollama

## Quick Start

### 1. Download binary (Windows / macOS / Linux)
→ Coming after first release — star to get notified!

### 2. Or run from source (dev)

```bash
# Backend MCP server (runs independently)
git clone https://github.com/yourusername/mcpad.git
cd mcpad/server
python -m venv venv && source venv/bin/activate
pip install -r requirements.txt
uvicorn main:app --port 8900 --reload
