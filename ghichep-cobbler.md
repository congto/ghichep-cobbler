## COBBLER NOTE

```sh
mount -o loop ubuntu-14.04.3-server-amd64.iso /mnt

cobbler import --name=ubuntu-14.04.3-server-amd64 --path=/mnt

umount /mnt

```


```sh
wget https://raw.githubusercontent.com/congto/ghichep-cobbler/master/files/sources.list \
    -O /var/www/html/trusty-sources.list

wget https://raw.githubusercontent.com/congto/ghichep-cobbler/master/files/ubuntu-server-14.04-unattended-cobbler.seed  \
    -O /var/lib/cobbler/kickstarts/ubuntu-server-14.04-unattended-cobbler.seed
```

```sh
cobbler profile add \
--name ubuntu-14.04.3-server-unattended \
--distro ubuntu-14.04.3-server-x86_64 \
--kickstart /var/lib/cobbler/kickstarts/ubuntu-server-14.04-unattended-cobbler.seed
```

```sh
service cobblerd restart
cobbler sync
```

