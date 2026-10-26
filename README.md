# Cifrado Asimetrico RSA

## A. Titulo del Proyecto y Resumen Ejecutivo

Cifrado Asimetrico RSA es una aplicacion web de un solo archivo que demuestra el principio del cifrado asimetrico mediante la generacion de un par de claves RSA, el cifrado de un mensaje con la clave publica y el descifrado con la clave privada. El problema que resuelve es ilustrar de forma educativa como dos partes pueden comunicarse de forma confidencial sin compartir la clave secreta, utilizando la Web Crypto API del navegador. Su alcance tecnologico se limita al entorno del navegador; no requiere servidor, ni base de datos, ni almacenamiento persistente.

## B. Arquitectura del Sistema

La aplicacion sigue una arquitectura de cliente puro (client-side only). Toda la logica de criptografia se ejecuta dentro del navegador del usuario utilizando la Web Crypto API nativa. El flujo de datos comienza con la generacion de un par de claves RSA (publica y privada) almacenadas en memoria del navegador, continua con el cifrado de un mensaje de texto utilizando la clave publica y finaliza con el descifrado del mensaje cifrado utilizando la clave privada. No existe comunicacion con servidores externos ni almacenamiento en disco, salvo la opcion de exportar las claves en formato JWK como archivos JSON descargables por el usuario.

## C. Caracteristicas Tecnicas Clave

- Generacion de claves RSA mediante la Web Crypto API del navegador (algoritmo RSA-OAEP).
- Cifrado de mensajes con la clave pública y descifrado con la clave privada, todo en el lado del cliente.
- Exportacion e importacion de claves en formato JWK (JSON Web Key) como archivos .json descargables.
- Interfaz de usuario responsiva construida con HTML5 y TailwindCSS mediante CDN.
- Ausencia de servidor, base de datos, persistencia de datos o almacenamiento en sesion.
- No utiliza mecanismos de concurrencia, procesamiento en tiempo real ni protocolos de red propios.
- Seguridad limitada al ambito del navegador; la clave privada se descarga en texto plano y es responsabilidad del usuario su custodia.

## D. Especificacion del Stack Tecnologico

| Categoria | Tecnologia / Librería |
|-----------|----------------------|
| Frontend | HTML5, JavaScript (Web Crypto API), TailwindCSS (CDN) |
| Criptografia | RSA-OAEP (Web Crypto API) |
| Navegador | Chrome, Edge, Firefox, Safari con soporte de Web Crypto API |

## E. Guia de Instalacion, Configuracion y Despliegue

### Requisitos previos del sistema

- Navegador moderno con soporte de Web Crypto API (Chrome, Edge, Firefox, Safari).
- Opcional: servidor HTTP local (por ejemplo, Python) si el navegador bloquea la API de criptografia al abrir el archivo directamente.

### Secuencia de comandos para clonacion e instalacion

```bash
git clone https://github.com/Matthew-Garay/CifradoAsimetrico.git
cd CifradoAsimetrico
```

### Configuracion de variables de entorno

Este proyecto no requiere archivo .env ni variables de entorno.

### Comandos para ejecucion en entorno de Desarrollo

Abrir el archivo `index.html` con doble clic en el navegador. Si el navegador bloquea la API de criptografia, servir el archivo por HTTP local:

```bash
python -m http.server 8000
```

Luego abrir `http://localhost:8000` en el navegador.

### Comandos para ejecucion en entorno de Produccion

No aplica entorno de produccion separado; es una aplicacion de un solo archivo ejecutada en el navegador del cliente.

## F. Creditos de Autoría

Desarrollado por: Matthew Ilveneff Garay Pérez
Correo Electronico: 1911.garay.perez@gmail.com

