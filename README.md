# Proyecto Lambda con API Gateway en AWS

Este proyecto despliega una función AWS Lambda accesible a través de AWS API Gateway utilizando CloudFormation y es gestionado por una pipeline de CI/CD implementada con GitHub Actions.

## Descripción

La pipeline automatiza el proceso de empaquetado y despliegue del código de la función Lambda directamente desde el repositorio de GitHub a AWS Lambda y API Gateway. Este enfoque facilita las actualizaciones continuas y la gestión de la infraestructura como código.

## Pipeline de CI/CD

La pipeline de GitHub Actions realiza los siguientes pasos:

1. **Checkout del código:** Obtiene la última versión del código fuente del repositorio.
2. **Configuración del entorno Python:** Prepara el entorno Python para usar herramientas como AWS CLI.
3. **Instalación de dependencias:** Instala AWS CLI que es necesario para interactuar con AWS.
4. **Empaquetado del código de la función Lambda:** Crea un archivo ZIP con el código fuente de Lambda.
5. **Subida del código a S3:** Sube el archivo ZIP a un bucket de S3 en AWS.
6. **Despliegue de la stack de CloudFormation:** Utiliza AWS CloudFormation para desplegar o actualizar los recursos necesarios, pasando la ubicación del código de Lambda en S3 como parámetros.