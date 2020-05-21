---
layout: post
title: "Notas sobre List, Maps, Tuples y Keyword Lists de Elixir"
category: Elixir
languages: [Elixir]
date: 2016-10-26
---

Estoy leyendo el capítulo 2 de **Elixir in Action** y llegado al momento en que describe cada uno de los elementos *[List, Maps, Tuples, Keyword Lists, HashDict y HashSet]* consideré importante tomar nota de la diferencia de cada uno, ya que en un principio se ve confuso. Quizás más adelante y con más práctica se vuelva algo natural, veamos:

### List

Las **List** son usadas para administrar colecciones de datos dinámicos de tamaño variable y su sintaxis es similar a la del Array para (algunos) otros lenguajes. Pero aunque son similares a los Arrays para hacer algo con una lista hay que pasar por cada uno de sus miembros.

{% highlight elixir %}
iex(1)> ["Uno", 2, "tres"]
["Uno", 2, "tres"]
{% endhighlight %}

### Maps

Los **Maps** guardan valores de modo key-value donde tanto el *key* como el *value* puede tener cualquier cosa, y son muy útiles para combinar varios campos dentro de una estructura, es similar a los *Tuples* y *HashDict* pero ofrece la posibilidad de acceder a un campo por su nombre cuando este es un *Atom*

{% highlight elixir %}
iex(1)> map = %{uno: 1, dos: 2}
%{dos: 2, uno: 1}
iex(2)> map.uno
1
iex(2)> map[:dos]
2
{% endhighlight %}

### Tuples

Son algo como *estructuras de datos sin tipo que se usan para agrupar un número fijo de elementos* para devolver el dato de un Tuple, se utiliza la función *Kernel.elem/2* el cual acepta una Tuple y el indice del elemento en entero y para modificarlo se usa *Kernel.put_elem/3* con la Tuple, el index y el nuevo valor. Por la naturaleza inmutable de Elixir, no se modifica a nivel de memoria, por lo que hay que reasignarlo a la variable.

{% highlight elixir %}
iex(1)> tuple = {"uno", 2, "tres"}
{"uno", 2, "tres"}
iex(2)> elem(tuple, 0)
"uno"
iex(2)> put_elem(tuple, 1, "dos")
{"uno", "dos", "tres"}
{% endhighlight %}

### Keyword List

Los **Keyword List** son listas donde cada elemento son un Tuple de dos elementos, el primer elemento debe ser un Atom y el segundo de cualquier tipo, pero conserva las mismas características de una List y para seleccionar un elemento se utiliza *Keyword.get/2* donde se otorga el **Keyword List** y el Atom correspondiente.

{% highlight elixir %}
iex(1)> keyword = [uno: 1, dos: 2]
[uno: 1, dos: 2]
iex(2)> Keyword.get(keyword, :dos)
2
{% endhighlight %}
