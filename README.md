Este proyecto implementa una arquitectura basada en contenedores utilizando Docker, Docker Compose, GitHub Actions y AWS EC2.
La solución fue desarrollada siguiendo principios DevOps con el objetivo de automatizar el despliegue de servicios, optimizar la construcción de imágenes y garantizar portabilidad, mantenibilidad y escalabilidad.
La arquitectura está compuesta por:
Frontend
Backend
Base de datos
Pipeline CI/CD
Infraestructura desplegada en AWS EC2

Dockerfiles

El backend fue contenedorizado utilizando un Dockerfile basado en multi-stage build.Primero está la compilación, donde se descargan dependencias y se genera el archivo.jar. Luego se usa una imagen
slim para reducir tamaño de imagen y consumo de recursos.Finalmente se copia el archivo .jar en la imagen. 
El dockerfile del front utiliza node.js también haciendo uso de multi stage build.

Docker compose
Permite organizar todos los servicios de la arquitectura.También se usa volumen docker para persistencia de datos y su conservación en caso de que el contenedor se reinicie.

Pipe Line CI/CD
Se ejecuta al realizar un push en la rama deploy, haciendo que GitHub Actions publique automáticamente las imágenes docker en un registro de contenedores (Amazon ECR). Además se usaron Secrets
para proteger informacion sensible y no mostrarla en el codigo fuente.

Con esto la arquitectura está debidamente contenedorizada y lista para desplegar en ec2





