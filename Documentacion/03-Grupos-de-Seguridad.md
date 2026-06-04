# 03 - Grupos de Seguridad

# Objetivo

Diseñar e implementar una estrategia de administración de permisos basada en Grupos de Seguridad de Active Directory, eliminando la dependencia de asignaciones directas sobre usuarios individuales y estableciendo una arquitectura escalable para la gestión de accesos.

El objetivo principal fue construir una estructura que permita administrar recursos de forma centralizada, replicando prácticas utilizadas habitualmente en entornos corporativos.

---

# Situación Inicial

Luego de la implementación del dominio RF.COM.AR y la creación de la estructura organizativa mediante Unidades Organizativas (OU), surgió la necesidad de controlar el acceso a recursos compartidos de acuerdo con el sector al que pertenece cada usuario.

Inicialmente todos los usuarios del laboratorio coexistían dentro del mismo dominio, por lo que era necesario implementar un mecanismo que permitiera separar los accesos de forma lógica y administrable.

---

# Problema a Resolver

Asignar permisos directamente sobre usuarios individuales genera diversos inconvenientes:

* Incrementa la complejidad administrativa.
* Dificulta la incorporación de nuevos usuarios.
* Complica la auditoría de permisos.
* Genera configuraciones inconsistentes.
* Aumenta el riesgo de errores operativos.

Ejemplo de una implementación no recomendada:

```text
rflores -> Permiso carpeta Sistemas
slopez -> Permiso carpeta Sistemas
mgonzalez -> Permiso carpeta RRHH
jperez -> Permiso carpeta Directorio
agarcia -> Permiso carpeta Administracion
```

En este escenario cada nuevo usuario requiere una modificación manual sobre los permisos del recurso.

---

# Estrategia de Diseño

Se decidió implementar un modelo basado en grupos de seguridad.

La estrategia adoptada fue:

```text
Usuario
    ↓
Grupo de Seguridad
    ↓
Permiso
    ↓
Recurso
```

De esta manera los permisos se asignan exclusivamente a grupos y nunca directamente a usuarios.

---

# Arquitectura Implementada

## Dominio

```text
RF.COM.AR
```

---

## Grupos de Seguridad

Se implementaron los siguientes grupos:

```text
GG_SISTEMAS
GG_RRHH
GG_DIRECTORIO
GG_ADMINISTRACION
```

---

## Tipo de Grupo

### Ámbito

```text
Global
```

### Tipo

```text
Seguridad
```

---

# Justificación Técnica

Se seleccionaron grupos Globales de Seguridad debido a que:

* Todos los usuarios pertenecen al mismo dominio.
* Los grupos serán utilizados para permisos NTFS.
* Permiten una administración centralizada.
* Son la práctica recomendada para la mayoría de los escenarios corporativos.

La utilización de grupos Globales de Seguridad facilita la futura integración con:

* File Servers.
* GPO.
* Recursos compartidos.
* Sistemas corporativos.
* Microsoft Exchange.

---

# Implementación

## GG_SISTEMAS

Usuarios asociados:

```text
rflores
slopez
```

---

## GG_RRHH

Usuarios asociados:

```text
mgonzalez
```

---

## GG_DIRECTORIO

Usuarios asociados:

```text
jperez
```

---

## GG_ADMINISTRACION

Usuarios asociados:

```text
agarcia
```

---

# Relación con la Estructura Organizativa

Las OUs fueron utilizadas para organizar objetos.

Los Grupos de Seguridad fueron utilizados para administrar permisos.

Esta separación de responsabilidades permite mantener una infraestructura más ordenada y escalable.

## Organización

```text
Usuarios
├── Sistemas
├── RRHH
├── Directorio
└── Administracion
```

## Seguridad

```text
GG_SISTEMAS
GG_RRHH
GG_DIRECTORIO
GG_ADMINISTRACION
```

---

# Integración con el File Server

Los grupos implementados fueron posteriormente utilizados para controlar el acceso al recurso compartido:

```text
\\RF-SRV\Recursos
```

---

## Carpeta Sistemas

```text
GG_SISTEMAS
```

---

## Carpeta RRHH

```text
GG_RRHH
```

---

## Carpeta Directorio

```text
GG_DIRECTORIO
```

---

## Carpeta Administracion

```text
GG_ADMINISTRACION
```

---

# Validaciones Realizadas

Se verificó el correcto funcionamiento del modelo mediante pruebas de acceso desde distintos usuarios del dominio.

## Resultado esperado

```text
slopez
    ↓
Acceso permitido
    ↓
Recursos\Sistemas
```

```text
slopez
    ↓
Acceso denegado
    ↓
Recursos\RRHH
```

---

## Resultado obtenido

La validación confirmó que cada usuario puede acceder únicamente a los recursos asociados a su grupo de seguridad.

---

# Beneficios Obtenidos

La implementación permitió:

* Centralizar la administración de permisos.
* Simplificar futuras incorporaciones de usuarios.
* Reducir errores administrativos.
* Mejorar la escalabilidad del entorno.
* Facilitar futuras auditorías.
* Implementar control de acceso basado en roles.

---

# Evolución Futura

La arquitectura implementada fue diseñada para servir como base de futuras funcionalidades.

Las siguientes etapas del proyecto contemplan:

## Group Policy Objects (GPO)

Aplicación de configuraciones por sector.

---

## Mapeo Automático de Unidades

Asignación automática de recursos compartidos mediante GPO.

---

## Delegación Administrativa

Administración descentralizada de OUs.

---

## Integración con Exchange

Creación de grupos de distribución complementarios.

---

## Auditoría de Accesos

Monitoreo de cambios y accesos sobre recursos compartidos.

---

# Conclusión Técnica

Se implementó una arquitectura basada en grupos Globales de Seguridad que desacopla la asignación de permisos de los usuarios individuales.

Esta estrategia constituye una práctica recomendada dentro de entornos Active Directory y proporciona una base sólida para la administración de recursos, la aplicación de políticas y la futura expansión de la infraestructura del laboratorio.

El modelo implementado replica el enfoque utilizado habitualmente en organizaciones que administran accesos mediante Active Directory y File Server corporativos.

