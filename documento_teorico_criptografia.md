
# Introducción a la Criptografía

La criptografía es una disciplina de la ciberseguridad que se encarga de proteger la información a través de técnicas matemáticas, permitiendo que solo las personas autorizadas puedan acceder a ella. Se utiliza para asegurar la confidencialidad, integridad y autenticidad de los datos.

## Conceptos Básicos de Criptografía

1. **Cifrado y Descifrado:**
   - **Cifrado (Encryption):** Es el proceso de convertir información legible (texto plano) en un formato ilegible (texto cifrado) utilizando un algoritmo de cifrado y una clave. Esto asegura que la información no pueda ser entendida sin la clave adecuada.
   - **Descifrado (Decryption):** Es el proceso inverso al cifrado. Transforma el texto cifrado de vuelta a su formato original usando la clave correspondiente.

2. **Tipos de Criptografía:**
   - **Criptografía Simétrica:** Utiliza la misma clave para cifrar y descifrar la información. Ejemplo de algoritmos: AES, DES, 3DES. Es rápida y eficiente, pero presenta problemas en la distribución segura de claves.
   - **Criptografía Asimétrica:** Utiliza un par de claves: una pública (para cifrar) y una privada (para descifrar). Ejemplo de algoritmos: RSA, ECC. Es más segura para la transmisión de claves pero es más lenta que la simétrica.
   - **Criptografía de Hash:** Genera un valor fijo (hash) a partir de un conjunto de datos, utilizado principalmente para verificar la integridad de la información. Ejemplo de algoritmos: SHA-256, MD5.

3. **Funciones Criptográficas:**
   - **Confidencialidad:** Asegura que la información solo pueda ser leída por quienes tienen permiso.
   - **Integridad:** Garantiza que la información no ha sido alterada durante la transmisión.
   - **Autenticación:** Verifica la identidad de las partes que se comunican.
   - **No repudio:** Impide que una parte niegue haber enviado un mensaje.

## Algoritmos Criptográficos Comunes

1. **AES (Advanced Encryption Standard):**
   - Es un algoritmo de cifrado simétrico ampliamente utilizado y considerado seguro. Usa claves de 128, 192 o 256 bits y opera en bloques de 128 bits.

2. **RSA (Rivest–Shamir–Adleman):**
   - Algoritmo de cifrado asimétrico basado en la dificultad de factorizar números grandes. Es utilizado para cifrado y firma digital.

3. **SHA (Secure Hash Algorithm):**
   - Algoritmo de hashing diseñado para asegurar la integridad de los datos. SHA-256, una variante de SHA-2, es ampliamente utilizado en criptomonedas y sistemas de autenticación.

## Criptografía Simétrica vs Asimétrica

- **Simétrica:**
  - Clave única compartida.
  - Rápido y eficiente.
  - Dificultad en la gestión y distribución segura de claves.

- **Asimétrica:**
  - Par de claves (pública y privada).
  - Más seguro para el intercambio de claves.
  - Más lento y consume más recursos.

## Funciones Hash y su Aplicación en Seguridad

- Las funciones hash convierten datos de cualquier tamaño a una longitud fija de manera irreversible. Se utilizan en firmas digitales, contraseñas y verificación de integridad.
- **Ejemplo: SHA-256** convierte cualquier entrada en un hash de 256 bits. Cambiar un solo bit en la entrada cambia completamente el hash.

## Herramientas Comunes para la Criptografía en Kali Linux

1. **OpenSSL:**
   - Una herramienta robusta que implementa los protocolos SSL y TLS, usada para cifrado simétrico y asimétrico, generación de claves y certificados.

2. **GPG (GNU Privacy Guard):**
   - Proporciona cifrado y firma digital para asegurar los datos y comunicaciones.

3. **Hashcat:**
   - Un cracker de contraseñas avanzado que utiliza múltiples técnicas de ataque, útil para demostrar la importancia de usar contraseñas seguras.

4. **John the Ripper:**
   - Herramienta de cracking de contraseñas popular para probar la seguridad de hashes.

## Aplicaciones y Relevancia de la Criptografía

- **Protección de datos sensibles:** Cifrado de datos personales, financieros y médicos.
- **Seguridad de las comunicaciones:** Mensajería cifrada, correos seguros.
- **Integridad de la información:** Verificación de software mediante firmas digitales.
- **Autenticación:** Certificados digitales para verificar la identidad.

## Conceptos Clave para Comprender los Ejercicios Prácticos

1. **Algoritmo de Cifrado:** Procedimiento que toma un texto plano y lo convierte en texto cifrado.
2. **Clave Criptográfica:** Información que determina el resultado del cifrado y descifrado.
3. **Firma Digital:** Método para verificar la autenticidad e integridad de un mensaje.
4. **Hash:** Salida fija generada por una función hash, utilizada para verificar la integridad.
