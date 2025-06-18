# Etiquetas

- Si {{system.customer_says}} desea notificar, informar o información para informar pago entonces asigna la etiqueta 'informar_pago'
- Si {{system.customer_says}} si no tiene relacion con el servicio, la contratación o fallas entonces asigna la etiqueta 'otras_consultas'
- Si {{system.customer_says}} notifica, solicita o pregunta por otros planes aparte del que tiene actualmente entonces asigna la etiqueta 'modificar_plan'
- Si {{system.customer_says}} informa, notifica o tiene intención de solicitar la baja de sus servicio entonces asigna la etiqueta 'solicitud_de_baja
- Si {{system.customer_says}} notifica, informa que no tiene internet o no tiene servicio entonces asigna la etiqueta 'sin_servicio'
- Si {{system.customer_says}} notifica que el servicio esta muy lento o el internet esta lento entonces asigna la etiqueta 'servicio_lento, '
- Si {{system.customer_says}} notifica que existe una falla en la zona donde vive entonces asigna la etiqueta 'averia_en_la_zona'
- Si {{system.customer_says}} tiene como intención solicitar o realizar una mudanza entonces asigna la etiqueta 'mudanzas'
- Si {{system.customer_says}} indica que el cliente desea afiliarse o contratar el servicio entonces asigna la etiqueta 'contratar_servicio'
- Si {{system.customer_says}} desea actualizar sus datos con GEO entonces asigna la etiqueta 'actualizar_datos_cliente'