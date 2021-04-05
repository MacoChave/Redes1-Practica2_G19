# Configuración topología 1

## Configurando PortChannels

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

## configurando VTP

### Switch 1, 2 y 3

```bash
configure terminal

vtp domain Grupo19
vtp password Grupo19
vtp mode client

do wri
```

## Configurando enlaces

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
switchport mode access
switchport access vlan 10
no shutdown
exit

do wri
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

interface fastEthernet 1/15
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,1002-1005
exit

interface fastEthernet 1/10
switchport mode access
switchport access vlan 20
no shutdown
exit

interface fastEthernet 1/11
switchport mode access
switchport access vlan 30
no shutdown
exit

interface fastEthernet 1/12
switchport mode access
switchport access vlan 30
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

interface fastEthernet 1/10
switchport mode access
switchport access vlan 10
no shutdown
exit

do wri
```