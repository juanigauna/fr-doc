# Friendly Router (Actualización Julio 2021).
He estado trabajando muchísimo para traer nuevas caracteristicas a mi proyecto. Vayamos a ver algunas cosas nuevas.

Por parte de las rutas he mejorado los módulos **Request** y **Response**.

Y también le he dado un buen refactor a la clase Router por lo que vamos a poder encontrar cosas más coherentes a la hora de usarlo.
```php
$router->get('/', function(Request $req, Response $res) {
    return 'Hello :)';
});
```
### Ahora paso a explicar algunas funciones del módulo **Request**.

*Aclaro que algunas funciones se usan en el proyecto que estes desarrollando y otras simplemente son para el uso entre los módulos del sistema, pero yo igual los pongo para que sepan cómo funciona todo y puedan seguir mejorando el proyecto.*

## getUri() : string
```php
$req->getUri();
```
Nos devuelve la uri solicitada en la solicitud entrante.

## clearUri() : string
```php
$req->clearUri($uri);
```
Se encarga de limpiar de caracteres extraños en nuestra url, por ejemplo, tenemos una url que ingresa así al sistema:

> /text/name%20of%20my%20cat

Usando la función clearUri esa cadena de texto quedaría algo así:

> /text/name-of-my-cat

El objetivo principal es tener unas url limpias y amigables para el usuario, algo entendible a simple vista en la url.

## getMethod() : string
```php
$req->getMethod();
```
Este método nos devuelve el verbo http de la solicitud entrante, tales pueden ser: GET, POST, PUT, DELETE. Entre otros.

## setUrlParams(array $params)
```php
$req->setUrlParams($params);
```
Se usa para establecer los parámetros obtenidos de una url.

## param(string $param) : mixed
```php
$req->param('id');
```
Nos devuelve el parámetro de nuestra url que pidamos y en caso de no existir ninguno, nos lanzará un error.

## server(string $param) : mixed
```php
$req->server('REQUEST_URI');
```
Nos va a devolver información tal como cabeceras, rutas y ubicaciones de scripts. De no existir lo que estamos requiriendo, nos lanzará un error.

## files(string $param) : mixed
```php
$req->files('photo');
```
En caso de una petición contenga archivos, podremos tratarlos con este método. De no existir lo que estamos requiriendo, nos lanzará un error.
