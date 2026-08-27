# Reto técnico — Tu primer día en IT de Alegra

¡Hola! Si estás leyendo esto es porque estás aplicando a la **práctica de IT
en Alegra**. Este es el reto técnico del proceso de selección: es individual,
estimamos **4–6 horas** de trabajo y la fecha de entrega viene en el correo
donde te lo compartimos.

No necesitas saber programar para resolverlo. Lo que sí necesitas —y es lo
que evaluamos— es **trabajar con un agente de AI**: configurarlo, delegarle
tareas, verificar lo que te dice y documentar lo que haces.

## El escenario

Hoy es tu primer día como practicante de IT en **Alegra** (dominio
`alegra.com`). Para el reto trabajas sobre una **versión simulada y reducida**
de la empresa (~20 personas). El equipo de IT administra usuarios, licencias
y accesos, y trabaja con agentes de AI en el día a día. Este repo es tu
"computador del primer día": tiene los datos de la empresa, tickets
pendientes y un playbook a medio escribir.

> **Fecha de corte de los datos: 2026-07-15.** Tómala como "hoy" dentro del
> escenario. Todos los datos son sintéticos: ninguna persona, correo o
> licencia es real. No escribas a ninguno de los correos que aparecen.

## Paso 0 — Consigue el reto y tu agente

1. **Descarga o clona este repo** y trabaja sobre esa copia local:

   ```bash
   git clone https://github.com/Alegra-Team/reto-it-alegra.git
   # o descarga el ZIP desde GitHub: Code → Download ZIP
   ```

2. **Instala un agente de AI de terminal.** La instalación hace parte del
   reto (si te atascas, apóyate en la documentación o en el propio chat de la
   herramienta). Opciones gratuitas — elige una:

   | Opción | Qué necesitas | Enlace |
   |--------|---------------|--------|
   | **Gemini CLI** | Cuenta de Google gratuita | https://github.com/google-gemini/gemini-cli |
   | **opencode + DeepSeek** | API key gratuita de DeepSeek | https://opencode.ai + https://platform.deepseek.com |

3. **Verifica que funciona**: abre el agente **dentro de la carpeta del
   reto** y pídele algo como *"lista los archivos de este repo y dime qué
   contiene cada carpeta"*. Si te responde con la estructura real, ya estás listo/a.

**Importante:** usar solo un chat web (copiar y pegar archivos a mano) **no
cumple el requisito**. El agente debe leer y modificar los archivos del repo
por sí mismo — de eso se trata el reto.

## Qué hay en este repo

```
├── README.md      # este archivo
├── data/          # datos de la empresa: usuarios, licencias y últimos logins (CSV)
├── tickets/       # 5 solicitudes pendientes que debes responder
├── playbooks/     # playbook de offboarding a medio escribir
└── evidencia/     # carpeta vacía: aquí dejas tus reportes y soportes
```

## Reglas de IT en Alegra

Estas son las reglas del equipo. Las vas a necesitar para todas las tareas
(y tu agente también debería conocerlas — pista para la Tarea 1):

1. **Ningún acceso de administrador** se otorga a practicantes ni personal temporal.
2. Toda cuenta de una persona **retirada se suspende el mismo día** de su retiro.
3. Los accesos a herramientas pagas requieren **aprobación del líder del área** del solicitante.
4. Licencias **sin uso por más de 60 días** se reportan para reasignación o cancelación.
5. Toda acción o hallazgo queda **documentado con evidencia** en la carpeta `evidencia/`.
6. Las solicitudes se responden **por escrito en el ticket**, con la decisión y su justificación.

## Las 3 tareas

### Tarea 1 — Configura tu agente (30%)

Escribe el **archivo de contexto** del agente para este workspace
(`GEMINI.md` si usas Gemini CLI, `AGENTS.md` si usas opencode) en la raíz de
la carpeta. Es el archivo que el agente lee al arrancar y que define cómo
trabaja. Debe lograr que se comporte como un miembro más del equipo de IT de
Alegra: quiénes somos, las reglas de arriba, la estructura del repo,
el formato de reportes y evidencia, y al menos **un procedimiento repetible**
que definas tú (por ejemplo: "cómo responder un ticket paso a paso").

**Este archivo (y cualquier otra configuración del agente) debe venir en el
repo que nos compartas**: evaluamos directamente cómo configuraste tu agente,
no solo los resultados.

**Plus:** si usas funcionalidades avanzadas de tu herramienta —subagentes,
comandos o skills personalizados, herramientas conectadas (MCP)— y se nota
que aportan al flujo (no de adorno), suma puntos extra.

*Qué evaluamos:* que entiendas que un agente rinde según cómo se configura.

### Tarea 2 — Auditoría de accesos y tickets (40%)

En `data/` están los usuarios, licencias y últimos logins de la empresa; en
`tickets/`, cinco solicitudes pendientes. Con ayuda de tu agente:

1. **Audita los accesos**: cruza los tres archivos y reporta todo lo que no
   cuadre — cuentas que deberían estar suspendidas, licencias desperdiciadas,
   accesos sin dueño, señales de riesgo… Los datos reflejan una operación
   real: **pueden tener errores e inconsistencias, y detectarlas es parte del
   trabajo**. Entrega el reporte en `evidencia/auditoria-accesos.md`.
2. **Responde los 5 tickets** por escrito: edita cada archivo agregando una
   sección `## Respuesta de IT` con la decisión (aprobado / rechazado /
   escalado) y su justificación según las reglas.

*Qué evaluamos:* delegación real al agente **y** criterio propio. El agente
te va a ayudar a cruzar datos, pero las trampas las tienes que confirmar tú.

### Tarea 3 — Termina el playbook de offboarding (30%)

`playbooks/offboarding.md` quedó a medio escribir. Complétalo para que
**cualquier otra persona (o agente) pueda ejecutarlo sin ayuda**: pasos
concretos, verificaciones y evidencia. Incluye al final un **prompt o
procedimiento reusable** para correrlo con un agente. Uno de los tickets te
va a servir como caso de prueba.

*Qué evaluamos:* documentación y pensamiento de proceso.

## Qué entregas y cómo

Devuélvenos tu copia del reto (link a un **repo privado** compartido con quien
te contactó, o un **zip** respondiendo al mismo correo) con:

- [ ] Tu archivo de contexto (`GEMINI.md` / `AGENTS.md`) **y toda la
      configuración de tu agente** (comandos, subagentes, settings…) — la
      configuración es parte de lo que se evalúa
- [ ] `evidencia/auditoria-accesos.md` — reporte de auditoría
- [ ] Los 5 tickets respondidos (sección `## Respuesta de IT` en cada uno)
- [ ] `playbooks/offboarding.md` completo
- [ ] `NOTAS.md` — máximo 1 página: qué agente usaste y cómo lo instalaste,
      qué le delegaste, qué te tocó corregirle y qué harías distinto con más tiempo

**No publiques tu solución en un repo público** — el reto lo usan otros
candidatos después de ti.

## Cómo te evaluamos

- Cada tarea pesa lo indicado arriba; el corte es **7/10**, con mínimos en
  uso del agente y criterio propio.
- Si pasas, la última etapa es una **entrevista en vivo de ~20 minutos**
  donde compartes pantalla y operas tu agente sobre el mismo repo. Por eso
  no sirve tercerizar el trabajo: lo que entregues lo vas a defender en vivo.

## Condiciones y tips

- Trabajo **individual**. Puedes usar internet y cualquier documentación.
- Ante cualquier duda de alcance, **toma una decisión razonable y
  documéntala** — eso también lo evaluamos.
- No le creas todo al agente: verifica sus conclusiones contra los datos.
  Los mejores candidatos son los que lo corrigen cuando se equivoca.

¡Éxitos! 🚀
