# Usar una imagen base de PHP con Apache
FROM php:8.3-apache

# Actualizar el sistema e instalar el cliente MariaDB
RUN apt-get update && apt-get install -y mariadb-client

# Instalar y habilitar la extensión mysqli de PHP
RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli

# Copiar los archivos de la aplicación al contenedor
ADD bookmedik /var/www/html/

# Exponer el puerto 80
EXPOSE 80

# Variables de entorno para la conexión con la base de datos
ENV DB_USER admin
ENV DB_PASS admin
ENV DB_NAME bookmedik
ENV DB_HOST servidor_mysql

# Copiar el script de inicialización y el esquema de la base de datos
ADD script.sh /usr/local/bin/script.sh
ADD bookmedik/schema.sql /opt

# Hacer que el script sea ejecutable
RUN chmod +x /usr/local/bin/script.sh

# Ejecutar el script de configuración
CMD ["/bin/bash", "-c", "/usr/local/bin/script.sh"]

