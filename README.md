Práctica con Serverless

Nota: No se pudo localizar un correo personal de la aula virtual, se uso el correo personal. Tambien se incorporo un documento con screenshots del proceso en >registro-serverless/Laboratorio de docker.docx 

Enlace: https://github.com/jairozamora/laboratorio-serverless/blob/main/registro-serverless/Laboratorio%20de%20docker.docx

Instalación de OpenFaaS CLI

Para este laboratorio se utilizó OpenFaaS CLI instalado mediante Homebrew en macOS. El cual se incluia en descarga_open_cli.txt

Nota: el script de Windows es una alternativa de instalación y no fue utilizado durante la implementación de este laboratorio.


Laboratorio Serverless – OpenFaaS

Descripción

Este proyecto corresponde a una práctica de laboratorio de la asignatura Introducción al Cómputo en la Nube. El objetivo fue implementar un entorno Serverless local utilizando Docker, Kubernetes y OpenFaaS, y desplegar una función desarrollada en Python.

La función permite registrar información mediante un formulario web y generar un archivo JSON con los datos ingresados y la información del entorno donde se ejecuta.

Tecnologías utilizadas

- macOS (Apple Silicon / ARM64)
- Docker Desktop
- Kubernetes
- Helm 3
- OpenFaaS
- Python 3
- Git y GitHub

Estructura del proyecto

```text
laboratorio-serverless/
├── registro-serverless/
│   ├── handler.py
│   ├── handler_test.py
│   ├── requirements.txt
│   └── tox.ini
├── template/
│   └── Plantillas de OpenFaaS
├── stack.yaml
└── .gitignore
```

Funcionamiento

La función `registro-serverless` presenta un formulario web que solicita:

- Nombre
- Apellido
- Correo electrónico

Al enviar el formulario, el sistema genera un archivo JSON que contiene:

- Datos del registro.
- Identificador único (UUID).
- Fecha y hora de ejecución en UTC.
- Sistema operativo y arquitectura del contenedor.
- Versión de Python.
- Nombre del contenedor.
- Plataforma de ejecución.
- Firma digital SHA-256.

Despliegue

El entorno se implementó localmente utilizando Docker Desktop y Kubernetes. OpenFaaS se instaló mediante Helm y se utilizó `faas-cli` para construir y desplegar la función.

Comandos principales utilizados:

```bash
faas-cli build -f stack.yaml
faas-cli deploy -f stack.yaml --gateway http://127.0.0.1:8080
faas-cli list
```

Resultado

Se logró desplegar correctamente la función `registro-serverless` en OpenFaaS. El formulario web permitió ingresar información y descargar el resultado en formato JSON.

La informacion del sistema operativo y la arquitectura corresponde al contenedor donde se ejecuta la función, no directamente al equipo anfitrion.

Autor

Jairo Zamora

Repositorio

[GitHub – laboratorio-serverless](https://github.com/jairozamora/laboratorio-serverless)
