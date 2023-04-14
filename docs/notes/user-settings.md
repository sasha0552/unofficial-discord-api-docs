# User settings

## Explanation

Endpoint: `/users/@me/settings-proto/:id`

| Id | Type                            | Description                                                               |
|----|---------------------------------|---------------------------------------------------------------------------|
| 1  | PRELOADED_USER_SETTINGS         | Discord Client settings (language, theme, etc)                            |
| 2  | FRECENCY_AND_FAVORITES_SETTINGS | Frecency & favorites of emojis, stickers, GIFs, application commands, etc |
| 3  | TEST_SETTINGS                   |                                                                           |

## .proto specification

For `PRELOADED_USER_SETTINGS` use `message PreloadedUserSettings`  
For `FRECENCY_AND_FAVORITES_SETTINGS` use `message FrecencyUserSettings`  

```protobuf
syntax = "proto3";
package discord_protos.discord_users.v1;

import "google/protobuf/timestamp.proto";
import "google/protobuf/wrappers.proto";

enum GIFType {
    NONE = 0;
    IMAGE = 1;
    VIDEO = 2;
}

enum InboxTab {
    UNSPECIFIED = 0;
    MENTIONS = 1;
    UNREADS = 2;
    TODOS = 3;
    FOR_YOU = 4;
}

enum GuildActivityStatusRestrictionDefault {
    OFF = 0;
    ON_FOR_LARGE_GUILDS = 1;
}

enum FavoriteChannelType {
    UNSET_FAVORITE_CHANNEL_TYPE = 0;
    REFERENCE_ORIGINAL = 1;
    CATEGORY = 2;
}

enum Theme {
    UNSET = 0;
    DARK = 1;
    LIGHT = 2;
}

message FrecencyUserSettings {
    discord_protos.discord_users.v1.Versions versions = 1;
    discord_protos.discord_users.v1.FavoriteGIFs favorite_gifs = 2;
    discord_protos.discord_users.v1.FavoriteStickers favorite_stickers = 3;
    discord_protos.discord_users.v1.StickerFrecency sticker_frecency = 4;
    discord_protos.discord_users.v1.FavoriteEmojis favorite_emojis = 5;
    discord_protos.discord_users.v1.EmojiFrecency emoji_frecency = 6;
    discord_protos.discord_users.v1.ApplicationCommandFrecency application_command_frecency = 7;
}

message FavoriteGIFs {
    map<string, discord_protos.discord_users.v1.FavoriteGIF> gifs = 1;
    bool hide_tooltip = 2;
}

message FavoriteGIF {
    discord_protos.discord_users.v1.GIFType format = 1;
    string src = 2;
    uint32 width = 3;
    uint32 height = 4;
    uint32 order = 5;
}

message FavoriteStickers {
    repeated fixed64 sticker_ids = 1;
}

message StickerFrecency {
    map<fixed64, discord_protos.discord_users.v1.FrecencyItem> stickers = 1;
}

message FavoriteEmojis {
    repeated string emojis = 1 [packed = false];
}

message EmojiFrecency {
    map<string, discord_protos.discord_users.v1.FrecencyItem> emojis = 1;
}

message ApplicationCommandFrecency {
    map<string, discord_protos.discord_users.v1.FrecencyItem> application_commands = 1;
}

message FrecencyItem {
    uint32 total_uses = 1;
    repeated uint64 recent_uses = 2;
    int32 frecency = 3;
    int32 score = 4;
}

message PreloadedUserSettings {
    discord_protos.discord_users.v1.Versions versions = 1;
    discord_protos.discord_users.v1.InboxSettings inbox = 2;
    discord_protos.discord_users.v1.AllGuildSettings guilds = 3;
    discord_protos.discord_users.v1.UserContentSettings user_content = 4;
    discord_protos.discord_users.v1.VoiceAndVideoSettings voice_and_video = 5;
    discord_protos.discord_users.v1.TextAndImagesSettings text_and_images = 6;
    discord_protos.discord_users.v1.NotificationSettings notifications = 7;
    discord_protos.discord_users.v1.PrivacySettings privacy = 8;
    discord_protos.discord_users.v1.DebugSettings debug = 9;
    discord_protos.discord_users.v1.GameLibrarySettings game_library = 10;
    discord_protos.discord_users.v1.StatusSettings status = 11;
    discord_protos.discord_users.v1.LocalizationSettings localization = 12;
    discord_protos.discord_users.v1.AppearanceSettings appearance = 13;
    discord_protos.discord_users.v1.GuildFolders guild_folders = 14;
    discord_protos.discord_users.v1.Favorites favorites = 15;
    discord_protos.discord_users.v1.AudioSettings audio_context_settings = 16;
    discord_protos.discord_users.v1.CommunitiesSettings communities = 17;
}

message InboxSettings {
    discord_protos.discord_users.v1.InboxTab current_tab = 1;
    bool viewed_tutorial = 2;
}

message AllGuildSettings {
    map<fixed64, discord_protos.discord_users.v1.GuildSettings> guilds = 1;
}

message GuildSettings {
    map<fixed64, discord_protos.discord_users.v1.ChannelSettings> channels = 1;
    uint32 hub_progress = 2;
    uint32 guild_onboarding_progress = 3;
    google.protobuf.Timestamp guild_recents_dismissed_at = 4;
    bytes dismissed_guild_content = 5;
}

message ChannelSettings {
    bool collapsed_in_inbox = 1;
}

message UserContentSettings {
    bytes dismissed_contents = 1;
    google.protobuf.StringValue last_dismissed_outbound_promotion_start_date = 2;
    google.protobuf.Timestamp premium_tier_0_modal_dismissed_at = 3;
}

message VoiceAndVideoSettings {
    discord_protos.discord_users.v1.VideoFilterBackgroundBlur blur = 1;
    uint32 preset_option = 2;
    discord_protos.discord_users.v1.VideoFilterAsset custom_asset = 3;
    google.protobuf.BoolValue always_preview_video = 5;
    google.protobuf.UInt32Value afk_timeout = 6;
    google.protobuf.BoolValue stream_notifications_enabled = 7;
    google.protobuf.BoolValue native_phone_integration_enabled = 8;
}

message TextAndImagesSettings {
    google.protobuf.StringValue diversity_surrogate = 1;
    google.protobuf.BoolValue use_rich_chat_input = 2;
    google.protobuf.BoolValue use_thread_sidebar = 3;
    google.protobuf.StringValue render_spoilers = 4;
    repeated string emoji_picker_collapsed_sections = 5 [packed = false];
    repeated string sticker_picker_collapsed_sections = 6 [packed = false];
    google.protobuf.BoolValue view_image_descriptions = 7;
    google.protobuf.BoolValue show_command_suggestions = 8;
    google.protobuf.BoolValue inline_attachment_media = 9;
    google.protobuf.BoolValue inline_embed_media = 10;
    google.protobuf.BoolValue gif_auto_play = 11;
    google.protobuf.BoolValue render_embeds = 12;
    google.protobuf.BoolValue render_reactions = 13;
    google.protobuf.BoolValue animate_emoji = 14;
    google.protobuf.UInt32Value animate_stickers = 15;
    google.protobuf.BoolValue enable_tts_command = 16;
    google.protobuf.BoolValue message_display_compact = 17;
    google.protobuf.UInt32Value explicit_content_filter = 19;
    google.protobuf.BoolValue view_nsfw_guilds = 20;
    google.protobuf.BoolValue convert_emoticons = 21;
    google.protobuf.BoolValue expression_suggestions_enabled = 22;
    google.protobuf.BoolValue view_nsfw_commands = 23;
    google.protobuf.BoolValue use_legacy_chat_input = 24;
}

message NotificationSettings {
    google.protobuf.BoolValue show_in_app_notifications = 1;
    google.protobuf.BoolValue notify_friends_on_go_live = 2;
    fixed64 notification_center_acked_before_id = 3;
}

message PrivacySettings {
    google.protobuf.BoolValue allow_activity_party_privacy_friends = 1;
    google.protobuf.BoolValue allow_activity_party_privacy_voice_channel = 2;
    repeated fixed64 restricted_guild_ids = 3;
    bool default_guilds_restricted = 4;
    bool allow_accessibility_detection = 7;
    google.protobuf.BoolValue detect_platform_accounts = 8;
    google.protobuf.BoolValue passwordless = 9;
    google.protobuf.BoolValue contact_sync_enabled = 10;
    google.protobuf.UInt32Value friend_source_flags = 11;
    google.protobuf.UInt32Value friend_discovery_flags = 12;
    repeated fixed64 activity_restricted_guild_ids = 13;
    discord_protos.discord_users.v1.GuildActivityStatusRestrictionDefault default_guilds_activity_restricted = 14;
    repeated fixed64 activity_joining_restricted_guild_ids = 15;
    repeated fixed64 message_request_restricted_guild_ids = 16;
    google.protobuf.BoolValue default_message_request_restricted = 17;
    google.protobuf.BoolValue drops_opted_out = 18;
    google.protobuf.BoolValue non_spam_retraining_opt_in = 19;
}

message DebugSettings {
    google.protobuf.BoolValue rtc_panel_show_voice_states = 1;
}

message GameLibrarySettings {
    google.protobuf.BoolValue install_shortcut_desktop = 1;
    google.protobuf.BoolValue install_shortcut_start_menu = 2;
    google.protobuf.BoolValue disable_games_tab = 3;
}

message GuildFolder {
    repeated fixed64 guild_ids = 1;
    google.protobuf.Int64Value id = 2;
    google.protobuf.StringValue name = 3;
    google.protobuf.UInt64Value color = 4;
}

message FavoriteChannel {
    string nickname = 1;
    discord_protos.discord_users.v1.FavoriteChannelType type = 2;
    uint32 position = 3;
    fixed64 parent_id = 4;
}

message AudioContextSetting {
    bool muted = 1;
    float volume = 2;
    fixed64 modified_at = 3;
}

message Versions {
    uint32 client_version = 1;
    uint32 server_version = 2;
    uint32 data_version = 3;
}

message StatusSettings {
    google.protobuf.StringValue status = 1;
    discord_protos.discord_users.v1.CustomStatus custom_status = 2;
    google.protobuf.BoolValue show_current_game = 3;
}

message LocalizationSettings {
    google.protobuf.StringValue locale = 1;
    google.protobuf.Int32Value timezone_offset = 2;
}

message AppearanceSettings {
    discord_protos.discord_users.v1.Theme theme = 1;
    bool developer_mode = 2;
    discord_protos.discord_users.v1.ClientThemeSettings client_theme_settings = 3;
}

message GuildFolders {
    repeated discord_protos.discord_users.v1.GuildFolder folders = 1;
    repeated fixed64 guild_positions = 2;
}

message Favorites {
    map<fixed64, discord_protos.discord_users.v1.FavoriteChannel> favorite_channels = 1;
    bool muted = 2;
}

message AudioSettings {
    map<fixed64, discord_protos.discord_users.v1.AudioContextSetting> user = 1;
    map<fixed64, discord_protos.discord_users.v1.AudioContextSetting> stream = 2;
}

message CommunitiesSettings {
    google.protobuf.BoolValue disable_home_auto_nav = 1;
}

message VideoFilterBackgroundBlur {
    bool use_blur = 1;
}

message VideoFilterAsset {
    fixed64 id = 1;
    string asset_hash = 2;
}

message CustomStatus {
    string text = 1;
    fixed64 emoji_id = 2;
    string emoji_name = 3;
    fixed64 expires_at_ms = 4;
}

message ClientThemeSettings {
    google.protobuf.UInt64Value primary_color = 1;
}
```