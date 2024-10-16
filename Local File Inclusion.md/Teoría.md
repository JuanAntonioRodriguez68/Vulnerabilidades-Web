Local File Inclusion (LFI)

Descripción:
LFI es una vulnerabilidad que permite a los atacantes incluir archivos locales del servidor manipulando parámetros en la URL. Generalmente ocurre en aplicaciones web que permiten la inclusión de archivos sin una validación adecuada.

Ejemplo de Explotación:

    URL vulnerable:

    http://example.com/index.php?page=about.php

    Explotación:

    http://example.com/index.php?page=../../../../etc/passwd

    Este ejemplo intenta acceder al archivo /etc/passwd en sistemas Linux, utilizando secuencias ../ para navegar por los directorios.

Herramientas para Explotar LFI

    Burp Suite:
    Intercepta y manipula las peticiones HTTP. Usa Intruder para automatizar la búsqueda de archivos vulnerables.

    wfuzz:
    Utiliza fuzzing para probar múltiples rutas de archivo.

        Comando de ejemplo:

        wfuzz -c -z file,/path/to/wordlist.txt --hc 404 http://example.com/index.php?page=FUZZ

    Metasploit:
    Framework que incluye módulos para la explotación de LFI.

    LFI Suite:
    Herramienta especializada en detectar y explotar LFI.

Mitigación de LFI

    Validar entrada: Asegura que solo se puedan cargar archivos desde directorios permitidos.
    Deshabilitar funciones peligrosas: En PHP, desactiva allow_url_include y allow_url_fopen.
    Escapar caracteres: Filtra secuencias como ../ para prevenir acceso no autorizado a archivos del sistema.
