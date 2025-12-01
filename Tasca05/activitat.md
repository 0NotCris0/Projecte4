# T05: Accés Remot – Connexió via SSH  
Documentació millorada

## 1. Creació de les màquines virtuals  
Creem dues màquines virtuals:  
- **Windows**  
- **Ubuntu Linux**

La primera interfície serà **NAT** i la segona **Host-Only**.

![](1.png)

---

## 2. Instal·lació i configuració d’SSH a Linux  

### Instal·lar el servei SSH  
```bash
sudo apt install ssh
```

![](2.png)

### Comprovació de la IP  
```bash
ip addr show
```

![](3.png)

### Verificar que SSH està actiu  
```bash
sudo systemctl status ssh
```

![](4.png)

---

## 3. Connexió des de Windows  
A Windows revisem la configuració de xarxa per assegurar que s’ha assignat correctament la IP.

![](5.png)

Després ens connectem a Ubuntu des del terminal de Windows:  
```bash
ssh usuari@ip_del_servidor
```

Acceptem amb `yes`.

![](6.png)

---

## 4. Configuració d’SSH al servidor Ubuntu  

### Editar el fitxer sshd_config  
```bash
sudo nano /etc/ssh/sshd_config
```

![](7.png)

### Deshabilitar accés root per SSH  
Afegim:  
```
PermitRootLogin no
```

Assignem contrasenya al root:  
```bash
sudo passwd root
```

Intentem entrar per SSH com a root i veiem que es denega.

![](8.png)

Localment sí que podem entrar com a root.

---

## 5. Permetre només usuaris autoritzats  
Creem un nou usuari:  
```bash
sudo adduser usuari2
sudo passwd usuari2
```

![](9.png)

Afegim al fitxer `sshd_config`:  
```
AllowUsers usuari
```

Reiniciem SSH:  
```bash
sudo systemctl restart ssh
```

Ara:  
- **usuari** → pot entrar  
- **usuari2** → NO pot entrar

![](10.png)

---

## 6. Autenticació per clau pública  
Al client (Windows PowerShell):  
```powershell
ssh-keygen -t rsa
```

![](11.png)

Mostrem el contingut de la clau pública:  
```powershell
cat ~/.ssh/id_rsa.pub
```

![](12.png)

Copiem la clau al servidor:  
```powershell
scp ~/.ssh/id_rsa.pub usuari@192.168.56.102:
```

![](13.png)

Al servidor:  
```bash
cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
```

![](14.png)

Ara ja podem accedir **sense contrasenya**.

---

## 7. Instal·lació i configuració d’OpenSSH a Windows  

Instal·lar OpenSSH:  
```powershell
Add-WindowsCapability -Online -Name OpenSSH.Server
```

![](15.png)

Iniciar el servei:  
```powershell
Start-Service sshd
```

Configurar inici automàtic:  
```powershell
Set-Service -Name sshd -StartupType Automatic
```

![](16.png)

Comprovem connexió des de Linux a Windows via SSH.

---

## 8. Túnel SSH  

Instal·lem **Wireshark**.

![](17.png)

Configurem un **proxy SOCKS5** a Windows:  
- IP: `127.0.0.1`  
- Port: `9876`

![](18.png)

Executem túnel:  
```bash
ssh -D 9876 usuari@10.0.2.15
```

![](19.png)

Desactivem el firewall temporalment.

Abans del túnel:  
![](20.png)

Després del túnel, el tràfic passa pel túnel SSH (visible a Wireshark).

![](21.png)

---

Fi del document.
