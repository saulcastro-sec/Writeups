
---
- Tags: #dockerlabs #metasploit #linux 
---

![[Pasted image 20250227173553.png]]

# Reconocimiento inicial

El host está activo, por el TTL es linux

![[Pasted image 20250227175337.png]]

## nmap

### Puertos abiertos

![[Pasted image 20250227174007.png]]

### Servicios corriendo en puertos

```bash
PORT     STATE SERVICE            VERSION
22/tcp   open  ssh                OpenSSH 8.4p1 Debian 5+deb11u3 (protocol 2.0)
| ssh-hostkey: 
|   3072 9c:7c:e5:ea:fe:ac:f5:bc:21:54:87:66:70:ed:df:75 (RSA)
|   256 b2:1a:b1:05:0e:7e:94:18:98:19:8f:60:d7:04:7a:1c (ECDSA)
|_  256 c1:81:ba:4f:1a:99:9f:32:10:4a:6a:d9:f4:aa:40:de (ED25519)
5222/tcp open  jabber
|_ssl-cert: ERROR: Script execution failed (use -d to debug)
| fingerprint-strings: 
|   RPCCheck: 
|_    <stream:error xmlns:stream="http://etherx.jabber.org/streams"><not-well-formed xmlns="urn:ietf:params:xml:ns:xmpp-streams"/></stream:error></stream:stream>
| xmpp-info: 
|   STARTTLS Failed
|   info: 
|     xmpp: 
|       version: 1.0
|     stream_id: 3ircjpuim0
|     unknown: 
|     errors: 
|       invalid-namespace
|       (timeout)
|     features: 
|     auth_mechanisms: 
|     capabilities: 
|_    compression_methods: 
5223/tcp open  ssl/hpvirtgrp?
|_ssl-date: TLS randomness does not represent time
5262/tcp open  jabber             Ignite Realtime Openfire Jabber server 3.10.0 or later
| xmpp-info: 
|   STARTTLS Failed
|   info: 
|     xmpp: 
|       version: 1.0
|     stream_id: 3w5qrkf4le
|     unknown: 
|     errors: 
|       invalid-namespace
|       (timeout)
|     features: 
|     auth_mechanisms: 
|     capabilities: 
|_    compression_methods: 
5263/tcp open  ssl/unknown
|_ssl-date: TLS randomness does not represent time
5269/tcp open  xmpp               Wildfire XMPP Client
| xmpp-info: 
|   Respects server name
|   STARTTLS Failed
|   info: 
|     xmpp: 
|       version: 1.0
|     stream_id: a13ekx4z8g
|     unknown: 
|     errors: 
|       host-unknown
|       (timeout)
|     features: 
|     auth_mechanisms: 
|     capabilities: 
|_    compression_methods: 
5270/tcp open  xmp?
5275/tcp open  jabber             Ignite Realtime Openfire Jabber server 3.10.0 or later
| xmpp-info: 
|   STARTTLS Failed
|   info: 
|     xmpp: 
|       version: 1.0
|     stream_id: 9yv8lc5y12
|     unknown: 
|     errors: 
|       invalid-namespace
|       (timeout)
|     features: 
|     auth_mechanisms: 
|     capabilities: 
|_    compression_methods: 
5276/tcp open  ssl/unknown
|_ssl-date: TLS randomness does not represent time
7070/tcp open  http               Jetty
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-title: Openfire HTTP Binding Service
7777/tcp open  socks5             (No authentication; connection not allowed by ruleset)
| socks-auth-info: 
|_  No authentication
9090/tcp open  hadoop-tasktracker Apache Hadoop
| hadoop-tasktracker-info: 
|_  Logs: jive-ibtn jive-btn-gradient
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-favicon: Unknown favicon MD5: E4888EE8491B4EB75501996E41AF6460
|_http-title: Site doesnt have a title (text/html).
| hadoop-datanode-info: 
|_  Logs: jive-ibtn jive-btn-gradient
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port5222-TCP:V=7.95%I=7%D=2/27%Time=67C0980C%P=x86_64-pc-linux-gnu%r(RP
SF:CCheck,9B,"<stream:error\x20xmlns:stream=\"http://etherx\.jabber\.org/s
SF:treams\"><not-well-formed\x20xmlns=\"urn:ietf:params:xml:ns:xmpp-stream
SF:s\"/></stream:error></stream:stream>");
MAC Address: 02:42:AC:11:00:02 (Unknown)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

```


En el puerto 9090 está corriendo el servicio Openfire, si entramos en la página http://172.17.0.2:9090 vemos un login

![[Pasted image 20250227180034.png]]


## Metasploit

## Buscamos vulnerabilidades 

![[Pasted image 20250227181035.png]]

![[Pasted image 20250227181049.png]]

![[Pasted image 20250227181234.png]]

