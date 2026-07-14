# Pulse — Documentation

Pulse is an anti-cheat system for Roblox games, with a Discord bot for
reviewing what it catches. This repository holds our public documents and
customer setup guides.

## Documents

- [Privacy Policy](PRIVACY.md)
- [Terms of Service](TERMS.md)

## What Pulse does

Pulse runs inside your Roblox game and detects, punishes, and logs cheaters:
speed, fly, noclip and teleport enforcement on the server, plus client tamper
detection. Every ban, kick, and detection is logged so your staff can review it
from Discord.

## The Discord bot

Once Pulse is installed in your game, link it to your Discord server and your
moderation team can use:

| Command | What it does |
| --- | --- |
| `/setup` | Link your Roblox game to your Discord server (server managers only) |
| `/status` | Show which game is linked |
| `/logs user` | A player's full anti-cheat history |
| `/recent` | The latest detections across your game |
| `/stats` | Total bans, kicks and detections |
| `/baninfo user` | Whether a player is currently banned, and why |
| `/unban user` | Lift a ban |

Commands accept a Roblox username or user id.

## Linking your game (customers)

1. Install the Pulse scripts in your game (provided with your purchase).
2. Create a Roblox Open Cloud API key at create.roblox.com → Open Cloud →
   API Keys, restricted to your experience, with:
   - `universe-datastores.objects:read`
   - `user-restrictions` read and write
3. In your Discord server, run `/setup` with your game's universe id and the
   API key. The key is only visible to you and is stored solely to serve your
   server's commands — see the [Privacy Policy](PRIVACY.md).

## Support

Discord: contact the bot owner listed on the bot's profile.
Email: pulseproductshq@gmail.com
