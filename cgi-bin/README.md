Based on instructions from https://serverfault.com/questions/232227/python-cgi-on-amazon-aws-ec2-micro-instance-a-how-to

1. sudo /bin/bash
2. yum install lighttpd
3. yum install lighttpd-fastcgi
4. Edit /etc/lighttpd/modules.conf, uncomment line that says include "conf.d/cgi.conf"
5. cd /var/www/lighttpd; mkdir cgi-bin; chmod 755 cgi-bin; cd cgi-bin
6. Create ydl.py, copied from this github folder
7. chmod 655 ydl.py
8. /etc/init.d/lighttpd start

For an AWS server, make it visible:
Go to your EC2 dashboard in your desktop's browser. Click on "Security Groups" in the left pane.
One or more security groups will appear in the upper right pane.
Choose the one that was assigned to your EC2 instance when you launched your instance.

A table called "Allowed Connections" will appear in the lower right pane.
A pop-up menu will let you choose "HTTP" as the connection method.

The other values in that line of the table should be: tcp, 80, 80, 0.0.0.0/0

Set environment variable on lambda instance, youtube_dl, as http://servername.com/cgi-bin/ydl.py


