# ufw-conf
UFW config files.

## Setup

```shell
cd ufw-conf
sudo rm /etc/default/ufw
sudo ln -s $PWD/etc/default/ufw /etc/default
sudo rm /etc/ufw/sysctl.conf
sudo ln -s $PWD/etc/ufw/sysctl.conf /etc/ufw
sudo rm /etc/ufw/before.rules
sudo ln -s $PWD/etc/ufw/before.rules /etc/ufw
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
