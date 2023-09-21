## 说明

**本openwrt仅适用于x86_64的CPU.**

  |名称 |说明 |
  |:----|:----|
  |IP| 10.5.2.1|
  |用户| root|
  |密码||

> **说明**:构建本openwrt目的是自己使用比较清爽,没有太多功能,仅仅适用我个人使用.

### 网络配置
接口-> lan-> IPV6设置-> 本地IPV6-> **DNS服务器取消勾选**

#### AdgHome DNS 配置
```
127.0.0.1:7874
# 防污染解析、
tls://dns.pub
https://dns.pub/dns-query
tls://dns.alidns.com
https://dns.alidns.com/dns-query
tls://dns.google.com
https://dns.google/dns-query
——————————————————
Bootstrap DNS
——————————————————
119.29.29.29
202.96.134.133
2402:4e00::
2400:3200::1
```

#### pve8.0 lxc配置
```
onboot: 0
features: nesting=1
lxc.cgroup2.devices.allow: c 108:0 rwm
lxc.mount.auto: proc:mixed sys:ro cgroup:mixed
lxc.mount.entry: /dev/net/tun dev/net/tun none rw,bind,create=file 0 0
lxc.mount.entry: /dev/ppp dev/ppp none rw,bind,optional,create=file 0 0
lxc.net.0.flags: up
lxc.net.0.type: veth
lxc.net.0.link: vmbr0
lxc.net.0.name: eth0
lxc.net.1.flags: up
lxc.net.1.type: phys
lxc.net.1.link: enp1s0
lxc.net.1.name: eth1
```

#### 服务
  1. OpenClash
  2. AdguardHome
  3. DDNS
  4. ~~SmartDns~~

## 鸣谢

- 感谢[openwrt源码](https://github.com/openwrt/openwrt)
- 感谢[@P3TERX](https://github.com/P3TERX)

> 使用了
>   1. [P3TERX大佬的云编译](https://github.com/P3TERX/Actions-OpenWrt)
>   2. 最后感谢上面使用了但未提及的大佬们

