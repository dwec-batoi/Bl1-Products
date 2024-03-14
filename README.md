# Bl1-Products
## Práctica 3 - DOM
La práctica consistirá en crear una página HTML para poder interactuar con el almacén creado anteriormente. Para dar un mejor aspecto a la página con poco trabajo utilizaremos **_bootstrap_**.

El HTML que renderizamos tendrá:
- una tabla con los productos del almacén. De cada uno mostraremos id, nombre, categoría (el nombre en vez de la id), uds, precio/u, importe y una celda de acciones con iconos para subir y bajar sus uds, editar y eliminar
- un formulario para añadir nuevos productos o editarlos con los campos necesarios y los botones de 'Añadir' y 'Reset'
- una tabla con las categorías del almacén. Mostraremos todos sus datos más 2 botones: editar y eliminar
- el formulario de añadir y editar categoría con los campos necesarios y los botones de 'Añadir' y 'Reset'

Para hacer nuestra aplicación seguiremos el patrón MVC. El modelo son las clases que ya tenemos hechas. Las meteremos dentro de una carpeta llamada _model_. 

La vista tendrá métodos que reciben del controlador unos datos (un producto a añadir o a eliminar, etc) y modifican la página para reflejar esos datos. 

El controlador tendrá 2 propiedades:
- **store**: almacenará una instancia de la clase 'Store' donde guardar los datos del modelo
- **view**: será una instancia de la clase 'View'

Tendrá métodos para cada una de las acciones que puede realizar el usuario: añadir productos, eliminar productos, eliminar categorías, ...

Lo que debe hacer cada método del controlador es:
- validar los datos recibidos (en muchos casos caso NO es necesario ya que los valida el modelo)
- si los datos son válidos
  - llamar al método correspondiente de la clase 'Store' para que se almacene el cambio realizado
  - si se realiza la operación correctamente
    - llamar al método de la vista que refleje el cambio en la página
  - si se produce algún error
    - mostrar el error
- si no son válidos
    - mostrar el error

El fichero principal y se encarga de instanciar e inicializar un controlador.

**Recuerda**: siempre que llames a una función que pueda generar un error debes capturar dicho error en algún sitio dentro de una sentencia `try...catch`. Ahora los errores deben llegar al controlador que dirá a la vista que los muestre como un nuevo mensaje en la página.

