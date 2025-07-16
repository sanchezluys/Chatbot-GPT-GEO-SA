# ✅ ACTA DE VALIDACIÓN Y ENTREGA DE CHATBOT: GEO SA (Versión 1.0)

## 🧾 Datos del Proyecto

- **Nombre del proyecto**: Implementación de Asistente Virtual para GEO SA
- **Cliente**: GEO SA
- **Fecha de entrega**: {{dd/mm/aaaa}}
- **Versión del bot entregado**: v1.0 / [Mes-Año de Entrega]
- **Modelo GPT**: 4o
- **Temperatura**: 0.1
- **Desarrollado por**: Asisteclick / L. Sánchez
- **Revisión y Aprobación**: GEO SA / [Nombre del Responsable]
- **Canales habilitados**: ✅ Asignado, ❌ Sin asignar, ⚠️ Pendiente por definir
  - ✅ Web
  - ❌ Email
  - ✅ Facebook Messenger
  - ✅ Instagram
  - ✅ Whatsapp
  - ⚠️ Telegram

## 🧪 Validación de Funcionalidades (UAT - User Acceptance Testing)

Se procede a la validación de las funcionalidades críticas del chatbot, según lo definido en el documento de requerimientos **GEO SA Rev 1.2**.

### 🔁 Leyenda de Estados

| Emoji | Estado      | Descripción                                                               |
| ----- | ----------- | ------------------------------------------------------------------------- |
| ✅     | Correcto    | La funcionalidad cumple completamente lo esperado.                        |
| ⚠️     | Parcial     | La funcionalidad opera parcialmente o con errores menores.                |
| ❌     | Falla       | La funcionalidad no cumple lo esperado o presenta errores críticos.       |
| 🔕     | Desactivada | El cliente decidió desactivar esta funcionalidad en esta versión del bot. |

---

### 📋 Resultados de Validación

| N°  | Funcionalidad                                        | Resultado Esperado                                                                                                   | Resultado Obtenido | Validado por el cliente |
| --- | ---------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------- |
| 1   | **Identificación y Bienvenida**                      | El bot responde al primer mensaje con un saludo profesional, presentándose como asistente virtual de GEO SA.         |                    |                         |
| 2   | **Validación de Cliente por DNI/CUIT**               | El bot solicita el DNI/CUIT, lo valida contra la API de ISP Brain y confirma la identidad del cliente.               |                    |                         |
| 3   | **Validación de Cliente por Teléfono**               | El bot solicita el teléfono, lo valida contra la API de ISP Brain y confirma la identidad del cliente.               |                    |                         |
| 4   | **Consulta de Cuenta Post-Validación**               | Tras validarse, el bot informa proactivamente el saldo pendiente y el plan actual, y ofrece opciones de gestión.     |                    |                         |
| 5   | **Notificación de Mantenimiento (Etiqueta INFOBOT)** | Si la API de ISP Brain informa un mantenimiento, el bot muestra el mensaje de alerta y finaliza la interacción.      |                    |                         |
| 6   | **Actualización de Datos de Contacto**               | Un cliente validado puede actualizar su email, teléfono o WhatsApp a través de la API.                               |                    |                         |
| 7   | **Consulta de Cobertura (No Cliente)**               | El bot solicita la dirección, informa que un agente de `Ventas` confirmará la disponibilidad y deriva la consulta.   |                    |                         |
| 8   | **Derivación a Soporte Técnico (Sin Servicio)**      | Al reportar "no tengo internet", el bot etiqueta, genera un ticket (ID 1) y deriva a `Soporte técnico`.              |                    |                         |
| 9   | **Derivación a Administración (Cambio de Plan)**     | Al solicitar un cambio de plan, el bot informa que un asesor debe gestionarlo y deriva a `Administración`.           |                    |                         |
| 10  | **Gestión de Horario No Laboral**                    | Al derivar una consulta fuera de horario, el bot informa la situación y deja la conversación abierta.                |                    |                         |
| 11  | **Gestión de Días Feriados**                         | Al derivar en un día feriado (según KB), el bot informa de posibles demoras en la respuesta.                         |                    |                         |
| 12  | **Fallback (Consulta no reconocida)**                | Ante una pregunta fuera de dominio, el bot responde con el mensaje de fallback definido y deriva a `Administración`. |                    |                         |

> *Los ítems marcados con ⚠️ o ❌ deben ser corregidos o mejorados en una versión posterior o quedar registrados como requerimientos futuros.*

## 🧩 Requerimientos Fuera de Alcance / Cambios Solicitados

A continuación, se enumeran solicitudes que **no forman parte del alcance de esta versión**, pero quedan registradas para evaluación futura:

### 🔁 Leyenda de Estados

| Emoji | Estado                              | Descripción                                                          |
| ----- | ----------------------------------- | -------------------------------------------------------------------- |
| ⚠️     | **Pendiente**                       | El cambio fue recibido pero aún no ha sido evaluado.                 |
| ⏳     | **En análisis**                     | Se está revisando su viabilidad técnica o funcional.                 |
| 🚫     | **No viable**                       | No es posible implementarlo por restricciones técnicas o de negocio. |
| 🔲     | **No priorizado**                   | Se documenta pero no se desarrollará por ahora.                      |
| 🟢     | **Aprobado para cotización futura** | Se acordó evaluar esfuerzo y costo para una próxima versión.         |

| N°  | Descripción del requerimiento                                   | Solicitado por | Fecha          | Estado          | Observaciones                                                                                                                                                                                             |
| --- | --------------------------------------------------------------- | -------------- | -------------- | --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | Verificación automática de cobertura geográfica en tiempo real. | GEO SA         | {{dd/mm/aaaa}} | 🚫 **No viable** | Requiere un desarrollo de microservicio dedicado y resultaría en altos costos de tokens y complejidad, superando el alcance de esta versión (según se definió en el documento de requerimientos Rev 1.2). |
| 2   |                                                                 |                |                |                 |                                                                                                                                                                                                           |