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
