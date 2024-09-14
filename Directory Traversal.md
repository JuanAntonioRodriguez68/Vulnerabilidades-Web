# **Directory Traversal**

**Descripción:**  
Directory Traversal es una vulnerabilidad que permite a los atacantes acceder a archivos y directorios fuera del directorio raíz de la aplicación web. Esto se logra manipulando parámetros en la URL o en las solicitudes para navegar por la estructura de directorios del servidor.

**Ejemplo de Explotación:**

- **URL vulnerable:**

  `http://example.com/index.php?page=about`

- **Explotación:**

  `http://example.com/index.php?page=../../../../etc/passwd`

  Este ejemplo intenta acceder al archivo `/etc/passwd` en sistemas Linux, utilizando secuencias `../` para navegar por los directorios.

---

## **Herramientas para Explotar Directory Traversal**

- **Burp Suite:**  
  Intercepta y manipula las peticiones HTTP. Usa **Intruder** para automatizar la búsqueda de rutas de archivos vulnerables.

- **wfuzz:**  
  Utiliza fuzzing para probar múltiples rutas de archivo.

  - **Comando de ejemplo:**

    ```bash
    wfuzz -c -z file,/path/to/wordlist.txt -u http://example.com/index.php?page=FUZZ -t 50 --hc 404
    ```

- **DirBuster:**  
  Herramienta de fuerza bruta para encontrar directorios y archivos ocultos en aplicaciones web.

- **Dirsearch:**  
  Escanea rutas de directorios y archivos en una aplicación web.

---

## **Mitigación de Directory Traversal**

- **Validar entrada:**  
  Asegúrate de validar y sanear todas las entradas del usuario para evitar secuencias `../` y otras técnicas de traversal.

- **Restringir acceso a archivos:**  
  Configura permisos y restricciones para limitar el acceso a archivos y directorios sensibles.

- **Utilizar rutas absolutas:**  
  Usa rutas absolutas en lugar de rutas relativas para evitar la manipulación de directorios.

- **Escapar caracteres:**  
  Filtra y escapa caracteres especiales como `../` para prevenir la navegación no autorizada por el sistema de archivos.

