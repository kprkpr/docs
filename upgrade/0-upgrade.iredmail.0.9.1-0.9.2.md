# Upgrade iRedMail from 0.9.1 to 0.9.2

[TOC]


## ChangeLog

* 2015-05-16: [OPTIONAL][All backends] Update one Fail2ban filter regular expressio to help catch DoS attacks to SMTP service

## General (All backends should apply these steps)

### [OPTIONAL] Update one Fail2ban filter regular expressio to help catch DoS attacks to SMTP service

1. Open file `/etc/fail2ban/filters.d/postfix.iredmail.conf` or
`/usr/local/etc/fail2ban/filters.d/postfix.iredmail.conf` (on FreeBSD), find
below line under `[Definition]` section:

```
            lost connection after AUTH from (.*)\[<HOST>\]
```

Update above line to below one:

```
            lost connection after (AUTH|UNKNOWN|EHLO) from (.*)\[<HOST>\]
```

Restarting Fail2ban service is required.