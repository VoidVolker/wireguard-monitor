# wireguard-monitor

[![Join the chat at https://gitter.im/VoidVolker/wireguard-monitor](https://badges.gitter.im/VoidVolker/wireguard-monitor.svg)](https://gitter.im/VoidVolker/wireguard-monitor?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

Simple bash script for monitoring current IP and WireGuard status in Xfce tray.

# Requirements

* Xfce desktop
* Installed genmon-plugin: https://docs.xfce.org/panel-plugins/xfce4-genmon-plugin
```bash
sudo apt install xfce4-genmon-plugin
```

# Install

Go to your favorite directory for scripts:
```bash
mkdir ./scripts
cd ./scripts
```

Clone repository:
```bash
git clone https://github.com/VoidVolker/wireguard-monitor
```

Add genmon widget
```bash
xfce4-panel --add genmon
```

Now you need to get widget name. To get this name, go to the panel properties screen and on the Items tab, hover your mouse over the genmon plugin to get it's internal name.

You will get: ```genmon-X```. Where `X` is plugin number. Example: `genmon-10`. Use this number as first argument for script. Plugin name used for plugin refresh via icon click.

Go to genmon plugin properties and add next settings:

* Command: `./scripts/wireguard-monitor/wireguard-monitor X`, where `X` is plugin number.
* Period: `60`
