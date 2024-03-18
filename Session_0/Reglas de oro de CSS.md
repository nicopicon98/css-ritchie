# Reglas de oro de CSS

## 1. Selectores

Los selectores son patrones que se utilizan para seleccionar los elementos a los que se les aplicarán los estilos. Los selectores pueden ser de diferentes tipos:

- **Selectores de etiqueta**: Son los más básicos y se utilizan para seleccionar elementos HTML específicos.
  Ejemplo:

  ```css
  p {
    color: red;
  }
  ```

- **Selectores de clase**: Se utilizan para seleccionar elementos que tienen un atributo de clase específico.
  Ejemplo:

  ```css
  .miClase {
    color: red;
  }
  ```

- **Selectores de ID**: Se utilizan para seleccionar elementos que tienen un atributo de ID específico.
  Ejemplo:

  ```css
  #miID {
    color: red;
  }
  ```

- **Selectores de atributo**: Se utilizan para seleccionar elementos que tienen un atributo específico.
  Ejemplo:

  ```css
  input[type="text"] {
    /* Selecciona todos los elementos <input> con el atributo type="text" */
    color: red;
  }
  input[type="password"] {
    /* Selecciona todos los elementos <input> con el atributo type="password" */
    color: red;
  }
  input[type="email"] {
    /* Selecciona todos los elementos <input> con el atributo type="email" */
    color: red;
  }
  input[type="number"] {
    /* Selecciona todos los elementos <input> con el atributo type="number" */
    color: red;
  }
  input[type="submit"] {
    /* Selecciona todos los elementos <input> con el atributo type="submit" */
    color: red;
  }
  button[type="button"] {
    /* Selecciona todos los elementos <button> con el atributo type="button" */
    color: red;
  }
  button[type="submit"] {
    /* Selecciona todos los elementos <button> con el atributo type="submit" */
    color: red;
  }
  a[href="https://www.google.com"]
  {
    /* Selecciona todos los elementos <a> con el atributo href="https://www.google.com" */
    color: red;
  }
  figure[role="img"] {
    /* Selecciona todos los elementos <figure> con el atributo role="img" */
    color: red;
  }
  ```

- **Selectores de pseudo-clase**: Se utilizan para seleccionar elementos que están en un estado específico.
  Ejemplo:

  ```css
  a:hover {
    /* Cuando el puntero del ratón está sobre el enlace */
    color: red;
  }
  a:visited {
    /* Cuando el enlace ha sido visitado */
    color: red;
  }
  a:active {
    /* Al hacer clic en el enlace, pero antes de que se complete la acción */
    color: red;
  }
  a:focus {
    /* Al hacer clic en el enlace */
    color: red;
  }
  a:link {
    /* Por defecto */
    color: red;
  }
  li:first-child {
    /* Selecciona el primer elemento <li> de su contenedor */
    color: red;
  }
  li:last-child {
    /* Selecciona el último elemento <li> de su contenedor */
    color: red;
  }
  li:nth-child(2) {
    /* Selecciona el segundo elemento <li> de su contenedor */
    color: red;
  }
  ```

- **Selectores de pseudo-elemento**: Se utilizan para seleccionar partes de un elemento que no están representadas por un elemento real.
  Ejemplo:
  ```css
  p::first-line {
    /* Selecciona la primera línea de un elemento <p> */
    color: red;
  }
  p::first-letter {
    /* Selecciona la primera letra de un elemento <p> */
    color: red;
  }
  p::before {
    /* Inserta contenido antes de un elemento <p> */
    content: "Antes de";
  }
  p::after {
    /* Inserta contenido después de un elemento <p> */
    content: "Después de";
  }
  p::selection {
    /* Selecciona el texto seleccionado */
    color: red;
    background-color: yellow;
  }
  a::first-line {
    /* Selecciona la primera línea de un elemento <a> */
    color: red;
  }
  input::placeholder {
    /* Selecciona el texto de marcador de posición de un elemento <input> */
    color: red;
  }
  li::marker {
    /* Selecciona el marcador de un elemento <li> */
    color: red;
  }
  ```

Nota: Los selectores de clase y los selectores de ID son los más utilizados en CSS.

## 2. Especificidad:

La especificidad se puede considerar como un conjunto de cuatro valores: (0-0-0-0), de izquierda a derecha, que representan diferentes tipos de selectores. A veces, se añade un quinto valor al principio para representar el uso de !important.

- **!important 1, 0, 0, 0, 0**:

  ```css
  .my-class {
    color: red !important;
  }
  ```

  - Reescribe cualquier estilo.
  - Para el navegador es de alta prioridad.
  - Hay que evitarlo o usarlo con mucha precaución.

- **Estilos en línea 0, 1, 0, 0, 0**:

  ```css
  <p style="color: red;">
  ```

  - Los estilos en línea aplicaran estilos nuevos sobre otros, aunque ya tengan clases o IDs.

- **#ID 0, 0, 1, 0, 0**:

  ```css
  #my-id {
    color: red;
  }
  ```

  - Los ID tienen mayor peso que las clases y etiquetas.
  - Pero al ser únicos es preferible usarlos para funcionalidad que para estilos.

- **Clases, atributos y pseudo clases 0, 0, 0, 1, 0**

  ```css
  .my-class {
    color: red;
  }
  ```

  - Es mejor usar clases para dar estilos, combinados con una metodología como [BEM](https://bem.info/) tendrás una especificidad manejable.

- **Elementos 0, 0, 0, 0, 1**
  ```css
  p {
    color: red;
  }
  ```
  - Los estilos aplicados a los elementos son los más básicos y fáciles de reescribir.

## 3. Uso del important!

Cuando se emplea important en una declaración de estilo, esta declaración sobrescribe a cualquier otra. Aunque técnicamente !important no tiene nada que ver con especificidad, interactúa directamente con esta. Sin embargo, el uso de !important es una mala práctica y debería evitarse porque hace que el código sea más difícil de depurar al romper la cascada natural de las hojas de estilo. Cuando dos declaraciones en conflicto con el !important son aplicadas al mismo elemento, se aplicará la declaración con mayor especificidad.

### Nota: Algunas reglas de oro para el uso de !important son las siguientes:

- Busca siempre una manera de emplear la especificidad antes de considerar el uso de !important.
- Usa !important solo en declaraciones específicas de CSS que sobrescriban CSS externo (de librerías externas como Bootstrap o normalize.css).
- Nunca uses !important cuando estés intentando escribir un plugin/mashup, ya que esto puede llevar a conflictos con los usuarios que usen el plugin/mashup.
- Nunca uses !important en todo el código CSS.

## 4. Herencia

La herencia es una de las características más importantes de CSS. La herencia es el mecanismo por el cual un elemento hijo adquiere los estilos de su elemento padre. La herencia es una forma de propagar los estilos de un elemento a todos sus descendientes. La herencia es útil porque permite aplicar estilos a un elemento y a todos sus descendientes sin tener que aplicar estilos a cada uno de ellos individualmente.

### Nota: Algunos de los estilos que se heredan son los siguientes:

- Color del texto (color)
- Tamaño del texto (font-size)
- Estilo del texto (negrita, cursiva, subrayado, etc.) (font-style)
- Algunos estilos de fondo (como el color de fondo) (background-color)
- Algunos estilos de borde (como el ancho del borde) (border-width)
- Algunos estilos de lista (como el estilo de la lista) (list-style-type)
- Algunos estilos de tabla (como el espaciado de la tabla) (border-spacing)

### Nota: Algunos de los estilos que no se heredan son los siguientes:

- Altura de la línea (line-height)
- Margen y relleno (margin y padding)
- Relleno (background)
- Ancho del borde (border-width)
- Posición (position)
- Z-index (z-index)
- Visibilidad (visibility)
- Color de fondo (background-color)
- Color del borde (border-color)
- Ancho del borde (border-width)
- Estilo del borde (border-style)
- Opacidad (opacity)
- Transformaciones (transform)
- Filtros (filter)
- Flexbox (flex)
- Grid (grid)
- Columnas (columns)
- Tablas (table)
- Posicionamiento (position)
- Flotación (float)
- Clear (clear)
- Overflow (overflow)
- Clip (clip)
- Page-break (page-break)
- Marcas de corte (marks)
- Contenido generado (content)
- Contenido insertado (inserted content)
- Contenido reemplazado (replaced content)
- Contenido de la lista (list-style)

## 5. Box Model

El modelo de caja es una de las características más importantes de CSS. El modelo de caja es una caja rectangular que rodea a un elemento HTML y define el espacio que ocupa el elemento. El modelo de caja consta de cuatro partes: el contenido, el relleno, el borde y el margen.

### Nota: Las partes del modelo de caja son las siguientes:

- **Contenido**: Es el área donde se muestra el contenido del elemento, como el texto o las imágenes.
  ```css
  .miClase {
    width: 100px;
    height: 100px;
  }
  ```
- **Relleno**: Es el espacio entre el contenido y el borde. El relleno es transparente y no tiene color de fondo.
  ```css
  .miClase {
    padding: 10px;
  }
  ```
- **Borde**: Es el borde que rodea el relleno y el contenido. El borde tiene un color, un ancho y un estilo.
  ```css
  .miClase {
    border: 1px solid black;
  }
  ```
- **Margen**: Es el espacio entre el borde y los elementos adyacentes. El margen es transparente y no tiene color de fondo.
  ```css
  .miClase {
    margin: 10px;
  }
  ```

### Nota: Algunas propiedades del modelo de caja son las siguientes:

- **Ancho y alto**: Se utilizan para establecer el ancho y el alto del contenido del elemento.
  ```css
  .miClase {
    width: 100px;
    height: 100px;
  }
  ```
- **Relleno**: Se utiliza para establecer el relleno del elemento.
  ```css
  .miClase {
    padding: 10px;
  }
  ```
- **Borde**: Se utiliza para establecer el borde del elemento.
  ```css
  .miClase {
    border: 1px solid black;
  }
  ```
- **Margen**: Se utiliza para establecer el margen del elemento.
  ```css
  .miClase {
    margin: 10px;
  }
  ```

## 6. Posicionamiento

El posicionamiento es una de las características más importantes de CSS. El posicionamiento se utiliza para controlar la ubicación de los elementos en una página web. Hay cuatro tipos de posicionamiento en CSS: estático, relativo, absoluto y fijo.

### Nota: Los tipos de posicionamiento en CSS son los siguientes:

- **Posicionamiento estático**: Es el tipo de posicionamiento predeterminado en CSS. Los elementos con posicionamiento estático no se ven afectados por las propiedades de posicionamiento (top, right, bottom, left).

  ```css
  .miClase {
    position: static;
  }
  ```

- **Posicionamiento relativo**: Los elementos con posicionamiento relativo se desplazan de su posición original. Los elementos con posicionamiento relativo se desplazan de su posición original, pero dejan un espacio vacío en su posición original.

  ```css
  .miClase {
    position: relative;
    top: 10px;
    left: 10px;
  }
  ```

- **Posicionamiento absoluto**: Los elementos con posicionamiento absoluto se desplazan de su posición original. Los elementos con posicionamiento absoluto se desplazan de su posición original, pero no dejan un espacio vacío en su posición original.

  ```css
  .miClase {
    position: absolute;
    top: 10px;
    left: 10px;
  }
  ```

- **Posicionamiento fijo**: Los elementos con posicionamiento fijo se desplazan de su posición original. Los elementos con posicionamiento fijo se desplazan de su posición original, pero no dejan un espacio vacío en su posición original. Además, los elementos con posicionamiento fijo se desplazan con la página cuando se desplaza.
  ```css
  .miClase {
    position: fixed;
    top: 10px;
    left: 10px;
  }
  ```

## 7. Flexbox

Flexbox es una de las características más importantes de CSS. Flexbox es un modelo de diseño unidimensional que permite distribuir los elementos en un contenedor de manera que se ajusten a diferentes tamaños de pantalla y dispositivos. Flexbox es útil para crear diseños flexibles y adaptables.

### Nota: Algunas propiedades de Flexbox son las siguientes:

- **Flex-direction**: Se utiliza para establecer la dirección principal de los elementos en el contenedor.
  ```css
  .miClase {
    flex-direction: row;
  }
  ```
- **Justify-content**: Se utiliza para alinear los elementos a lo largo del eje principal del contenedor.

  ```css
  .miClase {
    justify-content: center;
  }
  ```

- **Align-items**: Se utiliza para alinear los elementos a lo largo del eje transversal del contenedor.

  ```css
  .miClase {
    align-items: center;
  }
  ```

- **Flex-wrap**: Se utiliza para envolver los elementos en varias líneas si no caben en una sola línea.

  ```css
  .miClase {
    flex-wrap: wrap;
  }
  ```

- **Flex-flow**: Se utiliza para establecer la dirección principal y el ajuste de los elementos en el contenedor.

  ```css
  .miClase {
    flex-flow: row wrap;
  }
  ```

- **Align-content**: Se utiliza para alinear las líneas de elementos a lo largo del eje transversal del contenedor.
  ```css
  .miClase {
    align-content: center;
  }
  ```

### Nota: Tips para usar Flexbox:

- Flexbox es útil para crear diseños flexibles y adaptables.
- Flexbox es útil para crear diseños de una sola fila o columna.
- Flexbox es útil para crear diseños de varias filas o columnas.
- Flexbox es útil para crear diseños de cuadrícula.
- Flexbox es útil para crear diseños de alineación de elementos.
- Flexbox es útil para crear diseños de centrado de elementos.
- Flexbox es útil para crear diseños de distribución de espacio.
- Flexbox es útil para crear diseños de alineación de líneas.
- Flexbox es útil para crear diseños de envoltura de elementos.

## Nota: Como centrar elementos con Flexbox:

- **Centrar elementos horizontalmente**: Se utiliza justify-content: center; en el contenedor.

  ```css
  .miClase {
    display: flex;
    justify-content: center;
  }
  ```

- **Centrar elementos verticalmente**: Se utiliza align-items: center; en el contenedor.

  ```css
  .miClase {
    display: flex;
    align-items: center;
  }
  ```

- **Centrar elementos horizontal y verticalmente**: Se utiliza justify-content: center; y align-items: center; en el contenedor.
  ```css
  .miClase {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  ```

## 8. Grid

Grid es una de las características más importantes de CSS. Grid es un modelo de diseño bidimensional que permite distribuir los elementos en un contenedor de manera que se ajusten a diferentes tamaños de pantalla y dispositivos. Grid es útil para crear diseños flexibles y adaptables.

### Nota: Algunas propiedades de Grid son las siguientes:

- **Grid-template-columns**: Se utiliza para establecer el ancho de las columnas en el contenedor.

  ```css
  .miClase {
    display: grid;
    grid-template-columns: 100px 100px 100px;
  }
  ```

- **Grid-template-rows**: Se utiliza para establecer el alto de las filas en el contenedor.

  ```css
  .miClase {
    display: grid;
    grid-template-rows: 100px 100px 100px;
  }
  ```

- **Grid-template-areas**: Se utiliza para establecer el diseño de las áreas en el contenedor.

  ```css
  .miClase {
    display: grid;
    grid-template-areas:
      "header header header"
      "main main main"
      "footer footer footer";
  }
  ```

- **Grid-gap**: Se utiliza para establecer el espacio entre las filas y las columnas en el contenedor.

  ```css
  .miClase {
    display: grid;
    grid-gap: 10px;
  }
  ```

- **Justify-items**: Se utiliza para alinear los elementos a lo largo del eje principal del contenedor.

  ```css
  .miClase {
    display: grid;
    justify-items: center;
  }
  ```

- **Align-items**: Se utiliza para alinear los elementos a lo largo del eje transversal del contenedor.

  ```css
  .miClase {
    display: grid;
    align-items: center;
  }
  ```

- **Justify-content**: Se utiliza para alinear las columnas a lo largo del eje principal del contenedor.

  ```css
  .miClase {
    display: grid;
    justify-content: center;
  }
  ```

- **Align-content**: Se utiliza para alinear las filas a lo largo del eje transversal del contenedor.
  ```css
  .miClase {
    display: grid;
    align-content: center;
  }
  ```

### Nota: Tips para usar Grid:

- Grid es útil para crear diseños flexibles y adaptables.
- Grid es útil para crear diseños de una sola fila o columna.
- Grid es útil para crear diseños de varias filas o columnas.
- Grid es útil para crear diseños de cuadrícula.
- Grid es útil para crear diseños de alineación de elementos.
- Grid es útil para crear diseños de centrado de elementos.
- Grid es útil para crear diseños de distribución de espacio.
- Grid es útil para crear diseños de alineación de líneas.
- Grid es útil para crear diseños de envoltura de elementos.

## 9. Media Queries

Las media queries son una de las características más importantes de CSS. Las media queries se utilizan para aplicar estilos a diferentes tamaños de pantalla y dispositivos. Las media queries son útiles para crear diseños flexibles y adaptables.

### Nota: Algunas propiedades de Media Queries son las siguientes:

- **Ancho de la pantalla**: Se utiliza para aplicar estilos a diferentes anchos de pantalla.

  ```css
  @media screen and (max-width: 600px) {
    .miClase {
      background-color: lightblue;
    }
  }
  ```

- **Orientación de la pantalla**: Se utiliza para aplicar estilos a diferentes orientaciones de pantalla.

  ```css
  @media screen and (orientation: landscape) {
    .miClase {
      background-color: lightblue;
    }
  }
  ```

- **Resolución de la pantalla**: Se utiliza para aplicar estilos a diferentes resoluciones de pantalla.

  ```css
  @media screen and (min-resolution: 300dpi) {
    .miClase {
      background-color: lightblue;
    }
  }
  ```

- **Relación de aspecto de la pantalla**: Se utiliza para aplicar estilos a diferentes relaciones de aspecto de pantalla.

  ```css
  @media screen and (aspect-ratio: 16/9) {
    .miClase {
      background-color: lightblue;
    }
  }
  ```

- **Tipo de dispositivo**: Se utiliza para aplicar estilos a diferentes tipos de dispositivos.
  ```css
  @media screen and (device-type: screen) {
    .miClase {
      background-color: lightblue;
    }
  }
  ```

### Nota: Tips para usar Media Queries:

- Las media queries son útiles para aplicar estilos a diferentes tamaños de pantalla y dispositivos.
- Las media queries son útiles para crear diseños flexibles y adaptables.

## 10. Animaciones

Las animaciones son una de las características más importantes de CSS. Las animaciones se utilizan para crear efectos de animación en los elementos de una página web. Las animaciones son útiles para crear diseños interactivos y atractivos.

### Nota: Algunas propiedades de Animaciones son las siguientes:

- **Nombre de la animación**: Se utiliza para establecer el nombre de la animación.

  ```css
  @keyframes miAnimacion {
    0% {
      background-color: red;
    }
    100% {
      background-color: yellow;
    }
  }
  ```

- **Duración de la animación**: Se utiliza para establecer la duración de la animación.

  ```css
  .miClase {
    animation-name: miAnimacion;
    animation-duration: 4s;
  }
  ```

- **Dirección de la animación**: Se utiliza para establecer la dirección de la animación.

  ```css
  .miClase {
    animation-name: miAnimacion;
    animation-direction: alternate;
  }
  ```

- **Iteración de la animación**: Se utiliza para establecer el número de veces que se repite la animación.

  ```css
  .miClase {
    animation-name: miAnimacion;
    animation-iteration-count: infinite;
  }
  ```

- **Retraso de la animación**: Se utiliza para establecer el retraso de la animación.

  ```css
  .miClase {
    animation-name: miAnimacion;
    animation-delay: 2s;
  }
  ```

- **Tiempo de relleno de la animación**: Se utiliza para establecer el tiempo de relleno de la animación.

  ```css
  .miClase {
    animation-name: miAnimacion;
    animation-fill-mode: forwards;
  }
  ```

- **Estado de la animación**: Se utiliza para establecer el estado de la animación.
  ```css
  .miClase {
    animation-name: miAnimacion;
    animation-play-state: paused;
  }
  ```

### Nota: Tips para usar Animaciones:

- Las animaciones son útiles para crear efectos de animación en los elementos de una página web.
- Las animaciones son útiles para crear diseños interactivos y atractivos.
