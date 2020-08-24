# GOOGLE HACKING / DORKING 

* [¿Qué es el dorking?](#¿Qué-es-el-dorking?)
* [Importancia](#Importancia)
* [Conceptos basicos](#Conceptos-basicos)
* [¿Cómo usar esto en el "hacking"?](#¿Cómo-usar-esto-en-el-"hacking"?)


## ¿Qué es el dorking?

El Google hacking o Dorking no es mas que un modo de buscar cosas un poco mas especializada,
por el nombre "Google Hacking" se puede dar la imprecion de que solo se usa en google, pero eso no es correcto.
El dorking no es mas que una busqueda avanzada en donde hacemos uso de operadores que funcionan como un filtro
para dirigir la busqueda directamente a donde nosotros queremos, tambien usamos simbolos para buscar palafras o frases exactas.
Esto nos servirá para buscar en casi cualquier motor de busqueda que encontremos en internet.

## Importancia

El saber un poco de "Dorking" nos ayuda en muchos aspectos de nuestra vida, no es solo para buscar paginas vulnerables
recordemos que el termino "Hacking" primeramente se utiliza cuando una persona domina mucho una cosa a tal grado
que puede ver las cosas desde otros puntos de vista y asi llegar a ver o alcanzar cosas que otras personas no pueden,
si salimos un poco de la informatica podemos usar un ejemplo.

Un mecanico que tiene años trabajando con carros y se especializa en motores, el con el tiempo ya entiende 
mucho mejor los problemas de un motor que cualquier otro mecanico, al tener mucha mas experiencia en el tema,
se puede decir que el es un "hacker" en mecanica por llegar a saber eso.

Volviendo al tema de Dorking es muy importante que todas las personas sepan un poco de esto, en este escrito se tratará de 
explicar lo mas detalladamente posible como comenzar y si ya sabes algo de esto puedas reforzar temas basicos.

## Conceptos basicos

Como se explicó antes, estas busquedas avanzadas usan operadores y simbolos, como los siguientes: 

Vamos a empezar con algunos operadores muy comunes:



* site: sólo busca resultados dentro de la web que va detrás de “site:”

      Ejemplo: site:www.google.com 
      Esta busqueda solo nos mostrará resultados de la pagina de Google 
      
* intitle o allintitle: Esto solo buscará en los titulos 
      
      Ejemplo: intitle:"Google dorking"
      Esta busqueda nos mostrará solo articulos que tengan la frase "google dorkin" en su titulo
      
* inurl o allinurl: los resultados estarán en la url de las paginas 

      Ejemplo: inurl: /parametro.php?id=
      Esta busqueda nos mostrará resultados paginas en donde contengan "/parametro.php?id=" en su url.
      
      Nota: Este se puede confundir un poco al inicio con el operador "site" por que si no expresamos bien
      lo que queremos encontrar y ponemos un sitio web, nos mostrará el mismo resultado que el operador "site".
      
      Recordemos que un link o url tiene la siguiente sintaxis dependiendo si el administrador de la pagina
      configuró o no los links para que sean mas amigables.
      
      Sitio con links no amigables:
      `http/s://www.sitiowebdeejemplo.com/parametro1.php?id=1&parametro2.php?id=22`
      
      Sitio con links amigables:
      `http/s://www.sitiowebdeejemplo.com/ejemplo`
      
* filetype o ext: sólo busca archivos (doc, xls, txt…) 
        
      Nota: Este operador va acompañado con alguno de los que acabamos de ver.
      Ejemplo: site:www.paginaweb.com filetype:.pdf
      Esta busqueda nos mostrará los archivos .pdf que esten "sueltos" o que esten filtrados en la red desde la pagina www.paginaweb.com 
      
* related: busca webs relacionadas con una determinada.
        
      Ejemplo: relates: www.google.com 
      Nos mostrará paginas parecidas a google, es decir, nos mostrará otros motores de busqueda
      
* cache: muestra el resultado en la cache de Google de una página web.
      
      Ejemplo: cache:www.google.com
      Nos mostrará la pagina web guardada en el cache de google
      
* define: busca definiciones de palablas

      Ejemplo: define:linux
      Nos mostrará resultados en donde se defina que es linux
      
* Allintext o intext: nos buscara la frase exacta que pongamos

      Ejemplo: Allintext:abcdefghijklmnopqrstuvwxyz
      Nos mostrará paginas en donde venga el abecedario 
     
* weather: nos mostrará el clima de la parte del mundo que queramos ver 

      Ejemplo: weather:México
      Nos mostrará el clima de la ciudad de México 
      
* stock: nos mostrará informacion financiera 

      Ejemplo: ````
               stock:TSLA
               stock:goog
               ```
      Esto nos mostrará la informacion financiera de la bolsa de valores 
      
* link: nos muestra las paginas en donde esta enlazada la pagina que buscamos 

      Ejemplo: link:www.youtube.com
      Nos mostrará todas las paginas que enlazan algun link de youtube en su pagina 
      
Ahora vamos a ver algunos simbolos muy importantes:

* ” ” (comillas): buscar frase exacta
       
      Ejemplo: "alert(Y000!)"
      En este caso estoy buscando mi propio apodo o mi nick de twitter 
      
* `+ y -` : incluir o excluir alguna palabra

      ejemplo: animales -perros
      Esto nos da como resultado muchas paginas que hablan de animales pero intenta excluir todas las paginas en donde se hable de perros
      
* `*` (asterisco): comodín, cualquier palabra, pero una sóla palabra.
      
      Ejemplo: site:*.google.com
      Lo cual nos mostrará todas las paginas de google incluyendo sus subdominios.
      
      
## ¿Cómo usar esto en el "hacking"?      

Primero que nada, tenemos que tener muy en claro lo que queremos lograr, lo que vamos a buscar y lo que queremos encontrar.

Para poder empezar en el Google hacking ya viendo desde una perspectiva en donde queremos encontrar "informacion" que no todos pueden encontrar, tenemos que conocer
archivos que contengan esa informacion, tenemos que conocer los sistemas en los cuales se basa una pagina web, tenemos que estar enterados de todo un poco. 

El primer ejemplo que vamos a ver es el de como buscar el archivo "robots.txt", pero primero para buscar ese archivo tenemos que saber: ¿Qué es?, ¿qué contiene?,
¿Porqué las paginas lo usan?, no podemos buscar algo solo por buscarlo sin saber que es.

El archivo "robots.txt" es para facilitar la indexación de un sitio web.  Este archivo sirve para dar instrucciones a los robots sobre qué contenidos deben rastrear y cuáles no y cómo deberían hacerlo. En palabras mas faciles ese archivo sirve para que la pagina web este "segura" de las busquedas de google, ya que en el archivo vienen las paginas que el administrador no quiere que se vean en los resultados de google, vamos, que es como excluir las paginas para no ser encontradas.

Este archivo en concreto esta escrito de la siguiente manera: 

```
User-agent: *


Disallow: /ejemplo/
Disallow: /1/ejemplo/
Disallow: /2/
Disallow: /ejemplo2/
Disallow: /ejemplo3/
Disallow: /3/ejemplo4
Disallow: /no_quiero_que_me_vean
Allow: /yo_si_quiero_que_me_vean
Allow: /yo_tambien

```
Se usa de la siguiente manera en el link de la pagina:

`https://www.paginadeejemplo.com/robots.txt`

Con lo cual tenemos muchas maneras de como encontrarlo, por ejemplo... sabemos en que parte de el link esta, sabemos que se usa en la url:

podemos hacer una busqueda como la siguiente:

`inurl:robots.txt` pero esto nos mostrará resultados muy generales y puede ser que encuentre el archivo o algo relacionado a el

aqui es cuando vamos a usar de verdad los operadores, los vamos a mezclar para obtener mejores resultados:

usando el operador "site" + "inurl" y el simbolo `*` hacemos la busqueda mucho mas especifica:

`site:www.google.com inurl:robots.txt` ya con esto enfocamos que la busqueda es en la pagina de google, y listo!! nos da como resultado: https://www.google.com/robots.txt

pero si queremos hacen mucho mas especifica la busqueda podemos usar:

`site:*.com.mx inurl:/robots.txt intext:"User-agent:"`

En este caso estamos reduciendo los resultados a solo paginas que tengan el dominio .com junto con .mx ".com.mx" lo que quiere decir que estamos buscando paginas
Méxicanas ya que el dominio .mx pertenece a paginas alojadas en mexico, al encontrar esas paginas se aplica el operador inurl:/robots.txt que eso reduce aun mas 
paginas encontradas a solo las que contengan la palabla "robots.txt" en su url, por ultimo entra intext:"User-agent:" a reducir aun mas los resultado anteriores 
y verificando que las paginas encontradas antes tengan la palabra "user-agent:" en ellas, ahora si podemos asegurar que las paginas que encontramos nos mostraran el
archivo robots.txt de cada pagina.

Ese es solo un ejemplo de como utilizar los operadores para encontrar cosas interesantes.

