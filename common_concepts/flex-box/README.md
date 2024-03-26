# Propiedades de Flexbox

Flexbox es un modelo de diseño unidimensional que permite distribuir el espacio entre los elementos de un contenedor y alinearlos de manera eficiente incluso cuando sus tamaños son desconocidos o dinámicos.

Vamos a dividir las propiedades de Flexbox en dos categorías: propiedades del contenedor y propiedades de los elementos.

## Propiedades del contenedor

Para todos los ejemplos, consideraremos el siguiente HTML:

```html
<div class="contenedor">
  <div class="elemento">Elemento 1</div>
  <div class="elemento">Elemento 2</div>
  <div class="elemento">Elemento 3</div>
</div>
```

### display

La propiedad `display` es la que nos permite activar el modelo de diseño de Flexbox. Para ello, debemos asignarle el valor `flex` al contenedor.

```css
.contenedor {
  display: flex; /* flex | inline-flex */
}
```

### flex-direction

La propiedad `flex-direction` establece la dirección en la que los elementos se van a distribuir en el contenedor. Puede tomar uno de los siguientes valores:

- `row`: los elementos se distribuyen en la misma dirección que el texto. (default)
- `row-reverse`: los elementos se distribuyen en la dirección opuesta al texto.
- `column`: los elementos se distribuyen de arriba hacia abajo.
- `column-reverse`: los elementos se distribuyen de abajo hacia arriba.

```css
.contenedor {
  flex-direction: row; /* row | row-reverse | column | column-reverse */
}
```

### flex-wrap

La propiedad `flex-wrap` establece si los elementos se van a distribuir en una sola línea o en varias líneas. Puede tomar uno de los siguientes valores:

- `nowrap`: todos los elementos se distribuyen en una sola línea. (default)
- `wrap`: los elementos se distribuyen en varias líneas si es necesario.
- `wrap-reverse`: los elementos se distribuyen en varias líneas en dirección opuesta si es necesario.

```css
.contenedor {
  flex-wrap: wrap; /* nowrap | wrap | wrap-reverse */
}
```

### flex-flow

La propiedad `flex-flow` es un shorthand(propiedad abreviada) que combina las propiedades `flex-direction` y `flex-wrap` en una sola declaración.

```css
.contenedor {
  flex-flow: column-reverse wrap-reverse; /*<flex-direction> || <flex-wrap>*/
}
```

En este caso, los elementos se distribuirán de abajo hacia arriba (column-reverse) y en varias líneas en dirección opuesta (wrap-reverse) si es necesario. Y se hace incapie en "si es necesario" porque si los elementos caben en una sola línea, no se distribuirán en varias líneas. ¿Qué hace que los elementos quepan en una sola linea? El tamaño de los elementos y el tamaño del contenedor. Si deliberadamente se establece un tamaño para los elementos que no les permite caber en una sola línea, entonces se distribuirán en varias líneas.

### justify-content

La propiedad `justify-content` alinea los elementos a lo largo del eje principal del contenedor. Puede tomar uno de los siguientes valores:

- `flex-start`: los elementos se alinean al principio del contenedor.
- `flex-end`: los elementos se alinean al final del contenedor.
- `center`: los elementos se alinean en el centro del contenedor.
- `space-between`: los elementos se distribuyen de manera uniforme en el contenedor.
- `space-around`: los elementos se distribuyen de manera uniforme en el contenedor con espacios iguales alrededor de ellos.

```css
.contenedor {
  justify-content: space-between; /* flex-start | flex-end | center | space-between | space-around */
}
```

### align-items

La propiedad `align-items` alinea los elementos a lo largo del eje transversal del contenedor. Puede tomar uno de los siguientes valores:

- `stretch`: los elementos se estiran para llenar el contenedor. (default)
- `flex-start`: los elementos se alinean al principio del contenedor. 
- `flex-end`: los elementos se alinean al final del contenedor.
- `center`: los elementos se alinean en el centro del contenedor.
- `baseline`: los elementos se alinean en la línea base del contenedor.

```css
.contenedor {
  align-items: center; /* stretch | flex-start | flex-end | center | baseline */
}
```

### align-content

La propiedad `align-content` alinea las líneas de elementos a lo largo del eje transversal del contenedor. Solo tiene efecto si los elementos se distribuyen en varias líneas. Puede tomar uno de los siguientes valores:

- `stretch`: las líneas de elementos se estiran para llenar el contenedor. (default)
- `flex-start`: las líneas de elementos se alinean al principio del contenedor.
- `flex-end`: las líneas de elementos se alinean al final del contenedor.
- `center`: las líneas de elementos se alinean en el centro del contenedor.
- `space-between`: las líneas de elementos se distribuyen de manera uniforme en el contenedor.

```css
.contenedor {
  align-content: center; /* stretch | flex-start | flex-end | center | space-between */
}
```

## Propiedades de los elementos

### order

La propiedad `order` establece el orden en el que los elementos se van a distribuir en el contenedor. Por defecto, todos los elementos tienen un valor de `0`. Puede tomar cualquier valor entero, positivo o negativo.

```css
.elemento:nth-child(2) {
  order: 1;
}
```

En este caso, el segundo elemento se distribuirá después del primer elemento.

### flex-grow