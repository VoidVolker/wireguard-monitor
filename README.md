# wireguard-monitor

[![Join the chat at https://gitter.im/VoidVolker/wireguard-monitor](https://badges.gitter.im/VoidVolker/wireguard-monitor.svg)](https://gitter.im/VoidVolker/wireguard-monitor?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

Simple bash script for monitoring current IP and WireGuard status in Xfce tray.

# Requirements

* Xfce desktop
* Installed genmon-plugin: https://docs.xfce.org/panel-plugins/xfce4-genmon-plugin
```bash
sudo apt install xfce4-genmon-plugin
```
* wget
```bash
sudo apt install wget
```

# Features

* Colored tray icon:
green - all ok
red - wireguard is not working
gray - offline or network error
* WireGuard status parsing
* Real IP check and WireGuard endpoind compare
* Periodical run
* Immediatly run by icon click

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

Allow `wg show` command to run without password:
```bash
sudo visudo
```

Add next line to sudoers file:
```
username ALL = NOPASSWD: /usr/bin/wg show
```
Where `username` is your username. This command is used for collecting wireguard status.

Add genmon widget
```bash
xfce4-panel --add genmon
```

Now you need to get widget name. To get this name, go to the panel properties screen and on the Items tab, hover your mouse over the genmon plugin to get it's internal name.

You will get: ```genmon-X```. Where `X` is plugin number. Example: `genmon-10`. Use this number as first argument for script. Plugin name is used for plugin refresh via icon click.

Go to genmon plugin properties and add next settings:

* Command: `./scripts/wireguard-monitor/wireguard-monitor -n X`, where `X` is plugin number.
* Period: `60`

# Command line arguments

| Short name | Long name | Default value | Description |
| --- | --- | --- | --- |
| -n | --name       | -                 | Widget/plugin name |
| -i | --icon       | 32                | Icon size. Founded sizes: 24 32 48 64 |
| -f | --face       | 'JetBrains Mono'  | Font family |
| -e | --error      | ff4400            | Error color |
| -p | --ip         | 9dffa8            | Ip color |
| -n | --endpoint   | 707eff            | Endpoint color |
| -h | --handshake  | a164e0            | Handshake color |
| -t | --transfer   | f1e552            | Transfer color |
| -c | --command    | poll vpn status   | Custom command to run on click |
