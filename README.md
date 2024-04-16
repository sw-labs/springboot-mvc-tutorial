# Creando una aplicación web con Spring Boot

> En este tutorial creará una pequeña aplicación web usando [Spring Boot](https://spring.io/projects/spring-boot): un conjunto de herramientas y librerías que facilitan el desarrollo de aplicaciones empresariales. 

---

## Objetivos de aprendizaje

En este tutorial, aprenderá a 
- Desarrollar una aplicación web usando Spring Boot
- Mostrar páginas HTML como respuesta a peticiones HTTP GET


## Requisitos previos

- Conocimientos básicos de programación, Java y bases de datos.
- Una instancia de [Gitpod](https://gitpod.io/) o un computador con [Docker Desktop](https://www.docker.com/products/docker-desktop/) y [Visual Studio Code](https://code.visualstudio.com/) instalado. 

---

## Paso a paso

### 1. Crear una copia del repositorio

- Navegue hasta el repositorio del proyecto en Github
    - [https://github.com/sw-labs/springboot-mvc-tutorial](https://github.com/sw-labs/springboot-mvc-tutorial)

- Cree una copia del repositorio usando el botón "Use this Template", la opción "Create a new repository"
    - asigne un nombre al nuevo repositorio

### 2. Abra el nuevo repositorio 

- Abra el repositorio que acaba de crear usando Gitpod o Visual Studio Code
    - Para usar Gitpod, en el navegador, agregue  `gitpod.io` al inicio de la ruta URL del repositorio

    ```
    # Si el URL es https://github.com/ejemplo/spring-mvc
    # Use en el navegador:
    
    gitpod.io#https://github.com/ejemplo/spring-mvc
    ```
    - Para usar Visual Studio Code, haga una copia del proyecto y use el comando `code` 

    ```
    # Si el repositorio es https://github.com/ejemplo/spring-mvc
    # Ejecute los comandos:

    git clone https://github.com/ejemplo/spring-mvc
    cd spring
    code . 
    ```


### 3. Cree un nuevo proyecto de Spring

Para este tutorial se usarán varias dependencias de Sprint Boot

| Dependencia           | Descripción    |
|-----------------------|----------------|
| Spring Web            | Librerías para el desarrollo de aplicaciones web                         |
| Spring Boot DevTools  | Actualiza la aplicación en ejecución con cada cambio en el código fuente |
| Spring Thymeleaf      | Permite usar plantillas para crear aplicaciones web                      |


- En Gitpod o Visual Studio Code, presiones [F1] para mostrar las opciones del editor
- Seleccione la opción  `Spring Initializr: Create a new Maven Project...`
- Seleccione la última opción de Spring Boot
- Seleccione el lenguaje Java
- Indique el nombre del grupo, algo similar al nombre de una empresa, por ejemplo "com.empresa"
- Indique el nombre del proyecto, por ejemplo "tutorial"
- Seleccione el tipo de paquete "jar"
- Seleccione la versión de Java "22"
- Seleccione las dependencias "Spring Web", "Spring Thymeleaf" y "Sprint Boot DevTools". Presione Enter cuando haya terminado de seleccionar las dependencias.
-  Indique la carpeta donde se grabará el proyecto. Use el nombre recomendado por el editor.

---

Al crear el proyecto se crea un proyecto Spring con una serie de clases y archivos.

Si se usó el nombre de empresa "com.empresa" y el nombre de proyecto "tutorial", debieron crearse una serie de archivos similares a los siguientes:

```
/demo
  /src
    /main
      /java                         <-- carpeta con código fuente java
        /com/empresa/tutorial       <-- paquete en java
          TutorialApplication.java  <-- clase en java
      
      /resources                    <-- carpeta con archivos adicionales
        /static
        /templates
        application.properties      <-- archivo de configuración
  
            :  (otros archivos)
``` 

**NOTA:** Los nombres pueden variar de acuerdo a los datos suministrados en la configuración.

---

### 4. Agregue una plantilla para la aplicación

- En la carpeta `src/main/resources/templates`, cree un archivo llamado `index.html`

  ```
  <h1>Hola Mundo !!</h1>
  ```


### 4. Agregue un paquete para Controladores

> Los controladores son clases Java que responden a eventos y a solicitudes de los usuarios. Para el ejemplo, estos controladores van a responder a solicitudes web hechas con el protocolo HTTP

- Seleccione el paquete (la carpeta) donde se encuentra la clase `Application`. Para el ejemplo, seleccione el paquete `com.empresa.tutorial`
- Haga clic derecho y seleccione "New..." y la opción "Package"
- Indique el nombre del nuevo paquete. Por ejemplo `com.empresa.tutorial.controllers`

### 5. Agregue una clase Controladora

- Seleccione el paquete que acaba de crear
- Haga clic derecho y seleccione "New..." y la opción "Class"
- Indique el nombre de la clase `HomeController`

### 6. Escriba el código para crear el controlador

> Los Controladores REST atienden solicitudes web hechas con el protocolo HTTP. Estos controladores pueden atender, por ejemplo, solicitudes GET que son enviadas por un navegador web para obtener una página de internet.

- Agregue una anotación `@Controller" a la clase
- Agregue una anotación `@RequestMapping("/")` para indicar que el controlador va a responder a las solicitudes de la ruta `/`
- Agregue un método `hola()` que tenga la anotación `@GetMapping` indicando que este método debe responder a las solicitudes GET de la ruta `/`

  ```
  package com.empresa.tutorial.controllers;

  import org.springframework.stereotype.Controller;
  import org.springframework.web.bind.annotation.GetMapping;
  import org.springframework.web.bind.annotation.RequestMapping;

  @Controller
  @RequestMapping("/")
  public class HomeController {

      @GetMapping
      public String hola() {
          return "index";
      }

  }
  ```

### 7. Ejecute la aplicación

- Desde línea de comandos, cambie el directorio actual al directorio del proyecto
  ```
  # cd <nombre de la carpeta con el proyecto>
  cd tutorial
  ```

- Ejecute la aplicación usando `mvn spring-boot:run`
  ```
  mvn spring-boot:run
  ```

### 8. Visualice el funcionamiento del controlador

- Use un navegador y observe el resultado de la aplicación
  - En Gitpod, apenas ejecute la aplicación, debe aparecer una ventana preguntando si se desea ver la página web que acaba de lanzar
  - Haga clic en "Open in browser" para ver el funcionamiento de la aplicación

