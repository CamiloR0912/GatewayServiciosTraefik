# Autores:
 - Julian Bayona
 - Camilo Ramirez

## 1. Topología y redes
 - docker-compose.yml con los servicios, sin exponer los puertos de neo4j.
 ![alt text](img/image.png)

 - Compilación docker-compose.
 ![alt text](img/image-1.png)

 - Cargando los registros de los csv a la base de datos.
 ![alt text](img/image-2.png) 

 - Comprobación de funcionamiento api-db.
 ![alt text](img/image-3.png) 

 - Comprobación base de datos no accesible desde el host 
 ![alt text](img/image-4.png) 


## 2. Rutas estructuradas
 - modificación del docker-compose.yml para exponer el dashboard y la api en rutas estructuradas
 ![alt text](img/image-5.png)
 - api desde la url *http://api.localhost/people*
 ![alt text](img/image-6.png)
 - Dasboard desde la url *http://ops.localhost/dashboard/dashboard/* 
 ![alt text](img/image-7.png)

## 3. Middlewares
 

 - Middlewares de la api
 ![alt text](img/image-9.png)

 - Comprobación del funcionamiento de los middlewares
 ![alt text](img/image-10.png)
- Middlewares del dashboard
 ![alt text](img/image-8.png)
 - el middleware está configurado para recibir 10 peticiones, por lo cual aparecen las primeras 11 peticiones con codigo 200 de OK, luego cuando se sobrepasan las 11 peticiones aparece el codigo 429 **Too Many Requests** 
 ![alt text](img/image-11.png)

 - Middleware de autenticación básica
 ![alt text](img/image-12.png)
  ![alt text](img/image-13.png)

## 4. balanceo
- En nuestro Docker-compose.yml lo que hacemos es crear otro servicio haciendo referencia al mismo router.
  
 ![alt text](img/4.1.png)

- En nueeestra API generamos un endpoint que nos retorne la instacioa de cada servicio.
  
![alt text](img/4.2.png)

- Bajamos nuestro contenedor y lo levantamos de nuevo.
  
![alt text](img/4.3.png)

- Hacemos petciones a nuestro endpoint y podemos visualizar como hay en nuestro llamado 2 tipos de peticiones.
  
![alt text](img/4.4.png)

- Ya estando es traefik podemos visualizar que el servicio de backend tiene dos servidores.
  
![alt text](img/4.5.png)

## 5. Descubrimiento automático

- Definimos nuestro servicio para que envie notificaciones de trafico a Traefik.cv.
  
 ![alt text](img/5.1.png)

- Nuestro servico traefik lo ajustamos paa que detecte esos cambios.
  
 ![alt text](img/5.2.png)

- Bajamos y levantamos nuestros servicios.
  
 ![alt text](img/5.3.png)

- Vemos que tenemos en backend solo un servicio.
  
 ![alt text](img/5.4.png)

- Levantamos nuestro contenedro nuevamente con 3 replicas y vemos estan en nuestros 3 servicios de backend.
  
 ![alt text](img/5.5.png)

 - Ya en nuestro dashboard tendriamos en nuestro balanceador de cargas los 3 servicos.
   
 ![alt text](img/5.6.png)
 
## 6. Observabilidad 

 - Hacemos la contruccion de nuestro endpoint /health que nos dara el estado de nuestro servicio.
   
 ![alt text](img/6.1.png)

 - Esta es la respuesta que nos retornaria nuestro health.
   
 ![alt text](img/6.2.png)

 - Probamos nuestro endpoint de listar personas.
   
 ![alt text](img/6.3.png)

 - Miramos en nuestro dashboard los servicios, routers y middlewares.
   
 ![alt text](img/6.4.png)
 ![alt text](img/6.5.png)
 ![alt text](img/6.6.png)



## Puntos extra, Middleware errores
 - Se crea el servicio para los errores.
 ![alt text](image.png)

 - Se agrega el middleware al backend.
 ![alt text](image-1.png)

 - Se agrega el middleware global a traefik.
 ![alt text](image-5.png)

 - Se le da permisos a la carpeta para poder escribir en ella, luego se crea el archivo 404.html para redirigir al error.
 ![alt text](image-2.png)

 - Se crean los archivos 400.html y 502.html para redirigir al error.
 ![alt text](image-4.png)

 - Se crean endpoints en la api para forzar los errores 400, 404 y 502.
 ![alt text](image-6.png)

- prueba de funcionamiento del middleware.
![alt text](image-3.png)
![alt text](image-8.png)
![alt text](image-7.png)
