# Autores:
 - Julian Bayona
 - Camilo Ramirez

## 1. Topología y redes
 - docker-compose.yml con los servicios, sin exponer los puertos de neo4j.
 ![alt text](image.png)

 - Compilación docker-compose.
 ![alt text](image-1.png)

 - Cargando los registros de los csv a la base de datos.
 ![alt text](image-2.png) 

 - Comprobación de funcionamiento api-db.
 ![alt text](image-3.png) 

 - Comprobación base de datos no accesible desde el host 
 ![alt text](image-4.png) 


## 2. Rutas estructuradas
 - modificación del docker-compose.yml para exponer el dashboard y la api en rutas estructuradas
 ![alt text](image-5.png)
 - api desde la url *http://api.localhost/people*
 ![alt text](image-6.png)
 - Dasboard desde la url *http://ops.localhost/dashboard/dashboard/* 
 ![alt text](image-7.png)