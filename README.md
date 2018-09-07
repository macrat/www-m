www-m
=====

Google said `example.com` and `www.example.com` are same.
Ok, make DNS as same too.

# Start server
## use CoreDNS directly
``` shell
# coredns -conf ./Corefile
```

## with Docker
``` shell
$ docker run -d -v `pwd`/Corefile:/Corefile -p 53:53/udp coredns/coredns -conf /Corefile
```

## with Docker Compose
``` shell
$ docker-compose up -d
```

# Use
``` shell
$ dig @localhost +noall +answer example.com
example.com.		10479	IN	A	93.184.216.34

$ dig @localhost +noall +answer www.example.com
www.example.com.	60	IN	CNAME	example.com.

$ dig @localhost +noall +answer www.m.www.m.www.www.example.com
www.m.www.m.www.www.example.com.	60	IN	CNAME	example.com.
```
