# Entryway Monorepo

This monorepo contains both the bot and web service for Entryway.

The monorepo is managed using `pnpm` workspaces, although only the web service can take full advantage of this. The bot service only uses `pnpm` for tools and scripts, but its dependencies are managed with `pip` and a `requirements.txt` file.

## Crates

| Crate        | Description                                                                    |
|--------------|--------------------------------------------------------------------------------|
| `crates/web` | The dashboard and user verification system for Entryway, built with Sveltekit. |
| `crates/bot` | The actual bot that interacts with Stoat.chat, built with `Stoat.py`.          |

