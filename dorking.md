# GOOGLE HACKING / DORKING 

* [¿Qué es el dorking?](#¿Qué-es-el-dorking?)
* [Importancia](#Importancia)
* [Conceptos básicos](#Conceptos-básicos)
* [¿Cómo usar esto en el "hacking"?](#¿Cómo-usar-esto-en-el-"hacking"?)
* [Ejemplos de dorks](#Ejemplos-de-dorks)
* [Dorks para inyeccion SQL y XSS](#Dorks-para-inyeccion-SQL-y-XSS)
* [Dorks para encontrar cámaras](#Dorks-para-encontrar-cámaras)
* [OSINT y DORKS](#OSINT-y-DORKS)
* [Importancia final](#Importancia-final)


## ¿Qué es el dorking?

El Google hacking o Dorking es un modo de buscar cosas un poco más especializada.
Por el nombre "Google Hacking" se puede dar la impresión de que solo se usa en Google, pero eso no es correcto.
El dorking no es más que una búsqueda avanzada en donde hacemos uso de operadores que funcionan como un filtro
para dirigir la búsqueda directamente a donde nosotros queremos, usando símbolos para buscar palabras o frases exactas, por ejemplo.
Esto nos servirá para buscar en casi cualquier motor de búsqueda que encontremos en Internet.

## Importancia

El saber un poco de dorking nos ayuda en muchos aspectos de nuestra vida, no es solo para buscar páginas vulnerables.
Recordemos que el término "hacking" primeramente se utiliza cuando una persona domina una cosa a tal grado
que puede ver las cosas desde otros puntos de vista y así llegar a ver o alcanzar objetivos que otras personas no pueden.

Si salimos un poco de la informatica podemos ver un ejemplo: Un mecánico que tiene años trabajando con carros y se especializa en motores, el que con el tiempo ya entiende 
mucho mejor los problemas de un motor que cualquier otro mecánico, al tener mucha más experiencia en el tema,
se puede decir que el es un "hacker" en mecánica por llegar a saber eso.

Volviendo al tema de dorking, es muy importante que todas las personas sepan un poco de esto. En este escrito se tratará de 
explicar lo más detalladamente posible cómo comenzar y si ya sabes algo de esto puedas reforzar temas básicos.

## Conceptos básicos

Como se explicó antes, estas busquedas avanzadas usan operadores y símbolos, como los siguientes: 

Vamos a empezar con algunos operadores muy comunes:

* site: solo busca resultados dentro de la web que va detrás de “site:”.

      Ejemplo: site:www.google.com 
      Esta busqueda solo nos mostrará resultados de la página de Google.
      
* intitle o allintitle: Esto solo buscará en los títulos. 
      
      Ejemplo: intitle:"Google dorking"
      Esta búsqueda nos mostrará solo artículos que tengan la frase "google dorking" en su título.
      
* inurl o allinurl: los resultados estarán en la url de las páginas. 

      Ejemplo: inurl: /parametro.php?id=
      Esta búsqueda nos mostrará resultados de páginas en donde contengan "/parametro.php?id=" en su url.
      
      Nota: Éste se puede confundir un poco al inicio con el operador "site" porque si no expresamos bien
      lo que queremos encontrar y ponemos un sitio web, nos mostrará el mismo resultado.
      
      Recordemos que un link o url tiene la siguiente sintáxis dependiendo si el administrador de la página
      configuró o no los links para que sean más amigables.
      
      Sitio con links no amigables:
      `http/s://www.sitiowebdeejemplo.com/parametro1.php?id=1&parametro2.php?id=22`
      
      Sitio con links amigables:
      `http/s://www.sitiowebdeejemplo.com/ejemplo`
      
* filetype o ext: solo busca archivos (doc, xls, txt…). 
        
      Nota: Este operador va acompañado con alguno de los que acabamos de ver.
      Ejemplo: site:www.paginaweb.com filetype:.pdf
      Esta busqueda nos mostrará los archivos .pdf que esten "sueltos" o que estén filtrados en la red desde la página www.paginaweb.com. 
      
* related: busca webs relacionadas con una determinada.
        
      Ejemplo: relates: www.google.com 
      Nos mostrará páginas parecidas a Google, es decir, nos mostrará otros motores de búsqueda.
      
* cache: muestra el resultado en la caché de Google de una página web.
      
      Ejemplo: cache:www.google.com
      Nos mostrará la pagina web guardada en el caché de Google.
      
* define: busca definiciones de palablas

      Ejemplo: define:linux
      Nos mostrará resultados en donde se defina qué es Linux.
      
* Allintext o intext: nos buscará la frase exacta que pongamos.

      Ejemplo: Allintext:abcdefghijklmnopqrstuvwxyz
      Nos mostrará paginas en donde venga el abecedario. 
     
* weather: nos mostrará el clima de la parte del mundo que queramos ver. 

      Ejemplo: weather:México
      Nos mostrará el clima de la ciudad de México. 
      
* stock: nos mostrará información financiera. 

      Ejemplo: ````
               stock:TSLA
               stock:goog
               ```
      Esto nos mostrará la informacion financiera de la bolsa de valores. 
      
* link: nos muestra las páginas en donde está enlazada la web que buscamos. 

      Ejemplo: link:www.youtube.com
      Nos mostrará todas las páginas que enlazan algún link de Youtube en su contenido. 
      
Ahora vamos a ver algunos símbolos muy importantes:

* ” ” (comillas): buscar frase exacta.
       
      Ejemplo: "alert(Y000!)"
      En este caso estoy buscando mi propio apodo o mi nick de Twitter. 
      
* `+ y -` : incluir o excluir alguna palabra

      ejemplo: animales -perros
      Esto nos da como resultado muchas páginas que hablan de animales pero intenta excluir todos los resultados en donde se hable de perros.
      
* `*` (asterisco): comodín, cualquier palabra, pero una sola palabra.
      
      Ejemplo: site:*.google.com
      Lo cual nos mostrará todas las páginas de Google incluyendo sus subdominios.
      
      
## ¿Cómo usar esto en el "hacking"?      

Primero que nada, tenemos que tener muy en claro lo que queremos lograr, lo que vamos a buscar y lo que queremos encontrar.

Para poder empezar en el Google hacking ya viendo desde una perspectiva en donde queremos encontrar "información" que no todos pueden encontrar, tenemos que conocer
archivos que contengan esa informacion, tenemos que conocer los sistemas en los cuales se basa una página web, tenemos que estar enterados de todo un poco. 

El primer ejemplo que vamos a ver es el de cómo buscar el archivo "robots.txt", pero primero para buscar ese archivo tenemos que saber: ¿Qué es?, ¿qué contiene?,
¿Por qué las páginas lo usan?, no podemos buscar algo solo por buscarlo sin saber qué es.

El archivo "robots.txt" es para facilitar la indexación de un sitio web.  Este archivo sirve para dar instrucciones a los robots sobre qué contenidos deben rastrear y cuáles no y cómo deberían hacerlo. En palabras más fáciles, ese archivo sirve para que la página web esté "segura" de las búsquedas de Google, ya que en el archivo vienen las páginas que el administrador no quiere que se vean en los resultados de Google, vamos, que es como excluir las páginas para no ser encontradas.

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

Con lo cual tenemos muchas maneras de cómo encontrarlo, por ejemplo: sabemos en qué parte del link está, sabemos qué se usa en la URL, por lo que podemos hacer una búsqueda como la siguiente:

`inurl:robots.txt` pero esto nos mostrará resultados muy generales y puede ser que encuentre el archivo o algo relacionado a él.

Aquí es cuando vamos a usar de verdad los operadores, los vamos a mezclar para obtener mejores resultados:

Usando el operador "site" + "inurl" y el simbolo `*` hacemos la búsqueda mucho más específica:

`site:www.google.com inurl:robots.txt` ya con esto enfocamos que la búsqueda es en la página de Google y listo!! nos da como resultado: https://www.google.com/robots.txt

Pero si queremos hacer mucho más específica la búsqueda podemos usar:

`site:*.com.mx inurl:/robots.txt intext:"User-agent:"`

En este caso estamos reduciendo los resultados a solo páginas que tengan el dominio .com junto con .mx ".com.mx" lo que quiere decir que estamos buscando páginas
méxicanas, ya que el dominio .mx pertenece a sitios alojados en México. Al encontrar esas páginas se aplica el operador inurl:/robots.txt que reduce aún más 
a las página que solo contengan la palabla "robots.txt" en su url. Por último entra intext:"User-agent:" a reducir nuevamente los resultado anteriores 
y verificando que las páginas encontradas antes tengan la palabra "user-agent:" en ellas. Ahora sí podemos asegurar que las páginas que encontramos nos mostrarán el
archivo robots.txt de cada sitio.

Ese es solo un ejemplo de cómo utilizar los operadores para encontrar cosas interesantes.

Por otra parte también podemos enfocarnos en buscar páginas que estén hechas en algun CMS en específico, por ejemplo WordPress. Éste se ha caracterizado por ser muy cómodo para trabajar en él y bastante fácil ya que contiene muchos plugins que nos pueden ser de mucha ayuda, pero al mismo tiempo estos complementos pueden venir con muchos fallos que permiten a otra persona explotar vulnerabilidades. 

Para encontrar páginas creadas en WordPress primero tenemos que conocer un poco de él, su estructura básica de archivos y carpetas, los archivos más importantes, etc.
Aquí voy a tratar de explicar un poco para entender mejor por qué es importante conocer eso:

WordPress utiliza la siguiente estructura en su URL: 

`https://tudominio/wp-admin o https://tudominio/wordpress/wp-admin o https://tudominio/wp/wp-admin`

Sus principales carpetas y archivos importantes:
```
* wp-admin: Carpeta donde se guardan los archivos del back-end de WordPress, esta parte de la instalación nunca se modifica.

* wp-content: Es la carpeta donde se guarda todo el contenido en formato de archivos (no base de datos).

* wp-includes: Es una carpeta de archivos que necesita WordPress para funcionar, su API y las librerías principales se encuentran en esta carpeta que tampoco se modifica nunca.

* index.php: es el archivo principal al que se accede y desde donde se cargan el resto de partes de WordPress.

* wp-config-sample.php: Este archivo es la plantilla de lo que finalmente será el archivo wp-config.php tras la instalación del CMS.

* xmlrpc.php: Se trata de un archivo que ofrece la comunicación mediante el protocolo XML-RPC, actualmente WordPress recibe muchos ataques a través de este archivo, por lo que es importante hacer hincapié en su seguridad y su protección.

* wp-login.php:  Es un archivo bastante importante, ya que es el que se encarga de gestionar el login de los usuarios, tanto usuarios normales como administradores. 
```

Ahora, con eso en mente ya nos damos una idea de como encontrar páginas creadas en WordPress mediante dorking:

Sabemos ya cómo se comporta WordPress para crear sus URL, por lo que para encontrar páginas podemos usar lo siguiente:

`inurl:/wordpress/wp-content`
`inurl:/wordpress/wp-admin`
`inurl:/wordpress/wp-includes`

Aquí estamos buscando directamente una carpeta del directorio de WordPress mediante inurl, lo que nos mostrará muchas páginas en donde accederemos (si contamos con el permiso) directamente a los archivos del CMS.

## Ejemplos de dorks

En esta parte utilizaré como complemento un hilo de mi propia cuenta de Twitter en donde he publicado muchos dorks que me parecen interesantes y vamos a analizar algunos de ellos aquí:

El primero que vamos a utilizar será:

inurl:wp-config.php intext:DB_PASSWORD -stackoverflow -wpbeginner -foro -forum -topic -blog -about -docs -articles

`https://twitter.com/_Y000_/status/1205400779957440512?s=20`

Este dork nos permite encontrar páginas creadas en WordPress y estamos buscando especificamente el archivo wp-config.php. Después utilizamos intext:DB_PASSWORD para filtrar los resultado en donde se encuentre esa palabra, que es para encontrar configuraciones de la base de datos, encontramos informacion como: usuarios, contraseña, nombre de la base de datos, etc. la que es informacion muy importante que no debería ser visible para cuarquier persona. Por último tenemos palabras con un "-" lo que significa que estamos excluyendo esas palabras de nuestra búsqueda.

Otro dork muy interesante es el siguente:

intitle:"Index Of" intext:"iCloud Photos" OR intext:"My Photo Stream" OR intext:"Camera Roll"

`https://twitter.com/_Y000_/status/1205647749372203010?s=20`

En este ejemplo usamos intitle:"index of" que es para encontrar directorios dentro de la página web, eso quiere decir que estamos buscando páginas que contengan un listado de directorios en su interior. Normalmente estos no son visibles, después estamos filtrando los resultados entre varios intext y OR lo que significa que estamos buscando cualquiera de esas 3 frases.

En este caso estamos buscando dispositivos iCloud vulnerables, con lo cual podemos ver todas las fotos que esten compartiendo. este dork puede ser modificado para encontrar diferentes cosas.

Pero no solo hacemos uso de los dorks para encontrar carpetas u archivos, tambien podemos encontrar servidores corriendo algun servicio: 

intitle:"Welcome to JBoss"
inurl:"8080/jmx-console"

```
https://twitter.com/_Y000_/status/1232415430876090368?s=20
https://twitter.com/_Y000_/status/1220447109842984963?s=20
```
Con esos dorks podemos encontrar servidores ejecutando el sistema de Jboss. 

## Dorks para inyeccion SQL y XSS

El dorking está muy relacionado con las inyecciones SQL y XSS, ya que muchos "hackers" hacen uso de dorks para encontrar páginas vulnerables. Si quieren profundizar un poco más en las inyecciones SQL les recomiendo que pasen por este escrito que también creé y se enfoca en eso: 

https://github.com/Y000o/sql_injection_basic/blob/master/sql_injection_basic.md

En este escrito trato de explicar de una forma muy detallada las bases para una inyeccion SQL ya sea manualmente o automática haciendo uso de herramientas.

Volviendo al tema, haciendo uso de algunos dorks se facilita la búsqueda para encontrar páginas vulnerables a inyecciones SQL y XSS, como por ejemplo: 

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
## Dorks para encontrar cámaras

Tambien podemos encontrar cámaras en las cuales podemos entrar

```
inurl:/sample/LvAppl/lvappl.htm
allinurl:control/multiview
intitle:”Live View / – AXIS"
```

## OSINT y DORKS

Haciendo uso de dorks también podemos enfocarnos en OSINT que es un conjunto de técnicas y herramientas para recopilar información pública.

Para buscar nombres: 
```
“nombre” site:página web

“nombre” site:http://instagram.com

```

Usernames:

```
inurl:username site:página

allinurl:username site:página
```

Buscar informacion de una página web, obtener sitios relacionados a ella y todos sus subdominios:

```
Búsquedas en una página web:
site:http://example.com

Páginas parecidas:
related:http://example.com 

Subdominios:
site:*.example.com -www
```

Correos electrónicos: 

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

Un extra por @pedr4uz:

`https://twitter.com/pedr4uz?s=20`

```
"person_name" intext:cpf AND filetype:pdf

derivado -> "person_name" intitle:aprovado + intext:cpf AND filetype:X
```
# Importancia final

Como pudimos apreciar en este escrito, conocer bien el dorking nos abre un mundo de posibilidades, un mundo en donde se nos hace más fácil encontrar información que cualquier otra persona no encontraría con facilidad. Al nosotros entender bien este uso de las búsquedas especializadas tenemos mucho poder, por eso es bueno y me gustaría dejarlo muy claro, mucha de la informacion que podemos encontrar puede ser que esté protegida y por ende nos podemos meter en problemas si accedemos sin permiso. Todo lo aprendido en este artículo es meramente con fines educativos, cualquier uso que quieran darle es decisión de cada uno.
