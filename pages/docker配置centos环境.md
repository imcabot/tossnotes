## 拉取镜像并运行

```Shell
 docker run -tid --name CentOS --privileged=true --restart=always -p 2222:22 centos:latest usr/sbin/init
➜  ~ 
```
## 配置centos所需的环境

以下均在该镜像的终端中运行

```Shell
## 测试网络环境
sh-4.4# ping baidu.com
PING baidu.com (39.156.66.10) 56(84) bytes of data.
64 bytes from 39.156.66.10 (39.156.66.10): icmp_seq=1 ttl=37 time=10.6 ms
64 bytes from 39.156.66.10 (39.156.66.10): icmp_seq=2 ttl=37 time=17.9 ms
64 bytes from 39.156.66.10 (39.156.66.10): icmp_seq=3 ttl=37 time=11.9 ms
64 bytes from 39.156.66.10 (39.156.66.10): icmp_seq=4 ttl=37 time=11.8 ms
64 bytes from 39.156.66.10 (39.156.66.10): icmp_seq=5 ttl=37 time=11.3 ms
64 bytes from 39.156.66.10 (39.156.66.10): icmp_seq=6 ttl=37 time=17.9 ms
^C
--- baidu.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5014ms
rtt min/avg/max/mdev = 10.593/13.556/17.884/3.088 ms
## 测试网络环境
sh-4.4# curl www.baidu.com
<!DOCTYPE html>
<!--STATUS OK--><html> <head><meta http-equiv=content-type content=text/html;charset=utf-8><meta http-equiv=X-UA-Compatible content=IE=Edge><meta content=always name=referrer><link rel=stylesheet type=text/css href=http://s1.bdstatic.com/r/www/cache/bdorz/baidu.min.css><title>百度一下，你就知道</title></head> <body link=#0000cc> <div id=wrapper> <div id=head> <div class=head_wrapper> <div class=s_form> <div class=s_form_wrapper> <div id=lg> <img hidefocus=true src=//www.baidu.com/img/bd_logo1.png width=270 height=129> </div> <form id=form name=f action=//www.baidu.com/s class=fm> <input type=hidden name=bdorz_come value=1> <input type=hidden name=ie value=utf-8> <input type=hidden name=f value=8> <input type=hidden name=rsv_bp value=1> <input type=hidden name=rsv_idx value=1> <input type=hidden name=tn value=baidu><span class="bg s_ipt_wr"><input id=kw name=wd class=s_ipt value maxlength=255 autocomplete=off autofocus></span><span class="bg s_btn_wr"><input type=submit id=su value=百度一下 class="bg s_btn"></span> </form> </div> </div> <div id=u1> <a href=http://news.baidu.com name=tj_trnews class=mnav>新闻</a> <a href=http://www.hao123.com name=tj_trhao123 class=mnav>hao123</a> <a href=http://map.baidu.com name=tj_trmap class=mnav>地图</a> <a href=http://v.baidu.com name=tj_trvideo class=mnav>视频</a> <a href=http://tieba.baidu.com name=tj_trtieba class=mnav>贴吧</a> <noscript> <a href=http://www.baidu.com/bdorz/login.gif?login&amp;tpl=mn&amp;u=http%3A%2F%2Fwww.baidu.com%2f%3fbdorz_come%3d1 name=tj_login class=lb>登录</a> </noscript> <script>document.write('<a href="http://www.baidu.com/bdorz/login.gif?login&tpl=mn&u='+ encodeURIComponent(window.location.href+ (window.location.search === "" ? "?" : "&")+ "bdorz_come=1")+ '" name="tj_login" class="lb">登录</a>');</script> <a href=//www.baidu.com/more/ name=tj_briicon class=bri style="display: block;">更多产品</a> </div> </div> </div> <div id=ftCon> <div id=ftConw> <p id=lh> <a href=http://home.baidu.com>关于百度</a> <a href=http://ir.baidu.com>About Baidu</a> </p> <p id=cp>&copy;2017&nbsp;Baidu&nbsp;<a href=http://www.baidu.com/duty/>使用百度前必读</a>&nbsp; <a href=http://jianyi.baidu.com/ class=cp-feedback>意见反馈</a>&nbsp;京ICP证030173号&nbsp; <img src=//www.baidu.com/img/gs.gif> </p> </div> </div> </div> </body> </html>
sh-4.4# 
sh-4.4# 
sh-4.4# 
sh-4.4# 
sh-4.4# 
sh-4.4# ls
bin  dev  etc  home  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
## 进入/etc/ 文件夹
sh-4.4# cd /etc/
sh-4.4# ls
BUILDTIME                csh.cshrc      group-      krb5.conf                 modules-load.d     popt.d          resolv.conf  sysctl.d
GREP_COLORS              csh.login      gshadow     krb5.conf.d               motd               printcap        rpc          system-release
NetworkManager           dbus-1         gshadow-    ld.so.cache               mtab               profile         rpm          system-release-cpe
X11                      default        gss         ld.so.conf                netconfig          profile.d       sasl2        systemd
adjtime                  depmod.d       host.conf   ld.so.conf.d              networks           protocols       security     terminfo
aliases                  dhcp           hostname    libaudit.conf             nsswitch.conf      rc.d            selinux      tmpfiles.d
alternatives             dnf            hosts       libibverbs.d              nsswitch.conf.bak  rc.local        services     udev
bash_completion.d        dracut.conf    init.d      libnl                     openldap           rc0.d           shadow       vconsole.conf
bashrc                   dracut.conf.d  inittab     libreport                 opt                rc1.d           shadow-      virc
bindresvport.blacklist   environment    inputrc     locale.conf               os-release         rc2.d           shells       xattr.conf
binfmt.d                 ethertypes     iproute2    localtime                 pam.d              rc3.d           skel         xdg
centos-release           exports        issue       login.defs                passwd             rc4.d           ssl          xinetd.d
centos-release-upstream  filesystems    issue.net   logrotate.d               passwd-            rc5.d           subgid       yum
chkconfig.d              gcrypt         kdump       machine-id                pkcs11             rc6.d           subuid       yum.conf
crypto-policies          gnupg          kdump.conf  makedumpfile.conf.sample  pki                rdma            sysconfig    yum.repos.d
crypttab                 group          kernel      modprobe.d                pm                 redhat-release  sysctl.conf
## 进入 /etc/yum.repos.d 文件夹
sh-4.4# cd yum.repos.d/
sh-4.4# ls
CentOS-Linux-AppStream.repo          CentOS-Linux-Debuginfo.repo  CentOS-Linux-FastTrack.repo         CentOS-Linux-Plus.repo
CentOS-Linux-BaseOS.repo             CentOS-Linux-Devel.repo      CentOS-Linux-HighAvailability.repo  CentOS-Linux-PowerTools.repo
CentOS-Linux-ContinuousRelease.repo  CentOS-Linux-Extras.repo     CentOS-Linux-Media.repo             CentOS-Linux-Sources.repo
## 备份原文件
sh-4.4# mv CentOS-Linux-BaseOS.repo CentOS-Linux-BaseOS.repo.backup
sh-4.4# ls
CentOS-Linux-AppStream.repo          CentOS-Linux-Debuginfo.repo  CentOS-Linux-FastTrack.repo         CentOS-Linux-Plus.repo
CentOS-Linux-BaseOS.repo.backup      CentOS-Linux-Devel.repo      CentOS-Linux-HighAvailability.repo  CentOS-Linux-PowerTools.repo
CentOS-Linux-ContinuousRelease.repo  CentOS-Linux-Extras.repo     CentOS-Linux-Media.repo             CentOS-Linux-Sources.repo
## 下载所需文件
sh-4.4# curl -O https://mirrors.aliyun.com/repo/Centos-vault-8.5.2111.repo
% Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                               Dload  Upload   Total   Spent    Left  Speed
100  2495  100  2495    0     0   5544      0 --:--:-- --:--:-- --:--:--  5556
sh-4.4# ls
CentOS-Linux-AppStream.repo          CentOS-Linux-Devel.repo             CentOS-Linux-Media.repo       Centos-vault-8.5.2111.repo
CentOS-Linux-BaseOS.repo.backup      CentOS-Linux-Extras.repo            CentOS-Linux-Plus.repo
CentOS-Linux-ContinuousRelease.repo  CentOS-Linux-FastTrack.repo         CentOS-Linux-PowerTools.repo
CentOS-Linux-Debuginfo.repo          CentOS-Linux-HighAvailability.repo  CentOS-Linux-Sources.repo

## 重命名文件
sh-4.4# rename Centos-vault-8.5.2111.repo CentOS-Linux-BaseOS.repo Centos-vault-8.5.2111.repo 
sh-4.4# ls
CentOS-Linux-AppStream.repo          CentOS-Linux-Debuginfo.repo  CentOS-Linux-HighAvailability.repo  CentOS-Linux-Sources.repo
CentOS-Linux-BaseOS.repo             CentOS-Linux-Devel.repo      CentOS-Linux-Media.repo
CentOS-Linux-BaseOS.repo.backup      CentOS-Linux-Extras.repo     CentOS-Linux-Plus.repo
CentOS-Linux-ContinuousRelease.repo  CentOS-Linux-FastTrack.repo  CentOS-Linux-PowerTools.repo
## 打开CentOS-Linux-BaseOs.repo文件，并复制[AppStream]标签下的代码
sh-4.4# vi CentOS-Linux-BaseOS.repo

## 打开CentOS-Linux-AppStream.repo文件，注释[AppStream]标签下的代码，并粘贴[AppStream]标签下的代码
sh-4.4# vi CentOS-Linux-AppStream.repo 
## 安装vim进行测试
sh-4.4# yum install vim
Repository AppStream is listed more than once in the configuration
Repository extras is listed more than once in the configuration
CentOS-8.5.2111 - AppStream - mirrors.aliyun.com                                                                   1.6 MB/s | 8.4 MB     00:05    
CentOS-8.5.2111 - Base - mirrors.aliyun.com                                                                        1.4 MB/s | 4.6 MB     00:03    
CentOS-8.5.2111 - Extras - mirrors.aliyun.com                                                                       63 kB/s |  10 kB     00:00    
Dependencies resolved.
===================================================================================================================================================
 Package                              Architecture                 Version                                   Repository                       Size
===================================================================================================================================================
Installing:
 vim-enhanced                         x86_64                       2:8.0.1763-16.el8                         AppStream                       1.4 M
Installing dependencies:
 gpm-libs                             x86_64                       1.20.7-17.el8                             AppStream                        39 k
 vim-common                           x86_64                       2:8.0.1763-16.el8                         AppStream                       6.3 M
 vim-filesystem                       noarch                       2:8.0.1763-16.el8                         AppStream                        49 k
 which                                x86_64                       2.21-16.el8                               base                             49 k

Transaction Summary
===================================================================================================================================================
Install  5 Packages

Total download size: 7.8 M
Installed size: 30 M
Is this ok [y/N]: y
Downloading Packages:
(1/5): gpm-libs-1.20.7-17.el8.x86_64.rpm                                                                           428 kB/s |  39 kB     00:00    
(2/5): vim-filesystem-8.0.1763-16.el8.noarch.rpm                                                                   750 kB/s |  49 kB     00:00    
(3/5): which-2.21-16.el8.x86_64.rpm                                                                                531 kB/s |  49 kB     00:00    
(4/5): vim-enhanced-8.0.1763-16.el8.x86_64.rpm                                                                     1.2 MB/s | 1.4 MB     00:01    
(5/5): vim-common-8.0.1763-16.el8.x86_64.rpm                                                                       1.0 MB/s | 6.3 MB     00:06    
---------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                              1.2 MB/s | 7.8 MB     00:06     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
Preparing        :                                                                                                                           1/1 
Installing       : which-2.21-16.el8.x86_64                                                                                                  1/5 
Installing       : vim-filesystem-2:8.0.1763-16.el8.noarch                                                                                   2/5 
Installing       : vim-common-2:8.0.1763-16.el8.x86_64                                                                                       3/5 
Installing       : gpm-libs-1.20.7-17.el8.x86_64                                                                                             4/5 
Running scriptlet: gpm-libs-1.20.7-17.el8.x86_64                                                                                             4/5 
Installing       : vim-enhanced-2:8.0.1763-16.el8.x86_64                                                                                     5/5 
Running scriptlet: vim-enhanced-2:8.0.1763-16.el8.x86_64                                                                                     5/5 
Running scriptlet: vim-common-2:8.0.1763-16.el8.x86_64                                                                                       5/5 
Verifying        : gpm-libs-1.20.7-17.el8.x86_64                                                                                             1/5 
Verifying        : vim-common-2:8.0.1763-16.el8.x86_64                                                                                       2/5 
Verifying        : vim-enhanced-2:8.0.1763-16.el8.x86_64                                                                                     3/5 
Verifying        : vim-filesystem-2:8.0.1763-16.el8.noarch                                                                                   4/5 
Verifying        : which-2.21-16.el8.x86_64                                                                                                  5/5 

Installed:
gpm-libs-1.20.7-17.el8.x86_64 vim-common-2:8.0.1763-16.el8.x86_64 vim-enhanced-2:8.0.1763-16.el8.x86_64 vim-filesystem-2:8.0.1763-16.el8.noarch
which-2.21-16.el8.x86_64     

Complete!
## 安装openssh-server
sh-4.4# yum install openssh-server
Repository AppStream is listed more than once in the configuration
Repository extras is listed more than once in the configuration
Last metadata expiration check: 0:00:39 ago on Thu Nov  3 10:26:10 2022.
Dependencies resolved.
===================================================================================================================================================
 Package                                 Architecture                    Version                               Repository                     Size
===================================================================================================================================================
Installing:
 openssh-server                          x86_64                          8.0p1-10.el8                          base                          485 k
Installing dependencies:
 openssh                                 x86_64                          8.0p1-10.el8                          base                          522 k

Transaction Summary
===================================================================================================================================================
Install  2 Packages

Total download size: 1.0 M
Installed size: 2.8 M
Is this ok [y/N]: y
Downloading Packages:
(1/2): openssh-8.0p1-10.el8.x86_64.rpm                                                                             658 kB/s | 522 kB     00:00    
(2/2): openssh-server-8.0p1-10.el8.x86_64.rpm                                                                      528 kB/s | 485 kB     00:00    
---------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                              1.1 MB/s | 1.0 MB     00:00     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
Preparing        :                                                                                                                           1/1 
Running scriptlet: openssh-8.0p1-10.el8.x86_64                                                                                               1/2 
Installing       : openssh-8.0p1-10.el8.x86_64                                                                                               1/2 
Running scriptlet: openssh-server-8.0p1-10.el8.x86_64                                                                                        2/2 
Installing       : openssh-server-8.0p1-10.el8.x86_64                                                                                        2/2 
Running scriptlet: openssh-server-8.0p1-10.el8.x86_64                                                                                        2/2 
Verifying        : openssh-8.0p1-10.el8.x86_64                                                                                               1/2 
Verifying        : openssh-server-8.0p1-10.el8.x86_64                                                                                        2/2 

Installed:
openssh-8.0p1-10.el8.x86_64                                          openssh-server-8.0p1-10.el8.x86_64                                         

Complete!
## 安装openssh-clients
sh-4.4# yum install openssh-clients
Repository AppStream is listed more than once in the configuration
Repository extras is listed more than once in the configuration
Last metadata expiration check: 0:00:53 ago on Thu Nov  3 10:26:10 2022.
Dependencies resolved.
===================================================================================================================================================
 Package                               Architecture                 Version                                       Repository                  Size
===================================================================================================================================================
Installing:
 openssh-clients                       x86_64                       8.0p1-10.el8                                  base                       668 k
Installing dependencies:
 libedit                               x86_64                       3.1-23.20170329cvs.el8                        base                       102 k

Transaction Summary
===================================================================================================================================================
Install  2 Packages

Total download size: 770 k
Installed size: 2.7 M
Is this ok [y/N]: y
Downloading Packages:
(1/2): libedit-3.1-23.20170329cvs.el8.x86_64.rpm                                                                   533 kB/s | 102 kB     00:00    
(2/2): openssh-clients-8.0p1-10.el8.x86_64.rpm                                                                     1.1 MB/s | 668 kB     00:00    
---------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                              1.3 MB/s | 770 kB     00:00     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
Preparing        :                                                                                                                           1/1 
Installing       : libedit-3.1-23.20170329cvs.el8.x86_64                                                                                     1/2 
Installing       : openssh-clients-8.0p1-10.el8.x86_64                                                                                       2/2 
Running scriptlet: openssh-clients-8.0p1-10.el8.x86_64                                                                                       2/2 
Verifying        : libedit-3.1-23.20170329cvs.el8.x86_64                                                                                     1/2 
Verifying        : openssh-clients-8.0p1-10.el8.x86_64                                                                                       2/2 

Installed:
libedit-3.1-23.20170329cvs.el8.x86_64                                     openssh-clients-8.0p1-10.el8.x86_64                                    

Complete!
## 启动openssh
sh-4.4# systemctl start sshd
## 查看openssh运行状况
sh-4.4# systemctl status sshd
● sshd.service - OpenSSH server daemon
 Loaded: loaded (/usr/lib/systemd/system/sshd.service; enabled; vendor preset: enabled)
 Active: active (running) since Thu 2022-11-03 10:27:25 UTC; 22s ago
   Docs: man:sshd(8)
         man:sshd_config(5)
 Main PID: 216 (sshd)
  Tasks: 1 (limit: 49562)
 Memory: 1.1M
 CGroup: /system.slice/sshd.service
         └─216 /usr/sbin/sshd -D -oCiphers=aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes256-ctr,aes256-cbc,aes128-gcm@openssh.com,aes>

Nov 03 10:27:25 e3ca6526daf9 systemd[1]: Starting OpenSSH server daemon...
Nov 03 10:27:25 e3ca6526daf9 sshd[216]: Server listening on 0.0.0.0 port 22.
Nov 03 10:27:25 e3ca6526daf9 sshd[216]: Server listening on :: port 22.
Nov 03 10:27:25 e3ca6526daf9 systemd[1]: Started OpenSSH server daemon.
## 尝试修改密码
sh-4.4# passwd
sh: passwd: command not found
## 安装用于修改密码的工具passwd
sh-4.4# yum install -y passwd
Repository AppStream is listed more than once in the configuration
Repository extras is listed more than once in the configuration
Last metadata expiration check: 0:02:17 ago on Thu Nov  3 10:26:10 2022.
Dependencies resolved.
===================================================================================================================================================
 Package                            Architecture                      Version                                Repository                       Size
===================================================================================================================================================
Installing:
 passwd                             x86_64                            0.80-3.el8                             base                            115 k
Installing dependencies:
 libuser                            x86_64                            0.62-23.el8                            base                            417 k

Transaction Summary
===================================================================================================================================================
Install  2 Packages

Total download size: 531 k
Installed size: 2.4 M
Downloading Packages:
(1/2): passwd-0.80-3.el8.x86_64.rpm                                                                                724 kB/s | 115 kB     00:00    
(2/2): libuser-0.62-23.el8.x86_64.rpm                                                                              773 kB/s | 417 kB     00:00    
---------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                              980 kB/s | 531 kB     00:00     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
Preparing        :                                                                                                                           1/1 
Installing       : libuser-0.62-23.el8.x86_64                                                                                                1/2 
Running scriptlet: libuser-0.62-23.el8.x86_64                                                                                                1/2 
Installing       : passwd-0.80-3.el8.x86_64                                                                                                  2/2 
Running scriptlet: passwd-0.80-3.el8.x86_64                                                                                                  2/2 
Verifying        : libuser-0.62-23.el8.x86_64                                                                                                1/2 
Verifying        : passwd-0.80-3.el8.x86_64                                                                                                  2/2 

Installed:
libuser-0.62-23.el8.x86_64                                                passwd-0.80-3.el8.x86_64                                               

Complete!
## 修改密码
sh-4.4# passwd
Changing password for user root.
New password: 
BAD PASSWORD: The password is shorter than 8 characters
Retype new password: 
passwd: all authentication tokens updated successfully.
sh-4.4# 
```

之后就可以使用ssh工具连接centos了
-