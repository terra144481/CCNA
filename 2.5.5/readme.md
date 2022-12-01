1. Rename switch to name = S2  
```
Switch>enable  
Switch#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#hostname S2
```
2. Create password from console (enable user EXEC access)
```
S2(config)#line consol 0
S2(config-line)#password letmein
S2(config-line)#login
S2(config-line)#exit
```
3. Create password from privileged EXEC access
```
S2(config)#enable password c1$c0

S2(config)#enable secret itsasecret
```
4. Create password from VTY.
```
S2(config)#line vty 0 15
S2(config-line)#password cisco
S2(config-line)#login
S2(config-line)#exit
```
6. Create banner.
```
2#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
S2(config)#banner motd #Warning! Authorized access only!#
```
7. Encrypt passwords.
```
S2(config)#service password-encryption
```
8. Copy config to NVRAM
```
S2#copy Running-config startup-config 
Destination filename [startup-config]? 
Building configuration...
[OK]
```

```
S2#show running-config 
Building configuration...

Current configuration : 1310 bytes
!
version 15.0
no service timestamps log datetime msec
no service timestamps debug datetime msec
service password-encryption
!
hostname S2
!
!
enable secret 5 $1$mERr$ILwq/b7kc.7X/ejA4Aosn0
enable password 7 08221D0A0A49
!
!
!
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
interface FastEthernet0/1
!
interface FastEthernet0/2
!
interface FastEthernet0/3
!
interface FastEthernet0/4
!
interface FastEthernet0/5
!
interface FastEthernet0/6
!
interface FastEthernet0/7
!
interface FastEthernet0/8
!
interface FastEthernet0/9
!
interface FastEthernet0/10
!
interface FastEthernet0/11
!
interface FastEthernet0/12
!
interface FastEthernet0/13
!
interface FastEthernet0/14
!
interface FastEthernet0/15
!
interface FastEthernet0/16
!
interface FastEthernet0/17
!
interface FastEthernet0/18
!
interface FastEthernet0/19
!
interface FastEthernet0/20
!
interface FastEthernet0/21
!
interface FastEthernet0/22
!
interface FastEthernet0/23
!
interface FastEthernet0/24
!
interface GigabitEthernet0/1
!
interface GigabitEthernet0/2
!
interface Vlan1
 no ip address
 shutdown
!
banner motd ^CWarning! Authorized access only!^C
!
!
!
!
!
line con 0
 password 7 082D495A041C0C19
 login
 history size 100
!
line vty 0 4
 password 7 0822455D0A16
 login
line vty 5 15
 password 7 0822455D0A16
 login
!
!
!
!
end
```

Some command from configure:
```
show startup-config

copy running-config startup-config

show running-config

erase startup-config

reload  

