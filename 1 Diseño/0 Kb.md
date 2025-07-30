# Knowledge Base KB - Geo

Este documento contiene la información esencial que el chatbot debe conocer para responder consultas relacionadas con servicios, precios, ubicaciones, horarios y promociones de Geo S.A.

## Planes y servicios de Internet

### Planes por Antena

| Velocidad | Uso recomendado                   | Dispositivos soportados |
| --------- | --------------------------------- | ----------------------- |
| 7 Mbps    | Redes sociales, navegación básica | Hasta 2 dispositivos    |
| 10 Mbps   | Streaming HD, videollamadas       | Hasta 3 dispositivos    |
| 12 Mbps   | Streaming HD estable              | Hasta 4 dispositivos    |

### Planes por Fibra Óptica

| Velocidad | Uso recomendado                                      | Dispositivos soportados |
| --------- | ---------------------------------------------------- | ----------------------- |
| 60 Mbps   | Hogares con varios usuarios, Full HD                 | Hasta 8 dispositivos    |
| 100 Mbps  | Streaming 4K, gaming en línea                        | Hasta 10 dispositivos   |
| 300 Mbps  | Teletrabajo intensivo, múltiples pantallas 4K        | Hasta 15 dispositivos   |
| 600 Mbps  | Familias grandes, gaming competitivo, cargas pesadas | Más de 20 dispositivos  |

## Ubicación y Precios por Zona

- El cliente debe estar a menos de **150 metros** de una caja Nap de Geo S.A.
- Se utiliza la **fórmula de Haversine** para calcular distancia entre dos puntos geográficos.
- Radio terrestre: **6378 km (radio ecuatorial)**

### Troncales Especiales

- **Troncal N11:**
  - Planes disponibles: 10 Mbps, 15 Mbps, 30 Mbps
  - ID de planes: 19, 20, 21

- **Troncal N13 (carpeta "No tiene 600 Mbps")**
  - Planes disponibles: 60 Mbps, 100 Mbps
  - ID de planes: 9/13 (60), 5 (100)

## Precios de Instalación

### Fibra Óptica

| Planes             | ID  | Cuotas posibles       |
| ------------------ | --- | --------------------- |
| 60, 100 y 300 Mbps | 20  | 2 cuotas (4% interés) |
| 600 Mbps           | 23  | 2 o 3 cuotas (8%)     |

### Antena

| Planes           | ID  | Cuotas posibles        |
| ---------------- | --- | ---------------------- |
| Todos los planes | 16  | Hasta 2 cuotas (1/15%) |

> ⚠️ No mencionar porcentajes de interés al cliente. Solo mostrar precios finales calculados.

## Requisitos de Contratación

- Fotocopia de DNI  
- Fotocopia de recibo de sueldo, pago de servicio a su nombre o garantía  

## Horario de Atención

| Días                | Horario                       |
| ------------------- | ----------------------------- |
| Lunes a Viernes     | 08:00 – 13:00 / 16:00 – 20:00 |
| Sábados             | 08:00 – 13:00                 |
| Domingos y Feriados | 08:00 – 13:00 / 15:00 – 18:00 |

## Dirección de la Empresa

- **García Merou 127, Resistencia, Chaco**
- [Geo Conexiones - Google Maps](https://maps.app.goo.gl/DxYMt441f79kz8s5A)

## Promociones y Referidos

- **Programa de referidos:** Trae nuevos clientes y gana meses gratis.
- Consultar con un agente para registrar referidos.

## Equipos y Actualizaciones

| Equipo               | ID  | Descripción                  |
| -------------------- | --- | ---------------------------- |
| ONU Simple           | 6   | Precio de reemplazo          |
| Router AC2/N4        | 3   | Precio de reemplazo          |
| Router N2            | 1   | Precio de reemplazo          |
| Actualización Huawei | 21  | Servicio de cambio de equipo |
| Actualización Wifi 6 | 22  | Servicio de cambio de equipo |

## Reconexión

- Incluye pago de **1 mes de servicio + proporcional del mes actual**

## Guías Visuales

- **Fibra Óptica:**  
  ![Guía Fibra](https://static.wixstatic.com/media/b30165_08217842c77840d7b7bc3bade83ae683~mv2.jpeg)

- **Antena:**  
  ![Guía Antena](https://static.wixstatic.com/media/b30165_5648e8a44f7441dd8a2f8a4f6b4e088c~mv2.jpeg)

## IDs y Códigos Relevantes

| Concepto                          | ID  |
| --------------------------------- | --- |
| Instalación Fibra 60/100/300 Mbps | 20  |
| Instalación Fibra 600 Mbps        | 23  |
| Instalación Antena                | 16  |
| ONU Simple                        | 6   |
| Router AC2/N4                     | 3   |
| Router N2                         | 1   |
| Actualización a Huawei            | 21  |
| Actualización a Wifi 6            | 22  |

## Categorías de Tickets en IspBrain

| Categoría                | Código |
| ------------------------ | ------ |
| Estado de ticket abierto | 1      |
| Instalación Fibra Óptica | 2      |
| Instalación Antena       | 12     |

## Derivación a Personal Humano

El bot debe derivar a humano cuando:

- La consulta sea compleja o fuera del alcance del bot.
- El cliente lo solicite explícitamente.
- Sea necesario abrir un ticket o realizar cambios importantes.
- Se requiera validar información sensible (como identidad o datos financieros).

## Imágenes Adicionales

- [Asegurarse que los equipos estén conectados](https://static.wixstatic.com/media/b30165_36fa515ee4414528b1222ee3524d6647~mv2.jpeg)
- [Cambio de contraseña](https://static.wixstatic.com/media/b30165_e855d891021e455887e89e0a50d7353d~mv2.jpeg)
- [Amurar los equipos](https://static.wixstatic.com/media/b30165_05b2ab1880f84ea8b894fe4bb8387321~mv2.jpeg)
- [Equipos comodato](https://static.wixstatic.com/media/b30165_0a886efc844d431aa5852171c57f65a8~mv2.jpeg)

## Portal de Clientes

- Solo disponible para clientes con factura A/B/C.
- URL: `{{portal_url}}`
- Acceso mediante credenciales proporcionadas por el sistema.

## Soporte Técnico

### Problemas Comunes

- Sin servicio
- Lentitud de conexión
- Cambio de contraseña
- Mudanza
- Baja de servicio

### Procedimientos

- Verificar conexión física
- Solicitar fotos de equipos conectados
- Guiar al cliente con imágenes
- Abrir ticket si persiste el problema

## Costos por Casos Especiales

- **Clientes antiguos que quieren volver:** Aplica reconexión + proporcional del mes.
- **Cambio de plan:** Validar ubicación y ofrecer opciones disponibles.
- **Soporte técnico sin costo:** Excepto daños causados por manipulación incorrecta.

## Ejemplo de Resumen Final

Los datos que guardamos para su instalación son:
Nombre completo: [nombre]
DNI: [DNI]
Teléfono: [teléfono]
Dirección: [dirección]

## Políticas del servicio

🔹 *Instalación y Pago:* Para solicitar cualquier servicio de *Geo S.A.*, la instalación puede abonarse de dos maneras:

1. Pago único 💰 Será abonado al instalador al momento de que le instala nuestro servicio.
2. En cuotas 📅 Si elige pagar en cuotas, la primera cuota le abonará al instalador en el momento de la instalación. Las siguientes cuotas se abonarán junto con el plan elegido el mes siguiente, del 1 al 10 de cada mes.

🔹 *Coordinación con el Instalador:* Cuando le asignen un instalador, él se pondrá en contacto con usted para coordinar el día de la visita. Para ello, le pedimos que tenga listos los siguientes documentos:
• Fotocopia de su DNI 🆔
• Fotocopia del pago de servicio o recibo de sueldo a su nombre 📄

🔸 *Equipos en Comodato:* Todos los equipos entregados quedan en comodato 📦. Esto significa que, al rescindir de nuestros servicios, deben ser devueltos a la empresa.

## Cambio de titularidad

Debe venir a la empresa en *García Merou 127* 🏢 junto con la persona que va a ser el nuevo titular.

*Se solicita:*
✔ Fotocopia de DNI 🆔

Luego de cumplir estos requisitos, se le hará firmar un contrato al titular nuevo ✍️📑 y con ello finalizará este trámite.

## Mapas y Zonas de cobertura

Nota: esta información es general y puede no reflejar la cobertura exacta en todas las áreas. Para consultas específicas, recomendamos contactar a un agente de ventas.

Zona 1:
![Mapa de cobertura](https://static.wixstatic.com/media/b30165_0b1c3d6f2e4a4b8c9d5f7c8e2f3b4c5d~mv2.png)

Zona 2:
![Mapa de cobertura](https://static.wixstatic.com/media/b30165_1a)

## Datos para abonar, datos bancarios

Estos son los datos Bancarios 🏦 donde puedes abonar el servicio de forma electrónica: 📌

✔ *CBU*: {{api_cbu}}
✔ *ALIAS*: {{api_alias}}
✔ *CPE*: {{api_cpe}}

Si aún no tienes los datos para abonar, puedes elegir la opción de "*Hablar con el personal administrativo*". 🙋‍♂️

## Días Feriados 2025

| Fecha      | Tipo        | Nombre                                                    |
| ---------- | ----------- | --------------------------------------------------------- |
| 2025-01-01 | inamovible  | Año nuevo                                                 |
| 2025-03-03 | inamovible  | Carnaval                                                  |
| 2025-03-04 | inamovible  | Carnaval                                                  |
| 2025-03-24 | inamovible  | Día Nacional de la Memoria por la Verdad y la Justicia    |
| 2025-04-02 | inamovible  | Día del Veterano y de los Caídos en la Guerra de Malvinas |
| 2025-04-18 | inamovible  | Viernes Santo                                             |
| 2025-05-01 | inamovible  | Día del Trabajador                                        |
| 2025-05-02 | puente      | Puente turístico no laborable                             |
| 2025-05-25 | inamovible  | Día de la Revolución de Mayo                              |
| 2025-06-16 | trasladable | Paso a la Inmortalidad del General Martín Güemes          |
| 2025-06-20 | inamovible  | Paso a la Inmortalidad del General Manuel Belgrano        |
| 2025-07-09 | inamovible  | Día de la Independencia                                   |
| 2025-08-15 | puente      | Puente turístico no laborable                             |
| 2025-08-17 | trasladable | Paso a la Inmortalidad del Gral. José de San Martín       |
| 2025-10-12 | trasladable | Día del Respeto a la Diversidad Cultural                  |
| 2025-11-21 | puente      | Puente turístico no laborable                             |
| 2025-11-24 | trasladable | Día de la Soberanía Nacional                              |
| 2025-12-08 | inamovible  | Día de la Inmaculada Concepción de María                  |
| 2025-12-25 | inamovible  | Navidad                                                   |
