# Laboratorio 6

## Manejo de cookies

**Objetivo**: Al finalizar las actividades de este laboratorio, deberás ser capaz de comprender los aspectos básicos del trabajo de cookies en Java EE.

## Preparación
La descripción de este laboratorio parte del supuesto que ya se cuenta con la versión de NetBeans (EE) y que incluye un contenedor Web GlassFish o Apache Tomcat atendiendo un puerto de escucha 8080.

## Actividades

En este laboratorio se realizará una mini-aplicación web que funcione con el patrón MVC y haga uso de sesiones y cookies. El objetivo es construir un login sencillo y almacenar la información del usuario en variables de sesión y un color de fondo del perfil de usuario en una cookie.

## Actividad 1 - Ajuste de proyecto de Laboratorio 5

1.- Crear un proyecto de tipo Java Web en NetBeans de nombre `Laboratorio6`.

2.- Elimina el archivo `index.html` que crea por defecto NetBeans y que se encuentra dentro de la carpeta Web Pages.

3.- Utiliza los archivos del `Laboratorio5`.

## Actividad 2 - Cierre de sesión

Para completar el flujo del `Laboratorio5` deberemos construir un mecanismo para cerrar la sesión del usuario.

1.- Crea un nuevo servlet de nombre `LogoutController`.

2.- Agrega un enlace al final del archivo `profile.jsp` con la propiedad `href` apuntando hacia `LogoutController` y el texto `Cerrar sesión`.

3.- El controlador `LogoutController` deberá invalidar la sesión como sigue:

```java
HttpSession session = request.getSession();

session.invalidate();

response.sendRedirect("login.jsp");
```

## Actividad 3 - Personalización de color de perfil

EL objetivo de esta actividad es proveerle al usuario un mecanismo para "recordar" su color favorito como color de fondo de su perfil.


1.- Dentro de `perfil.jsp` deberá construir un elemento `select` para modificar el color del fondo de pantalla. Agregar mínimo tres colores.

2.- Agregar un botón "Guardar" que ejecute una petición `POST` hacia `ProfileController`, que crearemos en el siguiente punto.

3.- Crear un nuevo servlet de nombre `ProfileController`. Este servlet actuará como controlador para manejar la solicitud `POST` enviada por el cliente. El servlet, deberá construir una cookie de nombre "color" y con el valor del color a modificar (Ej. "red", "blue", "green", etc). Ejemplo:

```java
 //El valor red solo es ejemplo. Debe obtenerse del valor del campo select enviado por el POST
String color = "red";
Cookie cookie = new Cookie("color", color);
response.addCookie(cookie);
response.sendRedirect("profile.jsp");
```

4.- Al regresar la respuesta del servidor hacia el cliente, la página `profile.jsp` deberá buscar la cookie para asignar su valor a la regla de estilo `background-color` de la propiedad `style` del elemento `body` del `HTML`. Ejemplo:

```java
<%
String color = "";
Cookie[] cookies = request.getCookies();
for(Cookie c : cookies) { 
  if(c.getName().equals("color")) { 
    color = c.getValue();
  }
}
%>
<html>
  <head>....</head>
  <body style="background-color: <%= color %>;">
  ....
  </body>
</html>
```

# Pruebas

Realiza las pruebas para todos los escenarios.
- Inicio de sesión inválido (usuario o password erróneo)
- Inicio válido (usuario o password correctos)
- Entrar directamente a profile.jsp con sesión y sin sesión.
- Entrar directamente a login.jsp con sesión y sin sesión.
- Entrar a profile.jsp y elegir un color. 
- Cerrar sesión, volver a iniciar sesión y validar que el fondo de la página sea el color elegido en el punto anterior.

# Preguntas
- ¿Qué ventajas tienes al hacer manejo de cookies en la aplicación Web?
- ¿Qué problemas potenciales pueden presentarse al manejar las cookies?
- ¿Como funciona el `for(Cookie c : cookies)` y para que se utiliza su `if` interno?
- ¿Sería conveniente almacenar el valor del color en una sesión?
- ¿Sería conveniente almacenar el nombre de usuario en una cookie?

# Especificaciones del Reporte

- El reporte debe incluir una portada con tus datos al inicio.
- El reporte debe contener la descripción de los pasos realizados para llevar a cabo la práctica del laboratorio. Cada paso debe contar con un fragmento de código o imagen que ilustre lo descrito. Piense en el reporte como una explicación para alguien ajeno al tema y detalle los puntos técnicos que sean necesarios.
- Contesta las preguntas mencionadas en la sección anterior.
- Comprime en un archivo `.zip` el directorio raíz de la práctica.
- El envío de la práctica debe incluir dos archivos: El reporte en `PDF` y el archivo `.zip` con el código fuente del proyecto.
