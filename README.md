# HTTP (Protocolo de Transferencia de Hipertexto)
## Basico

### Introducción
``` sh
```
#### La WEB
Internet (o la WEB) es un masivo distribuidor de sistema de información cliente/servicio  como se muestra en el siguiente diagrama.

![](https://github.com/FranciscoRam/Protocolo-HTTP/blob/master/imagenes/01.png?raw=true)


Muchas aplicaciones se están ejecutando al mismo tiempo a través de Internet, tales como la navegación web/surfing, e-mail, transferencia de archivos, streaming de audio y video, y así sucesivamente. Para que una comunicación adecuada tenga lugar entre el cliente y el servidor, estas aplicaciones deben estar de acuerdo con un protocolo específico de nivel de aplicación como HTTP, FTP, SMTP, POP, etc.

#### Protocolo de Transferencia de Hipertexto (HTTP)
HTTP (Protocolo de Transferencia de Hipertexto) es quizás el protocolo de aplicación más popular en Internet (o en la web).
* HTTP es un protocolo cliente-servidor de petición-respuesta asimétrica como se ilustra. Un cliente HTTP envía un mensaje de petición a un servidor HTTP. El servidor, a su vez, devuelve un mensaje de respuesta. En otras palabras, HTTP es un protocolo de extracción, el cliente extrae la información desde el servidor (en lugar del servidor empujar información hasta el cliente).
![](https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP.png)
* HTTP es un protocolo sin estado. En otras palabras, la solicitud actual no sabe lo que se ha hecho en las anteriores solicitudes.
* HTTP permite la negociación de tipo de datos y representación, a fin de permitir que los sistemas se construyan de forma independiente de los datos que se transfieren.
* Citando el RFC2616: "El Protocolo de transferencia de hipertexto (HTTP) es un protocolo de nivel de aplicación para distribucion, colaboración, sistemas de información hipermedia. Es un genérico sin estado, el protocolo que se puede utilizar para muchas tareas más allá de su uso para el hipertexto, por ejemplo. como servidores de nombres y sistemas de gestión de objetos distribuidos, a través de la extensión de sus métodos de petición, códigos de error y los encabezados".
 #### Navegador
Cada vez que se emite una dirección URL de su navegador para obtener un recurso web a través de HTTP, por ejemplo, http://www.nowhere123.com/index.html, el navegador vuelve la dirección URL en un mensaje de solicitud y la envía al servidor HTTP. El servidor HTTP interpreta el mensaje de petición, y le devuelve un mensaje de respuesta apropiada, que puede ser el recurso que ha solicitado o un mensaje de error. Este proceso se ilustra a continuación:

![](https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_Steps.png)

#### Localizador Uniforme de Recursos (URL)
Un URL (Uniform Resource Locator) se utiliza para identificar de forma exclusiva un recurso a través de Internet. URL tiene la siguiente sintaxis:
``` sh
protocol://hostname:port/path-and-file-name
```
Hay 4 partes en una dirección URL :
* Protocolo : El protocolo de nivel de aplicación utilizada por el cliente y el servidor, por ejemplo, HTTP, FTP y telnet.
* Hostname: El nombre de dominio DNS (por ejemplo, www.nowhere123.com) o la dirección IP (por ejemplo, 192.128.1.2) del servidor.
* Puerto: el número de puerto TCP en el que el servidor está a la escucha de peticiones entrantes de los clientes.
* Path-y-file-name : El nombre y la ubicación del recurso solicitado, bajo el directorio base de documentos del servidor.
Por ejemplo, en la http://www.nowhere123.com/docs/index.html URL, el protocolo de comunicación es HTTP; el nombre de host es www.nowhere123.com. El número de puerto no se ha especificado en la URL, y adquiere el número predeterminado, que es el puerto TCP 80 para HTTP. La ruta y el nombre del archivo para el recurso que se encuentra es "/docs/index.html".
Otros ejemplos de URL son:
``` sh
ftp://www.ftp.org/docs/test.txt
mailto:user@test101.com
news:soc.culture.Singapore
telnet://www.nowhere123.com/
```

#### Protocolo HTTP
Como se ha mencionado, cada vez que se introduce una URL en el cuadro de dirección del navegador, el navegador traduce la dirección URL en un mensaje de solicitud de acuerdo con el protocolo especificado; y envía el mensaje de petición al servidor.

Por ejemplo , el navegador traduce la URL http://www.nowhere123.com/doc/index.html en el siguiente mensaje de solicitud:

``` sh
GET /docs/index.html HTTP/1.1
Host: www.nowhere123.com
Accept: image/gif, image/jpeg, */*
Accept-Language: en-us
Accept-Encoding: gzip, deflate
User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)
(blank line)
```

Cuando este mensaje de solicitud llega al servidor, el servidor puede tomar cualquiera de estas acciones:
* El servidor interpreta la petición recibida, los mapas de la solicitud en un archivo en el directorio de documentos del servidor, y devuelve el archivo solicitado al cliente.
* El servidor interpreta la petición recibida, los mapas de la solicitud en un programa guardado en el servidor, ejecuta el programa, y devuelve la salida del programa al cliente.
* La solicitud no puede ser satisfecha, el servidor devuelve un mensaje de error.
Un ejemplo del mensaje de respuesta HTTP es como se muestra:
``` sh
HTTP/1.1 200 OK
Date: Sun, 18 Oct 2009 08:56:53 GMT
Server: Apache/2.2.14 (Win32)
Last-Modified: Sat, 20 Nov 2004 07:16:26 GMT
ETag: "10000000565a5-2c-3e94b66c2e680"
Accept-Ranges: bytes
Content-Length: 44
Connection: close
Content-Type: text/html
X-Pad: avoid browser bug
  
<html><body><h1>It works!</h1></body></html>
```
El navegador recibe el mensaje de respuesta, interpreta el mensaje y muestra el contenido del mensaje en la ventana del navegador de acuerdo con el tipo de medio de la respuesta (como en la cabecera de respuesta Content-Type). Tipo de medios comunes incluyen "text/plain", "text/html", "image/gif", "image/jpeg", "audio/mpeg", "video/mpeg", "aplicación/pdf" y "application/pdf".
En su estado de reposo, un servidor HTTP no hace más que escuchar a la dirección (es) IP y el puerto (s) especificado en la configuración de solicitud entrante. Cuando llega una petición, el servidor analiza el encabezado del mensaje, aplica las reglas especificadas en la configuración, y toma la acción apropiada. control principal del webmaster sobre la acción del servidor web es a través de la configuración, el cual será tratado en mayor detalle en las secciones posteriores.
#### HTTP a través de TCP / IP
HTTP es un protocolo de nivel de aplicación cliente-servidor. Por lo general se ejecuta sobre una conexión TCP/IP, como se ilustra. (HTTP necesariamente no se ejecuta en TCP/IP. Sólo se presupone un transporte fiable. Cualquier protocolo de transporte que ofrecen tales garantías pueden ser utilizados.)

![](https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_OverTCPIP.png)

TCP/IP (Protocolo de Control de Transmición/Protocolo de Internet) es un conjunto de protocolos de transporte y capas de red para que máquinas se comuniquen entre sí a través de la red. IP (Protocolo de internet) es un protocolo de capa de red, se ocupa de direccionamiento de red y enrutamiento. En una red IP, cada máquina se asigna una dirección IP única (por ejemplo, 165.1.2.3), y el software de IP es responsable de encaminar un mensaje desde la fuente de IP a la dirección IP de destino. En IPv4 (versión 4 de IP ), la dirección IP se compone de 4 bytes, cada uno de los rangos de 0 a 255, separados por puntos, que se llama una forma de cuatro puntos. Este esquema de numeración soporta hasta 4G electrónico de la red. La última IPv6 (IP versión 6) soporta más direcciones. Como memorizar el número es difícil para la mayoría de las personas, un nombre de dominio-Inglés como www.nowhere123.com se utiliza en su lugar. El DNS (Servicio de nombre de dominio) traduce el nombre de dominio a la dirección IP (a través de tablas de búsqueda distribuidas). Una dirección IP 127.0.0.1 especial siempre se refiere a su propia máquina. Su nombre de dominio es "localhost" y puede ser utilizado para la prueba de bucle local.

TCP (Protocolo de control de transmisión) es un protocolo de capa de transporte, responsable de establecer una conexión entre dos máquinas. TCP consta de 2 protocolos: TCP y UDP (Datagrama de paquete de usuarios). TCP es fiable, cada paquete tiene un número de secuencia, y se espera un acuse de recibo. Un paquete será retransmitido si no es recibido por el receptor. la entrega de paquetes está garantizado en TCP. UDP no garantiza la entrega de paquetes, y por lo tanto no es fiable. Sin embargo, UDP tiene menos sobrecarga de la red y se puede utilizar para aplicaciones tales como vídeo y audio streaming, donde la fiabilidad no es crítica.

TCP multiplexa aplicaciones dentro de una máquina IP. Para cada máquina de IP, TCP soportes (multiplexa) de hasta 65.536 puertos (o enchufes), desde el puerto número 0 hasta 65535. Una aplicación, tal como HTTP o FTP, se ejecuta (o escucha ) en un número determinado de puerto para las solicitudes entrantes. Puerto 0 a 1023 son pre-asignados a los protocolos populares, por ejemplo, HTTP a 80, a los 21 FTP, Telnet a 23, SMTP a 25 , NNTP en el 119, y el DNS a los 53. El puerto 1024 y superiores están disponibles para los usuarios

A pesar de que el puerto TCP 80 es pre-asignado a HTTP, como el número de puerto HTTP predeterminado, esto no significa que prohíbe la ejecución de un servidor HTTP en otro número de puerto asignado por el usuario (1024-65535), tales como 8000 ,8080, especialmente como servidor de prueba. También se puede ejecutar varios servidores HTTP en la misma máquina en diferentes números de puerto. Cuando un cliente envía una URL sin indicar explícitamente el número de puerto http://www.nowhere123.com/docs/index.html, el navegador se conectará con el número de puerto por defecto 80 de la acogida www.nowhere123.com. Es necesario especificar el número del puerto en la URL, por ejemplo, http://www.nowhere123.com:8000/docs/index.html si el servidor está escuchando en el puerto 8000 y no el puerto por defecto 80. En resumen, para comunicarse a través de TCP/IP, lo que necesita saber (a) la dirección IP o el nombre de host, (b) numbero de puerto.
#### Especificaciones HTTP
La especificación HTTP se mantiene por el W3C (Consorcio Mundial Web) y disponible en http://www.w3.org/standards/techs/http. Actualmente hay dos versiones de HTTP, es decir, HTTP/1.0 y HTTP/1.1. La versión original, HTTP/0.9 (1991), escrito por Tim Berners-Lee, es un protocolo simple de transferencia de datos en bruto a través de Internet. HTTP/1.0 (1996) (definido en RFC 1945), ha mejorado el protocolo permitiendo mensajes MMIME-like. HTTP/1.0 no se ocupa de los problemas de servidores proxy, almacenamiento en caché de conexión persistente, hosts virtuales, y el rango de descarga. Estas características se proporcionan en HTTP/1.1 (1999) (definido en RFC 2616).
#### Servidor Apache HTTP o Servidor Apache Tomcat
Se necesita un servidor HTTP (como el Servidor Apache HTTP o Apache Tomcat) para estudiar el protocolo HTTP.

El servidor HTTP Apache es un servidor de producción industrial-fuerza popular, producida por Apache Software Foundation (ASF) @www.apache.org. ASF es una base de software de código abierto. Es decir, el servidor Apache HTTP es libre, con el código fuente.

El primer servidor HTTP fue escrito por Tim Berners-Lee en el CERN (Centro Europeo de Investigación Nuclear) en Ginebra, Suiza, que también inventó HTML. Apache fue construido en NCSA (National Center for Supercomputing Applications, EE.UU.) "httpd 1.3" servidor, a principios de 1995. Apache probablemente recibe su nombre del hecho de que consiste en un código original (desde un servidor web httpd anterior NCSA) además de algunos parches; o del nombre de una tribu india americana. Leer "[Apache How-to](https://www.ntu.edu.sg/home/ehchua/programming/howto/Apache_HowToInstall.html)" sobre cómo instalar y configuar un servidor Apache HTTP; o "[Tomcat How-to](https://www.ntu.edu.sg/home/ehchua/programming/howto/Tomcat_HowTo.html)" para instalar y empezar a trabajar con Apache Tomcat.

#### Mensajes de solicitud y respuesta HTTP
Un cliente HTTP y el servidor se comunican mediante el envío de mensajes de texto. El cliente envía un mensaje de petición al servidor. El servidor, a su vez, devuelve un mensaje de respuesta.
Un mensaje HTTP consta de una cabecera de mensaje y un cuerpo de mensaje opcional, separados por una línea en blanco, como se ilustra a continuación:

![](https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_MessageFormat.png)

#### Petición de mensaje HTTP
El formato de un mensaje de petición HTTP es como sigue:
![](https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_RequestMessage.png)

**Linea de Estado**
La primera línea de la cabecera se llama la línea de solicitud , seguido de las cabeceras de solicitud opcionales.
La línea de solicitud tiene la siguiente sintaxis: 
``` sh
request-method-name request-URI HTTP-version
```
* solicitud-nombre-método: protocolo HTTP define un conjunto de métodos de petición, por ejemplo, GET, POST, HEAD, y OPCIONES. El cliente puede utilizar uno de estos métodos para enviar una petición al servidor.
* solicitud-URI: especifica el recurso solicitado.
* HTTP-version: Dos versiones están actualmente en uso: HTTP/1.0 y HTTP/1.1.

Ejemplos de línea de solicitud son:
``` sh
GET /test.html HTTP/1.1
HEAD /query.html HTTP/1.0
POST /index.html HTTP/1.1
```
**Cabeceras de petición**
Los encabezados de solicitud están en la forma del nombre: pares de valores. Los valores múltiples, separados por comas, se pueden especificar.
``` sh
request-header-name: request-header-value1, request-header-value2, ...
```
Los ejemplos de los encabezados de solicitud son:
``` sh
Host: www.xyz.com
Connection: Keep-Alive
Accept: image/gif, image/jpeg, */*
Accept-Language: us-en, fr, cn
```
**Ejemplo**
A continuación se muestra un mensaje de petición HTTP de ejemplo:
![](https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_RequestMessageExample.png)

#### Mensaje de respuesta HTTP
El formato del mensaje de respuesta HTTP es como sigue:
![](https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_ResponseMessage.png)
**Linea de status**
La primera línea se llama la línea de estado, seguido de la cabecera de respuesta opcional(s).
La línea de estado tiene la siguiente sintaxis:
``` sh
HTTP-version status-code reason-phrase
```
* HTTP versión: La versión de HTTP utilizada en esta sesión. HTTP/1.0 y HTTP/1.1.
* código de estado: un número de 3 dígitos generado por el servidor para reflejar el resultado de la solicitud.
* razón Frase: da una breve explicación para el código de estado.
* código de estado común y la razón frase son "200 OK", "404 Not Found", "403 Prohibido", "500 Internal Server Error".
Los ejemplos de línea de estado son:
``` sh
HTTP/1.1 200 OK
HTTP/1.0 404 Not Found
HTTP/1.1 403 Forbidden
```
** Encabezados de respuesta**
Las cabeceras de respuesta están en la forma nombre: pares de valores:
``` sh
response-header-name: response-header-value1, response-header-value2, ...
```
Ejemplos:
``` sh
Content-Type: text/html
Content-Length: 35
Connection: Keep-Alive
Keep-Alive: timeout=15, max=100
```
El cuerpo del mensaje de respuesta contiene los datos de los recursos solicitados.
**Ejemplo**

A continuación se muestra un mensaje de respuesta:
![](https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_ResponseMessageExample.png)

#### Métodos de Petición HTTP

El protocolo HTTP define un conjunto de métodos de petición. Un cliente puede utilizar uno de estos métodos de petición para enviar un mensaje de petición a un servidor HTTP. Los métodos son:
* GET: Un cliente puede utilizar la solicitud GET para obtener un recurso web desde el servidor.
* HEAD: Un cliente puede utilizar la petición HEAD para obtener el encabezado que una petición GET habría obtenido. Desde el encabezado se contiene la fecha de última modificación de los datos, esto se puede utilizar para comprobarla contra la copia caché local.
* POST: Se utiliza para enviar los datos al servidor web.
* PUT: Pregunta al servidor para almacenar los datos.
* DELETE: Pregunta al servidor para eliminar los datos.
* TRACE: Pregunta al servidor para devolver un rastreo de diagnóstico de las medidas que adopta. 
* OPTIONS: Pregunta al servidor para devolver la lista de métodos de petición que apoya.
* CONNECT: Se utiliza para decirle a un proxy que establezca una conexión con otro host y sólo debe responder el contenido, sin intentar analizar o almacenar en caché. Esto a menudo se utiliza para hacer la conexión SSL a través del proxy.
* Otros métodos de extensión.

#### Metodo de petición "GET"

GET es el método más común de solicitud HTTP. Un cliente puede utilizar el método GET para solicitar (o "get") para una pieza de recursos desde un servidor HTTP. Un mensaje de petición GET toma la siguiente sintaxis:

``` sh
GET request-URI HTTP-version
(Encabezados de solicitud opcional)
(linea en blanco)
(Cuerpo de la petición opcional)
```
* La palabra clave GET es sensible y debe estar en mayúsculas.
* request-URL: especifica la ruta del recurso solicitado, la cual debe empezar desde la raíz "/" del directorio de la base de documentos.
* HTTP-version: HTTP / 1.0 o HTTP / 1.1. Este cliente negocia el protocolo a utilizar para la sesión actual. Por ejemplo, el cliente puede solicitar el uso de HTTP / 1.1. Si el servidor no soporta el protocolo HTTP / 1.1, puede informar al cliente en la respuesta a utilizar HTTP / 1.0.
* El cliente utiliza los encabezados de solicitud opcionales (tales como Accept, Accept-Language, y etc) para negociar con el servidor y pedir al servidor entregar los contenidos preferidos (por ejemplo, en el idioma que el cliente prefiere).
* El Mensaje de solicitud GET tiene un cuerpo de solicitud opcional que contiene la cadena de consulta (que se explica más adelante)

#### Probando las peticiones HTTP

Hay muchas maneras de poner a prueba las peticiones HTTP. Su puede utilizar un programa de utilidad como "telnet" o "Hyperterm", o escribir nuestro propio programa de red para enviar mensaje de solicitud de prima a un servidor HTTP para poner a prueba las diversas peticiones HTTP.

**TELNEL**

"Telnet" es una herramienta de red muy utlizada, Tu puedes usar telnet para establecer una conexión TCP con un servidor, y emitir solicitudes HTTP primas. Por ejemplo, suponga que quiere iniciar un servidor HTTP en el localhost (ip address 127.0.0.1) en el puerto 8000:
``` sh
>telnet
telnet> help
... telnet help menu ...
telnet> open 127.0.0.1 8000
Connecting To 127.0.0.1...
GET /index.html HTTP/1.0
(Hit enter twice to send the terminating blank line ...)
... HTTP response message ..
```
Telnet es un protocolo basado en caracteres. Cada caracter que se introduce en el cliente telnet se enviará inmediatamente al servidor. Por lo tanto, no se puede cometer un error tipográfico en un comando, borrar o un espacio en blanco se enviaran al servidor. Puede que tenga que activar la opción de "eco local" para ver los caracteres que ingresa. Consulte el manual de telnet (ayuda de búsqueda de Windows ') para obtener más información sobre el uso de telnet.

**Programa de Red**

Tambien se puede escribir nuestro propio programa de red para emitir solicitudes primas HTTP a un servidor HTTP. Nuestro programa de red debera establecer primero una conexion TCP/IP con el servidor, Una vez que la conexión TCP ha sido establecida, tu puedes emitir solicitudes primas.

Un ejemplo de un programa de RED escrito en java se muestra abajo (asumiendo que el servidor HTTP corre en el localhost (dirección IP 127.0.0.1) en el puerto 8000):
``` sh
import java.net.*;
import java.io.*;

public class HttpClient {
   public static void main(String[] args) throws IOException {
      // The host and port to be connected.
      String host = "127.0.0.1";
      int port = 8000;
      // Create a TCP socket and connect to the host:port.
      Socket socket = new Socket(host, port);
      // Create the input and output streams for the network socket.
      BufferedReader in
         = new BufferedReader(
              new InputStreamReader(socket.getInputStream()));
      PrintWriter out
         = new PrintWriter(socket.getOutputStream(), true);
      // Send request to the HTTP server.
      out.println("GET /index.html HTTP/1.0");
      out.println();   // blank line separating header & body
      out.flush();
      // Read the response and display on console.
      String line;
      // readLine() returns null if server close the network socket.
      while((line = in.readLine()) != null) {
         System.out.println(line);
      }
      // Close the I/O streams.
      in.close();
      out.close();
   }
}
```

#### Solicitud GET HTTP/1.0

A continuación se muestra la respuesta de una solicitud GET HTTP/1.0 (Emitida via telnet por medio de nuestro propio programa de red - asumiedo que hemos iniciado nuestro servidor HTTP):
``` sh
 GET /index.html HTTP/1.0
(enter twice to create a blank line) 
```
``` sh
HTTP/1.1 200 OK
Date: Sun, 18 Oct 2009 08:56:53 GMT
Server: Apache/2.2.14 (Win32)
Last-Modified: Sat, 20 Nov 2004 07:16:26 GMT
ETag: "10000000565a5-2c-3e94b66c2e680"
Accept-Ranges: bytes
Content-Length: 44
Connection: close
Content-Type: text/html
X-Pad: avoid browser bug

<html><body><h1>It works!</h1></body></html>

Connection to host lost.
```

En este ejemplo el cliente emite una solicitud HTTP par preguntar por un documento llamado "/index.html"; y negocia el uso del protocolo HTTP/1.0. Una linea en blanco es necesaria después del encabezado se petición. Este mensaje de solicitud no contiene cuerpo alguno.

El servidor recibe el mensaje de solicitud, interpreta y mapea la request-URL a un documento dentro del directorio de documentos. Si el documento solicitado esta disponible, el servidor regresa el documento con un estado de respuesta "200 OK". Los encabezados de respuesta proveen la descripción necesaria del documento devuelto, tal como la ultima fecha de modificación (last-modified) el tipo MIME (TYPE-CONTENT) y el largo del documento. El cuerpo de la respuesta contiene el documento solicitado. El navegador formatea y muestra el documento de acuerdo con su a su tipo (por ejemplo, texto plano, HTML, JPEG, GIF, etc) y otra información obtenida de las cabeceras de respuesta.

Notas:

* El método de petición llamado "GET" es sensible y debe estar en mayúsculas
* Si el método de petición llamado fue escrito incorrectamente, el servidor regresará un mensaje de error "405 Method Not Implemented".
* Si el método de petición no esta permitido, el servidor regresará un mensaje de error "405 Method Not Allowed". Ejemplo DELETE es un metodo valido , pero puede no ser permitido (o implementado) por el servidor.
* Si la request-URL no existe, el servidor regresara un mensaje de error "404 Not Found" Tu deberás emitir una request-URL apropiada, iniciando desde la raiz del documento "/". De otra manera el servidor regresará un mensaje de error "400 Bad request"
* Si la versión HTTP no se encuentra o es incorrecta, el servidor regresará un mensaje de error "400 Bad Request".
* En HTTP/1.0, por defecto, los servidores cierran las conexiones TCP después de que la respuesta sea liberada. Si usted usa telnet para conectarse al servidor, el mensaje "Connection to host lost" aparecerá inmediatamente después de que el cuerpo de la respuesta sea recibido. Usted podrá un encabezado de petición opcional "Connection : Keep-Alive" para solicitar una conexión continua (keep-alive), entonces otra petición puede ser enviada a través de la misma conexión TCP para lograr una mejor eficiencia de la red. Por otro lado HTTP/1.0 utiliza keep-alive como conexión predeterminada.

#### Código de respuesta de estado

La primera linea del mensaje de respuesta (i.e la linea de estado) contiene el código de respuesta de estado. la cual es generada por el servidor para indicar el resultado de la petición.
El código de estado tiene número de 3 digitos:
* 1xx (informativo) Petición recibida, el servidor continúa el proceso.
* 2xx (Éxito): La petición fue recibida con éxito, entendido, aceptado y mantenido.
* 3xx (redirección): hay medidas que deben ser tomadas con el fin de completar la solicitud.
* 4xx (Error de cliente): La solicitud contiene sintaxis incorrecta o no se puede entender.
* 5xx (Error del servidor): El servidor no pudo cumplir con una solicitud aparentemente válida.

Algunos códigos de estado se encuentran comúnmente son:
* 100 Continue: El servidor ha recibido la solicitud y está en el proceso de dar la respuesta.
* 200 OK: La solicitud se ha cumplido.
* 301 Move Permanently: el recurso solicitado se ha movido permanentemente a una nueva ubicación. La URL de la nueva ubicación se da en la cabecera de respuesta denominada Location. El cliente debe emitir una nueva petición a la nueva ubicación. La aplicación debe actualizar todas las referencias a esta nueva ubicación.
* 302 Found & Redirect (or Move Temporaly): Igual que el 301, pero la nueva ubicación está temporalmente indefinida. El cliente debe emitir una nueva solicitud, pero las aplicaciones no es necesario actualizar las referencias.
* 304 Not Modified: En respuesta a la instrucción If-Modified-Since petición GET condicional, el servidor notifica que el recurso solicitado no se ha modificado.
* 400 Bad Request: el servidor no podía interpretar o comprender la solicitud, probablemente error de sintaxis en el mensaje de petición.
* 401 Authentication Required: El recurso solicitado está protegido, y requieren credenciales de cliente (usuario / contraseña). El cliente debe volver a presentar la solicitud con su credencial (usuario / contraseña).
* 403 Forbidden: El servidor se niega a suministrar el recurso, independientemente de la identidad del cliente.
* 404 Not Found: El recurso solicitado no se encuentra en el servidor.
* 405 Method Not Allowed: El método de solicitud utilizado, por ejemplo, POST, PUT, DELETE, es un método válido. Sin embargo, el servidor no permite que el método para el recurso solicitado.
* 408 Request Timeout:
* 414 Request URI too Large:
* 500 Internal Server Error: El servidor se confunde, a menudo causada por un error en el programa de servidor de responder a la solicitud.
* 501 Method NoT Implemented: El método de solicitud utilizado no es válido (podría ser causada por un error de escritura, por ejemplo, "GET" escribir mal como "Get").
* 502 Bad Gateway: proxy o puerta de enlace indica que se recibe una mala respuesta del servidor en sentido ascendente.
* 503 Service Unavailable: El servidor no puede respuesta debido a una sobrecarga o mantenimiento. El cliente puede volver a intentarlo más tarde.
* 504 Gateway Timeout : proxy o puerta de enlace indica que se recibe un tiempo de espera de un servidor ascendente.

#### Mas Métodos de solicitud GET HTTP/1.0

**Ejemplo: Método de solicitud misspelt**

En la petición, "GET" in está mal escrito como "GET". El servidor devuelve un error "501 Metodo no implementado". El encabezado de respuesta "Allow" le dice al cliente los métodos permitidos.
``` sh
get /test.html HTTP/1.0
(enter twice to create a blank line)
```
``` sh
HTTP/1.1 501 Method Not Implemented
Date: Sun, 18 Oct 2009 10:32:05 GMT
Server: Apache/2.2.14 (Win32)
Allow: GET,HEAD,POST,OPTIONS,TRACE
Content-Length: 215
Connection: close
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>501 Method Not Implemented</title>
</head><body>
<h1>Method Not Implemented</h1>
<p>get to /index.html not supported.<br />
</p>
</body></html>
```
**Ejemplo: 404 Archivo no Encontrado**

En esta solicitud GET, la solicitud de URL "/t.html" no se puede encontrar en el directorio de documentos del servidor. El servidor devuelve un error "404 Not Found".
``` sh
GET /t.html HTTP/1.0
(enter twice to create a blank line)
```
``` sh
HTTP/1.1 404 Not Found
Date: Sun, 18 Oct 2009 10:36:20 GMT
Server: Apache/2.2.14 (Win32)
Content-Length: 204
Connection: close
Content-Type: text/html; charset=iso-8859-1
   
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>404 Not Found</title>
</head><body>
<h1>Not Found</h1>
<p>The requested URL /t.html was not found on this server.</p>
</body></html>
```
**Ejemplo: Número Erroneo de versión HTTP**

En esta solicitud "GET", la versión HTTP fue mal escrita, resultando una mala sintaxis, el servidor regresa un error "404 Bad Request". La versión HTTP debe ser HTTP/1.0 or HTTP/1.1
``` sh
GET /index.html HTTTTTP/1.0
(enter twice to create a blank line)
```
``` sh
HTTP/1.1 400 Bad Request
Date: Sun, 08 Feb 2004 01:29:40 GMT
Server: Apache/1.3.29 (Win32)
Connection: close
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<HTML><HEAD>
<TITLE>400 Bad Request</TITLE>
</HEAD><BODY>
<H1>Bad Request</H1>
Your browser sent a request that this server could not understand.<P>
The request line contained invalid characters following the protocol string.<P><P>
</BODY></HTML>
NOTA: la última versión de pache 2.2.14 ignora este error y regresa el documento con el codigo de estado "200 OK"
```
**Ejemplo: Incorrecto Request-URI**

En la solicitud GET siguiente, el URI de solicitud no comenzó de la raíz "/", y dio lugar a una "solicitud incorrecta".
``` sh
GET test.html HTTP/1.0
(blank line)
```
``` sh
HTTP/1.1 400 Bad Request
Date: Sun, 18 Oct 2009 10:42:27 GMT
Server: Apache/2.2.14 (Win32)
Content-Length: 226
Connection: close
Content-Type: text/html; charset=iso-8859-1
   
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>400 Bad Request</title>
</head><body>
<h1>Bad Request</h1>
<p>Your browser sent a request that this server could not understand.<br />
</p>
</body></html>
```
**Ejemplo: conexión Keep-Alive**

Por defecto, por petición HTTP / 1.0 GET, el servidor cierra la conexión TCP una ve quez la respuesta se entrega. Se podría solicitar que se mantenga la conexión TCP, (a fin de enviar otra solicitud a través de la misma conexión TCP, para mejorar la eficiencia de la red), a través de un encabezado de solicitud opcional "Conexión: Keep-Alive". El servidor incluye una "conexión: Keep-Alive" en la cabecera de respuesta para informar al cliente de que puede enviar otra solicitud a través de esta conexión, antes de que el tiempo de espera de mantenimiento de conexión. Otra cabecera de respuesta "Keep-Alive: timeout = x, x max =" indica al cliente el tiempo de espera (en segundos) y el número máximo de solicitudes que se pueden enviar a través de esta conexión persistente.
``` sh
GET /test.html HTTP/1.0
Connection: Keep-Alive
(blank line)
```
``` sh
HTTP/1.1 200 OK
Date: Sun, 18 Oct 2009 10:47:06 GMT
Server: Apache/2.2.14 (Win32)
Last-Modified: Sat, 20 Nov 2004 07:16:26 GMT
ETag: "10000000565a5-2c-3e94b66c2e680"
Accept-Ranges: bytes
Content-Length: 44
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html

<html><body><h1>It works!</h1></body></html>
```

NOTAS:
* El mensaje "Conection to host lost" (para telnet) aparece después de "keep-alive" tiempo de espera.
* Antes de que el mensaje "Conection to host lost" aparece (Keep-alive timeout), puede enviar una nueva solicitud a través de la misma conexión TCP.
* El encabezado "Conexión: keep-alive" no distingue entre mayúsculas y minúsculas. El espacio es opcional.
* Si una cabecera opcional está mal escrito o no válido, se omite en el servidor.

**Ejemplo: Cómo acceder a un recurso protegido**

La siguiente petición GET ha intentado acceder a un recurso protegido. El servidor devuelve un error "403 Prohibido". En este ejemplo, los "htdocs \ prohibidos" el directorio está configurado para denegar el acceso completo con el archivo de configuración del servidor HTTP Apache "httpd.conf" de la siguiente manera:
``` sh
<Directory "C:/apache/htdocs/forbidden">
   Order deny,allow
   deny from all
</Directory>
```
``` sh
GET /forbidden/index.html HTTP/1.0
(blank line)
```
``` sh
HTTP/1.1 403 Forbidden
Date: Sun, 18 Oct 2009 11:58:41 GMT
Server: Apache/2.2.14 (Win32)
Content-Length: 222
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>403 Forbidden</title>
</head><body>
<h1>Forbidden</h1>
<p>You don't have permission to access /forbidden/index.html
on this server.</p>
</body></html>
```

#### HTTP/1.1 GET Request

El Servidor HTTP / 1.1 es compatible con las llamadas máquinas virtuales. Es decir, el mismo servidor físico podría albergar varios hosts virtuales, con diferentes nombres de host (por ejemplo, www.nowhere123.com y www.test909.com) y sus propios directorios raíz de documentos dedicados. Por lo tanto, en una petición HTTP / 1.1 GET, es obligatorio incluir un encabezado de solicitud llamado "host", para seleccionar uno de los hosts virtuales.

**Ejemplo: Solicitud HTTP/1.1**

HTTP / 1.1 mantiene persistente (o keep-alive) de conexión por defecto para mejorar la eficiencia de la red. Puede utilizar una "Connection: Close" encabezado de solicitud para pedir el servidor para cerrar la conexión TCP una vez que se entrega la respuesta.
``` sh
GET /index.html HTTP/1.1
Host: 127.0.0.1
(blank line)
```
``` sh
HTTP/1.1 200 OK
Date: Sun, 18 Oct 2009 12:10:12 GMT
Server: Apache/2.2.14 (Win32)
Last-Modified: Sat, 20 Nov 2004 07:16:26 GMT
ETag: "10000000565a5-2c-3e94b66c2e680"
Accept-Ranges: bytes
Content-Length: 44
Content-Type: text/html

<html><body><h1>It works!</h1></body></html>
```

**Ejemplo: HTTP / 1.1 falta el encabezado de host**

El siguiente ejemplo muestra que "host" de cabecera es obligatoria en una petición HTTP / 1.1 . Si "Host" de cabecera no se encuentra, el servidor devuelve un error "400 Bad Request".
``` sh
GET /index.html HTTP/1.1
(blank line)
```
``` sh
HTTP/1.1 400 Bad Request
Date: Sun, 18 Oct 2009 12:13:46 GMT
Server: Apache/2.2.14 (Win32)
Content-Length: 226
Connection: close
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>400 Bad Request</title>
</head><body>
<h1>Bad Request</h1>
<p>Su navegador envío una petición que este servidor no puede entender.<br />
</p>
</body></html>
```
#### Solicitudes Condicionales GET

En todos los ejemplos anteriores, el servidor devuelve todo el documento si la petición puede ser satisfecha (es decir incondicional). Es posible utilizar encabezado de la solicitud adicional para emitir una "solicitud condicional". Por ejemplo, para que solicite el documento basado en la fecha de última modificación (a fin de decidir si utilizar la copia caché local), o para pedir una parte del documento (o rango) en lugar de todo el documento (útil para la descarga de documentos de gran tamaño).

Los encabezados de solicitud condicional incluyen:
* If-Modified-Since (comprobación de código de estado de respuesta "304 Not Modified").
* Si-No Modificados-Desde
* If-Match
* If-None-Match
* Si-Rango

#### Encabezados de Solicitud

En esta sección se describen algunas de las cabeceras de petición de uso común. Consulte la especificación HTTP para más detalles. La sintaxis del nombre de la cabecera es decir con inicial-cap se unen utilizando guión (-), por ejemplo, Content-Length, If-Modified-Since.

**host**: ***Domain Name*** - HTTP / 1.1 soporta máquinas virtuales. múltiples nombres DNS (por ejemplo, www.nowhere123.com y www.nowhere456.com) pueden residir en el mismo servidor físico, con sus propios directorios raíz de documentos. Los encabezados de host es obligatorio en HTTP / 1.1 para seleccionar uno de los anfitriones.

Los siguientes encabezados pueden ser utilizados para la negociación de contenido por el cliente para pedir al servidor entregar el tipo preferido del documento (en términos del tipo de medio, por ejemplo, JPEG vs GIF, o el lenguaje usado por ejemplo Inglés vs francés) si el servidor mantiene múltiples versiones de un mismo documento.

**Accept**: ***mime-type-1, el mimo type-2, ...***- El cliente puede utilizar el encabezado Accept para indicar al servidor los tipos MIME que puede manejar y cual prefiere. Si el servidor tiene varias versiones del documento solicitado (por ejemplo, una imagen en formato GIF y PNG, o un documento en formato TXT y PDF), se puede comprobar esta cabecera para decidir qué versión entregará al cliente. (Por ejemplo, PNG es más avanzado más GIF, pero no todas navegador soporta PNG.) Este proceso se denomina negociación de tipo de contenido.

**Accept-Language:** ***lenguaje-1, el lenguaje-2, ...-*** El cliente puede utilizar la cabecera Accept-Language para indicar al servidor qué idiomas se puede manejar o que prefiere. Si el servidor tiene varias versiones del documento solicitado (por ejemplo, en Inglés, chino, francés), se puede comprobar esta cabecera para decidir cuál es la versión para volver. Este proceso se llama negociación de idioma.

**Accept-Charset:** ***Juego de caracteres-1, juego de caracteres-2, ... -*** Para la negociación del juego de caracteres, el cliente puede utilizar esta cabecera para indicar al servidor qué juegos de caracteres puede manejar o que prefiere. Ejemplos de conjuntos de caracteres ISO-8859-1, ISO-8859-2, ISO-8859-5, Big5, UCS2, UCS4, UTF8.

**Accept-Encoding:** ***Codificación-método-1, que codifica-método-2, ... -*** El cliente puede utilizar esta cabecera para indicar al servidor el tipo de codificación que soporta. Si el servidor se ha codificado (o comprimido) o la versión del documento solicitado, puede devolver una versión codificada soportada por el cliente. El servidor también puede elegir codificar el documento antes de volver al cliente para reducir el tiempo de transmisión. El servidor debe establecer la cabecera de respuesta "Content-Encoding" para informar al cliente de que se codifica el documento devuelto. Los métodos de codificación son comunes "x-gzip (.gz, .tgz)" y "x-compress (.Z)".

**Conexión:** ***Cerrar | Keep-Alive-*** El cliente puede utilizar esta cabecera para indicar al servidor la posibilidad de cerrar la conexión después de esta solicitud, o para mantener la conexión activa durante otra solicitud. HTTP / 1.1 usa conexión persistente (keep-alive) de forma predeterminada. HTTP / 1.0 cierra la conexión por defecto.

**Árbitro:** ***árbitro-URL -*** El cliente puede utilizar esta cabecera para indicar el referente de esta solicitud. Si hace clic en un enlace desde la página web 1 a visitar desde la página web 2, la página web 1 es la de referencia para la solicitud de la página web 2. Todos los navegadores más importantes establecen esta cabecera, que puede ser utilizada para hacer un seguimiento cuando la solicitud proviene de (publicidad en la web o la personalización del contenido). No obstante, esta cabecera no es fiable y se puede suplantar fácilmente. Tenga en cuenta que Referente está mal escrito como "Referer" (por desgracia, usted tiene que hacerlo también).

**User-Agent:** ***Tipo-Navegador -*** Identificar el tipo de navegador que se utiliza para realizar la solicitud. El Servidor puede utilizar esta información para volver documentos diferentes dependiendo del tipo de navegador.

**Content-Length:** ***número-de-bytes -*** Usado por solicitud POST, para informar al servidor de la longitud del cuerpo de la petición.

**Content-Type:** ***mime-type -*** Utilizado por solicitud POST, para informar al servidor el tipo del medio del cuerpo de la petición.

**Cache-Control:** ***no-cache | ... -*** El cliente puede utilizar esta cabecera para especificar cómo las páginas se van a almacenar en caché por el servidor proxy. "No-cache" requiere un proxy para obtener una nueva copia del servidor original, a pesar de que una copia en caché local está disponible. (HTTP / 1.0 el servidor no reconoce "Cache-Control: no-cache". En su lugar, se utiliza "Pragma: no-cache" incluida tanto en las cabeceras de petición aun si no está seguro acerca de la versión del servidor.).

**Authorization:** Usado por el cliente para suministrar su credencial (usuario / contraseña) para acceder a recursos protegidos. (Esta cabecera se describirá en el capítulo después de la autenticación.)

**Cookie:** ***cookie-name-1=cookie-value-1, cookie-name-2=cookie-value-2,, ... -*** El cliente utiliza esta cabecera para devolver la cookie (s) devuelta al servidor, que se estableció por este servidor antes de la administración del estado. (Esta cabecera se discutirá en el capítulo más adelante la administración del estado.)

**If-Modified-Since:** ***date -*** Dile al servidor que envie la página sólo si ha sido modificado después de la fecha específica.

#### Solicitud GET al directorio

Supongamos que un directorio llamado "testdir" está presente en los "htdocs" deL directorio de documentos.

Si un cliente emite una solicitud GET a "/ testdir /" (es decir, en el directorio).
1.  El servidor devolverá "/testdir/index.html" si el directorio contiene un archivo "index.html".
2.  De lo contrario, el servidor devuelve el listado de directorios, si el listado de directorios está habilitada en la configuración del servidor.
3.  De lo contrario, el servidor devuelve "404 página no encontrada".

Es interesante tener en cuenta que si un cliente emite una solicitud GET a "/ testdir" (sin especificar la ruta del directorio "/"), el servidor devuelve un "301 trasladarse permanentemente" con una nueva "ubicación" de "/ testdir / ", como sigue
``` sh
GET /testdir HTTP/1.1
Host: 127.0.0.1
(blank line)
```
``` sh
HTTP/1.1 301 Moved Permanently
Date: Sun, 18 Oct 2009 13:19:15 GMT
Server: Apache/2.2.14 (Win32)
Location: http://127.0.0.1:8000/testdir/
Content-Length: 238
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="http://127.0.0.1:8000/testdir/">here</a>.</p>

</body></html>
```

La mayor parte del navegador seguirá con otra petición de "/ testdir /". Por ejemplo, si emite http://127.0.0.1:8000/testdir sin el arrastre "/" de un navegador, se puede notar que una "/" se añadió a la dirección después de que se le dio la respuesta. La moraleja de la historia es: usted debe incluir la solicitud "/" para el directorio para ahorrarle una solicitud GET adicional.

#### Emitir una solicitud GET a través de un servidor proxy

Para enviar una petición GET a través de un servidor proxy, (a) establecer una conexión TCP con el servidor proxy; (B) utilizar una ruta absoluta URL de solicitud http: // nombre de host: puerto / ruta / nombre de archivo en el servidor de destino.

El siguiente seguimiento fue capturado por medio de telnet. Se establece una conexión con el servidor proxy, y se emitió una petición GET.URL absoluta de solicitud quese utiliza en la línea de petición.

``` sh
GET http://www.amazon.com/index.html HTTP/1.1
Host: www.amazon.com
Connection: Close
(blank line)
```
``` sh
HTTP/1.1 302 Found
Transfer-Encoding: chunked
Date: Fri, 27 Feb 2004 09:27:35 GMT
Content-Type: text/html; charset=iso-8859-1
Connection: close
Server: Stronghold/2.4.2 Apache/1.3.6 C2NetEU/2412 (Unix)
Set-Cookie: skin=; domain=.amazon.com; path=/; expires=Wed, 01-Aug-01 12:00:00 GMT
Connection: close
Location: http://www.amazon.com:80/exec/obidos/subst/home/home.html
Via: 1.1 xproxy (NetCache NetApp/5.3.1R4D5)

ed
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<HTML><HEAD>
<TITLE>302 Found</TITLE>
</HEAD><BODY>
<H1>Found</H1>
The document has moved
<A HREF="http://www.amazon.com:80/exec/obidos/subst/home/home.html">
here</A>.<P>
</BODY></HTML>

0
```
Tome en cuenta que la respuesta se devuelve en "trozos".

#### Método de petición "HEAD"

La petición HEAD es similar a la petición GET. Sin embargo, el servidor devuelve sólo el encabezado de respuesta sin el cuerpo de la respuesta, que contiene el documento actual. La petición HEAD es útil para comprobar las cabeceras, como Last-Modified, Content-Type, Content-Length, antes de enviar una solicitud GET adecuada para recuperar el documento.

La sintaxis de la petición HEAD es la siguiente:

Ejemplo
``` sh
HEAD /index.html HTTP/1.0
(blank line)
```
``` sh
HTTP/1.1 200 OK
Date: Sun, 18 Oct 2009 14:09:16 GMT
Server: Apache/2.2.14 (Win32)
Last-Modified: Sat, 20 Nov 2004 07:16:26 GMT
ETag: "10000000565a5-2c-3e94b66c2e680"
Accept-Ranges: bytes
Content-Length: 44
Connection: close
Content-Type: text/html
X-Pad: avoid browser bug
```
Note que la respuesta actual consiste en el encabezado solo sin el cuerpo, el cual contiene el documento actual

#### "OPTIONS" MÉTODO DE PETICÍON

Un cliente puede utilizar un método de petición OPTIONS para consultar el servidor el que se apoyan los métodos de petición. La sintaxis de mensaje de solicitud de OPCIONES es:
``` sh
OPTIONS request-URL|* HTTP-version
(other optional headers)
(blank line)
```
"*" Se puede utilizar en lugar de un REQUEST-URL para indicar que la solicitud no se aplica a cualquier recurso en particular

**Ejemplo**

Por ejemplo la siguiente petición OPTIONS es enviada a través de un servidor proxy:
``` sh
OPTIONS http://www.amazon.com/ HTTP/1.1
Host: www.amazon.com
Connection: Close
(blank line)
``` 
``` sh
HTTP/1.1 200 OK
Date: Fri, 27 Feb 2004 09:42:46 GMT
Content-Length: 0
Connection: close
Server: Stronghold/2.4.2 Apache/1.3.6 C2NetEU/2412 (Unix)
Allow: GET, HEAD, POST, OPTIONS, TRACE
Connection: close
Via: 1.1 xproxy (NetCache NetApp/5.3.1R4D5)
(blank line)
```
Todos los servidores que permiten solicitudes GET permitiran solicitudes HEAD. Algunas vecess, HEAD no esta listada.

#### Métodos de Petición "TRACE"

Un cliente puede enviar una solicitud de rastreo para pedir al servidor para devolver un rastreo de diagnóstico.

La solicitud de rastreo toma la siguiente sintaxis
``` sh
TRACE / HTTP-version
(blank line)
```
**Ejemplo**

El siguiente ejemplo muestra una petición TRACE emitida a través de un servidor proxy.
``` sh
TRACE http://www.amazon.com/ HTTP/1.1
Host: www.amazon.com
Connection: Close
(blank line)
```
``` sh
HTTP/1.1 200 OK
Transfer-Encoding: chunked
Date: Fri, 27 Feb 2004 09:44:21 GMT
Content-Type: message/http
Connection: close
Server: Stronghold/2.4.2 Apache/1.3.6 C2NetEU/2412 (Unix)
Connection: close
Via: 1.1 xproxy (NetCache NetApp/5.3.1R4D5)

9d
TRACE / HTTP/1.1
Connection: keep-alive
Host: www.amazon.com
Via: 1.1 xproxy (NetCache NetApp/5.3.1R4D5)
X-Forwarded-For: 155.69.185.59, 155.69.5.234

0
```
(Para comparar la petición TRACE con una ruta de indicio)

#### Presentando formularios de datos HTML y cadenas de consulta

En muchas aplicaciones de Internet, tales como e-commerce y motores de búsqueda, se requieren los clientes para presentar información adicional al servidor (por ejemplo, el nombre, la dirección, las palabras clave de búsqueda). En base de los datos presentados, el servidor toma una acción apropiada y produce una respuesta personalizada.

Los clientes suelen presentarse con una forma (producido utilizando la etiqueta HTML <form>). Una vez que se llenan los datos solicitados y pulsa el botón de enviar, el navegador empaca los datos del formulario y las presenta al servidor, usando una petición GET o una solicitud POST.
La siguiente es una muestra en forma HTML, que se produce por la siguiente secuencia de comandos HTML:
``` sh
<html>
<head><title>A Sample HTML Form</title></head>
<body>
  <h2 align="left">A Sample HTML Data Entry Form</h2>
  <form method="get" action="/bin/process">
    Enter your name: <input type="text" name="username"><br />
    Enter your password: <input type="password" name="password"><br />
    Which year?
    <input type="radio" name="year" value="2" />Yr 1
    <input type="radio" name="year" value="2" />Yr 2
    <input type="radio" name="year" value="3" />Yr 3<br />
    Subject registered:
    <input type="checkbox" name="subject" value="e101" />E101
    <input type="checkbox" name="subject" value="e102" />E102
    <input type="checkbox" name="subject" value="e103" />E103<br />
    Select Day:
    <select name="day">
      <option value="mon">Monday</option>
      <option value="wed">Wednesday</option>
      <option value="fri">Friday</option>
    </select><br />
    <textarea rows="3" cols="30">Enter your special request here</textarea><br />
    <input type="submit" value="SEND" />
    <input type="reset" value="CLEAR" />
    <input type="hidden" name="action" value="registration" />
  </form>
</body>
</html>
```
![](https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTML_SampleForm.png)

Una forma contiene campos. Los tipos de campos incluyen:
* Text Box: producido por <input type="text">.
* Password Box: producido por <input type="password">.
* Radio Button: producido por <input type="radio">.
* Checkbox: producido por <input type="checkbox">.
* Selection: producido por <select> and <option>.
* Text Area: producido por <textarea>.
* Submit Button: producido por <input type="submit">.
* Reset Button: producido por <input type="reset">.
* Hidden Field: producido por <input type="hidden">.
* Button: producido por <input type="button">.

Cada campo tiene un nombre y puede tomar un valor especifico. Una vez que el cliente rellena los campos y pulsa el botón de enviar, el navegador recoge cada nombre y valor de los campos, los empaca en pares tipo "nombre = valor", y concatena todos los campos utilizando "&" como separador de campo. Esto se conoce como una cadena de consulta. La cadena de consulta se enviará al servidor como parte de la solicitud.
``` sh
name1=value1&name2=value2&name3=value3&... 
```
Los caracteres especiales no están permitidos dentro de la cadena de consulta. Ellos deben ser reemplazados por un "%" seguido del código ASCII en hexadecimal. Por ejemplo, "~" se sustituye por "%7E", "#" por "%23" y así sucesivamente. Un espacio en blanco es bastante común, puede ser sustituido por uno o "%20" "+" (el carácter "+" debe sustituirse por "%2B"). Este proceso de sustitución se llama codificación URL, y el resultado es una cadena de consulta con codificación URL. Por ejemplo, supongamos que hay 3 campos dentro de un formulario, con el nombre de "name = Peter Lee", "address = #123 Ave feliz" y "language = C++", la cadena de consulta con codificación URL es:
``` sh
name=Peter+Lee&address=%23123+Happy+Ave&Language=C%2B%2B
```
La cadena de consulta se puede enviar al servidor por medio del método de solicitud HTTP GET o POST, que se especifica en la etiqueta <form>'s atributo "método".
``` sh
<form method="get|post" action="url">
```
Si el método de solicitud GET es usado, la codificación URL de la cadena de consulta aparecerá detras de la request-URL despues de un caracter "?"
``` sh
GET request-URI?query-string HTTP-version
(other optional request headers)
(blank line)
(optional request body)
```
Usar la solicitud GET para enviar cadenas de consulta tiene los siguientes inconvenientes:
* La cantidad de datos que se puede agregar detrás de petición-URI es limitado. Si esta cantidad excede un umbral específico del servidor, el servidor devolverá un error "414 URI de la solicitud demasiado grande".
* La cadena de consulta con codificación URL aparecería en el cuadro de dirección del navegador.

El método POST elimina estos inconvenientes. Si se utiliza el método de solicitud POST, la cadena de consulta se enviará en el cuerpo del mensaje de solicitud, donde la cantidad no está limitada. Las cabezeras de la solicitud Content-Type y Content-Length se utilizan para notificar al servidor el tipo y la longitud de la cadena de consulta. La cadena de consulta no aparecerá en el cuadro de dirección del navegador. El método POST se discutirá más adelante.

**Ejemplo**

La siguiente forma HTML es usada para reunir el usuario y contraseña de un menu login.
``` sh
<html>
<head><title>Login</title></head>
<body>
  <h2>LOGIN</h2>
  <form method="get" action="/bin/login">
    Username: <input type="text" name="user" size="25" /><br />
    Password: <input type="password" name="pw" size="10" /><br /><br />
    <input type="hidden" name="action" value="login" />
    <input type="submit" value="SEND" />
  </form>
</body>
</html>
``` 
![](https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTML_LoginForm.png)

El método de la petición HTTP GET se utiliza para enviar la cadena de consulta. Supongamos que el usuario introduce "Peter Lee" como nombre de usuario, "123456" como contraseña; y pulse el botón Enviar. La siguiente petición GET es:
``` sh
GET /bin/login?user=Peter+Lee&pw=123456&action=login HTTP/1.1
Accept: image/gif, image/jpeg, */*
Referer: http://127.0.0.1:8000/login.html
Accept-Language: en-us
Accept-Encoding: gzip, deflate
User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)
Host: 127.0.0.1:8000
Connection: Keep-Alive
``` 

Tenga en cuenta que aunque la contraseña que introduzca no se muestra en la pantalla, se muestra claramente en el cuadro de dirección del navegador. Nunca se debe enviar la contraseña sin cifrado adecuado.
``` sh
http://127.0.0.1:8000/bin/login?user=Peter+Lee&pw=123456&action=login
```

### URL and URI

**URL (Localizador de Recursos Uniformes)**

Una URL que se define en el RFC 2396, se utiliza para identificar de forma exclusiva un recurso a través de Internet. Una URL tiene la siguiente sintaxis:
``` sh
protocol://hostname:port/path-and-file-name
```
Hay 4 partes en una dirección URL:
* Protocol: El protocolo de capa de aplicación utilizado por el cliente y el servidor, por ejemplo, HTTP, FTP y telnet.
* hostname: El nombre de dominio DNS (por ejemplo, www.nowhere123.com) o la dirección IP (por ejemplo, 192.128.1.2) del servidor.
* Puerto: el número de puerto TCP que el servidor está a la escucha de peticiones entrantes de los clientes.
* Path-and-file-name: El nombre y la ubicación del recurso solicitado, bajo el directorio base de documentos del servidor.

Por ejemplo, en la http://www.nowhere123.com/docs/index.html URL, el protocolo de comunicación es HTTP; el nombre de host es www.nowhere123.com. El número de puerto no se ha especificado en la URL, y adquiere el número predeterminado, que es el puerto TCP 80 para HTTP [STD 2]. La ruta y el nombre del archivo para el recurso que se encuentra es "/docs/index.html". bajo el directorio base de documentos del servidor.

Otros ejemplos de URL son:
``` sh
ftp://www.ftp.org/docs/test.txt
mailto:user@test101.com
news:soc.culture.Singapore
telnet://www.nowhere123.com/
```

**Codificación de URL**

URL no puede contener caracteres especiales, como blanco o '~'. Los caracteres especiales se codifican, en forma de% xx, donde xx es el código ASCII hexadecimal. Por ejemplo, '~' se codifica como% 7e; '+' Se codifica como% 2b. Un espacio en blanco puede ser codificado como% 20 o '+'. La dirección URL después de la codificación se llama URL codificada.

**URI (Identificador Uniforme de Recursos)**

URI (Uniform Resource Identifier), que se define en el RFC 3986, es más general que el URL, que puede incluso localizar un fragmento dentro de un recurso. La sintaxis URI para el protocolo HTTP es:
``` sh
http://host:port/path?request-parameters#nameAnchor
```
* Los parámetros de la petición, en forma de pares nombre = valor, se separan de la URL por un '?'. Los pares nombre = valor están separados por un '&'.
* El #nameAnchor identifica un fragmento dentro del documento HTML, que se define a través de la etiqueta de ancla ... .
* URL rescribe para la gestión de la sesión, por ejemplo, "...; Id.sesión = xxxxxx".

### Método de Solicitud "POST"

El método de solicitud POST se utiliza para añadir datos adicionales "post" hasta el servidor (por ejemplo, la presentación de los datos del formulario HTML o cargando un archivo). La emisión de un URL HTTP desde el navegador siempre activa una solicitud GET. Para desencadenar una solicitud POST, puede utilizar un formulario HTML con el método de atributo = "post" o escribir su propio programa de la red. Para la presentación de los formularios HTML, La solicitud POST es la misma que la solicitud GET, excepto que la cadena de consulta con codificación URL se envía en el cuerpo de la solicitud, en lugar de adjuntó detrás de la solicitud URI.

La solicitud POST toma la siguiente sintaxis:
``` sh
POST request-URI HTTP-version
Content-Type: mime-type
Content-Length: number-of-bytes
(other optional request headers)

(URL-encoded query string)
```

Las Cabeceras de petición Content-Type y Content-Length son necesaria en la solicitud POST para informar al servidor el tipo y la longitud del cuerpo de la petición.

**Ejemplo: Presentando Formularios de datos usando métodos de petición POST**

Usamos el mismo script HTML que antes, pero cambiamos el método de solicitud a POST.
``` sh
<html>
<head><title>Login</title></head>
<body>
  <h2>LOGIN</h2>
  <form method="post" action="/bin/login">
    Username: <input type="text" name="user" size="25" /><br />
    Password: <input type="password" name="pw" size="10" /><br /><br />
    <input type="hidden" name="action" value="login" />
    <input type="submit" value="SEND" />
  </form>
</body>
</html>
```
Suponiendo que el usuario ingresa "Peter lee" como username y "123456" como contraseña, y despues hace click sobre el boton enviar, la siguiente solicitud post sera generada por el navegador:
``` sh
POST /bin/login HTTP/1.1
Host: 127.0.0.1:8000
Accept: image/gif, image/jpeg, */*
Referer: http://127.0.0.1:8000/login.html
Accept-Language: en-us
Content-Type: application/x-www-form-urlencoded
Accept-Encoding: gzip, deflate
User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)
Content-Length: 37
Connection: Keep-Alive
Cache-Control: no-cache

User=Peter+Lee&pw=123456&action=login
```
Tenga en cuenta que la cabecera Content-Type informa al servidor que los datos se codifican en URL (con un tipo MIME especial application/x-www-form-urlencoded), y la cabecera Content-Length indica al servidor el número de bytes que se lee en el cuerpo del mensaje.

**POST vs GET Para presentacion de formas de datos**

Como se mencionó en la sección anterior, La solicitud POST tiene las siguientes ventajas en comparación con la solicitud GET en el envío de la cadena de consulta:

* La cantidad de datos que pueden ser publicado es ilimitada, y se mantienen en el cuerpo de la petición, que generalmente se envía al servidor en un flujo de datos independiente.
* La cadena de consulta no se muestra en el cuadro de dirección del navegador.

Tenga en cuenta que aunque la contraseña no se muestra en el cuadro de dirección del navegador, se transmite al servidor en texto claro, y se somete a la red sniffing. Por lo tanto, el envío de la contraseña mediante una solicitud POST no es absolutamente seguro.

### Carga de Archivos utilizando multipartes/Petición POST form-data

"RFC 1867: Forma basada en la carga de archivos en HTML" especifica que un archivo se puede cargar en el servidor mediante una petición POST de un formulario HTML. Un nuevo tipo de atributo = "archivo" se añadió a la etiqueta de HTML para soportar la carga de archivos. Los datos de la carga de archivos de un POST no está codificada en URL (en el estándar application / x-www-form-urlencoded), pero utiliza un nuevo tipo MIME multipart / form-data.

**Ejemplo**

La siguiente forma HTML PUEDE ser usada para subir archivos:
``` sh
<html>
<head><title>File Upload</title></head>
<body>
  <h2>Upload File</h2>
  <form method="post" enctype="multipart/form-data" action="servlet/UploadServlet">
    Who are you: <input type="text" name="username" /><br />
    Choose the file to upload:
    <input type="file" name="fileID" /><br />
    <input type="submit" value="SEND" />
  </form>
</body>
</html>
upload
```
![](https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTML_FileUploadForm.png)

Cuando el navegador encuentra una etiqueta con el atributo de tipo "archivo" =, se muestra un cuadro de texto y un "... Examinar", para permitir al usuario elegir el archivo para ser cargado.

Cuando el usuario hace clic en el botón de enviar, el navegador envía los datos del formulario y el contenido del archivo (s) seleccionado. El viejo tipo de codificación "application / x-www-form-urlencoded" es ineficiente para el envío de datos binarios y los caracteres no ASCII. Un nuevo tipo de medio "multipart / form-data" se utiliza en su lugar.

Cada parte identifica el nombre de entrada en el formulario HTML original, y el tipo de contenido si se conoce los medios, o como application / octet-stream de otro modo.

El nombre de archivo local original podría ser suministrado como parámetro "nombre de archivo", o en el "Content-Disposition: form-data" de cabecera.

Un ejemplo del mensaje POST de carga de archivos es la siguiente:
``` sh
POST /bin/upload HTTP/1.1
Host: test101
Accept: image/gif, image/jpeg, */*
Accept-Language: en-us
Content-Type: multipart/form-data; boundary=---------------------------7d41b838504d8
Accept-Encoding: gzip, deflate
User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)
Content-Length: 342
Connection: Keep-Alive
Cache-Control: no-cache

-----------------------------7d41b838504d8 Content-Disposition: form-data; name="username" 
Peter Lee
-----------------------------7d41b838504d8 Content-Disposition: form-data; name="fileID"; filename="C:\temp.html" Content-Type: text/plain 
<h1>Home page on main server</h1> 
-----------------------------7d41b838504d8--
```

Servlet 3.0 provee soporte construido para el procesamiento de carga, "Uploading Files in Servlet 3.0"

### Método de solicitud "CONNECT"

La solicitud de conexión HTTP se utiliza para pedir a un proxy establecer una conexión con anteras de acogida y simplemente retransmitir el contenido, en lugar de intentar analizar o almacenar en caché el mensaje. Esto a menudo se utiliza para realizar una conexión a través de un proxy.

(En construcción)

### Otros Métodos de Petición

PU: Pregunta al servidor para guardar datos

DELETE: Pregunta al servidor para borrar información

Para consideraciones de seguridad, PUT y DELETE no son soportadas por la mayoria de los servidores de producción.

Métodos de extención (de igual manera errores de codigo y cabezeras) pueden ser definidos para extnder la funcionalidad del protocolo HTTP.

(En construcción)

### Contenido de Negociaión

Como se menciona anteriormente, HTTP soporta la negociación de contenido entre el cliente y el servidor. Un cliente puede utilizar los encabezados de solicitudes adicionales (como Aceptar, Accept-Language, Accept-Charset, Accept-Encoding) para indicar al servidor que puede manejar o el contenido que se prefiere. Si el servidor posee varias versiones de un mismo documento en un formato diferente, devolverá el formato que el cliente prefiera. Este proceso se llama negociación de contenido.

### Negociación Tipo de contenido

El servidor utiliza un archivo de configuración MIME (llamado "conf \ mime.types") para asignar la extensión de archivo a un tipo de medio, de modo que pueda determinar el tipo de medio del archivo examinando su extensión de archivo. Por ejemplo, las extensiones de archivos "htm", "html" están asociados con el tipo de medio MIME "text / html", la extensión de archivo ".jpg", ".jpeg" están asociados con "image / jpeg". Cuando un archivo se devuelve al cliente, el servidor tiene que aguantar una cabecera de respuesta Content-Type para informar al cliente el tipo de soporte de los datos.

Para la negociación de tipo de contenido, supongamos que las solicitudes de los clientes para un archivo llamado "logo" , sin especificar su tipo, y envía una cabecera "Accept: image / gif, image / jpeg, ...". Si el servidor tiene 2 formatos del "logo": "logo.gif" y "logo.jpg", y el archivo de configuración MIME tiene las siguientes entradas:
``` sh
image/gif        gif
image/jpeg       jpeg jpg jpe
```

El servidor devolverá "logo.gif" al cliente, basado en la cabecera la cabezera accept del cliente , y la asignación de tipo MIME / archivo. El servidor incluirá un "Content-type: image / gif" en el encabezado de respuesta.

Se muestra el siguiente mensaje:

``` sh
GET /logo HTTP/1.1
Accept: image/gif, image/x-xbitmap, image/jpeg, image/pjpeg,
  application/x-shockwave-flash, application/vnd.ms-excel, 
  application/vnd.ms-powerpoint, application/msword, */*
Accept-Language: en-us
Accept-Encoding: gzip, deflate
User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)
Host: test101:8080
Connection: Keep-Alive
(blank line)
```
``` sh
HTTP/1.1 200 OK
Date: Sun, 29 Feb 2004 01:42:22 GMT
Server: Apache/1.3.29 (Win32)
Content-Location: logo.gif
Vary: negotiate,accept
TCN: choice
Last-Modified: Wed, 21 Feb 1996 19:45:52 GMT
ETag: "0-916-312b7670;404142de"
Accept-Ranges: bytes
Content-Length: 2326
Keep-Alive: timeout=15, max=100
Connection: Keep-Alive
Content-Type: image/gif
(blank line)
(body omitted)
```
Sin embargo, el servidor tiene 3 archivos "logo.*", "logo.gif", "logo.html", "logo.jpg" y "Accept: /" es usado:
``` sh
GET /logo HTTP/1.1
Accept: */*
Accept-Language: en-us
Accept-Encoding: gzip, deflate
User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)
Host: test101:8080
Connection: Keep-Alive
(blank line)
```
``` sh
HTTP/1.1 200 OK
Date: Sun, 29 Feb 2004 01:48:16 GMT
Server: Apache/1.3.29 (Win32)
Content-Location: logo.html
Vary: negotiate,accept
TCN: choice
Last-Modified: Fri, 20 Feb 2004 04:31:17 GMT
ETag: "0-10-40358d95;404144c1"
Accept-Ranges: bytes
Content-Length: 16
Keep-Alive: timeout=15, max=100
Connection: Keep-Alive
Content-Type: text/html
(blank line)
(body omitted)
```
``` sh
Accept: */*
```
Las siguientes directivas de configuración de apache son relevantes al tipo de contenido de negociación:

* La diretiva TypeConfig puede ser usada para especificar la localización del mapeo del archivo MIME.
``` sh
TypeConfig conf/mime.types
```

* La directiva AddType puede ser usada para incluir Mapeos del tipo MIME adicionales al contenido del archivo.
``` sh
AddType mime-type extension1 [extension2]
```
* La directiva DefaultType da el tipo MIME de una extención de archivo desconocida(en el tipo-de-contenido de la cabezera de respuesta).
``` sh
DefaultType text/plain
```

### Lenguaje de Negociación y "Opciones de Multivista"

Las directivas de opciones de multivista es una forma simple de implementar lenguajes de negociación. Por ejemplo:
``` sh
AddLanguage en .en
<Directory "C:/_javabin/Apache1.3.29/htdocs">
    Options Indexes MultiViews
</Directory>
```

Suponiendo que el cliente solicita el archivo "index.html" y envia un "Accept-Lenguage: en-us", Si el servidor tiene "test.html", "test.html.en" and "test.html.cn" basados en las preferencias del cliente "test.html.en" sera regresado ("en" incluye "en-us")

Un trazo del mensaje es el siguiente:
``` sh
GET /index.html HTTP/1.1
Accept: */*
Accept-Language: en-us
Accept-Encoding: gzip, deflate
User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)
Host: test101:8080
Connection: Keep-Alive
(blank line)
```
``` sh
HTTP/1.1 200 OK
Date: Sun, 29 Feb 2004 02:08:29 GMT
Server: Apache/1.3.29 (Win32)
Content-Location: index.html.en
Vary: negotiate
TCN: choice
Last-Modified: Sun, 29 Feb 2004 02:07:45 GMT
ETag: "0-13-40414971;40414964"
Accept-Ranges: bytes
Content-Length: 19
Keep-Alive: timeout=15, max=100
Connection: Keep-Alive
Content-Type: text/html
Content-Language: en
(blank line)
(body omitted)
```

Se necesita la directiva AddLanguage para asociar un código de idioma con una extensión de archivo, similar a la asignación de tipo/archivo MIME.

Tenga en cuenta que la directiva "Options All" no incluye la opción "MultiViews". Es decir, hay que girar de forma explícita en MultiViews.

La directiva LanguagePriority puede ser usada para especificar la preferencia de idioma en caso de empate durante la negociación de contenido o si el cliente no expresa una preferencia. Por ejemplo:
``` sh
<IfModule mod_negotiation.c>
   LanguagePriority en da nl et fr de el it ja kr no pl pt pt-br
</IfModule>
```

### Conjunto de Caracteres de Negociación

Un cliente puede utilizar la solicitud de cabecera Accept-Charset para negociar con el servidor el conjunto de caracteres que prefiere.
``` sh
Accept-Charset: charset-1, charset-2, ...
```
Los conjuntos de caracteres comúnmente encontrados incluyen: ISO-8859-1 (Latin-I), ISO-8859-2, ISO-8859-5, Big5 (chino tradicional), GB2312 (chino simplificado), UCS2 (2 bytes Unicode), UCS4 (4 bytes Unicode), UTF-8 (Unicode codificada), y etc.

Del mismo modo, la directiva AddCharset se utiliza para asociar la extensión de archivo con el conjunto de caracteres. Por ejemplo:
``` sh
AddCharset ISO-8859-8   .iso8859-8
AddCharset ISO-2022-JP  .jis
AddCharset Big5         .Big5  .big5
AddCharset WINDOWS-1251 .cp-1251
AddCharset CP866        .cp866
AddCharset ISO-8859-5   .iso-ru
AddCharset KOI8-R       .koi8-r
AddCharset UCS-2        .ucs2
AddCharset UCS-4        .ucs4
AddCharset UTF-8        .utf8
```
### Negociación de codificación
Un cliente puede utilizar el encabezado Accept-Encoding para indicar al servidor el tipo de codificación que soporta. Los esquemas de codificación comunes son: "x-gzip (.gz, .tgz)" y "x-compress (.Z)".
``` sh
Accept-Encoding: Codificación-método-1, que codifica-método-2, ...
```
Del mismo modo, la directiva AddEncoding se utiliza para asociar la extensión de archivo con el esquema de una codificación. Por ejemplo:
``` sh
AddEncoding x-compress  .Z
AddEncoding x-gzip      .gz .tgz
```

### Conexiones Persistentes (o Keep-alive)

En HTTP / 1.0, el servidor cierra la conexión TCP después de entregar la respuesta por defecto (Connection: Close). Es decir, cada uno de servicios de conexión TCP es sólo una petición. Esta no es eficiente cuando muchas páginas HTML contienen hipervínculos (a través de la etiqueta href="URL">a) a otros recursos (como imágenes, scripts - ya sea local o desde un servidor remoto). Si se descarga una página que contiene 5 imágenes en línea, el navegador tiene que establecer una conexión TCP 6 veces en el mismo servidor.

El cliente puede negociar con el servidor y pedir al servidor no cerrar la conexión después de la entrega de la respuesta, de modo que otra petición puede ser enviada a través de la misma conexión. Esto se conoce como conexión persistente (o keep-alive conexión). Las conexiones persistentes mejoran en gran medida la eficiencia de la red. Para HTTP / 1.0, la conexión por defecto es no persistente. Para solicitar conexión persistente, el cliente debe incluir un encabezado de solicitud "Conexión: keep-alive" en el mensaje de petición de negociar con el servidor.

Para HTTP / 1.1, la conexión por defecto es persistente. El cliente no tiene que enviar la cabecera "Conexión: keep-alive" . En su lugar, el cliente puede desear enviar la cabecera "Connection: Close" para pedir al servidor para cerrar la conexión después de la entrega de la respuesta.

La conexión persistente es extremadamente útil para páginas web con muchas imágenes pequeñas en línea y otros datos asociados, ya que todos estos pueden ser descargadas a través de la misma conexión. Los beneficios para la conexión persistente son:

* Tiempo de CPU y ahorro de recursos en la apertura y cierre de conexión TCP en el cliente, proxy, puertas de enlace, y el servidor de origen.
* La Solicitud puede ser "pipeline". Es decir, un cliente puede hacer varias solicitudes sin esperar a que cada respuesta, con el fin de utilizar la red de manera más eficiente.
* Una respuesta más rápida ya que no hay tiempo necesario para realizar la conexión del protocolo de enlace de apertura TCP.

En servidores HTTP Apache, varias directivas de configuración están relacionados con las conexiones persistentes:

La directiva KeepAlive decide si admite conexiones persistentes. Esto toma el valor de encendido o apagado.
``` sh
KeepAlive On|Off
```

La directiva MaxKeepAliveRequests establece el número máximo de solicitudes que se pueden enviar a través de una conexión persistente. Se puede establecer en 0 para permitir que un número ilimitado de solicitudes. Se recomienda establecer en un número alto para un mejor rendimiento y eficiencia de la red.
``` sh
MaxKeepAliveRequests 200
```
La directiva KeepAliveTimeOut establece tiempo de espera para un conexión peristente en espera de la siguiente solicitud.
``` sh
KeepAliveTimeout 10
```

### Rango de descarga
``` sh
Accept-Ranges: bytes
Transfer-Encoding: chunked
```
(En construcción)

### Control de cache

El cliente puede enviar un encabezado de solicitud "Cache-Control: no cache" para indicar al proxy que consiga una copia fresca del servidor original, aun cuando hay una copia en la cache local, Desafortunadamente el servidor HTTP/1.0 no entiende esta cabecera, pero usa un viejo encabezado de solicitud "Pragma: no-cache" Usted puede incluir varias cabeceras en su petición.
``` sh
Pragma: no-cache
Cache-Control: no-cache
```

(Más, En construcción)

### REFERENCIAS Y RECURSOS

* W3C HTTP specifications at http://www.w3.org/standards/techs/http.
* RFC 2616 "Hypertext Transfer Protocol HTTP/1.1", 1999 @ http://www.ietf.org/rfc/rfc2616.txt.
* RFC 1945 "Hypertext Transfer Protocol HTTP/1.0", 1996 @ http://www.ietf.org/rfc/rfc1945.txt.
* STD 2: "Assigned numbers", 1994.
* STD 5: "Internet Protocol (IP)", 1981.
* STD 6: "User Datagram Protocol (UDP)", 1980.
* STD 7: "Transmission Control Protocol (TCP)", 1983.
* RFC 2396: "Uniform Resource Identifiers (URI): Generic Syntax", 1998.
* RFC 2045: "Multipurpose Internet Mail Extension (MIME) Part 1: Format of Internet Message Bodies", 1996.
* RFC 1867: "Form-based File upload in HTML", 1995, (obsoleted by RFC2854).
* RFC 2854: "The text/html media type", 2000.
* Mutlipart Servlet for file upload @ www.servlets.com