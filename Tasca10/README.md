# Introducció

Molt bé, equip.

A la nostra consultora, **EverPia**, busquem constantment optimitzar els recursos dels nostres clients per reduir costos i simplificar la gestió. Un dels punts més problemàtics en qualsevol oficina és la **gestió d'impressores**: drivers incompatibles, costos de tòner sense control, usuaris imprimint en impressores equivocades… el caos habitual.

La solució professional és implementar un **Servidor d’Impressió Centralitzat**.

El nostre client, **DevOptimize Solutions**, ens ha sol·licitat una proposta per centralitzar la impressió a tots els seus departaments, que treballen amb una combinació de:

- Clients **Linux Zorin OS**
- Servidors **Ubuntu Server**

---

# La Vostra Missió: Prova de Concepte (PoC)

Abans d’invertir en impressores de xarxa professionals, el client vol veure una **Prova de Concepte** que demostri:

- Que un servidor Linux pot gestionar una impressora.
- Que pot compartir-la amb clients Zorin OS.
- Que els clients poden imprimir de manera centralitzada i transparent.

Per evitar adquirir hardware, utilitzarem la impressora virtual **`cups-pdf`**, que:
- funciona com una impressora real,
- però en lloc de paper, genera fitxers PDF,
- i els desa directament al servidor.

L’objectiu és demostrar que un client pot enviar una feina d’impressió al servidor i que aquesta queda registrada com a PDF.

---

# Escenari de Treball

Utilitzarem **el mateix entorn** que la PoC de NFS:

### 🖥️ Màquina 1 — *Servidor*
- **Ubuntu Server**
- Xarxa:  
  - 1 adaptador en **NAT**  
  - 1 adaptador en **Host-Only**

### 💻 Màquina 2 — *Client*
- **Zorin OS (Desktop)**
- Mateixa configuració de xarxa que el servidor.

---

# PoC (Prova de Concepte)

A continuació tens les fases que haureu de completar i documentar:

---

## **1. Instal·lació de CUPS al servidor**
Inclou la instal·lació del servei d’impressió per defecte a Linux.

---

## **2. Instal·lar la impressora virtual `cups-pdf`**
Serveix per generar un PDF per cada feina d’impressió enviada.

---

## **3. Configuració de l’administració de CUPS**
- Permetre l’accés a la interfície d’administració.
- Fer que CUPS escolti per totes les interfícies.
- Modificar el fitxer de configuració quan sigui necessari.

---

## **4. Compartir la impressora via el frontal web de CUPS**
Usant el navegador:  
**http://IP_DEL_SERVIDOR:631**

---

## **5. Afegir la impressora al client Zorin OS**
Des del panell d’impressió del sistema.

---

## **6. Realitzar proves d’impressió**
Enviar diversos documents i verificar que arriben al servidor.

---

## **7. Comprovació de resultats al servidor**
Verificar que s’han generat correctament els arxius PDF que representen les feines d’impressió.

Els PDF generats normalment es troben a:  
`/var/spool/cups-pdf/<usuari>/`

---

# Documentació Final

Heu de documentar:

- **Totes les comandes utilitzades** (seguint el format del document PDF explicat a classe).
- **Captures de pantalla**:  
  - Web de CUPS  
  - Impressora instal·lada  
  - Impressió enviada  
  - PDF generat al servidor  
- **Notes importants** sobre configuració i resolució d’errors.

Aquesta documentació formarà part del material de formació d’EverPia per als futurs tècnics.

---

Si vols, puc generar també:

✅ la plantilla de documentació  
✅ totes les comandes corresponents  
✅ un checklist final de validació  

- [Tornar pagina principal](../README.md)
- [Anar a la activitat](activitats.md)
