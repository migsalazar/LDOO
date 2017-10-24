# Laboratorio 9

## Patrón Singleton

**Objetivo**: Al finalizar las actividades de este laboratorio, deberás ser capaz de comprender la finalidad de el patrón Singleton.

## Preparación

La descripción de este laboratorio parte del supuesto que ya se cuenta con la versión de NetBeans (EE) y que incluye un contenedor Web GlassFish o Apache Tomcat atendiendo un puerto de escucha 8080.

En este laboratorio se reconstruirá el escenario del Laboratorio 7. A la práctica del Laboratorio 7, agregaremos una pequeña funcionalidad de logging de eventos.

## Actividad 1 - Ajuste de proyecto de Laboratorio 7

1.- Crear un proyecto de tipo Java Web en NetBeans de nombre `laboratorio9`.

2.- Elimina el archivo `index.html` que crea por defecto NetBeans y que se encuentra dentro de la carpeta Web Pages.

3.- Utiliza los archivos completos del `Laboratorio7`.

## Actividad 2 - Construcción de Singleton

Construye la clase `laboratorio9.utils.Log` con la estructura como se muestra en el siguiente diagrama:

<img src="https://github.com/migsalazar/DOO201709/blob/master/docs/assets/week9-img/01.png" width="200" />

*Nota: La propiedad `fileName` es `final` y no `static`.*

- `Log(String fileName)`: "Settear" la propiedad `fileName` en el constructor con el valor del argumento de entrada.
- `getInstance`: Validar si existe la instancia. Si existe, retornarla. De no existir, crear una nueva y retornarla.
- `write(String message)`: Este método deberá escribir un archivo de texto como sigue:

```java
try {
            try (BufferedWriter br = new BufferedWriter(new FileWriter(fileName, true))) { 
                        DateFormat dateFormat = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
                        Calendar cal = Calendar.getInstance();

                        //Create the name of the file from the path and current time
                        String data = "\n" + dateFormat.format(cal.getTime()) + ": " + message ;
                        br.write(data);
            }
}
catch(Exception e) { }
```

## Actividad 3 - Implementación de Logging

Añade la llamada al método write de la clase anterior en todos los catch y finalizaciones de métodos. 

- En cada catch introduce como mensaje el resultado de
- En cada finalización de los métodos o en cada finalización de if, introduce algun mensaje descriptivo relativo a lo que realice el método.

# Pruebas

Realiza las pruebas para todos los escenarios mencionados en el laboratorio 7

# Preguntas

- ¿Qué ventajas identificas con el uso de un sistema de Logging de eventos?
- ¿Qué ventajas tienes al utilizar una clase singleton?
- ¿Qué "pros" y "contras" identificas al utilizar singleton vs clases estáticas?

# Especificaciones del Reporte

- El reporte debe incluir una portada con tus datos al inicio.
- El reporte debe contener la descripción de los pasos realizados para llevar a cabo la práctica del laboratorio. Cada paso debe contar con un fragmento de código o imagen que ilustre lo descrito. Piense en el reporte como una explicación para alguien ajeno al tema y detalle los puntos técnicos que sean necesarios.
- Contesta las preguntas mencionadas en la sección anterior.
- Comprime en un archivo .zip el directorio raíz de la práctica.
- El envío de la práctica debe incluir dos archivos: El reporte en PDF y el archivo .zip con el código fuente del proyecto.
