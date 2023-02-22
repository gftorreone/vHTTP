# vHTTP
Clase que permite realizar peticiones HTTP simples, cuya finalidad es simplificar el uso de XMLHTTPREQUEST
## Instalación
Se debe descargar el archivo vHTTP.js e importarlo en el apartado scripts del proyecto

Una vez importado, para usarlo en la clase deseada :
```js
#include "(CurrentProject)/vHTTPjs"
```
Una vez hecho ya podremos usarlo

```sh
#include "(CurrentProject)/vHTTPjs"
  vHTTP(
      {
                method: "GET",
                url: "https://jsonplaceholder.typicode.com/todos",
                data: null,
                responseType: 'json',
                onComplete: function (status, response) {
                    alert(JSON.stringify(response))
                },
                onFailed: function (status, response) {
                    alert(response);
                }
        }
    );
```
## Configuración
* Los parámetros que lleven una ? significa que son opcionales

| Parámetros | Descripción |
| ------ | ------ |
| method? | Tipo de petición HTTP que queremos procesar: POST,PUT,GET,DELETE,PATCH. Por defecto es GET|
| url | URL del recurso al que queremos hacer la petición |
| data | [plugins/googledrive/README.md][PlGd] |
| responseType | Este parámetro nos va a permitir definir el tipo de respuesta devuelto por nuestra petición. Soporta:  json,text,xml y arraybuffer  |
| onComplete | Esta función solo devolverá el contenido de la petición cuando el estado sea un 200 o un 201. Devuelve el Status y los Datos |
| onFailed | Esta es la función que se ejecutará en el caso de que la petición no se realice o esté errónea |

## Ejemplos


Obtener 200 usuarios de JSONPLACEHOLDER:

```sh
vHTTP({
            url: "https://jsonplaceholder.typicode.com/todos",
            data: null,
            responseType: 'json',
            onComplete: function (status, response) {
                alert("Código Respuesta: "+ status)
                alert("Usarios: " + JSON.stringify(response))
            },
            onFailed: function (status, response) {
                alert("Código de Respuesta: " + status);
            }
        });
```

Alta  de una publicación:

```sh
vHTTP(
  {
			method:"POST",
            url: "https://jsonplaceholder.typicode.com/posts",
            data:JSON.stringify(
			{
					title: 'Prueba con mi librería vHTTP',
					body: 'Esto es muy sencillo',
					userId: 1,
			}),
            responseType: 'json',
			headers:{
			 'Content-type': 'application/json; charset=UTF-8',
			},
            onComplete: function (status, response) {
                alert(JSON.stringify(response))
            },
            onFailed: function (status, response) {
                alert(response);
            }
    });
```
Y como resultado obtenemos:

```json
{
    "title":"Prueba con mi librería vHTTP",
    "body":"Esto es muy sencillo",
    "userId":1,
    "id":101
}
```



