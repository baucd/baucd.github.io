---
title: devices customizations
date: 2021-12-03 16:13:09
tags: 
 - Linux
 - macos
categories: coding
---
# Arch Linux PC Customization

For the convenience of migrating my Arch Linux and MacOS operating system to new computers, I create this note to help me and others to customize the new hardwares.

## Desktop Environment

I don't like and use those ***heavy*** desktops such as KDE or GNOME. Because they are too large and redundant. Most of their features are totally useless for me. So my philosophy of operating system is ***KISS*** (keep it simple and stupid).

- small but exclusive program
- good extendiability, customizable
- connect and corporate with other program easily

At the same time, I also value the GUI softwares. I am not totally against GUI. In some occassions, GUI softwares are way better than CLI ones such as Markdown editor, Adobe's family etc. For coding, IDE and vim/emacs have their own merits and shortcomings. It depends on the people and requirements to make the choice.

### Window Manager

***i3-gaps*** is my choice. I am in favor of tiling window manager over floating window manager. All windows are sorted and well organized by tiling window manager. Tiling window manager also gives me the oppportunity to get rid of mouse in most cases. Customized keyboard shortcuts greatly enhance the efficiency of window operations.

### Status Bar

The information that needs to be displayed on status bar are

- workspaces and current workspace
- internet connectivity
- hardware status: CPU, GPU usage, temperature, connection speed (upload/download), current time and date
- other applets

Menu bar is not necessary. In most cases, keyboard shortcuts are enough. ***polybar*** is my choice.

### Notification Center

Use ***dunst*** to push notification.

## Coding Environments

### Terminal Emulator

***URXVT*** is great.

- Very small and consume very little resources
- use ***.Xresources*** to config
- good extendibility

### Shell

***zsh*** is the best! I have modified some of the ***oh-my-zsh*** themes to suit my need. ***zsh*** with ***git*** support is great. However, I also have a very nice ***.bashrc*** for ***bash***. Bash is the choice on most computational servers.

### Editor

Vim is the editor that I used since I learnd to use Linux systems. And my customized Vim settings including plugins and themes have been backuped to Gitlab of T03 at https://code.itp.ac.cn/baucd/vim_settings. By the way, my ***dotfiles*** are backuped to https://code.itp.ac.cn/baucd/dotfiles. Most of the config files are in ***dotfiles***.

### Terminal Multiplexer

Why **tmux** is important? For me, the most useful function is **session management**.

- session management
- session management on remote headless server
- window tiling and multiplexing
- easy to save current working environment (with help of **tmux-resurrect** plugin)

By the way, thanks **oh-my-tmux** project!

### Version Management

***Git*** is a great gift from Linus. git works well with zsh, ***tig*** and ***icdiff***. **zsh** is also good partner of **git**.

### Compilers

#### Fortran Compilers

Firstly one can install gfortran and gcc for testing the code. However, for the sake of performance, the Intel compiler is the best option. I backup the installation package of 2013 version at ***seafile***. The license file is **NCOM\_L\_\_\_N433-7ZVC9N6P.lic** Also, for nvidia-gpus support, install ***PGI Fortran*** compiler.

#### Nvidia GPU Compilers

Install nvidia proprietary driver on Arch Linux is simple, just use ***pacman***. Install ***CUDA*** is also simple on Arch Linux. Actually, install ***Intel*** compiler is also simple on Arch Linux, just to apply for license yourself and put them into the corresponding folder.

#### MPI Compilers

In most cases, I use ***mpich***, but ***openmpi*** is also needed especially for ***GPU*** support. I use the MPICH 3.2 for MPI application. One can build it from source by the following command

> ./configure C=gcc CXX=g++ F77=ifort FC=ifort -prefix=/home/alexchen/mpich-install --enable-shared

###Libraries

- MKL from Intel
- Openblas with Lapack support, sequential or multi-threaded version
- cuBlas from CUDA, full support for BLAS.
- cuSolver from CUDA, partial supoort for Lapack
- Magma: full support of BLAS and Lapack on GPU

See the readme.md of **general\_cuda\_fortran_dqmc** git repo for instructions on how to compile **magma** library.

### Scripting Language

#### Shell

I have one complete set of shell scripts to submit jobs, fetch data, analyz data and make plots. But I already switched to Python.

#### Python

- My job manager and Plot maker.
- Web Crawler

## Browser

Browser is very important for anyone who uses Internet to gather information and entertainment. Requiremnts

- Extendibility. The basic functions are always too limitted. ***Safari*** is far from good enough from this perspective.
- Performance. Especially Video decoding. GPU hardware acceleration is rigid demand.

***Chrome*** and ***Chromium*** are choices for macos and Arch Linux separately. All extenstions bookmarks and settings are synced.

## Internet Environments

One basic need is to go across the ***GFW*** in Mainland China. The current solution to buy VPS and setup ***shadowsocks*** and ***v2ray*** to bypass the ***GFW***. However, the efficiency to VPN is largely affected by the route IPS provided. Another rigid demand is to have a private network connecting my devices regardless of locations and network structure. I firstly setup a P2P network connecting to IOP office devices using zerotier-one. Then through IOP route, I can connect to my VPN server, which is far more stable than ordinary network environments.

### By Pass GFW

- Shadowsocks with obfs
- V2Ray using tls and domain

### Private Network

I always need to use the IOP network to download papers, movies (IPV6 resources) and access my VPN server (VPS) as well as Seafile.

- Tinc layer 2 P2P VPN
- Zerotier-one: I find this more stable than tinc. Possible reason is that the zerotier-one communication server is more easily connected than tinc server (Guang-Yu Sun's VPS)

### Router

Openwrt router. Desired function:

- global proxy management for all connected devices
- AD filter
- Zerotier on router
- smart QoS
- customized DNS

## Scientific Environments

### Reference Management

**Mendeley desktop**. Free space is large enough, syncing between differnet devices. At the same time, I manage my references using seafile with the following two ways

- Seafile: **Knowledge_Library** for relatively earlier papers and books.
- Seafile: **Scientific\_Research/Projects\_Refs** for papers directly related to my projects. **Scientific\_Research/Recent\_Papers** for recent interesting papers.

### LaTeX Editor

***Texmaker*** plus ***vim*** and ***git-latexdiff*** build a relatively comfortable writing environment.

#### Important Update

With the help of Zhe Li, I start to using ***sublime text*** \+ ***skim*** to edit and view latex and pdf files. I also enable the ***vintage*** plugin to use **vi-mode** to edit code in sublime. Color scheme is **Dracula** as always. The environment is setup on my mac and I am going to setup the Linux as well.

### Notebook

- LyX: dealing with equations and formula, usually for my scientific projects
- Typora: markdown editor, making notes, basically pure text notes
- GoodNotes5: hand-written notes

### Mathematica

Useful to perform some analytical calculations.

## Entertainment Environments

- **Seafile**: on RPI4, serve as netdisk and syncdisk. Store my collections of musics, pictures, movies and my backups. I can mount fuse seafile through ***NFS***.
- **CMUS**: Console Music Player, together with **Apple Music** and **Xiami** (use for those not in Apple Music)
- **MPV**: video player, **IINA** on macOS
- **Steam**: Gaming on Linux, also Don't Starve Together dedicated server.
- **PT Downloader**: Setup on RPI4, allow me to have access to a lot of excellent multi-media resources.

## Backup and System Maintenance

### /etc

**etckeeper** will backup /etc files in a version contro manner. It is a automatic tool and will update the git repo when

- before and after pacman upgrades
- commit it on a daily basis using ***daily*** script with **cron**
- manually

### dotfiles

Use pure Git to backup $HOME dotfiles. Following the instructions on this Arch Linux wiki [git dotfiles](https://wiki.archlinux.org/index.php/Dotfiles#Tracking_dotfiles_directly_with_Git).

### Pacman Backups

- pacman packages list backup using **backup_packages.sh** script and the list is also controlled by **dotfiles** git repo.
- pacman local database backup using ***pakbak-git*** in aur

**In conclusion**, /etc will be backuped automatically. dotfiles are controlled by git and I should push the changes manually. As for the pacman, I have to manually backup the package list and the local database will be managed by ***pakbak-git*** automatically. **Manual operations**

- home folder dotfiles management
- pacman package list management

## Miscellaneous

### Other Useful Softwares

- **i7z** : CPU monitor
- **mendeley** : references management software
- **ubuntu-restricted-extras** : third-party decoders
- **fcitx-table-wbpy** : input method
- **gnuplot** : plot
- **filezilla** : ftp client
- **mpv** : player
- **htop** : system performance monitor
- **iftop** : system internet monitor
- **git** : version management
- **wps** : office
- **openssh-server** : ssh support
- **texlive** : Latex environment
- **texmaker** : tex file editor
- **matlab** : matlab
- **transmission-daemon** : command line torrent management software
- **nfs** : network file sharing
- **steam** : gaming platform
- **rime**: input method
- **ranger**: CLI filemanager
- **deepin-screenshot**: better than **shutter**, which has memory leak
- **tig**: nice tool to view git history
- **nmon**: CLI system monitor
- **cmus**: CLI music player
- **ncdu**: display disk usage (very nice tool, easy than **du**)
- **cloc**: count the lines of code
- **tldr**: very short version of man page
- **fuck**: correct the previous command
- **nethogs**: processes network activity statistics
- **s-tui**: stress test and performance monitor
- **fzf**: fuzzy search

### Adobe Family

- **Illustrator**: Edit bitmap image
- **Photoshop**: Edit photos
- Linux counterparts: **Inkscape** and **GIMP**

### Productivity

- **Lyx**: Latex editor aside from **Sublime-text**
  
- **Typora**: Markdown editor
  
- **XMind**: flowchart
  
- **TickTick**: agenda management
  
- **Apple Watch**: Activity and time management

### Social Network and Instant Messenger

**FUCK TENCENT**!

I am currently using ***telegram*** to fetch all WeChat messages. I also setup a **RSS robot** on VPS to automatically fetch interesting infomation from the sites I care. ***Telegram*** can fetch my Gmail as well. Now my phone msm and missed calls will also be pushed to ***telegram***.

I like ***slack*** and will use it when I have projects corporating with foreign groups.

# MacBook Pro Customization

Most of the configurations related to CLI are the same as Arch Linux counterparts.

## Touch ID in iterm2 and tmux

**Important**: everytime after upgrade of macos or ios, watchos, there are chances that the apple watch auto unlock will fail. In such case, please use the **keychain access** method or **sign out of iCloud on every device** or **re-pair the apple watch with iPhone**. One of them will work eventually, just have to try! 

### **sudo** with Touch ID and Apple Watch.

```
auth     optional     pam_reattach.so
auth     sufficient   pam_tid.so
```

add the above two lines to file /etc/pam.d/sudo and install **pam_reattach**

`brew install fabianishere/personal/pam_reattach`

to use Touch ID within **tmux** sessions. Note that everytime macOS does a major update, I have to rewrite the /etc/pam.d/sudo file.

### **sudo** with Apple Watch when lid is closed

A very nice open-source project to realize this function [pam-watchid](https://github.com/biscuitehh/pam-watchid).Add the following code to the first line of /etc/pam.d/sudo file

`auth sufficient pam_watchid.so "reason=execute a command as root"`

in total

```
auth     sufficient   pam_watchid.so "reason=execute a command as root"
auth     optional     pam_reattach.so
auth     sufficient   pam_tid.so
```

## CMUS

I use cmus as one of my two music players on macos (the other is of course Apple Music). CMUS is used to connect to my seafile Music library, playing my music collections.

[**cmus-osx**](https://github.com/PhilipTrauner/cmus-osx) will show track change notifications and enable media key control on cmus. When try to use media key to control the playback, only one of Apple Music or cmus can run in the background to avoid confusion (need [noTunes](https://github.com/tombonez/noTunes)). So use cmus, stop Apple Music and stop cmus when using Apple Music (after all, there is only one media key and macOS is not smart enough to distinguish the current playing source) .

## Tiling Window Manager

[**koekeishiya/yabai**](https://github.com/koekeishiya/yabai) is working and meets my requirements. I usually have four workspaces

- ws1 for telegram and all other sort of applications, floating mode
- ws2 for finder and pdf preview, floating mode
- ws3 for Chrome only, tiling mode
- ws4 for iterm2 only, tiling mode

## Python

### built-in python

Python's are shipped with macos by default. Two version of pythons but the default one is still python2.7

- python2: `/System/Library/Frameworks/Python.framework/Versions/2.7/bin/python2.7` or `/usr/bin/python`
- python3: `/usr/bin/python3`, now the version is 3.8.2. It is provided by the Xcode command line developer tools.

Default library paths are `/Applications/Xcode.app/Contents/Developer/Library/Frameworks/Python3.framework/Versions/3.8/lib/python3.8`, something like this. It is in the Xcode folders. Built-in python2 was never used by me explicitly.

### homebrew python

Python installed using homebrew are in

- python2: `/usr/local/bin/python2` or `/usr/local/Cellar/python@2/2.7.17_1/bin/python2`
- python3:`/usr/local/bin/python3` or `/Library/Frameworks/Python.framework/Versions/3.9/bin` or `/usr/local/Cellar/python@3.9/3.9.0/bin/python3`

Python libraries can be installed using two methods

- pip and pip3: these **pip** are provided by homebrew, but the libraries are from **PyPI** server.
- homebrew: `brew install numpy` etc. The libraries are from homebrew server.

The installation location is `/usr/local/lib/python3.x/site-packages` and `/usr/local/lib/python2.x/site-packages`.

### relations

Python -> Ipython (Ipykernel) -> JupyterLab

I am using all of the above products installed from **homebrew**.

- upgrade python3.x: need to reinstall libraries. Update only python3.x.y, no need to reinstall libraries.
- upgrade Ipython: nothing need to be done.
- upgrade JupyterLab: all extensions need to be reinstalled using **$HOME/bin/install\_jupyter\_extensions.sh**
- extensions for jupyterlab are
  - sudo pip install jupyter-lsp
  - sudo pip install jupyter_nbextensions_configurator
  - sudo pip install python-lsp-server


**About Jupyterlab**:

Every major upgrade: especially after upgrading python3 version via brew, please make sure **/Users/alexchen/Library/Jupyter/kernels/python3/kernel.json** set the python3 kernel in Jupyterlab correctly.

## Backups

**Time Machine** is good enough. I also use git to backup some **dotfiles**, now seems not necessary.

## Note Taking

**Joplin** \+ **Typora** very nice, Joplin supports using external markdown editor. Joplin with \*\*outline\*\* plugin [outline](https://github.com/cqroot/joplin-outline). Also with a chrome extension **Joplin Web Clipper**.

## Storage Management

Use system storage tool and command line tool **ncdu** to list large files and folders. Some caches can be cleaned to save my mac spaces. 

- XCode Caches: use the system storage management to clean xcode caches
- Chrome caches: use chrome itself to clean caches
- other useless data

# VPS, SBC and Router Customization

VPS and SBC such as Raspberry 4 are important assistant devices. They will serve as the following tools

- v2ray: proxy
- shadowsocks: proxy
- frp: reverse proxy
- telegram mtproxy: proxy
- gost: socks5 to http, proxy
- nginx+php: web server + reverse proxy
- seafile: netdisk
- pi-hole: dns
- telegram bots: wechat bot, rss bot and ys check in bot (on github)
- rsshub: rss
- zerotier-one: vpn
- transmission: PT downloader
- nfs: network sharing
- time machine: for macOS
- webhook via node.js: need to use **nvm** to force node.js 10 version, export **ENV** first
- ifttt: on Android
- cockpit

## VPS

VPS outside mainland China. The IP is quite useful. It will host

- network assistant
    - VPN: shadowsocks + v2ray
    - VPN: zerotier-one
- telegram bot (require IP outside mainland China)
    - RSS bot
    - WeChat bot
- personal website server
- frp server connects with **rpi4**'s frp client
- cockpit web 

## SBC

SBC is more powerful in terms of computational power and IO than the cheapest VPS. It will host

- PT downloader: use transmission to download PT torrents of IPV6 resources
- Seafile: cloud storage on the one hand and network sync-disk on the other hand
- TimeMachine: cloud backup for my macbook pro
- cockpit

and some network services

- Docker: host **rsshub** for me
- network assistant: zerotier-one and mainland China shadowsocks VPN server ( useful when I am outside mainland China)
- local DNS server: **pi-hole**
- transparent proxy: v2ray
- webhook downloader via nodejs https://github.com/DIYgod/download-webhook \+ ifttt + rsshub: **workflow** bilibili coined -> trigger rss feed -> ifttt send webhook request -> frp to **sbc** -\> trigger you-get download

Therefore, SBC will require a large size external hard drive to fulfill its missions.

## Router

Router is used to manage all network traffic of devices in local network. For better experience, we should use **opnewrt** based operating system for router. Some global functions can and actually should be installed on router instead of each individual device.

- VPN related:
    - zerotier-one: allow each device in local network to have access to my private zerotier network, very convenient.
    - global VPN: run shadowsocks or v2ray on router and setup autoswitch proxy rules. I have setup v2ray transparent proxy on **cc-arch**.
- traffic management:
    - QoS: QoS for local devices to avoid poor network quality when downloading something with full speed automatically.
    - hardware accelerated NAT: may conflict with QoS.
- services: experience improvements
    - local DNS server: maybe install pi-hole on **soft** router is a better choice.
    - AdBlocker: should be installed on router to filter Ad urls apart from browser plugins.

I will setup my openwrt router with two vlans, one with function of network switch and wireless ap (5G), another with routing and wireless routing (2.4G). Because I have two wireless cards.

## Summary of my current setup

**Running Servers**:

- **10.128.4.71**: **raspberry Pi 4** with 20TB disk
    - PT downloader
    - Seafile server: 10.128.4.71/seafile using nginx, and accessible through [public url](http://baucdlovechina.katsusama.xyz/seafile/accounts/login/). 10.28.4.71:8000 only for client not for web access
    - NFS server
    - shadowsocks server: iop-rpi4 for accessing APS papers and ipv6 resources
    - shadowsocks client: socks port 1234 use mainly for web browsers
    - v2ray transparent proxy server: for all my devices in 2.4G network and provide support for other 10.128.x.x machines. It is used as gateway, domestic DNS request is still through **pi-hole** (10.128.4.104). Other request will be handled by 8.8.8.8 via vps's proxy. By disabling the **destoverride** for tls, now the iOS notification and mtproxy are working within the tproxy environment. 
    - telegram MTProxy server (JSMTProxy, C version not working on aarch64)+frp client, use **tproxy** to connect to telegram servers, much stable than hosting MTProxy on VPS directly (still not stable with frp, useful when having access to 10.128.4.71)
    - cockpit
    - frp client connected to gysun's vps for socks5 port forwarding
    - 2021.05.11: media center setup, jellyfin + transmission-remote + nfs (relative high connection speed)
    - 2021.05.11: zerotier for iop networks
    - 2021.05.27: rsshub docker + frp port 1200
    - 2021.05.27: jd-scripts docker
- **10.128.4.104**: **rock64 sbc**
    - pi-hole: local DNS server for all my devices
    - rsshub (docker): my rsshub to fetch rss feed
    - zerotier client: necessary, because my vps must contact with it (172.26.0.10) to fetch and send rss feed via RSS telegram bot
    - zerotier client 2: for Zhe Li's network, access 10.128.4.71 for VPN
    - **zerotier gateway**: route to 10.128.4.x and 10.105.17.x machines in IOP network
    - cockpit
    - jellyfin: media center, now do not transcode (encode), use local player to decode (local jellyfin clients have no **hevc** deconding capability, even software deconding. Now safari clients can use its own hevc decoder to play the h265 videos). frp to **vps**. However, pi-hole is using 80 so that I cannot use nginx to reverse proxy for jellyfin as secondary page and then use frp to give it a domain. Just use port 8096 on **vps** domain. 
    - frp client port forwarding to my vps for rsshub, webhook downloader and jellyfin 
    - jd-scripts: for JD, need server chan for notification
    - 2021.05.11: zerotier just my private network **172.26.0.x**, not for iop anymore
    - 2021.05.11: jellyfin only for bilibili coined videos. Other multimedia resources are at **rpi4** 
    - 2021.05.11: v2ray + shadowsocks client of my vps
- **45.76.167.79**: **vps**
    - shadowsocks server
    - v2ray server with tls support
    - telegram MTProxy server (not working actually because of port being blocked). Now working with TLS support
    - zerotier client:
        - necessary, need to contact with **rock64 sbc** to fetch rss feed from rsshub
        - necessary, need to contact with **rpi4** to proxy for seafile, now use http://baucdlovechina.katsusama.xyz/seafile/accounts/login as its public domain
    - frp server:
        -  mainly connect with **rpi4**'s client for telegram MTProxy server + tproxy
        -  rsshub server and webhook downloader on **sbc**
        -  jellyfin server on **sbc**
        -  webhook downloader on **sbc**
    - telegram Bots:
        - WeChat bot
        - RSS bot: now using flowerss_bot
    - nginx reversed proxy
        - my wordpress blog as root
        - T03 Seafile server on **rpi4**, need zerotier-one
        - T03 Seafile webDAV support, need zerotier-one. webDAV is used to sync my **Joplin** notebooks
        - frps dashboard on **vps** , need frp: **not working**, seems it is a dynamic site, don't know how to properly proxy it.
        - rsshub server on **sbc**, need frp
        - webhook downloader on **sbc**, need frp
        - cockpit webpage interface, monitoring the status of **sbc + rpi4 + ccarch + vps**
    - cockpit: use nginx to reverse proxy the web dashboard. On Arch Linux machines, one has to
        - install cockpit, use ```systemctl start cockpit.service``` to start the cockpit. use ```systemctl enable --now cockpit.socket``` for auto-start.
        - install cockpit-pcp, use ```systemctl start pmcd.service``` plus (sometimes needed) ```systemctl start pmlogger.service``` to start the graphics stats.
- cloud platforms:
    - github: genshin check in helper
    - heroku: telegram image collector, need **mega** and **google firebase** support

**Running Clients**:

**10.128.4.105**: **Newifi Pandorabox**

- AP mode: wired and 5G wlan work in AP mode to give my device 10.128.x.x ip
- AC mode: 2.4G wlan work in routing mode for my mobile devices such as phone, iPhone, iPad and watch
- zerotier client: necessary, make my 2.4G wlan network (mobile devices) have access to 172.26.0.x devices (actually all 10.128 and 10.105 machines because of zerotier gateway on 172.26.0.10 sbc machine)
- 2.4G network uses **tproxy** machine as gateway such that my mobile devices all have access to blocked websites

**Backup Servers**:

- **10.128.4.107**: **cc-arch**
    - serve as backup of my v2ray tproxy
    - my pbs job management system
    - Don't Starve Together Dedicated Server
    - cockpit
- **10.128.4.42**: **gitserver**
    - mainly serve as backup for **rpi4**'s duties

## Some Notes

2021.10.11: After reboot, I need to ssh to rpi4 to start

- jellyfin service
- frp
- gosh, for the 8080 port
- tsm-daemon
- docker->rsshub

# Android Phone Customization

I use phone for what? The following

- Basic communications: answer phone call and receive text messages (mainly verification code)
- Taking pictures and videos, scan QR code
- Gaming: Honkai3rd and Genshin impact
- Social Networking and Instant Messenging: WeChat, Bilibili, Douban, Zhihu and Stackexchange etc
- Finance Apps: many bank apps including Alipay, JD and WeChat
- Other apps

The most important apps on phone are

- Telegram: I use telegram to collect all of my messages even including the WeChat messages. And luckily I can use mtproxy+faketls to connect to telegram server without the help of shadowsocks or v2ray client app.
- Browser: **kiwi** browser + switchyomega with frp, I can access my proxy server hosted inside iop office. I can access Google search without the need o f shadowsocks or v2ray client app.  As for other app that need proxy, I can use shadowsocks or v2ray client app.

## Ads Block

**light start** will help me skip the opening ads of most apps automatically. It is a necessity for me now.

## Information Forwarding

Use **IFTTT** to forward missed phone calls and SMS to telegram **IFTTT** bot. So that basically all of the my information will be collected and manged by telegram.

## Across the GFW

Use **shadowsocks** plus **GFW list** to connect to Google etc and bypass the domestic sites. And **IFTTT** will need **shadowsocks** to work normally. In conclusion, **shadowsocks** and **IFTTT** have to run all the time in the background as well as the **light start**.

# iPad Pro Customization

iPad Pro for two requirements

- **GoodNotes5**: pdf reading and annotations with Apple Pencial
- **GoodNotes5**: handwritten notes
- Social Networking: bilibili, zhihu and douban etc. With **Bigger** screen than phone
- Shopping apps: **Bigger** screens
- Gaming experience should be better, but I don't play those casual games on iPad. I choose Steam, miHoYo and Windows.

# Windows PC Customization

The sole purpose of having a Windows PC is for gaming. So I need nothing not related to gaming. However, the following necessities should be installed

- Chrome, browser
- telegram client
- miHoYo n0va desktop, wallpaper

As for the gaming platforms, I have selected the following ones

- Steam: most of my games are in Steam
- Ubisoft: some games collected when they are free (3A)
- miHoYo: Honkai 3rd (include mumu emulator) and Genshin Impact
