
# Consumo Rest Microservicios
## Introducción:
La implementación y configuración de los microservicios fue realizada por el estudiante Pablo Sario, quien asumió la responsabilidad de resolver los problemas técnicos, gestionar adecuadamente las dependencias y ejecutar correctamente los servicios involucrados en el proyecto. Por su parte, la elaboración del presente informe y la sistematización del procedimiento técnico fueron llevadas a cabo por la estudiante Micaela Barbecho, quien estructuró la información de manera clara, precisa y formal.

Este trabajo conjunto evidencia la importancia de la colaboración entre los aspectos técnicos de la programación y la documentación técnica, permitiendo así una presentación integral y comprensible del proceso de desarrollo basado en una arquitectura moderna de microservicios.
## 1. Tiempo de duración:
La configuración, corrección de errores y ejecución exitosa de los microservicios tomó aproximadamente 2 horas, incluyendo identificación de errores, configuración del entorno y pruebas funcionales.
## 2. Fundamentos:
Los microservicios permiten dividir una aplicación monolítica en varios servicios pequeños, desplegables y escalables individualmente. Cada servicio se comunica entre sí a través de APIs REST. En este caso, se usó:
- Spring Boot: Para crear servicios rápidamente con configuración mínima.
- Eureka Server: Como servicio de descubrimiento para registrar y localizar los microservicios.
- Maven: Para la gestión de dependencias y construcción del proyecto.
## 3. Conocimientos previos
- Conocimientos básicos de Java y Spring Boot.
- Manejo de herramientas como Visual Studio Code o IntelliJ.
- Familiaridad con Maven.
- Comprensión general del concepto de microservicios.
## 4. Objetivo a alcanzar
- Configurar y ejecutar correctamente los tres microservicios.
- Solucionar errores de compilación y conflictos de puertos.
- Registrar exitosamente los servicios en el servidor Eureka.
- Demostrar la independencia y comunicación entre microservicios.
## 5. Equipo necesario
- Computadora con al menos 8 GB de RAM.
- Sistema operativo Windows 10 o superior.
- Conexión a internet.
- Editor de código (Visual Studio Code, IntelliJ, etc.).
## 6. Material de apoyo:
- Dependencias de Spring Boot.
- Documentación oficial de Spring Cloud.
- Comandos básicos de PowerShell y netstat.
- Repositorios de Maven:
https://repo.maven.apache.org
https://repo.spring.io
## 7. Procedimiento:
### Paso 1: Ejecución y visualización de Eureka Server
Descripción del procedimiento:
Configuración del proyecto Eureka Server:
- Se creó un proyecto Spring Boot con las siguientes dependencias necesarias:
Eureka Server
Spring Boot DevTools (opcional para recarga en caliente)
- En la clase principal del proyecto se añadió la anotación @EnableEurekaServer para habilitar el servidor Eureka.
- En el archivo application.properties o application.yml, se configuraron los parámetros básicos como:
```
server.port=8761
eureka.client.register-with-eureka=false
eureka.client.fetch-registry=false
````
### Evidencia:
<imag!![1](https://github.com/user-attachments/assets/1b839c88-9d31-419e-9fee-033fd972cc3d)

### Paso 2:Ejecución de Eureka Server desde consola (PowerShell)
Descripción del procedimiento:
Compilación del proyecto:
- Previamente, se generaron los archivos del proyecto mediante Maven o Gradle.
- El comando de ejecución fue algo similar a:
```
./mvnw spring-boot:run
````
### Evidencia:
<imag!![2](https://github.com/user-attachments/assets/73b2b91b-3fad-45a4-88dd-e985fcefe678)

### Paso 3: Creación del microservicio API Gateway
Acceso al proyecto raíz:
Se ingresó desde PowerShell al directorio del proyecto principal con el comando:
````
cd "C:\Users\usuario\Documents\Tercer ciclo\microservicios-proyecto"
```
e utilizó el siguiente comando para crear una carpeta destinada al microservicio api-gateway:
````
mkdir api-gateway
```
Finalmente, se accedió al nuevo directorio con:
````
cd api-gateway
```
### Evidencia:
<imag!![3](https://github.com/user-attachments/assets/03b95ba8-9e5b-480e-b07b-bd4fa41b68f3)

### Paso 4:Creación del proyecto API Gateway desde Spring Initializr
Acceso a Spring Initializr:
- Se ingresó al sitio oficial https://start.spring.io para generar un nuevo proyecto Spring Boot.
Configuración del proyecto:
- Tipo de proyecto: Maven - Java
- Versión de Spring Boot: 3.5.3
- Grupo: com.proyecto.gateway
- Artefacto y nombre del proyecto: api-gateway
- Versión de Java: 17
- Tipo de empaquetado: Jar
### Evidencia:
<imag!![4](https://github.com/user-attachments/assets/c3804758-cb4a-4520-aec9-7e6c8b91a5ab)

### Paso 5:Configuración del archivo application.properties en Eureka y API Gateway
Configuración del servidor Eureka (eureka-server):
````
server.port=8761
spring.application.name=eureka-server
eureka.client.register-with-eureka=false
eureka.client.fetch-registry=false
```
### Evidencia:
<imag!![5](https://github.com/user-attachments/assets/9ae286ec-5b0f-48fb-8a72-1ca915b44bfe)

- Archivo: src/main/resources/application.properties
### Paso 6: Verificación del Registro de Microservicios en Eureka
Acceso a la consola de Eureka:
- Se ingresó a la interfaz web del servidor Eureka a través de http://localhost:8761.
Visualización de microservicios registrados:
- Se confirmó que los siguientes servicios se registraron correctamente:
- API-GATEWAY en el puerto 8080
- CLIENTES-SERVICE en el puerto 8081
- PAGOS-SERVICE en el puerto 8082
Uno adicional marcado como UNKNOWN (puede tratarse de una instancia mal configurada o que no definió su nombre de aplicación).
### Evidencia:
<imag!![6](https://github.com/user-attachments/assets/a79865cc-afc8-43c0-b138-ac1b1f72c5c3)

### Paso 7: Revisión de archivos de configuración Maven y properties
pom.xml de Eureka Server:
- Se revisó el archivo pom.xml dentro de eureka-server, donde se encuentran configurados:
- El plugin de Spring Boot, que permite empaquetar y ejecutar la aplicación como microservicio.
- Los repositorios necesarios para obtener las dependencias desde repo.spring.io.
maven-wrapper.properties:
- En la carpeta .mvn/wrapper, se encuentra la configuración del wrapper de Maven, especificando:
- Versión utilizada (3.3.2)
- Tipo de distribución (only-script)
- URL del repositorio de Maven para descarga automática.
Confirmación de estructura:
Se visualizan correctamente los módulos clientes-service, pagos-service, eureka-server y api-gateway, organizados en un mismo proyecto de microservicios, lo que respalda una arquitectura modular bien estructurada.
### Evidencia:
<imag!![7](https://github.com/user-attachments/assets/51116708-3b2b-462f-bc1e-9a03c1aef396)

## 8. Resultado esperado:
- Todos los microservicios arrancaron correctamente.
- El servidor Eureka mostró los servicios con estado UP.
- Se estableció la comunicación REST entre ellos a través del api-gateway.
- Los errores iniciales fueron resueltos de forma efectiva.
### Evidencia:
<imag!
## 9. Conclusión:
El despliegue exitoso de una arquitectura de microservicios depende tanto de una correcta configuración de herramientas como de la capacidad para identificar y corregir errores en tiempo real. Utilizar Eureka como servidor de descubrimiento facilita el manejo de múltiples servicios, asegurando escalabilidad y flexibilidad en entornos distribuidos.
## 10. Bibliografía
- Spring Boot Reference Documentation – https://spring.io/projects/spring-boot
- Spring Cloud Netflix – https://cloud.spring.io/spring-cloud-netflix
- Documentación de Eureka Server – https://cloud.spring.io/spring-cloud-netflix/multi/multi_spring-cloud-eureka-server.html
- Maven Repository – https://mvnrepository.com
- Oracle Java Documentation – https://docs.oracle.com/javase/






