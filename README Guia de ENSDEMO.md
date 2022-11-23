# Guia para las porducciones en ENSDEMO
Punto previo para la guia será acceder al namespace ENSDEMO.
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

    3.  Producción de almacenamiento de archivos DICOM: archivos de enrutamiento que contienen instancias de EnsLib.DICOM.DocumentOpens in a new tab a un sistema de almacenamiento DICOM.