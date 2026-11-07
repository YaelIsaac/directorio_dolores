# Directorio Dolorense · Flutter + API local en Node (TDD)

**Materia:** Desarrollo Móvil Integral
**Universidad:** UTNG, Dolores Hidalgo
**Alumno:** González López Yael Isaac
**Fecha:** 6 de Noviembre de 2026

## Descripción

Directorio de negocios de Dolores Hidalgo. Una API REST en Node (un solo archivo, sin dependencias) guarda los negocios; la app Flutter los consulta, agrega, marca como favoritos y elimina. El cliente HTTP se probó con `MockClient` (sin red ni servidor) y la pantalla cubre los 5 estados: inicial, cargando, listo, vacío y error.


## Estructura del proyecto

![Estructura del proyecto](capturas/01_estructura.jpeg)


## Evidencia de la API

### API encendida
![API encendida](capturas/02_api_encendida.jpeg)


### Peticiones con curl: lista, crear y borrar
![Peticiones curl](capturas/03_api_curl.jpeg)


### Códigos de error: GET /negocios/99 (404) y POST sin categoría (400)
![Códigos 404 y 400](capturas/04_api_errores.jpeg)


### Todas las pruebas en verde (17)
![Pruebas en verde](capturas/05_pruebas.jpeg)


## Evidencia de la aplicación

### Lista de negocios (estado listo)
![Lista de negocios](capturas/06_app_lista.jpeg)


### Favorito, agregar y eliminar, con la terminal de la API mostrando las peticiones
![Favorito, agregar y eliminar](capturas/07_app_acciones.jpeg)


### Sin servidor: mensaje de error y botón Reintentar
![Estado de error](capturas/08_app_error.jpeg)


### Servidor encendido de nuevo: la lista regresa
![Después de reintentar](capturas/09_app_reintentar.jpeg)