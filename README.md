# cmanage
Primitive HA Cluster management script with CGI healthcheck primary designed for use with two OpenWRT routers.
Manages sharing of  Virtual IP between master and slave: if master healthcheck fails slave will bring up Virtual IP on it while master is not healthy. Primary goal of this script is high avaliability of one of two internet links connected throught two routers

# Requirements
 - Two OpenVRT or other compatible unix-like systems
 - /bin/sh or other compatible interpretter
 - Any Webserver with CGI support
 - ifconfig

# Installation
- copy cmanagesrv to /lib/cmanage and set it executable
- copy check.sh to /lib/cmanage and set it executable
- copy cmanage to Yours cgi-bin directory and set it executable
- copy cmanage.conf to /etc

# Configuration
Modify /etc/cmanage.conf and set this values:
 - MASTER - ip of prefered master
 - SLAVE - ip of slave
 - VIP - Virtual (shared) IP
 - CHECKSCRIPT - script whitch will return 0 when node is healthy or anything elthe otherwise

# Ussage
Modify CHECKSCRIPT to node health checking according to Yours conditions. Run /lib/cmanage/cmanagesrv on both systems (or set it startup on boot). The Virtual IP sharring will start.
