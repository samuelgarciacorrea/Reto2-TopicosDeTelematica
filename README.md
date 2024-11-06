# Reto 2 Topicos de Telematica 
Samuel Garcia Correa - Sgarciac6@eafit.edu.co
Juan Andres Vera Alvarez - javeraa@eafit.edu.co


En este reto se implementa una arquitectura que incluye dos sitios WordPress, un balanceador de carga, una base de datos y un servidor NFS. Se emplean dos instancias de WordPress para garantizar la disponibilidad del sitio web, además de asegurar una conexión segura mediante HTTPS con un dominio con certificado SSL.

### Aspectos Desarrollados

Todos los requisitos funcionales  se han cumplido. Se han creado cinco instancias: una para el servidor Nginx, que actúa como balanceador de carga y gestiona el certificado SSL para el dominio, dos instancias para los sitios WordPress, conectados a una base de datos remota, una instancia para la base de datos, y una instancia para el servidor NFS.

### Información General de Diseño

La arquitectura implementada sigue un enfoque cliente-servidor utilizando contenedores Docker para las instancias del balanceador de carga, WordPress y base de datos. Se destina una máquina al balanceador de carga, que distribuye las peticiones entre las instancias de WordPress. Estas instancias comparten una base de datos y un servidor NFS para el almacenamiento de archivos.

### Ambiente de Desarrollo y Técnico

#### Base de Datos:

- Actualización de la instancia y instalación de Docker.
  
![image](https://github.com/user-attachments/assets/3c5f310d-bb23-40b0-9659-a4b92a021093)



  
- Creación de un archivo .yml para Docker Compose con la configuración requerida.
nano wordpressbd.yml

![image](https://github.com/user-attachments/assets/9243ed7c-9cb4-447f-97be-a46273ed106e)



- Ejecución del comando "docker-compose -f wordpressdb.yml up".

#### WordPress:

- Actualización de la instancia y instalación de Docker.
  
![image](https://github.com/user-attachments/assets/ab9720e9-ea3b-4068-a706-2829546b658a)


- Creación de un archivo .yml para Docker Compose con la configuración de WordPress, base de datos remota y NFS.
  
![image](https://github.com/user-attachments/assets/0a8d2cc6-cc0b-41b5-bcdf-8985d174a743)



- Configuración del cliente NFS.

![image](https://github.com/user-attachments/assets/03c9a763-5c31-4641-878e-3d72c897e659)


- Ejecución del comando "docker-compose -f wordpress.yml up".

#### NFS Server:

- Instalación del NFS-server y Configuración del NFS server
  
![image](https://github.com/user-attachments/assets/8f978350-392c-4787-950f-c428db268b91)

- Especificación de las instancias WordPress.
  
![image](https://github.com/user-attachments/assets/3cc2e2aa-2d7c-4cf5-a06e-62f2a53dbe2f)


![image](https://github.com/user-attachments/assets/7e048e42-2678-4eb4-9ed8-fc2ec78e6a9d)



- Reinicio del NFS server.

![image](https://github.com/user-attachments/assets/6966562c-db24-4677-a0e3-85a351bb4c05)



#### Balanceador de Carga:

- Verificación de puertos requeridos.

![image](https://github.com/user-attachments/assets/0305b267-1d3a-4b4e-927f-27004d064857)


  
- Actualización de la máquina e instalación de letsencrypt, certbot y nginx.
  
  
- Modificación del archivo de configuración de nginx.

![image](https://github.com/user-attachments/assets/f92b08b2-3562-4d58-ac96-36c0ad69a9ca)



![image](https://github.com/user-attachments/assets/7b8142bc-7e06-452a-af74-07781121bef7)




- Creación de la carpeta para letsencrypt y recarga de nginx.

  ![image](https://github.com/user-attachments/assets/0b08a310-6a45-4140-b4e4-fa29d72f41f9)


  
- Reserva de nombre de dominio y asignación de IP elástica y Obtención del certificado SSL para el dominio.

![image](https://github.com/user-attachments/assets/586944b7-5fb1-4554-b444-746d609d2b00)


![image](https://github.com/user-attachments/assets/6051a5c2-11f5-42ba-942a-7f753115195c)


- Instalación de Docker.
  ![image](https://github.com/user-attachments/assets/b3299318-1cb7-4c62-999d-bd38a1070b88)

![image](https://github.com/user-attachments/assets/9b616672-9e55-4f4c-8866-a37c7c34fdd0)


- Creación y configuración de archivos Docker Compose.

![image](https://github.com/user-attachments/assets/4de8de86-6b70-4746-abfa-965ea76d59cb)




- Modificación del archivo de configuración de nginx y ssl.conf

![image](https://github.com/user-attachments/assets/94ec5926-20af-4e3f-a359-97466e5f6504)


![image](https://github.com/user-attachments/assets/e104819e-fbd5-4e9c-bf60-b90fd57d8312)



  
- Verificación de la no ejecución predeterminada de nginx.
  ![image](https://github.com/user-attachments/assets/fbd63334-6982-474e-93b5-d203da3d6d2b)


- Ejecución del docker-compose.
  
![image](https://github.com/user-attachments/assets/333ae8c3-f5cb-4b41-a9fb-aec739ba1b02)


## Instancias

![image](https://github.com/user-attachments/assets/6030062d-d08e-4772-a265-1beb861c8188)

# Video Sustentación

Link:
https://youtu.be/RsnAxMeCeBo

## Referencias

- https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-20-04
- https://www.digitalocean.com/community/tutorials/how-to-run-nginx-in-a-docker-container-on-ubuntu-22-04
- https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/How-to-setup-an-Nginx-load-balancer-example
