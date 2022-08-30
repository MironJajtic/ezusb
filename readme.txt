In case installed ezusb.bundle driver doesn't work, try with this one.

EZ100PU Linux 32/64bit driver installation script:
https://www.castlestech.com/wp-content/uploads/2016/08/201511920271676073.zip

Install: apt-get install opensc pcscd pcsc-tools libusb-dev libusb-0.1-4

File location: /usr/lib/pcsc/drivers/ezusb.bundle/Contents/Linux/ezusb.so

Loaded with: systemctl enablestart pcscd.service

/etc/os-release
================
PRETTY_NAME="Ubuntu 22.04.1 LTS"
  NAME="Ubuntu"
  VERSION_ID="22.04"
  VERSION="22.04.1 LTS (Jammy Jellyfish)"
  VERSION_CODENAME=jammy
  ID=ubuntu
  ID_LIKE=debian
  HOME_URL="https://www.ubuntu.com/"
  SUPPORT_URL="https://help.ubuntu.com/"
  BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
  PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
  UBUNTU_CODENAME=jammy
================

uname -r
================
  5.15.0-46-generic
================

usb-devices
================
T:  Bus=03 Lev=01 Prnt=01 Port=13 Cnt=01 Dev#= 15 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0ca6 ProdID=0010 Rev=00.05
S:  Manufacturer=CASTLES
S:  Product=EZ100PU Smart Card Reader
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=00(>ifc ) Sub=00 Prot=00 Driver=usbfs
E:  Ad=01(O) Atr=02(Bulk) MxPS=  16 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  16 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   8 Ivl=1ms
================

lsusb
================
Bus 003 Device 015: ID 0ca6:0010 Castles Technology Co., Ltd EZUSB PC/SC Smart Card Reader

|__ Port 14: Dev 15, If 0, Class=, Driver=usbfs, 12M
================
