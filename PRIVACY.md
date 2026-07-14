# Pulse AC Bot — Privacy Policy

_Last updated: July 14, 2026_

Pulse AC ("the bot") is a Discord application that lets Roblox game moderation
teams review anti-cheat activity for their own game.

## Data we collect and store

When a server manager registers a game with `/setup`, we store:

- the Discord **server (guild) ID**,
- the **Discord user ID** of the person who ran `/setup` and the time they ran it,
- the **Roblox universe ID**, **DataStore name**, and optional **admin role ID** they provided,
- the **Roblox Open Cloud API key** they voluntarily provided for their own game.

This is the complete list. The bot uses no privileged intents: it cannot read
messages, view server member lists, or see user presence. Command inputs
(such as a Roblox user ID passed to `/logs`) are processed to answer the
command and are not stored.

## How data is used

Stored data is used solely to route each server's commands to its registered
Roblox game via the Roblox Open Cloud API. Anti-cheat log data shown by the
bot lives in the game owner's own Roblox DataStore and is fetched on demand;
we do not copy or retain it.

Data is never sold, shared with third parties, or used to train machine
learning or AI models.

## Data retention and deletion

Registration data is kept until a server manager runs `/unregister` (which
deletes it immediately, including the API key) or the bot is removed from the
server. You may also request deletion by contacting us (below).

## Roblox data

The bot displays moderation records (bans, kicks, detection events) about
Roblox players, created by the game's own anti-cheat system inside that
game owner's Roblox DataStore. Those records are controlled by the game
owner, not by the bot; requests about them should go to the game's
moderation team or Roblox itself.

## Contact

For questions or deletion requests, contact the developer on Discord
(the bot's owner listed on its profile) or via pulseproductshq@gmail.com.
