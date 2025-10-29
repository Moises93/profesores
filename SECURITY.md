```markdown
# SECURITY.md

La seguridad de {project_name} es de suma importancia. Este documento describe cómo reportar vulnerabilidades de seguridad de manera responsable, las prácticas de seguridad recomendadas para el proyecto, las vulnerabilidades conocidas y cómo mitigarlas, las características de seguridad del proyecto y sus limitaciones, y los recursos adicionales para aprender más sobre seguridad.

Este documento está diseñado para ayudar a usuarios y contribuidores a comprender las consideraciones de seguridad asociadas con {project_name}.

## Reportar Vulnerabilidades de Seguridad

Agradecemos sus esfuerzos para identificar y reportar vulnerabilidades de seguridad de manera responsable. Para proteger a nuestros usuarios, le pedimos que *no* divulgue públicamente vulnerabilidades antes de que hayamos tenido la oportunidad de abordarlas.

Por favor, reporte las vulnerabilidades de seguridad enviando un correo electrónico a: {contact_email}.

Al reportar una vulnerabilidad, incluya la siguiente información:

*   Una descripción detallada de la vulnerabilidad.
*   Pasos para reproducir la vulnerabilidad (si es posible).
*   La versión de {project_name} afectada.
*   Información sobre el impacto potencial de la vulnerabilidad.

Nos esforzaremos por responder a su informe en un plazo de 72 horas para confirmar la recepción y proporcionar una estimación del tiempo necesario para abordar la vulnerabilidad.  Trabajaremos con usted para entender el problema y desarrollar una solución.

**Proceso de Divulgación Responsable:**

Una vez que hayamos abordado la vulnerabilidad, trabajaremos con usted para coordinar una divulgación responsable. Esto puede incluir publicar un aviso de seguridad y acreditar su descubrimiento (si lo desea).  Normalmente, esperaremos un período de tiempo razonable (por ejemplo, 7 días) después de la publicación de la solución antes de divulgar públicamente la vulnerabilidad.

## Prácticas de Seguridad

Las siguientes son prácticas de seguridad recomendadas para el desarrollo y el uso de {project_name}.

### Gestión de Dependencias

Es crucial gestionar las dependencias del proyecto de forma segura para evitar la introducción de vulnerabilidades.

*   **Verificación de Dependencias:**  Utilice herramientas como `pip-audit` (para Python) o `npm audit` (para Node.js) para verificar si sus dependencias tienen vulnerabilidades conocidas.

    ```bash
    pip-audit # Python
    npm audit # Node.js
    ```

*   **Mantenimiento Actualizado:** Mantenga las dependencias actualizadas a las últimas versiones para corregir las vulnerabilidades conocidas.

    ```bash
    pip install --upgrade <paquete> # Python
    npm update <paquete> # Node.js
    ```

*   **Alertas de Vulnerabilidades:** Configure alertas de vulnerabilidades para recibir notificaciones cuando se descubran nuevas vulnerabilidades en sus dependencias.  GitHub y otras plataformas de alojamiento ofrecen esta funcionalidad.

### Manejo de Secretos

El manejo seguro de secretos es fundamental para proteger la información confidencial.

*   **Nunca Hardcodear Secretos:**  *Nunca* incluya secretos (claves API, contraseñas, etc.) directamente en el código.

*   **Variables de Entorno:** Utilice variables de entorno para almacenar secretos.

    ```python
    import os

    api_key = os.environ.get("API_KEY")
    ```

*   **.env en .gitignore:**  Si utiliza archivos `.env` para almacenar variables de entorno localmente, asegúrese de agregarlos a su archivo `.gitignore` para evitar que se suban al repositorio.

*   **Herramientas para Detectar Leaks:** Utilice herramientas como `git-secrets` para detectar secretos accidentalmente comprometidos en el historial de Git.

### Validación de Entrada

Validar la entrada del usuario es esencial para prevenir ataques de inyección y otros problemas de seguridad.

*   **Validar Entrada:**  Siempre valide y sanee la entrada del usuario antes de usarla en su código.

    **Ejemplo Inseguro (Python):**

    ```python
    import os

    nombre_archivo = input("Ingrese el nombre del archivo: ")
    os.system(f"cat {nombre_archivo}") # Vulnerable a inyección de comandos
    ```

    **Ejemplo Seguro (Python):**

    ```python
    import os
    import shlex

    nombre_archivo = input("Ingrese el nombre del archivo: ")
    nombre_archivo_seguro = shlex.quote(nombre_archivo)
    os.system(f"cat {nombre_archivo_seguro}") # Más seguro, pero evitar os.system siempre que sea posible
    ```

    **Mejor Opción (Python):**

    ```python
    with open("archivo.txt", "r") as f:
        contenido = f.read()
    print(contenido)
    ```

*   **Prevenir Inyección:**  Utilice técnicas de parametrización o escape para prevenir ataques de inyección SQL, inyección de comandos y otros tipos de inyección.

### Gestión de Acceso

Controle el acceso a los recursos para proteger la información confidencial.

*   **Principio de Mínimo Privilegio:** Otorgue a los usuarios y procesos solo los permisos necesarios para realizar sus tareas.

*   **SSH Keys vs HTTPS:**  Utilice claves SSH para la autenticación en lugar de contraseñas siempre que sea posible.  Asegúrese de utilizar HTTPS para todas las comunicaciones web.

*   **Permisos de Archivos:** Configure los permisos de archivos y directorios correctamente para evitar el acceso no autorizado.

## Seguridad en CI/CD

La seguridad debe integrarse en sus procesos de Integración Continua y Entrega Continua (CI/CD).

*   **Secrets en Jenkins/GitHub Actions:** Almacene los secretos utilizados en sus pipelines de CI/CD (claves API, contraseñas, etc.) de forma segura utilizando las funciones de gestión de secretos proporcionadas por su plataforma de CI/CD (por ejemplo, Credenciales de Jenkins, Secretos de GitHub Actions).

*   **Cómo Usar Credenciales:**  Acceda a los secretos almacenados en sus pipelines de CI/CD utilizando las variables de entorno o las funciones de interpolación proporcionadas por su plataforma.

    **Ejemplo (GitHub Actions):**

    ```yaml
    steps:
      - name: Usar API Key
        env:
          API_KEY: ${{ secrets.API_KEY }}
        run: |
          echo "La API Key es: $API_KEY"
    ```

*   **No Loguear Información Sensible:**  Evite loguear información sensible (secretos, contraseñas, etc.) en los registros de su pipeline de CI/CD.

## Testing de Seguridad

Realice pruebas de seguridad periódicas para identificar y corregir vulnerabilidades.

*   **Herramientas SAST:**  Utilice herramientas de análisis estático de código (SAST) como `bandit` (para Python) para identificar posibles vulnerabilidades en su código.

    ```bash
    bandit -r <directorio_del_proyecto>
    ```

*   **Herramientas de Análisis de Dependencias:**  Utilice herramientas como `safety` (para Python) y `pip-audit` (para Python) para identificar vulnerabilidades en sus dependencias.

    ```bash
    safety check # Python
    pip-audit # Python
    ```

*   **Qué Buscar:**  Busque vulnerabilidades comunes como inyección SQL, cross-site scripting (XSS), cross-site request forgery (CSRF), desbordamientos de búfer y errores de autenticación.

## Checklist de Seguridad para Contribuidores

Los contribuidores deben seguir estas pautas de seguridad al enviar código al proyecto.

*   **No Incluir Secretos:**  *Nunca* incluya secretos (claves API, contraseñas, etc.) en su código.
*   **No Usar `shell=True`:**  Evite usar `shell=True` en las llamadas a `subprocess.Popen` o `os.system` en Python, ya que puede conducir a vulnerabilidades de inyección de comandos.  Utilice `shlex.quote` para escapar los argumentos si es absolutamente necesario.
*   **Validar Inputs:**  Valide y sanee la entrada del usuario antes de usarla en su código.
*   **Sin Hardcoded Passwords:** No incluya contraseñas codificadas en el código.
*   **Revisar Cambios:**  Revise cuidadosamente sus cambios antes de enviarlos para detectar posibles vulnerabilidades de seguridad.

## Vulnerabilidades Conocidas

| Vulnerabilidad | CVE | Versiones Afectadas | Solución |
|---|---|---|---|
|  Ejemplo: Vulnerabilidad de inyección SQL en el módulo de autenticación  | CVE-2023-XXXX | 1.0.0 - 1.0.5 | Actualizar a la versión 1.0.6 o posterior. |
| Ejemplo: Vulnerabilidad de Cross-Site Scripting (XSS) en la interfaz de usuario  | CVE-2023-YYYY | 1.1.0 - 1.1.2 | Actualizar a la versión 1.1.3 o posterior. |

*Nota: Esta tabla se actualizará a medida que se descubran y se aborden nuevas vulnerabilidades.*

## Recursos de Seguridad

*   **OWASP Top 10:**  [https://owasp.org/top10/](https://owasp.org/top10/)
*   **Python Security Best Practices:** [https://wiki.python.org/moin/WebProgramming#Security](https://wiki.python.org/moin/WebProgramming#Security)
*   **CWE/SANS Top 25:** [https://cwe.mitre.org/top25/](https://cwe.mitre.org/top25/)

## Soporte

Si tiene alguna pregunta o inquietud sobre la seguridad de {project_name}, no dude en ponerse en contacto con nosotros.

*   **Reportar Vulnerabilidades:** Envíe un correo electrónico a {contact_email}.
*   **Contacto Directo:** Puede ponerse en contacto con el equipo de seguridad directamente a través de {contact_email}.
```