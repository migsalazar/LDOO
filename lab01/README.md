# Construir una página simple con HTML, CSS y JS.

## Objetivos

- Construir un pequeño formulario haciendo uso de elemtos de html: `input` y `label`.
- Aplicar un color de fondo al `body` del documento con CSS
- Manipular los datos con javascript y mostrarlos en otra sección.

## Actividad 1

- Construir el html.

Se debe mostrar un formulario simple, similar al de la siguiente imagen: 

[]

## Actividad 2

- Modificar el color del fondo. Debe aplicarse una regla de estilo `background-color`, con tu color favorito, al elemento `body`.

## Actividad 3

- Hacer uso de la propiedad `onclick`, para el elemento `input` de tipo `submit`. Dicha propiedad deberá contener como valor el nombre de una función de javascript.

- Crear la función de javascript en el `head` del documento de html. Incluye la función dentro de las etiquetas `script`.

- Dicha función deberá realizar lo siguiente:
  - Obtener el valor de los campos "Nombre", "Primer apellido" y "Segundo apellido", haciendo uso de la funcion `document.getElementById("id-del-campo").value`
  - Almacenar en variables diferentes cada uno de los valores del punto anterior.
  - Concatenar dichas variables y almacenar el resultado en una nueva variable.
  - La nueva variable, deberá "imprimirse" dentro de una etiqueta vacía en la sección de "Resultados".

Ejemplo:

```
<html>
  <head>
    <script>
      function concatenar() {
        
        //Comentario: Solo se escribe el código importante

        var campoEjemplo = document.getElementById("campo-ejemplo").value;

        var nuevaVariable = campoEjemplo + "con el signo +, concateno esta cadena sin sentido para este ejemplo.";

        document.getElementById("label-resultado").innerHTML = nuevaVariable;
      }
    </script>
  </head>
  <body>

    <!-- Comentario: Solo se escribe el código importante -->
    <input type="text" id="campo-ejemplo" />

    <input type="submit" value="Enviar" onclick="concatenar()" />

    <label id="label-resultado"></label>
  </body>
</html>
```
