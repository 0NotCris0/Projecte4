# Servidor NFS

El primer que farem seran crear dos maquines virtuals, una sera el server NFS que sera un ubuntu i per ultim el client que sera un Zorin OS.

img 1

img 2

Els dos hauren de tenir host-only i s'hauren de veure.

img 11

img 12

## Preparacio Ubuntu (Servidor) 

Primer entrarem al servidor i actualizarem tot amb apt update && apt upgrade, i crearem dos grups que sera Devs i Admins. 

img 3

img 4

Lo seguent sera crear un usuari que es digui devs01 i que sigui membre del grup devs i un altre usuari que sera admin01 i del grup admins. 

img 5

Comrpovarem que s'han cret correctament

```bash
cat /etc/group | grep -E "devs|admins"
``` 

img 19

## Creacio de directoris

Lo que farem sera crear un directori /srv/nfs/dev_projectes.  

```bash
cd /srv
mkdir nfs 
mkdir dev_projectes
```

img 6

Crearem un altre directori /srv/nfs/admin_tools. 

img 7

Ara farem que els developers tinguin control sobre el seu directori que sera amb chown. 

```bash
chown :devs dev_projectes/
``` 

img 8

Despres farem lo mateix pero amb la de admin. 

```bash
chown :admins admin_tools/
```

img 9

Ara cambiem que tinguin els permisos amd:

```bash
chmod 770 admin_tools/
chmod 770 dev_projectes/
```

img 10

## Preparació Zorin OS (Client)

Ara haurem de fer lo matexi amb el client que sera el Zorin OS.

Pero ho farem diferent i mes facil, gracies a la aplicacio users and groups que la descareguem en software. 

img 13 

img 14

Ara crearem els mateixos usuaris i groups en el client de Zorin.

Lo primer sera crear el usuari devs01 i admin01. Li donarem añadir.

Posarem el nom i el usuario.

img 15

img 17

Despres configurarem la contrasenya.

img 16

img 18

Ahora pasaremos a crear los grupos es molt important que tenen el mateix GID i UID.

Posarem gestionar grups.

img 20

Lo seguent Añadir.

img 21

Posarem el nom de devs i despres el ID 1001.

img 22

Posarem el nom admins i despres el ID 1002.

img 23

Per ultim posarem els usuari en cada grup. Anirem a configuracio de grups. Selecionarem a admins i despres devs. 

Donarem a propietats.

img 24

Posarem admins01.

img 25

Farem lo mateix amb devs.

img 26

## Instalacio i configuracio de Servidor NFS



