# Montra for Cursor

Connects Cursor to [Montra](https://montra.com), which turns narrated screen recordings
into implementation-ready documents made of **tickets** — each ticket a markdown spec with
the annotated screenshots and narration behind it.

With the plugin installed, Cursor can read your Montra documents and tickets, open the
screenshots attached to them, and pull the transcript of what was said while the recording
was made — so "move this button and make the empty state less shouty" arrives with the
screen it refers to.

## What's in here

This plugin ships no code. Montra's MCP server is hosted at
`https://montra.com/api/mcp`, so the repo is a manifest that points Cursor at it, plus a
rule describing how to work with Montra content.

```
.cursor-plugin/plugin.json   plugin manifest
mcp.json                     the Montra MCP server
rules/montra.mdc             how to treat Montra tickets (read-only by default)
assets/logo.svg              plugin logo
```

## Install

Install **Montra** from the Cursor marketplace, or add this repository as a plugin in
Cursor.

The first time Cursor connects, it opens Montra in your browser to sign in. Approve the
connection and pick the workspace it should act in — the connection is bound to that one
workspace, and each client you connect (Cursor, Claude, Codex) can be bound to a
different one.

If you would rather not use a plugin, the same server works as a plain entry in
`~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "montra": {
      "url": "https://montra.com/api/mcp"
    }
  }
}
```

Use one or the other, not both — otherwise Cursor sees Montra's tools twice.

## Tools

| Tool | Purpose |
| --- | --- |
| `get_workspace` | Which workspace this connection is bound to |
| `list_folders` | Folders in the workspace |
| `list_documents` | Recent documents, optionally filtered by folder |
| `search_workspace` | Search documents and tickets in the workspace |
| `get_document` | One document with its tickets, including each ticket's markdown body |
| `get_ticket` | One ticket in full |
| `get_ticket_images` | A ticket's annotated screenshots |
| `get_transcript` | The recording's narration, with timestamps |
| `get_document_by_share_url` | Resolve a pasted Montra share link |
| `create_document`, `update_document` | Create or edit a document |
| `create_ticket`, `update_ticket`, `delete_ticket` | Create, edit, or remove a ticket |
| `link_ticket_issue` | Record the Linear or Notion issue created from a ticket |

Writes are opt-in: the tickets are your spec, so the agent is told to change them only
when you explicitly ask, and never to record progress by rewriting one.

## Verifying the connection

Ask Cursor to call `get_workspace`. It returns the name of the workspace the connection is
bound to — confirmation that sign-in and workspace binding both worked.

## Docs and support

- Connection guide: https://docs.montra.com/connect
- Tool reference: https://docs.montra.com
- support@montra.com

## License

MIT — see [LICENSE](LICENSE).
