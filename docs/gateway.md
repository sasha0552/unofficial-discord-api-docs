# Gateway

## Gateway opcodes

| Code | Name                                     | Sent by       | Description                                                                             |
|------|------------------------------------------|---------------|-----------------------------------------------------------------------------------------|
| 0    | DISPATCH                                 | server        | An event was dispatched.                                                                |
| 1    | HEARTBEAT                                | client/server | Fired periodically by the client to keep the connection alive.                          |
| 2    | IDENTIFY                                 | client        | Starts a new session during the initial handshake.                                      |
| 3    | PRESENCE_UPDATE                          | client        | Update the client's presence.                                                           |
| 4    | VOICE_STATE_UPDATE                       | client        | Used to join/leave or move between voice channels.                                      |
| 5    | VOICE_SERVER_PING                        |               |                                                                                         |
| 6    | RESUME                                   | client        | Resume a previous session that was disconnected.                                        |
| 7    | RECONNECT                                | server        | You should attempt to reconnect and resume immediately.                                 |
| 8    | REQUEST_GUILD_MEMBERS                    | client        | Request information about offline guild members in a large guild.                       |
| 9    | INVALID_SESSION                          | server        | The session has been invalidated. You should reconnect and identify/resume accordingly. |
| 10   | HELLO                                    | server        | Sent immediately after connecting, contains the heartbeat_interval to use.              |
| 11   | HEARTBEAT_ACK                            | server        | Sent in response to receiving a heartbeat to acknowledge that it has been received.     |
| 13   | CALL_CONNECT                             |               |                                                                                         |
| 14   | GUILD_SUBSCRIPTIONS                      |               |                                                                                         |
| 15   | LOBBY_CONNECT                            |               |                                                                                         |
| 16   | LOBBY_DISCONNECT                         |               |                                                                                         |
| 17   | LOBBY_VOICE_STATES_UPDATE                |               |                                                                                         |
| 18   | STREAM_CREATE                            |               |                                                                                         |
| 19   | STREAM_DELETE                            |               |                                                                                         |
| 20   | STREAM_WATCH                             |               |                                                                                         |
| 21   | STREAM_PING                              |               |                                                                                         |
| 22   | STREAM_SET_PAUSED                        |               |                                                                                         |
| 24   | REQUEST_GUILD_APPLICATION_COMMANDS       |               |                                                                                         |
| 25   | EMBEDDED_ACTIVITY_LAUNCH                 |               |                                                                                         |
| 26   | EMBEDDED_ACTIVITY_CLOSE                  |               |                                                                                         |
| 27   | EMBEDDED_ACTIVITY_UPDATE                 |               |                                                                                         |
| 28   | REQUEST_FORUM_UNREADS                    |               |                                                                                         |
| 29   | REMOTE_COMMAND                           |               |                                                                                         |
| 30   | GET_DELETED_ENTITY_IDS_NOT_MATCHING_HASH |               |                                                                                         |
