# COMPLETAR  
Comparando sus conocimientos antes de hacer la práctica con sus conocimientos después de hacer la tarea, explicar los principales aprendizajes logrados para beneficio de su formación profesional.  
Si solucionó un problema presentado o utilizó otros comandos que no se mencionan al realizar la práctica también se debe documentar.
#
Antes de la práctica sabía lo básico sobre docker, no tenía claro cómo conservar los datos cuando se elimina un contenedor.
#
Aprendí que los contenedores son desechables y que los datos deben guardarse fuera de ellos. Comprobé que al eliminar y recrear WordPress, el tema y la entrada se conservaron gracias a las carpetas db y www del host.
#
**Problema 1:server-postgres se detenía:** pgAdmin mostraba failed to resolve host 'server-postgres'. Con docker ps -a vi que el contenedor estaba caído y con docker logs server-postgres descubrí la causa: desde la versión 18 de la imagen postgres, el punto de montaje cambió de /var/lib/postgresql/data a /var/lib/postgresql. Eliminé el contenedor y el volumen, los recreé montando en la nueva ruta y funcionó.
#
**Benificio profesional**
Estas habilidades aplican directamente en desarrollo y despliegue de aplicaciones asi como: reproducir entornos idénticos en cualquier máquina, separar aplicación y datos, diagnosticar fallos leyendo logs y documentación,
