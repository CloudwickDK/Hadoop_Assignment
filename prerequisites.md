**Hadoop prerequisites**


## 1. Disable ip and ipv6 tables

service iptables stop
chkconfig iptables off
service ip6tables stop
chkconfig ip6tables off


## 2. setup ntp

yum -y install ntp
ntpdate 0.centos.pool.ntp.org
service ntpd start
chkconfig ntpd on
ntpstat

echo "ntpd is running and enabled on boot" 


## 3. ssh, scp and rsync 

ssh:


* **scp**:
http://www.hypexr.org/linux_scp_help.php , http://www.tecmint.com/scp-commands-examples/

*Copy the file "foobar.txt" from a remote host to the local host

    $ scp your_username@remotehost.edu:foobar.txt /some/local/directory 

*Copy the file "foobar.txt" from the local host to a remote host

    $ scp foobar.txt your_username@remotehost.edu:/some/remote/directory 
	

* **rsync**:
	http://www.tecmint.com/rsync-local-remote-file-synchronization-commands/
	
rsync -zvh local-file user@remote-host:remote-file
rsync -avzhe ssh root@192.168.0.100:/root/install.log /tmp/  (-e in order to specify the protocol:ssh)




##  4. Configure hostname and FQDN(Fully Qualifies DOmain Name) for server

Edit file /etc/sysconfig/network:

sudo vim /etc/sysconfig/network

Add an entry of your desired hostname by replacing boson.dev.local boson where boson.dev.local is the fully qualified hostname and boson is hostname.

127.0.1.1       boson.dev.local boson

Restart the hostname service:

sudo service hostname restart

Test your configuration by opening a terminal and enter the below commands:

    hostname
        This should output boson
    hostname -f
        This should output boson.dev.local
	
	
	
In order to change FQDN:
	
sudo vim /etc/hosts

127.0.0.1   localhost.localdomain   localhost
127.0.1.1   hostname.yourdomain.tld hostname
YourIP      hostname.yourdomain.tld hostname



## 5. Understand Reverse DNS lookup’s and hosts file

Standard DNS: www.itworld.com -> 23.23.212.126 Reverse DNS: 23.23.212.126 -> ec2-23-23-212-126.compute-1.amazonaws.com. 

http://www.itworld.com/article/2833006/networking/how-to-setup-reverse-dns-and-ptr-records.html
https://forum.ivorde.com/unix-reverse-dns-lookup-using-dig-command-ptr-dns-record-type-t19521.html
http://www.thegeekstuff.com/2012/02/dig-command-examples/

$ dig -x 75.126.153.206

You can only display the answer section of a reply with +answer option and clear all other display info with +noall option as follow:
 $ dig +noall +answer -x 199.232.41.10
 
10.41.232.199.in-addr.arpa. 36000 IN    CNAME   rev-c41-10.gnu.org.
rev-c41-10.gnu.org.       300     IN      PTR     www.gnu.org.

The PTR record is the one that contains the domain host name. The domain name is, as you expect, www.gnu.org.
Note that PTR records are not required for IP addresses. If a PTR record is not defined for an IP address, you cannot do a remote DNS lookup. 

Whereas a DNS lookup is:

 $ dig +noall +answer www.gnu.org
www.gnu.org.            67      IN      CNAME   gnu.org.
gnu.org.                67      IN      A       199.232.41.10

The IP address is displayed in the A record, and is 199.232.41.10.


## 6. IPTables

https://wiki.centos.org/HowTos/Network/IPTables

The /etc/sysconfig/iptables-config file stores information used by the kernel to set up packet filtering services at boot time or whenever the service is started. 

commands:
$ rpm -q iptables
$ lsmod | grep ip_tables
$iptables -L

If iptables is not running, you can enable it by running:
# system-config-securitylevel


## 7. Enable services at specified run time levels

https://www.digitalocean.com/community/tutorials/how-to-configure-a-linux-service-to-start-automatically-after-a-crash-or-reboot-part-2-reference
https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Deployment_Guide/s2-services-chkconfig.html

    Runlevel 0: System shutdown
    Runlevel 1: Single-user, rescue mode
    Runlevels 2, 3, 4: Multi-user, text mode with networking enabled
    Runlevel 5: Multi-user, network enabled, graphical mode
    Runlevel 6: System reboot
	
basic commands:
chkconfig --list service_name
chkconfig service_name on
chkconfig service_name on --level runlevels
chkconfig service_name off 
chkconfig service_name off --level runlevels
	

## 8. 

		
cd OneDrive/Έγγραφα/cloudwick/hadoop/hadoop_assignment	
