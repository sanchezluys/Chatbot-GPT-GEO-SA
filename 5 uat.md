# ✅ ACTA DE VALIDACIÓN Y ENTREGA: ASISTENTE VIRTUAL GEO SA (v1.0)

## 1. Datos del Proyecto

| Parámetro                    | Valor                                            |
| :---------------------------- | :----------------------------------------------- |
| **Nombre del Proyecto** | Implementación de Asistente Virtual para GEO SA |
| **Cliente**             | GEO SA                                           |
| **Fecha de Entrega**    | {{dd/mm/aaaa}}                                   |
| **Versión del Bot**    | v1.0 / [Mes-Año de Entrega]                     |
| **Modelo IA**           | OpenAI GPT-4o                                    |
| **Desarrollado por**    | Asisteclick / Luis Sánchez                      |
| **Revisado por**        | GEO SA / [Nombre del Responsable]                |

## 2. Objetivo del Documento

Este documento tiene como objetivo validar que las funcionalidades del Asistente Virtual se ajustan a los requerimientos definidos en el documento **"Requerimientos del Bot – GEO SA Rev 1.2"**. La aprobación de este UAT (User Acceptance Testing) certifica la correcta implementación y entrega de la versión 1.0 del bot.

## 3. Leyenda de Estados para Pruebas

| Emoji | Estado                | Descripción                                                              |
| :---- | :-------------------- | :------------------------------------------------------------------------ |
| ✅    | **Correcto**    | La funcionalidad cumple 100% con lo esperado.                             |
| ⚠️  | **Parcial**     | La funcionalidad opera, pero con errores menores que no impiden el flujo. |
| ❌    | **Falla**       | La funcionalidad no cumple lo esperado o presenta errores críticos.      |
| 🔕    | **Desactivada** | Funcionalidad desactivada intencionalmente en esta versión.              |

---

## 4. Casos de Prueba

### **Sección A: Bloques principales**

| N° | Funcionalidad                   | Pasos para Probar | Resultado Esperado                             | Resultado Obtenido                                  | Validado |
| :-- | :------------------------------ | :---------------- | :--------------------------------------------- | :-------------------------------------------------- | :------- |
| A.1 | buscar dni                      |                   | Pendiente: ajustar a Tu saldo actual es numero | ✅ valida ok por dni<br />⚠️ ajustar mensaje      |          |
| A.2 | buscar telefono                 |                   | Pendiente ajustar mensaje                      | ✅ valida ok por telefono<br />⚠️ ajustar mensaje |          |
| A.3 | buscar datos del cliente        |                   |                                                | ✅                                                  |          |
|     | - facturas abc                  |                   |                                                | ✅                                                  | ✅       |
|     | - ajustar var: mostrar informes |                   | ⚠️                                           |                                                     |          |
| A.4 |                                 |                   |                                                |                                                     |          |
| A.5 | estado servicios mostrar        |                   |                                                |                                                     |          |
|     |                                 |                   |                                                |                                                     |          |
|     |                                 |                   |                                                |                                                     |          |

### **Sección B: Menu Ventas**

| N° | Funcionalidad                 | Pasos para Probar             | Resultado Esperado | Resultado Obtenido            | Validado |
| :-- | :---------------------------- | :---------------------------- | :----------------- | :---------------------------- | :------- |
| B.1 | Menu Ventas                   | Muestra las opciones          |                    | ✅                            | ✅       |
| B.2 | ventas.politicas              | Pedir las politicas           |                    | ✅                            | ✅       |
| B.3 | ventas.planes                 | Mostrar los planes            |                    | ✅                            | ✅       |
| B.4 | ventas.horario y direccion    | Preguntar horario y direccion |                    | ✅ Direccion<br />✅ Horarios | ✅       |
| B.5 | ventas. contratar servicio    |                               |                    |                               |          |
|     | - crear ticket de instalacion |                               |                    |                               |          |
| B.5 | ventas.otras consultas        |                               |                    |                               |          |
|     | - otras consultas.reconexion  | ⚠️ ajustar prompt           |                    |                               |          |
|     | - otras consultas.            | ⚠️ ajustar prompt           |                    |                               |          |
|     | --- a clientes:               | ⚠️ ajustar prompt           |                    |                               |          |
|     | --- a externos:               | ⚠️ ajustar prompt           |                    |                               |          |
|     |                               |                               |                    |                               |          |
|     |                               |                               |                    |                               |          |

### **Sección C: Horarios y Feriados**

| N° | Funcionalidad                  | Pasos para Probar       | Resultado Esperado | Resultado Obtenido | Validado |
| :-- | :----------------------------- | :---------------------- | :----------------- | :----------------- | :------- |
| C.1 | Gestión de Horario No Laboral | preguntar el horario    |                    | ✅                 | ✅       |
| C.2 | Gestión de Días Feriados     | preguntar si es feriado |                    | ✅                 | ✅       |
|     |                                |                         |                    |                    |          |

### **Sección D: Autogestión para Clientes**

| N° | Funcionalidad                                    | Pasos para Probar                                                                      | Resultado Esperado                                                                                                                                                                          | Resultado Obtenido | Validado |
| :-- | :----------------------------------------------- | :------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----------------- | :------- |
| D.1 | **Autenticación Exitosa (DNI/Teléfono)** | 1. Proporcionar un DNI o teléfono de cliente válido cuando el bot lo solicite.       | El bot confirma la identidad exitosamente y lo comunica al usuario.                                                                                                                         |                    |          |
| D.2 | **Consulta de Plan y Saldo**               | 1. Siendo un cliente validado, preguntar "¿Cuál es mi saldo y qué plan tengo?".     | El bot consume las APIs correspondientes y muestra el plan/conexiones activas y el saldo pendiente.                                                                                         |                    |          |
| D.3 | **Acceso al Portal (Cliente A/B/C)**       | 1. Siendo un cliente validado con factura A, B o C, pedir "dame los datos del portal". | El bot provee las credenciales `api_usuario_portal` y `api_clave_portal` y el link al portal.                                                                                           |                    |          |
| D.4 | **Acceso al Portal (Cliente sin A/B/C)**   | 1. Siendo un cliente validado sin factura A, B o C, pedir "dame los datos del portal". | El bot responde amablemente: "Tus credenciales para el portal aún no se encuentran disponibles", sin explicar el motivo.                                                                   |                    |          |
| D.5 | **Actualización de Datos de Contacto**    | 1. Siendo un cliente validado, solicitar "Quiero cambiar mi email".                    | El bot inicia el flujo de actualización, solicita el nuevo dato y utiliza el endpoint de la API para realizar el cambio. La conversación es etiquetada como `actualizar_datos_cliente`. |                    |          |
| D.6 | **Informar Pago**                          | 1. Siendo cliente validado, decir "quiero informar un pago" y adjuntar una imagen.     | El bot recibe la imagen y detalles, etiqueta la conversación como `informar_pago` y la deriva a `Administración`.                                                                     |                    |          |
| D.7 | **Solicitar Cambio de Plan**               | 1. Siendo cliente validado, solicitar "quiero cambiar mi plan".                        | El bot muestra los planes disponibles de la KB, pregunta cuál desea el cliente, etiqueta como `modificar_plan` y deriva a `Administración`.                                           |                    |          |
| D.8 | **Solicitud de Baja**                      | 1. Siendo cliente validado, solicitar "quiero la baja del servicio".                   | El bot genera un ticket de soporte, etiqueta la conversación como `solicitud_de_baja` y la asigna a `Soporte técnico`.                                                                |                    |          |
|     | Informar plan del cliente,<br />'mi_plan'        | ⚠️                                                                                   |                                                                                                                                                                                             |                    |          |
|     | Conexiones del cliente,<br />'mis_conexiones'    | ⚠️                                                                                   |                                                                                                                                                                                             |                    |          |
|     |                                                  |                                                                                        |                                                                                                                                                                                             |                    |          |
|     |                                                  |                                                                                        |                                                                                                                                                                                             |                    |          |
|     |                                                  |                                                                                        |                                                                                                                                                                                             |                    |          |
|     |                                                  |                                                                                        |                                                                                                                                                                                             |                    |          |

### **Sección E: Soporte Técnico y Tickets**

| N° | Funcionalidad | Pasos para Probar | Resultado Esperado | Resultado Obtenido | Validado |
| :-- | :------------ | :---------------- | :----------------- | :----------------- | :------- |
| E.1 |               |                   |                    |                    |          |

### **Sección F: Información General (No requiere autenticación)**

| N° | Funcionalidad | Pasos para Probar | Resultado Esperado | Resultado Obtenido | Validado |
| :-- | :------------ | :---------------- | :----------------- | :----------------- | :------- |
| F.1 |               |                   |                    |                    |          |
| F.2 |               |                   |                    |                    |          |

---

## 5. Requerimientos Fuera de Alcance (Versión 1.0)

| N° | Descripción del Requerimiento                                     | Motivo / Observaciones                                                                                                                                               |
| :-- | :----------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | Verificación automática de cobertura geográfica en tiempo real. | **No viable en v1.0.** Requiere un desarrollo de microservicio dedicado y resultaría en altos costos de tokens y complejidad. Se gestiona derivando a Ventas. |
| 2   |                                                                    |                                                                                                                                                                      |

---

## 6. Firma de Conformidad

La firma de este documento certifica que las funcionalidades descritas han sido validadas y el cliente GEO SA acepta la entrega de la versión 1.0 del Asistente Virtual.

`<br><br>`

---

**Por GEO SA:**
`<br>`
[Nombre del Responsable]
`<br>`
[Cargo]

`<br><br>`

---

**Por Asisteclick:**
`<br>`
Luis Sánchez
`<br>`
Bot Builder

Revisiones 5/8/2025

[ubicacion google maps: Coordenadas que deben tomarse validas, en el sistema debe cargarlo como coordenadas LAT,LNG: -27.409326553345,-58.953578948975               Ese es un formato valido, pero, podria realizarse un parsing y reestructuracion de los siguientes links de google ya que contienen la misma informacion en el link pero puesta de otra manera: ?api=1&amp;query=-27.409326553345,-58.953578948975            tambien https://www.google.com/maps/search/?api=1&amp;query=-27.409326553345,-58.953578948975    y tambien: https://www.google.com/maps/place/27%C2%B024&#39;33.6%22S+58%C2%B057&#39;12.9%22W/@-27.4093266,-58.9535789,679m/data=!3m2!1e3!4b1!4m4!3m3!8m2!3d-27.4093266!4d-58.9535789?entry=ttu&amp;g_ep=EgoyMDI1MDcyMy4wIKXMDSoASAFQAw%3D%3D]()
