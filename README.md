# Public IP Address widget for KDE 5

## Description

Plasma 5 widget for showing informations about your public IP address and the status of your VPN (active/inactive). This is useful for informational purposes and to monitor VPN geolocation.

The expanded view shows a map with informations requested from [ipinfo.com](https://ipinfo.io/): you can copy to clipboard the different informations by clicking over them. You can also open the map on the browser, and update the informations by sending another request.

By default, the widget update itself every 5 minutes. You can change this behaviour in the settings. Please note that [ipinfo.com](https://ipinfo.io/) API limits the total amount of requests to 1000 per day: this means that the plugin will update itself at most every 2 minutes.

You can change the colors of the displayed informations in the settings.

This widget uses the [excellent flags icon pack by lipis and contributors](https://github.com/lipis/flag-icon-css).

![tooltip screenshot](screenshots/screenshot_4.png)
![expanded screenshot](screenshots/screenshot_3.png)

## Dependencies

The primary functions of the widget (check IP address) should work correctly even if the following dependencies are not installed. Anyway, to get the best experience you need:

* `libnotify-bin`: this is for showing notifications when clicking links, thus copying the link's content to the clipboard.  
`sudo apt install libnotify-bin`
* `nmcli`: this is part of the `network-manager` package. It'll check the status of the VPN by executing the command `nmcli c show --active`; if a VPN is active, there should be some entries containing the keywords `vpn` or `tun`. It should already be installed in Ubuntu. Don't know about other distros (let me know in the comments or by opening an issue).

## Installation

### From openDesktop.org

1. Go to **[Open Desktop](https://www.opendesktop.org/p/1289644/)**
2. Click on the Files tab
3. Click the Install button

### From within the Plasma workspace

1. If your widgets are locked, right-click the desktop and select `Unlock Widgets`
2. Right-click the desktop and select `Add Widgets...`
3. Click the `Get new widgets` button in the Widget Explorer that just opened
4. Type `Public IP Address` into the search field
5. Click the `Install` button next to `Public IP Address`

## FAQ

### The widget is not working. There are errors about `QtPositioning` and `QtLocation`. What can I do?

It may happens that the widget does not load, complaining about something like `QtPositioning` and `QtLocation`. If this is the case and you are using Ubuntu (18.04), run this command:

`sudo apt-get install libqt5positioning5 libqt5location5 qtlocation5-dev qtpositioning5-dev qml-module-qtlocation qml-module-qtpositioning`

In any other distribution, you must look for libraries regarding *qt5 positioning* and *qt5 location*, as well the development libraries and the *qml bindings*.

### Can you add an option to use a different map provider other than OpenStreetMap?

No, because most other map providers require an API key, whereas OSM does not need it. This means everyone should be able to view the map.
