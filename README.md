# Event Listeners en JavaScript: Cómo Funcionan y su Uso Avanzado

En JavaScript, los event listeners permiten que nuestro código responda a interacciones del usuario o cambios en la página.

## 🔹 El método `addEventListener`

El método `addEventListener` se usa para escuchar eventos en un elemento del DOM. Su sintaxis es:

```js
    element.addEventListener(evento, callback, opciones);
```

### 🔹 Parámetros:

- **evento** (string): Nombre del evento (ej. "click", "input", "submit").
- **callback** (función): La función que se ejecutará cuando ocurra el evento.
- **opciones** (opcional): Un objeto con configuraciones adicionales como `once` (para ejecutar una sola vez) o `capture` (para cambiar el orden de propagación del evento).

## 🔹 El objeto `event`

Cuando un evento ocurre, el navegador genera un objeto de evento (`event object`), que se pasa automáticamente al callback.

Ejemplo de un evento de `click` y exploración del objeto `event`:

```js
document.querySelector("button").addEventListener("click", function(event) {
    console.log(event); // Muestra el objeto event en la consola
});
```

### 🔹 Propiedades comunes del objeto `event`:

- `event.target`: Elemento que disparó el evento.
- `event.type`: Tipo de evento (ej. "click", "keydown").
- `event.preventDefault()`: Previene la acción por defecto (ej. evitar el envío de un formulario).
- `event.clientX`, `event.clientY`: Coordenadas del mouse en la ventana.

## 🔹 Eventos Comunes y el Uso del `event` Object

### 👡 Evento `click` (Detectar en qué botón se hizo clic)

```js
document.querySelector("button").addEventListener("click", function(event) {
    console.log("Clic en el botón:", event.target.textContent);
});
```

### ⌨ Evento `input` (Mostrar lo que el usuario escribe en tiempo real)

```js
document.querySelector("#text-input").addEventListener("input", function(event) {
    console.log("Texto ingresado:", event.target.value);
});
```

### 📩 Evento `submit` (Evitar que el formulario recargue la página)

```js
document.querySelector("form").addEventListener("submit", function(event) {
    event.preventDefault(); // Evita el envío por defecto
    console.log("Formulario enviado");
});
```

## 🔹 ¿Qué es un Callback en un Evento?

Un **callback** es una función que se pasa como argumento a otra función y se ejecuta cuando ocurre el evento.

Ejemplo de un callback en un `addEventListener`:

```js
function mostrarMensaje() {
    console.log("Hiciste clic en el botón");
}

document.querySelector("button").addEventListener("click", mostrarMensaje);
```

🚀 Aquí `mostrarMensaje` es la función de callback que se ejecutará cuando el usuario haga clic en el botón.

## 🔹 Ejemplo Práctico Combinando Todo

Crearemos un formulario que, al escribir en el campo de texto, muestre el valor en tiempo real, y al enviarlo, muestre un mensaje sin recargar la página.

```html
<form id="miFormulario">
    <input type="text" id="nombre" placeholder="Escribe tu nombre">
    <button type="submit">Enviar</button>
</form>
<p id="resultado"></p>

<script>
    const input = document.querySelector("#nombre");
    const form = document.querySelector("#miFormulario");
    const resultado = document.querySelector("#resultado");

    // Evento input: Actualizar en tiempo real
    input.addEventListener("input", (event) => {
        resultado.textContent = "Hola, " + event.target.value;
    });

    // Evento submit: Evitar recarga y mostrar alerta
    form.addEventListener("submit", (event) => {
        event.preventDefault();
        alert("Formulario enviado con el nombre: " + input.value);
    });
</script>
```

## 🔹 ¿Qué aprendimos?

- `addEventListener` escucha eventos en los elementos.
- El `event object` nos da información útil del evento.
- **Callbacks** son funciones ejecutadas dentro de un evento.
- **Ejemplo práctico**: Actualizar un mensaje en tiempo real y evitar la recarga del formulario.

## 🚀 Conclusión

Los **event listeners** permiten una interacción dinámica en nuestras aplicaciones web. Aprovechar el **objeto event** y los **callbacks** nos ayuda a manejar eventos de manera más eficiente y flexible. 



