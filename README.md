# Joomla Check List
Coses a tenir en compte en un Joomla per entregar al client final

## Configuració
En l'apartat de configuració és important tenir en compte el següent:

* Email del sistema canviar per el del client
* Paths de logs i tmp modificar pels del servidor final d'allotjament
* Urls amigables i activar mod_rewrite amb htaccess
* Error reporting "None"
* Activar la compressió de pàgines amb Gzip
* Gestió de sessions amb PHP en comptes de la base de dades

## Extensions
Algunes extensions necessaries en qualsevol instal·lació:

* Email as username (properament inclós en el JPFramework)
* Secure Login
* Activar plugin redirect per recolectar links trencats 404 i poder donar-los una solució

## Comproprovar resolucions
* http://whatismyscreenresolution.net/multi-screen-test
* Acordar llista de resolucions standard

## SSL
Si tenim el com_botiga i fem servir redsys a la configuració global ha de desactivar-se el ssl i al htaccess afegir aquestes linies al final:

~~~
##configuració especifica per redsys sota ssl
RewriteEngine On
RewriteCond %{HTTPS} !=on
RewriteCond %{QUERY_STRING} !(^|&)view=callback(&|$)
RewriteRule ^ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]

#La url del reset password falla en aquestes condicions la modifiquem
RewriteEngine On
RewriteCond %{HTTPS} !=on
#RewriteCond %{QUERY_STRING} !(^|&)layout=confirm&token=(.+?)$
#RewriteRule ^ https://%{HTTP_HOST}%password-reset{REQUEST_URI}  [L,R=301]
~~~
