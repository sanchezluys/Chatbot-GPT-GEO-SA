# Requerimientos del ChatBot Upgrade GPT – GEO SA

## Departamentos

El bot debe poder asignar conversaciones a los siguientes departamentos:
*   Administración
*   Atención al cliente
*   Soporte técnico
*   Ventas

## Funciones generales del bot

*   **Asignar las conversaciones a los departamentos correspondientes**.
*   **Etiquetar las conversaciones** con las siguientes opciones:
    *   informar\_pago
    *   otras\_consultas
    *   modificar\_plan
    *   solicitud\_de\_baja
    *   sin\_servicio
    *   averia\_en\_la\_zona
    *   mudanzas
    *   contratar\_servicio
    *   Se debe agregar la etiqueta de **servicio lento**. Tenga en cuenta que "servicio lento" y "sin servicio" corresponden en el sistema a un ticket de "Soporte técnico" que tiene ID 1.
*   **Validar si la conversación está dentro del horario laboral**. Si está fuera, dejar la conversación abierta.
*   **Validar si el día es feriado** utilizando un listado anual. Ese listado será cargado anualmente por GEO SA en las bases de conocimiento del bot
*   **Archivar el chat si el bot entiende que el motivo de reclamo está resuelto**, es decir, si el motivo de la charla ya está encaminada y no hay nada más que hablar (ej: si se abrió ticket y debe aguardar el llamado del técnico).
*   Las conversaciones con interés en contratar el servicio deben **quedar en estado abierto solo si el cliente solicita consultar algo particular**. Si el cliente ya dio sus datos y se hizo un ticket de instalación (usando los IDs correspondientes), entonces **archivar la conversación si el flujo finalizó** (ej: el cliente dijo gracias).

## Autogestión para clientes (autenticados)

*   **Autenticación** por teléfono.
*   **Autenticación** por DNI o CUIT.
*   Mostrar planes y conexiones activas.
*   **NO mostrar los últimos comprobantes de pago**. Informar que el cliente puede ver su historial de pagos y pagar por internet a través del portal. Si el cliente necesita una factura por algún motivo, derivar a agentes humanos. Si el cliente tiene factura A, B o C, pasarle el portal, avisarle que puede ver ahí sus facturas y si no le aparece, que dé aviso y entonces derivar a un agente humano.
*   **NO mostrar los últimos tickets generados**. A lo sumo, permitir **compartir el estado del último ticket generado** (si está abierto o cerrado). Si está cerrado y el cliente quiere saber por qué, derivar a agente humano.
*   **Crear ticket para visita técnica** y asignarlo a Soporte.
*   Informar pago: enviar a Administración con la foto y detalles.
*   Cambio de plan: derivar a Administración.
*   Proveer credenciales de acceso al portal mediante `api_usuario_portal` y `api_clave_portal`. **Importante:** Esto es **SOLAMENTE para clientes que cuentan con factura A, B o C**. En otro caso, decir que aún no se encuentra disponible para su número de cliente. **NO se debe informar al cliente este criterio** para dar o no el portal, a pedido de la empresa.
*   Cambio de titularidad: informar el proceso y derivar a Administración.
*   Informar sobre medios de pago y datos bancarios. **Importante:** Los **ÚNICOS medios de pago disponibles son en efectivo por ventanilla o mediante el portal** (este último solo se da a clientes con facturas A, B o C). **El criterio para dar o no el portal no debe informarse al cliente**.
*   Proveer **información general de la empresa**: dirección, horarios de atención, ubicación (Google Maps).
*   Consultas generales: derivar a Administración con DNI y detalle de la consulta.
*   Agregar otro domicilio al plan: derivar a Administración.
*   Cambio de ancho de banda: derivar a Administración.
*   Solicitud de reconexión: derivar a Administración.
*   Ver resumen de cuenta a través de un enlace al portal que se informa
*   Consultar saldo mediante la API.
*   Solicitar facturas de un período: derivar a Administración. Si el cliente tiene factura A, B o C, pasarle el portal, avisarle que puede ver sus facturas ahí y si no le aparece, que dé aviso y entonces proceder a derivar a un agente humano.
*   Solicitud de baja: generar ticket y asignar a Soporte. El bot IVR lo hace bien
*   Asistencia técnica con imágenes (casos de fibra y antena).
*   Reportar avería: generar ticket y asignar a Soporte.
*   Informar sobre avería en la zona ("Problema general"): generar ticket con **ID 10** en el sistema y a su vez **derivar a un humano**. Es importante que esté en el sistema aunque se derive, para que los agentes estén al tanto del problema general.
*   Información para cambiar la contraseña del router. Se indican los pasos a seguir.
*   Reportar problemas de zona (servicio lento o sin servicio): incluir tipo de conexión (fibra o antena), fotos y videos. Se asigna a Soporte.
*   Solicitar contacto con personal técnico: se pide detalle del caso y se asigna a Soporte.
*   Solicitar mudanza: se recaban datos y se deriva a Soporte.
*   **NO ejecutar test de velocidad con herramientas disponibles**. La razón es que las mediciones del cliente suelen ser incorrectas si no se hacen bajo condiciones específicas (vía cable UTP, sin otros equipos conectados, sin consumo de ancho de banda en el equipo de medición). Por tanto, no se considera algo que amerite una urgencia basado en mediciones de speedtest. 
*   Solicitar visita técnica: se solicita información, se genera ticket y se deriva a Soporte.

## Autogestión para no clientes

*   Consultar planes disponibles.
*   Solicitar datos para contratar (DNI, recibo de sueldo, ubicación por Google Maps, forma de pago). Luego, derivar el caso a Ventas.
*   Informar sobre los tipos de servicio, velocidades y características (Fibra óptica, Antena wireless).
*   **Para la contratación de instalación**: si el cliente tiene dudas, que derive a Ventas. Si no tiene dudas, que haga el ticket de instalación automáticamente.
*   **Nuevos requerimientos:** Determinar si hay **cobertura** en la ubicación geográfica del cliente (compartida por Google Maps) utilizando archivos KML o KMZ.

# Requerimientos que no pueden ser atendidos.

*   Si pasan **4 horas sin respuesta de un agente humano** después de una derivación, **reiterar la derivación 1 vez** (para que suba arriba del chat). Esto por plataforma lo debe hacer un agente o colaborador
*   Si pasan **más de 24 horas sin respuesta a la segunda derivación**, **archivar el chat** para que el cliente pueda volver a hablar con el bot. Esto por plataforma lo debe hacer un agente o colaborador.