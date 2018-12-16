# Skinny Mac Menubar Memory Monitor

Mac Menubar Memory Monitor - a skinny implementation in bash

Why? Because 4GB RAM Macs are now on the verge of non-viability for ordinary use and 8GB Macs are only viable for development if you can sweep the cruft off the machine, and close out of applications that you're not using.

While companies making software are fee to use whatever programing languages, frameworks and libraries they like, they should worry about RAM usage. Particularly for the menu-bar doohickeys come with the hope that they're not eating much resources. As companies release successive version of applications and base technologies they invariably slowly bloat their apps. That's bigger downloads, installs, and memory usage while running. CPU use too, but that's not the focus of this script. This goes for the operating system itself, too, which is one reason that seasoned veterans of MacOS don't snap update from Sierra to High Sierra or Mojave. Anyway, this skinny almost non-tech (and crude database) is about menubar app RAM usage

## Running it

Download the adjacent `smmmm` script and shove it in `/usr/bin/` (err, has downsides) or `/usr/local/bin` (Homebrew command to follow)

```
smmmm
```

Or run it from GitHub's raw server:

```
curl https://raw.githubusercontent.com/paul-hammant/skinny_mac_menubar_memory_monitoring/master/smmmm | bash -s
```

## MenuBar apps looked for

Rough order to memory requirements (descending)

1. Docker's Container virtualization tech (Swift & Objective-C for UI and Mac bits at least; 500 to 1500 MiB)
1. Skype Helper - voice/video conf calls (Electron framework; 250 MiB)
1. Avira Anti Virus (Qt + C++; 160 MiB)
1. Google Drive file sync (Chromium Embedded; 90 MiB)
1. JetBrains Toolbox - downloads updates for Intellij IDEA, PyCharm, etc (Qt+QML+C++; 30-90 MiB)
1. Jing - Techsmith's screen-cap tool (Objective-C, 78 MiB)
1. Wunderlist - keeps TODO lists  (21 MiB)
1. 1Password password manager (7 MiB or so)
1. Express VPN (13 MiB or so)
1. Dr Cleaner - cleans away cruft from machine when needed
1. Get Plain Text - removes formatting from rich text (61 MiB)
1. ZoomOpener - launches Zoom.us for video conf calls (6 MiB)

(1 MiB = 1024 * 1024 bytes, ref [wikipedia article](https://en.wikipedia.org/wiki/Mebibyte))

On Docker - it is really difficult to tell which processes are to do with the menu-bar presence (pseudo background), and which are to do with active, passive or ready to go virtualization, so I'm adding it all together for memory usage above.

## Sample output

Percentage of RAM, memory K, process-ID, command that was launched.

```
0.9  78864 38952 /Applications/Jing.app/Contents/MacOS/Jing
 0.4  34304  1040 /Applications/JetBrains Toolbox.app/Contents/jetbrains-toolbox-cef.app/Contents/Frameworks/jetbrains-toolbox-cef-helper.app/Contents/MacOS/jetbrains-toolbox-cef-helper
 0.4  31524   968 /Applications/Google Drive File Stream.app/Contents/Frameworks/Google Drive File Stream Helper.app/Contents/MacOS/Google Drive File Stream Helper
 0.3  27808   922 /Applications/Google Drive File Stream.app/Contents/MacOS/Google Drive File Stream
 0.3  23820   859 2BUA8C4S2C.com.agilebits.onepassword4-helper
 0.3  21368   887 QA2G25RMZ4.com.wunderkinder.wunderlist-helper
 0.2  16624   996 /Applications/JetBrains Toolbox.app/Contents/jetbrains-toolbox-cef.app/Contents/MacOS/jetbrains-toolbox-cef
 0.2  16432  1899 /Applications/Google Drive File Stream.app/Contents/Frameworks/Google Drive File Stream Helper.app/Contents/MacOS/Google Drive File Stream Helper
 0.2  15848   878 /Applications/JetBrains Toolbox.app/Contents/MacOS/jetbrains-toolbox
 0.2  14020  5765 /Applications/1Password 6.app/Contents/Library/LoginItems/2BUA9C4S2C.com.agilebits.onepassword4-helper.app/Contents/MacOS/OnePasswordNativeMessageHost
 0.1  11120   872 /Applications/ExpressVPN.app/Contents/MacOS/expressvpnd
 0.1  10196  1018 /Applications/JetBrains Toolbox.app/Contents/jetbrains-toolbox-cef.app/Contents/Frameworks/jetbrains-toolbox-cef-helper.app/Contents/MacOS/jetbrains-toolbox-cef-helper
 0.1   5740   898 /Applications/Google Drive File Stream.app/Contents/MacOS/Google Drive File Stream
 0.1   5228   900 /Users/paul/.zoomus/ZoomOpener.app/Contents/MacOS/ZoomOpener
 0.1   5160   572 /Applications/Google Drive File Stream.app/Contents/PlugIns/FinderSyncExtension.appex/Contents/MacOS/FinderSyncExtension
 0.0   3328   919 /Applications/Google Drive File Stream.app/Contents/MacOS/crashpad_handler
 ```

## Contributing to it

Pull requests adding lines to this README.md and the `smmmm` script please.