---
layout: post
title: "Configure DNS on Ubuntu"
date: 2014-09-02 11:36
comments: true
categories: Ubuntu
---

I had network issue with my Ubuntu 12.04 machine. It was able to fetch IP from DHCP but It was incapable to connect to outside world. I pinged google.com using its IP successfully but failed using domain name. It was obvious, something is wrong with DNS!  
<!--more-->

Linux uses /etc/resolve.conf as a DNS resolver library, a plain text file with dns entries. like `` nameserver 8.8.8.8``  

Ubuntu no more use `/etc/resolve.conf` however, it needs to specify dns entry in `/etc/network/interfaces` as 
`dns-nameserver 8.8.8.8`  

and then restart network-manager.




