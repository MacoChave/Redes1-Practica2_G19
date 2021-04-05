# Configuración topología 2

## Configurando PortChanels

### Switch 1

```bash
configure terminal

interface range fastEthernet 1/0 - 1
channel-group 1 mode on
exit

interface range fastEthernet 1/2 - 4
channel-group 2 mode on
exit

interface range fastEthernet 1/5 - 7
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

interface range fastEthernet 1/11 - 13
channel-group 4 mode on
exit

interface range fastEthernet 1/8 - 10
channel-group 5 mode on
exit

do wri
```

### Switch 3

```bash
configure terminal
interface range fastEthernet 1/2 - 4
channel-group 2 mode on
exit

interface range fastEthernet 1/11 - 13
channel-group 4 mode on
exit

do wri
```

### Switch 4

```bash
configure terminal

interface range fastEthernet 1/5 - 7
channel-group 3 mode on
exit

interface range fastEthernet 1/8 - 10
channel-group 5 mode on
exit

do wri
```

## Configurando VTP

### Switch 1

```bash
configure terminal

vtp domain Grupo19
vtp password Grupo19
vtp mode server

do wri
```

### Switch 2, 3 y 4

```bash
configure terminal

vtp domain Grupo19
vtp password Grupo19
vtp mode client

do wri
```

## Configurando VLANs

### Switch 1

```bash
configure terminal

vlan 10
name ADMINISTRACION
vlan 20
name CONTABILIDAD
vlan 30
name VENTAS-INFORMATICA
exit

do wri
```

## Configurando enlaces troncales

### Switch 1

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

interface port-channel 3
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,1002-1005
exit

interface fastEthernet 1/15
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,1002-1005
exit

do wri
exit
```

### Switch 2

```bash
configure terminal

interface port-channel 1
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,1002-1005
exit

interface port-channel 4
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,1002-1005
exit

interface port-channel 5
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,1002-1005
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

interface port-channel 4
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,1002-1005
exit

interface fastEthernet 1/15
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,1002-1005
exit

do wri
```

### Switch 4

```bash
configure terminal

interface port-channel 3
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,1002-1005
exit

interface port-channel 5
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,1002-1005
exit

do wri
```

## Agregar STP si no está

```bash
configure terminal

spanning-tree vlan 10 root primary
spanning-tree vlan 20 root primary
spanning-tree vlan 30 root primary
end

sh spanning-tree root
```