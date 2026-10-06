# Cifrado Asimetrico (RSA)

Pagina que demuestra el cifrado asimetrico en la practica: genera un par de claves RSA, cifra con la publica y descifra con la privada.

Todo pasa en el navegador con la Web Crypto API, sin servidor ni base de datos. Las claves se exportan en formato JWK para descargarlas y volver a cargarlas. Es un solo archivo, se abre con doble clic.

## Uso

1. Generar claves (descarga los dos .json)
2. Cifrar con la clave publica
3. Descifrar con la clave privada

Si al abrirlo por archivo el navegador bloquea la API de criptografia, hay que servirlo por HTTP con `python -m http.server 8000` y entrar a localhost:8000.

## Advertencia

Proyecto educativo. La privada se descarga en texto plano: no subirla a ningun lado.
