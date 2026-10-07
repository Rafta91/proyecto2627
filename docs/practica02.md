## Práctica 02

- **Creación del archivo `ut02p02.html`:**

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <title>Unidad 2: Tarea 2</title>
    <style>
        @import "https://cdn.jsdelivr.net/npm/bulma@1.0.4/css/bulma.min.css";
    </style>
</head>
<body>
    <form method="post" action="ut02p02a.php">
        SUELDO:<input class="input" id="num" name="sueldo" type="number" min="1001" required>
        CARGO:<select class="select" name="cargo">
            <option>Base</option>
            <option>Directivo</option>
            <option>Alto cargo</option>
        </select>
        <input class="button is-link" type="submit" value="ENVIAR">
    </form>

</body>
</html>
```

  - Contiene un formulario con SUELDO (`input`) que necesita un valor mínimo (`min`) de 1001 y es requerido (`required`).
  - CARGO es un valor seleccionable (`select`) entre tres opciones: Base, Directivo y Alto cargo. Por defecto es Base.
  - Ambos valores se envían a `ut02p02a.php` como valores de variables recogidas con `$_POST`.


- **Creación del archivo `ut02p02a.php`:** 

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <title>Unidad 2: Tarea 2A</title>
    <style>
        @import "https://cdn.jsdelivr.net/npm/bulma@1.0.4/css/bulma.min.css";
    </style>
</head>
<body>

    <?php 
        $sueldo = $_POST['sueldo'] ?? 1001;
        $cargo = $_POST['cargo'] ?? "Base";

        if ($cargo == "Base") { $complemento = 10; }
        else if ($cargo == "Directivo") { $complemento = 15; }
        else { $complemento = 20; }

        $sueldoFinal = (int)$sueldo + ((int)$sueldo * $complemento/100);
    ?>

    <p>El sueldo base es de <?php echo "$sueldo"; ?>€</p>
    <p>El complemento es del <?php echo "$complemento"; ?>%</p>
    <p>El sueldo final es de <?php echo "$sueldoFinal"; ?>€</p>
</body>
</html>
```

  - `$sueldo` y `$cargo` recogen los valores del formulario de la página anterior.
  - Si no se les envia un valor les asigna uno por defecto.
  - Dependiendo del cargo el complemento será de 10%, 15% o 20%.
  - Se muestra mediante párrafos HTML el sueldo, el complemento y el sueldo final.