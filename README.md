```shell
cd ufw-conf
sudo rm /etc/default/ufw
sudo ln -s $PWD/etc/default/ufw /etc/default
sudo rm /etc/ufw/sysctl.conf
sudo ln -s $PWD/etc/ufw/sysctl.conf /etc/ufw
sudo rm /etc/ufw/before.rules
sudo ln -s $PWD/etc/ufw/before.rules /etc/ufw
```
