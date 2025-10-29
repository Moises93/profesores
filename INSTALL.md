# 📦 Guía de Instalación - Proyecto Profesores

![Spring Boot](https://img.shields.io/badge/Spring%20Boot-1.5.9-green)
![Java](https://img.shields.io/badge/Java-8-blue)
![MySQL](https://img.shields.io/badge/MySQL-5.7%2B-blue)
![Maven](https://img.shields.io/badge/Maven-3.5%2B-red)

## 📋 Tabla de Contenidos

1. [Requisitos del Sistema](#requisitos-del-sistema)
2. [Instalación por Sistema Operativo](#instalación-por-sistema-operativo)
3. [Configuración de Base de Datos](#configuración-de-base-de-datos)
4. [Compilación y Ejecución](#compilación-y-ejecución)
5. [Verificación de la Instalación](#verificación-de-la-instalación)
6. [Troubleshooting](#troubleshooting)
7. [Próximos Pasos](#próximos-pasos)

## 🖥️ Requisitos del Sistema

### Hardware Mínimo

- **Procesador**: Dual-core 2.0 GHz
- **RAM**: 2 GB (4 GB recomendado)
- **Disco**: 500 MB de espacio libre
- **Conexión a Internet**: Para descargar dependencias

### Software Requerido

| Software | Versión | Versión Mínima | Propósito |
|----------|---------|-----------------|-----------|
| **Java JDK** | 8 (1.8.0) | 8u131 | Compilación y ejecución |
| **Maven** | 3.5+ | 3.3.1 | Build tool y gestor de dependencias |
| **MySQL** | 5.7+ | 5.7 | Base de datos relacional |
| **Git** | 2.20+ | 2.0 | (Opcional) Clonar repositorio |

### Versiones Específicas Verificadas

```
✅ Testificado con:
   - Java 8 (1.8.0_292)
   - Maven 3.6.3
   - MySQL 5.7.31 / MySQL 8.0.23
   - Spring Boot 1.5.9
```

## 🚀 Instalación por Sistema Operativo

### 1. WINDOWS 10/11

#### Paso 1: Instalar Java 8

**Opción A: Mediante Instalador Oracle (Recomendado)**

1. Descargar JDK 8 desde: https://www.oracle.com/java/technologies/javase/javase8u211-later-archive-downloads.html
2. Ejecutar instalador `.exe`
3. Seleccionar ruta: `C:\Program Files\Java\jdk1.8.0_XXX`
4. Configurar variables de entorno:

```bash
# Abrir: Configuración del Sistema → Variables de entorno
# Crear variables de usuario:

JAVA_HOME = C:\Program Files\Java\jdk1.8.0_XXX
PATH = %PATH%;%JAVA_HOME%\bin

# En PowerShell, verificar:
java -version
javac -version
```

**Opción B: Mediante Chocolatey**

```bash
# En PowerShell como administrador
choco install jdk8 -y
java -version
```

#### Paso 2: Instalar Maven 3.5+

**Opción A: Descarga Manual**

1. Descargar desde: https://maven.apache.org/download.cgi
2. Extraer en: `C:\Program Files\apache-maven-3.6.3`
3. Configurar variables de entorno:

```bash
# Agregar a PATH
setx MAVEN_HOME "C:\Program Files\apache-maven-3.6.3"
setx PATH "%PATH%;%MAVEN_HOME%\bin"

# Verificar en nueva ventana PowerShell
mvn -version
```

**Opción B: Mediante Chocolatey**

```bash
choco install maven -y
mvn -version
```

#### Paso 3: Instalar MySQL 5.7+

**Opción A: MySQL Community Server**

1. Descargar: https://dev.mysql.com/downloads/mysql/
2. Ejecutar instalador
3. Seleccionar `Full Installation`
4. Configurar como Windows Service
5. Configurar puerto: 3306
6. Usuario root y contraseña

```bash
# Verificar en PowerShell
mysql --version

# Conectarse a MySQL
mysql -u root -p
# Ingresar contraseña

# En MySQL CLI:
CREATE DATABASE profesores;
SHOW DATABASES;
EXIT;
```

**Opción B: Mediante Chocolatey**

```bash
choco install mysql -y
```

#### Paso 4: Clonar y Configurar Proyecto

```bash
# En PowerShell
cd C:\Projects  # O directorio deseado

# Clonar
git clone https://github.com/Moises93/profesores.git
cd profesores

# Copiar y editar configuración
Copy-Item "application.properties.example" "src\main\resources\application.properties"

# Editar archivo (usar Notepad++):
# notepad "src\main\resources\application.properties"

# Cambiar:
# spring.datasource.url=jdbc:mysql://localhost:3306/profesores
# spring.datasource.username=root
# spring.datasource.password=tu_contraseña_aqui
```

#### Paso 5: Compilar y Ejecutar

```bash
# En PowerShell desde carpeta profesores

# Compilar
mvnw.cmd clean install

# Ejecutar
mvnw.cmd spring-boot:run

# Esperar hasta ver:
# [main] o.s.b.a.e.t.TomcatEmbeddedServletContainer : Tomcat started on port(s): 8080
```

---

### 2. macOS (Intel y Apple Silicon)

#### Paso 1: Instalar Java 8

**Opción A: Descargar de Oracle**

1. Visitar: https://www.oracle.com/java/technologies/javase8u211-later-archive-downloads.html
2. Descargar `.dmg` para macOS
3. Ejecutar instalador
4. Agregar a `~/.bash_profile` o `~/.zshrc`:

```bash
export JAVA_HOME=$(/usr/libexec/java_home -v 1.8)
export PATH=$JAVA_HOME/bin:$PATH

# Para Apple Silicon M1/M2
export JAVA_HOME=$(/usr/libexec/java_home -v 1.8 -a arm64)
```

Recargar: `source ~/.zshrc`

**Opción B: Usando Homebrew**

```bash
# Instalar Homebrew si no está
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Instalar Java 8
brew install java@8

# Crear symlink
sudo ln -sfn /opt/homebrew/opt/openjdk@8/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk-8.jdk

# Verificar
java -version
```

#### Paso 2: Instalar Maven

```bash
brew install maven

# Verificar
mvn -version
```

#### Paso 3: Instalar MySQL

**Opción A: Homebrew**

```bash
brew install mysql

# Iniciar MySQL
brew services start mysql

# Conectarse
mysql -u root

# Crear base de datos
CREATE DATABASE profesores;
EXIT;
```

**Opción B: DMG Installer**

1. Descargar desde: https://dev.mysql.com/downloads/mysql/
2. Ejecutar instalador `.dmg`
3. Seguir wizard

#### Paso 4: Clonar y Configurar

```bash
cd ~/Projects  # O directorio deseado

git clone https://github.com/Moises93/profesores.git
cd profesores

cp application.properties.example src/main/resources/application.properties

# Editar con tu editor favorito:
nano src/main/resources/application.properties

# Cambiar credenciales MySQL:
# spring.datasource.url=jdbc:mysql://localhost:3306/profesores
# spring.datasource.username=root
# spring.datasource.password=
```

#### Paso 5: Compilar y Ejecutar

```bash
# Dar permisos al mvnw
chmod +x mvnw

# Compilar
./mvnw clean install

# Ejecutar
./mvnw spring-boot:run

# Debe mostrar:
# Tomcat started on port(s): 8080
```

---

### 3. LINUX (Ubuntu/Debian)

#### Paso 1: Instalar Java 8

```bash
# Actualizar lista de paquetes
sudo apt-get update

# Instalar OpenJDK 8
sudo apt-get install openjdk-8-jdk openjdk-8-jre -y

# Verificar
java -version
javac -version

# (Opcional) Si tienes múltiples versiones Java:
sudo update-alternatives --config java
sudo update-alternatives --config javac

# Agregar a ~/.bashrc o ~/.zshrc:
echo 'export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64' >> ~/.bashrc
source ~/.bashrc
```

#### Paso 2: Instalar Maven

```bash
# Instalar Maven
sudo apt-get install maven -y

# Verificar
mvn -version

# (Alternativa: Instalación manual)
cd /opt
sudo wget https://archive.apache.org/dist/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz
sudo tar xzf apache-maven-3.6.3-bin.tar.gz
sudo ln -s apache-maven-3.6.3 maven

# Agregar a PATH:
echo 'export M2_HOME=/opt/maven' >> ~/.bashrc
echo 'export PATH=$M2_HOME/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
```

#### Paso 3: Instalar MySQL Server

**Para Ubuntu 18.04/20.04:**

```bash
# Instalar MySQL Server
sudo apt-get install mysql-server mysql-client -y

# Iniciar servicio
sudo systemctl start mysql
sudo systemctl enable mysql  # Para que inicie automáticamente

# Verificar
mysql --version

# Crear usuario y base de datos
sudo mysql -u root

# En MySQL CLI:
CREATE USER 'admin'@'localhost' IDENTIFIED BY 'password123';
CREATE DATABASE profesores;
GRANT ALL PRIVILEGES ON profesores.* TO 'admin'@'localhost';
FLUSH PRIVILEGES;
EXIT;

# Verificar conexión
mysql -u admin -p  # Ingresar: password123
SHOW DATABASES;
EXIT;
```

**Para sistemas con Systemd:**

```bash
# Ver estado
sudo systemctl status mysql

# Reiniciar
sudo systemctl restart mysql
```

#### Paso 4: Clonar y Configurar

```bash
# Crear directorio de proyectos
mkdir -p ~/Projects
cd ~/Projects

# Clonar repositorio
git clone https://github.com/Moises93/profesores.git
cd profesores

# Copiar configuración
cp application.properties.example src/main/resources/application.properties

# Editar con nano o vim
nano src/main/resources/application.properties

# Configurar:
# spring.datasource.url=jdbc:mysql://localhost:3306/profesores
# spring.datasource.username=admin
# spring.datasource.password=password123
```

#### Paso 5: Compilar y Ejecutar

```bash
# Dar permisos
chmod +x mvnw

# Compilar
./mvnw clean install

# Ejecutar
./mvnw spring-boot:run

# Debe mostrar:
# Tomcat started on port(s): 8080 (http)
```

---

## 🗄️ Configuración de Base de Datos

### Verificar Conexión a MySQL

**Windows (PowerShell):**
```bash
mysql -h localhost -u admin -p
# Ingresar contraseña
```

**Linux/macOS (Terminal):**
```bash
mysql -h localhost -u admin -p
# Ingresar contraseña
```

### Crear Base de Datos Manualmente (si no existe)

```sql
-- Conectarse como root
mysql -u root -p

-- En MySQL CLI:
CREATE DATABASE IF NOT EXISTS profesores;

-- Usar base de datos
USE profesores;

-- Spring Boot creará las tablas automáticamente
-- O ejecutar script manual:

CREATE TABLE teacher (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255),
    department VARCHAR(255)
);

CREATE TABLE course (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(255) NOT NULL,
    teacher_id BIGINT,
    FOREIGN KEY (teacher_id) REFERENCES teacher(id)
);

CREATE TABLE social_media (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    platform VARCHAR(255),
    url VARCHAR(500),
    teacher_id BIGINT,
    FOREIGN KEY (teacher_id) REFERENCES teacher(id)
);

-- Verificar
SHOW TABLES;
DESC teacher;
```

### Archivo application.properties

```properties
# ============================================
# SPRING BOOT CONFIGURATION
# ============================================
spring.application.name=profesores-api
server.port=8080
server.servlet.context-path=/

# ============================================
# DATABASE CONFIGURATION
# ============================================
# Connection URL
spring.datasource.url=jdbc:mysql://localhost:3306/profesores

# Username and password
spring.datasource.username=admin
spring.datasource.password=password123

# Driver
spring.datasource.driver-class-name=com.mysql.jdbc.Driver

# ============================================
# JPA/HIBERNATE CONFIGURATION
# ============================================
# Database platform
spring.jpa.database-platform=org.hibernate.dialect.MySQL5Dialect

# Hibernate DDL (create, create-drop, validate, update)
spring.jpa.hibernate.ddl-auto=update

# Show SQL
spring.jpa.show-sql=false
spring.jpa.properties.hibernate.format_sql=true

# ============================================
# LOGGING
# ============================================
logging.level.root=INFO
logging.level.com.example.profesores=DEBUG
logging.level.org.springframework.web=DEBUG
logging.level.org.hibernate=WARN

# ============================================
# SERVER
# ============================================
server.compression.enabled=true
```

## ✅ Verificación de la Instalación

### 1. Verificar Java

```bash
# Windows
java -version
javac -version

# Linux/macOS
java -version
javac -version

# Salida esperada:
# java version "1.8.0_XXX"
# Java(TM) SE Runtime Environment ...
```

### 2. Verificar Maven

```bash
mvn -version

# Salida esperada:
# Apache Maven 3.6.3
# Maven home: ...
# Java version: 1.8.0_XXX
```

### 3. Verificar MySQL

```bash
mysql --version
mysql -u admin -p -e "SELECT VERSION();"

# Salida esperada:
# mysql  Ver 8.0.23 for ...
```

### 4. Verificar Proyecto en Ejecución

```bash
# En otra terminal/tab, una vez que la app esté corriendo:

# Test de conexión
curl http://localhost:8080/teacher

# Respuesta esperada:
# []

# O en Windows (PowerShell):
(Invoke-WebRequest -Uri "http://localhost:8080/teacher").Content
```

## 🔧 Troubleshooting

### Error 1: "java: No such file or directory"

**Problema:** Java no está en el PATH

**Soluciones:**

```bash
# Windows: Verificar variable JAVA_HOME
echo %JAVA_HOME%

# Si está vacía:
setx JAVA_HOME "C:\Program Files\Java\jdk1.8.0_XXX"
setx PATH "%PATH%;%JAVA_HOME%\bin"

# Reiniciar PowerShell

# Linux/macOS:
echo $JAVA_HOME
# Debe mostrar la ruta a Java 8

# Si no:
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
```

### Error 2: "mvn: command not found"

**Problema:** Maven no está instalado o no en PATH

```bash
# Verificar instalación
which mvn  # Linux/macOS
where mvn  # Windows

# Agregar al PATH:
# Windows: setx PATH "%PATH%;C:\Program Files\apache-maven-3.6.3\bin"
# Linux/macOS: export PATH=$PATH:/opt/maven/bin
```

### Error 3: "Port 8080 already in use"

**Problema:** Otro proceso usa el puerto 8080

**Windows:**
```bash
# En PowerShell
netstat -ano | findstr ":8080"
taskkill /PID <PID> /F

# O cambiar puerto en application.properties:
# server.port=8081
```

**Linux:**
```bash
lsof -i :8080
kill -9 <PID>

# O:
sudo fuser -k 8080/tcp
```

**macOS:**
```bash
lsof -i :8080
kill -9 <PID>
```

### Error 4: "Cannot connect to MySQL"

**Problema:** MySQL no está corriendo o credenciales incorrectas

```bash
# Verificar que MySQL está corriendo:

# Windows:
net start MySQL80
# o
sc query MySQL80

# Linux:
sudo systemctl status mysql
sudo systemctl start mysql

# macOS:
brew services list  # Ver estado
brew services start mysql
```

**Verificar credenciales:**

```bash
# Conectar manualmente
mysql -h localhost -u admin -p
# Ingresar contraseña

# Verificar base de datos
SHOW DATABASES;
USE profesores;
SHOW TABLES;
```

### Error 5: "ClassNotFoundException: com.mysql.jdbc.Driver"

**Problema:** Driver MySQL no descargado

```bash
# Limpiar y reinstalar
mvn clean install

# Verificar dependencias
mvn dependency:resolve

# Forzar descarga
mvn clean dependency:resolve-plugins dependency:resolve
```

### Error 6: "Connection refused"

**Problema:** MySQL no está escuchando en el puerto correcto

```bash
# Verificar puerto de MySQL en:
# Windows: C:\ProgramData\MySQL\MySQL Server 8.0\my.ini
# Linux: /etc/mysql/mysql.conf.d/mysqld.cnf
# Buscar: port = 3306
```

## 🎓 Próximos Pasos

1. ✅ Instalación completada
2. 📚 Leer `README.md` para información del proyecto
3. 🔗 Consultar `API_ENDPOINTS.md` para endpoints disponibles
4. 🤝 Ver `CONTRIBUTING.md` para contribuir
5. 🔒 Revisar `SECURITY.md` para prácticas de seguridad

## 📞 Soporte

Si encuentras problemas:

1. Verificar logs en `target/logs/`
2. Ejecutar: `./mvnw -X spring-boot:run` para debug
3. Consultar issues en: https://github.com/Moises93/profesores/issues
4. Crear nuevo issue con:
   - Sistema operativo y versión
   - Versión Java (`java -version`)
   - Versión Maven (`mvn -version`)
   - Mensaje de error completo

---

**Última actualización:** Octubre 2025
**Versión:** 1.0.0

