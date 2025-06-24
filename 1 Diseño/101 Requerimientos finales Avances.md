# ~~Requerimientos del Bot – GEO SA Rev 1.2~~

~~Objetivo General: Migrar las funcionalidades del IVR actual y añadir nuevas capacidades de autogestión y atención al cliente utilizando un chatbot con tecnología OpenAI GPT-4o, integrado en la plataforma AsisteClick y conectado con las APIs de ISP Brain.~~

## ~~Departamentos para Derivación~~

 ~~Administración~~

 ~~Atención al cliente~~

 ~~Soporte técnico~~

 ~~Ventas~~

## Funciones Generales del Bot

    Asignación Inteligente de Conversaciones:

    Derivar conversaciones al departamento correcto según la intención del usuario.

    Etiquetado Automático de Conversaciones:

    Aplicar etiquetas relevantes como: informar_pago, otras_consultas, modificar_plan, solicitud_de_baja, sin_servicio, servicio_lento, averia_en_la_zona, mudanzas, contratar_servicio, actualizar_datos_cliente.

    Generar tickets según la etiqueta:

    sin_servicio / servicio_lento: Ticket de "Soporte técnico" (ID 1).

    averia_en_la_zona: Ticket de "Problema general" (ID 10) y derivación a agente humano.

    Gestión de Horarios y Disponibilidad:

    Horario Laboral: Informar si la consulta es fuera de horario y dejar la conversación abierta para atención en la siguiente jornada.

    Días Feriados:

    Consultar archivo .json de feriados nacionales inamovibles (provisto anualmente por GEO SA, basado en fuente argentinadatos.com).

    Si es feriado, informar posible demora en la respuesta y proceder con la derivación.

    Gestión de Flujos de Conversación:

    Archivado Post-Contratación: Archivar conversaciones de contratación si el ticket de instalación fue generado y el cliente finalizó la interacción. Mantener abierta si hay consultas pendientes.

    Archivado por Resolución: Archivar chats si el bot determina que el motivo del reclamo está resuelto o encaminado.

## Autogestión para Clientes (Integración con API de ISP Brain)

    ~~Autenticación Segura del Cliente:~~

 ~~Validar identidad mediante DNI/CUIT o número de teléfono, utilizando los endpoints de ISP Brain. Requisito para acceso a datos y modificaciones.~~

    Consultas de Cuenta y Servicios:

    ~~Mostrar planes~~ y conexiones activas.

    Consultar estado (abierto/cerrado) del último ticket generado. Derivar si el cliente cerrado desea más detalles.

    Proveer credenciales del portal GEO SA (si el cliente tiene factura A, B o C). Informar "aún no disponible" si no cumple.

    Proveer enlace al resumen de cuenta en el portal.

    ~~Consultar saldo pendiente~~.

    Actualización de Datos de Contacto:

    Permitir a clientes autenticados actualizar teléfono, correo electrónico y WhatsApp a través del endpoint PATCH /customers/{id}/contact de ISP Brain.

    Pagos y Facturación:

    ~~Informar Pago: Recibir imagen y detalles, derivar a Administración.~~

    Solicitar Facturas:

    Clientes con factura A, B o C: Indicar que las vean en el portal. Derivar si hay problemas.

    Otros casos: Derivar a Administración.

    Informar Medios de Pago: Detallar opciones (ventanilla, portal). Guiar al portal a clientes con factura A, B o C para pagos (sin mencionar explícitamente la condición).

    Modificaciones de Servicio (Derivación a Administración):

    Cambio de plan, titularidad (informar proceso), agregar domicilio, cambio de ancho de banda, solicitud de reconexión.

    Soporte Técnico (Generación de Tickets y/o Derivación a Soporte):

    Visita técnica, solicitud de baja, asistencia con imágenes (links provistos por GEO SA), reportar avería, información para cambio de contraseña de router (info provista por GEO SA), reportar problemas de zona (permitir adjuntar multimedia), contacto con personal técnico, mudanza.

## Información General (No requiere autenticación)

    Proveer datos de la empresa (dirección, horarios, Google Maps) desde base de conocimiento.

    Consultas generales no cubiertas: Recabar DNI (opcional) y detalle, derivar a Administración.

## Autogestión para No Clientes

    Información de Servicios:

    Planes disponibles, tipos de servicio (Fibra, Antena, Rural) desde base de conocimiento.

    Consulta de Cobertura:

    Al consultar por cobertura, solicitar dirección/ubicación.

    Informar que un agente de Ventas confirmará la disponibilidad y derivar la consulta.

    Opcional: Mostrar mapas de cobertura generales por zona (imágenes provistas por GEO SA en base de conocimiento), aclarando su carácter general.

    ~~(NOTA: La funcionalidad de verificación automática de cobertura geográfica mediante cálculo de geolocalización (Haversine) no se implementará en esta versión. Las pruebas con el bot "Ubicabot" no fueron exitosas, y se requeriría un desarrollo de microservicio dedicado, lo cual resultaría en altos costos de tokens con GPT-4o para un procesamiento directo por el LLM).~~

    Proceso de Contratación:

    Solicitar datos: DNI, recibo de sueldo, ubicación (para referencia del agente), forma de pago.

    Derivar a Ventas si hay dudas.

    Si se completan datos, generar ticket de instalación.

## ~~Plataforma y Tecnologías~~

 ~~Plataforma de Chatbot: AsisteClick.com~~

 ~~Modelo IA: OpenAI GPT-4o (API de Assistants).~~

 ~~Integraciones Backend: API de ISP Brain (endpoints para clientes, facturación, etc.), sistema de ticketing de GEO SA.~~

    Base de Conocimiento del Bot: Archivos .json (feriados), imágenes (mapas de cobertura, asistencia), texto (info de empresa, router, etc.).

## Puntos Clave para GEO SA

    Confirmar que los procesos de derivación y generación de tickets (IDs, departamentos) son los correctos.

    Proveer el contenido para la base de conocimiento del bot (JSON de feriados, imágenes de mapas y asistencia).

    Revisar que el flujo de atención para consultas de cobertura (sin verificación automática) se alinea con sus procesos operativos.
