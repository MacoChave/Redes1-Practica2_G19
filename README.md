# Redes1-Practica2_G19

- [Redes1-Practica2_G19](#redes1-practica2_g19)
  - [INTEGRANTES](#integrantes)
  - [Configuración de red multipunto](#configuración-de-red-multipunto)
  - [Configuración de la topología de red en GNS3](#configuración-de-la-topología-de-red-en-gns3)
    - [Topología 1](#topología-1)
    - [Topología 2](#topología-2)
    - [Topología 3](#topología-3)
  - [Configuración por dispositivo](#configuración-por-dispositivo)
  - [Comandos utilizados](#comandos-utilizados)
    - [Archivos de configuración](#archivos-de-configuración)

## INTEGRANTES

|  CARNET   | NOMBRE                        |
| :-------: | ----------------------------- |
| 201020831 | Marco Antonio Chavez Fuentes  |
| 201612331 | Jose Orlando Wannan Escobar   |
| 201602421 | Diego Alejandro Vasquez       |
| 201712350 | Helmut Efrain Najarro Alvarez |

## Configuración de red multipunto

## Configuración de la topología de red en GNS3

### Topología 1

### Topología 2

### Topología 3

## Configuración por dispositivo

## Comandos utilizados

Para configurar los switches de capa 3, se siguieron los siguientes pasos:

- Crear Port Channels a cada switch de las 3 topologías
- Crear vtp de tipo cliente a cada switch de las 3 topologías, excepto al 1er switch de la topología 2 que debía ser tipo servidor
- En el switch servidor de la topología 3, se crearon las 3 vlans
- En cada switch se configuraron los enlaces troncales y de acceso según el puerto lo requiera.

### Archivos de configuración

[Configuración topología 1](Topo1_conf.md)

[Configuración topología 2](Topo2_conf.md)

[Configuración topología 3](Topo3_conf.md)
