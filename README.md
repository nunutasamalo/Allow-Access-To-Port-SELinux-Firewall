Allow-Access-To-Port-SELinux-Firewall
To allow access to port 9443
--------------------------------------
Start with checking the port allocation and confirming the port you want to allow access to isn't already being used

#sudo semanage port -l | grep http_port_t
Allow access to port
#sudo semanage port -a -t http_port_t -p tcp 9443
Check firewall ports passthrough
#sudo firewall-cmd --list-all
Add port (and make it permanent)
#sudo firewall-cmd --zone=public --add-port=9443/tcp --permanent
Reload firewall for the changes to take effect
#sudo firewall-cmd --reload
