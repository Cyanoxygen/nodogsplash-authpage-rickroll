# Rickroll using NoDogSplash

Prerequisites
------

- An OpenWrt wireless router:
  - To set up Guest WiFi and run NoDogSplash instance for it

- This set of pages
  - To replace the corresponding files
  - `splash.html` is shown when a guest is connected and waiting for authentication
  - `status.html` is shown if a guest visited authentication page while already authenticated.

- Never Gonna Give You Up MV
  - You can download it in your way, i.e. download this [YouTubu video](https://www.youtube.com/watch?v=dQw4w9WgXcQ) using youtube-dl or some other tool, or download it from [archive.org](https://archive.org/details/kikTXNL6MvX6ZpRXM).
  - The video file resides on `imgs/rickroll.mp4`.

Adding Guest WiFi in OpenWrt
------

Follow this [guide](https://openwrt.org/docs/guide-user/network/wifi/guestwifi/configuration_webinterface) to set up a proper isolated Guest WiFi on your OpenWrt router.

Installing NoDogSplash 
------

NDS is in OpenWrt official package feeds. Just install it as you install other packages:

```
opkg update
opkg install nodogsplash
```

Configuring NoDogSplash
------

The UCI configuration for NDS is at `/etc/config/nodogsplash`.

Edit it with your favorite editor, you need to change a few settings:

1. Listening interface  
    NDS should listen to a device interface such as `br-lan`, `wlan0-1`.

2. Gateway Name   
    In this auth page the `$gatewayname` is never used.

This site uses basic authentication method, so no further changes needed.

NDS Documentation can be visited at https://nodogsplashdocs.readthedocs.io/en/stable/index.html.

Putting this page
------

Once done you can try connecting your Guest WiFi, a default authentication page should pop up.

After confirming that the configuration is correct, you can copy these pages to `/etc/nodogsplash/htdocs/`.

The video should be in `/etc/nodogsplash/htdocs/imgs/rickroll.mp4`.