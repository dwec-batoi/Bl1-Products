# Bl1-Products
## Práctica 1 - Clases
En primer lugar crearemos un nuevo proyecto Vite para realizar estas prácticas ya que tendremos muchos ficheros Javascript diferentes y en algunos casos también haremos tests.

A continuación las clases que usaremos en la aplicación. En este ejercicio vamos a trabajar con los productos de un almacén, para lo que crearemos las clases **Category**, **Product** y **Store**.

### Clase Category
La guardaremos en el fichero _category.class.js_. Tendrá las siguientes **propiedades**:
  - **id** (number)
  - **name**
  - **description**: opcional. Si no se pasa su descripción será 'No hay descripción'  
  
Esta clase no tiene ningún método.

### Clase Product
La guardaremos en el fichero _product.class.js_. Tendrá las siguientes **propiedades**:
  - **id** (number)
  - **name**
  - **categoryId**: el nº de su categoría
  - **price**
  - **units**: argumento opcional (si no le pasamos este parámetro al constructor su número por defecto será 0)
  
Esta clase tendrá los siguientes **métodos**:
  ```javascript
  productImport(): Number
  ```  
  - devuelve el importe total del producto (su precio multiplicado por el nº de unidades)

  ```javascript
  xxxx(): String
  ``` 
  - (¿qué nombre le deberías dar a este método?): si se intenta **imprimir** el producto se mostrará su descripción, sus unidades entre paréntesis, su precio y el importe total (los € siempre con 2 decimales) como en el siguiente ejemplo:
  ```html
        TV Samsung MP45: 10 uds. x 235,95 €/u = 2359,50 €
  ```

### Clase Store
Es el almacén de productos (podríamos tener más de uno) que guardaremos en _store.class.js_. Tendrá las **propiedades**:
  -  **id**: código numérico que nos pasan al crear el almacén
  - **name**: nombre del almacén (texto)
  -  **products**: array de productos. No se le pasa al constructor sino que al crear un almacén se inicializa a un array vacío
  - **categories**: array de categorías. No se le pasa, se inicializa vacío
  
La clase tendrá los **métodos**:
  ```javascript
  getCategoryById(id: Integer): Category
  ```   
  - recibe una id y devuelve su categoría. Si no existe lanzará una excepción 

  ```javascript
  getCategoryByName(name: String): Category
  ```  
  - recibe un nombre y devuelve su categoría. Si no existe lanzará una excepción. No tendrá en cuenta la capitalización

```javascript
getProductById(id: Integer): Product
```
  - recibe como parámetro una id de producto y devuelve el producto del almacén que tiene dicha id (si no existe  lanzará una excepción)

```javascript
getProductsByCategory(id: Integer): Product[]
```
  - recibe como parámetro una id de categoría y devuelve un array con los productos del almacén que tienen dicha categoría

  ```javascript
  addCategory(nombre: String [, descripcion: String]): Category
  ```
  - recibe el nombre de la categoría y, opcionalmente, una descripción y devuelve el objeto _Category_ creado. Crea un objeto de clase _Category_ y lo añade al almacén (a _categories_). Como a la clase _Category_ hay que pasarle una _id_ haremos una función que la calcule buscando la máxima _id_ de las categorías que hay en el almacén (debéis usar un _reduce_) y sumándole 1. Este método genera un error si
    - no se le pasa un nombre
    - ya existe una categoría con ese nombre


  ```javascript
  addProduct(payload: Object): Product
  ```
  - **addProduct**: recibe como **único** parámetro **un objeto** con los datos del producto a añadir (propiedades _name_, _category_, _price_ y, opcionalmente, _units_) y devuelve el objeto _Product_ creado. Este método crea un nuevo producto (llamará al constructor de la clase _Product_) y lo añade al almacén. Como a la clase _Product_ hay que pasarle una _id_ haremos una función que la calcule buscando la máxima _id_ de los productos que hay en el almacén (debéis usar un _reduce_) y sumándole 1. Este método genera un error si
    - no se le pasa _name_
    - no se le pasa _category_ o no existe esa categoría
    - no se le pasa _price_ o no es un número positivo
    - se le pasa _units_ pero no es un número entero positivo

  ```javascript
  delCategory(id: Integer): Category
  ```
  - recibe como parámetro la id de una categoría y, si no tiene productos, la elimina del almacén y devuelve la categoría eliminada. Genera un error si no existe la categoría o si tiene productos

  ```javascript
  delProduct(id: Integer): Product
  ```
  - recibe como parámetro la id de un producto y, si no tiene unidades, lo elimina del almacén y devuelve el producto eliminado. Genera un error si no existe el producto o si sus unidades no están a 0

  ```javascript
  totalImport(): Number
  ```    
  - devuelve el valor total de los productos del almacén (su precio por sus uds). Para ello usa el método _productImport_ de cada producto
  ```javascript
  orderByUnits(): Product[]
  ```    
  - devuelve el array de productos ordenado por unidades de forma descendente
  ```javascript
  orderByName(): Product[]
  ```    
  - devuelve el array de productos ordenado por el nombre del producto
  ```javascript
  underStock(units: Integer): Product[]
  ```    
  - recibe un nº de unidades y devuelve un array con los productos que tengan menos de dichas unidades
  ```javascript
  xxxx(): String
  ```  
  - (¿qué nombre le deberías dar a este método?): si se intenta imprimir el almacén devuelve una cadena con la id del almacén, el nº de productos y su importe total con 2 decimales, y debajo una lista con los datos de cada producto como en el siguiente ejemplo:
```html
Almacén 1 => 2 productos: 2174,75 €
- TV Samsung MP45: 10 uds. x 235,95 €/u = 2359,50 €
- USB Kingston 16 GB: 100 uds. x 19,95 €/u = 1995,00 €
```

Recuerda que siempre que llames a una función que pueda generar un error debes hacer dicha llamada dentro de una sentencia `try...catch`. Lo que hace _index.js_ si captura un error es mostrarlo por consola con el comando `console.error`.

