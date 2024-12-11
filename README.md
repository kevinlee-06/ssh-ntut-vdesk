# ssh-ntut-vdesk

Commands to SSH into NTUT's Ubuntu VDI platform.

## First Part - Setting Up the Environment

All steps in this part should be run in the Ubuntu VDesk's terminal and with root privileges.

### Access root shell
Run the following command to get root access, you will not be asked for password.
```bash
sudo sh -c
```
Once you have root access, proceed to the next step.

### Installing ZeroTier
ZeroTier is a peer-to-peer VPN service that creates a virtual LAN, allowing you to connect directly to the VDesk using its ZeroTier IP. Execute the following command in the root shell to install ZeroTier:
```
curl -s https://install.zerotier.com | bash
```

### Joining a ZeroTier Network
1. Create an Account: First, create an account and set up a public network at [ZeroTier Central](https://my.zerotier.com/).
1. Join the Network: After creating your network, use the following command in the terminal to join it:
```
zerotier-cli join <network_id>
```
  - Make sure to run this command in the root shell.

### Obtaining Your ZeroTier IP Address
To find your ZeroTier IP address, run the following command:
```
ip a
```

Here’s an example of what the output might look like:
```python
5: ztr3e42ae2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 2800 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether aa:d6:85:6a:08:4a brd ff:ff:ff:ff:ff:ff
    inet 192.168.194.34/24 brd 192.168.194.255 scope global ztr3e42ae2
       valid_lft forever preferred_lft forever
```
In this example, `192.168.194.34` is the IP address you want to use.

### Starting the SSH Service
To start the SSH service, run the following command in the root shell:
```bash
systemctl start ssh
```

