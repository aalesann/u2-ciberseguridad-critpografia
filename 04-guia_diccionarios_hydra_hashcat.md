
# Guía Completa de Uso de Diccionarios con Hydra y Hashcat

## Introducción
El uso de diccionarios es fundamental en ataques de fuerza bruta para descifrar contraseñas cifradas o acceder a servicios protegidos. Herramientas como **Hydra** y **Hashcat** son ampliamente utilizadas para este propósito, permitiendo realizar ataques eficaces utilizando diccionarios personalizados.

## Creación de Diccionarios

### 1. **Uso de Crunch**
`Crunch` es una herramienta versátil para crear diccionarios personalizados a partir de patrones específicos.

**Instalación en Kali Linux:**
```bash
sudo apt install crunch
```

**Ejemplos de Uso de Crunch:**
- **Generar combinaciones con espacios:**
  ```bash
  crunch 1 3 "patr n" > diccio4.txt
  ```
- **Generar combinaciones con patrones de letras y números:**
  ```bash
  crunch 6 6 -t mesa%%
  ```
  - `-t mesa%%` genera combinaciones donde los últimos dos caracteres son números.
- **Generar combinaciones con minúsculas, números y caracteres especiales:**
  ```bash
  crunch 8 8 -t @@@%%%!!
  ```

### 2. **Uso de CeWL**
`CeWL` permite crear listas de palabras basadas en el contenido de sitios web, útil para generar diccionarios específicos de un objetivo.

**Instalación en Kali Linux:**
```bash
sudo apt install cewl
```

**Ejemplo de Uso:**
```bash
cewl https://ejemplo.com -w diccionario.txt
```
Este comando genera un diccionario con las palabras encontradas en la página web.

### 3. **Filtrar y Combinar Diccionarios con Herramientas de Línea de Comandos**
Puedes combinar y filtrar diccionarios con comandos como `cat`, `sort`, y `uniq` para eliminar duplicados y optimizar los diccionarios.

**Ejemplo:**
```bash
cat dic1.txt dic2.txt | sort | uniq > diccionario_final.txt
```

## Uso de Diccionarios con Hydra

### **Hydra**
Hydra es una herramienta para realizar ataques de fuerza bruta a servicios de autenticación como SSH, FTP, HTTP, entre otros.

**Instalación en Kali Linux:**
```bash
sudo apt install hydra
```

### **Ejemplo de Uso de Hydra con Diccionarios:**
1. **Ataque a un Servicio SSH:**
   ```bash
   hydra -l admin -P diccionario.txt 192.168.1.1 ssh
   ```
   - `-l admin`: Define el nombre de usuario (en este caso, "admin").
   - `-P diccionario.txt`: Define el archivo de diccionario con las posibles contraseñas.
   - `192.168.1.1 ssh`: Define el objetivo y el protocolo (SSH).

2. **Ataque a un Servicio HTTP POST Form:**
   ```bash
   hydra -l usuario -P diccionario.txt 192.168.1.1 http-post-form "/login.php:username=^USER^&password=^PASS^:F=incorrecto"
   ```
   - Este comando prueba combinaciones de usuario y contraseña en una página de inicio de sesión HTTP.

### **Consejos para Usar Hydra:**
- **Asegúrate de conocer bien el servicio:** Conocer el formato correcto de las solicitudes puede hacer tu ataque más efectivo.
- **Optimiza los diccionarios:** Un diccionario más específico y reducido suele ser más eficiente que uno genérico y extenso.

## Uso de Diccionarios con Hashcat

### **Hashcat**
Hashcat es una herramienta potente para crackear hashes de contraseñas utilizando varios modos de ataque, incluyendo diccionarios.

**Instalación en Kali Linux:**
```bash
sudo apt install hashcat
```

### **Formatos de Hash Compatibles:**
Hashcat soporta una amplia variedad de formatos de hash, incluyendo:
- MD5 (`-m 0`)
- SHA1 (`-m 100`)
- bcrypt (`-m 3200`)

### **Ejemplos de Uso de Hashcat:**

1. **Ataque de Diccionario a Hash MD5:**
   ```bash
   hashcat -m 0 -a 0 hash.txt diccionario.txt
   ```
   - `-m 0`: Define el tipo de hash (MD5 en este caso).
   - `-a 0`: Define el modo de ataque (diccionario).
   - `hash.txt`: Archivo que contiene el hash a crackear.
   - `diccionario.txt`: Diccionario con posibles contraseñas.

2. **Ataque de Diccionario a Hash SHA1:**
   ```bash
   hashcat -m 100 -a 0 hash.txt diccionario.txt
   ```

3. **Ataque de Diccionario Combinado (Diccionario + Reglas):**
   ```bash
   hashcat -m 0 -a 0 -r rules/best64.rule hash.txt diccionario.txt
   ```
   - `-r rules/best64.rule`: Aplica una regla para modificar cada entrada del diccionario, ampliando las combinaciones probadas.

### **Permutación con Hashcat:**
1. **Indicador de cantidad de parámetros:**
   ```bash
   hashcat -m 0 -a 3 hash.txt ?a?a?a?a?a?a?a?a -o resultado.txt
   ```
   - `-a 3`: Define un ataque de permutación o máscara.
   - `?a`: Representa cualquier carácter (letras, números, y símbolos).
   - `-o resultado.txt`: Guarda los resultados en `resultado.txt`.

2. **Permutación con 5 letras y 3 números:**
   ```bash
   hashcat -m 0 -a 3 hash.txt ?l?l?l?l?l?d?d?d -o resultado.txt
   ```
   - `?l`: Representa una letra minúscula.
   - `?d`: Representa un número.

### **Consejos para Usar Hashcat:**
- **Optimiza el uso de la GPU:** Hashcat está diseñado para aprovechar al máximo la potencia de las GPUs, haciendo el cracking mucho más rápido.
- **Utiliza Reglas:** Las reglas permiten modificar las palabras del diccionario en tiempo real, aumentando las combinaciones probadas sin necesidad de expandir el diccionario físicamente.
- **Mantén el software actualizado:** Las actualizaciones de Hashcat frecuentemente mejoran la velocidad y añaden soporte para nuevos tipos de hash.

## Consideraciones Éticas y Legales
- **Uso Responsable:** Estas técnicas deben ser empleadas únicamente para fines legales, como pruebas de seguridad autorizadas y tareas de auditoría.
- **Autorización Previa:** Asegúrate de tener permiso explícito para realizar cualquier tipo de prueba de penetración o cracking en sistemas que no son de tu propiedad.

## Conclusión
El uso de diccionarios personalizados junto con herramientas como Hydra y Hashcat permite realizar ataques de fuerza bruta de manera más eficiente y dirigida. Comprender cómo generar y aplicar estos diccionarios es clave para tareas de pentesting y auditoría de seguridad.

**Disclaimer:** Esta guía está destinada únicamente para fines educativos y debe utilizarse de acuerdo con las leyes vigentes y de manera ética.
