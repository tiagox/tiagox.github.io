---
layout: post
title: Instalación simple de LAMP en GNU/Linux Ubuntu
date: 2012-02-29 18:52:01.000000000 -03:00
categories:
- blog
tags:
- apache
- instalar
- lamp
- linux
- mysql
- php
- tasksel
- ubuntu
status: publish
type: post
published: true
meta:
  display: Imported from santiagorojo.com.ar
  dsq_thread_id: '594065754'
author:
  display_name: tiagox
  email: sr@santiagorojo.com.ar
  first_name: Santiago
  last_name: Rojo
  login: admin
---
La manera mas sencilla de montar un servidor LAMP (Linux, Apache, MySQL y PHP)
en Ubuntu que encontré, es la de utilizar una pequeña aplicación, por linea de
comandos, que simplifica enormemente la tarea de instalación y configuración de
todos los paquetes necesarios para tener un entorno de desarrollo (no tan
mínimo) funcionando. La aplicación es `tasksel` y para poder instalarla basta
con poner en una terminal, `Ctrl+Alt+T` (Ubuntu):

{% highlight sh %}
sudo apt-get install tasksel
{% endhighlight %}{: .noscroll}

Una vez que se termina de instalar ejecutamos:

{% highlight sh %}
sudo tasksel
{% endhighlight %}{: .noscroll}

Y eso nos mostrará un listado de servicios, paquetes, escritorios alternativos y
muchas otras cosas que vale la pena revisar, pero en este caso el que nos
importa es la opción de **LAMP Server**.

![tasksel](/assets/tasksel.png){: .centered}

Durante el proceso de instalación, podrán configurar la contraseña de MySQL, y
otros parametro solicitados por `tasksel`.

Fácil, rápido e indoloro.
