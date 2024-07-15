<h1 align="center">HttpSession Servlet</h1>
<h2>Introducción</h2>
<p>HttpSession es otra opción para almacenar datos del usuario que sean persistentes en diferentes request y se almacena en el lado del servidor.</p>
<p align="center"><img width="719" alt="image" src="https://github.com/user-attachments/assets/287569a4-67f4-4d89-9e0d-8b1e9fe7d985"></p>

<h2>Manejo de estados</h2>

- Los datos no se comparten entre diferentes objetos de sesión (el cliente solo puede acceder a los datos desde su sesión)
- Las sesiones http nos permiten un forma para mantener información del usuario entre peticiones y poder recordarlas
- También contiene pares clave-valor, pero en comparación con una cookie, una sesión puede contener un objeto como valor.

<h2>Trabajar con Session en Servlet</h2>

- <b>Crear una sesión http</b>
  - Se crea de forma automática por cada cliente o navegador web y la accedemos mediante el objeto request:
```java
HttpSession session = request.getSession();
```
- <b>Obtener un objeto o valor de la sesión http</b>
```java
String username = session.getAttribute("username");
```
- <b>Guardar un objeto en la sesión http</b>
```java
session.setAttribute("username", usuario);
```
- <b>Eliminar un valor de la sesión del cliente</b>
```java
session.removeAttribute("username");
```
- <b>Eliminar o invalidar la sesión actual del cliente</b>
```java
session.invalidate();
```
<h2>Otros métodos importantes</h2>

- <b>isNew()</b>: verifica si la sesión fue creada recientemente. Es decir, devuelve `true` si el cliente aún no ha confirmado que se ha unido a la sesión
```java
HttpSession session = request.getSession();
boolean isNew = session.isNew();
```
- <b>getCreationTime()</b>: devuelve el tiempo de creación de la sesión en milisegundos desde la época (1 de enero de 1970, 00:00:00 GMT). Esto puede ser útil para saber cuándo se inició la sesión.
 ```java
HttpSession session = request.getSession();
long creationTime = session.getCreationTime();
```
- <b>getLastAccessedTime()</b>: devuelve el tiempo en milisegundos desde la época cuando la sesión fue accedida por última vez. Es decir, cuándo fue la última vez que se realizó alguna actividad en la sesión.
 ```java
HttpSession session = request.getSession();
long lastAccessedTime = session.getLastAccessedTime();
```  
- <b>getMaxlnactivelnterval()</b>: devuelve el intervalo máximo de inactividad en segundos, después del cual la sesión será invalidada por el contenedor. Si el tiempo de inactividad de la sesión supera este valor, la sesión será terminada automáticamente.
 ```java
HttpSession session = request.getSession();
int maxInactiveInterval = session.getMaxInactiveInterval();
```  
- <b>setMaxlnactivelnterval(int interval)</b>: establece el intervalo máximo de inactividad en segundos para la sesión. Es decir, el tiempo que una sesión puede permanecer inactiva antes de que el contenedor la invalide.
 ```java
HttpSession session = request.getSession();
session.setMaxInactiveInterval(1800); // Establece el intervalo a 30 minutos
```
