# Usuarios y OUs

## Objetivo

Organizar los usuarios del dominio mediante Unidades Organizativas (OU) para facilitar la administración, aplicación de GPO y asignación de permisos.

## Dominio

RF.COM.AR

## Usuarios creados

| Usuario   | Área           |
| --------- | -------------- |
| rflores   | Sistemas       |
| slopez    | Sistemas       |
| mgonzalez | RRHH           |
| jperez    | Directorio     |
| agarcia   | Administración |

## Estructura de OUs

```text
RF.COM.AR
│
└── Usuarios
    ├── Sistemas
    │   ├── rflores
    │   └── slopez
    │
    ├── RRHH
    │   └── mgonzalez
    │
    ├── Directorio
    │   └── jperez
    │
    └── Administracion
        └── agarcia
```

## Procedimiento realizado

1. Se creó la OU principal "Usuarios".
2. Se crearon las OUs:

   * Sistemas
   * RRHH
   * Directorio
   * Administracion
3. Se movieron los usuarios a la OU correspondiente según su sector.

## Beneficios

* Mejor organización del Active Directory.
* Posibilidad de aplicar GPO por sector.
* Facilita la administración de usuarios.
* Escalable para agregar nuevos departamentos.

## Resultado

Los usuarios quedaron organizados según su área de trabajo dentro del dominio RF.COM.AR.

