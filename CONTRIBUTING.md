# 🤝 Guía de Contribución - Proyecto Profesores

¡Gracias por tu interés en contribuir a este proyecto! Esta guía te ayudará a entender cómo puedes participar de manera efectiva.

## 📋 Tabla de Contenidos

1. [Código de Conducta](#código-de-conducta)
2. [¿Cómo Puedo Contribuir?](#cómo-puedo-contribuir)
3. [Configuración del Entorno](#configuración-del-entorno)
4. [Proceso de Contribución](#proceso-de-contribución)
5. [Guía de Estilo de Código](#guía-de-estilo-de-código)
6. [Testing](#testing)
7. [Commit y PR](#commit-y-pull-request)
8. [Preguntas](#preguntas)

## 🤗 Código de Conducta

Todos los contribuyentes deben seguir nuestro código de conducta:

- **Respeto**: Trata a todos con respeto, independientemente de su experiencia
- **Inclusividad**: Damos la bienvenida a contribuidores de todos los trasfondos
- **Profesionalismo**: Mantén un lenguaje profesional y constructivo
- **Colaboración**: Busca colaborar y ayudar a otros

**Comportamiento inaceptable**:
- Acoso, insultos, o discriminación de cualquier tipo
- Lenguaje ofensivo o despectivo
- Ataques personales

Reporta comportamiento inaceptable a: maintainers@example.com

## 💡 ¿Cómo Puedo Contribuir?

### 1. Reportar Bugs

**¿Encontraste un bug?** Abre un issue en GitHub:

1. Ve a: https://github.com/Moises93/profesores/issues
2. Haz clic en "New Issue"
3. Selecciona "Bug report"
4. Incluye:
   - **Título**: Descripción clara del bug
   - **Descripción**: Detalles específicos
   - **Pasos para reproducir**: Lista precisa
   - **Comportamiento esperado**: Qué debería ocurrir
   - **Comportamiento actual**: Qué está ocurriendo
   - **Entorno**: 
     - OS: Windows/macOS/Linux
     - Java version: `java -version`
     - Maven version: `mvn -version`
     - MySQL version: `mysql --version`
   - **Logs**: Output relevante

**Ejemplo de buen reporte:**

```
Título: Teachers endpoint devuelve error 500 al consultar con parámetro vacío

Descripción: 
Al hacer GET a /teacher?name= devuelve error 500 en lugar de usar valor por defecto

Pasos para reproducir:
1. Iniciar aplicación (./mvnw spring-boot:run)
2. Ejecutar: curl "http://localhost:8080/teacher?name="
3. Observar respuesta

Comportamiento esperado:
Devolver lista completa de teachers (200 OK)

Comportamiento actual:
Error 500 - java.lang.NullPointerException

Entorno:
- OS: Ubuntu 20.04
- Java 8 (1.8.0_292)
- Maven 3.6.3
- MySQL 8.0.23
```

### 2. Sugerir Mejoras

Para sugerir una mejora:

1. Ve a Issues y abre "Feature request"
2. Describe la mejora deseada
3. Proporciona justificación
4. Incluye ejemplos si es posible

**Ejemplo:**

```
Título: Agregar paginación al endpoint GET /teacher

Descripción:
El endpoint GET /teacher devuelve todos los teachers. Con muchos registros 
sería mejor implementar paginación.

Propuesta:
GET /teacher?page=0&size=20&sort=name,asc

Beneficios:
- Mejor rendimiento
- Mejor UX en frontend
- Cumple con estándares REST
```

### 3. Escribir Documentación

Puedes mejorar la documentación:

- Corregir errores ortográficos
- Clarificar instrucciones
- Agregar ejemplos
- Traducir a otros idiomas

Simplemente crea un PR con los cambios.

### 4. Enviar Código

El proceso es:

1. Fork el repositorio
2. Crea una rama
3. Haz cambios
4. Escribe tests
5. Crea Pull Request

(Ver [Proceso de Contribución](#proceso-de-contribución))

## 🛠️ Configuración del Entorno

### 1. Fork y Clonar

```bash
# 1. Fork en GitHub (botón "Fork" en la esquina superior derecha)

# 2. Clonar tu fork
git clone https://github.com/TU_USUARIO/profesores.git
cd profesores

# 3. Agregar upstream
git remote add upstream https://github.com/Moises93/profesores.git

# 4. Verificar
git remote -v
# origin: TU_FORK
# upstream: ORIGINAL
```

### 2. Instalar Dependencias

```bash
# Instalar según tu OS (ver INSTALL.md)
# - Java 8
# - Maven 3.5+
# - MySQL 5.7+

# Compilar proyecto
mvn clean install

# Verificar
mvn test
```

### 3. Configurar IDE

**IntelliJ IDEA (Recomendado):**
```
1. File → Open → Seleccionar carpeta profesores
2. Esperar a que cargue e indexe
3. Run → Run Configurations → Create New...
4. Seleccionar Maven
5. Configurar:
   - Working directory: $PROJECT_DIR$
   - Command line: clean spring-boot:run
6. Run
```

**Eclipse:**
```
1. File → Import → Existing Maven Projects
2. Seleccionar carpeta profesores
3. Right-click → Run As → Maven build
4. Goals: clean spring-boot:run
```

**Visual Studio Code:**
```
1. Instalar extensiones:
   - Extension Pack for Java
   - Spring Boot Extension Pack
2. Open folder: profesores
3. Debug con F5
```

## 📝 Proceso de Contribución

### Paso 1: Sincronizar con Upstream

```bash
# Asegurarse de estar en main
git checkout main

# Traer cambios del repositorio original
git fetch upstream
git rebase upstream/main

# O si prefieres merge:
git merge upstream/main

# Actualizar tu fork
git push origin main
```

### Paso 2: Crear Rama de Feature

```bash
# Crear rama con nombre descriptivo
git checkout -b feature/teachers-pagination
# o: git checkout -b fix/null-pointer-exception

# O para bugs:
git checkout -b bugfix/issue-123-teacher-name-filter

# Convención de nombres:
# - feature/description
# - bugfix/description
# - docs/description
# - test/description
# - refactor/description
```

### Paso 3: Realizar Cambios

**Estructura de carpetas:**
```
src/
├── main/
│   ├── java/com/example/profesores/
│   │   ├── controller/      ← API endpoints
│   │   ├── service/         ← Lógica de negocio
│   │   ├── repository/      ← Acceso a datos
│   │   ├── entity/          ← Modelos JPA
│   │   ├── dto/             ← Data Transfer Objects
│   │   └── exception/       ← Custom exceptions
│   └── resources/
│       └── application.properties
└── test/java/...            ← Tests unitarios
```

**Agregar nueva feature:**

```java
// 1. Crear Entity en entity/Teacher.java
@Entity
@Table(name = "teacher")
public class Teacher {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    @Column(nullable = false)
    private String name;
    
    // ... getters, setters, constructor
}

// 2. Crear Repository en repository/TeacherRepository.java
@Repository
public interface TeacherRepository extends JpaRepository<Teacher, Long> {
    List<Teacher> findByNameContainingIgnoreCase(String name);
    Page<Teacher> findAll(Pageable pageable);
}

// 3. Crear Service en service/TeacherService.java
@Service
@Transactional
public class TeacherService {
    @Autowired
    private TeacherRepository teacherRepository;
    
    public List<Teacher> getAllTeachers() {
        return teacherRepository.findAll();
    }
    
    public Teacher getTeacher(Long id) {
        return teacherRepository.findById(id)
            .orElseThrow(() -> new ResourceNotFoundException("Teacher not found"));
    }
    // ...
}

// 4. Crear Controller en controller/TeacherController.java
@RestController
@RequestMapping("/teacher")
public class TeacherController {
    @Autowired
    private TeacherService teacherService;
    
    @GetMapping
    public ResponseEntity<List<Teacher>> getAllTeachers() {
        return ResponseEntity.ok(teacherService.getAllTeachers());
    }
    
    @PostMapping
    public ResponseEntity<Teacher> createTeacher(@RequestBody Teacher teacher) {
        return ResponseEntity.status(HttpStatus.CREATED)
            .body(teacherService.createTeacher(teacher));
    }
    // ...
}
```

### Paso 4: Escribir Tests

**Test unitario en test/java/.../**

```java
@RunWith(SpringRunner.class)
@SpringBootTest
public class TeacherServiceTest {
    
    @MockBean
    private TeacherRepository teacherRepository;
    
    @Autowired
    private TeacherService teacherService;
    
    @Test
    public void testGetAllTeachers() {
        // Arrange
        List<Teacher> teachers = Arrays.asList(
            new Teacher(1L, "Prof. García"),
            new Teacher(2L, "Prof. López")
        );
        when(teacherRepository.findAll()).thenReturn(teachers);
        
        // Act
        List<Teacher> result = teacherService.getAllTeachers();
        
        // Assert
        assertEquals(2, result.size());
        assertEquals("Prof. García", result.get(0).getName());
    }
    
    @Test
    public void testGetTeacherNotFound() {
        // Arrange
        when(teacherRepository.findById(999L))
            .thenReturn(Optional.empty());
        
        // Act & Assert
        assertThrows(ResourceNotFoundException.class, () -> {
            teacherService.getTeacher(999L);
        });
    }
}
```

Ejecutar tests:

```bash
# Todos los tests
mvn test

# Test específico
mvn test -Dtest=TeacherServiceTest

# Con cobertura
mvn test jacoco:report
# Ver en target/site/jacoco/index.html
```

### Paso 5: Commit

```bash
# Ver cambios
git status
git diff

# Agregar cambios (todos)
git add .

# O agregar específicos
git add src/main/java/...
git add src/test/java/...

# Commit con mensaje descriptivo
git commit -m "feat: agregar paginación a GET /teacher"
git commit -m "fix: corregir NullPointerException al consultar con nombre vacío"
git commit -m "docs: actualizar INSTALL.md con instrucciones macOS"
git commit -m "test: agregar test para validación de email"

# Formato de commit: type(scope): subject
# types: feat, fix, docs, test, refactor, perf, style, chore
```

### Paso 6: Push a tu Fork

```bash
# Push al branch
git push origin feature/teachers-pagination

# Si la rama existe, agregar cambios:
git push origin feature/teachers-pagination
```

### Paso 7: Crear Pull Request

1. Ve a GitHub
2. Haz clic en "Compare & pull request"
3. Asegúrate de que:
   - Base repository: `Moises93/profesores`
   - Base branch: `main`
   - Head repository: `TU_USUARIO/profesores`
   - Compare branch: `feature/teachers-pagination`

4. Completa el PR:

```markdown
## Descripción
Implementar paginación en endpoint GET /teacher para mejorar rendimiento 
con grandes volúmenes de datos.

## Tipo de cambio
- [x] Nueva feature
- [ ] Bug fix
- [ ] Breaking change

## Cambios realizados
- Agregar parámetro `page` y `size` a GET /teacher
- Modificar TeacherRepository para usar JpaRepository Pageable
- Actualizar TeacherService con método paginado
- Agregar tests para paginación

## Testing realizado
- [x] Tests unitarios pasando
- [x] Manual testing en Postman
- [x] Verificación de cobertura (>80%)

## Checklist
- [x] Mi código sigue el guía de estilo
- [x] He realizado self-review
- [x] He agregado comentarios explicativos
- [x] He actualizado la documentación
- [x] Mis cambios no generan warnings
- [x] He agregado tests que prueban mi feature
- [x] Tests nuevos y existentes pasando localmente

## Issues relacionados
Closes #123
```

## 🎨 Guía de Estilo de Código

### Java Style Guide

```java
// 1. Nombres de variables (camelCase)
String teacherName;       // ✅ correcto
String teacher_name;      // ❌ incorrecto
String tn;                // ❌ demasiado corto

// 2. Nombres de clases (PascalCase)
public class TeacherService { }      // ✅
public class teacherservice { }      // ❌

// 3. Constantes (UPPER_SNAKE_CASE)
public static final String API_VERSION = "1.0";     // ✅
public static final String apiVersion = "1.0";      // ❌

// 4. Métodos
public void createTeacher() { }       // ✅
public void create_teacher() { }      // ❌

// 5. Indentación (4 espacios)
public void method() {
    if (condition) {
        doSomething();
    }
}

// 6. Imports organizados
import java.util.*;           // java.* primero
import org.springframework.*;  // javax.* después
import com.example.*;         // luego librerías terceros
                              // línea en blanco
import static ...;            // imports estáticos al final

// 7. Documentación (Javadoc)
/**
 * Obtiene un profesor por ID.
 *
 * @param id el ID del profesor
 * @return el profesor encontrado
 * @throws ResourceNotFoundException si no existe
 */
public Teacher getTeacher(Long id) {
    // ...
}

// 8. Anotaciones Spring
@Service                                    // Una por línea
@Transactional
public class TeacherService {
    
    @Autowired                              // Inyección explícita
    private TeacherRepository repository;
    
    @Transactional(readOnly = true)        // Con parámetros
    public List<Teacher> getAll() { }
}

// 9. Manejo de excepciones
try {
    doSomething();
} catch (IOException e) {
    logger.error("Error: {}", e.getMessage(), e);  // Log completo
    throw new ApplicationException("mensaje", e);   // Re-lanzar informativo
}

// 10. Línea máxima: 120 caracteres
public ResponseEntity<List<Teacher>> getAllTeachersWithPaginationAndSortingByNameAndDepartment() {
    // Si supera, romper estratégicamente
}
```

### Comentarios

```java
// ✅ BUENOS comentarios

/**
 * Obtiene todos los profesores con paginación.
 * El índice de página comienza en 0.
 */
public Page<Teacher> getAllTeachers(int page, int size) { }

// TODO: Implementar caché para mejorar rendimiento
private String getTeacherName() { }

// FIXME: Esta lógica puede fallar si name es null
String name = teacher.getName().toUpperCase();

// ❌ MALOS comentarios

// obtener profesor            // Obvio, innecesario
Teacher t = getTeacher();

// this method gets teacher    // Innecesario
public Teacher get() { }

// esto es un loop             // Obvio
for (int i = 0; i < n; i++) { }
```

### Logs

```java
// Usar SLF4J
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

@Service
public class TeacherService {
    private static final Logger logger = LoggerFactory.getLogger(TeacherService.class);
    
    public void createTeacher(Teacher teacher) {
        logger.info("Creating teacher: {}", teacher.getName());    // info
        
        try {
            repository.save(teacher);
            logger.debug("Teacher saved with ID: {}", teacher.getId());  // debug
        } catch (Exception e) {
            logger.error("Error saving teacher", e);               // error
        }
    }
}
```

## ✅ Testing

### Coverage Mínimo

- Total project: **70%** mínimo
- Controller: **75%** mínimo
- Service: **85%** mínimo
- Repository: Testeado vía integración

### Ejecutar Tests

```bash
# Todos
mvn test

# Específico
mvn test -Dtest=TeacherServiceTest

# Con cobertura
mvn test jacoco:report

# Ver reporte
open target/site/jacoco/index.html  # macOS
start target\site\jacoco\index.html # Windows
firefox target/site/jacoco/index.html # Linux
```

## 📤 Commit y Pull Request

### Mensajes de Commit

Formato:
```
type(scope): subject

body

footer
```

Tipos:
- `feat`: Nueva feature
- `fix`: Bug fix
- `docs`: Cambios de documentación
- `style`: Cambios de formato (espacios, etc.)
- `refactor`: Refactorización sin cambios funcionales
- `test`: Agregar o actualizar tests
- `chore`: Tareas (dependencias, build, etc.)

Ejemplos:
```
feat(teacher): agregar endpoint para listar por departamento
fix(auth): corregir validación de token expirado
docs(readme): actualizar instrucciones de instalación
test(service): agregar 5 tests para TeacherService
refactor(repository): extraer lógica común en método privado
```

### PR Checklist

Antes de crear PR, verifica:

- [ ] Rama actualizada con `main`
- [ ] Tests pasando: `mvn test`
- [ ] Cobertura >= 70%: `mvn jacoco:report`
- [ ] Sin warnings: `mvn clean compile`
- [ ] Código sigue guía de estilo
- [ ] Documentación actualizada
- [ ] Commits con mensajes claros

## ❓ Preguntas

¿Necesitas ayuda? Opciones:

1. **Documentación**: Lee INSTALL.md, README.md, SECURITY.md
2. **Issues**: Busca issues similares en GitHub
3. **Discusiones**: Abre una discusión en GitHub
4. **Email**: Contacta a maintainers@example.com

---

**Última actualización:** Octubre 2025
**Versión:** 1.0.0

¡Gracias por contribuir! 🎉

