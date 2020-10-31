# Actions-OpenWrt

Build OpenWrt and publish docker image using GitHub Actions

Credit to ***P3TERX***, ***bin20088*** and ***flippy***，this is just a combination of their work.

The firmwares released are for S9xxx devices, Newifi_D2, G-Dock, amd64 and the J4125 with rtl8125 ethernet device.

Feel free to [fork](https://github.com/HoldOnBro/Actions-OpenWrt/generate) or just pull [my docker image](https://hub.docker.com/r/minirailgun/openwrt-aarch64/tags) to save time, it will be updated everyday.

## How to Use

You need to add 4(at least 3) secrets to make Actions work.

1. **RELEASES_TOKEN**, which should be your Github **Personal Access Token** with at least the *public_repo* checked.
2. **DOCKER_USERNAME** is your dockerhub username.
3. **DOCKER_PASSWORD**, which is actually not the password for your dockerhub account but the **Access Token** generated from dockerhub Account Settings.
4. **ServerChan**(Optional, but remember to comment out relational action in ymls) , the **SCKEY** for your serverchan account. [click here for more information](http://sc.ftqq.com/3.version)

[P3TERX大佬写的中文教程|Usage Guide in Chinese](https://p3terx.com/archives/build-openwrt-with-github-actions.html)


## Some Hints

### NetData
  If NetData doesn't work correctly,

  Take N1 as an example,

  SSH into container and run command :``chown -R root:root /usr/share/netdata/``

  then refresh the ``IP:19999``, it should be working properly.

### IP and Password
  Default IPs for those devices can be found in bash scripts (``DEVICE_NAME.sh``) associated with them.
  
  Password by default is ``password``.
  
### aarch64
  There are three versions of firmware for this arch.
  
  The ones without prefix contain no Acc applications.
  
  Those named as ``S-*`` are SFE type, they are faster but not fully tested, may have some instability issues.
  
  And the ones named as ``F-*`` are flowoffload type, stable but a little bit slower.
  
  Choose ``S-*`` type if you feel adventurous or use the other ones for convenience.

### Newifi_D2
  There are three versions for Newifi_D2.
  
  1. **Basic Version**: Basic version has ipv6 support, full ssr-plus(equipped with **TUN**) and unblocknetease(with **NodeJS**) just like other guys' versions.
  
  2. **Normal Version**: It contains all functions **Basic Version** have and syncdial.
  
  3. **Lite Version**: Lite version is based on the **Normal Version** but lacks jd-daily-bonus, TUN and NodeJS, Instead, it has **transmission** and **samba4**.
  
  The one and only reason for making two versions for Newifi_D2 is it has such a tiny flash memory.
  
  Just choose the one suits your need.
  
~~BTW, if you encounter any hardware instability problems like auto-reboot for no reason, having no access to Internet,~~
  ~~**TURN OFF** the **HWNAT** under ``network->hwacc``.~~
  ~~Refer to [1](https://github.com/coolsnowwolf/lede/issues/4531), [2](https://github.com/openwrt/openwrt/pull/1916) for more details.~~
  ~~Or you can use the [PandoraBox](http://downloads.pangubox.com:6380/), it has **NO** HWNAT issues.~~

## Acknowledgments

- [P3TERX/Actions-OpenWrt](https://github.com/P3TERX/Actions-OpenWrt)
- [bin20088/Bin](https://github.com/bin20088/Bin)
- [Microsoft](https://www.microsoft.com)
- [Microsoft Azure](https://azure.microsoft.com)
- [GitHub](https://github.com)
- [GitHub Actions](https://github.com/features/actions)
- [tmate](https://github.com/tmate-io/tmate)
- [mxschmitt/action-tmate](https://github.com/mxschmitt/action-tmate)
- [csexton/debugger-action](https://github.com/csexton/debugger-action)
- [Cisco](https://www.cisco.com/)
- [OpenWrt](https://github.com/openwrt/openwrt)
- [Lean's OpenWrt](https://github.com/coolsnowwolf/lede)
- [Cowtransfer](https://cowtransfer.com)
- [WeTransfer](https://wetransfer.com/)
- [Mikubill/transfer](https://github.com/Mikubill/transfer)
