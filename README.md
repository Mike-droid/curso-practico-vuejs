# Curso práctico de Vue.js

## Introducción

[Repositorio del proyecto del curso](https://github.com/platzi/practico-vue)

### Creación del proyecto

Usamos el vue-cli de siempre.

[Figma del proyecto](https://www.figma.com/file/P3EL4J17QtATlH1lqYryfG/Personal-CashFlow?node-id=0%3A1)

## Setup inicial

### Splashscreen

Vue tiene un componente llamado 'suspense' que se usa cuando estamos cargando información en nuestro proyecto. Es como un recuadro gris donde vemos que estará la información.

### Header y su contenido

### Layout

## Vista

### Resumen de datos

### Agregando formato a la moneda

Podemos darle formato de moneda a los números con JS vanilla:

```javascript
const currencyFormatter = new Intl.NumberFormat("es-MX", {
  style: "currency",
  currency: "MXN",
});

amountCurrency() {
  return currencyFormatter.format(this.amountVisual);
}
```

[Documentación para Intl.NumberFormat](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Intl/NumberFormat)

### Componente del historial

### Lista del historial

### El botón para agregar

### Formulario para agregar

## Gráfico

### Creación del SVG del gráfico

Creación sencilla de un SVG estático:

```html
<template>
  <div>
    <svg viewBox="0 0 300 200">
      <line
        stroke="#c4c4c4"
        stroke-width="2"
        x1="0"
        y1="100"
        x2="300"
        y2="100"
      />
      <polyline
        fill="none"
        stroke="#0689b0"
        stroke-width="2"
        points="0,0 100,100 200,100 300,200"
      />
      <line
        stroke="#04b500"
        stroke-width="2"
        x1="200"
        y1="0"
        x2="200"
        y2="200"
      />
    </svg>
    <p>Últimos 30 días</p>
  </div>
</template>

<style scoped>
svg {
  width: 100%;
}

p {
  text-align: center;
}
</style>
```

- [SVG Mozilla docs](https://developer.mozilla.org/es/docs/Web/SVG)
- [polyline Mozilla docs](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/polyline)

### Creación de las coordenadas en el gráfico

### Creación de la lógica del gráfico

### Creando la interacción con el gráfico
