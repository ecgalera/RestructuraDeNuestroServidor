# RestructuraDeNuestroServidor

Restructuramos nuestro servidor: 
1- Creamos dentro de la carpeta Service:
        - cart.service.js
        - product.service.js 
        - index.js 

//-------------------------------------------------------------------------------

2- Dentro de la carpeta index.js podemos elegir la persistencia a utilizar: 
       
// Persistencia : mongodb --------------------------------------
import ProductsManager from "../dao/mongodb/manager/productsManagers.js";
// Persistencia : fileSystem ----------------------------------
//import ProductsManager from "../dao/fs/manager/ProductManager.js";

import ProductsService from "./product.service.js";

// Persistencia : mongodb --------------------------------------
import CartsManager from "../dao/mongodb/manager/cartManager.js";
// Persistencia : fileSystem ----------------------------------
//import CartsManager from "../dao/fs/manager/CartManager.js";

import CartsService from "./cart.service.js";

export const productService = new ProductsService(new ProductsManager());

export const cartService = new CartsService(new CartsManager());

Para poder intercambiar persistencias elijo que import queda operativo

//-------------------------------------------------------------------------------

3- Para poder provar las persistencias con MONGODB utilizo los siguientes empoint:
    Para CART: 
      - GET localhost:3000/api/cart => obtengo los carritos 
      - POST localhost:3000/api/cart => creo un carrito
     Para PRODUCT: 
       - GET localhost:3000/api/product => obtengo los productos
       - POST localhost:3000/api/product => creo un producto
         para crear el producto utilizo: 
           {
            
            "title": "Pan Negro con Cereales",
            "description": "pan con grasa",
            "price": 35,
            "category": "Panaderia",
            "code": "6r0905dd",
            "status": true,
            "stock": 67
            
        }
       -GET localhost:3000/api/product/:pid => para obtener un porducto 

  //-------------------------------------------------------------------------------

  4- Para poder probar las persistencias con FS: 

      - GET localhost:3000/api/products => Obtengo los productos
      - POST localhost:3000/api/products => creo un producto 
        para crear un producto utilizo: 
        
      {
            
            "title": "Pan Negro con Cereales",
            "description": "pan con grasa",
            "price": 35,
            "category": "Panaderia",
            "code": "0905dd",
            "status": true,
            "stock": 67
            
        }

       - PUT localhost:3000/api/products/:pid => modifico un producto 
         tambien utilizo: 
        {
            
            "title": "Producto Modificado",
            "description": "pan con grasa",
            "price": 35,
            "category": "Panaderia",
            "code": "090o5dd",
            "status": true,
            "stock": 67
            
        }

        //-------------------------------------------------------------------------------

        5- Se genero también el controller para el paginate en:
          controller 
              viewsController
                    viewsController.js 


        //-------------------------------------------------------------------------------

        6- Se crearon las variables de entorno .env y config.js, para hacer más fácil la corrección no agregue el .env en .gitignore


            
