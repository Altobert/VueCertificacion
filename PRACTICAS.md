# Prácticas para la Certificación Vue.js (Nivel 1)

Este archivo contiene ejercicios cortos y simples, con enunciado, para practicar cada uno de los temas del examen de certificación **Vue.js Developer Certification - Level 1**. Cada ejercicio está pensado para resolverse en pocos minutos, usando un componente `.vue` nuevo o el propio `App.vue` del proyecto.

> Sugerencia de trabajo: crea un componente por ejercicio dentro de `src/components/practicas/` (por ejemplo `Ej01Spa.vue`) y móntalo temporalmente en `App.vue` para probarlo.

---

## 1. Creating a Vue Application

### Ejercicio 1.1 — Como SPA (Vite/CLI)
Usando este mismo proyecto (creado con Vite), crea un componente `Saludo.vue` que muestre un `<h1>` con el texto "Hola, Vue 3". Impórtalo y móntalo en `App.vue`. Verifica que `main.ts` esté creando la app con `createApp(App).mount('#app')`.

### Ejercicio 1.2 — Usando CDN
Crea un archivo `cdn.html` independiente (fuera del proyecto Vite) que cargue Vue desde un CDN mediante `<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>`, defina una app con `Vue.createApp({...})` y muestre un contador que empiece en 0. No debe usar ningún paso de build.

### Ejercicio 1.3 — Usando el CLI de creación de proyectos
Sin usar este proyecto, ejecuta en una carpeta nueva `npm create vue@latest` (o `vue create` si usas Vue CLI clásico). Explora la estructura generada y anota en 3-4 líneas qué archivos/carpetas se crearon y para qué sirve cada uno (`main.ts`, `App.vue`, `src/`, `public/`, `vite.config.ts`).

---

## 2. Reactivity Fundamentals

### Ejercicio 2.1 — Options API
Crea un componente `ContadorOptions.vue` usando **Options API** con:
- Un dato reactivo `contador` inicializado en 0.
- Una propiedad `computed` llamada `contadorDoble` que devuelva `contador * 2`.
- Un botón que incremente `contador` en 1 al hacer clic.
- Muestra ambos valores en el template.

### Ejercicio 2.2 — Composition API
Repite el ejercicio anterior como `ContadorComposition.vue`, pero usando **Composition API** con `<script setup>`, `ref()` para `contador` y `computed()` para `contadorDoble`.

### Ejercicio 2.3 — `ref` vs `reactive`
Crea un componente que declare un objeto `usuario` de dos formas distintas: una vez con `reactive({ nombre: '', edad: 0 })` y otra con `ref({ nombre: '', edad: 0 })`. Enlaza ambos a inputs de texto/número y explica en un comentario qué diferencia notas al acceder a las propiedades en el `<script>` (uso de `.value`) frente al `<template>`.

---

## 3. Template Syntax

### Ejercicio 3.1 — Interpolación de texto y `v-bind`
Crea un componente con un dato `titulo` (string) y `urlImagen` (string). Muestra `titulo` interpolado en un `<h2>` y usa `v-bind:src` (o `:src`) para mostrar una imagen con esa URL. Agrega también un atributo `title` enlazado al mismo `titulo`.

### Ejercicio 3.2 — Class and Style Bindings
Crea un componente con un booleano `activo` y un botón que lo alterne. Enlaza dinámicamente:
- La clase `activo` usando el **object syntax** de `:class` (`{ activo: activo }`).
- El estilo `color` usando `:style` (verde si `activo` es `true`, rojo si es `false`).

### Ejercicio 3.3 — List Rendering
Crea un arreglo reactivo `frutas` con al menos 4 elementos (objetos `{ id, nombre }`). Renderiza una lista `<ul>` con `v-for`, usando `:key="fruta.id"`. Agrega un input que permita agregar una nueva fruta al arreglo.

### Ejercicio 3.4 — Conditional Rendering
Usando el arreglo del ejercicio anterior, muestra un mensaje "No hay frutas" con `v-if` cuando el arreglo esté vacío, y la lista con `v-else`. Agrega además un botón que muestre/oculte un panel de detalles usando `v-show` (y explica en un comentario por qué aquí conviene `v-show` en vez de `v-if`).

---

## 4. Event Handling

### Ejercicio 4.1 — Handlers inline vs method
Crea un botón que use un **handler inline** para mostrar un `alert('Clic!')`, y otro botón que llame a un **method handler** (`saludar`) definido en el componente que haga lo mismo.

### Ejercicio 4.2 — Acceso al objeto `$event`
Crea un input de texto y, en el evento `@input`, muestra en consola el valor tipiado usando el objeto de evento nativo, tanto con un handler inline (`@input="valor = $event.target.value"`) como pasando `$event` explícitamente a un método.

### Ejercicio 4.3 — Modificadores de eventos
Crea un formulario simple con un botón "Enviar" y:
- Usa `@submit.prevent` para evitar el refresco de página.
- Usa `@click.stop` en un botón anidado dentro de un `div` que también tiene un `@click`, y demuestra que el clic no se propaga.
- Agrega un input de texto que solo reaccione a la tecla Enter usando `@keyup.enter`.

---

## 5. Form Input Bindings

### Ejercicio 5.1 — `v-model` en distintos tipos de input
Crea un formulario con:
- Un `<input type="text">` enlazado con `v-model` a `nombre`.
- Un `<input type="checkbox">` enlazado a un booleano `aceptaTerminos`.
- Un grupo de `<input type="radio">` enlazado a `colorFavorito` (mínimo 3 opciones).
- Un `<select>` enlazado a `pais`, con al menos 3 `<option>`.

Muestra todos los valores en tiempo real debajo del formulario.

### Ejercicio 5.2 — Modificadores de `v-model`
Sobre el input de `nombre` del ejercicio anterior, agrega y prueba:
- `.trim` para eliminar espacios al inicio/fin.
- `.lazy` para que el valor se actualice solo al perder el foco (`change`) en vez de en cada tecla.
Crea un input numérico aparte con `v-model.number` y verifica que el valor guardado sea de tipo `number` y no `string`.

---

## 6. Watchers

### Ejercicio 6.1 — `watch` simple
Crea un `ref` llamado `pregunta` enlazado a un input de texto. Usa `watch` para que, cada vez que `pregunta` cambie y no esté vacía, se imprima en consola "Pensando en tu pregunta...".

### Ejercicio 6.2 — `watch` vs `computed`
Crea dos `ref`: `precio` y `cantidad`. Implementa el `total` de dos formas y compara: una con `computed` y otra con `watch` que actualice manualmente una variable `totalWatch`. Explica en un comentario cuándo usarías cada enfoque.

### Ejercicio 6.3 — Fuentes múltiples, `deep` e `immediate`
Crea un objeto reactivo `filtro = { categoria: '', precioMax: 0 }`. Usa un único `watch` que observe el objeto completo con `{ deep: true, immediate: true }` y loguee los cambios. Luego crea otro `watch` que observe un arreglo de fuentes `[categoria, precioMax]` por separado (usando funciones getter) y compara el comportamiento.

---

## 7. Lifecycle Hooks

### Ejercicio 7.1 — Hooks básicos con Composition API
Crea un componente que registre en consola, usando `onMounted`, `onUpdated` y `onUnmounted`, cada vez que ocurre esa fase. Agrega un botón en el componente padre para mostrar/ocultar este componente (con `v-if`) y así poder ver el `unmounted`. Agrega también un dato reactivo y un botón que lo modifique para disparar `onUpdated`.

### Ejercicio 7.2 — Hooks con Options API
Repite el ejercicio 7.1 usando Options API (`mounted()`, `updated()`, `unmounted()`) y compara la sintaxis con la versión de Composition API.

### Ejercicio 7.3 — Uso práctico: petición al montar
Crea un componente que, en `onMounted`, simule una carga de datos (por ejemplo con `setTimeout` de 1 segundo) y luego actualice un `ref` `cargando` a `false` y muestre una lista de datos "recibidos".

---

## 8. Template Refs

### Ejercicio 8.1 — Ref a un elemento del DOM
Crea un input de texto con `ref="inputRef"` y un botón "Enfocar" que, al hacer clic, llame a `.focus()` sobre ese elemento usando la referencia (`ref()` en `<script setup>` con el mismo nombre).

### Ejercicio 8.2 — Ref a un componente hijo
Crea un componente hijo `Temporizador.vue` con un método `reiniciar()` y una variable interna `segundos`. Expón el método con `defineExpose`. Desde el padre, obtén una referencia al hijo con `ref` y agrega un botón que llame a `temporizadorRef.value.reiniciar()`.

---

## 9. Components

### Ejercicio 9.1 — Components Basics: props y emit
Crea un componente hijo `TarjetaProducto.vue` que reciba las props `nombre` (string) y `precio` (number), y emita un evento `agregar-carrito` con el `nombre` del producto cuando se haga clic en un botón. En el padre, escucha el evento y muestra en una lista los productos agregados.

### Ejercicio 9.2 — Single File Components y `<script setup>`
Reescribe `TarjetaProducto.vue` (si no lo hiciste ya) usando `<script setup lang="ts">`, `defineProps` y `defineEmits` con tipado TypeScript.

### Ejercicio 9.3 — Async Components
Crea un componente pesado ficticio `PanelAvanzado.vue` y cárgalo en el padre usando `defineAsyncComponent(() => import('./PanelAvanzado.vue'))`. Agrega un botón "Mostrar panel avanzado" que solo renderice el componente asíncrono al hacer clic.

### Ejercicio 9.4 — `v-model` en componentes personalizados
Crea un componente `InputPersonalizado.vue` que envuelva un `<input>` y soporte `v-model` (usando `modelValue` y el evento `update:modelValue`, o `defineModel()`). Úsalo desde el padre como `<InputPersonalizado v-model="texto" />`.

---

## 10. Slots

### Ejercicio 10.1 — Slot por defecto y fallback
Crea un componente `Tarjeta.vue` con un slot por defecto que muestre "Sin contenido" si no se le pasa nada. Úsalo dos veces: una sin contenido y otra pasando un párrafo de texto.

### Ejercicio 10.2 — Named slots
Extiende `Tarjeta.vue` para tener slots nombrados `header`, `default` y `footer`. Úsalo desde el padre pasando contenido distinto a cada uno con `<template #header>`, etc.

### Ejercicio 10.3 — Scoped slots
Crea un componente `ListaGenerica.vue` que reciba un arreglo `items` por prop y, por cada item, exponga un scoped slot con el `item` y su `index`, dejando que el padre decida cómo renderizar cada fila (por ejemplo, mostrando el item en mayúsculas o con un ícono distinto según el padre).

---

## 11. Transitions

### Ejercicio 11.1 — `<Transition>` básico
Crea un botón "Mostrar/Ocultar" que alterne un `v-if` sobre un `<div>` con un mensaje, envuelto en `<Transition name="fade">`. Define en CSS las clases `fade-enter-active`, `fade-leave-active`, `fade-enter-from` y `fade-leave-to` para lograr un efecto de aparición/desaparición gradual (opacity).

### Ejercicio 11.2 — `<TransitionGroup>`
Crea una lista de tareas (`v-for`) donde se puedan agregar y eliminar elementos, envuelta en `<TransitionGroup name="lista" tag="ul">`. Define transiciones CSS para que al agregar/eliminar un elemento se anime su entrada/salida y el reacomodo de los demás.

---

## 12. Plugins

### Ejercicio 12.1 — Crear un plugin simple
Crea un plugin `miPlugin.ts` que agregue una propiedad global `$saludo` (por ejemplo, mediante `app.config.globalProperties.$saludo = 'Hola desde el plugin'`) o que registre un componente global. Instálalo en `main.ts` con `app.use(miPlugin)` y úsalo desde cualquier componente.

### Ejercicio 12.2 — Plugin con opciones
Modifica el plugin anterior para que reciba opciones al instalarlo, por ejemplo `app.use(miPlugin, { mensaje: 'Hola personalizado' })`, y utiliza ese mensaje en vez de uno fijo.

---

## 13. Custom Directives

### Ejercicio 13.1 — Directiva `v-focus`
Crea una directiva personalizada `v-focus` que enfoque automáticamente un input cuando el elemento se monta (`mounted(el) { el.focus() }`). Regístrala localmente en un componente y pruébala en un formulario.

### Ejercicio 13.2 — Directiva con valor y modificadores
Crea una directiva `v-resaltar` que reciba un valor (color) y lo aplique como `background-color` del elemento, por ejemplo `v-resaltar="'yellow'"`. Agrega soporte para un modificador `.texto` que, si está presente, cambie el color del texto en vez del fondo.

---

## 14. Vue Router

### Ejercicio 14.1 — Configuración básica de rutas
Instala `vue-router`, crea un archivo `router/index.ts` con al menos 3 rutas (`/`, `/acerca`, `/contacto`), cada una apuntando a un componente de página simple. Móntalo en `main.ts` con `app.use(router)` y coloca `<RouterView />` en `App.vue`.

### Ejercicio 14.2 — Navegación con `<RouterLink>`
Crea un menú de navegación en `App.vue` usando `<RouterLink to="...">` para cada una de las 3 rutas del ejercicio anterior. Agrega la clase `router-link-active` en el CSS para resaltar visualmente el enlace activo.

### Ejercicio 14.3 — Rutas con parámetros
Agrega una ruta dinámica `/usuario/:id` que muestre un componente `Usuario.vue` mostrando el `id` recibido (usando `useRoute()` o la prop `id` si habilitas `props: true` en la definición de la ruta). Agrega enlaces a `/usuario/1` y `/usuario/2` para probarla.

---

## 15. Ecosystem

### Ejercicio 15.1 — Investigación guiada
Responde en una lista, en una sola frase por herramienta, qué problema resuelve cada una dentro del ecosistema Vue:
- **VueUse**
- **Pinia**
- **Nuxt**
- **Vuetify**
- **Vue Devtools**
- **Volar**

### Ejercicio 15.2 — Aplicación práctica mínima
Elige **una** de las herramientas anteriores (recomendado: Pinia o VueUse) e impleméntala en un mini-ejemplo dentro de este proyecto:
- Con **Pinia**: crea un store simple (`useCounterStore`) con un estado `count` y una acción `increment`, y consúmelo desde un componente.
- Con **VueUse**: usa un composable como `useMouse()` o `useLocalStorage()` en un componente y muestra el resultado en pantalla.
