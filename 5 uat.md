
# ✅ ACTA DE VALIDACIÓN Y ENTREGA: ASISTENTE VIRTUAL GEO SA (v1.0)

## 🧾 1. Datos del Proyecto

| Parámetro               | Valor                                           |
| :---------------------- | :---------------------------------------------- |
| **Nombre del Proyecto** | Implementación de Asistente Virtual para GEO SA |
| **Cliente**             | GEO SA                                          |
| **Fecha de Entrega**    | {{dd/mm/aaaa}}                                  |
| **Versión del Bot**     | v1.0 / [Mes-Año de Entrega]                     |
| **Modelo IA**           | OpenAI GPT-4o                                   |
| **Desarrollado por**    | Asisteclick / Luis Sánchez                      |
| **Revisado por**        | GEO SA / [Nombre del Responsable]               |

## 🎯 2. Objetivo del Documento

Este documento tiene como objetivo validar que las funcionalidades del Asistente Virtual (en adelante, "el bot") se ajustan a los requerimientos definidos en el documento **"Requerimientos del Bot – GEO SA Rev 1.2"**. La aprobación de este UAT (User Acceptance Testing) certifica la correcta implementación y entrega de la versión 1.0 del bot.

## 🔁 3. Leyenda de Estados para Pruebas

| Emoji | Estado          | Descripción                                                                         |
| :---- | :-------------- | :---------------------------------------------------------------------------------- |
| ✅     | **Correcto**    | La funcionalidad cumple 100% con lo esperado.                                       |
| ⚠️     | **Parcial**     | La funcionalidad opera, pero con errores menores que no impiden el flujo principal. |
| ❌     | **Falla**       | La funcionalidad no cumple lo esperado o presenta errores críticos.                 |
| 🔕     | **Desactivada** | Funcionalidad desactivada intencionalmente en esta versión.                         |

---

## 🧪 4. Casos de Prueba

### **Sección A: Interacción y Experiencia de Usuario**

| N°      | Funcionalidad                         | Pasos para Probar                                                            | Resultado Esperado                                                                                                                                | Resultado Obtenido | Validado |
| :------ | :------------------------------------ | :--------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------ | :----------------- | :------- |
| **A.1** | **Tono, Estilo y Bienvenida**         | 1. Iniciar una nueva conversación.                                           | El bot responde con un saludo profesional, se presenta como "GEO-Bot", utiliza emojis y negritas para resaltar información clave, y ofrece ayuda. |                    |          |
| **A.2** | **Fallback (Consulta no reconocida)** | 1. Preguntar algo fuera de dominio (ej: "¿Cuál es la capital de Mongolia?"). | El bot responde amablemente que no tiene información sobre ese tema y que derivará la consulta a un asesor. Asigna la etiqueta `otras_consultas`. |                    |          |
| **A.3** | **Pregunta de Cierre**                | 1. Completar un flujo exitoso (ej: consultar saldo).                         | Antes de finalizar, el bot pregunta "¿Hay algo más en lo que pueda ayudarte hoy, {{name}}? 😊".                                                    |                    |          |

### **Sección B: Flujos para No Clientes (Sin Autenticación)**

| N°      | Funcionalidad                      | Pasos para Probar                                          | Resultado Esperado                                                                                                                                                                 | Resultado Obtenido | Validado |
| :------ | :--------------------------------- | :--------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------- | :------- |
| **B.1** | **Consulta de Planes y Servicios** | 1. Preguntar "¿Qué planes de internet tienen?".            | El bot muestra las tablas de planes de Fibra y Antena (extraídas de la KB) y ofrece derivar la consulta a `Ventas`.                                                                |                    |          |
| **B.2** | **Consulta de Cobertura**          | 1. Preguntar "¿Tienen cobertura en [Dirección Ficticia]?". | 1. El bot solicita la dirección. 2. Muestra los mapas generales de la KB. 3. Aclara que un agente de `Ventas` debe confirmar. 4. Deriva la conversación a `Ventas`.                |                    |          |
| **B.3** | **Proceso de Contratación**        | 1. Expresar la intención de contratar.                     | 1. El bot explica las "Políticas del servicio" y requisitos de la KB. 2. Solicita datos (nombre, DNI, etc.). 3. Genera un ticket de instalación (ID 2 o 12). 4. Deriva a `Ventas`. |                    |          |

### **Sección C: Flujos para Clientes (Post-Autenticación)**

| N°      | Funcionalidad                          | Pasos para Probar                                                   | Resultado Esperado                                                                                                                                                          | Resultado Obtenido | Validado |
| :------ | :------------------------------------- | :------------------------------------------------------------------ | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------- | :------- |
| **C.1** | **Validación Exitosa (DNI)**           | 1. Proporcionar un DNI de cliente válido cuando el bot lo solicite. | El bot confirma la identidad exitosamente y lo comunica al usuario antes de continuar.                                                                                      |                    |          |
| **C.2** | **Validación Fallida (DNI)**           | 1. Proporcionar un DNI no registrado.                               | El bot informa amablemente que no pudo validar la identidad y no puede proceder con gestiones de cuenta.                                                                    |                    |          |
| **C.3** | **Consulta de Saldo y Plan**           | 1. Siendo un cliente validado, preguntar "¿Cuál es mi saldo?".      | El bot utiliza las herramientas `mi_plan` y `resumen_comprobantes` para mostrar la información correcta.                                                                    |                    |          |
| **C.4** | **Acceso al Portal de Clientes**       | 1. Siendo un cliente validado, pedir acceso al portal.              | El bot verifica si el cliente tiene factura A/B/C. Si es así, le da el link del portal. Si no, responde "Tus credenciales para el portal aún no se encuentran disponibles". |                    |          |
| **C.5** | **Actualización de Datos de Contacto** | 1. Siendo un cliente validado, solicitar "Quiero cambiar mi email". | El bot inicia el flujo correcto utilizando la herramienta `actualizar_datos_de_contacto` y pidiendo la nueva información.                                                   |                    |          |

### **Sección D: Lógica de Negocio y Derivaciones**

| N°      | Funcionalidad                            | Pasos para Probar                                                                                                           | Resultado Esperado                                                                                                                                                              | Resultado Obtenido | Validado |
| :------ | :--------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----------------- | :------- |
| **D.1** | **Gestión de Horario No Laboral**        | 1. Realizar una consulta que requiera derivación (ej: "cambiar mi plan") fuera del horario de atención (ej: a las 23:00hs). | El bot informa correctamente que está fuera del horario laboral, asegura que la consulta fue registrada y que será atendida en la siguiente jornada. No cierra la conversación. |                    |          |
| **D.2** | **Gestión de Días Feriados**             | 1. Realizar una consulta que requiera derivación durante un día feriado (según KB).                                         | El bot informa sobre el día feriado y la posible demora en la respuesta antes de proceder con la derivación.                                                                    |                    |          |
| **D.3** | **Derivación y Ticket: Soporte Técnico** | 1. Siendo cliente validado, reportar "No tengo internet".                                                                   | 1. El bot ofrece una guía visual de la KB. 2. Genera un ticket de "Soporte técnico" (ID 1). 3. Deriva la conversación al departamento de `Soporte técnico`.                     |                    |          |
| **D.4** | **Derivación y Ticket: Avería en Zona**  | 1. Siendo cliente validado, reportar "Hay un corte en el barrio".                                                           | 1. El bot genera un ticket de "Problema general" (ID 10). 2. Deriva la conversación inmediatamente a `Soporte técnico`.                                                         |                    |          |
| **D.5** | **Derivación: Administración**           | 1. Siendo cliente validado, solicitar "Quiero cambiar de titular".                                                          | El bot explica el proceso exacto que figura en la KB y deriva correctamente a `Administración`.                                                                                 |                    |          |

### **Sección E: Sistema de Etiquetado Inteligente**

| N°      | Funcionalidad                       | Pasos para Probar                                             | Resultado Esperado                                                                             | Resultado Obtenido | Validado |
| :------ | :---------------------------------- | :------------------------------------------------------------ | :--------------------------------------------------------------------------------------------- | :----------------- | :------- |
| **E.1** | **Etiquetado `sin_servicio`**       | 1. Iniciar conversación con "se cortó internet".              | La conversación es etiquetada automáticamente con `sin_servicio` en la plataforma Asisteclick. |                    |          |
| **E.2** | **Etiquetado `servicio_lento`**     | 1. Iniciar conversación con "mi conexión anda muy despacio".  | La conversación es etiquetada automáticamente con `servicio_lento`.                            |                    |          |
| **E.3** | **Etiquetado `solicitud_de_baja`**  | 1. Iniciar conversación con "quiero dar de baja el servicio". | La conversación es etiquetada automáticamente con `solicitud_de_baja`.                         |                    |          |
| **E.4** | **Etiquetado `contratar_servicio`** | 1. Iniciar conversación con "quiero saber los precios".       | La conversación es etiquetada automáticamente con `contratar_servicio`.                        |                    |          |

---

## 🧩 5. Requerimientos Fuera de Alcance y para Futuras Versiones

### **Leyenda de Estados para Requerimientos Futuros**

| Emoji | Estado                       | Descripción                                                          |
| :---- | :--------------------------- | :------------------------------------------------------------------- |
| ⚠️     | **Pendiente**                | El cambio fue recibido pero aún no ha sido evaluado.                 |
| ⏳     | **En análisis**              | Se está revisando su viabilidad técnica o funcional.                 |
| 🚫     | **No viable**                | No es posible implementarlo por restricciones técnicas o de negocio. |
| 🔲     | **No priorizado**            | Se documenta pero no se desarrollará por el momento.                 |
| 🟢     | **Aprobado para cotización** | Se acordó evaluar esfuerzo y costo para una próxima versión.         |

### **Listado de Requerimientos**

| N°   | Descripción del Requerimiento                                        | Solicitado por | Fecha          | Estado                         | Observaciones                                                                                          |
| :--- | :------------------------------------------------------------------- | :------------- | :------------- | :----------------------------- | :----------------------------------------------------------------------------------------------------- |
| 1    | Verificación automática de cobertura geográfica en tiempo real.      | GEO SA         | {{dd/mm/aaaa}} | 🚫 **No viable**                | Requiere un desarrollo de microservicio dedicado y resultaría en altos costos de tokens y complejidad. |
| 2    | Integración con sistema de facturación para descarga directa de PDF. | GEO SA         | {{dd/mm/aaaa}} | 🟢 **Aprobado para cotización** | Se evaluará para la v2.0. Requiere desarrollo de API específica.                                       |
| 3    | Agendamiento automático de visitas técnicas en calendario.           | GEO SA         | {{dd/mm/aaaa}} | ⏳ **En análisis**              | Se está revisando la compatibilidad de la API del sistema de calendarios interno.                      |

---

## ✍️ 6. Firma de Conformidad

La firma de este documento certifica que las funcionalidades descritas han sido validadas y el cliente GEO SA acepta la entrega de la versión 1.0 del Asistente Virtual.

<br>
<br>

---
**Por GEO SA:**
<br>
[Nombre del Responsable]
<br>
[Cargo]

<br>
<br>

---
**Por Asisteclick:**
<br>
Luis Sánchez
<br>
Bot Builder