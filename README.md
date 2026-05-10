# 🌐 API REST Jakarta EE + Pruebas con Karate

![Java](https://img.shields.io/badge/Java-11+-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Jakarta EE](https://img.shields.io/badge/Jakarta_EE-JAX--RS-FF6C37?style=for-the-badge)
![Karate](https://img.shields.io/badge/Karate-1.4.0-00BCD4?style=for-the-badge)
![JUnit](https://img.shields.io/badge/JUnit-5.9.3-25A162?style=for-the-badge&logo=junit5&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-C71A36?style=for-the-badge&logo=apachemaven&logoColor=white)

> Proyecto Java que implementa una **API REST con Jakarta EE (JAX-RS)** y pruebas de integración automatizadas con el framework **Karate**
---

## 🏗️ Arquitectura del Proyecto

```
APIS/
├── src/main/java/org/espe/apis/
│   ├── HelloApplication.java    # Configuración JAX-RS (@ApplicationPath)
│   └── HelloResource.java       # Endpoint REST GET /api/hello-world
├── src/main/resources/META-INF/
│   └── beans.xml                # Configuración CDI Jakarta EE
└── pom.xml                      # Dependencias: Karate + JUnit 5
```

---

## 📡 Endpoint Disponible

| Método | Ruta | Descripción | Respuesta |
|---|---|---|---|
| `GET` | `/api/hello-world` | Saludo básico | `Hello, World!` |

### Ejemplo de uso

```bash
curl http://localhost:8080/api/hello-world
# Respuesta: Hello, World!
```

---

## 🛠️ Tecnologías Utilizadas

| Tecnología | Versión | Uso |
|---|---|---|
| Java | 11+ | Lenguaje principal |
| Jakarta EE (JAX-RS) | Latest | Framework REST API |
| CDI (Beans) | 4.1 | Inyección de dependencias |
| Karate | 1.4.0 | Pruebas de integración de APIs |
| JUnit | 5.9.3 | Motor de ejecución de pruebas |
| Maven | 3.9.6 | Gestión de dependencias y build |

---

## 📁 Clases Principales

### `HelloApplication.java`
```java
@ApplicationPath("/api")
public class HelloApplication extends Application { }
```
Configura la ruta base de la API como `/api`.

### `HelloResource.java`
```java
@Path("/hello-world")
public class HelloResource {
    @GET
    @Produces("text/plain")
    public String hello() {
        return "Hello, World!";
    }
}
```
Expone el endpoint `GET /api/hello-world` que retorna texto plano.

---

## 🧪 Pruebas con Karate

El proyecto incluye **Karate** como framework de pruebas de APIs REST, integrado con JUnit 5. Karate permite escribir pruebas en lenguaje natural tipo BDD.

### Ejecutar pruebas

```bash
# Ejecutar todas las pruebas
mvn test

# Ejecutar con reporte detallado
mvn verify
```

### Ejemplo de prueba Karate (`.feature`)

```gherkin
Feature: Hello World API

  Scenario: Obtener saludo básico
    Given url 'http://localhost:8080/api/hello-world'
    When method GET
    Then status 200
    And response == 'Hello, World!'
```

---

## 🚀 Compilar y Ejecutar

### Prerrequisitos
- Java 11+
- Maven 3.9+
- Servidor de aplicaciones Jakarta EE (WildFly, Payara, GlassFish, etc.)

### Compilar

```bash
# Clonar el repositorio
git clone https://github.com/roberto1831/jakarta-ee-rest-api.git
cd jakarta-ee-rest-api

# Compilar el proyecto
mvn clean package

# Ejecutar pruebas
mvn test
```

### Desplegar

```bash
# Generar el WAR
mvn clean package

# Copiar el WAR al servidor de aplicaciones
# (ejemplo con WildFly)
cp target/petstore-api-tests-1.0.0.war $WILDFLY_HOME/standalone/deployments/
```

---

## 👤 Autor

**Ing. Roberto Toapanta**  
📍 Quito, Ecuador  
🔗 [GitHub](https://github.com/roberto1831) · [LinkedIn](https://linkedin.com/in/roberto1831)

---

## 📄 Licencia

Uso académico / demostrativo.
