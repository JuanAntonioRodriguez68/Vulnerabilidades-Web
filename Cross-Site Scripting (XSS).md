# **Cross-Site Scripting (XSS)**

**Descripción:**  
Cross-Site Scripting (XSS) es una vulnerabilidad que permite a los atacantes inyectar scripts maliciosos en páginas web vistas por otros usuarios. Esto puede resultar en el robo de datos, manipulación de contenido y otras acciones no autorizadas.

**Tipos de XSS:**

1. **XSS Reflejado**  
   El script malicioso es parte de la URL o de una solicitud, y se refleja en la respuesta del servidor sin ser almacenado.

   - **Ejemplo:** `http://example.com/search?q=<script>alert('XSS')</script>`

2. **XSS Almacenado**  
   El script malicioso se almacena en el servidor (por ejemplo, en una base de datos) y se ejecuta cada vez que un usuario accede a la página afectada.

   - **Ejemplo:** Un comentario en un blog que contiene `<script>alert('XSS')</script>` y se muestra a otros usuarios.

3. **XSS Basado en DOM**  
   La vulnerabilidad se produce cuando el script malicioso modifica el Document Object Model (DOM) del navegador, generalmente a través de manipulaciones en el lado del cliente.

   - **Ejemplo:** Un enlace que cambia el contenido del DOM al hacer clic, inyectando un script malicioso.

---

## **Herramientas para Explotar XSS**

- **Burp Suite:**  
  Intercepta y manipula las peticiones HTTP. Usa **Intruder** y **Scanner** para identificar y explotar vulnerabilidades XSS.

- **OWASP ZAP:**  
  Herramienta de escaneo de seguridad que incluye pruebas para XSS y otras vulnerabilidades web.

- **XSStrike:**  
  Herramienta especializada en la detección y explotación de XSS.

  - **Comando de ejemplo:**

    ```bash
    xsstrike -u "http://example.com/search?q=" --crawl
    ```

- **XSSer:**  
  Herramienta automática para la detección y explotación de XSS.

---

## **Mitigación de XSS**

- **Escapar entrada:** Asegúrate de escapar adecuadamente cualquier entrada del usuario que se incluya en el HTML o JavaScript para evitar la ejecución de scripts maliciosos.

- **Validar entrada:** Implementa una validación estricta de los datos de entrada para asegurar que solo se permitan valores válidos.

- **Content Security Policy (CSP):** Usa CSP para restringir los recursos que pueden ser cargados y ejecutados en una página web.

- **HTTPOnly y Secure Cookies:** Marca las cookies como `HTTPOnly` y `Secure` para prevenir que los scripts maliciosos puedan acceder a ellas.


