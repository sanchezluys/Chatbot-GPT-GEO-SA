Hay varias cosas del documento que redacté que no se encuentran en la propuesta que me enviaste. Algunas de ellas son específicas que ya había aclarado por el chat de Asisteclick que no debían estar (por ejemplo, el test de velocidad, que tampoco lo tenía el bot anterior) y se encuentran también en el documento compartido: BOT CHATGPT: GEO S - Documentos de Google

Sin embargo de eso que usted me mandó voy a hacer unas correcciones

Todo lo que yo no nombre acá de lo que usted escribió es correcto, sin embargo faltan características que se encuentran en el documento adjuntado, lo que no esta en ese documento o tal vez no fui muy claro lo voy a detallar a continuación:

Falta la etiqueta de servicio lento. Tene en cuenta que servicio lento y sin servicio, corresponden en el sistema a un ticket de "Soporte técnico" que tiene ID 1.
Avería en la zona también tiene su correspondiente en el sistema como "Problema general" que tiene ID 10, me gustaría que abra un ticket de problema general pero que a su vez también derive a un humano, los problemas generales son de importancia ya que suelen afectar a varios clientes, y quiero que esté en el sistema porque es importante que no se le pase al agente humano, puede que se le pase contestarle pero es importante que los que están en el sistema estén al tanto del problema general aunque sea una falsa alarma y tengan que cerrar el ticket.

Validar si está dentro del horario laboral, los feriados que reconoce la empresa son solos los feriados nacionales inamovibles que estan en esta pagina Feriados 2025 | Argentina.gob.ar son los de colores azules, simplemente dar aviso al cliente que por ser feriado puede que nadie responda su derivación hasta que vuelvan a la oficina, y ahí derivar.

Si pasa un tiempo de 4 horas desde que se derivó y aun el cliente no recibe respuesta de un agente humano reiterar la derivación 1 vez (para que suba arriba de todo el chat)
Si pasa más de 24 horas sin respuesta a la segunda derivación archivar el chat para que el cliente pueda volver a hablar con el bot.
Archivar el chat si el bot entiende que el motivo de reclamo está resuelto, osea, si el motivo de la charla ya está encaminada y no hay nada más que hablar (por ejemplo si se abrió ticket y debe aguardar el llamado del técnico, etc...)

Las conversaciones con interés en contratar el servicio deben quedar en estado abierto. NO NECESARIAMENTE, si el cliente ya dio sus datos y el sistema hizo un ticket de instalación (en el documento compartido deje todos los ID de los tickets de instalación), entonces simplemente archivar la conversación si el flujo de conversación finalizó (ej: el cliente dijo gracias, espero su llamado), dejar abierto solo si el cliente solicita que quiere consultar algo particular

Ver últimos comprobantes de pago. ESTO NO, El otro bot no lo tenía y no quiero que este lo tenga, ellos van a poder ver su historial de pagos y pagar por internet vía el portal, otro medio alternativo a ese no quieren que se utilice. Si el cliente necesita una factura por algún motivo entonces derivar a agentes humanos y que ellos le den, si el cliente tiene factura A,B o C entonces pasarle el portal, avisarle que pueden ver ahí sus facturas y si no le aparece que den aviso de esa situación y entonces proceder a derivar a un agente humano.

No quiero que se vean los ultimos tickets generados, a lo sumo me permiten que se comparta el estado del último ticket generado (si es abierto o cerrado), si está cerrado y el cliente quiere saber porque entonces derivar a agente humano

Proveer credenciales de acceso al portal mediante api_usuario_portal y api_clave_portal. ESTO ESTA BIEN PERO INSISTO, SOLAMENTE SE LE PROVEE DEL PORTAL A AQUELLOS CLIENTES QUE CUENTAN CON FACTURA  A,B O C, en otro caso decir que aun no se encuentra disponible para su número de cliente.

Informar sobre medios de pago y datos bancarios. LOS ÚNICOS MEDIO DE PAGO DISPONIBLE ES EN EFECTIVO POR VENTANILLA O MEDIANTE EL PORTAL (QUE SOLO SE DA A CLIENTES CON FACTURAS A B O C, este criterio para dar o no portal no debe informarse al cliente a pedido de la empresa)

Las solicitudes de baja están bien cómo se generan en el sistema viejo.

En el caso de la instalación, que derive a ventas si tiene dudas, si no que haga el ticket de instalación automáticamente y ya.

Mucho en el resumen que me mandó se encuentra explicado a detalle en ese documento que le compartí, hay muchos matices que no pueden reflejarse en el resumen que me mandó y otras cosas que pedí que no estén específicamente y que se encuentran en el mail que me envió (como el tema del speedtest) y el motivo es sencillo, si el cliente mide por speedtest su conexión y no le llegan los megas que contratas no necesariamente es porque es un fallo nuestro, la medición de mbps tiene que ser realizada vía cable utp conectado a un equipo y que no haya nada más conectado en esa red, caso contrario jamás le van a llegar esos mbps que contrato, inclusive si el equipo que está usando para medir esta consumiendo ancho de banda también se verá reflejado en la medición, por tanto no lo tomamos como algo que amerite una urgencia, si el cliente viene a la empresa a quejarse por dicha situación bueno, mandaremos puntualmente a alguien, pero generalmente es porque miden mal. Y así con cada tema que pedimos que no esté en el bot actual.