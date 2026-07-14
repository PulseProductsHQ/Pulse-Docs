# Pulse AC Discord bot (multi-tenant)

One bot, many games. Each Discord server registers its **own** Roblox game
with `/setup`; every command then operates on that server's game. The bot
owner (`OWNER_DISCORD_ID`) bypasses all permission checks and can see every
registered game.

## Commands

### For every customer server

| Command | Who can use it | What it does |
| --- | --- | --- |
| `/setup universe_id api_key [admin_role] [datastore]` | Manage Server | Register (or replace) this server's game. Validates the key against Open Cloud before saving. |
| `/unregister` | Manage Server | Remove the registration and stored API key |
| `/status` | anyone | Show this server's registered game (key masked) |
| `/logs user:<id or name> [count]` | admin role* | A Roblox user's anti-cheat history |
| `/recent` | admin role* | Last ~50 events across all players |
| `/stats` | admin role* | Total bans / kicks / log hints / unbans |
| `/baninfo user:<id or name>` | admin role* | Current Roblox ban status |
| `/unban user:<id or name>` | admin role* | Lift the Roblox ban via Open Cloud |

\* the role passed to `/setup`; if none was set, anyone with Manage Server.

### Owner only

| Command | What it does |
| --- | --- |
| `/tenants` | List every registered game: name, universe, guild, who added it, when |

## What a customer needs to do (put this in your product docs)

1. Install the anti-cheat scripts in their game (`ServerAntiCheat`, `ACAuthority`,
   `ACLog`, the two client copies).
2. Create an Open Cloud API key for **their** game at
   create.roblox.com → Open Cloud → API Keys with:
   - `universe-datastores.objects:read`
   - `user-restrictions` read + write
   - restricted to their experience (tell them to enable "Restrict by Experience")
3. Invite your bot, then run `/setup universe_id:<id> api_key:<key>` in their server.

The `/setup` response is ephemeral (only the person running it sees the key).

## Running the bot (you)

1. Copy `.env.example` → `.env`, fill in `DISCORD_TOKEN` and `OWNER_DISCORD_ID`
   (your Discord user id). The `UNIVERSE_ID`/`ROBLOX_API_KEY` block is an
   optional default game used by servers that never ran `/setup` — handy for
   your own testing server.
2. Invite link scopes: `bot` + `applications.commands`. No privileged intents.
3. `pip install -r requirements.txt` then `python bot.py`.

Slash commands appear instantly in `GUILD_ID`'s server and take up to an hour
to propagate globally to customer servers the first time.

## Security notes

- Customer API keys are stored in `tenants.db` (SQLite) next to the bot —
  **treat that file like a password vault**: don't commit it, don't share it,
  back it up privately. Anyone with the file can manage bans in every
  registered game.
- `.env` holds your own secrets; only `.env.example` is safe to share.
- Real-time push per game: each customer can set `WebhookUrl` in their
  `ACLog.lua` to their own Discord webhook (via a proxy — Discord blocks
  direct Roblox calls). The bot itself is pull-based and needs nothing extra.
