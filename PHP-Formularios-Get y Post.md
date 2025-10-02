Tenemos los métodos **Get** y **Post** para almacenar en arrays y mandar información a otro archivo o fichero, esto mismo es importante , ya que funciona como un medio de comunicación entre el usuario e servidor, pero estos mismo puede ser información privada como pública.

- `$_GET :` Información Pública
- `$_POST :` Información Privada

Para ello resolveremos ciertos ejercicios con formularios, para entender que como se transmite y que se puede hacer con esta información.

**Estructura:**
- Formularios
	- Públicos
		- index.html
		- procesarDatosGet.php
	- Privados
		- index.html
		- procesarDatosPost.php

Crea las siguientes páginas. Es importante respetar el nombre de las páginas especificadas en cada punto. 

----
# Ejemplos

## Públicos

**Estructura:**
- Públicos
	- index.html
	- procesarDatosGet.php

### Index.html
```HTML
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <title>Inicio</title>
    <link rel="stylesheet" href="/public/css/style.css" />
    <script src="/public/js/main.js"></script>
  </head>
  <body>
    <h1>FORMULARIO</h1>
    <form name="form" method="GET" action="procesarDatos.php">
      <div>
        <label>Nombre: </label>
        <input type="text" name="nombre" value="" />
      </div>
      <div>
        <label>Curso: </label>
        <input type="radio" id="primero" name="curso" value="primero" /><label
          for="primero"
          >Primero</label
        >
        <input type="radio" id="segundo" name="curso" value="segundo" /><label
          for="segundo"
          >Segundo</label
        >
      </div>
      <div>
        <input type="submit" name="Enviar" />
      </div>
    </form>
  </body>
</html>

```

### procesarDatosGet.php

```php
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <title>Datos procesados</title>
</head>
<body>
  <h1>Resultado del formulario</h1>

  <?php
  if (isset($_GET['nombre']) && isset($_GET['curso'])) {
      $nombre = htmlspecialchars($_GET['nombre']);
      $curso = htmlspecialchars($_GET['curso']);
      echo "<p>👤 Nombre: <strong>$nombre</strong></p>";
      echo "<p>📚 Curso seleccionado: <strong>$curso</strong></p>";
  } else {
      echo "<p>⚠️ No se han recibido todos los datos.</p>";
  }
  ?>
</body>
</html>

```


---
## Privados

### index.html

```html
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <title>Inicio</title>
    <link rel="stylesheet" href="/public/css/style.css" />
    <script src="/public/js/main.js"></script>
  </head>
  <body>
    <h1>FORMULARIO</h1>
    <form name="form" method="POST" action="procesarDatosPost.php">
  <div>
    <label>Nombre: </label>
    <input type="text" name="nombre" value="" />
  </div>
  <div>
    <label>Curso: </label>
    <input type="radio" id="primero" name="curso" value="primero" />
    <label for="primero">Primero</label>
    <input type="radio" id="segundo" name="curso" value="segundo" />
    <label for="segundo">Segundo</label>
  </div>
  <div>
    <input type="submit" name="Enviar" />
  </div>
</form>
  </body>
</html>
```

### procesarDatosPost.php

```php
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <title>Datos procesados</title>
</head>
<body>
  <h1>Resultado del formulario</h1>
        <?php
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    if (isset($_POST['nombre']) && isset($_POST['curso'])) {
        $nombre = htmlspecialchars($_POST['nombre']);
        $curso = htmlspecialchars($_POST['curso']);

        echo "<h1>Datos recibidos</h1>";
        echo "<p>👤 Nombre: <strong>$nombre</strong></p>";
        echo "<p>📚 Curso: <strong>$curso</strong></p>";
    } else {
        echo "<p>⚠️ Faltan datos en el formulario.</p>";
    }
} else {
    echo "<p>❌ Este formulario debe enviarse por POST.</p>";
}
?>

  </body>
</html>

```

---
# Ejercicios

1. Crear una página **/comprobarSiContiene** que compruebe si una frase proporcionada por el usuario contiene una palabra determinada (también introducida por el usuario). Por ejemplo, Si ingresamos la frase "Estoy aprendiendo a programar" en el formulario y la palabra "programar" en el otro campo, el programa imprimirá el siguiente resultado: Contiene la palabra 'programar' .
   <br>
2. Crear una página **/obtenerHora que permita seleccionar una zona horaria e imprima la fecha y hora actual en esa zona horaria**.
   <br>
3. Crear una página **/epochAtimestamp que permita convertir un número expresado en Unix epoch a Timestamp (fecha y hora en UTC) y viceversa.
<br>
4. Crea una página en la que el usuario meta su fecha de nacimiento, expresada por 3 selectores: dia, mes y año. Debe indicar el número exácto de años que tiene la persona. Es decir, si hoy mete la fecha 30/11/1990, debe indicar que tiene 34 años (aún le queda un poco para cumplir los 35).