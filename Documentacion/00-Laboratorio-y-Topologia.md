# 00 - Laboratorio y Topología

## Objetivo

Crear un entorno de laboratorio para adquirir experiencia práctica en Infraestructura Windows, Active Directory, File Server, permisos NTFS, GPO y administración de usuarios.

El objetivo es simular un entorno corporativo real para desarrollar habilidades orientadas a posiciones de SysAdmin e Infraestructura.

---

# Entorno de Laboratorio

## Plataforma de Virtualización

* Oracle VirtualBox

## Equipo Host

* Sistema Operativo: Windows 11

---

# Máquinas Virtuales

## Servidor Principal

### Información General

* Nombre del servidor: RF-SRV
* Sistema Operativo: Windows Server 2019
* Función:

  * Active Directory Domain Services (AD DS)
  * DNS
  * File Server

### Recursos Asignados

* CPU: [Completar]
* RAM: [Completar]
* Disco: [Completar]

---

## Cliente

### Información General

* Sistema Operativo: Windows 10
* Unido al dominio RF.COM.AR
* Utilizado para pruebas de autenticación y acceso a recursos compartidos

### Recursos Asignados

* CPU: [Completar]
* RAM: [Completar]
* Disco: [Completar]

---

# Configuración de Red

## Servidor

* Dirección IP: [Completar]
* Máscara de Subred: [Completar]
* Gateway: [Completar]
* DNS: [Completar]

## Cliente

* DNS apuntando al controlador de dominio RF-SRV.

---

# Instalación de Windows Server

## Procedimiento

1. Creación de la máquina virtual en VirtualBox.
2. Montaje de la ISO de Windows Server 2019.
3. Instalación del sistema operativo.
4. Configuración inicial del servidor.
5. Cambio de nombre del servidor a:

```text
RF-SRV
```

6. Configuración de IP estática.
7. Reinicio del servidor.

---

# Instalación de Active Directory

## Instalación del Rol AD DS

Desde Server Manager:

1. Seleccionar "Add Roles and Features".
2. Elegir instalación basada en roles.
3. Seleccionar el servidor RF-SRV.
4. Instalar el rol:

```text
Active Directory Domain Services
```

5. Finalizar instalación.

---

# Creación del Dominio

## Promoción a Controlador de Dominio

Una vez instalado AD DS:

1. Seleccionar:

```text
Promote this server to a domain controller
```

2. Elegir:

```text
Add a new forest
```

3. Configurar el dominio:

```text
RF.COM.AR
```

4. Definir contraseña DSRM.
5. Validar prerrequisitos.
6. Completar la instalación.
7. Reiniciar el servidor.

---

# Validación del Dominio

Se ejecutaron los siguientes comandos:

```cmd
whoami
hostname
net user /domain
net group /domain
```

## Resultados

### Usuario

```text
RF\Administrador
```

### Hostname

```text
RF-SRV
```

### Usuarios del Dominio

```text
Administrador
Invitado
krbtgt
rflores
slopez
```

### Grupos del Dominio

```text
Administradores del dominio
Usuarios del dominio
Equipos del dominio
Controladores de dominio
Administradores de empresas
Administradores de esquema
```

---

# Unión del Cliente al Dominio

## Procedimiento

1. Configuración del DNS apuntando al controlador de dominio.
2. Acceso a Propiedades del Sistema.
3. Cambio de grupo de trabajo a dominio.
4. Ingreso del dominio:

```text
RF.COM.AR
```

5. Autenticación con una cuenta administrativa.
6. Reinicio del equipo.

---

# Topología del Laboratorio

```text
Cliente Windows 10
        │
        │
        ▼
RF-SRV
├── Active Directory
├── DNS
└── File Server
```

---

# Estado Actual del Laboratorio

## Active Directory

* Dominio RF.COM.AR operativo.
* Controlador de Dominio funcional.
* Autenticación validada.

## Usuarios

### Sistemas

* rflores
* slopez

### RRHH

* mgonzalez

### Directorio

* jperez

### Administración

* agarcia

---

## OUs

```text
RF.COM.AR
│
└── Usuarios
    ├── Sistemas
    ├── RRHH
    ├── Directorio
    └── Administracion
```

---

## Grupos de Seguridad

```text
GG_SISTEMAS
GG_RRHH
GG_DIRECTORIO
GG_ADMINISTRACION
```

---

## File Server

Recurso compartido:

```text
\\RF-SRV\Recursos
```

Estructura:

```text
Recursos
│
├── Sistemas
├── RRHH
├── Directorio
└── Administracion
```

---

## Permisos

Los permisos de acceso a carpetas se administran mediante grupos de seguridad.

Ejemplo:

```text
GG_SISTEMAS
→ Recursos\Sistemas
```

```text
GG_RRHH
→ Recursos\RRHH
```

```text
GG_DIRECTORIO
→ Recursos\Directorio
```

```text
GG_ADMINISTRACION
→ Recursos\Administracion
```

---

# Próximos Objetivos

* Documentación de Active Directory.
* Documentación de OUs y Usuarios.
* Documentación de Grupos de Seguridad.
* Documentación de File Server y NTFS.
* Implementación de Group Policy Objects (GPO).
* Configuración de DNS.
* Configuración de DHCP.
* Automatización mediante PowerShell.
* Implementación de Backup.
* Monitoreo de infraestructura.

---

# Conclusión

Se implementó exitosamente un entorno de laboratorio basado en Active Directory utilizando Windows Server 2019 y VirtualBox.

Actualmente el laboratorio cuenta con autenticación centralizada, estructura organizativa por áreas, grupos de seguridad y un File Server con permisos administrados mediante NTFS y Active Directory.


