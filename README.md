Note:  This is geared for Hexnicks because I made it for my server.  You can change out `hexnicks_nick` with any PAPI placeholder that resolves to a nickname, like `essentials_nickname`.  Make sure to exclude the % in this case.



This vanish aware skript is a lightweight Skript that replaces the default join and leave messages with nickname-aware broadcasts and full vanish support. Instead of showing raw usernames, it pulls each player's HexNicks nickname and falls back to their real name when no nick is set — and it stays completely silent for vanished players, including when staff toggle vanish mid-session.


Features:


Nickname-aware join and leave broadcasts using the HexNicks nickname placeholder
Automatic fallback to the player's real name when no nickname is set
Silent join and leave for vanished players — no message is broadcast while a player is vanished
Mid-session vanish detection — when a player toggles vanish, it broadcasts a matching "left"/"joined" line so vanishing reads as a leave and unvanishing reads as a join
Works with common vanish commands: /vanish, /v, /sv, and the plugin-namespaced variants for SuperVanish, PremiumVanish, EssentialsX, and CMI
Handles the /cmi vanish subcommand form as well
Clears the default vanilla join/quit messages so only the custom broadcasts show
Simple, dependency-driven design — no config or database, just drop it in and reload


Use Cases:


Servers using HexNicks that want join/leave messages to show nicknames instead of usernames
Staff teams that vanish in and out and want those transitions handled cleanly (silent, or shown as a natural leave/join)
Networks wanting a consistent, minimal join/leave message style without a heavyweight plugin


How it works:


On join and quit, it reads the hexnicks_nick placeholder for the player, falls back to their name if empty, and broadcasts the message — unless the player carries the vanished metadata, in which case nothing is sent.
On a vanish command, it snapshots the target's vanish state, waits a couple of ticks for the vanish plugin to apply, then broadcasts a leave (if now vanished) or join (if now visible) using the resolved nickname.


Requirements:


Skript
HexNicks — provides the hexnicks_nick placeholder used for nicknames (Again - or any plugin that exposes nickname placeholders)
A Skript PlaceholderAPI bridge addon (such as skript-placeholderapi or SkBee) so Skript can read the HexNicks placeholder
A vanish plugin that sets the shared vanished metadata key — SuperVanish, PremiumVanish, EssentialsX, or CMI — for the vanish-aware behavior


Note: This is a Skript, not a compiled plugin — you'll need Skript installed to run it. Without HexNicks it will simply broadcast real usernames; without a vanish plugin setting the vanished metadata, the silent/mid-session vanish handling won't trigger. Because it clears the default join/quit messages, don't run it alongside another join/leave message plugin or you'll get blank or doubled messages.
