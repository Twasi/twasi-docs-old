# Songrequest
This plugin provides songrequest functionality to Twasi.

## Providers
Twasi will support the following music providers:

- YouTube (Web Player)
- Spotify (Spotify Player / Not embedded)
- SoundCloud (Web Player) (Low priority)

## Cross-Requests
Twasi tries to fit best in every streamers scenario. We want to allow cross requests, so that users can request songs from spotify or youtube on the same line.

## Commands
There are many ways to write a song request command nowadays. And guess what: Twasi supports almost all of them!

The first part of the command has to be one of the following:

- `!songrequest`
- `!requestsong`
- `!sr`
- `!rs`
- `!request`

The second part has to be one of the following:

A reference to a song

- YouTube Video Link (e.g. https://www.youtube.com/watch?v=dQw4w9WgXcQ or https://youtu.be/dQw4w9WgXcQ)
- Spotify Share Link (e.g. https://open.spotify.com/track/7mRGq0jEVatQGrdn1DvDfM)
- SoundCloud Share Link (e.g. https://soundcloud.com/k-391/k-391-ignite-feat-alan-walker-julie-bergan-seungri)
- A text search that will be queried against the main provider (YouTube). Note that the text search cannot start with one of the keywords listed below.

or any operational keyword:

- `list`: Returns a link to the online songlist
- `current`, `playing`, `status` or without anything (just `!songrequest`): Shows the current status and song that is played.
- `next`: Shows the next track that will be played.
- `info [request-id]`: Shows info about a requested track, e.g. when it will be approximately played
- `delete [request-id]`: Delete your own requests. Not applicable if the song is already playing. Can also be used by moderators.
- `skip`: Skip the current playing song. This can only be executed with moderation rights.
- `clear`: This clears the entire list. Careful with that one!
- `revert`, `wrongsong`, `oops`: This removes your latest song from the request list.
- `voteskip`: Vote to skip this song. You can set options in the panel (e.g. what percentage of viewer need to vote skip)
