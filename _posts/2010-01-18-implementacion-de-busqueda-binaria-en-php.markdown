---
layout: post
title: Implementación de Búsqueda Binaria en PHP
date: 2010-01-18 16:43:26.000000000 -03:00
categories:
- blog
tags:
- binary search
- búsqueda binaria
- php
- recursividad
status: publish
type: post
published: true
meta:
  display: Imported from santiagorojo.com.ar
  dsq_thread_id: '536961092'
author:
  display_name: tiagox
  email: sr@santiagorojo.com.ar
  first_name: Santiago
  last_name: Rojo
  login: admin
---
La Búsqueda Binaria se utiliza para saber si un elemento se encuentra en una
colección de datos, como podría ser un array, un vector o cualquier estructura
de datos similar. Este algoritmo se basa en la premisa de que nuestra colección
de datos se encuentra ordenada por la misma clave que buscamos.

La filosofía del algoritmo es la de [_Divide et
impera_](http://es.wikipedia.org/wiki/Algoritmo_divide_y_vencerás), en el que la
idea es separar el problema en partes mas pequeñas, descartando lo que no me
sirve y quedándome con los rangos útiles. Los algoritmos de este tipo, que
descargan la mitad de los datos en cada comparación, se dice que son de un orden
de complejidad de:

{% highlight text %}
log( N )
{% endhighlight %}

Donde N es la cantidad de elementos de nuestra colección de datos. Así podemos
saber que en cada pasada, nos quedaran la mitad de los elementos, algo muy
importante a al hora de optimizar recursos.

La implementación que presento a continuación, esta hecha de forma recursiva. La
recursividad puede ser un tanto engañosa y colgar todo si no esta bien definida
su condición de corte.

{% highlight php linenos%}
<?php
function binarySearch($key, $collection, $start, $end){
    // Selección de la posición del elemento central.
    $pivot = (int)($start + ($end - $start) / 2);
    // Condición de corte.
    if($start >= $end) return FALSE;
    if($collection[$pivot] > $key){
        return binarySearch($key, $collection, $start, $pivot - 1);
    } else if ($collection[$pivot] < $subscriber){
        return binarySearch($key, $collection, $pivot + 1, $end);
    } else {
        return TRUE;
    }
}
{% endhighlight %}{: .noscroll}

Simplemente eso, este mismo algoritmo podría ser optimizado o mejorado en cuanto
a la inteligencia en el tratamiento de las variables `$start` y `$end`, haciendo
que el mismo script calcule estos datos. Yo no los calculo por un tema de
rendimiento.

Espero que pueda servirle a alguien en cualquier momento, desde ya esta todo el
mundo invitado a utilizar este código. Y obviamente a dejar sus comentarios al
respecto.
