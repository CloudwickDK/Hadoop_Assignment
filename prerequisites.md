**Hadoop prerequisites**


#Disable ip and ipv6 tables

service iptables stop
chkconfig iptables off
service ip6tables stop
chkconfig ip6tables off


#setup ntp

yum -y install ntp
ntpdate 0.centos.pool.ntp.org
service ntpd start
chkconfig ntpd on
ntpstat

echo "ntpd is running and enabled on boot" 


# **ssh, scp and rsync **

ssh:


**scp**:
http://www.hypexr.org/linux_scp_help.php , http://www.tecmint.com/scp-commands-examples/

Copy the file "foobar.txt" from a remote host to the local host

    $ scp your_username@remotehost.edu:foobar.txt /some/local/directory 

Copy the file "foobar.txt" from the local host to a remote host

    $ scp foobar.txt your_username@remotehost.edu:/some/remote/directory 
	

**rsync**:
	http://www.tecmint.com/rsync-local-remote-file-synchronization-commands/
	
rsync -zvh local-file user@remote-host:remote-file
rsync -avzhe ssh root@192.168.0.100:/root/install.log /tmp/  (-e in order to specify the protocol:ssh)


cd OneDrive/Έγγραφα/cloudwick/hadoop/hadoop_assignment





**Configure hostname and FQDN(Fully Qualifies DOmain Name) for server**

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



5. **Understand Reverse DNS lookup’s and hosts file**


		
		
		
