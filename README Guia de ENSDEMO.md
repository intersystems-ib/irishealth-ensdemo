# Guia para las porducciones en ENSDEMO
Punto previo para la guia será acceder al namespace ENSDEMO.

InterSystems IRIS (for Health) o HealthShare Health Connect permite que solo se ejecute una producción en un espacio de nombres dado en un momento dado.

Una producción en ejecución continúa ejecutándose incluso cuando cierra el Portal de administración.


## Inventario de producciones de ejemplo
Para acceder a cualquier de las producciones ejemplo disponibles habrá que ir a Interoperabilidad -> Configurar -> Producción, en la pastaña Acciones ir a Abrir y seleccionar la producción deseada.

### Demo.HL7.MsgRouter.Production
Enruta los mensajes HL7 en función del origen y el contenido del mensaje. Para obtener más información, haga clic en ABC_Router o XYZ_Router. Haga clic en Ver reglas para ver las reglas de enrutamiento de mensajes. La producción utiliza un proceso de enrutamiento Ens.Alert para enrutar alertas. La regla en Ens.Alert consulta una tabla de búsqueda para ver dónde enviar la alerta. Para demostrar las alertas, asigne a EMailAlertOperation un servidor STMP y un Destinatario válidos. También puede editar la tabla de búsqueda de AlertTable. Asigne temporalmente una ruta de archivo incorrecta a un servicio de archivos habilitado.

### Demo.ComplexMap.SemesterProduction
Muestra de Producción para ilustrar el uso de Mapas Complejos. NOTA: El archivo de origen, ComplexMap_Semester_Data.txt, así como los archivos de salida de muestra, deben ubicarse en [install_dir]/dev/ComplexMap/.

### Demo.Dashboard.Production
En esta producción tenemos un ejemplo de una clase de métrica empresarial. Define un conjunto de propiedades de métricas comerciales (también conocidas como KPI - indicadores clave de rendimiento) y proporciona el código para calcular periódicamente sus valores. Estas métricas luego se pueden mostrar dentro de un cuadro de Mando en la plataforma.

### Demo.DICOM.Production.*
Producción de lista de trabajo de modalidad DICOM: preparación de la información para precargar datos de pacientes y programación en una modalidad, por ejemplo, una máquina de rayos X.
Producciones de Enrutamiento (sync/async) DICOM a producción de almacenamiento: enrutamiento de mensajes que contienen imágenes al punto final adecuado, por ejemplo, un sistema PACS.
Producciones de almacenamiento de archivos DICOM: archivos de enrutamiento que contienen instancias de EnsLib.DICOM.DocumentOpens a un sistema de almacenamiento DICOM.

### Demo.FloodMonitor.Production
Producción con ejemplo de uso de Business Process customizado.

### Demo.HL7v3.Production.InterfaceEngine
Enruta y transforma los mensajes HL7v3 en función del contenido.

### Demo.Loan.BankUSProduction
Producción que orquesta multiples sistemas y correspondientes llamadas. Tiene ejemplos de processos de largo recorrido.

### Demo.Loan.FindRateProduction
Producción que orquesta multiples sistemas y correspondientes llamadas. Contiene elementos para interactuar con distintas tecnologias/endpoints - servicios web, email, ficheros, MQSeries, MSMQ...

### Demo.RecordMap.Production
Producción de ejemplo para ilustrar una transformación de entrada/salida simple usando RecordMaps generados. 
NOTA: El archivo de origen, RecordMap.Delimited.Input.txt, y un archivo de salida de muestra, RecordMap.Delimited.Output.txt, deben ubicarse en [install_dir]/dev/RecordMap/.

### Demo.RecordMapBatch.Production
Ejemplo de producción para ilustrar una transformación de entrada/salida utilizando lotes de Record Map. El lote de entrada contiene datos sobre los tiempos de llegada y los tiempos de llegada esperados de los trenes. El lote de salida filtra para incluir solo las horas de llegada reales y reformatea los datos. MassDOT proporciona estos datos en http://developer.mbta.com/Data/Red.txt. 
NOTA: El archivo de origen, TrainDataIn_Sample.txt y un archivo de salida de muestra, TrainDataOut_Sample.txt, se encuentran en [install_dir]/dev/RecordMapBatch/.

### Demo.REST.Production
Ejemplo de producción para ilustrar una integración basada en APIs REST - presentación y consumo de estas APIs.

### Demo.SAP.Production.Minimal
Conectividad SAP a través de SAPJCo. Compatibilidad con SAPJCo 3.07+

### Demo.Workflow.Production
Ejemplo de producción para la demostración de flujo de trabajo. Reproduce un flujo de HelpDesk.

### Demo.X12.*
Enruta, procesa y transforma los mensajes X12 en función del contenido.

## Gestión de la información

### Soporte nativo para los estándares
Acceder a Interoperabilidad -> Interoperar y podremos comprobar los estándares disponibles.  De manera resumida tenemos:
1. ASC X12
    - Ver, importar y eliminar esquemas X12; ver y transformar documentos X12
2. ASTM
    - Ver, importar y eliminar esquemas de ASTM; ver y transformar documentos ASTM 
3. DICOM
    - Crear, ver o editar asociaciones DICOM; visualizar sintaxis DICOM abstracta; ver diccionario DICOM 
4. HL7 v2.x
    - Ver, importar y eliminar esquemas HL7 v2.x; ver y transformar documentos HL7 v2.x
5. UN/EDIFACT
    - Ver, importar y eliminar esquemas EDIFACT; ver y transformar documentos EDIFACT
Accediendo al menú Health podremos comprobar el soporte a FHIR y IHE.

### Generación de mensajes concretos en base a reglas y a la información disponible en la Plataforma de Integración.
Arrancar la producción ... Para ello, acceder a Interoperabilidad -> Configurar -> Producción, sobre la pestaña Acciones (mano derecha), ir a Abrir - Demo -> HL7 -> MsgRouter -> Producción. Tenemos 2 enrutadores de mensajería: ABC_Router y XYZ_Router. Podemos seleccionar el XYZ_Router y acceder a la propiedad Regla de Negocio - dándole a la lupa. Podemos ver las reglas definidas y las transformaciones realizadas. 

### Búsquedas de mensajes concretos sobre consultas de datos específicos contenidos en el mensaje.
La búsqueda de mensajes se hace desde Interoperabilidad -> Vista -> Mensajes. En este menú tenemos disponibles los criterios de búsqueda. Permite también la visualización de los mensajes.

### Visualización y comparación de mensajes.
Además del visor de mensajería los mensajes se pueden ver también desde Interoperabilidad -> Interoperar -> HL7v2.x -> Visor de Mensajes HL7v2.x. En esta pantalla se pueden definir una comparación entre mensajes, aplicar una transformación a um mensaje dado y comprobar el resultado y, incluso, guardarlo en disco. 

### Validación de mensajes (detección de mensajes incorrectos)
Los mensajes HL7v2.x en concreto se pueden validar mediante configuración. En el enrutador de mensajería podemos definir el parámetro Validación que especifica los tipos de Validación a realizar. Defínelo en 1 para bloquear documentos que no superen la validación predeterminada. La validación predeterminada requiere un DocType, permite mensajes con segmentos Z no asignados y bloquea mensajes con cualquier otro error encontrado al asignar la secuencia de segmentos del documento utilizando la estructura de esquema HL7 especificada por el DocType del documento. Esto es equivalente a 'dm-z'.
(La '-z' significa 'lo opuesto a z', es decir, tolera segmentos Z finales no reconocidos, que es el comportamiento habitual de HL7). Sobre la cadena Validación podremos ver todos los valores posibles para este parámetro.

### Enrutamiento específico para los estándares que permita crear reglas en función de estructuras o datos específicos de los estándares.
En la producción MsgRouter tenemos el enrutador XYZ_Router donde tenemos a una regla de negocio Demo.HL7.MsgRouter.XYZRoutingRule - a la que podemos acceder mediante la lupa al en Regla de Negocio. En esta regla tenemos ejemplos de parseo del contenido de mensajería HL7 y mediante el contenido hay un flujo de decision. 

### Transformación de los mensajes HL7 tanto sintáctica como semánticamente a través de asistentes que faciliten el proceso.
La definición de las transformaciones se hace desde Interoperabilidad -> Generar -> Transformación de datos. En Demo -> HL7 -> MsgRouter tenemos 3 transformaciones de datos cambiando de un objeto a otro. En la transformación EmailAlertTransform se usa una Tabla de Búsqueda, lo que sería el mecanismo idóneo para el mapeo de sistemas de codificación (semántica). 
### El sistema deberá de implementar funcionalidades BI que permitan entre otros:
1.  La posibilidad de elaboración de informes de manera sencilla relativos al funcionamiento y al estado del sistema implantado
    - System Alerting and Monitoring (SAM) proporciona una solución de monitoreo para instancias de la plataforma. Ya sea que su aplicación se ejecute en un mirror local o en la nube con múltiples aplicaciones y servidores de datos, puede usar SAM para monitorear sus instancias de InterSystems IRIS.
2.  El desarrollo de métricas y cuadros de mando
    - SAM permite extender las métricas disponibles y crear las que se puedan requerir.

### Debe permitir el acceso a la información correspondiente a las transacciones ocurridas a través de conexiones nativas.
Todos los eventos de conexión de una producción de integración dejan traza en el log de eventos. Este es el comportamiento por defecto de la plataforma. Para acceder a ello: Interoperabilidad -> Vista -> Log de eventos. Se permiten filtros de busqueda basados en los criterios disponibles. 

### Deberá de permitir la gestión de colas
La página Interoperabilidad > Monitor > Colas muestra el estado actual de todas las colas de mensajes que utiliza la producción en ejecución en el namespace seleccionado. Para ver el contenido de cualquier cola dada, seleccione la fila para esa cola. Se muestran los mensajes activos y el contenido de la cola para esa cola. Si selecciona una entrada en el contenido de la cola o mensajes activos, se muestra información sobre el mensaje.

### Debe permitir el manejo de mensajería síncrona/asíncrona en general y HL7 y DICOM en particular, permitiendo convertir los mensajes en objetos a los que poder asignar métodos, eventos, etc.
Los productos de InterSystems admiten mensajes HL7v2.x como documentos virtuales. Un documento virtual es un tipo de mensaje que los productos de InterSystems analizan solo parcialmente. Este tipo de mensaje tiene el encabezado de mensaje de producción estándar y las propiedades de mensaje estándar, como ID, Prioridad y SessionId. Sin embargo, los datos del mensaje no están disponibles como propiedades del mensaje; en cambio, se almacena directamente en un global de uso interno, para una mayor velocidad de procesamiento. Para acceder a una producción HL7 ir a Interoperabilidad -> Configurar -> Producción y abrir Demo.HL7.MsgRouter.Production. 
Digital Imaging and Communications in Medicine (DICOM) es un estándar mundial de tecnología de la información que se utiliza en la mayoría de los hospitales del mundo. Está diseñado para garantizar la interoperabilidad de los sistemas utilizados para producir, almacenar, mostrar, procesar, enviar, recuperar, consultar o imprimir imágenes médicas y documentos estructurados derivados, así como para gestionar el flujo de trabajo relacionado.
Se proporcionarán producciones de muestra:
    1.  Producción de lista de trabajo de modalidad DICOM: preparación de la información para precargar datos de pacientes y programación en una modalidad, por ejemplo, una máquina de rayos X.

    2.  Enrutamiento DICOM a producción de almacenamiento: enrutamiento de mensajes que contienen imágenes al punto final adecuado, por ejemplo, un sistema PACS.

    3.  Producción de almacenamiento de archivos DICOM: archivos de enrutamiento que contienen instancias de EnsLib.DICOM.DocumentOpens a un sistema de almacenamiento DICOM.

## Conectividad

### Deberá de garantizar la conectividad de manera síncrona o asíncrona (dependiendo de la necesidad de integración) entre los distintos elementos que compondrán el ecosistema de la red sanitaria.
En la producción Demo.FloodMonitor.Production hay multiples ejemplos de conectividad síncrona y asíncrona. En todas las demás producciones hay ejemplos de ambos casos de uso.

### Los adaptadores deben de poder funcionar sobre diversos mecanismos de conexión. Al menos deberán de permitirse: HTTP/HTTPS, SMTP/MIME, FTP/SFTP, TCP/MLLP, File, POP3/MIME, JMS, y LDAP.
En todas las producciones hay ejemplos de uso de estos y otros adaptadores. En cualquier caso, para crear un nuevo componente HL7 usando qualquier de estos adaptadores no se necesita desarrollo - es solamente cofiguración. Para ello ir a la producción Demo.HL7.MsgRouter.Production, en Servicios/Operaciones elegir entrada/salida HL7 y seleccionar el adaptador que proceda. 

### La plataforma deberá permitir incorporar adaptadores para paquetes SW tipo ERP (SAP o similares)
Esto es algo soportado. El recurso idoneo para buscar este tipo de recurso sería la ![comunidad de dessarroladores] (https://es.community.intersystems.com/)

### Deberá soportar servicios web pudiendo actuar como proveedor o como cliente de un servicio web. Deberá soportar diferentes modos de implementación de estos servicios (SOAP, REST, ...)
Hay ejemplos de servicios SOAP y RESTE en distintas producciones. En Demo.Loan.FindRateProduction, en Demo.REST.Production, en Demo.HL7v3.Production.InterfaceEngine y otras hay ejemplos de los distintos casos de uso.

## Coordinación, gestión y monitorización

### Deberá de contar con un sistema de generación automática de alertas para permitir la identificación de situaciones anómalas de manera temprana.
La producción Demo.HL7.MsgRouter.Production utiliza un proceso de enrutamiento Ens.Alert para enrutar alertas. La regla en Ens.Alert consulta una tabla de búsqueda para ver dónde enviar la alerta. Se podrá tabién configurar el control de alertas en cada componente (servicio u operación) para ello habrá que acceder al control de alertas y configurar; Alerta de recuento de cola o Alerta de espera en cola para las operaciones; Tiempo de espera para inactividad para los servicios. 

### La plataforma debe disponer de una capa de coordinación que controlará las acciones que se producen en una integración mientras se está ejecutando.
Una producción es un paquete especializado de software y documentación que integra múltiples sistemas de software potencialmente dispares. Una producción incluye elementos que se comunican con estos sistemas externos, así como elementos que realizan un procesamiento interno a la producción.
Una producción consta de varios componentes que se comunican entre sí (y con sistemas externos). Hay tres tipos distintos de host comercial:
    1. Servicio, recibe información desde fuera de la producción.
    2. Proceso, es responsable de la comunicación y la lógica que está completamente dentro de la producción.
    3. Operación, generalmente envía resultados desde la producción. Las operaciones también se pueden utilizar para la comunicación y la lógica dentro de una producción determinada.
Dentro de una producción, toda la comunicación se realiza mediante mensajes de solicitud y respuesta entre los anfitriones comerciales.
En el menú Interoperabilidad -> Monitor tenemos las principales tareas de control de una producción.
### Deberá de ofrecer funcionalidades de monitorización en tiempo real tanto de la plataforma en su conjunto como de los distintos procesos de negoció implementados.
System Alerting and Monitoring (SAM) proporciona una solución de monitoreo para instancias de la plataforma. 
Para control y seguimiento de los distintos processos de negócio implantados tenemos el Monitor (en Interoperabilidad -> Monitor y en Interoperabilidad -> Gestionar).
### La plataforma permitirá tanto la implantación como el seguimiento de políticas y niveles de servicio que faciliten la mejora continua de la infraestructura
Se pueden definir los cuadros de mando que procedan de manera a controlar los niveles de servicio. Ejemplo de ello sería la producción Demo.Dashboard.Production.
### Deberá de aportar un conjunto de herramientas que permitan el desarrollo de la lógica de enrutamiento a través de interfaces gráficas, sin necesidades de lenguajes de programación.
En la producción Demo.HL7.MsgRouter.Production hay 2 enrutadores de mensajería ABC_Router y XYZ_Router. En cualquier de ellos es posible ver la interfaz grafica que permite definir reglas de negocio y su aplicacion en tiempo de ejecución - sin parada.

### La plataforma deberá incorporar funcionalidades de gestión y administración de la propia plataforma y de las integraciones realizadas.
System Alerting and Monitoring (SAM) proporciona una solución de monitoreo para instancias de la plataforma. 
Para control y seguimiento de los distintos processos de negócio implantados tenemos el Monitor (en Interoperabilidad -> Monitor y en Interoperabilidad -> Gestionar). En Interoperabilidad -> Monitor tenemos los distintos logs permitidos por defecto.

## Orquestación

### La plataforma deberá de permitir la definición de procesos y reglas de negocio a través de una interface gráfica.

### Deberá de permitir la gestión de manera centralizada de todos los aspectos relacionados con la API de comunicaciones hacia/desde el exterior (monitorización del tráfico, identificación de problemas potenciales, gestión de IPs y dominios permitidos, etc).

### El sistema debe de incorporar un Gestor de Procesos de Negocio (BPM) que permita la gestión del estado de los procesos en ejecución.

### La plataforma incorporará un motor de flujos de trabajo o workflow, a través de interfaces gráficas de manera integrada. Este motor permitirá la gestión de los usuarios y roles intervinientes en los procesos.

### El Sistema debe de tener la capacidad de implementar el procesamiento de interfaces con terceros, como puede ser el procesamiento de ficheros de movimientos, facturas, entre otros.

## Desarrollo

### El sistema debe de tener la capacidad de realizar desarrollos basados en el paradigma de la orientación a objetos.

### El sistema debe de permitir la integración con alguna herramienta que permita el control de las versiones del código implementado (SVN, GIT, etc).
En este propio repositorio GIT lo estamos integrando con la plataforma.
### La plantaforma debe disponer de capacidad de desarrollo en diferentes lenguajes de programación no propietarios a través de algún IDE que asista en el diseño y en la construcción de los artefactos (Eclipse, Visual Studio, etc...).
En este repositorio estamos sugeriendo el uso de VSCode con las necesarios extensiones para integrar con la plataforma.

## Almacenamiento

### La gestión de almacenamiento de la plataforma deberá de ofrecer independencia en el alojamiento físico respecto a la aplicación.

### Deberá proporcionar la persistencia de mensajes, la recuperación de información transaccional en caso de caída del sistema, el registro y trazabilidad de mensajes para el análisis de los mismos.

## Seguridad

### Deberá permitir la aplicación de políticas de seguridad (autenticación y autorización) de forma centralizada y desacoplada de las aplicaciones y el BackEnd.

### La seguridad de las comunicaciones deberá garantizarse permitiendo las tareas de autenticación, autorización y cifrado utilizando estándares de seguridad como SSL y/o certificados digitales.

### La plataforma deberá de ser capaz de ofrecer un conjunto de servicios de cifrado y descifrado de mensajes.

























