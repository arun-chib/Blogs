# Assiging Static IP to RHEL9 VM

My Setup:

*   RHEL 9 spinning on Vbox with a wireless home router
    

# Steps to Assign Static IP:

1.  Note the IP address that your home router has provided using this command: `nmcli` or `ip a`.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671093283430/25fgT30dq.jpg align="center")
    
2.  You can view more information from the output of the command below: `nmcli connection show enp0s8`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671097515640/os525y72s.jpg align="center")
    
    Note <mark>IP4.ADDRESS </mark> and <mark>IP4.GATEWAY</mark> assigned.
    
3.  Update static IP *\[IP4.ADDRESS noted in step 2\]* using the command below:
    
    `nmcli con mod enp0s8 ipv4.method manual ipv4.addr "192.168.0.108/24"`
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671097892486/YTcnB5odl.jpg align="center")

4.  Check updated setting in below file under ipv4 section:
    
    `/etc/NetworkManager/system-connections/enp0s8.nmconnection`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671098375767/IDSGsnCc0.jpg align="center")
    
5.  Restart network services:
    
    `nmcli con down enp0s8`
    
    `nmcli con up enp0s8`
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671098656487/V0WNlJbUn.png align="center")

6.  Now check status with command `nmcli:`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671098803530/kdTSyBMnb.png align="center")
    
7.  Try to ssh from mobaxterm or putty:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671098940761/Mjmvki1aC.png align="center")
    
    Voilà!
    

# Revert to Dynamic ip configuration:

Run the following commands:

`nmcli con mod enp0s8 ipv4.method auto`

`nmcli con mod enp0s8 ipv4.address ""`

Restart Network Services:

`nmcli con down enp0s8`

`nmcli con up enp0s8`

Done!

Examine the ipv4 section of the config file now.

`/etc/NetworkManager/system-connections/enp0s8.nmconnection`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671099371825/c8R2aksCM.png align="center")

I hope you found this useful!