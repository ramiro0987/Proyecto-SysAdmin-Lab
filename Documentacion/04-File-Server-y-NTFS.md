# Objetivo
Implementar un File Server utilizando Active Directory y grupos de seguridad.
# Estructura
\\RF-SRV\Recursos

├── Sistemas
├── RRHH
├── Directorio
└── Administracion
# Grupos creados
GG_SISTEMAS
GG_RRHH
GG_DIRECTORIO
GG_ADMINISTRACION
# Problema encontrado
Todos los usuarios podían acceder a todas las carpetas.
# Causa
Permisos heredados desde C:\.
# Solución
Se deshabilitó la herencia NTFS y se eliminaron los permisos del grupo Usuarios (RF\Usuarios).
# Resultado
Cada usuario accede únicamente a la carpeta correspondiente a su sector.
