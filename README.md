# Directorio Dolorense · Consumo de API local con Flutter y TDD

**Materia:** Desarrollo de Aplicaciones Móviles
**Alumno:** González López Yael Isaac
**Fecha:** 6 de noviembre de 2026

## Descripción

Directorio de negocios de Dolores Hidalgo. Una API REST hecha en Node (corriendo en la computadora) guarda los negocios, y la app Flutter los consulta (GET), agrega (POST), marca como favoritos (PUT) y elimina (DELETE). El cliente HTTP y el ViewModel se desarrollaron con TDD usando MockClient, así que las pruebas no dependen de red ni de servidor. La pantalla maneja los cinco estados: inicial, cargando, listo, vacío y error.

## Estructura del proyecto

![Estructura del proyecto](capturas/01_estructura.jpeg)

## Pruebas de casos (éxito y fallo)

## Pruebas del modelo (4) · test/negocio_test.dart

### Prueba 1: desdeJson lee todos los campos

**Éxito:**

<img width="308" height="280" alt="image" src="https://github.com/user-attachments/assets/78b145a5-cb40-43e2-b37a-62eb0c7399b4" />

**Fallo:**

<img width="308" height="158" alt="image" src="https://github.com/user-attachments/assets/91f5a71a-c838-4143-bc1b-da29cad7c000" />

### Prueba 2: campos opcionales ausentes usan valores por omisión

**Éxito:**

<img width="311" height="104" alt="image" src="https://github.com/user-attachments/assets/5022c0ad-7241-4d45-ad03-f1ed4b249392" />

**Fallo:**

<img width="309" height="119" alt="image" src="https://github.com/user-attachments/assets/030d6c0a-161e-4f57-82c2-ca2958f71ca8" />

### Prueba 3: aJson no manda id cuando es nuevo

**Éxito:**

<img width="311" height="107" alt="image" src="https://github.com/user-attachments/assets/37e5be82-bded-4719-9480-a393556193e1" />

**Fallo:**

<img width="312" height="110" alt="image" src="https://github.com/user-attachments/assets/2d09ebb0-6f24-4574-9c56-a6c365544e0f" />

### Prueba 4: copiarCon cambia solo el favorito

**Éxito:**

<img width="310" height="130" alt="image" src="https://github.com/user-attachments/assets/cbeb87d0-d3fb-4794-8f42-74b85ca39432" />

**Fallo:**

<img width="311" height="168" alt="image" src="https://github.com/user-attachments/assets/304393e5-706a-43ac-ae8d-b7bb6afa7062" />

## Pruebas del cliente HTTP (8) · test/negocios_api_test.dart

### Prueba 5: listar convierte el JSON en objetos Negocio

**Éxito:**

<img width="310" height="179" alt="image" src="https://github.com/user-attachments/assets/5b18762b-0bda-439f-bb03-5532a6d652d6" />

**Fallo:**

<img width="313" height="154" alt="image" src="https://github.com/user-attachments/assets/596e9dd3-a2d1-4914-ad08-88aeb7cf5a1b" />

### Prueba 6: status 500 lanza ErrorServidorException con el código

**Éxito:**

<img width="308" height="123" alt="image" src="https://github.com/user-attachments/assets/7e2c29b4-20fb-4e77-a172-cf9df0b7e54c" />

**Fallo:**

<img width="310" height="140" alt="image" src="https://github.com/user-attachments/assets/944b1a18-457a-4207-b3aa-b97687c7d8e5" />

### Prueba 7: sin red lanza SinConexionException

**Éxito:**

<img width="311" height="106" alt="image" src="https://github.com/user-attachments/assets/659078bf-ef0a-4659-a6b1-e7ca5959c2cb" />

**Fallo:**

<img width="311" height="110" alt="image" src="https://github.com/user-attachments/assets/f65c81b3-b1ac-44e8-ad42-5259b0cc9e3d" />

### Prueba 8: timeout se trata como sin conexión

**Éxito:**

<img width="311" height="155" alt="image" src="https://github.com/user-attachments/assets/d7b94d03-70d6-462c-9483-26723f1433de" />

**Fallo:**

<img width="311" height="158" alt="image" src="https://github.com/user-attachments/assets/7f89bb63-7d2b-4562-953f-213be5dc3099" />

### Prueba 9: JSON roto lanza RespuestaInvalidaException

**Éxito:**

<img width="314" height="111" alt="image" src="https://github.com/user-attachments/assets/7b9fca17-2429-40b4-beb2-c31b0dacfd0c" />

**Fallo:**

<img width="313" height="113" alt="image" src="https://github.com/user-attachments/assets/db2633d1-b578-4dda-bf2f-de937cbaab8c" />

### Prueba 10: listar con búsqueda manda el parámetro q codificado

**Éxito:**

<img width="313" height="130" alt="image" src="https://github.com/user-attachments/assets/ab64a9fc-ff7a-4b62-b45e-7df562c01f65" />

**Fallo:**

<img width="314" height="134" alt="image" src="https://github.com/user-attachments/assets/4ce03898-6922-4d51-8b6c-58d49431d28c" />

### Prueba 11: crear envía JSON con Content-Type correcto

**Éxito:**

<img width="311" height="176" alt="image" src="https://github.com/user-attachments/assets/b12b3c93-9321-44aa-a9ad-70ccb3973c31" />

**Fallo:**

<img width="311" height="176" alt="image" src="https://github.com/user-attachments/assets/e995d9f3-1778-4aec-87ee-7a6a384328da" />

### Prueba 12: eliminar usa DELETE al id correcto

**Éxito:**

<img width="313" height="155" alt="image" src="https://github.com/user-attachments/assets/7d2da97f-dca7-41eb-b51f-a5d34f54c9e5" />

**Fallo:**

<img width="311" height="157" alt="image" src="https://github.com/user-attachments/assets/31a75a62-2852-4226-9d42-265fb3df0e09" />

## Pruebas del ViewModel (5) · test/viewmodel_test.dart

### Prueba 13: cargar con datos termina en listo

**Éxito:**

<img width="308" height="162" alt="image" src="https://github.com/user-attachments/assets/9b05bb78-5dcd-49d9-8985-cada92866188" />

**Fallo:**

<img width="310" height="148" alt="image" src="https://github.com/user-attachments/assets/277fd01f-a669-470c-b4c1-96fa0fbd355b" />

### Prueba 14: cargar con lista vacía termina en vacio

**Éxito:**

<img width="311" height="124" alt="image" src="https://github.com/user-attachments/assets/ff544678-5ec5-4203-92d1-8db43f6bd0f1" />

**Fallo:**

<img width="312" height="118" alt="image" src="https://github.com/user-attachments/assets/d241fa0c-7da2-4f2d-8fca-7f25e0f550b3" />

### Prueba 15: cargar con error de servidor termina en error con mensaje

**Éxito:**

<img width="313" height="131" alt="image" src="https://github.com/user-attachments/assets/5ec6b906-6d73-421d-99e3-4992adaeda06" />

**Fallo:**

<img width="312" height="133" alt="image" src="https://github.com/user-attachments/assets/31c6ffff-4a9d-4a1d-9bfe-ed7615ce4869" />

### Prueba 16: eliminar quita el negocio de la lista

**Éxito:**

<img width="311" height="156" alt="image" src="https://github.com/user-attachments/assets/4a8fd1b5-4ce8-4141-b0f9-d9f20f59859a" />

**Fallo:**

<img width="308" height="170" alt="image" src="https://github.com/user-attachments/assets/a0477fcc-3e53-457d-ad77-b786756bd7cd" />

### Prueba 17: alternarFavorito actualiza con la respuesta del servidor

**Éxito:**

<img width="311" height="173" alt="image" src="https://github.com/user-attachments/assets/4d90fdcb-ba52-4066-9eea-defa3293b46f" />

**Fallo:**

<img width="313" height="160" alt="image" src="https://github.com/user-attachments/assets/64d15c50-0fd4-4d8c-845d-e9091d243d25" />

## Todas las pruebas en verde (17)

![Pruebas en verde](capturas/05_pruebas.jpeg)

## Evidencia de la aplicación

### API corriendo con node server.js

![API encendida](capturas/02_api_encendida.jpeg)

### Peticiones registradas en la terminal del servidor

![Peticiones curl](capturas/03_api_curl.jpeg)

### Sin conexión (servidor apagado) con botón Reintentar

![Estado de error](capturas/08_app_error.jpeg)
