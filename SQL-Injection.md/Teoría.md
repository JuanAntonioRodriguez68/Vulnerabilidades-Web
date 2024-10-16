SQL Injection (SQLi)

Descripción:
SQL Injection (SQLi) es una vulnerabilidad que permite a los atacantes ejecutar comandos SQL maliciosos en la base de datos de una aplicación web. Esto ocurre cuando una aplicación no valida o escapa adecuadamente las entradas del usuario, permitiendo la inyección de código SQL.

Ejemplo de Explotación:

    URL vulnerable:

    http://example.com/index.php?id=1

    Explotación:

    http://example.com/index.php?id=1' OR '1'='1

    Este ejemplo utiliza una inyección de SQL para modificar la consulta y obtener acceso no autorizado o filtrar datos.

Tipos de SQL Injection:

    Inyección Basada en Error
    Los atacantes inducen errores en la base de datos para obtener información sobre la estructura de la base de datos.
        Ejemplo: http://example.com/index.php?id=1' AND 1=CONVERT(int, (SELECT @@version))--

    Inyección Ciega
    Cuando la aplicación no muestra mensajes de error, los atacantes infieren la estructura de la base de datos mediante la observación de las respuestas de la aplicación.
        Ejemplo: http://example.com/index.php?id=1' AND IF(1=1, SLEEP(5), 0)--

    Inyección SQL Basada en Tiempo
    Utiliza funciones que hacen que la base de datos se demore intencionalmente para inferir la existencia de datos.
        Ejemplo: http://example.com/index.php?id=1' AND IF(1=1, SLEEP(5), 0)--

    Inyección SQL Unitaria
    Añade o modifica una consulta SQL existente usando una sola línea de inyección.
        Ejemplo: http://example.com/index.php?id=1' UNION SELECT null, username, password FROM users--

    Inyección SQL de Unión
    Utiliza la cláusula UNION para combinar resultados de múltiples consultas SQL.
        Ejemplo: http://example.com/index.php?id=1' UNION SELECT null, username, password FROM users--

    Inyección SQL de Inferencia
    También conocida como Blind SQL Injection, se basa en la respuesta del sistema para inferir información sobre la base de datos.

Herramientas para Explotar SQL Injection

    Burp Suite:
    Intercepta y manipula las peticiones HTTP. Usa Intruder y Scanner para identificar y explotar vulnerabilidades SQLi.

    sqlmap:
    Automatiza la detección y explotación de SQL Injection. Proporciona una variedad de opciones para la explotación.

        Comando de ejemplo:

        sqlmap -u "http://example.com/index.php?id=1" --dbs

    Metasploit:
    Framework que incluye módulos específicos para explotar SQL Injection.

Mitigación de SQL Injection

    Preparar declaraciones: Usa declaraciones preparadas y consultas parametrizadas para evitar la inyección de código SQL.

    Validar y escapar entrada: Asegúrate de validar y escapar adecuadamente las entradas del usuario para evitar la ejecución de comandos SQL maliciosos.

    Utilizar ORM: Considera el uso de un Object-Relational Mapping (ORM) para abstraer las consultas SQL y reducir el riesgo de inyección.

    Limitar privilegios: Configura los permisos de la base de datos de manera que el usuario de la aplicación tenga los menores privilegios necesarios para operar.

