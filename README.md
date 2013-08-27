forever-init-script
===================

init.d script to daemonize node applications using "forever"


Installation
============
1. Install forever:

		$ npm install forever -g
2. Create a regular user for running node processes:

		$ useradd -m -d /home/node -s /usr/sbin/nologin node
3. Because node will run under regular user which don't have write rights to /var/run it is necessary to create a directory for storing pidfiles:

		$ mkdir /var/run/forever
		$ chown node:node /var/run/forever
4. Copy script to /etc/init.d and enable its autostart:

		$ cp forever /etc/init.d
		$ chmod +x /etc/init.d/forever
		$ chkconfig forever on
5. Configure script variables `NAME`, `NODE_USER`, `APPLICATION_DIRECTORY` etc. Default values are provided.
6. Enable appropriate location of init functions library. It is already enabled for CentOS: `. /lib/lsb/init-functions`.


Usage
=====
### Start script
	$ service forever start
### Get status
	$ service forever status
### Restart script
	$ service forever restart
### Stop script
	$ service forever stop
	
Licensing
=========

© 2013 <a href="https://www.exratione.com" target="_blank">Reason</a> and <a href="http://soaw.com" target="_blank">SOAW</a>. Source code is distributed under CDDL 1.0 open source license.