# GOOGLE HACKING / DORKING 

* [¿Qué es el dorking?](#¿Qué-es-el-dorking?)
* [Importancia](#Importancia)
* [Conceptos basicos](#Conceptos-basicos)
* [¿Cómo usar esto en el "hacking"?](#¿Cómo-usar-esto-en-el-"hacking"?)
* [Ejemplos de dorks](#Ejemplos-de-dorks)
* [Dorks para inyeccion sql y xss](#Dorks-para-inyeccion-sql-y-xss)
* [Dorks para encontrar camaras](#Dorks-para-encontrar-camaras)
* [OSINT y DORKS](#OSINT-y-DORKS)
* [Importancia final](#Importancia-final)


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

Por otra parte tambien podemos enfocarnos en buscar paginas que esten hechas en algun CMS en especifico, por ejemplo WORDPRESS, este se ha caracterizado por ser muy comodo para trabajar en el y bastante facil ya que contiene muchos plugins que nos pueden ser de mucha ayuda, pero al mismo tiempo estos complementos pueden venir con muchos fallos que permiten a otra persona explotar varias vulnerabilidades. 

Para encontrar paginas creadas en WORDPRESS primero tenemos que conocer un poco de el, su estructura basica de archivos y carpetas, los archivos mas importantes... etc, aqui voy a tratar de explicar un poco para entender mejor por que es importante conocer eso:

WORDPRESS utiliza la siguiente estructura en su url: 

`https://tudominio/wp-admin o https://tudominio/wordpress/wp-admin o https://tudominio/wp/wp-admin`

Sus principales carpetas y archivos importantes:
```
* wp-admin: Carpeta donde se guardan los archivos del back-end de WordPress, esta parte de la instalación nunca se modifica.

* wp-content: Es la carpeta donde se guarda todo el contenido en formato de archivos (no base de datos)

* wp-includes: Es una carpeta de archivos que necesita WordPress para funcionar, su API y las librerías principales se encuentran en esta carpeta que tampoco se modifica nunca.

* index.php: es el archivo principal al que se accede y desde donde se cargan el resto de partes de WordPress.

* wp-config-sample.php: Este archivo es la plantilla de lo que finalmente será el archivo WP-CONFIG.PHP tras la instalación del CMS

* xmlrpc.php: Se trata de un archivo que ofrece la comunicación mediante el protocolo XMLRPC.PHP, actualmente WordPress recibe muchos ataques a través de este archivo, por lo que es importante hacer hincapié en su seguridad y su protección.

* wp-login.php:  Es un archivo bastante importante, ya que es el que se encarga de gestionar el login de los usuarios, tanto usuarios normales como administradores. 
```

Ahora, con eso en mente ya nos damos una idea de como encontrar paginas creadas en wordpress mediante dorking:

sabemos la como se comporta wordpress para crear sus url, para encontrar paginas podemos usar lo siguiente:

`inurl:/wordpress/wp-content`
`inurl:/wordpress/wp-admin`
`inurl:/wordpress/wp-includes`

aqui estamos buscando directamente una carpeta del directorio de wordpress mediante inurl, lo que nos mostrará muchas paginas en donde accederemos(si contamos con el permiso) directamente a los archivos de wordpress.

## Ejemplos de dorks

En esta parte utilizaré como complemento un hilo de mi propia cuenta de twitter en donde he publicado muchos dorks que me parecen interesantes y vamos a analizar algunos de ellos aqui:

El primero que vamos a utilizar será:

inurl:wp-config.php intext:DB_PASSWORD -stackoverflow -wpbeginner -foro -forum -topic -blog -about -docs -articles

`https://twitter.com/_Y000_/status/1205400779957440512?s=20`

Este dork nos permite encontrar paginas creadas en wordpress y estamos buscando especificamente el archivo wp-config.php, despues utilizamos intext:DB_PASSWORD para filtrar los resultado en donde se encuentre esa palabra, que es para encontrar configuraciones de la base de datos, encontramos informacion como: usuarios, contraseña, nombre de la base de datos... etc, informacion muy importante que no deberia ser visible para cuarquier persona, por ultimo tenemos parabras con un "-" eso significa que estamos excluyendo esas palabras de nuetra busqueda.


Otro dork muy interesante es el siguente:

intitle:"Index Of" intext:"iCloud Photos" OR intext:"My Photo Stream" OR intext:"Camera Roll"

`https://twitter.com/_Y000_/status/1205647749372203010?s=20`

En este ejemplo usamos intitle:"index of" que es para encontrar directorios dentro de la pagina web, eso quiere decir que estamos buscando paginas que contengan un listado de directorios en su interior, normalmente estos no son visibles, despues estamos filtrando los resultados entre varios intext y OR lo que significa que estamos buscando cualquiera de esas 3 frases.

En este caso estamos buscando dispositivos iCloud vulnerables, con lo cual podemos ver todas las fotos que esten compartiendo. este dork puede ser modificado para encontrar diferentes cosas.

Pero no solo hacemos uso de los dorks para encontrar carpetas u archovos, tambien podemos encontrar servidores corriendo algun servicio: 

intitle:"Welcome to JBoss"
inurl:"8080/jmx-console"

```
https://twitter.com/_Y000_/status/1232415430876090368?s=20
https://twitter.com/_Y000_/status/1220447109842984963?s=20
```
Con esos dorks podemos encontrar servidores ejecutando el sistema de Jboss. 

## Dorks para inyeccion sql y xss

El Dorking es muy relacionado con las inyecciones sql y xss, ya que muchos "hackers" hacen uso de dorks para encontrar paginas vulnerables. si quieren profundizar un poco mas en las inyecciones sql les recomiendo que pasen por este escrito que tambien creé y se enfoca en eso: 

https://github.com/Y000o/sql_injection_basic/blob/master/sql_injection_basic.md

En este escrito trato de explicar de una forma muy detallada las bases para una inyeccion sql ya sea manualmente o automatica haciendo uso de herramientas.

volviendo al tema, haciendo uso de algunos dorks se facilita la busqueda para encontrar paginas vulnerables a inyecciones sql y xss, algunos son: 

```
specials.cfm?id=
store_listing.cfm?id=
store.cfm?id=
store_bycat.cfm?id=
storefront.cfm?id=
Store_ViewProducts.cfm?Cat=
store-details.cfm?id=
StoreRedirect.cfm?ID=
storefronts.cfm?title=
storeitem.cfm?item=
subcategories.cfm?id=
tuangou.cfm?bookid=
 
tek9.cfm?
template.cfm?Action=Item&pid=
topic.cfm?ID=
type.cfm?iType=
view_cart.cfm?title=
 
updatebasket.cfm?bookid=
updates.cfm?ID=
view.cfm?cid=
view_detail.cfm?ID=
viewitem.cfm?recor=
 
viewcart.cfm?CartId=
viewCart.cfm?userID=
viewCat_h.cfm?idCategory=
viewevent.cfm?EventID=
WsAncillary.cfm?ID=
 
viewPrd.cfm?idcategory=
ViewProduct.cfm?misc=
voteList.cfm?item_ID=
whatsnew.cfm?idCategory=
WsPages.cfm?ID=HP
inurl:".php?cid="+intext:"online+betting"
 
inurl:".php?cat="+intext:"Paypal"+site:UK
inurl:".php?cat="+intext:"/Buy Now/"+site:.net
inurl:".php?id=" intext:"View cart"
inurl:".php?id=" intext:"/store/"
 
inurl:".php?id=" intext:"Buy Now"
inurl:".php?id=" intext:"add to cart"
inurl:".php?id=" intext:"shopping"
inurl:".php?id=" intext:"boutique"
inurl:".php?cid=" intext:"Buy Now"
 
inurl:".php?id=" intext:"/shop/"
inurl:".php?id=" intext:"toys"
inurl:".php?cid="
inurl:".php?cid=" intext:"shopping"
inurl:".php?cid=" intext:"add to cart"
inurl:".php?cat="
 
inurl:".php?cid=" intext:"View cart"
inurl:".php?cid=" intext:"boutique"
inurl:".php?cid=" intext:"/store/"
inurl:".php?cid=" intext:"/shop/"
inurl:".php?cid=" intext:"Toys"
inurl:".php?cat=" intext:"/store/"

```
## Dorks para encontrar camaras

Tambien podemos encontrar camaras en las cuales podemos entrar

```
inurl:/sample/LvAppl/lvappl.htm
allinurl:control/multiview
intitle:”Live View / – AXIS"
```

## OSINT y DORKS

Haciendo uso de Dorks tambien podemos enfocarnos en OSINT que es un conjunto de técnicas y herramientas para recopilar información pública.

para buscar nombres: 
```
“nombre” site:página web

“nombre” site:http://instagram.com

```

usernames:

```
inurl:username site:página

allinurl:username site:página
```

Buscar informacion de una pagina web, obtener paginas relacionadas a ella y todos sus subdominios:

```
Búsquedas en una página web:
site:http://example.com

Páginas parecidas:
related:http://example.com 

Subdominios:
site:*.example.com -www
```

Correos electronicos: 

```
Estos nos ayudarán a recolectar correos electrónicos de diferentes páginas web:

“
@example
.com” site: página

HR “email” site: página filetype:csv | filetype:xls | filetype:xlsx

site:http://example.com intext:
@gmail
.com filetype:xls

```

un extra por @pedr4uz:

`https://twitter.com/pedr4uz?s=20`

```
"person_name" intext:cpf AND filetype:pdf

derivado -> "person_name" intitle:aprovado + intext:cpf AND filetype:X
```
# Importancia final

Como pudimos apreciar en este escrito, conocer bien el Dorking nos abre un mundo de posibilidades, un mundo en donde se nos hace mas facil encontrar informacion que cualquier otra persona no encotraría con facilidad, al nosotros entender bien este uso de las busquedas especializadas tenemos mucho poder, por eso es bueno y me gustaría dejarlo muy claro, mucha de la informacion que podemos encontrar puede ser que este protegida y por ende nos podemos meter en problemas si accedemos sin permiso. Todo lo aprendido en este articulo es meramente con fines educativos, cualquier uso que quieran darle es desicion de cada uno.
