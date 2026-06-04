# Laboratorio y Topología

## Objetivo

Crear un entorno de laboratorio para practicar Active Directory, File Server, GPO y administración de infraestructura Windows.

## Entorno utilizado

### Host

* Windows 11
* VirtualBox

### Máquinas virtuales

#### RF-SRV

* Windows Server 2019
* Controlador de Dominio
* DNS
* File Server

#### Cliente

* Windows 10
* Unido al dominio RF.COM.AR

## Recursos asignados

### RF-SRV

* CPU:
* RAM:
* Disco:

### Cliente

* CPU:
* RAM:
* Disco:

## Configuración de red

* Adaptador:
* Rango IP:
* DNS apuntando al Domain Controller

## Instalación de Active Directory

1. Instalación del rol AD DS.
2. Promoción a Controlador de Dominio.
3. Creación del dominio RF.COM.AR.
4. Configuración de DNS.

## Topología

Cliente Windows 10
│
▼
RF-SRV
├── Active Directory
├── DNS
└── File Server

## Estado actual

* Dominio operativo.
* Usuarios creados.
* OUs configuradas.
* Grupos de seguridad creados.
* File Server funcionando.
* Permisos NTFS implementados.

