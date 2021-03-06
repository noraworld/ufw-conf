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

I haven’t tested the following commands because they have already been configured. And I’m not sure it is appropriate.

```shell
sudo ufw deny 22/tcp
sudo ufw allow $(cat /etc/ssh/sshd_config.d/port.conf | grep -E "^Port [0-9]{4,5}" | awk '{ print $2 }')
sudo ufw allow $(cat /etc/ssh/sshd_config.d/port.conf | grep -E "^Port [0-9]{4,5}" | awk '{ print $2 }')/tcp
sudo ufw allow 53
sudo ufw allow out to any port 53
sudo ufw allow 67/udp
sudo ufw allow 68/udp
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
