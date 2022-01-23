#### The resolv.conf file is overwritten on each boot so we can’t edit this file directly. Instead, we edit one of the two files used to create the resolv.conf file, those being the head and base files. We’ll be editing the head file so that each boot-up, resolv.conf gets written with our custom DNS servers at the top.

#### Check to see if resolvconf is installed 
```
sudo systemctl status resolvconf.service
```

#### Install resolveconf package

```
sudo apt update
sudo apt install resolvconf
```

#### Confirm resolveconf is running

```
systemctl status resolvconf.service
```

#### If resolveconf isn't running, enable then start it

```
systemctl enable resolvconf.service
systemctl start resolvconf.service
```

#### Edit the head file

```
vi /etc/resolvconf/resolv.conf.d/head

Enter your nameservers :

nameserver 8.8.8.8
nameserver 8.8.4.4
```

#### Update resolve.conf file

```
resolvconf --enable-updates
resolvconf -u
```

#### Check to see if the entries are correctly refecled in the following file

```
 vi /etc/resolv.conf
```

#### Before changing DNS servers, you’ll need to find a third-party DNS provider, there are plenty of good (and free) services available. I recommend Google DNS which is what I use and have never had an issue. 

```
GOOGLE :

Primary IPv4: 8.8.8.8
Secondary IPv4: 8.8.4.4
```
