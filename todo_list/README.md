# Manejo de eventos en una aplicación ToDo con React

## Función `handleSubmit`

La función handleSubmit es utilizada para manejar la presentación de un formulario en una aplicación ToDo en React.

```javascript
function handleSubmit(e) {
    e.preventDefault();
    let todo = document.getElementById('todoAdd').value
    const newTodo = {
      id: new Date().getTime(),
      text: todo.trim(),
      completed: false,
    };
    if (newTodo.text.length > 0 ) {
        setTodos([...todos].concat(newTodo));
    } else {
        alert("Enter Valid Task");
    }
    document.getElementById('todoAdd').value = ""
}
```

#### Descripción
e.preventDefault() previene el comportamiento predeterminado del evento, evitando que la página se actualice cuando se envía el formulario.

Se obtiene el valor del elemento con el id 'todoAdd' del DOM y se crea un nuevo objeto newTodo que representa la tarea a agregar.

Se verifica si el texto de la nueva tarea tiene una longitud mayor que cero. Si es así, se agrega al estado todos. De lo contrario, se muestra una alerta.
Finalmente, se borra el contenido del campo de entrada del formulario.

## Eliminar una tarea existente

La eliminación de una tarea se maneja mediante la función deleteTodo, que filtra las tareas basándose en el id.

### Código para eliminar una tarea

```javascript
function deleteTodo(id) {
  let updatedTodos = [...todos].filter((todo) => todo.id !== id);
  setTodos(updatedTodos);
}
```

Este código crea un nuevo arreglo excluyendo la tarea con el id proporcionado y establece ese arreglo como el nuevo estado todos, eliminando efectivamente la tarea del estado y de la interfaz de usuario.

## Agregar un botón para eliminar una tarea
Se añade un botón junto a cada tarea en la lista que llama a la función deleteTodo pasando el id de la tarea al hacer clic.
```javascript
<button onClick={() => deleteTodo(todo.id)}>Delete</button>
```

### Conclusión 
El manejo de eventos en React es fundamental para desarrollar aplicaciones interactivas como una lista de tareas (ToDo). A través del ejemplo proporcionado, hemos visto cómo las funciones handleSubmit y deleteTodo permiten agregar y eliminar tareas, respectivamente, manipulando el estado de la aplicación de manera reactiva. Al seguir expandiendo estos conceptos, se pueden implementar características más avanzadas y personalizaciones, haciendo de React una herramienta poderosa para los desarrolladores.
