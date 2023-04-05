# Voice connection

## Voice connection opcodes

| Code | Name                   | Sent by       | Description                                              |
|------|------------------------|---------------|----------------------------------------------------------|
| 0    | IDENTIFY               | client        | Begin a voice websocket connection.                      |
| 1    | SELECT_PROTOCOL        | client        | Select the voice protocol.                               |
| 2    | READY                  | server        | Complete the websocket handshake.                        |
| 3    | HEARTBEAT              | client        | Keep the websocket connection alive.                     |
| 4    | SELECT_PROTOCOL_ACK    | server        | Describe the session.                                    |
| 5    | SPEAKING               | client/server | Indicate which users are speaking.                       |
| 6    | HEARTBEAT_ACK          | server        | Sent to acknowledge a received client heartbeat.         |
| 7    | RESUME                 | client        | Resume a connection.                                     |
| 8    | HELLO                  | server        | Time to wait between sending heartbeats in milliseconds. |
| 9    | RESUMED                | server        | Acknowledge a successful session resume.                 |
| 12   | VIDEO                  |               |                                                          |
| 13   | CLIENT_DISCONNECT      | server        | A client has disconnected from the voice channel         |
| 14   | SESSION_UPDATE         |               |                                                          |
| 15   | MEDIA_SINK_WANTS       |               |                                                          |
| 16   | VOICE_BACKEND_VERSION  |               |                                                          |
| 17   | CHANNEL_OPTIONS_UPDATE |               |                                                          |
