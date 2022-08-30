In case installed ezusb.bundle driver doesn't work, try with this one.

EZ100PU Linux 32/64bit driver installation script:
https://www.castlestech.com/wp-content/uploads/2016/08/201511920271676073.zip

Install: apt-get install opensc pcscd pcsc-tools libusb-dev libusb-0.1-4

File location: /usr/lib/pcsc/drivers/ezusb.bundle/Contents/Linux/ezusb.so

Loaded with: systemctl enable --now pcscd.service

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

pcsc_scan
================
Using reader plug'n play mechanism
Scanning present readers...
0: CASTLES EZ100PU 00 00
 
Tue Aug 30 15:43:43 2022
 Reader 0: CASTLES EZ100PU 00 00
  Event number: 5
  Card state: Card inserted, Shared Mode, 
  ATR: 3B FF 13 00 00 81 31 FE 45 00 31 B9 64 04 44 EC C1 73 94 01 80 82 90 00 12

ATR: 3B FF 13 00 00 81 31 FE 45 00 31 B9 64 04 44 EC C1 73 94 01 80 82 90 00 12
+ TS = 3B --> Direct Convention
+ T0 = FF, Y(1): 1111, K: 15 (historical bytes)
  TA(1) = 13 --> Fi=372, Di=4, 93 cycles/ETU
    43010 bits/s at 4 MHz, fMax for Fi = 5 MHz => 53763 bits/s
  TB(1) = 00 --> VPP is not electrically connected
  TC(1) = 00 --> Extra guard time: 0
  TD(1) = 81 --> Y(i+1) = 1000, Protocol T = 1 
-----
  TD(2) = 31 --> Y(i+1) = 0011, Protocol T = 1 
-----
  TA(3) = FE --> IFSC: 254
  TB(3) = 45 --> Block Waiting Integer: 4 - Character Waiting Integer: 5
+ Historical bytes: 00 31 B9 64 04 44 EC C1 73 94 01 80 82 90 00
  Category indicator byte: 00 (compact TLV data object)
    Tag: 3, len: 1 (card service data byte)
      Card service data byte: B9
        - Application selection: by full DF name
        - BER-TLV data objects available in EF.DIR
        - BER-TLV data objects available in EF.ATR
        - EF.DIR and EF.ATR access services: by READ BINARY command
        - Card without MF
    Tag: 6, len: 4 (pre-issuing data)
      Data: 04 44 EC C1
    Tag: 7, len: 3 (card capabilities)
      Selection methods: 94
        - DF selection by full DF name
        - DF selection by file identifier
        - Short EF identifier supported
      Data coding byte: 01
        - Behaviour of write functions: one-time write
        - Value 'FF' for the first byte of BER-TLV tag fields: invalid
        - Data unit in quartets: 2
      Command chaining, length fields and logical channels: 80
        - Command chaining
        - Logical channel number assignment: No logical channel
        - Maximum number of logical channels: 1
    Mandatory status indicator (3 last bytes)
      LCS (life card cycle): 82 (Proprietary)
      SW: 9000 (Normal processing.)
+ TCK = 12 (correct checksum)

Possibly identified card (using /usr/share/pcsc/smartcard_list.txt):
3B FF 13 00 00 81 31 FE 45 00 31 B9 64 04 44 EC C1 73 94 01 80 82 90 00 12
	Croation personal ID card (eID)
	http://eid.hr/
================
