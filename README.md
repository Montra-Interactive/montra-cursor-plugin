# Montra for Cursor

Connects Cursor to [Montra](https://montra.com), which turns narrated screen recordings
into implementation ready documents made of **tickets**. Each ticket is a markdown spec
with the annotated screenshots and narration behind it.

With the plugin installed, Cursor can read those documents and tickets, open the
screenshots a ticket refers to, and pull the transcript of what was said while the
recording was made. A recorded request arrives with the screen it refers to, so you
record it once instead of retyping it.

## What is in here

This plugin ships no code. Montra's MCP server is hosted, so the repo is a manifest that
points Cursor at it, plus a rule describing how to treat Montra content.

```
.cursor-plugin/plugin.json   plugin manifest
mcp.json                     the Montra MCP server
rules/montra.mdc             how to treat Montra tickets
assets/                      plugin logo
```

## Install

Install **Montra** from the Cursor marketplace, or add this repository as a plugin in
Cursor.

The first time Cursor connects, it opens Montra in your browser to sign in. Approve the
connection and choose the workspace it should act in.

Setup notes for Cursor and other MCP clients: https://docs.montra.com/connect

## What Cursor can do with it

Read your documents, tickets, ticket screenshots, and recording transcripts. Writing is
opt in: the tickets are your spec, so the agent changes them only when you ask it to.

## Docs

https://docs.montra.com

## License

MIT, see [LICENSE](LICENSE).
