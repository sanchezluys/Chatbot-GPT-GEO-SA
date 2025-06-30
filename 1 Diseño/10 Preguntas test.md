# Listado de preguntas de test

Preguntas para validar el comportamiento del bot:

| Id | Pregunta / Intención                               | Valida / Lógica Responsable                                                                                              | Estatus                  |
| -- | --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- | ------------------------ |
| 1  | acceso al portal                                    | iteracción:  validar por dni o telefono                                                                                  | OK                       |
| 2  | consultar saldo                                     | iteracción: validar por dni o telefono                                                                                   | OK                       |
| 3  | consultar plan actual                               | iteracción: mi_plan                                                                                                      | OK                       |
| 4  | informar pago                                       | iteracción: informar_pago                                                                                                | OK                       |
| 5  | cambio de titularidad                               | kb: cambio de titularidad                                                                                                 | OK                       |
| 6  | Reconexión                                         | No hay info                                                                                                               |                          |
| 7  | Solicitar baja de servicio                          | iteracción: solicitar_baja                                                                                               |                          |
| 8  | Proceso de contratación                            | 1. informa y pasa a ventas<br />2. genera ticket de instalacion en isp brain                                              |                          |
| 9  | Consulta por cobertura                              | 1. muestra mapas de cobertura- > kb mapas de cobertura<br />2. pasa a un asesor de ventas -> IA Tool: consultar_cobertura | Faltan los mapas, bot OK |
| 10 | consulta planes y costos                            | kb: planes y servicios                                                                                                    | OK                       |
| 11 | ver mis utimos tickets                              | IAT: 'consultar_tickets'                                                                                                  | OK                       |
| 12 | ver mi tipo de factura abc                          | IAT: con 'buscar_facturas_abc'                                                                                            | OK                       |
|    | generar ticket de mudanza                           | IAT: crear_ticket                                                                                                         | OK                       |
|    | datos de la empresa, direccion, ubicacion, horarios | KB:                                                                                                                       | OK                       |
|    | solicitar factura                                   | IAT: 'solicitar_factura', 'consultar_factura'                                                                             | OK                       |
|    | cambio de plan                                      | IAT: 'cambio_plan'                                                                                                        | OK                       |
|    | agregar domicilio                                   | IAT: 'agregar_domicilio'                                                                                                  | OK                       |
|    |                                                     |                                                                                                                           |                          |
