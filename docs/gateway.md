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

## Gateway dispatch events

| Name                                        | Description                                                                         |
|---------------------------------------------|-------------------------------------------------------------------------------------|
| ACTIVITY_START                              |                                                                                     |
| ACTIVITY_USER_ACTION                        |                                                                                     |
| APPLICATION_COMMAND_AUTOCOMPLETE_RESPONSE   |                                                                                     |
| APPLICATION_COMMAND_PERMISSIONS_UPDATE      | Application command permission was updated                                          |
| AUTH_SESSION_CHANGE                         |                                                                                     |
| BILLING_POPUP_BRIDGE_CALLBACK               |                                                                                     |
| CALL_CREATE                                 |                                                                                     |
| CALL_DELETE                                 |                                                                                     |
| CALL_UPDATE                                 |                                                                                     |
| CHANNEL_CREATE                              | New guild channel created                                                           |
| CHANNEL_DELETE                              | Channel was deleted                                                                 |
| CHANNEL_PINS_ACK                            |                                                                                     |
| CHANNEL_PINS_UPDATE                         | Message was pinned or unpinned                                                      |
| CHANNEL_RECIPIENT_ADD                       |                                                                                     |
| CHANNEL_RECIPIENT_REMOVE                    |                                                                                     |
| CHANNEL_UPDATE                              | Channel was updated                                                                 |
| CONSOLE_COMMAND_UPDATE                      |                                                                                     |
| DELETED_ENTITY_IDS                          |                                                                                     |
| EMBEDDED_ACTIVITY_UPDATE                    |                                                                                     |
| ENTITLEMENT_CREATE                          |                                                                                     |
| ENTITLEMENT_DELETE                          |                                                                                     |
| ENTITLEMENT_UPDATE                          |                                                                                     |
| FORUM_UNREADS                               |                                                                                     |
| FRIEND_SUGGESTION_CREATE                    |                                                                                     |
| FRIEND_SUGGESTION_DELETE                    |                                                                                     |
| GENERIC_PUSH_NOTIFICATION_SENT              |                                                                                     |
| GIFT_CODE_CREATE                            |                                                                                     |
| GIFT_CODE_UPDATE                            |                                                                                     |
| GUILD_APPLICATION_COMMAND_INDEX_UPDATE      |                                                                                     |
| GUILD_BAN_ADD                               | User was banned from a guild                                                        |
| GUILD_BAN_REMOVE                            | User was unbanned from a guild                                                      |
| GUILD_CREATE                                | Lazy-load for unavailable guild, guild became available, or user joined a new guild |
| GUILD_DELETE                                | Guild became unavailable, or user left/was removed from a guild                     |
| GUILD_DIRECTORY_ENTRY_CREATE                |                                                                                     |
| GUILD_DIRECTORY_ENTRY_DELETE                |                                                                                     |
| GUILD_DIRECTORY_ENTRY_UPDATE                |                                                                                     |
| GUILD_EMOJIS_UPDATE                         | Guild emojis were updated                                                           |
| GUILD_FEATURE_ACK                           |                                                                                     |
| GUILD_INTEGRATIONS_UPDATE                   | Guild integration was updated                                                       |
| GUILD_JOIN_REQUEST_CREATE                   |                                                                                     |
| GUILD_JOIN_REQUEST_DELETE                   |                                                                                     |
| GUILD_JOIN_REQUEST_UPDATE                   |                                                                                     |
| GUILD_MEMBERS_CHUNK                         | Response to Request Guild Members                                                   |
| GUILD_MEMBER_ADD                            | New user joined a guild                                                             |
| GUILD_MEMBER_LIST_UPDATE                    |                                                                                     |
| GUILD_MEMBER_REMOVE                         | User was removed from a guild                                                       |
| GUILD_MEMBER_UPDATE                         | Guild member was updated                                                            |
| GUILD_ROLE_CREATE                           | Guild role was created                                                              |
| GUILD_ROLE_DELETE                           | Guild role was deleted                                                              |
| GUILD_ROLE_UPDATE                           | Guild role was updated                                                              |
| GUILD_SCHEDULED_EVENT_CREATE                | Guild scheduled event was created                                                   |
| GUILD_SCHEDULED_EVENT_DELETE                | Guild scheduled event was deleted                                                   |
| GUILD_SCHEDULED_EVENT_UPDATE                | Guild scheduled event was updated                                                   |
| GUILD_SCHEDULED_EVENT_USER_ADD              | User subscribed to a guild scheduled event                                          |
| GUILD_SCHEDULED_EVENT_USER_REMOVE           | User unsubscribed from a guild scheduled event                                      |
| GUILD_STICKERS_UPDATE                       | Guild stickers were updated                                                         |
| GUILD_UPDATE                                | Guild was updated                                                                   |
| INTERACTION_CREATE                          | User used an interaction, such as an Application Command                            |
| INTERACTION_FAILURE                         |                                                                                     |
| INTERACTION_MODAL_CREATE                    |                                                                                     |
| INTERACTION_SUCCESS                         |                                                                                     |
| LIBRARY_APPLICATION_UPDATE                  |                                                                                     |
| LOBBY_CREATE                                |                                                                                     |
| LOBBY_DELETE                                |                                                                                     |
| LOBBY_MEMBER_CONNECT                        |                                                                                     |
| LOBBY_MEMBER_DISCONNECT                     |                                                                                     |
| LOBBY_MEMBER_UPDATE                         |                                                                                     |
| LOBBY_MESSAGE                               |                                                                                     |
| LOBBY_UPDATE                                |                                                                                     |
| LOBBY_VOICE_SERVER_UPDATE                   |                                                                                     |
| LOBBY_VOICE_STATE_UPDATE                    |                                                                                     |
| MESSAGE_ACK                                 |                                                                                     |
| MESSAGE_CREATE                              | Message was created                                                                 |
| MESSAGE_DELETE                              | Message was deleted                                                                 |
| MESSAGE_DELETE_BULK                         | Multiple messages were deleted at once                                              |
| MESSAGE_REACTION_ADD                        | User reacted to a message                                                           |
| MESSAGE_REACTION_REMOVE                     | User removed a reaction from a message                                              |
| MESSAGE_REACTION_REMOVE_ALL                 | All reactions were explicitly removed from a message                                |
| MESSAGE_REACTION_REMOVE_EMOJI               | All reactions for a given emoji were explicitly removed from a message              |
| MESSAGE_UPDATE                              | Message was edited                                                                  |
| NOTIFICATION_CENTER_ITEMS_ACK               |                                                                                     |
| NOTIFICATION_CENTER_ITEM_COMPLETED          |                                                                                     |
| NOTIFICATION_CENTER_ITEM_CREATE             |                                                                                     |
| NOTIFICATION_CENTER_ITEM_DELETE             |                                                                                     |
| OAUTH2_TOKEN_REVOKE                         |                                                                                     |
| PASSIVE_UPDATE_V1                           |                                                                                     |
| PAYMENT_UPDATE                              |                                                                                     |
| PRESENCES_REPLACE                           |                                                                                     |
| PRESENCE_UPDATE                             | User was updated                                                                    |
| READY                                       | Contains the initial state information                                              |
| READY_SUPPLEMENTAL                          |                                                                                     |
| RECENT_MENTION_DELETE                       |                                                                                     |
| RELATIONSHIP_ADD                            |                                                                                     |
| RELATIONSHIP_REMOVE                         |                                                                                     |
| RELATIONSHIP_UPDATE                         |                                                                                     |
| RESUMED                                     | Response to Resume                                                                  |
| SESSIONS_REPLACE                            |                                                                                     |
| STAGE_INSTANCE_CREATE                       | Stage instance was created                                                          |
| STAGE_INSTANCE_DELETE                       | Stage instance was deleted or closed                                                |
| STAGE_INSTANCE_UPDATE                       | Stage instance was updated                                                          |
| STREAM_CREATE                               |                                                                                     |
| STREAM_DELETE                               |                                                                                     |
| STREAM_SERVER_UPDATE                        |                                                                                     |
| STREAM_UPDATE                               |                                                                                     |
| THREAD_CREATE                               | Thread created, also sent when being added to a private thread                      |
| THREAD_DELETE                               | Thread was deleted                                                                  |
| THREAD_LIST_SYNC                            | Sent when gaining access to a channel, contains all active threads in that channel  |
| THREAD_MEMBERS_UPDATE                       | Some user(s) were added to or removed from a thread                                 |
| THREAD_MEMBER_LIST_UPDATE                   |                                                                                     |
| THREAD_MEMBER_UPDATE                        | Thread member for the current user was updated                                      |
| THREAD_UPDATE                               | Thread was updated                                                                  |
| TYPING_START                                | User started typing in a channel                                                    |
| USER_ACHIEVEMENT_UPDATE                     |                                                                                     |
| USER_CONNECTIONS_LINK_CALLBACK              |                                                                                     |
| USER_CONNECTIONS_UPDATE                     |                                                                                     |
| USER_GUILD_SETTINGS_UPDATE                  |                                                                                     |
| USER_NON_CHANNEL_ACK                        |                                                                                     |
| USER_NOTE_UPDATE                            |                                                                                     |
| USER_PAYMENT_CLIENT_ADD                     |                                                                                     |
| USER_PAYMENT_SOURCES_UPDATE                 |                                                                                     |
| USER_PREMIUM_GUILD_SUBSCRIPTION_SLOT_CREATE |                                                                                     |
| USER_PREMIUM_GUILD_SUBSCRIPTION_SLOT_UPDATE |                                                                                     |
| USER_REQUIRED_ACTION_UPDATE                 |                                                                                     |
| USER_SETTINGS_PROTO_UPDATE                  |                                                                                     |
| USER_SUBSCRIPTIONS_UPDATE                   |                                                                                     |
| USER_UPDATE                                 | Properties about the user changed                                                   |
| VOICE_CHANNEL_EFFECT_SEND                   |                                                                                     |
| VOICE_SERVER_UPDATE                         | Guild's voice server was updated                                                    |
| VOICE_STATE_UPDATE                          | Someone joined, left, or moved a voice channel                                      |
| WEBHOOKS_UPDATE                             | Guild channel webhook was created, update, or deleted                               |
