# Playbook: Offboarding de usuario

> **Estado: COMPLETO (v1.0)**. Guía operativa estándar para el equipo de IT.

## Cuándo se ejecuta

Cuando People Ops notifica formalmente el retiro de una persona (vía ticket o correo), con fecha efectiva clara.

---

## Procedimiento Operativo

### Fase 1: Preparación (Al recibir la notificación)
1.  **Validar Solicitud:** Confirmar nombre, correo, área y fecha efectiva del retiro.
2.  **Verificación de Datos:** 
    *   Verificar que la persona exista en `data/usuarios.csv` y esté en estado `activo`. 
    *   Si hay discrepancias (ej. el usuario figura como `activo` pero la notificación dice que es retiro inminente), **detener proceso** y solicitar a People Ops la actualización del sistema fuente.
3.  **Inventario de Accesos:** Revisar en `data/licencias.csv` qué licencias tiene asignadas.

### Fase 2: Ejecución (El día del retiro)
1.  **Transferencia de archivos (Drive):**
    *   Identificar archivos críticos en Drive según el rol del usuario.
    *   Transferir la propiedad de las carpetas al líder del área del solicitante o a la cuenta de equipo correspondiente.
    *   Documentar el nombre de la carpeta y quién es el nuevo propietario.
2.  **Gestión de Licencias de Terceros:**
    *   **Salesforce / GitHub / Figma:** Iniciar sesión en la consola administrativa de cada herramienta.
    *   **Acción:** Cancelar la suscripción del usuario.
    *   **Prioridad:** Salesforce y Figma (alto costo) primero.
3.  **Suspensión de Google Workspace:**
    *   Suspender la cuenta principal de Google Workspace para bloquear el acceso a todos los servicios corporativos.

### Fase 3: Post-ejecución y Registro
1.  **Actualización de Registros:**
    *   Actualizar `data/usuarios.csv`: Cambiar estado a `retirado` y registrar la `fecha_retiro`.
    *   Actualizar `data/licencias.csv`: Cambiar estado a `suspendida` o eliminar registro según corresponda.
2.  **Generación de Evidencias:**
    *   Crear archivo en `evidencia/offboarding-{correo}-{fecha}.md` con:
        *   Lista de licencias canceladas.
        *   Soporte de transferencia de archivos (captura o log).
        *   Fecha/hora de suspensión de cuenta.

---

## Verificación final
*   [ ] ¿La cuenta de Google está suspendida?
*   [ ] ¿Se han cancelado las licencias de terceros?
*   [ ] ¿Se transfirieron los archivos de Drive?
*   [ ] ¿Se actualizaron los archivos CSV?
*   [ ] ¿Se generó la evidencia?

---

## Procedimiento Reusable para Agente de AI (Prompt)

Puedes usar este prompt para ejecutar el proceso con un agente (asegúrate de que tenga los permisos y acceso a los archivos):

> "Actúa como IT de Alegra. Ejecuta el Playbook de Offboarding para el usuario {CORREO} con fecha efectiva {FECHA}. 
> 1. Primero verifica su existencia y estado en data/usuarios.csv. 
> 2. Si es 'activo', procede a identificar sus licencias en data/licencias.csv. 
> 3. Documenta cada paso de la Fase 2 y 3. 
> 4. Al finalizar, genera un reporte en evidencia/offboarding-{CORREO}-{FECHA}.md siguiendo el formato de evidencias del equipo."

---

## Caso de prueba (Basado en TICKET-005)

*   **Usuario:** María Fernanda López (`maria.lopez@alegra.com`)
*   **Situación:** Notificación de retiro para el 2026-07-31.
*   **Acción requerida previa:** Validar estado laboral (`activo` vs notificación) y solicitar a People Ops la actualización de `data/usuarios.csv` para reflejar la fecha correcta.
*   **Acción posterior:** Una vez corregido el CSV, ejecutar este playbook.

---

## Notas
- Ojo: hemos tenido casos de cuentas de retirados que quedan activas por semanas. Este playbook existe justamente para que eso no vuelva a pasar.
