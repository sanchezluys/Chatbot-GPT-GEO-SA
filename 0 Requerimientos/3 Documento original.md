BOT CHATGPT: GEO S.A.
El Proyecto se dividirá en etapas, a consejo de Luis convendrá poner las características más simples y principales en la primera de las etapas por tanto lo haremos así.
Actualmente ya contamos con un modelo de chatbot hecho por asisteclick, el cual cuenta con una serie de características básicas que queremos trasladar a este nuevo bot mas avanzado, para evitar que vaya a mirar el bot directamente o el diagrama de flujo facilitare las funciones que quiero que tenga el bot en esta primera etapa en este mismo documento.
 
A grandes rasgos quiero que el bot añada una característica que no tenia el bot anterior pero que podría haber tenido, que es el poder generar diferentes tipos de tickets en IspBrain (actualmente ya genera tickets de baja y de mudanza) ya que nos es mas simple simplemente cerrar aquellos que no están abiertos de forma “errónea”. Otra característica seria poder dar al futuro cliente que solicite, el precio y servicio acorde a donde se encuentra geográficamente su domicilio. Todas estas cuestiones las iré detallando a lo largo de la descripción de lo que necesitamos que realice el bot. Otra característica que se me ocurre es un apartado de promociones que se mostrara si es cliente.
 
BIENVENIDA: 👋 Gracias por comunicarte con Geo S.A. Dígame, ¿En que podemos ayudarte?
 
Validar si el teléfono existe en IspBrain
·         Si existe: "Bienvenido, ¿Usted es el cliente [name]?" 🙂
si la respuesta es SI va al menú principal.
sí es NO va a ¿Quieres intentar con otro DNI?
 
Esto permite que el cliente pueda ver su cuenta o la de un familiar, o si esta usando otro celular pueda encontrarse a si mismo y saber la información que le interesa.
 
·         Si no existe consulta ¿En que te podemos ayudar? ✨
 
Aquí el cliente puede optar por insistir que es cliente, a lo cual se volverá a solicitar el DNI o que no es cliente aun, si no es deberá mostrar un mensaje de Marketing similar a este:
 
¡Bienvenido a Geo S.A. 🌐!
¿Necesitas internet en lugares donde otros no llegan? ¡Geo está acá para vos! 💪
En Geo, nos especializamos en llevar conectividad de calidad a las zonas más remotas. Nuestro servicio combina la tecnología de fibra óptica y antena para que tengas acceso a internet dónde te encuentres.
¿Por qué elegirnos?
🌍 Cobertura Extensa: Llegamos a donde otros no pueden, con soluciones de Fibra Óptica y enlaces vía Antena.
🌾 Conexión al alcance de todos: Diseñamos nuestros planes pensando en quienes necesitan conectividad, tanto en la ciudad o en áreas rurales.
⚡ Buena Velocidad: Disfruta de una conexión rápida y estable que te permite navegar, trabajar o estudiar sin interrupciones.
Con Geo, te aseguras un internet confiable y con la mejor cobertura en el Gran Resistencia. ¡Súmate y crea tus conexiones! 🔗
 
Acá podrá consultar acerca de: PLANES / REQUISITOS Y PRECIOS DE INSTALACION SEGÚN SU ZONA / HORARIOS DE ATENCION / DIRECCION / OTRAS CONSULTAS o podrá insistir en que es cliente a lo que se le deberá pedir el DNI para validarlo.
 
Vamos por partes:
 
PLANES
¡Ofertas en Geo Conexiones! 📶
Aprovecha nuestras ofertas y contrata la mejor conexión a internet que se ajuste a tus necesidades:
 
🌐Por Antena
7 Mbps
• Ideal para: Navegación y redes sociales con hasta 2 dispositivos conectados.
10 Mbps
• Ideal para: ver streaming en HD y videollamadas en hasta 3 dispositivos.
12 Mbps
• Ideal para: ver streaming en HD y conexión estable con hasta 4 dispositivos.
 
🚀Por Fibra Óptica
60 Mbps
• Ideal para: Hogares con varios usuarios, Full HD y hasta 8 dispositivos conectados.
 
100 Mbps
• Ideal para: Streaming 4K, gaming en línea y hasta 10 dispositivos.
 
300 Mbps
 • Ideal para: Teletrabajo intensivo, videollamadas en alta calidad, streaming en múltiples pantallas 4K y hasta 15 dispositivos conectados.
 
600 Mbps
 • Ideal para: Familias grandes o casas inteligentes, gaming competitivo, cargas y descargas pesadas en la nube, y más de 20 dispositivos conectados
 
💬 ¡No te pierdas esta oportunidad de conectarte con la mejor cobertura en Resistencia! En Geo Conexiones, llegamos a donde otros no pueden. Conecta tu hogar o negocio con la tecnología que necesitas.
 
¿Queres saber qué servicios podemos ofrecerte en tu zona? Pasanos tu dirección exacta o ubicación (actual o de Google maps) así te podemos pasar los precios y planes que ofrecemos en tu zona 💪
 
 
---------- Recibido ----------
Bien Aquí esta la cuestión, una vez que recibimos la ubicación o dirección debemos poder filtrarlos comparándolos con las cajas de la empresa. El criterio es que el cliente debe estar en un rango menor a 150 metros de 1 o mas cajas nap de la empresa, para ello se utiliza la formula de distancia entre 2 puntos, pero como la tierra es una esfera tendremos que tener en cuenta la curvatura, entonces se utilizara la formula del Haversine.
Utiliza el radio terrestre 6378 km (radio ecuatorial)
 
Te dejo un link de utilidad: ¿Cómo calcular la distancia entre dos puntos geográficos en C#? (Fórmula de Haversine)
 
El bot tiene que evitar realizar comparaciónes sin importancia, como por ejemplo comparar al cliente con todas las cajas de la empresa, ya que es algo ineficiente, debería compararlo con el de su zona como mucho, el kmz está dividido por troncales, si el cliente se encuentra en el radio de ese troncal deberá comparar únicamente con las cajas de ese troncal. No sé me ocurre la forma de hacerlo pero podrían dividir gran resistencia en cuadrantes, o por zonas como comenté. Hacerlo comparando con todas las cajas daría el resultado correcto, pero sería sumamente ineficiente ya que no tiene sentido comparar las cajas de un barrio donde está el cliente con la casa del cliente y las cajas de otro barrio en otra localidad.

Deberá comparar la ubicación del cliente con las cajas mas cercanas a esa ubicación dentro del archivo kmz “GEO CAJAS” que les pasare, aquí se encuentran todos los troncales de fibra óptica de la empresa, y se le debe brindar la información según lo que consulte el cliente, si es sobre planes o instalación.
 
Los planes que contamos se encuentran en ISPbrain, de nuestro lado los vemos en la pestaña ventas -> planes, en todos los troncales se aplica los planes comunes de fibra óptica salvo en troncales específicos que les indicare luego, aparecen con su respectivo ID para acceder a la información, de esta manera:
 
o   PLAN 60 MBPS: Aparece con el ID 7, su nombre es P60MBFO aquí obtendrás el precio de este plan.
o   PLAN 100 MBPS: Aparece con el ID 11, su nombre es P100MBFO. Aquí obtendrás el precio de este plan.
o   PLAN 300 MBPS: Aparece con el ID 3, su nombre es P300MBFO aquí obtendrás el precio de ese plan.
o   PLAN 600 MBPS: Aparece con el ID 23, su nombre es P600MBFO aquí obtendrás el precio de ese plan.
 
Bien, hay zonas especificas donde estos planes no se pueden ofrecer por diversos motivos, en el Google Earth estas son las zonas en los cuales hay que ofrecer otros precios que indicare a continuación
 
·         TRONCAL N11: Si el cliente manda la ubicación y se encuentra en este lugar hay que decirle que en su zona se ofrecen planes distintos a los anunciados, en esta zona contamos con estos planes:
o   PLAN 10 MBPS: Aparece con el ID 19, su nombre es 30MBFO. Aquí obtendrás el precio de este plan.
o   PLAN 15 MBPS: Aparece con el ID 20, su nombre es 15MBFO. Aquí obtendrás el precio de este plan.
o   PLAN 30 MBPS: Aparece con el ID 21, su nombre es 10MBFO. Aquí obtendrás el precio de este plan.
·         TRONCAL N13: Dentro del KMZ veras una carpeta que dice “No tiene 600 mbps”, en esa zona solo se ofrecerán los planes hasta 100 mbps, 300 mbps y 600 mbps no están disponibles allí, estos son las ID de estos planes que ofrecemos en esa zona para acceder a su precio:
o   PLAN 60 MBPS: Aparece con el ID 9 o con el ID13, su nombre es P60MBFO! o P60MBFO!. Aquí obtendrás el precio de este plan.
o   PLAN 100 MBPS: Aparece con el ID 5, su nombre es P100MBFO! Aquí obtendrás el precio de este plan.
 
sin embargo las otras cajas que están fuera de esa carpeta “No tiene 600 mbps” y dentro el Troncal N13 se puede ofrecer normalmente los planes comunes (60,100,300 y 600 mbps).
Todos aquellos clientes o futuros clientes que consulten por planes o instalación que se encuentren fuera de este rango de 150 metros de una caja de la empresa, pero dentro del GRAN RESISTENCIA, CHACO. Se le deberá ofrecer el servicio de conexión a internet vía antena. Este enlace ofrece:
·         PLAN 7 MBPS: Aparece con el ID 14, su nombre es 7MB Aquí obtendrás el precio de este plan. Por algún motivo se encuentra duplicado, si no encontras el plan con el ID14, búscalo con el ID 16, su nombre es P7MP.
·         PLAN 10 MBPS: Aparece con el ID 1, su nombre es 10Mbps Aquí obtendrás el precio de este plan.
·         PLAN 12 MBPS: Aparece con el ID 6, su nombre es P12mb Aquí obtendrás el precio de este plan.
 
Los otros planes que no nombre acá, salvo que demos aviso de creación de un plan nuevo o cambio de precio que requiera crear otro plan no los utilices bajo ningún concepto.
 
Los precios de instalación con los que contamos se encuentran en ISPbrain, de nuestro lado los vemos en la pestaña ventas -> productos, esto puede cambiar, si hay un cambio avisaremos que hay que cambiar el precio de un ID a otro, debido a que no podemos editar los precios, solo crear nuevos productos y eliminar los anteriores, no estoy seguro si pasa lo mismo con los planes, en fin. Los precios de instalación son los siguientes:
 
Fibra óptica:
·         60, 100 y 300 MBPS: El precio de la instalación tiene la ID 20, también puede abonarse en 2 cuotas con el 4% de interés sobre el valor de la instalación a 1 cuota (ejemplo, si la instalación vale $25000, cada cuota valdrá $16000).
·         600 MBPS: El precio de la instalación tiene la ID 23, también se puede abonar en 2 cuotas con el 8% de interés sobre el valor de la instalación a 1 cuota (ejemplo, si la instalación vale $50000, cada cuota valdrá $27000), lo mismo sucede en 3 cuotas (ejemplo, si la instalación vale $50000, cada cuota valdrá $18000)
 
El motivo de la diferencia de precio entre uno y el otro es que se coloca un equipo de mejor tecnología.
 
Antena:
·         Los 3 planes de antena cuestan para instalar lo mismo, Es el ID 16 que dice Instalación Antena Marzo 25, también pueden optar en hacer hasta 2 cuotas, pero cada cuota tiene un 1/15% de interés sobre el valor de la instalación a 1 cuota (por ejemplo, si la instalación vale $30000, cada cuota valdrá $16000).
 
Los otros productos que no nombre acá, salvo que demos aviso de creación de un plan nuevo o cambio de precio que requiera crear otro plan no los utilices bajo ningún concepto.
 
 
Supongamos que el cliente se ve interesado en contratar el servicio y quiere conocer los requisitos, deberás mandar un mensaje similar a este:
 
Los únicos requisitos que necesitamos que usted tenga es:
• Fotocopia de DNI
• Fotocopia de un recibo de sueldo de empleado activo, pago de servicio a su nombre o alguna garantía
Si cuenta con los requisitos podemos avanzar 💪 ¿Quiere continuar con la solicitud?
 
Bien, se deberá solicitar al cliente su nombre completo, DNI, numero telefónico que desea agendar como contacto, su dirección y también su ubicación actual para saber que servicio ofrecerle.
 
Acá hay un pequeño recordatorio del bot anterior:
 
Es necesario que usted sepa acerca de lo siguiente:
🔹 Instalación y Pago:
Para solicitar cualquier servicio de Geo S.A., la instalación puede abonarse de dos maneras:
1. Pago único 💰
Sera abonado al instalador al momento de que le instala nuestro servicio.
2. En cuotas 📅
Si elige pagar en cuotas, la primera cuota le abonara al instalador en el momento de la instalación. Las siguientes cuotas se abonarán junto con el plan elegido el mes siguiente, del 1 al 10 de cada mes.
🔹 Coordinación con el Instalador:
Cuando le asignen un instalador, él se pondrá en contacto con usted para coordinar el día de la visita.
Para ello, le pedimos que tenga listos los siguientes documentos:
• Fotocopia de su DNI 🆔
• Fotocopia del pago de servicio o recibo de sueldo a su nombre 📄
🔸 Equipos en Comodato:
Todos los equipos entregados quedan en comodato 📦. Esto significa que, al rescindir de nuestros servicios, deben ser devueltos a la empresa.
 
Podes mejorar el formato pero manteniendo el mensaje.
 
 
 
 
 
 
UNA VEZ QUE SE TERMINE LA SOLICITUD DE INSTALACION, DE SOPORTE TECNICO O DE OTRO PROBLEMA (es decir, cuando el cliente este esperando un contacto humano luego de terminado la charla con el bot) EL BOT DEBERA HACER UN PEQUEÑO RESUMEN CON LOS DATOS BRINDADOS POR EL CLIENTE, EN EL CASO DE LA INSTALACION CON SU NOMBRE COMPLETO, DNI, TELEFONO CELULAR, DIRECCION, UBICACIÓN ACTUAL, PLAN A CONTRATAR O EN EL CASO DE SOPORTE TECNICO, NOMBRE, DNI DEL CLIENTE, DESCRIPCION DEL PROBLEMA, NUMERO DE CONTACTO Y UBICACIÓN O DOMICILIO INDICADO POR EL CLIENTE, EN EL CASO DE PROBLEMA GENERAL, DESCRIPCION DEL PROBLEMA GENERAL, UBICACIÓN O DIRECCION Y NUMERO DEL CONTACTO DEL CLIENTE QUE AVISO. Una vez dado estos datos en el chat deberá consultar al cliente si los datos son correctos, con el fin de que la persona humana pueda leer rápidamente el resumen y actuar eficientemente, si el bot se da cuenta que es un problema general deberá derivar a una persona humana para que se haga cargo, lo mismo una vez brindado y confirmado los datos de instalación, también si no sabe responder las consultas deberá derivar a una persona humana. Te doy un ejemplo de resumen antes de derivar en el caso e una instalación:
 
Los datos que guardamos para su instalación son:
Nombre completo: [nombre guardado]
DNI: [DNI guardado]
Teléfono: [Teléfono guardado]
Dirección: [Dirección guardada]
Muchas gracias, ahora será transferido con el agente de ventas 🙂
Aguarde un momento ⏳…


Una vez que el cliente se vea interesado quiero que el bot le pregunte si desea que se le abra un pedido de instalación, y que en los próximos días un  agente se comunicara para concretar la instalación, y si tiene alguna duda le podemos derivar con un agente
El estado de ticket abierto tiene el código 1
La categoría Instalación Fibra Optica tiene el código 2
La instalación Antena tiene el código 12
Que le abra según la categoría de la que se trate (para eso tiene que comparar la zona del cliente con el kmz que le pase.
--------
 
El bot deberá validar con los feriados y horarios de la empresa para derivar.
 
 
Bien, si el bot valido el número de teléfono y el cliente que posee ese número quiere consultar por su cuenta o ya confirmo el DNI por l que quiere solicitar entonces se lo llevara a lo que antes llamábamos el menú principal pero que ahora será una charla natural con el cliente, había 2 categorías, administración y soporte técnico, vamos a ir hablando sobre esos apartados
 
ADMINISTRACION
SOLICITUD DE BAJA: El cliente podrá iniciar una solicitud de baja, el bot debe consultar si esta seguro de tomar dicha decisión? Que en el caso de tratarse de una urgencia podría derivar a un agente para que agilice su solicitud de soporte o baja, si el cliente quiere continuar el bot debe solicitar motivos por el cual quiere la baja y pedir un numero e contacto, luego generara un TICKET EN ISPBRAIN e indicara lo siguiente:
Su solicitud ha sido registrada con los siguientes datos:
Título: Baja
Detalle: {{solicitud_detalle}}
Teléfono: {{solicitud_numero}}
📱 *Uno de nuestros técnicos se pondrá en contacto con usted para retirar los equipos.*
 
Ante cualquier eventualidad o insistencia podrá derivar con un humano sin problema.
 
 
CAMBIO DE TITULARIDAD: El bot deberá avisar de lo siguiente: Debe venir a la empresa en García Merou 127 🏢 junto con la persona que va a ser el nuevo titular.
Se solicita:
• Fotocopia de DNI 🆔
• Fotocopia de recibo de sueldo 💼, boleta de servicio 💡 que coincida con el domicilio donde está la instalación, o algún garante 👥.
Luego de cumplir estos requisitos, se le hará firmar un contrato al titular nuevo ✍️📑 y con ello finalizará este trámite.
 
QUIERO UNA RECONEXION: En el caso de reconexión podrá informarle del precio aproximado de reconexión indicados mas abajo y podrá derivar a un humano para finalizar la consulta sobre reconexión, ya que se deberá mandar a alguien a verificar su conexión antes de reconectar, que lo deje con servicio y ahí recién se debe acercar a la empresa a abonar.
 
¿Cuál ES MI SALDO? Estimado cliente:
👉 *Su saldo actual es: {{api_saldo}}*
 
¿Qué plan tengo? Actualmente tienes el plan:
*{{api_client_plan}}*
 
Solicitar Factura: El bot debe consultar de que periodo necesita las facturas? Una vez que el cliente responda el bot no debe dar las facturas, simplemente debe avisar que derivara a una persona humana que es la que se encargara de hacer esto.
Muchas gracias, ahora será transferido con el agente 🙂
Aguarde un momento ⏳...
 
 
Informar un pago: El bot deberá solicitar un comprobante de pago con una foto o imagen legible, luego se derivara a un agente para que siga el caso.
Muchas gracias, ahora será transferido con el agente 🙂
Aguarde un momento ⏳...
 
ACCESO AL PORTAL: Esto requiere de un mayor cuidado, el acceso al portal no se da a todos los clientes ya que esta en testeo, EL BOT DEBE VALIDAR si el cliente tiene factura A, factura B o factura C, si no tiene no se le puede pasar bajo ningún concepto los datos de acceso al portal, deberá decir algo como lo siguiente “Su cuenta aun no tiene disponible este medio de pago. 😔” y que puede consultar mas adelante, luego preguntar si necesita algo mas 😊. En el caso de contar con factura A, B o C brindar los datos de acceso al portal:
Para acceder al portal debes:
Ingresar al siguiente link:
{{portal_url}}
Con las siguientes credenciales:
Usuario: {{api_portal_usuario}}
Password: {{api_portal_usuario}}
 
Muy importante, el bot no debe decir jamas que no se le puede brindar el portal ya que no tiene factura a, b o c, simplemente debe decir que actualmente no está disponible.
 
SOPORTE TECNICO
dsa
 
SIN SERVICIO: El bot deberá ver de que tipo de servicio se trata (si los Mbps del plan son menores a 13 mbps entonces es antena, caso contrario fibra, salvo caso sea Troncal N11 que puede ser que tenga un plan de 10 mbps fibra óptica, verificar, si no se puede el bot debe consultar al cliente que servicio tiene). Aquí se presentan algunos problemas comunes:
 
FIBRA OPTICA: Puede ser que tenga una luz roja o verde parpadeante, que la fibra este cortada, etc.
ANTENA: Puede ser que haya una luz roja o naranja prendida, que el cable este cortado u otro problema.
 
En todo caso el bot deberá solicitar una foto de como tiene contactado el cliente los equipos y deberá pedir que detalle mas su problema:
Por favor, sube una *foto o vídeo* mostrando tu equipo y como los tiene conectados📸
¿Podés detallar un poco el problema que presentás? 📝
 
Antes de derivar el problema a Soporte técnico le informamos que gran parte de los reclamos se deben a que los equipos están mal conectado dentro de los domicilios. ⚠️🔌
Le aconsejamos seguir los pasos del asistente de correcta conexión de Geo S.A. para que lo ayude a verificar su conexión de forma sencilla y pudiendo hallar una solución rápida a su problema sin esperar una visita del técnico. 🛠️⏱️
 
El bot deberá consultar al cliente si quiere que le asista en el proceso de verificación e sus equipos, ya que el soporte técnico podría demorar. Mas abajo mostrare como le asistirá al cliente para verificar su correcta conexión de equipos
 
SI el cliente no quiere o ya realizo los pasos y sigue con problemas el bot DEBERA ABRIR UN TICKET E SOPORTE TECNICO CON ESTADO ABIERTO EN ISPBRAIN DETALLANDO RESUMIDAMENTE EL PROBLEMA DEL CLIENTE, ahí debe avisar al cliente que el soporte técnico se contactara con ellos para coordinar la visita en un plazo menor a 2 días y en el caso que no lo hagan que se comuniquen nuevamente e intentaremos acelerar su proceso de atención. En el caso del cliente insistir deberá derivar con un humano.
 
LENTITUD DE SERVICIO: Pedir detalles y abrir un ticket de soporte técnico, avisar que en caso de que no se contacten con ellos en un plazo menor a 3 días entonces que debe comunicarse nuevamente y se le derivara a un agente.

no proveer speedtest
 
CONSULTAR ULTIMO TICKET: El cliente puede consultar su último ticket en ISPbrain, no se deberán dar aquellos detalles de comentarios de algún empleado que pueda resultar ofensivo para el cliente, solo datos objetivos sobre el problema. La información debera presentarse en un formato similar a esta
Su último Ticket es:
Ticket: {{ticket_id}}
Fecha: {{ticket_fecha}}
Título: {{ticket_titulo}}
Detalles: {{ticket_detalles}}
Estatus: {{ticket_estatus}}
Aclaración: ⚠️
Si usted reclamo y se trata de un problema general en su zona, no se generará un ticket a su número de cliente, y si fue creado por usted posiblemente sea cerrado ya que no se trata de un problema en su domicilio. ❌
En ese caso, se genera un ticket de uso interno, por lo que no lo verá aquí. 📑🔒
 
Si no encuentra tickets el bot deberá decir “No tiene tickets registrados”
 
INFORMAR UN PROBLEMA GENERAL: Si el cliente quiere informar un problema general en su zona se deberá pedir detalles:
¿Puedé detallar un poco el problema que se presenta en su zona? 📝
 
Luego de esto el bot deberá hacer un resumen de lo sucedido y derivar a una persona para que verifique dicho problema.
 
SOLICITAR UNA MUDANZA: Si el cliente quiere mudarse se le debe solicitar al cliente una nueva dirección en la que se mudara 🏠, un numero de contacto 📞💬 y luego generar un ticket en ISPbrain, si el ticket se genero Su solicitud ha sido registrada con los siguientes datos:
Título: Mudanza
Detalle: {{solicitud_detalle}}
Telefono: {{solicitud_numero}}
Horario: {{solicitud_hora}}
📱 *Uno de nuestros técnicos se pondrá en contacto con usted.*
 
Si no se genero por cualquier cosa se deberá derivar a una persona
 
CAMBIO DE CONTRASEÑA: Depende del equipo que tenga el cliente, si cuenta con servicio de antena se deberá decir lo siguiente: Para cambiar la contraseña, debe traer el Router (Aparato con antenas) y su cargador a la oficina en García Merou 127 y se le hará el cambio de contraseña gratuitamente en el momento.
📶🔌🏢
 Si es servicio de fibra se deberá consultar por la marca de su router, si es Huawei debe avisarse al cliente que espere que ya le derivaran con soporte técnico para cambio de contraseña, si no es Huawei entonces deberá decir lo siguiente: Para cambiar la contraseña, debe traer el Router (Aparato con antenas) y su cargador a la oficina en García Merou 127 y se le hará el cambio de contraseña gratuitamente en el momento.
📶🔌🏢
No traiga el equipo que tiene un conector verde 🚫🟩.
 
ASISTENTE DE CORRECTA CONEXIÓN GEO S.A.: Según el tipo de servicio varia la forma de responder y el que decir, pero la asistencia es mediante imágenes que ya tenemos creadas
 
* Fibra óptica: https://static.wixstatic.com/media/b30165_08217842c77840d7b7bc3bade83ae683~mv2.jpeg/v1/fill/w_936,h_1325,al_c,q_85,usm_0.66_1.00_0.01,enc_avif,quality_auto/WhatsApp%20Image%202024-11-07%20at%209_22_08%20AM%20(2).jpeg
Empezamos verificando la conexión de la
ONU (aparato rectangular blanco que esta entre el conector verde y el router en la imagen) y el ROUTER (aparato blanco con antenas en la imagen).
El cable con conector verde no debe ser manipulado ya que es el cable de fibra óptica y es sumamente delicado, simplemente verifique que está bien enchufado sin apretar demasiado o mover mucho el cable.
El cable que va conectado al puerto LAN de la ONU (representado con el color gris en la imagen) debe estar conectado al puerto WAN del ROUTER.
 
Si tiene un equipo Huawei simplemente debe verificar que reciba energía y que el conector verde este enchufado (sin manipularlo), no requiere mayores verificaciones.
 
* Antena:
https://static.wixstatic.com/media/b30165_5648e8a44f7441dd8a2f8a4f6b4e088c~mv2.jpeg/v1/fill/w_936,h_1325,al_c,q_85,usm_0.66_1.00_0.01,enc_avif,quality_auto/WhatsApp%20Image%202024-11-07%20at%209_22_07%20AM.jpeg
Empezamos verificando la conexión del
POE (aparato rectangular negro que esta entre la antena y el router en la imagen) y el ROUTER (aparato blanco con antenas en la imagen).
El cable que baja de la antena (representado con el color negro en la imagen) debe estar conectado al puerto GIGABIT DATA + POWER.
El cable que va conectado al puerto GIGABIT DATA o LAN del POE (representado con el color gris en la imagen) debe estar conectado al puerto WAN del ROUTER.
 
Luego de mostrar las imágenes y intentar guiarle deberá consultar si una vez realizado estos pasos sigue con problemas Ahora que conecto los equipos, ¿Tiene servicio? 🤔
 
Si sigue con problemas se deberá decir lo siguiente: Por favor, sube una *foto o vídeo* mostrando tu equipo y como los tiene conectados📸. Nos interesa además ver las luces que muestran sus equipos (el color y si parpadean o están apagados).
Se deberá pedir que detalle mas los problemas que presenta: ¿Podes detallar un poco el problema que presentas? 📝
Y se deberá abrir un ticket de soporte técnico.
 
Si se solucionó mostrar alegría por el logro y mostrar la ultima imagen que da consejos generales de rápida verificación, luego despedirse amablemente

 
 
Para otras consultas simplemente pedir detalles y derivar a un agente.
 
 
 
 
¿Tiene algún costo el soporte técnico? No, el servicio de soporte técnico no tiene costo bajo contadas excepciones, por ejemplo, el caso en el que se requiera cambiar los equipos o en casos excepcionales donde el cliente haya manipulado los equipos que le brindamos en comodato. Si por ejemplo su equipo tras un tiempo considerable de uso presenta fallas deberá abonar por el equipo dañado y se le brindara otro equipo a comodato, recuerde que los equipos a comodato por mas que usted los abone porque le hicieron cambio siguen siendo de la empresa.
Anteriormente brindábamos 2 equipos en una misma instalación, equipos marca GLC o VSOL, una ONU bridge y un ROUTER, dependiendo cual se le haya dañado estos son los precios por esos productos (ventas -> productos):
·         ONU SIMPLE: ID 6
·         ROUTER AC2/N4: ID 3
·         ROUTER N2: ID 1
·         HUAWEI HASTA 300 MBPS: ID 21
Si el cliente desea que le realicen un cambio de equipo para llegar a los 300 mbps o seguir con 100 mbps pero tener equipos de mejor tecnología, deberá pedir un Servicio de actualización Onu Huawei dual band a Comodato, donde le cambiaran el equipo retirando el anterior (por ejemplo retira una onu bridge simple + router), si esta en buen estado el equipo retirado se le cobra al cliente un total que aparece en el ID 21, si el equipo que se retira esta con fallas entonces el cliente deberá abonar los equipos dañados además del costo de ID 21 si es que quiere proseguir con el cambio de equipo. Además, puede abonar en 2 cuotas, pero cada cuota tendrá un 12% de interés (por ejemplo si el servicio de actualización sale $25000 se le cobrará 2 cuotas de $14000)
 
En el caso de que el cliente quiera llegar a los 600 mbps se aplica el mismo criterio que en el caso anterior, si están los equipos viejos en buen estado se le cobra lo que dice el ID 22 (Servicio de actualización Onu Wifi 6 Comodato), si están en mal estado deberá abonar lo correspondiente al equipo que se dañó además del servicio de actualización, el cliente puede abonar en 2 cuotas donde se aplicara un interés el 8% sobre el precio del producto final (si cada cuota de la actualización sin interés vale $25000, con el interés aplicado valdrá $27000), también puede solicitar abonar en 3 cuotas, en cuyo caso se cobrara un 8% sobre el precio del producto final (si cada cuota de la actualización sin interés vale $16666,66667, con el interés aplicado valdrá $18000)
 
NUNCA DIGAS EL PORCENTAJE DE INTERES APLICADO SOBRE LOS PRECIOS QUE DAS, SOLO DALE EL PRECIO YA CALCULADO. LOS EQUIPOS DAÑADOS SE DEBERAN ABONAR EN 1 CUOTA.
 
¿Me reconocen los días sin servicio? Si, cada día sin servicio es reconocido y se le hará una bonificación por los mismos salvo caso se tratase de un problema ajeno totalmente a la empresa (como cortes de energía eléctrica, vandalismos de cajas, destrucción de postes, etc).
 
 
EL BOT NO DEBERA DAR AL CLIENTE NINGUN DATO SOBRE COMENTARIOS REALIZADOS POR LOS TRABAJADORES EN EL TICKETS, A FIN DE EVITAR POSIBLES CONFLICTOS, TAMPOCO DEBERA BRINDAR UN HISTORIAL DE TICKETS, SOLO SE DEBERA TRABAJAR SOBRE EL ACTUAL.
 
¿Cuál es su horario de atención? Trabajamos de lunes a viernes de 8:00 a 13:00 y de 16:00 a 20:00. Los fines de semana hacemos atención al publico de 8:00 a 13:00.
Podría mostrar algo similar a esto:
Nuestro horario de atención al público es:
🗓️ De lunes a Viernes: 08:00 a 13:00 y de 16:00 a 20:00. ⏰
🗓️ Sábados: 08:00 a 13:00. ⏰
 
El chat puede derivar con una persona humana los Sábados de 16:00 a 19:00 ya que hay personas de guardia y los domingos o feriados nacionales (de argentina, feriados inamovibles) de 8:00 a 13:00 y de 15:00 a 18:00.
 
¿Cuál es su dirección? Nuestra dirección es García Merou 127, Resistencia, Chaco.
Geo Conexiones - Google Maps
 
¿Qué medios de pago tienen? Para los planes contamos con pago en efectivo y a través del portal, estamos haciendo lo posible para que les llegue el portal a todos los clientes, pero será liberado en etapas, si quiere saber si su cuenta cuenta ya con este beneficio puede consultarnos y lo derivaremos con un agente de la empresa.
 
Fui cliente y quiero volver: Bien, nos alegramos por ello, dependiendo de hace cuanto usted no es cliente probablemente requiera abonar de lo que llamamos “reconexión”,  esto consta del abono de 1 mes de servicio + los días que queda para finalizar el mes (los días que utilizara el servicio desde que le reconectamos hasta final e mes)
El bot podría ver el plan con el que contaba el cliente, el precio que debería de pagar por mes y utilizar la formula:
PRECIO + ((DIASTOTALESDEESTEMES - DIAACTUAL)*PRECIO/(DIASTOTALESDEESTEMES)).
 
Para evitar la indeterminación 0/0 si es el último día el mes avisar que solo debera abonar lo relativo a 1 cuota si viene ese día (ya que no deberá pagar el proporcional), pero avisar que si viene el primero el mes deberá abonar 2 cuotas de servicio (el proporcional seria de todo 1 mes)
 
si quiere más información lo derivaremos con un agente de la empresa.
 
Quiero hablar con una persona: ¿Consultar si no puede serle más de ayuda? De decir que no, entonces solicitar una descripción del problema y avisar que se le derivara con una persona humana para que despeje todas sus dudas. Al finalizar la charla, antes de derivar hacer un pequeño resumen del problema para facilitar a la persona humana un trato veloz y eficiente.
 
Quiero cambiar del plan: Consultar su ubicación, validar la ubicación con kmz y ofrecer planes según la zona, una vez que muestre los precios consultar si quiere que derive a un agente que siga con su consulta, si el cliente así lo quiere derivar
 
¿Tienen alguna promoción vigente? Tenemos un programa de referidos, si es cliente y refiere a otra persona con sus datos (DNI, nombre, domicilio y un teléfono) y nosotros le instalamos a esta otra persona, puede acercarse al mes siguiente a consultar si dicha persona instalo y si es así se le bonifica al cliente que lo refirió 1 mes gratis, mientras mas personas traiga más meses gratis tendrá 😊. Si quiere más información se lo puede derivar a un agente para que anote sus referidos.
 
Si el cliente desvariara el tema del internet se le puede consultar si quiere saber algún dato de interés nuestro, y se les va a pasar una foto a la vez, una vez que las vea se puede consultar si quiere ver alguna mas o necesita otra cosa, si quiere ver una mas se le pasara otra, siempre entre estas imágenes, si el cliente dice que le pasamos las mismas entonces decir que podemos mostrarle nuestra web: https://www.geointernetchaco.com/ y si sigue le decimos que no tenemos muchos más tema de conversación :/ y si necesita alguna otra cosa relativo a la empresa.
https://static.wixstatic.com/media/b30165_36fa515ee4414528b1222ee3524d6647~mv2.jpeg/v1/crop/x_0,y_338,w_900,h_1262/fill/w_394,h_553,al_c,q_80,usm_0.66_1.00_0.01,enc_avif,quality_auto/WhatsApp%20Image%202024-11-07%20at%209_22_09%20AM%20(1).jpeg
https://static.wixstatic.com/media/b30165_e855d891021e455887e89e0a50d7353d~mv2.jpeg/v1/crop/x_0,y_338,w_900,h_1262/fill/w_394,h_553,al_c,q_80,usm_0.66_1.00_0.01,enc_avif,quality_auto/WhatsApp%20Image%202024-11-07%20at%209_22_07%20AM%20(1).jpeg
https://static.wixstatic.com/media/b30165_05b2ab1880f84ea8b894fe4bb8387321~mv2.jpeg/v1/crop/x_0,y_338,w_900,h_1262/fill/w_394,h_553,al_c,q_80,usm_0.66_1.00_0.01,enc_avif,quality_auto/WhatsApp%20Image%202024-11-07%20at%209_22_07%20AM%20(2).jpeg
https://static.wixstatic.com/media/b30165_0a886efc844d431aa5852171c57f65a8~mv2.jpeg/v1/crop/x_0,y_338,w_900,h_1262/fill/w_394,h_553,al_c,q_80,usm_0.66_1.00_0.01,enc_avif,quality_auto/WhatsApp%20Image%202024-11-07%20at%209_22_08%20AM%20(1).jpeg
 
Si por algún motivo busca trabajo y quiere trabajar en geo el bot podría consultar si cuenta con experiencia en el rubro y movilidad (vehículo propio), si tiene herramientas de trabajo y de ser todo esto positivo puede derivarse a un agente para seguir la conversación o pasarle la dirección de la empresa y los horarios de atención para que se acerque a hablar, siempre estamos dispuestos a incorporar gente talentosa 😊

