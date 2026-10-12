<div align="center">

# Cifrado Asimétrico (RSA)

**Página web que demuestra el cifrado asimétrico** mediante la generación de claves RSA, cifrado con la clave pública y descifrado con la privada.

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square)]()
[![Web Crypto API](https://img.shields.io/badge/Web%20Crypto%20API-RSA-2ea44f?style=flat-square)]()
[![TailwindCSS](https://img.shields.io/badge/TailwindCSS-38B2AC?style=flat-square)](https://tailwindcss.com/)

</div>

---

## Descripción

Aplicación web **100% del lado del cliente** que demuestra el principio del **cifrado asimétrico** en un entorno controlado: genera un par de claves **RSA**, cifra un mensaje con la clave pública y lo descifra con la clave privada.

Está pensada como material educativo para ilustrar cómo dos partes pueden comunicarse de forma confidencial sin compartir la clave secreta. **No requiere servidor ni base de datos.**

## Características

- **Generación de claves RSA** con la **Web Crypto API** del navegador.
- **Cifrado** con la clave pública y **descifrado** con la clave privada.
- **Exportación e importación** de claves en formato **JWK** (descargables como `.json`).
- Interfaz responsiva con **TailwindCSS**.
- Todo ocurre en el navegador: sin servidor ni almacenamiento.

## Tecnologías utilizadas

- **Frontend:** HTML5, JavaScript (Web Crypto API), TailwindCSS (CDN)
- **Criptografía:** RSA-OAEP (Web Crypto API)

## Requisitos previos

- Navegador moderno con soporte de **Web Crypto API** (Chrome, Edge, Firefox, Safari).
- Opcional: servidor HTTP local si el navegador bloquea la criptografía al abrir el archivo directamente.

## Instalación

Es un archivo único; no requiere instalación.

```bash
git clone https://github.com/Matthew-Garay/CifradoAsimetrico.git
cd CifradoAsimetrico
```

Abre `index.html` con doble clic. Si el navegador bloquea la API de criptografía, sírvelo por HTTP:

```bash
python -m http.server 8000
# Abre http://localhost:8000
```

## Uso

1. **Generar claves** — descarga los dos archivos `.json` (pública y privada).
2. **Cifrar** — pega la clave pública y escribe el mensaje.
3. **Descifrar** — pega la clave privada y el mensaje cifrado.

## Estructura del proyecto

```
CifradoAsimetrico/
├── index.html           # Aplicación completa (HTML + CSS + JS)
├── images/
│   ├── siclogo.png
│   └── tescologo.png
└── README.md
```

## Advertencia

Proyecto **educativo**. La clave privada se descarga en texto plano: **no la subas a ningún lado** ni la compartas.

## Licencia

Proyecto académico y educativo; puedes usarlo libremente con fines de aprendizaje.

## Autor

**Matthew Garay** — [GitHub](https://github.com/Matthew-Garay)

