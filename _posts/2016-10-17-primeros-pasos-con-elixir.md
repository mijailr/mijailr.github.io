---
layout: post
title: "Primeros pasos con Elixir"
category: Elixir
date: 2016-10-17
---

Desde hace algún tiempo, vengo escuchando sobre [Elixir](http://elixir-lang.org/) y la verdad no le había prestado atención porque con [Ruby](http://www.ruby-lang.org/en/) tenía lo suficiente para hacer lo que necesitaba. Sin embargo, últimamente he estado sintiendo presión social para aprender *Elixir*

> Elixir es un lenguaje dinámico y funcional diseñado para construir aplicaciones escalables y mantenibles.

Creo que el mejor recurso para aprender que es Elixir es yendo directamente a la fuente, por lo que recomiendo leer (completo) [Elixir-School](https://elixirschool.com)

No había tenido previamente ninguna experiencia con **Functional Programming** (al menos no conscientemente) y _Ruby me acostumbro a ver todo como un objeto_ por lo que tuve que hacer un esfuerzo en romper el OOP. Hay una serie de artículos de Charles Scalfani([@cscalfani](https://twitter.com/cscalfani)) que me ayudaron bastante a comprender este tema: [So You Want to be a Functional Programmer](https://medium.com/@cscalfani/so-you-want-to-be-a-functional-programmer-part-1-1f15e387e536#.efetv2g1r)

Hay que dedicarle un tiempo a esa sección y derrepente sentirás que la _programación funcional_ es más natural que la _orientada a objetos_. Llegados a este punto, hay que leer obligatoriamente la guía [_"Elixir Getting Started Guide"_](https://elixir-lang.org/getting-started/introduction.html) mientras lo leía, se me hacía necesario aplicar algunos elementos para entender mejor su funcionamiento, por lo que empecé a utilizar [Exercism](https://exercism.io) para realizar algunos ejercicios. También realicé completo el [elixir-koans](https://github.com/elixirkoans/elixir-koans) lo cual es muy util para entender algunos comportamientos.

La sintaxis de Elixir está inspirada en Ruby y esa es una de las cosas que más me agrada, lo otro que le da un plus es que la comunidad apenas está creciendo, por lo que representa una oportunidad para aportar en el desarrollo.

Aqui dejo un ejemplo del famoso `HolaMundo` para Ruby y Elixir respectivamente

{% highlight ruby %}
# Con Ruby
module HolaMundo
  def self.hola(quien = "Mundo")
    puts "Hola #{quien}!"
  end
end
{% endhighlight %}

Luego en `irb`

{% highlight ruby %}
001> HolaMundo.hola "Mijail"
Hola Mijail!
=> nil
{% endhighlight %}

{% highlight elixir %}
# Con Elixir
defmodule HolaMundo do
  def hola(quien \\ "Mundo") do
    IO.puts "Hola #{quien}!"
  end
end
{% endhighlight %}

Luego en `iex`

{% highlight elixir %}
iex(1)> HolaMundo.hola "Mijail"
Hola Mijail!
:ok
{% endhighlight %}

Como pueden notar, se parecen tanto que parece lo mismo, de verdad recomiendo empezar ya a aprender Elixir.

Actualmente estoy leyendo _"Elixir in Action"_ para profundizar un poco más en el tema.

**OJO:** Recomiendo también unirse al canal en [#Slack elixir-lang](https://elixir-slackin.herokuapp.com/)
