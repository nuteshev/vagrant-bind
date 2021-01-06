# Тестирование

С машины client1:

```
[vagrant@client1 ~]$ nslookup web1.dns.lab 192.168.50.10
Server:         192.168.50.10
Address:        192.168.50.10#53

Name:   web1.dns.lab
Address: 192.168.50.15

[vagrant@client1 ~]$ nslookup web2.dns.lab 192.168.50.10
Server:         192.168.50.10
Address:        192.168.50.10#53

** server can't find web2.dns.lab: NXDOMAIN

[vagrant@client1 ~]$ nslookup www.newdns.lab 192.168.50.10
Server:         192.168.50.10
Address:        192.168.50.10#53

Name:   www.newdns.lab
Address: 192.168.50.14
Name:   www.newdns.lab
Address: 192.168.50.15

[vagrant@client1 ~]$ nslookup www.newdns.lab 192.168.50.11
Server:         192.168.50.11
Address:        192.168.50.11#53

Name:   www.newdns.lab
Address: 192.168.50.14
Name:   www.newdns.lab
Address: 192.168.50.15

[vagrant@client1 ~]$ nslookup web1.dns.lab 192.168.50.11
Server:         192.168.50.11
Address:        192.168.50.11#53

Name:   web1.dns.lab
Address: 192.168.50.15

[vagrant@client1 ~]$ nslookup web2.dns.lab 192.168.50.11
Server:         192.168.50.11
Address:        192.168.50.11#53

** server can't find web2.dns.lab: NXDOMAIN
```

С машины client2:

```
[vagrant@client2 ~]$ nslookup web1.dns.lab 192.168.50.10
Server:         192.168.50.10
Address:        192.168.50.10#53

Name:   web1.dns.lab
Address: 192.168.50.15

[vagrant@client2 ~]$ nslookup web2.dns.lab 192.168.50.10
Server:         192.168.50.10
Address:        192.168.50.10#53

Name:   web2.dns.lab
Address: 192.168.50.14

[vagrant@client2 ~]$ nslookup www.newdns.lab 192.168.50.10
Server:         192.168.50.10
Address:        192.168.50.10#53

** server can't find www.newdns.lab: NXDOMAIN

[vagrant@client2 ~]$ nslookup www.newdns.lab 192.168.50.11
Server:         192.168.50.11
Address:        192.168.50.11#53

** server can't find www.newdns.lab: NXDOMAIN

[vagrant@client2 ~]$ nslookup web1.dns.lab 192.168.50.11
Server:         192.168.50.11
Address:        192.168.50.11#53

Name:   web1.dns.lab
Address: 192.168.50.15

[vagrant@client2 ~]$ nslookup web2.dns.lab 192.168.50.11
Server:         192.168.50.11
Address:        192.168.50.11#53

Name:   web2.dns.lab
Address: 192.168.50.14
```