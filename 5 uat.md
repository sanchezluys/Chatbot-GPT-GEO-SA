# ✅ ACTA DE VALIDACIÓN Y ENTREGA: ASISTENTE VIRTUAL GEO SA (v1.0)

## 1. Datos del Proyecto

| Parámetro               | Valor                                           |
| :---------------------- | :---------------------------------------------- |
| **Nombre del Proyecto** | Implementación de Asistente Virtual para GEO SA |
| **Cliente**             | GEO SA                                          |
| **Fecha de Entrega**    | {{dd/mm/aaaa}}                                  |
| **Versión del Bot**     | v1.0 / [Mes-Año de Entrega]                     |
| **Modelo IA**           | OpenAI GPT-4o                                   |
| **Desarrollado por**    | Asisteclick / Luis Sánchez                      |
| **Revisado por**        | GEO SA / [Nombre del Responsable]               |

## 2. Objetivo del Documento

Este documento tiene como objetivo validar que las funcionalidades del Asistente Virtual se ajustan a los requerimientos definidos en el documento **"Requerimientos del Bot – GEO SA Rev 1.2"**. La aprobación de este UAT (User Acceptance Testing) certifica la correcta implementación y entrega de la versión 1.0 del bot.

## 3. Leyenda de Estados para Pruebas

| Emoji | Estado          | Descripción                                                               |
| :---- | :-------------- | :------------------------------------------------------------------------ |
| ✅     | **Correcto**    | La funcionalidad cumple 100% con lo esperado.                             |
| ⚠️     | **Parcial**     | La funcionalidad opera, pero con errores menores que no impiden el flujo. |
| ❌     | **Falla**       | La funcionalidad no cumple lo esperado o presenta errores críticos.       |
| 🔕     | **Desactivada** | Funcionalidad desactivada intencionalmente en esta versión.               |

---

## 4. Casos de Prueba

### **Sección A: Funciones Generales y Lógica de Negocio**

| N°      | Funcionalidad                     | Pasos para Probar                                                                                       | Resultado Esperado                                                                                                                                                    | Resultado Obtenido | Validado |
| :------ | :-------------------------------- | :------------------------------------------------------------------------------------------------------ | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------- | :------- |
| **A.1** | **Gestión de Horario No Laboral** | 1. Realizar una consulta que requiera derivación (ej: "cambiar mi plan") fuera del horario de atención. | El bot informa que está fuera del horario laboral, asegura que la consulta fue registrada y que será atendida en la siguiente jornada. La conversación queda abierta. |                    |          |
| **A.2** | **Gestión de Días Feriados**      | 1. Realizar una consulta que requiera derivación durante un día feriado (según KB/JSON).                | El bot informa sobre el día feriado y la posible demora en la respuesta antes de proceder con la derivación.                                                          |                    |          |
| **A.3** | **Archivado por Resolución**      | 1. Completar un flujo que genera un ticket (ej: solicitar baja). 2. Agradecer y despedirse.             | El bot entiende que el flujo finalizó, se despide cordialmente y la conversación se archiva.                                                                          |                    |          |
| **A.4** | **Fallback (Fuera de Dominio)**   | 1. Preguntar algo no relacionado al negocio (ej: "¿Cuál es la capital de Mongolia?").                   | El bot responde amablemente que su especialidad es sobre GEO SA y reenfoca la conversación, sin derivar.                                                              |                    |          |

### **Sección B: Autogestión para No Clientes**

| N°      | Funcionalidad                           | Pasos para Probar                                                                | Resultado Esperado                                                                                                                                                                                  | Resultado Obtenido | Validado |
| :------ | :-------------------------------------- | :------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------- | :------- |
| **B.1** | **Consulta de Planes y Servicios**      | 1. Preguntar "¿Qué planes de internet tienen?".                                  | El bot muestra la información de planes de la KB y ofrece derivar la consulta a `Ventas`.                                                                                                           |                    |          |
| **B.2** | **Consulta de Cobertura**               | 1. Preguntar "¿Tienen cobertura en [Dirección]?".                                | El bot solicita la dirección, informa que un agente de `Ventas` confirmará la disponibilidad y deriva la consulta. Opcionalmente, puede mostrar mapas generales de la KB.                           |                    |          |
| **B.3** | **Proceso de Contratación (con dudas)** | 1. Expresar intención de contratar. 2. En el proceso, manifestar una duda.       | El bot deriva la conversación al departamento de `Ventas` para que un agente resuelva la duda.                                                                                                      |                    |          |
| **B.4** | **Proceso de Contratación (sin dudas)** | 1. Expresar intención de contratar. 2. Proporcionar todos los datos solicitados. | El bot genera un ticket de instalación, informa al usuario que un agente lo contactará y archiva la conversación si el cliente se despide. La conversación es etiquetada como `contratar_servicio`. |                    |          |

### **Sección C: Autogestión para Clientes (Requiere Autenticación)**

| N°      | Funcionalidad                            | Pasos para Probar                                                                      | Resultado Esperado                                                                                                                                                                      | Resultado Obtenido | Validado |
| :------ | :--------------------------------------- | :------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------- | :------- |
| **C.1** | **Autenticación Exitosa (DNI/Teléfono)** | 1. Proporcionar un DNI o teléfono de cliente válido cuando el bot lo solicite.         | El bot confirma la identidad exitosamente y lo comunica al usuario.                                                                                                                     |                    |          |
| **C.2** | **Consulta de Plan y Saldo**             | 1. Siendo un cliente validado, preguntar "¿Cuál es mi saldo y qué plan tengo?".        | El bot consume las APIs correspondientes y muestra el plan/conexiones activas y el saldo pendiente.                                                                                     |                    |          |
| **C.3** | **Acceso al Portal (Cliente A/B/C)**     | 1. Siendo un cliente validado con factura A, B o C, pedir "dame los datos del portal". | El bot provee las credenciales `api_usuario_portal` y `api_clave_portal` y el link al portal.                                                                                           |                    |          |
| **C.4** | **Acceso al Portal (Cliente sin A/B/C)** | 1. Siendo un cliente validado sin factura A, B o C, pedir "dame los datos del portal". | El bot responde amablemente: "Tus credenciales para el portal aún no se encuentran disponibles", sin explicar el motivo.                                                                |                    |          |
| **C.5** | **Actualización de Datos de Contacto**   | 1. Siendo un cliente validado, solicitar "Quiero cambiar mi email".                    | El bot inicia el flujo de actualización, solicita el nuevo dato y utiliza el endpoint de la API para realizar el cambio. La conversación es etiquetada como `actualizar_datos_cliente`. |                    |          |
| **C.6** | **Informar Pago**                        | 1. Siendo cliente validado, decir "quiero informar un pago" y adjuntar una imagen.     | El bot recibe la imagen y detalles, etiqueta la conversación como `informar_pago` y la deriva a `Administración`.                                                                       |                    |          |
| **C.7** | **Solicitar Cambio de Plan**             | 1. Siendo cliente validado, solicitar "quiero cambiar mi plan".                        | El bot muestra los planes disponibles de la KB, pregunta cuál desea el cliente, etiqueta como `modificar_plan` y deriva a `Administración`.                                             |                    |          |
| **C.8** | **Solicitud de Baja**                    | 1. Siendo cliente validado, solicitar "quiero la baja del servicio".                   | El bot genera un ticket de soporte, etiqueta la conversación como `solicitud_de_baja` y la asigna a `Soporte técnico`.                                                                  |                    |          |

### **Sección D: Soporte Técnico y Tickets**

| N°      | Funcionalidad                   | Pasos para Probar                                                                      | Resultado Esperado                                                                                                                                                                           | Resultado Obtenido | Validado |
| :------ | :------------------------------ | :------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------- | :------- |
| **D.1** | **Reporte "Sin Servicio"**      | 1. Siendo cliente validado, reportar "No tengo internet".                              | El bot ofrece una guía visual de la KB. Si el problema persiste, genera un ticket de "Soporte técnico" (ID 1), etiqueta la conversación como `sin_servicio` y la deriva a `Soporte técnico`. |                    |          |
| **D.2** | **Reporte "Servicio Lento"**    | 1. Siendo cliente validado, reportar "internet anda lento".                            | El bot genera un ticket de "Soporte técnico" (ID 1), etiqueta la conversación como `servicio_lento` y la deriva a `Soporte técnico`. **Importante:** No debe ofrecer test de velocidad.      |                    |          |
| **D.3** | **Reporte "Avería en la Zona"** | 1. Siendo cliente validado, reportar "Hay un corte en el barrio" o "problema general". | El bot genera un ticket de "Problema general" (ID 10), etiqueta la conversación como `averia_en_la_zona` y deriva la conversación inmediatamente a `Soporte técnico` para atención humana.   |                    |          |
| **D.4** | **Consulta de Último Ticket**   | 1. Siendo cliente validado, preguntar "¿cómo va mi reclamo?".                          | El bot consume la API para obtener el estado (abierto/cerrado) del último ticket y lo informa. Si el ticket está cerrado y el cliente pregunta por qué, el bot deriva a un agente humano.    |                    |          |

### **Sección E: Información General (No requiere autenticación)**

| N°      | Funcionalidad                       | Pasos para Probar                                                                               | Resultado Esperado                                                                                                | Resultado Obtenido | Validado |
| :------ | :---------------------------------- | :---------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------- | :----------------- | :------- |
| **E.1** | **Consulta de Datos de la Empresa** | 1. Preguntar "¿Cuál es la dirección?" o "¿Hasta qué hora atienden?".                            | El bot responde con la dirección, link de Google Maps y horarios de atención, extrayendo la información de la KB. |                    |          |
| **E.2** | **Consulta General (Derivación)**   | 1. Realizar una consulta general no cubierta en otros flujos (ej: "consultas administrativas"). | El bot solicita DNI (opcional) y el detalle de la consulta, y deriva a `Administración`.                          |                    |          |

---

## 5. Requerimientos Fuera de Alcance (Versión 1.0)

| N°   | Descripción del Requerimiento                                   | Motivo / Observaciones                                                                                                                                        |
| :--- | :-------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1    | Verificación automática de cobertura geográfica en tiempo real. | **No viable en v1.0.** Requiere un desarrollo de microservicio dedicado y resultaría en altos costos de tokens y complejidad. Se gestiona derivando a Ventas. |
| 2    | Reiteración automática de derivación tras 4 horas.              | **Limitación de plataforma.** Esta lógica debe ser gestionada por un agente o colaborador dentro de AsisteClick.                                              |
| 3    | Archivado automático de chats tras 24 horas sin respuesta.      | **Limitación de plataforma.** Esta lógica debe ser gestionada por un agente o colaborador dentro de AsisteClick.                                              |

---

## 6. Firma de Conformidad

La firma de este documento certifica que las funcionalidades descritas han sido validadas y el cliente GEO SA acepta la entrega de la versión 1.0 del Asistente Virtual.

<br><br>

---

**Por GEO SA:**
`<br>`
[Nombre del Responsable]
`<br>`
[Cargo]

<br><br>

---

**Por Asisteclick:**
`<br>`
Luis Sánchez
`<br>`
Bot Builder