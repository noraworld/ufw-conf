# ufw-conf
UFW config files.

## Setup

```shell
cd ufw-conf

sudo rm /etc/default/ufw
sudo ln -s $PWD/etc/default/ufw /etc/default

sudo rm -r /etc/ufw
sudo ln -s $PWD/etc/ufw /etc
```

## Start daemon

```shell
sudo ufw enable
sudo systemctl start ufw
sudo systemctl enable ufw
```

## Restart daemon

```shell
sudo ufw reload
sudo systemctl restart ufw
```

## Check daemon status

```shell
sudo ufw status
sudo systemctl status ufw
```

## Blocked forwarding ports
The forwarding ports except for well-known ones are blocked by default, but these ones are accepted exceptionally.

| Port          | Proto     | Purpose              |
| :-----------: | :-------: | -------------------- |
| 60313         | TCP / UDP | SSH                  |
| 50000 - 51819 | UDP       | Discord (voice chat) |
| 51821 - 65535 | UDP       | Discord (voice chat) |

The port `51820` is used for [NordVPN WireGuard](https://chatgpt.com/share/6734528b-0d14-8004-9253-770de34c4db2).

## Cautions
You shouldn't update the settings manually or comment in the file in this repository because they are overwritten by the `ufw` command.

---

If you modify the UFW configuration illegally, like the following, it's sometimes disabled (the value of "ENABLED" is turned into "no" in `etc/ufw/ufw.conf`) automatically, which causes network issues and the infinite application.

```shell
printf "*filter\nCOMMIT\n*nat\nCOMMIT\n" | sudo iptables-restore; sudo ufw reload
```

## Troubleshootings
If you suspect the UFW rules are reloaded repeatedly and it causes the network issue, you can check the following command to detect the repeated reloading.

```shell
watch -t -n 0.5 git diff
```
