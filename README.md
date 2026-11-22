# vinted-discord-bot

A Discord bot skeleton for Vinted automation (login, filters, search, purchase). Only the Discord command layer exists; the Vinted logic is not implemented.

Originally named Vinted-Discord-Bot.

## Status

Stub. The commands register and reply, but nothing talks to Vinted:

- `/log-in` and `/log-out` only log a message and reply (no authentication).
- `/filter_edit` and `/filter_view` store filters in memory in a dictionary.
- `/start_search` and `/stop_search` flip a flag; the search loop is a comment.
- `/buy` logs the item ID; no purchase happens.
- `send_item_details` (DM an item) is defined but never called.
- Proxy, captcha and "Buy" button features mentioned in the earlier README do not exist in the code.

## Tech stack

Python, discord.py (slash commands via `app_commands`), python-dotenv. `playwright` and `aiohttp` are listed in requirements but unused so far.

## Project structure

```
main.py            bot setup, loads cogs, syncs slash commands
cogs/auth.py       /log-in, /log-out (placeholders)
cogs/filter.py     /filter_edit, /filter_view
cogs/search.py     /start_search, /stop_search
cogs/purchase.py   /buy (placeholder)
requirements.txt
```

## Setup and run

Requirements: Python 3.9 or newer, a Discord application with a bot token.

Environment variables (put them in a `.env` file, which is git-ignored):

| Name | Purpose |
|---|---|
| `DISCORD_TOKEN` | Discord bot token |

```bash
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
echo 'DISCORD_TOKEN=your-token' > .env
python main.py
```

## Usage

Invite the bot to a server, then use the slash commands, for example `/filter_edit filter_type:size value:M` and `/filter_view`.

## Limitations

- Do not type real passwords into `/log-in`: it is a placeholder and slash command arguments are visible to Discord.
- Filters are lost on restart.
- Automating a Vinted account may break Vinted's terms of use.
