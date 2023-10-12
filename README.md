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

## Cautions
You shouldn't update the settings manually or comment in the file in this repository because they are overwritten by the `ufw` command.

---

If you modify the UFW configuration illegally, like the following, it's sometimes disabled (the value of "ENABLED" is turned into "no" in `etc/ufw/ufw.conf`) automatically, which causes network issues and the infinite application.

```shell
printf "*filter\nCOMMIT\n*nat\nCOMMIT\n" | sudo iptables-restore; sudo ufw reload
```
