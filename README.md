## Esta aplicacion se compone de tres recusos
    -Frontend
    -Products
    -Shopping

 ### Si se requiere hacer una prueba con docker

Primero deberan tener las imagenes

    Pueden crear la imagenes con las aplicaciones del repositorio
    o bien descargalas
    Les dejo la info del repositorio de Docker Hub
    - docker pull tiztan21/ms-frontend:01
    - docker pull tiztan21/ms-products:01
    - docker pull tiztan21/ms-shopping-cart:01

Luego deben levantar las aplicacion

    - docker run -d -p 3002:3002 --name SHOPPING --network test1 ms-shopping-cart
    - docker run -d -p 3001:3001 --name PRODUCTS --network test1 ms-products 
    - docker run -d -p 3000:3000 -e PRODUCTS="PRODUCTS" -e SHOPPING="SHOPPING" --name frontend --network test1 ms-frontend

--- El Frontend requiere unas variables para su funcionamiento
        PRODUCTS
        SHOPPING
    Esta variables, segun el entorno que manejemos, deben asociarse a lo recursos correspondientes.
    En el ejemplo anterior como trabajamos con docker, el valor que toman estas variables son los nombres de los contenedores. Se recomienda desplegar los contenedores con nombre para asi poder asociarlos a las variables de caso contrario no funcionara la APP.
    Tambien es recomendable que los tres esten en la misma network. En el ejemplo se creo la network "test1"
        -  docker network create --driver bridge test1

### En caso de desplegar en Kubernetes

    Pueden utilizar los manifiesto de este repositorio.
    A tener en cuenta que las variables a utilizar en frontend en este caso debe ser igual al nombre del servicio del recurso correspondiente.




