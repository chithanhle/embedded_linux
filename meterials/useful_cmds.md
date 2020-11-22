## Useful commands
* **Change hostname**
```
    remote# echo new_name > /etc/hostname
    remote# vim /etc/hosts -> replace all text with old name to new name
```
* **Rename user**
```
    - Create new user, enter password & other info
        local$ ssh old_name@hostname
        remote# useradd temp_user
        remote# exit
        local$ ssh temp_user@hosname
        remote# usermod -l new_name old_name
        remote# mv /home/old_name /home/new_name
        remote# usermod -d new_home_path new_name
        remote# exit
        local$ ssh new_name@hostname
```
* **Switch user**
```
    remote# sudo -u username -s
```
* **Add user to group, sudoer ...**
```
    remote# usermod -aG groupname | sudo username
```
* **Connect to Internet via USB**
```
    local# ifconfig beagle_network_name 192.168.7.1
    local# sysctl net.ipv4.ip_forward=1
    local# iptables --table nat --append POSTROUTING --out-interface wifi_network_name -j MASQUERADE
    local# iptables --append FORWARD --in-interface beagle_network_name -j ACCEPT
    remote# route add default gw 192.168.7.1
    remote# echo "nameserver 8.8.8.8" >> /etc/resolv.conf
```