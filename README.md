# InterSystems IRIS for Health ENSDEMO

Configuración básica del contenido de ENSDEMO en InterSystems IRIS for Health.

## DEMO

[![Demo](https://img.shields.io/badge/Demo%20on-Cloud%20Run%20Deploy-F4A460)](https://irishealth-ensdemo.demo.community.intersystems.com/csp/healthshare/ensdemo/EnsPortal.Productions.zen?$NAMESPACE=ENSDEMO&$NAMESPACE=ENSDEMO)

[![Quality Gate Status](https://community.objectscriptquality.com/api/project_badges/measure?project=OneLastTry%2Firishealth-ensdemo&metric=alert_status)](https://community.objectscriptquality.com/dashboard?id=OneLastTry%2Firishealth-ensdemo)

## Configuración

**Asegúrate de tener Docker en funcionamiento antes de comenzar.**

Clone el repositorio `git clone https://github.com/intersystems-ib/irishealth-ensdemo.git` y luego ejecútelo desde el directorio principal `docker-compose build`.

### Ejecución

Una vez que se complete la compilación, desde el directorio principal, inicie su contenedor de iris:

- **arranque el contenedor:** `docker-compose up -d`

### Ejecute su contenedor

Después de construir la imagen, simplemente puede ejecutar a continuación y estará en funcionamiento 🚀:

*-d ejecutará el contenedor separado de su sesión de línea de comando*

```bash
docker-compose up -d
```

Ahora puede acceder al portal del administrador a través de: http://localhost:9092/csp/sys/%25CSP.Portal.Home.zen

- **Username:** SuperUser
- **Password:** SYS
- **SuperServer port:** 9091
- **Web port:** 9092
- **Namespace:** ENSDEMO

![ensdemo](https://openexchange.intersystems.com/mp/img/packages/468/screenshots/zhnwycjrflt4q7gttwsidcntxk.png)

Para iniciar una sesión de terminal, ejecute:

```bash
docker exec -it ensdemo iris session iris
```

Con la extensión [InterSystems ObjectScript](https://marketplace.visualstudio.com/items?itemName=daimor.vscode-objectscript) Visual Studio Code extension, puedes acceder al código directamente desde _vscode_

![vscode](https://openexchange.intersystems.com/mp/img/packages/468/screenshots/bgirfnblz2zym4zi2q92lnxkmji.png)

### Detener el Contenedor

```bash
docker-compose stop
```

### Soporte a ZPM

```bash
zpm "install irishealth-ensdemo"
```
