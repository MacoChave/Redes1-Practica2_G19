# Configuración topología 3

## Configurando PortChanels

### Switch 1

```bash
configure terminal

interface range fastEthernet 1/0 - 1
channel-group 1 mode on
exit

interface range fastEthernet 1/4 - 5
channel-group 3 mode on
exit

do wri
```

### Switch 2

```bash
configure terminal

interface range fastEthernet 1/0 - 1
channel-group 1 mode on
exit

interface range fastEthernet 1/2 - 3
channel-group 2 mode on
exit

interface range fastEthernet 1/4 - 5
channel-group 4 mode on
exit

do wri
```

### Switch 3

```bash
configure terminal

interface range fastEthernet 1/2 - 3
channel-group 2 mode on
exit

interface range fastEthernet 1/4 - 5
channel-group 3 mode on
exit

do wri
```

### Switch 4

```bash
configure terminal

interface range fastEthernet 1/4 - 5
channel-group 4 mode on
exit

do wri
```

## Configurar VTP

### Switch 1, 2, 3 y 4

```bash
configure terminal

vtp domain Grupo19
vtp password Grupo19
vtp mode client

do wri
```

## Configurar enlaces troncales

### Switch 1

```bash
configure terminal

interface port-channel 1
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,1002-1005
exit

interface port-channel 3
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,1002-1005
exit

interface fastEthernet 1/10
switchport mode trunk
switchport trunk allowed vlan 1,20,30,1002-1005
no shutdown
exit
```

### Switch 2

```bash
configure terminal

interface port-channel 1
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,1002-1005
exit

interface port-channel 2
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,1002-1005
exit

interface port-channel 4
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,1002-1005
exit

interface fastEthernet 1/10
switchport mode trunk
switchport trunk allowed vlan 1,30,1002-1005
no shutdown
exit

do wri
```

### Switch 3

```bash
configure terminal

interface port-channel 2
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,1002-1005
exit

interface port-channel 3
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,1002-1005
exit

interface fastEthernet 1/15
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,1002-1005
no shutdown
exit
```

### Switch 4

```bash
configure terminal

interface port-channel 4
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,1002-1005
exit

interface fastEthernet 1/10
switchport mode access
switchport access vlan 20
no shutdown
exit

do wri
```

```bash
show etherchannel summary
show vlan brief
show vtp status
```
