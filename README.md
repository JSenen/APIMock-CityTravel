# APIMock-CityTravel
***
![Json](https://img.shields.io/badge/{JSON}-grey?style=for-the-badge&logo=JSON&logoColor=blue)
![Postman](https://img.shields.io/badge/Postman-orange?style=for-the-badge&logo=postman&logoColor=white)
![Wiremock](https://img.shields.io/badge/wiremock-blue?style=for-the-badge&logo=wiremock&logoColor=blue)
***
API virtual diseñada para la simulación de la api CityTravel (https://github.com/JSenen/CityTravel)
Para el desarrollo del proyecto se ha usado **WireMock**

En el proyecto se pueden distinguir 2 carpetas principales:
1. **mappings** : Con las rutas y codigos de estado y los enlaces a los archivos que contienes los bodyrequest y los
                  response a las diversas peticiones.
    
    Ejemplo archivo mapping:
    ```
   {
    "mappings": [
    {
    "request": {
    "method": "GET",
    "url": "/lines"
    },
    "response": {
    "status": 200,
    "headers": {
    "Content-Type": "application/json"
    },
    "bodyFileName": "GET-Lines-OK.json"
    }
    },
    {
    "request": {
    "method": "GET",
    "url": "/lines500"
    },
    "response": {
    "status": 500,
    "headers": {
    "Content-Type": "application/json"
    },
    "bodyFileName": "GET-Lines-500-KO.json"
    }
    },
    {
    "request": {
    "method": "GET",
    "url": "/lines400"
    },
    "response": {
    "status": 400,
    "headers": {
    "Content-Type": "application/json"
    },
    "bodyFileName": "Generic-400-KO.json"
    }
    }
    ]
    }

2. **files**: Con las respuestas y codigos referenciados en el directorio anterior
    
    Ejemplo codigo __files de respuesta:

```
{
  "id": 11,
  "codeLine": "L-786",
  "color": "blue",
  "firstTime": "04:00",
  "lastTime": "21:30",
  "stopTime": 11,
  "trains": null,
  "stations": null
}
```

Se ha diseñado la API virtual para que pueda comprobarse 3 códigos de estado por cada operación o endpoint de la API original
Podemos encontrar los siguietes codigos de estado ha diferentes peticiones

- 200 OK: El servidor ha recibido la solicitud correctamente y ha devuelto la respuesta solicitada.
- 202 Accepted: El servidor ha recibido la solicitud pero todavía no ha completado el proceso de solicitud.
- 204 No Content: El servidor ha recibido la solicitud correctamente, pero no tiene nada que devolver en la respuesta.
- 400 Bad Request: El servidor no pudo procesar la solicitud debido a un error del cliente, como un parámetro de solicitud incorrecto.
- 401 Unauthorized: El servidor ha rechazado la solicitud porque el cliente no ha proporcionado la autenticación adecuada o no tiene permiso para acceder al recurso solicitado.
- 404 Not Found: El servidor no ha encontrado el recurso solicitado.
- 500 Internal Server Error: El servidor ha encontrado un error interno y no puede completar la solicitud.

***

Dentro del proyecto también se encuentra una carpeta __**POSTMAN**__ , en la que se encuentran los archivos necesarios 
de __ENTORNO__ y __COLECCION__ para importarlos y comprobarla API virtual.

***

**EJECUCION**: Para ejecutar la API virtual, solo debe ejecutar el siguiente comando en la consola o en su terminal, 
comprobando que se haya en la carpeta raiz del proyecto
```
java -jar wiremock-jre8-standalone-2.35.0.jar
```






