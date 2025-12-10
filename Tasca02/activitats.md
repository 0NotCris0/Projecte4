# T02: DPR: còpies de seguretat. Cas pràctic

El primer que farem serà crear dues màquines virtuals, la de Windows i una altra d’Ubuntu, i les configurarem amb aquestes especificacions. En la de Windows crearem dos discs: el del sistema en general i el segon per fer les còpies de seguretat, que serà de 10GB.

![](img/2.png)

## Part 1: Còpia de seguretat dels equips clients Windows

Començarem amb la de Windows, que és la primera que ens demana.

El primer que farem serà anar a Administració de discs, per poder habilitar el segon disc que hem creat, i li donarem a inicialitzar disc.

![](img/3.png)

Posarem tot el disc.

![](img/4.png)

Formatarem el disc amb la configuració predeterminada.

![](img/5.png)

I per últim li donarem a finalitzar i el tindrem habilitat.

![](img/6.png)

![](img/7.png)

Ara el següent pas serà instal·lar Duplicati, que anirem a la seva pàgina web i li donarem a descarregar per a Windows.

![](img/8.png)

En haver finalitzat li donarem a executar.

![](img/9.png)

I ens sortirà això, li haurem de donar a Next.

![](img/10.png)

Acceptarem tot, ho deixarem predeterminat i li donarem a Next.

![](img/11.png)

![](img/12.png)

![](img/13.png)

I li donarem a Finish.

![](img/14.png)

Inicialitzarem i haurem de posar una contrasenya que serà "usuari".

![](img/15.png)

![](img/16.png)

### Creació de backup en el propi equip

Ja comencem creant el backup i li donarem a Add backup.

![](img/17.png)

Després Add new backup.

![](img/18.png)

Ara haurem de posar la configuració general, com el nom, descripció i contrasenya, i li donarem a Continuar.

![](img/19.png)

Haurem d’escollir on volem fer el backup, que serà en el segon disc perquè es guardi allà, i farem Continue. També escollim que farem de My Documents de l’equip.

![](img/20.png)

![](img/53.png)

Escollirem cada quant volem que es faci, que en aquest cas serà cada 1 hora tots els dies.

![](img/21.png)

Aquí deixarem com està predeterminat.

![](img/22.png)

I podrem veure que ja està creat correctament, però ara falta comprovar.

![](img/23.png)

### Comprovació de backup en el propi equip

Crearem una carpeta i podrem posar també unes fotos, en l’apartat de Documents.

![](img/24.png)

Les esborrem totes.

![](img/25.png)

Entrarem una altra vegada en l’aplicació i li donarem a Start.

![](img/26.png)

Veurem el backup que hem fet i li donarem a Restore.

![](img/27.png)

Seleccionarem el que volem recuperar, que serà tot.

![](img/28.png)

I podrem decidir on els recuperarem, però posarem el mateix lloc, que serà en Documents.

![](img/29.png)

![](img/30.png)

I podrem veure que ja ho tindrem ben fet.

![](img/52.png)

![](img/31.png)

### Creació de backup en Google Drive

Farem les mateixes passes que abans i donarem Add backup i New backup.

Després ens sortirà per posar la configuració general i li posarem un altre nom per saber diferenciar.

![](img/32.png)

Però ara en Backup destination posarem Google Drive en vegada de fitxers.

![](img/33.png)

Ens demanaran la Folder path, que posarem Documents, i l’AuthID.

![](img/37.png)

Que això ho aconseguirem automàticament.

![](img/34.png)

![](img/35.png)

![](img/36.png)

Després decidirem a què fer el backup, que serà una altra vegada a Documents.

![](img/38.png)

Posarem que voldrem fer cada dia a les 18:00 el backup.

![](img/39.png)

Deixarem la configuració predeterminada.

![](img/40.png)

I ja tindrem el backup que es guarda en el Google Drive.

![](img/41.png)

Podrem veure en el Drive que està.

![](img/42.png)

### Comprovació de backup en Google Drive

Ara com abans tindrem una carpeta i fotos.

![](img/43.png)

Esborrarem tot.

![](img/44.png)

Li donarem a Inici i a Restore.

![](img/45.png)

I escollirem la de Google Drive i li donarem a Restore.

![](img/46.png)

Una altra vegada seleccionarem el que volem recuperar, que serà tot.

![](img/47.png)

I aquí podem escollir la ruta, però deixarem l’original.

![](img/48.png)

![](img/49.png)

![](img/51.png)

I podrem veure que ja està tot una altra vegada.

![](img/50.png)


## Part 2: Còpia seguretat servidor Linux

Ara continuarem amb el servidor de linux que el configurarem amb un disc secundari de 10GB. I les seguents especificacions. 

![](img/54.png)

Entrarem en la maquina de linux i comprovarem que veu el segon disk. Amb aquesta comanda.

```bash
sudo fdisk -l
``` 

img 55 

Ara crearem una particio nova en el segon disc de 10GB.
Posarem primer N(nova particio), P(Una particio primaria), posarem el que surt per defecte i per ultim W(per guardar.)

```bash
sudo fdisk /dev/sdb
```

img 56

I ara podem veure que s'ha creat correctament. 

```bash
sudo fdisk -l
``` 
img 57

Haurem de posarle en el format XFS amb aquesta comanda.

```bash
sudo mkfs.xfs /dev/sdb1
```

img 58

Creem el punt de muntatge manualment a /media/backup. El primer sera crear la carpeta.

```bash
mkdir /media/backup
```

Lo seguent sera montar. 

```bash
mount /dev/sdb1 /media/backup
```

img 59

Ara ja podrem instalar duplicity.

```bash 
apt install duplicity
```

img 60

Despres podem comprovar que s'ha instalat correctament.

```bash
duplicity --version
``` 

Despres creem dos usuaris adicionals amb carpetas personals. Que seran user2 i user3.

```bash
useradd -m -s /bin/bash user2
useradd -m -s /bin/bash user3
```

img 61

Per comprovar que s'han creat correctament farem.

```bash
grep -E "user2|user3" /etc/passwd
``` 

img 62

Li configurarem la contrasenya amb aquesta comanda.

```bash
passwd user2
passwd user3
```

img 63

Crearem arxius buit sense proposit nomes perqu estiguin alla per poder fer la prova en el carpeta de home del usuari.

```bash 
fallocate -l 10MB archivo1
...
```

img64

El seguent pas sera fer la copia de seguretat de la carpeta /home amb la seguent comanda.

```bash 
sudo duplicity full /home/ file:///media/backup/
``` 

img 65

Despres comprovem que s'ha fet correctament en /media/backup/.

```bash
ls /media/backup
```

img 66

Ara borrarem alguns arxius per poder despres fer el backup.

```bash
rm archivo1
...
```

img 67

El seguent sera fer la restauracio de el /home de usuari ho farem amb.

```bash
duplicity restore file:///media/backup/ /home/usuari
```

img 68

Despres farem un ls i entrarem en el usuari i comprovem que ho tenim tot un altre vegada.

```bash
ls
cd usuari
ls
```

img 69

Despres el seguent pas sera crear un nou fitxer per fer un altre comprovacio.

```bash
fallocate -l 10MB archivo5
``` 

img 70 

Farem una copia nova, i com hem creat un nou arxiu el detectara i fara una copia incremental.

```bash
duplicity full /home/ file:///media/backup/
```

img 71

Ara desmontarem /media/backup.

```bash 
umount /media/backup
```

img 72

Ara crearem un script amb bin-bash que fara la copia completa de /home del usuari principal. Osigui fara tot el que hem fet pero automaticament.

img 73

Despres li donarem permisos de execusio perque sino no podrem executarlo,

```bash
chmod +x fullbackup.sh
```

img 74

I modifiquem el cron perquè s’executi els diumenges a les 23:00. I guardarem.

```bash
crontab -e
```

img 75

img 76

El seguent pas i el ultim sera crear un altre arxiu executable de bin-bash, que sigui el incremental. 

img 77

Donarem tambe els permisos amb chmod.

```bash
chmod +x incrementalbackup.sh
```

img 78

Comprovarem que hem creat els dos am ls -l.

```bash 
ls -l
``` 

img 79

Per ultim el programem a cron perquè s’executi de dilluns a dissabte a les 23:00.

img 80