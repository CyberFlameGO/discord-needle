# Needle
Needle is a discord bot that helps you manage your discord threads.

## Features
- Automatically create new threads for every message in certain channels
- More to come :wink: Check out open [issues](https://github.com/MarcusOtter/discord-needle/issues)!

## Running the bot
1. Clone the repository
2. Edit the `src/config.json` with API token and the IDs of the channels you want to thread every message in:
    ```json
    {
        "discordApiToken": "INSERT TOKEN",
        "threadChannels": [
            "CHANNEL ID 1",
            "CHANNEL ID 2",
        ]
    }
    ```
3. Run `npm install`
4. Make sure the bot has the required permissions in Discord. Depending on your [configuration](#configuration), these can be:
    - `USE_PUBLIC_THREADS` (always required)
    - `SEND_MESSAGES_IN_THREADS` (always required)
    - `READ_MESSAGE_HISTORY` (always required)
    - `EMBED_LINKS` (required if there are any [embeds](#embeds))
    - `MANAGE_MESSAGES` (required if [shouldPin](#shouldpin) is `true`)
5. Run `npm start`
5. Done! :tada:

## Configuration :construction: UNDER CONSTRUCTION, NOT WORKING YET :construction:
If you want to, you can (**IN THE FUTURE**) configure how the bot reacts by editing the `src/config.json`.
An explanation follows.

### threadArchiveDurationInMinutes
Determines the duration of inactivity that causes a thread to be automatically archived (by Discord). If your server's boost level is not high enough for the setting you choose, or if you leave it blank, it will default to `"MAX"`.

Allowed values:
- `60` (= 1hr)
- `1440` (= 1d)
- `4320` (= 3d) :warning: *only for servers with boost level 1 or higher*
- `10080` (= 1w) :warning: *only for servers with boost level 2 or higher*
- `"MAX"` (depends on the server's boost level)

### threadMessage
Settings regarding the message that is sent by the bot in the thread when it is created.

#### shouldSend
Whether or not to send a message. If you set this to `false`, the rest of these settings are ignored.

#### shouldPin
Whether or not to pin the message that was sent by the bot. If you set this to `false`, the bot does not need the `MANAGE_MESSAGES` permission.

#### content
The text content of the message that is sent. Available variables:
- `$$authorMention` - A mention of the author that sent the original message
- `$$channelMention` - A mention of the channel that the original message was sent in
- `$$relativeTimeSince` - A relative timestamp for when the original message was posted

#### embeds
An array of the embeds to attach to the message, with a maximum of 10. Available embeds:
- `$$messageEmbed` - A copy of the original message in embed format
