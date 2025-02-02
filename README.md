# NetSupport

### Background

- https://unit42.paloaltonetworks.com/cortex-xdr-detects-netsupport-manager-rat-campaign/

### Testing PCAP:

- https://app.any.run/tasks/b5d9853f-0dca-45ef-9532-83feeedcbf42

### Example:

```
$ zeek -Cr b5d9853f-0dca-45ef-9532-83feeedcbf42.pcap

$ cat notice.log

#separator \x09
#set_separator	,
#empty_field	(empty)
#unset_field	-
#path	notice
#open	2024-06-12-13-51-41
#fields	ts	uid	id.orig_h	id.orig_p	id.resp_h	id.resp_p	fuid	file_mime_type	file_desc	proto	note	msg	sub	src	dst	p	n	peer_descr	actions	email_dest	suppress_for	remote_location.country_code	remote_location.region	remote_location.city	remote_location.latitude	remote_location.longitude
#types	time	string	addr	port	addr	port	string	string	string	enum	enum	string	string	addr	addr	port	count	string	set[enum]	set[string]	interval	string	string	string	double	double
1717442617.920239	CQ7b0y4Vd4NVQ3nJRi	192.168.100.146	49741	45.134.174.143	443	-	-	-	tcp	NetSupport::C2_Traffic_Observed_HTTP_Headers	NetSupport C2 detected via HTTP headers.  NetSupport is often used in malware attacks, so be sure to check the endpoints.	-	192.168.100.146	45.134.174.143	443	-	-	Notice::ACTION_LOG	(empty)	3600.000000	-	-	-	-	-
1717442617.920239	CQ7b0y4Vd4NVQ3nJRi	192.168.100.146	49741	45.134.174.143	443	-	-	-	tcp	NetSupport::C2_Traffic_Observed_CMD_POLL	NetSupport C2 detected by CMD=POLL in connection.  NetSupport is often used in malware attacks, so be sure to check the endpoints.  Payload is in sub field.	POST http://45.134.174.143/fakeurl.htm HTTP/1.1\x0aUser-Agent: NetSupport Manager/1.3\x0aContent-Type: application/x-www-form-urlencoded\x0aContent-Length:    22\x0aHost: 45.134.174.143\x0aConnection: Keep-Alive\x0a\x0aCMD=POLL\x0aINFO=1\x0aACK=1\x0a	192.168.100.146	45.134.174.143	443	-	-	Notice::ACTION_LOG	(empty)	3600.000000	-	-	-	-	-
1717442617.955368	CQ7b0y4Vd4NVQ3nJRi	192.168.100.146	49741	45.134.174.143	443	-	-	-	tcp	NetSupport::C2_Traffic_Observed_CMD_ENCD	NetSupport C2 detected by CMD=ENCD in connection.  CMD=ENCD is often seen in malware attacks.  Be sure to check the endpoints.  Payload is in sub field.	HTTP/1.1 200 OK\x0aServer: NetSupport Gateway/1.92 (Windows NT)\x0aContent-Type: application/x-www-form-urlencoded\x0aContent-Length:    69\x0aConnection: Keep-Alive\x0a\x0aCMD=ENCD\x0aES=1\x0aDATA=\x83g+$\x81{\x14\xfe \\\x81\x05\x07\xacW\xb8\x8d[R\xb7\xf17)\x13^\\\x95\x01d8\x92=M`s\xf8\xb1\x7f\x8f\x18\x02\xac\xb3\xdfM\xdb6\xb3\xa1\x0a	192.168.100.146	45.134.174.143	443	-	-	Notice::ACTION_LOG	(empty)	3600.000000	-	-	-	-	-
#close	2024-06-12-13-51-41
```