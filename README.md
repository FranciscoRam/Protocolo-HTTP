# HTTP (Protocolo de Transferencia de Hipertexto)
## Basico

### Introducción
``` sh
```
#### La WEB
Internet (o la WEB) es un masivo distribuidor de sistema de información cliente/servicio  como se muestra en el siguiente diagrama.

![alt text][logo]
[logo]:https://github.com/FranciscoRam/Protocolo-HTTP/blob/master/imagenes/01.png?raw=true


Muchas aplicaciones se están ejecutando al mismo tiempo a través de Internet, tales como la navegación web/surfing, e-mail, transferencia de archivos, streaming de audio y video, y así sucesivamente. Para que una comunicación adecuada tenga lugar entre el cliente y el servidor, estas aplicaciones deben estar de acuerdo con un protocolo específico de nivel de aplicación como HTTP, FTP, SMTP, POP, etc.

#### Protocolo de Transferencia de Hipertexto (HTTP)
HTTP (Protocolo de Transferencia de Hipertexto) es quizás el protocolo de aplicación más popular en Internet (o en la web).
* HTTP es un protocolo cliente-servidor de petición-respuesta asimétrica como se ilustra. Un cliente HTTP envía un mensaje de petición a un servidor HTTP. El servidor, a su vez, devuelve un mensaje de respuesta. En otras palabras, HTTP es un protocolo de extracción, el cliente extrae la información desde el servidor (en lugar del servidor empujar información hasta el cliente).
![alt text][logo]
[logo]: https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP.png
* HTTP es un protocolo sin estado. En otras palabras, la solicitud actual no sabe lo que se ha hecho en las anteriores solicitudes.
* HTTP permite la negociación de tipo de datos y representación, a fin de permitir que los sistemas se construyan de forma independiente de los datos que se transfieren.
* Citando el RFC2616: "El Protocolo de transferencia de hipertexto (HTTP) es un protocolo de nivel de aplicación para distribucion, colaboración, sistemas de información hipermedia. Es un genérico sin estado, el protocolo que se puede utilizar para muchas tareas más allá de su uso para el hipertexto, por ejemplo. como servidores de nombres y sistemas de gestión de objetos distribuidos, a través de la extensión de sus métodos de petición, códigos de error y los encabezados".
 #### Navegador
Cada vez que se emite una dirección URL de su navegador para obtener un recurso web a través de HTTP, por ejemplo, http://www.nowhere123.com/index.html, el navegador vuelve la dirección URL en un mensaje de solicitud y la envía al servidor HTTP. El servidor HTTP interpreta el mensaje de petición, y le devuelve un mensaje de respuesta apropiada, que puede ser el recurso que ha solicitado o un mensaje de error. Este proceso se ilustra a continuación:

![alt text][logo]
[logo]: https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_Steps.png

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

![alt text][logo]
[logo]: https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_OverTCPIP.png

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

![alt text][logo]
[logo]:https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_MessageFormat.png

#### Petición de mensaje HTTP
El formato de un mensaje de petición HTTP es como sigue:
![alt text][logo]
[logo]:https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_RequestMessage.png
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
![alt text][logo]
[logo]:https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_RequestMessageExample.png

#### Mensaje de respuesta HTTP
El formato del mensaje de respuesta HTTP es como sigue:
![alt text][logo]
[logo]:https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_ResponseMessage.png
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
![alt text][logo]
[logo]:https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_ResponseMessageExample.png
