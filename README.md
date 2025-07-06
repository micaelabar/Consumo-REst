
# Consumo Rest Microservicios
## Introducción:

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
### Paso 1: Liberación del puerto 8080
Se detectó que el puerto 8080 ya estaba en uso, impidiendo el inicio de api-gateway.
```
netstat -ano | findstr :8080
````
```
taskkill /PID <PID> /F
````
### Evidencia:
<imag!
### Paso 2:  Corrección de errores BOM en archivos Java
Los servicios clientes-service y pagos-service no compilaban por un carácter invisible BOM (\ufeff) en sus clases principales.
### Evidencia:
<imag!
### Paso 3:Corrección de dependencias Maven
Los archivos pom.xml no contenían versiones de algunas dependencias clave, lo que impedía la construcción correcta del proyecto.
Se agregó la propiedad:
```
<spring-cloud.version>Hoxton.SR9</spring-cloud.version>
````
Se incluyó el BOM de Spring Cloud:
```
<dependencyManagement>
  <dependencies>
    <dependency>
      <groupId>org.springframework.cloud</groupId>
      <artifactId>spring-cloud-dependencies</artifactId>
      <version>${spring-cloud.version}</version>
      <type>pom</type>
      <scope>import</scope>
    </dependency>
  </dependencies>
</dependencyManagement>
````
### Evidencia:
<imag!

### Paso 4: Ejecución de microservicios
Se usó Maven para ejecutar los servicios:
```
mvn clean spring-boot:run
````
### Evidencia:
<imag!
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






