Домашнее задание к занятию 1 «Disaster recovery и Keepalived» - `Эсадов Роман`
---
### Задание 1
`Настройки`

![HSRP](https://github.com/BeastieBoy93/sflt-homeworks/blob/main/HSRP.png)

`Ping`

![HSRP](https://github.com/BeastieBoy93/sflt-homeworks/blob/main/HSRP2.png)
`Ссылка на лабу`
[Ссылка](https://github.com/BeastieBoy93/sflt-homeworks/blob/a90fa3e74bccd8d2f2e182792903a76f2fcd0786/hsrp_advanced.pkt)
---

### Задание 2
`keepalived.conf`
```
global_defs {
    enable_script_security
}

vrrp_script nginx_check {
    script "/home/guba/web_check.sh"
    interval 3
    user guba
}

vrrp_instance web {
    state MASTER
    interface enp0s3
    virtual_router_id 5
    priority 100
    advert_int 3
    preempt_delay 10
    virtual_ipaddress {
        192.168.3.5/24
    }
    track_script {
        nginx_check
    }
}
```
`web_check.sh`
```
#!/bin/bash
curl 127.0.0.1 && test /var/www/html/index.nginx-debian.html
```
![HSRP](https://github.com/BeastieBoy93/sflt-homeworks/blob/main/keepalived.png)

---
