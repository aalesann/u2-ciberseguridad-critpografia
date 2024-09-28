
# Guía Práctica de Criptografía en Kali Linux

## 1. Introducción a la Criptografía
- **Objetivo:** Introducir a los estudiantes a los conceptos básicos de criptografía: cifrado, descifrado, claves, algoritmos simétricos y asimétricos.
- **Herramientas a utilizar:** `OpenSSL`, `GPG`, `hashcat`, `John the Ripper`.

## 2. Ejercicio 1: Cifrado Simétrico con OpenSSL

**Descripción:**
En este ejercicio aprenderás a cifrar y descifrar un archivo utilizando un algoritmo de cifrado simétrico (AES).

**Pasos:**
1. **Crea un archivo de texto:**
   ```bash
   echo "Este es un mensaje secreto" > mensaje.txt
   ```

2. **Cifra el archivo con AES-256-CBC:**
   ```bash
   openssl enc -aes-256-cbc -salt -in mensaje.txt -out mensaje_cifrado.txt -k clave123
   ```

3. **Descifra el archivo:**
   ```bash
   openssl enc -d -aes-256-cbc -in mensaje_cifrado.txt -out mensaje_descifrado.txt -k clave123
   ```

4. **Verifica el contenido:**
   ```bash
   cat mensaje_descifrado.txt
   ```

**Explicación Detallada:**
- En el primer paso, se crea un archivo de texto llamado `mensaje.txt` que contiene un mensaje simple.
- Luego, el archivo se cifra utilizando el algoritmo AES-256-CBC con una clave proporcionada (`clave123`). El uso de `-salt` asegura que el cifrado sea más seguro al añadir aleatoriedad.
- El archivo cifrado se guarda como `mensaje_cifrado.txt`.
- El tercer paso muestra cómo descifrar el archivo cifrado usando la misma clave, generando `mensaje_descifrado.txt`, que debería contener el mensaje original.
- Finalmente, el comando `cat` verifica que el descifrado fue exitoso mostrando el contenido original.

## 3. Ejercicio 2: Cifrado Asimétrico con GPG

**Descripción:**
En este ejercicio aprenderás a generar pares de claves, cifrar un mensaje con la clave pública y descifrarlo con la clave privada.

**Pasos:**
1. **Genera un par de claves GPG:**
   ```bash
   gpg --full-generate-key
   ```

2. **Exporta la clave pública:**
   ```bash
   gpg --export -a "nombre" > clave_publica.asc
   ```

3. **Cifra un mensaje con la clave pública:**
   ```bash
   echo "Mensaje importante y confidencial" > mensaje.txt
   gpg --encrypt --recipient "nombre" mensaje.txt
   ```

4. **Descifra el mensaje con la clave privada:**
   ```bash
   gpg --decrypt mensaje.txt.gpg > mensaje_descifrado.txt
   ```

**Explicación Detallada:**
- Se comienza generando un par de claves (pública y privada) utilizando GPG. Estas claves se usan para cifrar y descifrar mensajes de forma segura.
- La clave pública se exporta y guarda en un archivo para compartirla con otros.
- El mensaje se cifra utilizando la clave pública del destinatario, generando un archivo cifrado que solo puede ser descifrado con la clave privada correspondiente.
- Finalmente, se descifra el mensaje cifrado usando la clave privada, asegurando que solo el destinatario legítimo pueda leerlo.

## 4. Ejercicio 3: Hashing y Cracking de Contraseñas con `hashcat`

**Descripción:**
En este ejercicio aprenderás sobre funciones hash y cómo utilizar `hashcat` para intentar romper contraseñas.

**Pasos:**
1. **Genera un hash SHA-256 de una contraseña:**
   ```bash
   echo -n "contrasena123" | sha256sum
   ```

2. **Utiliza `hashcat` para romper el hash:**
   - Crea un archivo llamado `hash.txt` con el hash generado.
   - Ejecuta `hashcat`:
     ```bash
     hashcat -m 1400 hash.txt /usr/share/wordlists/rockyou.txt
     ```

**Explicación Detallada:**
- En el primer paso, una contraseña se convierte en un hash SHA-256, un valor único que representa la contraseña pero no revela su contenido.
- El archivo `hash.txt` contiene el hash generado, que se usará para los intentos de crackeo.
- `hashcat` aplica un ataque de diccionario utilizando una lista de contraseñas comunes (`rockyou.txt`) para intentar encontrar la contraseña original que generó el hash.
- Este ejercicio demuestra la importancia de utilizar contraseñas seguras y complejas para proteger los datos.

## 5. Ejercicio 4: Firma Digital y Verificación con GPG

**Descripción:**
Demostrar la creación de una firma digital y su verificación, simulando la autenticidad e integridad de los mensajes.

**Pasos:**
1. **Firma un archivo:**
   ```bash
   gpg --output mensaje.txt.sig --detach-sign mensaje.txt
   ```

2. **Verifica la firma:**
   ```bash
   gpg --verify mensaje.txt.sig mensaje.txt
   ```

**Explicación Detallada:**
- La firma digital garantiza que el archivo no ha sido modificado y que proviene del autor legítimo.
- Se firma el archivo generando un archivo `.sig` que contiene la firma digital.
- La verificación de la firma asegura que el contenido del archivo no ha sido alterado y que la firma es válida, asegurando autenticidad e integridad.

> ## To be continued...
![To be continued...](https://s1.significados.com/foto/hacker-og.jpg)