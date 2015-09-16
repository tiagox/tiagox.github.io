---
layout: post
title: Como usar HyperSQL en Ubuntu
date: 2010-03-29 23:15:30.000000000 -03:00
categories:
- blog
tags:
- bases de datos
- databases
- hibernate
- hsql
- hsqldb
- hypersql
- java
- linux
- ubuntu
status: publish
type: post
published: true
meta:
  display: Imported from santiagorojo.com.ar
  dsq_thread_id: '539763348'
author:
  display_name: tiagox
  email: sr@santiagorojo.com.ar
  first_name: Santiago
  last_name: Rojo
  login: admin
---
HyperSQL es un motor de base de datos liviano que tiene la posibilidad de
funcionar en memoria. En los casos en los que necesitamos una forma rápida y
sencilla de probar algún proyecto, es bueno tener a mano una herramienta que no
requiera de una infraestructura demasiado compleja y que sea fácil de utilizar.

HyperSQL esta desarrolla en Java, y es una buena opción para trabajar con bases
de datos con este mismo lenguaje.

A continuación voy a instalar y configurar este motor de base de datos en
Linux/Ubuntu (e imagino que servirá para la mayoría de las distros Debian-
based).

Primero instalamos por medio de apt los paquetes que encontramos en los
repositorios oficiales de Ubuntu.

{% highlight sh %}
sudo apt-get install hsqldb-server
{% endhighlight %}{: .noscroll}

Ahora se configuran los archivos del motor.

{% highlight sh %}
sudo gedit /etc/hsqldb/server.properties
{% endhighlight %}{: .noscroll}

Este archivo hay que modificarlo, descomentando la linea donde se indica la
ubicación de los archivos de la base. Con lo que el archivo resultante quedará
de la siguiente forma.

{% highlight sh %}
# HSQLDB server configuration file
# See the Advanced Topics chapter of the Hsqldb User Guide.
# See also the file /etc/hsqldb/sqltool.rc.

server.database.0       file:///var/lib/hsqldb/db0/db0
{% endhighlight %}{: .noscroll}

Y lo mismo con.

{% highlight sh %}
sudo gedit /etc/hsqldb/webserver.properties
{% endhighlight %}{: .noscroll}

Hay que descomentar la ultima linea que indica la ubicación de los archivos del
servidor.

{% highlight sh %}
# HSQLDB server configuration file
# See the Advanced Topics chapter of the Hsqldb User Guide.
# See also the file /etc/hsqldb/sqltool.rc.

server.port 8080

server.database.0       file:///var/lib/hsqldb/db0/db0
{% endhighlight %}{: .noscroll}

De esta forma ya esta configurado correctamente y ahora solo queda iniciar el
servicio. Como casi todo en Ubuntu le damos inicio mediante.

{% highlight sh %}
sudo /etc/init.d/hsqldb-server start
{% endhighlight %}{: .noscroll}

Con esto ya es suficiente para poder utilizar nuestra base de datos liviana.
Solo debemos tener en cuenta que para trabajar con esta los datos de
configuración son:

{% highlight text %}
url      : jdbc:hsqldb:db0://localhost
driver   : org.hsqldb.jdbcDriver
login    : sa
password :
libsql   : hsqldb.jar
{% endhighlight %}{: .noscroll}

Simplemente con eso ya tenemos listo nuestro pequeño entorno de pruebas de bases
de datos.

Un detalle que me pareció importante rescatar es lo que encontré en la
documentación de HyperSQL, y que fue algo que me tuvo un rato entretenido
intentando hacerlo, que fue la simple tarea de crear una base de datos o schema
(como prefieran), un textual de la documentación:

> ## Cómo crear una nueva base de datos
>
> Una nueva base de datos se crea automáticamente si esta no existe aún. Sólo
> hay que conectar a la "aún no existente" base de datos mediante el
> `jdbc:oracle:file:<ruta-de-la-base-de-datos>` URL (debe
> reemplazar la última parte de la ruta que desea) con el usuario 'sa' y una
> contraseña vacía.

[Link a la documentación](http://hsqldb.org/web/hsqlFAQ.html#NEWDB)

Espero que esta información pueda servirle a cualquiera que quiera utilizar esta
tecnología.

Fuente: [javageek.free.fr](http://javageek.free.fr/wiki/index.php/Ubuntu:Programming#HSQL)
