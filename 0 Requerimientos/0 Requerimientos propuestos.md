Requerimientos del ChatBot Upgrade GPT – GEO SA
Departamentos:

    Administración

    Atención al cliente

    Soporte técnico

    Ventas

Funciones generales del bot

    Asignar las conversaciones a los departamentos correspondientes.

    Etiquetar las conversaciones con:

        informar_pago

        otras_consultas

        modificar_plan

        solicitud_de_baja

        sin_servicio

        averia_en_la_zona

        mudanzas

        contratar_servicio

    Validar si está dentro del horario laboral. Si está fuera, dejar la conversación abierta.

    Las conversaciones con interés en contratar el servicio deben quedar en estado abierto.

    Validar si el día es feriado (utilizando un listado anual) y responder que no es un día laboral.

Autogestión para clientes

    Autenticación por teléfono.

    Autenticación por DNI o CUIT.

    Mostrar planes y conexiones activas.

    Ver últimos comprobantes de pago.

    Crear ticket para visita técnica (se asigna a Soporte).

    Ver últimos tickets generados.

    Informar pago: enviar a Administración con la foto y detalles del mismo.

    Cambio de plan: derivar a Administración.

    Proveer credenciales de acceso al portal mediante api_usuario_portal y api_clave_portal.

    Cambio de titularidad: informar el proceso y derivar a Administración.

    Informar sobre medios de pago y datos bancarios.

    Proveer información general de la empresa: dirección, horarios de atención, ubicación (Google Maps).

    Consultas generales: derivar a Administración con DNI y detalle de la consulta.

    Agregar otro domicilio al plan: derivar a Administración.

    Cambio de ancho de banda: derivar a Administración.

    Solicitud de reconexión: derivar a Administración.

    Ver resumen de cuenta a través de un enlace al portal.

    Consultar saldo mediante la API.

    Solicitar facturas de un período: derivar a Administración.

    Solicitud de baja: generar ticket y asignar a Soporte.

    Asistencia técnica con imágenes (casos de fibra y antena).

    Reportar avería: generar ticket y asignar a Soporte.

    Información para cambiar la contraseña del router.

    Reportar problemas de zona (servicio lento o sin servicio): incluir tipo de conexión (fibra o antena), fotos y videos. Se asigna a Soporte.

    Solicitar contacto con personal técnico: se pide detalle del caso y se asigna a Soporte.

    Solicitar mudanza: se recaban datos y se deriva a Soporte.

    Ejecutar test de velocidad con herramientas disponibles.

    Solicitar visita técnica: se solicita información, se genera ticket y se deriva a Soporte.

Autogestión para no clientes

    Consultar planes disponibles.

    Solicitar datos para contratar: DNI, recibo de sueldo, ubicación (Google Maps), forma de pago. Luego, derivar el caso a Ventas.

    Informar sobre los tipos de servicio, velocidades y características:

        Fibra óptica

        Antena wireless

        Contratación rural

Nuevos requerimientos

    Determinar si hay cobertura en la ubicación geográfica del cliente compartida por Google Maps, utilizando archivos KML o KMZ