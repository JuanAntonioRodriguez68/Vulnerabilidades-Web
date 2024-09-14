# **Cross-Site Request Forgery (CSRF)**

**Descripción:**  
CSRF es una vulnerabilidad que permite a los atacantes realizar acciones no autorizadas en nombre de un usuario autenticado sin su consentimiento. Esto ocurre cuando una aplicación web realiza una solicitud en nombre del usuario sin verificar que la solicitud es legítima.

**Ejemplo de Explotación:**

- **Escenario:**  
  Un usuario autenticado en `http://example.com` recibe un correo electrónico con un enlace malicioso.

- **Explotación:**

  `http://example.com/transfer?amount=1000&to=attacker`

  En este caso, al visitar la página que contiene el enlace, el navegador hace una solicitud al servidor para realizar una transferencia de dinero sin que el usuario lo sepa.

---

## **Herramientas para Explotar CSRF**

- **CSRF-Tester:**  
  Herramienta para probar la presencia de vulnerabilidades CSRF en aplicaciones web.

- **OWASP ZAP:**  
  Herramienta de escaneo de seguridad que incluye pruebas para CSRF y otras vulnerabilidades web.

- **Burp Suite:**  
  Usa el módulo **Intruder** para automatizar la explotación de CSRF en solicitudes HTTP.

  - **Comando de ejemplo:**

    ```bash
    burpsuite -I -p "http://example.com/transfer?amount=1000&to=attacker"
    ```

- **CSRF-POC-Generator:**  
  Genera pruebas de concepto para vulnerabilidades CSRF.

---

## **Mitigación de CSRF**

- **Tokens CSRF:**  
  Implementa tokens únicos en los formularios y verifica su validez en el servidor. Los tokens deben ser únicos por sesión y no predecibles.

- **Verificación de Origen:**  
  Usa encabezados `Referer` y `Origin` para validar que las solicitudes provienen de fuentes esperadas.

- **SameSite Cookies:**  
  Configura las cookies con la opción `SameSite` para restringir el envío de cookies a solicitudes del mismo origen.

- **Autenticación Multifactor:**  
  Añade capas adicionales de seguridad, como la autenticación multifactor, para asegurar que las solicitudes sean legítimas.

