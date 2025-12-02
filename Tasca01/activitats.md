# Fase 1: Treball individual
De forma individual, heu de donar resposta a les següents preguntes basant-se en el cas pràctic:

## 1. Què copiar? (Priorització)
Quines són les dades més crítiques del servidor? Cal fer còpia dels 10 equips clients? Justifica-ho.

El primer que cal identificar són quines dades són realment essencials per al funcionament de l’empresa. En aquest cas, el sistema més crític és el de **Comptabilitat i Clients**, ja que s’utilitza cada dia, està en constant actualització i només podem permetre una pèrdua màxima de **4 hores** de feina. Per això, aquestes bases de dades són la màxima prioritat en el pla de còpies.

En segon lloc, trobem els **Documents de Projectes**, que inclouen plànols i documentació tècnica. Encara que no es modifiquin tan sovint com les bases de dades, formen part del treball principal de l’empresa i una pèrdua seria molt perjudicial.

Finalment, s’han de protegir les **Carpetes personals dels usuaris**, que contenen fitxers relacionats amb la feina del dia a dia. Són importants, però poden tolerar una pèrdua màxima de **24 hores**.

Pel que fa als **10 equips clients**, sí que convé incloure’ls en el sistema de còpies, però no de manera completa. No és necessari copiar tot l’ordinador, ja que el sistema operatiu i les aplicacions es poden reinstal·lar. En canvi, la carpeta *Documents*, on alguns tècnics desen fitxers importants temporalment, sí que s’ha de protegir perquè pot contenir informació rellevant.

---

## 2. Periodicitat i Tipus de Còpia
Proposa un calendari bàsic per a la setmana (Diari / Setmanal / Mensual) i quin tipus de còpia aplicaràs (Completa, Diferencial, Incremental) per a les dades crítiques.

Per garantir una recuperació ràpida i complir els requisits del cas, és necessari establir un calendari de còpies que combini diferents tipus de backup.

### Bases de dades
- **Còpies incrementals cada 4 hores**, per mantenir un punt de restauració sempre recent.
- **Còpia completa cada nit**.
- **Còpia completa cada diumenge** per tenir un punt més estable i segur.

### Documents de Projectes
- **Còpia completa setmanal**.
- **Còpies incrementals diàries** per registrar els canvis.

### Carpetes personals i Documents dels equips clients
- **Backup incremental diari**.
- **Backup complet setmanal**.

---

## 3. Mitjans i Ubicació
Quin tipus de mitjà de còpia utilitzaries (Discs durs externs, NAS, Cloud, Cintes)? On s'hauria de guardar físicament la còpia més recent? (*Regla 3-2-1*)

Per assegurar un sistema de còpies fiable i pràctic, és recomanable combinar diferents mitjans:

- **NAS intern** per a les còpies diàries, que permet restauracions ràpides en cas d’error del servidor.
- **Còpia fora de les instal·lacions (núvol)** per protegir-se d’incendis, robatoris o fallades greus. Ideal per guardar còpies setmanals o completes amb retenció d’un mes.
- **Discs durs externs** en rotació per còpies setmanals o mensuals guardades físicament en un altre lloc.

### Compliment de la regla 3-2-1
- **3 còpies** de les dades (servidor original, NAS i còpia off-site).
- **2 tipus de suports diferents** (NAS + núvol o NAS + disc extern).
- **1 còpia fora de l’empresa**.

La **còpia més recent** ha d’estar sempre al **NAS intern**, perquè permet restaurar el sistema de manera immediata davant d’un problema.

# Fase 2: Treball per parelles
Treballant per parelles:

## 1. Discussió i Consens
Comparen les seves respostes individuals (Fase 1).

## 2. Elaboració d'una Proposta Unificada
Heu de consensuar i dissenyar el vostre propi **Esquema 3-2-1 de Còpies** (3 còpies, 2 mitjans, 1 fora de lloc) basat en els requisits del cas.

---

## Proposta de la Parella

| Element | Proposta de la Parella | Justificació |
|--------|-------------------------|--------------|
| **Dades Crítiques** | Bases de dades de Comptabilitat i Clients, Documents de Projectes i Carpetes Personals | Les bases de dades tenen canvis constants i són essencials; els projectes i carpetes personals contenen informació de treball important. |
| **Periodicitat (BD)** | Incremental cada 4 hores + completa cada nit | Per complir el RPO de 4 hores i assegurar un punt de recuperació estable cada dia. |
| **Tipus de Còpia (BD)** | Completa diària + incrementals cada 4 hores | Les incrementals permeten captar tots els canvis recents i les completes asseguren un backup íntegre. |
| **Mitjà 1 (Local)** | NAS intern | Permet restaurar ràpidament i guardar les còpies més recents dins l’empresa. |
| **Mitjà 2 (Extern)** | Còpia al núvol (Cloud Backup) | Garanteix una còpia off-site en cas d’incendi, robatori o fallada física de la infraestructura local. |

# Proposta de Còpies – Muntatges i Serveis Tècnics SL (grupal)

## 1) Dades Objecte de Còpia

| Origen      | Dades                                 | Crítiques | Freqüència de còpia                                |
|------------|--------------------------------------|-----------|--------------------------------------------------|
| **Servidor** | Bases de Dades (Comptabilitat i Clients) | Sí        | Incremental cada 4 hores + Completa diària; còpia completa setmanal diumenge |
| **Servidor** | Documents de Projectes               | No        | Incremental diària + Completa setmanal          |
| **Servidor** | Carpetes Personals dels Usuaris     | No        | Incremental diària + Completa setmanal          |
| **Clients**  | Carpeta “Documents” dels equips      | Sí/No     | Incremental diària + Completa setmanal          |

**Justificació:**  
Les **bases de dades** són crítiques perquè tenen canvis constants i només poden perdre fins a 4 hores de dades. Els **Documents de Projectes** i **Carpetes Personals** són importants, però poden tolerar una pèrdua de fins a 24 hores. La **carpeta Documents dels clients** es copia parcialment, ja que alguns tècnics hi deixen informació rellevant.

---

## 2) Cronograma Setmanal Detallat

| Dia       | Dades                  | Tipus de còpia                     | Mitjà                     |
|-----------|-----------------------|----------------------------------|---------------------------|
| Dilluns   | Bases de Dades         | Incremental cada 4 h + completa diària | NAS                       |
|           | Documents de Projectes | Incremental                       | NAS                     |
|           | Carpetes Personals     | Incremental                       |  Disco Duro Extern                       |
| Dimarts   | Bases de Dades         | Incremental cada 4 h + completa diària | NAS                       |
|           | Documents de Projectes | Incremental                       | NAS         |
|           | Carpetes Personals     | Incremental                       | Disco Duro Extern                       |
| Dimecres  | Bases de Dades         | Incremental cada 4 h + completa diària | NAS                       |
|           | Documents de Projectes | Incremental                       | NAS                     |
|           | Carpetes Personals     | Incremental                       | Disco Duro Extern         |
| Dijous    | Bases de Dades         | Incremental cada 4 h + completa diària | NAS                       |
|           | Documents de Projectes | Incremental                       | NAS                     |
|           | Carpetes Personals     | Incremental                       | Disco Duro Extern                       |
| Divendres | Bases de Dades         | Incremental cada 4 h + completa diària | NAS                       |
|           | Documents de Projectes | Incremental                       | NAS         |
|           | Carpetes Personals     | Incremental                       | Disco Duro Extern                       |
| Dissabte  | Bases de Dades         | Incremental cada 4 h + completa diària | NAS                       |
|           | Documents de Projectes | Incremental                       | NAS                     |
|           | Carpetes Personals     | Incremental                       | Disco Duro Extern         |
| Diumenge  | Bases de Dades         | Còpia completa setmanal            | Cloud                       |
|           | Documents de Projectes | Còpia completa setmanal            | Cloud                     |
|           | Carpetes Personals     | Còpia completa setmanal            | Cloud         |

---

## 3) Elecció de Mitjans i Ubicació (Regla 3-2-1)

- **Mitjà 1 (Local):** NAS intern  
  **Justificació:** Permet restaurar dades de manera ràpida en cas de fallada del servidor. És el suport principal per a còpies diàries i incrementals.  

- **Mitjà 2 (Extern):** Cloud Backup (Google Cloud o Backblaze B2)  
  **Justificació:** Ofereix còpia fora de l’empresa amb alta disponibilitat i seguretat. També es poden usar discos durs externs setmanals com a suport físic addicional.  

- **Ubicació Fora de Lloc:**  
  - Cloud: còpia fora de l’empresa, accessible remotament.  
  - Discos durs externs: emmagatzemats en un altre despatx o arxiu segur.  
  - Responsable: responsable IT, que comprova la sincronització i integritat de les còpies.

---

## 4) Estratègia de Recuperació (RTO/RPO)

- **RPO (Pèrdua de dades admissible):**  
  Les bases de dades es copien incrementalment cada 4 hores, assegurant que la pèrdua màxima de dades no superi les 4 hores.  

- **RTO (Temps màxim de recuperació):**  
  Les còpies locals al NAS permeten restaurar dades crítiques en menys de 4 hores. Les còpies al Cloud o discos externs garanteixen recuperació encara que es perdi l’equip físic complet.  

**Conclusió:**  
Amb aquesta combinació de mitjans i ubicacions, es compleixen tots els requisits de la regla 3-2-1 i es garanteix que les dades més crítiques estiguin disponibles dins del temps màxim permès amb mínim risc de pèrdua.

- [Tornar al enunciat](README.md)
