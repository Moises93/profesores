# Proyecto Profesores - API REST con Spring Boot

![Spring Boot](https://img.shields.io/badge/Spring%20Boot-1.5.9-green?logo=spring-boot)
![Java](https://img.shields.io/badge/Java-8-blue?logo=java)
![MySQL](https://img.shields.io/badge/MySQL-5.7%2B-blue?logo=mysql)
![Maven](https://img.shields.io/badge/Maven-3.5%2B-red?logo=apache-maven)

## 📋 Descripción General

Sistema de gestión de profesores, cursos y redes sociales desarrollado con **Spring Boot 1.5.9** y **Java 8**. API REST completa con arquitectura de microservicios que proporciona endpoints para gestionar profesores, cursos y perfiles en redes sociales.

**Stack tecnológico principal:**
- Spring Boot 1.5.9 (Framework web)
- Spring Data JPA (Acceso a datos)
- Java 8 (Lenguaje de programación)
- MySQL 5.7+ (Base de datos)
- Maven 3.5+ (Build tool)
- GitHub Actions (CI/CD)

## 🎯 Propósito del Proyecto

Sistema backend completo para gestión académica con enfoque en:
- **Administración de profesores**: Crear, actualizar, listar y eliminar profesores
- **Gestión de cursos**: Asociar cursos a profesores
- **Redes sociales**: Integración con perfiles de redes sociales

## 🏗️ Arquitectura

```
┌─────────────────────────────────────────┐
│   Controladores REST (Controllers)      │
│   ├─ /teacher                          │
│   ├─ /course                           │
│   └─ /socialmedia                      │
└──────────────┬──────────────────────────┘
               │
┌──────────────▼──────────────────────────┐
│   Spring Data JPA (Servicios)           │
│   ├─ TeacherService                    │
│   ├─ CourseService                     │
│   └─ SocialMediaService                │
└──────────────┬──────────────────────────┘
               │
┌──────────────▼──────────────────────────┐
│   JPA Repositories                      │
│   ├─ TeacherRepository                 │
│   ├─ CourseRepository                  │
│   └─ SocialMediaRepository             │
└──────────────┬──────────────────────────┘
               │
┌──────────────▼──────────────────────────┐
│   MySQL 5.7+ Database                  │
│   ├─ teacher (tabla)                   │
│   ├─ course (tabla)                    │
│   └─ social_media (tabla)              │
└─────────────────────────────────────────┘
```

## 📚 Endpoints API

### Profesores

| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | `/teacher` | Obtener lista de todos los profesores |
| GET | `/teacher/{id}` | Obtener un profesor específico |
| POST | `/teacher` | Crear un nuevo profesor |
| PUT | `/teacher/{id}` | Actualizar un profesor |
| DELETE | `/teacher/{id}` | Eliminar un profesor |

**Ejemplo de respuesta GET /teacher:**
```json
[
  {
    "id": 1,
    "name": "Juan García",
    "email": "juan@example.com",
    "department": "Informática",
    "courses": [...]
  }
]
```

### Cursos

| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | `/course` | Obtener lista de cursos |
| GET | `/course/{id}` | Obtener un curso específico |
| POST | `/course` | Crear un nuevo curso |
| PUT | `/course/{id}` | Actualizar un curso |
| DELETE | `/course/{id}` | Eliminar un curso |

### Redes Sociales

| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | `/socialmedia` | Obtener redes sociales |
| GET | `/socialmedia/{id}` | Obtener red social específica |
| POST | `/socialmedia` | Crear perfil en red social |
| PUT | `/socialmedia/{id}` | Actualizar perfil |
| DELETE | `/socialmedia/{id}` | Eliminar perfil |

## 🛠️ Requisitos Previos

### Sistema Operativo

**Windows:**
- Windows 10/11 (x64)
- PowerShell o CMD
- 2 GB RAM mínimo

**macOS:**
- macOS 10.13+
- Terminal/iTerm2
- 2 GB RAM mínimo

**Linux:**
- Ubuntu 18.04+, CentOS 7+, Debian 10+
- Bash/Zsh
- 2 GB RAM mínimo

### Software Requerido

1. **Java Development Kit (JDK) 8**
   - Versión mínima: Java 8 (1.8.0)
   - Versión recomendada: Java 8u292+
   
2. **Maven 3.5+**
   - Para compilación y empaquetado del proyecto
   
3. **MySQL 5.7+**
   - Base de datos relacional
   - Compatible con MySQL 8.0 también

4. **Git** (recomendado)
   - Para clonar el repositorio

## 📦 Instalación

### 1. Instalar Java 8

**Windows:**
```bash
# Descargar desde: https://www.oracle.com/java/technologies/javase/javase8u211-later-archive-downloads.html
# O usando Chocolatey:
choco install jdk8
```

**macOS:**
```bash
# Usando Homebrew
brew install java@8

# O descargar manualmente desde Oracle
```

**Linux (Ubuntu/Debian):**
```bash
sudo apt-get update
sudo apt-get install openjdk-8-jdk
java -version  # Verificar instalación
```

### 2. Instalar Maven 3.5+

**Windows:**
```bash
# Descargar desde: https://maven.apache.org/download.cgi
# Configurar MAVEN_HOME y agregar bin a PATH
setx MAVEN_HOME "C:\Program Files\apache-maven-3.6.3"
setx PATH "%PATH%;%MAVEN_HOME%\bin"

# Verificar
mvn -version
```

**macOS:**
```bash
brew install maven
mvn -version  # Verificar
```

**Linux (Ubuntu/Debian):**
```bash
sudo apt-get install maven
mvn -version  # Verificar
```

### 3. Instalar MySQL 5.7+

**Windows:**
```bash
# Descargar desde: https://dev.mysql.com/downloads/installer/
# O usando Chocolatey:
choco install mysql

# Crear base de datos
mysql -u root -p
CREATE DATABASE profesores;
USE profesores;
```

**macOS:**
```bash
# Usando Homebrew
brew install mysql

# Iniciar MySQL
brew services start mysql

# Crear base de datos
mysql -u root
CREATE DATABASE profesores;
```

**Linux (Ubuntu/Debian):**
```bash
sudo apt-get install mysql-server
sudo systemctl start mysql

# Crear base de datos
sudo mysql -u root
CREATE DATABASE profesores;
GRANT ALL PRIVILEGES ON profesores.* TO 'admin'@'localhost' IDENTIFIED BY 'password';
FLUSH PRIVILEGES;
```

### 4. Clonar y Configurar el Proyecto

```bash
# Clonar repositorio
git clone https://github.com/Moises93/profesores.git
cd profesores

# Copiar archivo de configuración
cp application.properties.example src/main/resources/application.properties

# Editar configuración de MySQL
# Editar: src/main/resources/application.properties
# spring.datasource.url=jdbc:mysql://localhost:3306/profesores
# spring.datasource.username=admin
# spring.datasource.password=tu_contraseña
```

### 5. Compilar y Ejecutar

```bash
# Compilar con Maven
./mvnw clean install

# O usando Maven directamente
mvn clean install

# Ejecutar la aplicación
./mvnw spring-boot:run

# O
mvn spring-boot:run

# La aplicación estará disponible en: http://localhost:8080
```

## 🔧 Configuración

### application.properties

```properties
# Puerto
server.port=8080

# Base de datos
spring.datasource.url=jdbc:mysql://localhost:3306/profesores
spring.datasource.username=admin
spring.datasource.password=password
spring.datasource.driver-class-name=com.mysql.jdbc.Driver

# JPA/Hibernate
spring.jpa.hibernate.ddl-auto=update
spring.jpa.database-platform=org.hibernate.dialect.MySQL5Dialect
spring.jpa.show-sql=false
spring.jpa.properties.hibernate.format_sql=true

# Logging
logging.level.root=INFO
logging.level.com.example.profesores=DEBUG
```

## 🚀 Ejecución

### Opción 1: Maven Wrapper (Recomendado)

```bash
# En Windows
mvnw.cmd spring-boot:run

# En Linux/macOS
./mvnw spring-boot:run
```

### Opción 2: Maven Directo

```bash
mvn spring-boot:run
```

### Opción 3: Ejecutar JAR compilado

```bash
# Compilar
mvn clean package

# Ejecutar
java -jar target/profesores-1.0.0.jar
```

### Verifica que la aplicación está corriendo

```bash
curl http://localhost:8080/teacher
```

Respuesta esperada:
```json
[]
```

## 🧪 Testing

```bash
# Ejecutar todos los tests
mvn test

# Tests con cobertura
mvn test jacoco:report

# Ejecutar tests específicos
mvn test -Dtest=TeacherControllerTest
```

## ❌ Troubleshooting

### "Port 8080 already in use"

```bash
# Windows: Encontrar proceso en puerto 8080
netstat -ano | findstr :8080
taskkill /PID <PID> /F

# Linux/macOS: Encontrar y matar proceso
lsof -ti:8080 | xargs kill -9
```

### "Cannot connect to MySQL"

```bash
# Verificar que MySQL está corriendo
# Windows
net start MySQL80

# Linux
sudo systemctl start mysql

# Verificar credenciales en application.properties
# Probar conexión manualmente
mysql -h localhost -u admin -p

# Asegurar que la base de datos existe
mysql -u admin -p -e "CREATE DATABASE IF NOT EXISTS profesores;"
```

### "java.lang.ClassNotFoundException: com.mysql.jdbc.Driver"

```bash
# Verificar que Maven descargó las dependencias
mvn dependency:resolve

# Limpiar y reinstalar
mvn clean install
```

### "Spring Boot no inicia"

```bash
# Ver logs completos
mvn spring-boot:run -X

# Verificar que Java 8 está configurado
java -version

# Comprobar que Maven ve las dependencias
mvn dependency:tree
```

## 📚 Estructura del Proyecto

```
profesores/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/example/profesores/
│   │   │       ├── controllers/
│   │   │       │   ├── TeacherController.java
│   │   │       │   ├── CourseController.java
│   │   │       │   └── SocialMediaController.java
│   │   │       ├── services/
│   │   │       │   ├── TeacherService.java
│   │   │       │   ├── CourseService.java
│   │   │       │   └── SocialMediaService.java
│   │   │       ├── repositories/
│   │   │       │   ├── TeacherRepository.java
│   │   │       │   ├── CourseRepository.java
│   │   │       │   └── SocialMediaRepository.java
│   │   │       ├── models/
│   │   │       │   ├── Teacher.java
│   │   │       │   ├── Course.java
│   │   │       │   └── SocialMedia.java
│   │   │       └── Application.java
│   │   └── resources/
│   │       ├── application.properties
│   │       └── application-dev.properties
│   └── test/
│       └── java/...
├── pom.xml
├── README.md
└── .gitignore
```

## 🔒 Seguridad

- Validación de entrada en todos los endpoints
- Prepared statements para prevenir SQL injection
- CORS configurado correctamente
- Spring Security integrado

## 📖 Documentación Completa

Para más detalles sobre configuración avanzada, ver:
- `INSTALL.md` - Guía de instalación detallada
- `CONTRIBUTING.md` - Guía de contribución
- `SECURITY.md` - Política de seguridad

## 🤝 Contribución

Consultar `CONTRIBUTING.md` para instrucciones sobre cómo contribuir al proyecto.

## 📄 Licencia

Este proyecto está bajo licencia MIT. Ver `LICENSE` para más detalles.

## 👥 Autores

- **Moisés García** - Desarrollo principal

## 📞 Contacto

Para reportar bugs o sugerir mejoras, abrir un issue en el repositorio de GitHub.

