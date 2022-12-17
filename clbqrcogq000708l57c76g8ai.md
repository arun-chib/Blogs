# Installing KVM/qmeu on RHEL 9.

KVM: Kernel-based Virtual Machine.

My Setup:

*   RHEL9 Machine spinning on vbox.
    
*   Preq: RHEL or any OS iso for server installation.
    

# Steps to install KVM on RHEL:

1.  Run below command to check if virtualization is enabled on your system:  
    `egrep -c '(vmx|svm)' /proc/cpuinfo`
    

The output should be a number greater than 0. If not, enable virtualization in the BIOS settings of your system.

If you are using VBox, then check this box:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671186778601/nY4SFHNpG.png align="center")

2.  Install below packges from yum/dnf repo.
    
    `sudo yum install virt-install virt-viewer libvirt virt-top libguestfs-tools xorg* -y`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671204397780/4cQ5c1Yhr.png align="center")
    
    After successful installation run following command: `virt-manager` to launch GUI.
    
    Note: Try opening the server in a new terminal if you are receiving the error below:
    
    <mark>(virt-manager:5994): Gtk-WARNING **: cannot open display:</mark>
    
3.  **Create VM using virt-manager GUI:**
    
    *   open `virt-manager`
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671210226434/Kg9bRieqS.png align="center")
        

*   click on *File &gt; New Virtual Machine*
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671207652047/ji3oZp8Z3.png align="center")

*   This will launch a fresh VM creation wizard. Since we had downloaded RHEL 9.0 from this [page](https://developers.redhat.com/products/rhel/download), we'll go with option 1.
    
    Select *Local installation media &gt; click Forward button*.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671207908618/t3veJw8DJ.png align="center")
    
    *   Browse the download directory.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671210396796/N8r_jEy3L.png align="center")
        
    *   after that click *Browse Local* to find the ISO on the local path.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671210448538/cNSAaHbMz.png align="center")
        
    *   Select the iso & click open.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671211164778/d_6M4R16x.png align="center")
        
    *   After choosing ISO, press Forward to go to the following stage.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671210693161/KtKB6j3so.png align="center")
        
    *   Set Desired RAM and vCPUS for your Machine.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671210823681/6bwCTlYME.png align="center")
        
    *   Set Desired Disk Size.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671210839940/jY-aC5wrm.png align="center")
        
    *   Select default Network in our Case.  
        Note : We can create a bridge network too and select it at this point.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671210877435/CrXy3CCVV.png align="center")
        
    *   If all goes well you will have GRUB screen in front of you and you can proceed with linux installation.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671210910645/Z1y0_U_az.png align="center")
        
        *   Voilà!
            
            Please give this post a thumbs up if you found it helpful and have fun learning. :)