# T06: Accés remot. Escriptori remot (RDP)

El primer que farem serà crear dues màquines virtuals: una amb Windows i l’altra amb Linux Zorin OS. La primera interfície de xarxa serà la que ve per defecte, NAT, i la segona serà host-only. Per configurar-la en host-only, haurem d’anar a la configuració de xarxa de les màquines virtuals, habilitar una segona interfície i seleccionar l’opció “només amfitrió”.

![](img/1.png)

El següent pas serà entrar a la màquina de Windows i buscar l’opció de Configuració de l’Escriptori Remot.

![](img/2.png)

I haurem d’activar l’opció d’Escriptori Remot.

![](img/3.png)

Ara ja ens podrem connectar i passarem a la màquina Linux.

Haurem de configurar la màquina Linux, el Zorin OS, per així poder connectar-nos remotament a la de Windows.

Anirem a Configuració i després a Sharing, on haurem d’activar l’opció superior.

![](img/4.png)

Després anirem a Remote Desktop i activarem les opcions de Remote Desktop i Remote Control per poder controlar la màquina remotament.

Per a la contrasenya, farem servir el mateix usuari i contrasenya.

![](img/5.png)

Ara connectarem la màquina de Windows a la de Zorin OS de manera remota, i ho farem amb la Connexió a l’Escriptori Remot.

![](img/6.png)

Posarem la IP de l’equip Zorin OS, que serà aquesta:

```bash
ip a
``` 

![](img/7.png)

![](img/8.png)

Posarem el nom d’usuari i la contrasenya, que seran usuari-usuari, tal com hem dit abans.

![](img/9.png)

Ens sortirà una advertència i li direm que sí.

![](img/10.png)

I podem veure que ja estem a la màquina Zorin de manera remota.

![](img/11.png)

Ara el següent pas serà connectar-nos des de Zorin a Windows de manera remota.

Buscarem Remmina, que ve per defecte a Zorin OS, i que serà l’aplicació que ens facilitarà tot el procés.

![](img/12.png)

Mirarem la IP de la màquina Windows amb ipconfig, i serà aquesta:

![](img/13.png)

Posarem la IP en Remmina.

![](img/14.png)

Ens sortirà una advertència i li posarem que sí (Yes).

![](img/15.png)

Ens demana el nom d’usuari i la contrasenya, i els posem com abans.

![](img/16.png)

I ja podem veure la màquina Windows des de Zorin.

![](img/17.png)

- [Tornar al enunciat](README.md)