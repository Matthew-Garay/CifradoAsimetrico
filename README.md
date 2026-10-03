# Cifrado Asimétrico (RSA)

Página web que demuestra el cifrado asimétrico con RSA. Genera un par de
claves, cifra un mensaje con la clave pública y lo descifra con la privada, para
enseñar de forma práctica por qué la clave pública se puede repartir sin
riesgo y la privada no.

Todo ocurre **en el navegador**. No hay servidor, no hay base de datos y
ningún dato sale del equipo.

## Cómo funciona

La criptografía la hace la **Web Crypto API** del navegador
(`window.crypto.subtle`), no una implementación propia. Eso importa: el
algoritmo está auditado por el propio navegador y el material de clave se
genera en el módulo criptográfico del sistema, no en JavaScript.

El objeto de clave generado es:

```js
{
  name: "RSA-OAEP",
  modulusLength: 2048,
  publicExponent: new Uint8Array([1, 0, 1]),  // 65537
  hash: "SHA-256",
}
```

| Parámetro | Valor | Por qué |
|-----------|-------|---------|
| Algoritmo | `RSA-OAEP` | el relleno OAEP, no el PKCS#v1.5 antiguo |
| Tamaño del módulo | 2048 bits | el mínimo que se considera aceptable hoy |
| Exponente público | 65537 | primo pequeño y eficiente |
| Hash | SHA-256 | para el esquema OAEP |

### Las claves se exportan en formato JWK

`crypto.subtle.exportKey("jwk", ...)` devuelve el JSON de la clave, y la página
ofrece descargar `clave_publica.json` y `clave_privada.json`. Para volver a
usarlas, `importKey("jwk", ...)` las carga desde un selector de archivos.

## Cómo usarlo

Es un único archivo `index.html`. Ábrelo con doble clic; no necesita servidor
ni instalación.

> La Web Crypto API **solo está disponible en contextos seguros**. Si abres el
> archivo con doble clic desde `file://`, `window.crypto.subtle` puede venir
> indefinido en algunos navegadores y el botón de generar claves fallará con un
> error poco descriptivo. Si te pasa, sírvelo por HTTP:
>
> ```bash
> python -m http.server 8000
> ```
>
> y entra en `http://localhost:8000`.

1. **Generar Claves** — descarga los dos `.json`
2. **Cifrar** — carga `clave_publica.json`, escribe el mensaje y cifra
3. **Descifrar** — carga `clave_privada.json`, pega el mensaje cifrado y descifra

El recorrido completo sirve para ver la propiedad que define a RSA: el mismo
par de claves cifra y descifra, pero solo la mitad pública es pública.

## Estructura

```
index.html          la página entera: marcado, estilos y script
images/
  tescologo.png     logo de la escuela
  siclogo.png       logo del instituto
```

El diseño usa Tailwind por CDN y la tipografía Inter de Google Fonts. No hay
paso de compilación ni dependencias de JavaScript.

## Advertencia

La clave privada se descarga a tu equipo en claro, como un `.json` de texto
plano. Trátala como una contraseña: no la subas a ningún repositorio ni la
compartas. Y recuerda que el cifradoRSA no cifra el mensaje entero: con 2048
bits y relleno OAEP el límite práctico es del orden de 190 bytes. Para
contenidos largos hay que usar un cifrado simétrico para el cuerpo y RSA solo
para envolver la clave de sesión.

Este proyecto es **educativo**. Para proteger datos reales, usa
[librisage](https://age-encryption.org/) o GPG.
