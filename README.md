# greckrypto

Spring Boot Starter ligero para criptografía desarrollado en **Java 17** con **Gradle**. Facilita la integración de componentes de cifrado y utilidades criptográficas en proyectos Spring Boot mediante autoconfiguración.

---

## 🛠️ Requisitos Previos

* **Java JDK 17** o superior.
* **Gradle** (usando el wrapper incluido `./gradlew`) o **Maven** para el proyecto consumidor.
* Un **GitHub Personal Access Token (PAT)** con alcance `read:packages` si se consume desde GitHub Packages.

---

## Instalación

### Opción 1: GitHub Packages (Recomendado)

#### 1. Configurar credenciales de GitHub
Antes de construir tu proyecto, debes exportar tu usuario y token de GitHub en tu entorno:
```bash
export GITHUB_USER="tu-usuario-github"
export GITHUB_TOKEN="tu-github-personal-access-token"
```

#### 2. Agregar el repositorio y la dependencia

* **Gradle (`build.gradle`):**
```bash
repositories {
    mavenCentral()
    maven {
        url = uri("https://maven.pkg.github.com/renz-ayala/greckrypto_starter")
        credentials {
            username = System.getenv("GITHUB_USER")
            password = System.getenv("GITHUB_TOKEN")
        }
    }
}

dependencies {
    implementation 'gg.renz:greckrypto:1.0'
}
```

* **Maven (`pom.xml`):**
```bash
<repositories>
    <repository>
        <id>github</id>
        <url>https://maven.pkg.github.com/renz-ayala/greckrypto_starter</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>gg.renz</groupId>
        <artifactId>greckrypto</artifactId>
        <version>1.0</version>
    </dependency>
</dependencies>
```

---

### Opción 2: Instalación Local (`mavenToLocal`)

Si deseas instalar la librería directamente en tu repositorio local (`~/.m2/repository`) para pruebas de desarrollo local sin publicar en GitHub Packages:

1. Clona el repositorio:
```bash
   git clone https://github.com/renz-ayala/greckrypto_starter.git
   cd greckrypto_starter
```

3. Publica en tu Maven Local:
```bash
   ./gradlew publishToMavenLocal
```
5. En el proyecto consumidor, asegúrate de incluir `mavenLocal()` en los repositorios:
```bash
   repositories {
       mavenLocal()
       mavenCentral()
   }

   dependencies {
       implementation 'gg.renz:greckrypto:1.0'
   }
```

---

## Uso en Spring Boot

El starter registrará automáticamente los componentes criptográficos en el contexto de tu aplicación al incluir la dependencia (Spring Boot Auto-configuration `3.2.4+`).

Debe añadir el valor de
```bash
secret_keys.codes.crypt_key: <suClaveAqui>
```
en su perfil de aplicación.

---
