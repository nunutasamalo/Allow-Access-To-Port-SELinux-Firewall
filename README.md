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




==================================================================
Listing Ports with Semanage

To list port numbers of a specific port like http, use this command:
# semanage port -l | grep -w http_port_t
# semanage port -l | grep -w mysqld_port_t

Creating or Adding Ports with Semanage
semanage port -a -t http_port_t -p tcp 2222

to view the newly created port, we use the command list command with the -C option to show only customizations.

# semanage port -lC


To assign a range of ports numbers to a specific port, use the command:

# semanage port -a -t http_port_t -p tcp 2223-2225

Delete:
# semanage port -d -t unreserved_port_t -p tcp 2222
To delete a range of ports, use the command:

# semanage port -d -t http_port_t -p tcp 2223-2225

