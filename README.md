# Bl1-Products
## Práctica 2 - Ajax
Vamos a dar persistencia a nuestra aplicación. Crearemos la carpeta `repositories` y dentro 2 clases:
- **`categoriesRepo.class.js`**: clase para gestionar los datos de la tabla _categories_. La haremos con promesas y no puedes usar `fetch`.Tendremos métodos para:
  -  `getAll()`: obtener todas las categorías
  -  `addItem(item)`: recibe una categoría y la añade a la BBDD
  -  `editItem(item)`: modifica una categoría
  -  `delItem(id)`: recibe una _id_ y borra de la BBDD esa categoría
- **`productsRepo.class.js`**: clase para gestionar los datos de la tabla _products_. Deberás utilizar `fetch` y promesas o `async/await`. Tendremos métodos para:
  -  `getAll()`: obtener todos los productos
  -  `getAllFromCategory(categoryId)`: obtener todos los productos de la categoría pasada
  -  `getById(id)`: obtener el producto con la _id_ pasada
  -  `addItem(item)`: añade un producto
  -  `editItem(item)`: modifica un producto
  -  `changeUnits(prodId, uds)`: establece las unidades del producto indicado
  -  `delItem(id)`: recibe una _id_ y borra de la BBDD ese producto

Nuestro _index.js_ deberá:
- crear un nuevo almacén, de nombre ACME
- cargar y guardar en él todas las categorías del fichero
- cargar y guardar todos los productos
- crea un nuevo producto en el almacén: Tóner HP Lasarjet 402, categoría 2, precio 23.95 €
- modifica sus unidades a 4
- imprime por consola la lista de productos con menos de 5 uds
- imprime por consola la lista alfabética de productos

Recuerda que siempre que hagas una llamada a la API puede generar un error, lo que debes tener en cuenta. 


