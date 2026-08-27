# Reporte de Auditoría de Accesos y Licencias — Alegra
**Fecha de ejecución (Simulada):** 2026-07-15
**Autor:** Agente de IT (Automatizado)

---

## 1. Resumen Ejecutivo
Se ha realizado una auditoría cruzada entre la base de datos de usuarios, el inventario de licencias y el historial de últimos logins. Se detectaron incumplimientos críticos de las políticas de seguridad (Regla 2), licencias con uso ineficiente (Regla 4), cuentas de usuarios no registrados y errores severos de integridad en los datos. Se requiere acción inmediata para mitigar riesgos de seguridad y optimizar costos.

---

## 2. Hallazgos Críticos (Políticas Incumplidas)

### 2.1. Usuario retirado con accesos activos
*   **Persona:** Jorge Ramírez (jorge.ramirez@alegra.com)
*   **Evidencia:** `usuarios.csv` lo marca como `retirado` desde `2026-05-30`. `licencias.csv` muestra licencias `activa` de Google Workspace y Salesforce. `logins.csv` muestra login en Salesforce el `2026-05-28` (anterior al retiro) y en Google Workspace el `2026-06-20` (posterior al retiro).
*   **Regla relacionada:** Regla 2 (Suspensión inmediata).
*   **Explicación:** Incumplimiento de seguridad. El usuario mantiene licencias activas y se ha detectado acceso posterior a la fecha oficial de retiro (Google Workspace, 2026-06-20).
*   **Acción recomendada:** Suspender inmediatamente todas las licencias y accesos de Jorge Ramírez.

### 2.2. Cuenta/licencia sin correspondencia en el registro de usuarios
*   **Cuenta:** dev.externo@alegra.com
*   **Evidencia:** `usuarios.csv` NO EXISTE. `licencias.csv` muestra licencia de GitHub `activa`. `logins.csv` muestra último acceso `2026-07-12`.
*   **Regla relacionada:** N/A (Gestión de identidades).
*   **Explicación:** Cuenta/licencia activa que no tiene una correspondencia en el registro centralizado de usuarios, lo que requiere validación de identidad y autorización formal.
*   **Acción recomendada:** Validar la identidad y la necesidad de esta cuenta/licencia para determinar si debe ser creada formalmente en `usuarios.csv` o si el acceso debe ser revocado.

---

## 3. Oportunidades de Optimización (Licencias inactivas > 60 días)

*   **Persona:** María Fernanda López (maria.lopez@alegra.com)
*   **Evidencia:** Último login en Figma: `2026-03-10`. Último login en Salesforce: `2026-02-28`. Ambas licencias figuran como `activa`.
*   **Regla relacionada:** Regla 4 (Optimización de licencias sin uso).
*   **Explicación:** Las licencias superan los 60 días de inactividad (127 y 137 días respectivamente).
*   **Acción recomendada:** Proceder a la reasignación o cancelación de estas licencias para reducir costos mensuales.

---

## 4. Inconsistencias de Datos

### 4.1. Posible duplicidad y desperdicio de licencias
*   **Usuario:** Juan Pérez (juan.perez@alegra.com y jperez@alegra.com)
*   **Evidencia:** Dos identidades registradas con licencias de Figma (`juan.perez` activa desde 2024, `jperez` activa con login reciente `2026-07-01`). Costo mensual total de las dos licencias: $30/mes.
*   **Explicación:** Los datos sugieren una posible duplicidad de identidad. El uso de la cuenta no registrada `jperez` implica un posible desperdicio de licencia, pero esta duplicidad debe validarse antes de tomar acciones sobre las cuentas.
*   **Acción recomendada:** Validar con el usuario y People Ops la necesidad de ambas cuentas, consolidar la identidad y, de confirmarse el desperdicio, cancelar la licencia redundante.

### 4.2. Inconsistencia de fechas de ingreso/retiro
*   **Usuario:** Pedro Salazar
*   **Evidencia:** `fecha_ingreso`: 2025-08-01, `fecha_retiro`: 2025-03-15.
*   **Explicación:** Error de integridad de datos; la fecha de retiro es anterior a la fecha de ingreso.
*   **Acción recomendada:** Corregir la base de datos `usuarios.csv` una vez validada la información histórica real con People Ops.

---

## 5. Criterio de Verificación
Los hallazgos expuestos han sido obtenidos mediante un proceso de contraste riguroso entre los tres archivos de datos:
1.  **`usuarios.csv`**: Validación de estado activo/retirado e integridad de registros.
2.  **`licencias.csv`**: Verificación de asignación de productos, costos y estados de licencia.
3.  **`logins.csv`**: Análisis de actividad real basado en la fecha de corte `2026-07-15`.
Toda conclusión (como la inferencia de desperdicio en el caso de Juan Pérez) está respaldada por la disparidad entre los registros de usuario, los registros de facturación de licencias y los registros de actividad técnica.
