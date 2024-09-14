# **SQL Injection (SQLi)**

**Descripción:**  
SQL Injection (SQLi) es una vulnerabilidad que permite a los atacantes ejecutar comandos SQL maliciosos en la base de datos de una aplicación web. Esto ocurre cuando una aplicación no valida o escapa adecuadamente las entradas del usuario, permitiendo la inyección de código SQL.

**Ejemplo de Explotación:**

- **URL vulnerable:**

  `http://example.com/index.php?id=1`

- **Explotación:**

  `http://example.com/index.php?id=1' OR '1'='1`

  Este ejemplo utiliza una inyección de SQL para modificar la consulta y obtener acceso no autorizado o filtrar datos.

---

## **Herramientas para Explotar SQL Injection**

- **Burp Suite:**  
  Intercepta y manipula las peticiones HTTP. Usa **Intruder** y **Scanner** para identificar y explotar vulnerabilidades SQLi.

- **sqlmap:**  
  Automatiza la detección y explotación de SQL Injection. Proporciona una variedad de opciones para la explotación.

  - **Comando de ejemplo:**

    ```bash
    sqlmap -u "http://example.com/index.php?id=1" --dbs
    ```

- **Metasploit:**  
  Framework que incluye módulos específicos para explotar SQL Injection.

---

## **Mitigación de SQL Injection**

- **Preparar declaraciones:** Usa declaraciones preparadas y consultas parametrizadas para evitar la inyección de código SQL.

- **Validar y escapar entrada:** Asegúrate de validar y escapar adecuadamente las entradas del usuario para evitar la ejecución de comandos SQL maliciosos.

- **Utilizar ORM:** Considera el uso de un Object-Relational Mapping (ORM) para abstraer las consultas SQL y reducir el riesgo de inyección.

- **Limitar privilegios:** Configura los permisos de la base de datos de manera que el usuario de la aplicación tenga los menores privilegios necesarios para operar.


