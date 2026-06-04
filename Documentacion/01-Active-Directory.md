# 01 - Active Directory

## Descripción

Se implementó un entorno de Active Directory Domain Services (AD DS) utilizando Windows Server 2019 con el objetivo de centralizar la autenticación, autorización y administración de recursos dentro del dominio RF.COM.AR.

---

# Información General

## Dominio

```text
RF.COM.AR
```

## Bosque (Forest)

```text
RF.COM.AR
```

## Árbol (Tree)

```text
RF.COM.AR
```

## Controlador de Dominio

```text
RF-SRV
```

## Sistema Operativo

```text
Windows Server 2019
```

---

# Roles Instalados

## Active Directory Domain Services

Servicio encargado de:

* Autenticación centralizada
* Administración de usuarios
* Administración de grupos
* Administración de equipos
* Aplicación de GPO
* Delegación de permisos

---

## DNS

Instalado automáticamente junto con AD DS.

Responsabilidades:

* Resolución de nombres
* Localización de Controladores de Dominio
* Registro de servicios LDAP y Kerberos

---

# Servicios Utilizados por Active Directory

## LDAP

```text
TCP/UDP 389
```

Utilizado para consultas al directorio.

---

## LDAP SSL

```text
TCP 636
```

Utilizado para conexiones LDAP seguras.

---

## Kerberos

```text
TCP/UDP 88
```

Protocolo principal de autenticación dentro del dominio.

---

## DNS

```text
TCP/UDP 53
```

Resolución de nombres y descubrimiento de servicios.

---

## SMB

```text
TCP 445
```

Acceso a recursos compartidos.

---

# Base de Datos de Active Directory

Archivo principal:

```text
C:\Windows\NTDS\ntds.dit
```

Contiene:

* Usuarios
* Grupos
* Equipos
* OUs
* Objetos del dominio

---

# Particiones del Directorio

## Domain Partition

Contiene:

* Usuarios
* Equipos
* Grupos
* OUs

---

## Configuration Partition

Contiene:

* Configuración del bosque
* Sitios
* Servicios

---

## Schema Partition

Define:

* Tipos de objetos
* Atributos permitidos
* Estructura lógica del directorio

---

# Métodos de Validación

## Verificación del usuario autenticado

Comando:

```cmd
whoami
```

Resultado:

```text
RF\Administrador
```

---

## Verificación del servidor

Comando:

```cmd
hostname
```

Resultado:

```text
RF-SRV
```

---

## Enumeración de usuarios del dominio

Comando:

```cmd
net user /domain
```

Resultado observado:

```text
Administrador
Invitado
krbtgt
rflores
slopez
```

---

## Enumeración de grupos del dominio

Comando:

```cmd
net group /domain
```

Resultado observado:

```text
Admins. del dominio
Usuarios del dominio
Equipos del dominio
Controladores de dominio
Administradores de empresas
Administradores de esquema
```

---

# Autenticación

Proceso simplificado:

```text
Usuario
    │
    ▼
Controlador de Dominio
    │
    ▼
Kerberos
    │
    ▼
Ticket de autenticación
    │
    ▼
Acceso a recursos
```

---

# Beneficios Obtenidos

* Administración centralizada.
* Control de acceso mediante grupos.
* Integración con File Server.
* Escalabilidad para futuras GPO.
* Gestión simplificada de usuarios y recursos.

---

# Estado Actual

Implementado y operativo:

* Dominio RF.COM.AR
* Active Directory
* DNS
* Usuarios
* OUs
* Grupos de Seguridad
* File Server
* Permisos NTFS

---

# Próximos Pasos

* Group Policy Objects (GPO)
* DNS avanzado
* DHCP
* PowerShell
* Auditoría
* Backup del Controlador de Dominio
* Segundo Controlador de Dominio (DC adicional)
