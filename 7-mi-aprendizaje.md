# Imagenes
Antes del desarrollo de esta práctica no sabia como crear mis propias imagenes, sin embargo ahora puedo crear imagenes con configuraciones mediante los Dockerfile.
# Uso de recursos
Esta seccion fue de gran ayuda para futuros contenedores, ya que no se les puede dar toda la capacidad de hardware del host a varios contenedores.
# Problemas
Se presento un problema en la parte de Dockerfile con la creacion de la primera imagen, ya que parece que algunos repositorios ya no estan disponibles pero con el siguiente dockerfile funcionó
```
FROM centos:7
RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
RUN sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*

RUN yum update -y
RUN yum install -y httpd
COPY ./web /var/www/html
EXPOSE 80
CMD ["apachectl", "-D", "FOREGROUND"]
```

