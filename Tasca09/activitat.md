# Servidor NFS

El primer que farem seran crear dos maquines virtuals, una sera el server NFS que sera un ubuntu i per ultim el client que sera un Zorin OS.

img 1
img 2


## Preparacio servidor 

Primer entrarem al servidor i actualizarem tot amb apt update && apt upgrade, i crearem dos grups que sera Devs i Admins. 

img 3
img 4

Lo seguent sera crear un usuari que es digui devs01 i que sigui membre del grup devs i un altre usuari que sera admin01 i del grup admins. 

img 5

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

