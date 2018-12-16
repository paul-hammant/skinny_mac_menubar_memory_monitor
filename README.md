# Skinny Mac Menubar Memory Monitor

Mac Menubar Memory Monitor - a skinny implementation in bash

Why? Because 4GB RAM Macs are now on the verge of non-viability for ordinary use and 8GB Macs are only viable for development if you can sweep the cruft off the machine, and close out of applications that you're not using.

While companies making software are fee to use whatever programing languages, frameworks and libraries they like, they should worry about RAM usage. Particularly for the menu-bar doohickeys come with the hope that they're not eating much resources. As companies release successive version of applications and base technologies they invariably slowly bloat their apps. That's bigger downloads, installs, and memory usage while running. This goes for the operating system itself, too, which is one reason that seasoned veterans of MacOS don't snap 
update from Sierra to High Sierra or Mojave. Anyway, this skinny almost non-tech (and crude database) is about menubar apps.

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
1. JetBrains Toolbox - downloads updates for Intellij, PyCharm, etc (Qt+QML+C++; 30-90 MiB)
1. Jing - Techsmith's screen-cap tool (Objective-C, 78 MiB)
1. Wunderlst - keeps TODO lists  (21 MiB)
1. 1Password password manager (7 MiB or so)
1. Express VPN (13 MiB or so)
1. Dr Cleaner - cleans away cruft from machine when needed
1. ZoomOpener - launches Zoom.us for video conf calls (6 MiB)

(1 MiB = 1024 * 1024 bytes, ref [wikipedia article](https://en.wikipedia.org/wiki/Mebibyte))

On Docker - it is really difficult to tell which processes are to do with the menu-bar presence (pseudo background), and which are to do with active, passive or ready to go virtualization, so I'm adding it all together for memory usage above.

## Contributing to it

Pull requests adding lines to this README and the `smmmm` script please.