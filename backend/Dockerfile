# Usar una imagen base con JDK 17 en alpine
FROM openjdk:15-alpine

# Crear un nuevo grupo llamado "devopsc" para el almacenamiento
RUN addgroup -g 1028 devopsc  \
    && adduser -D -G devopsc admin

# Crear una carpeta "tmp" para el almacenamiento de cache
VOLUME /tmp

# Establecer una argumento para asignar el JAR
ARG JAR_FILE

# Establecer una variable local DB_PASSWORD con el valor del argumento
ARG DB_PASSWORD

# Establecer una varible de entorno DB_PASSWORD
ENV DB_PASSWORD=$DB_PASSWORD

# Copiar el archivo JAR
COPY ${JAR_FILE} /tmp/app.jar

# Cambiar los permisos en el directorio para el usuario "admin"
RUN chown -R admin:devopsc /tmp

# Cambiar al usuario admin
USER admin

# Ejecutar el JAR al iniciar el contenedor
ENTRYPOINT [ "java","-jar","/tmp/app.jar" ]                         