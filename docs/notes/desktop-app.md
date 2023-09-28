# Desktop Application

## Application

You can download the application at  
`https://dl.discordapp.net/apps/linux/<version>/discord-<version>.deb`  
`https://dl.discordapp.net/apps/osx/<version>/Discord.dmg`  
`https://dl.discordapp.net/distro/app/stable/win/x86/<version>/DiscordSetup.exe`  

Examples as of September 28, 2023:  
`https://dl.discordapp.net/apps/linux/0.0.30/discord-0.0.30.deb`  
`https://dl.discordapp.net/apps/osx/0.0.278/Discord.dmg`  
`https://dl.discordapp.net/distro/app/stable/win/x86/1.0.9018/DiscordSetup.exe`  

You can use the [web archive](https://web.archive.org/web/20230000000000*/https://discord.com/download) to access old version codes.  

## Native Modules

You can download the modules at  
`https://dl.discordapp.net/apps/linux/<version>/modules/<module name>-<module version>.zip`  
`https://dl.discordapp.net/apps/osx/<version>/modules/<module name>-<module version>.zip`  
`https://dl.discordapp.net/distro/app/stable/win/x86/<version>/<module name>/<module version>/full.distro`  

Examples as of September 28, 2023:  
`https://dl.discordapp.net/apps/linux/0.0.30/modules/discord_desktop_core-1.zip`  
`https://dl.discordapp.net/apps/osx/0.0.278/modules/discord_desktop_core-1.zip`  
`https://dl.discordapp.net/distro/app/stable/win/x86/1.0.9018/discord_desktop_core/1/full.distro`  

## Downloading script
Here is a script that downloads all clients as of January 1, 2023, and all modules for all three platforms.  

??? info "Downloading script"
    ```sh title="download.sh" linenums="1"
    #!/bin/bash
    set -eu

    # release date: 2022-12-10
    VERSION_LINUX="0.0.22"

    # release date: 2022-12-10
    VERSION_OSX="0.0.270"

    # release date: 2022-12-09
    VERSION_WIN="1.0.9008"

    # you can add additional module array for different version and copy-paste "for" below.
    #   MODULES_V2="discord_somenewmodule"
    #
    # for example: version as of 2023-09-28 has module discord_voice version 4
    #   MODULES_V1="discord_cloudsync discord_desktop_core discord_dispatch discord_erlpack discord_game_utils discord_krisp discord_modules discord_rpc discord_spellcheck discord_utils"
    #   MODULES_V4="discord_voice"
    #   ...
    #   pushd modules
    #     for module in $MODULES_V1; do
    #       wget "https://dl.discordapp.net/apps/linux/$VERSION_LINUX/modules/$module-1.zip"
    #     done
    #
    #     for module in $MODULES_V4; do
    #       wget "https://dl.discordapp.net/apps/linux/$VERSION_LINUX/modules/$module-4.zip"
    #     done
    #   popd
    MODULES_V1="discord_cloudsync discord_desktop_core discord_dispatch discord_erlpack discord_game_utils discord_krisp discord_modules discord_rpc discord_spellcheck discord_utils discord_voice"

    # create directories
    mkdir -p linux/modules
    mkdir -p osx/modules
    mkdir -p windows/modules

    # linux & modules
    pushd linux
      wget "https://dl.discordapp.net/apps/linux/$VERSION_LINUX/discord-$VERSION_LINUX.tar.gz"

      pushd modules
        for module in $MODULES_V1; do
          wget "https://dl.discordapp.net/apps/linux/$VERSION_LINUX/modules/$module-1.zip"
        done
      popd
    popd

    # osx & modules
    pushd osx
      wget "https://dl.discordapp.net/apps/osx/$VERSION_OSX/Discord.dmg"

      pushd modules
        for module in $MODULES_V1; do
          wget "https://dl.discordapp.net/apps/osx/$VERSION_OSX/modules/$module-1.zip"
        done
      popd
    popd

    # windows & modules
    pushd windows
      wget "https://dl.discordapp.net/distro/app/stable/win/x86/$VERSION_WIN/DiscordSetup.exe"

      pushd modules
        for module in $MODULES_V1; do
          wget "https://dl.discordapp.net/distro/app/stable/win/x86/$VERSION_WIN/$module/1/full.distro" -O "$module.tar.br"
        done
      popd
    popd
    ```
