# 🕵️‍♀️ POWERBYTE Ransomware Investigation

Caso práctico de análisis forense y recuperación de datos tras un posible incidente de **ransomware interno** en la empresa ficticia **POWERBYTE Déborah Loisel S.A.**, una tienda en línea de productos electrónicos.

## 🧩 Contexto

Tras el despido de un empleado, se sospecha que este ha comprimido archivos críticos de la empresa en un archivo `.rar` protegido con contraseña, exigiendo ser readmitido para devolver el acceso.

Has sido contratada para investigar y tratar de recuperar los archivos sin negociar con el atacante.

---

## 🛠️ Pasos realizados

### 1. Localización del archivo sospechoso
Se localizó un archivo `.rar` sospechoso en el escritorio del equipo afectado.

### 2. Creación de hash para análisis forense
Se generó un hash SHA-256 del archivo para asegurar su integridad durante el proceso:

```bash
sha256sum archivo.rar > archivo.hash
```

### 3. Descifrado de la contraseña con John the Ripper

Se utilizó la herramienta `John the Ripper` con el módulo `rar2john` para extraer el hash del archivo y lanzar un ataque por diccionario:

```bash
rar2john archivo.rar > archivo_john.hash
john archivo_john.hash --wordlist=/usr/share/wordlists/rockyou.txt
```

✅ Contraseña encontrada: `skull`

---

## 📂 Archivos encontrados

Una vez descomprimido el archivo, se hallaron los siguientes ficheros:

- **`secreto.txt`**
  ```
  INFORMACIÓN NO
  DISPONIBLE
  ```

- **`chantaje.doc`**
  ```
  PA-GA-ME
  ```

---

## 🖼️ Evidencias del proceso

Se adjuntan capturas del proceso en la carpeta `/evidencias/`:

- Localización del archivo
- Creación del hash
- Extracción con `rar2john`
- Ejecución de `john`
- Contenido de los archivos

---

## 📌 Conclusiones

Este ejercicio representa un incidente interno con intento de chantaje. La investigación permitió:

- Recuperar la contraseña sin negociar
- Obtener evidencia clave para tomar acciones legales

---

## 🧠 Conocimientos aplicados

- Análisis forense básico
- Hashing de archivos
- Cracking de contraseñas con John the Ripper
- Manejo de archivos comprimidos
- Documentación de evidencias

---

⚠️ **Este caso es ficticio y con fines formativos.**
