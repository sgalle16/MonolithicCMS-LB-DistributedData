# CMS Monolítico con Balanceo de Carga y Datos Distribuidos

## ST0263 Tópicos Especiales en Telemática

### Estudiante: Santiago Gallego , sgalle16@eafit.edu.co
### Profesor: Juan Carlos Montoya, jcmontoy@eafit.edu.co


## Reto 3: Aplicación Monolítica con Balanceo y Datos Distribuidos (BD y archivos)

Despliegue de WordPress con SSL y Balanceo de Carga
Este proyecto consiste en desplegar un sistema WordPress utilizando Docker, con un balanceador de carga implementado mediante Nginx,
y una base de datos MySQL. Todo el tráfico web es asegurado con SSL a través de certificados generados por Let’s Encrypt.

## 1.1. Que aspectos cumplió o desarrolló de la actividad propuesta por el profesor (requerimientos funcionales y no funcionales)
- [x] Balanceo de Carga: Utilización de Nginx como balanceador para distribuir las solicitudes entre múltiples instancias de WordPress.
- [x] Seguridad con SSL: Uso de certificados SSL para asegurar todas las comunicaciones mediante HTTPS.
- [x] Base de Datos Centralizada: MySQL utilizado como base de datos central para todas las instancias de WordPress.
- [x] Almacenamiento Compartido: Configuración de NFS para el almacenamiento de medios y archivos de WordPress, accesible por todas las instancias.
- [x] Desplegar WordPress empleando la tecnología de contenedores.
- [x] Propio dominio y certificado SSL.

## 1.2. Que aspectos NO cumplió o desarrolló de la actividad propuesta por el profesor (requerimientos funcionales y no funcionales)
- Se cumplieron con todo lo propuesto por el profesor.

## Requisitos Funcionales y No Funcionales
El sistema fue diseñado cumple con los siguientes requisitos:
- **Requisitos Funcionales:**
  - Despliegue de una aplicación WordPress en un entorno Docker.
  - Implementación de un balanceador de carga Nginx para gestionar el tráfico HTTPS.
  - Utilización de dos instancias de procesamiento de WordPress detrás del balanceador de carga.
  - Configuración de una instancia de base de datos MySQL para ambas instancias del CMS y NFS para la gestión de archivos.
  - Almacenamiento NFS para compartir archivos entre instancias de WordPress.
  - Certificados SSL para asegurar la comunicación.

- **Requisitos No Funcionales:**
  - **Disponibilidad**: Implementación de múltiples instancias de WordPress para asegurar la disponibilidad del servicio, en este caso se desplejaron 2 instancias.
  - **Escalabilidad:** La arquitectura permite escalar horizontalmente añadiendo más instancias de WordPress detrás del balanceador de carga
  - **Rendimiento:** El balanceo de carga asegura una gestión eficiente del tráfico y la utilización de los recursos.
  - **Mantenibilidad**: Uso de Docker y Docker Compose facilita la gestión y el mantenimiento de los servicios.  
  - **Seguridad:** Encriptación SSL/TLS para la transmisión segura de datos y uso de HTTPS .

## Diseño de Alto Nivel y Arquitectura
El sistema emplea una arquitectura con:
- **Balanceador de Carga:** Utiliza Nginx para distribuir las solicitudes HTTPS entrantes a las instancias de WordPress.
- **Capa de Aplicación:** Las instancias de WordPress manejan la generación de contenido estatico y dinámico.
- **Capa de Base de Datos:** Un servidor MySQL para la persistencia de datos.
- **Almacenamiento de Archivos:** Servidor NFS para la gestión de archivos distribuidos.

  
# 2. Diseño de alto nivel, arquitectura, patrones, mejores prácticas utilizadas.



![image](https://github.com/sgalle16/MonolithicCMS-LB-DistributedData/assets/14111169/9effb30d-454e-4771-8f0e-743b5dbcb28a)




# 3. Descripción del ambiente de desarrollo y técnico: lenguaje de programación, librerias, paquetes, etc, con sus numeros de versiones.

*Lenguajes y Herramientas*:
- Docker y Docker Compose para la orquestación de contenedores.
- Nginx como servidor web y balanceador de carga.
- WordPress como sistema de gestión de contenidos.
- MySQL como sistema de gestión de bases de datos.
- NFS para el almacenamiento compartido.

*Versiones*:
- Docker: 20.10.7
- Docker Compose: 1.29.2
- Nginx: latest
- WordPress: latest
- MySQL: 5.7

*Acceso*:
- Dominio del Sitio Web: https://reto3.rentevo.site
- Administración de WordPress: https://reto3.rentevo.site/wp-admin

## detalles del desarrollo.



## detalles técnicos
 

## descripción y como se configura los parámetros del proyecto (ej: ip, puertos, conexión a bases de datos, variables de ambiente, parámetros, etc)


# 4. Descripción del ambiente de EJECUCIÓN (en producción) lenguaje de programación, librerias, paquetes, etc, con sus numeros de versiones.
- Sistema Operativo: Ubuntu 20.04 en AWS EC2
- Docker: Versión 20.10.7, soporte para la gestión de contenedores

# IP o nombres de dominio en nube o en la máquina servidor.
Para acceder a la página web: https://reto3.rentevo.site

Load Balancer: IP elástica en AWS: 3.232.238.182

Wordpress1 - IP privada: 172.31.41.8

Wordpress2 - IP privada: 172.31.88.232

DBServer - IP privada: 172.31.88.161

NFServer - IP privada: 172.31.92.236

## descripción y como se configura los parámetros del proyecto (ej: ip, puertos, conexión a bases de datos, variables de ambiente, parámetros, etc)

## como se lanza el servidor.

## una mini guia de como un usuario utilizaría el software o la aplicación


## Pantallazos 
![reto3site](https://github.com/sgalle16/MonolithicCMS-LB-DistributedData/assets/14111169/2bbf8ee1-f465-4f0e-8a5d-a74c8f4e7862)
![httpsreto3site](https://github.com/sgalle16/MonolithicCMS-LB-DistributedData/assets/14111169/fe085180-ec81-4d09-ad2b-99de83469938)

# 5. otra información que considere relevante para esta actividad.

# 6. Referencias:

- https://docs.docker.com/engine/install/ubuntu/
- https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-20-04
- https://www.letscloud.io/community/how-to-set-up-an-nginx-with-certbot-on-ubuntu
