# T04: Serveis de directori. LDAP  

## 1️⃣ Creació de la màquina virtual

Creem una màquina virtual on instal·larem **Ubuntu Server**.

<img src="img/1.png" alt="Creació d'una màquina virtual amb Ubuntu Server per instal·lar el servei LDAP.">

Un cop dins, actualitzem els paquets:

```bash
sudo apt update && sudo apt upgrade -y
```

Editem el fitxer `/etc/hosts` per definir el domini:

```bash
sudo nano /etc/hosts
```

<img src="img/2.png" alt="Edició de l'arxiu /etc/hosts per definir el domini del servidor.">

Verifiquem que els canvis s’han aplicat correctament al domini.

<img src="img/3.png" alt="Visualització dels canvis aplicats al domini després d'editar l'arxiu hosts.">

---

## 2️⃣ Configuració de xarxa

Per permetre la comunicació amb l’amfitrió, configurem una interfície **Host-Only**:

<img src="img/4.png" alt="Configuració d'una interfície de xarxa host-only per comunicar-se amb l'amfitrió." width="750">

Editarem l’arxiu `/etc/netplan/50-cloud-init.yaml` amb la comanda següent per habilitar la interfície:

```bash
sudo nano /etc/netplan/50-cloud-init.yaml
```

<img src="img/5.png" alt="Edició de l'arxiu /etc/netplan/50-cloud-init.yaml per habilitar la interfície host-only.">

Apliquem els canvis i comprovem la interfície amb `ip a`:

<img src="img/6.png" alt="Comprovació de la nova interfície de xarxa amb la comanda ip a." width="750">

---

## 3️⃣ Instal·lació d’OpenLDAP

Instal·lem el servidor LDAP i les utilitats:

```bash
sudo apt install slapd ldap-utils -y
```

Durant la instal·lació, el sistema ens demanarà la contrasenya de l’administrador. Introduirem `p@ssw0rd`, tal com s’indica al Plec de Condicions Tècniques.

<img src="img/7.png" alt="Instal·lació del servei OpenLDAP mitjançant la comanda apt install slapd ldap-utils.">

Un cop executada la comanda anterior, comprovarem que el servei s’està executant correctament amb la següent comanda:

```bash
sudo systemctl status slapd
```

<img src="img/8.png" alt="Verificació de l'estat del servei slapd amb systemctl status.">

Ara comprovarem que el directori s’ha creat amb el nom desitjat:

```bash
sudo slapcat
```

<img src="img/9.png" alt="Consulta del contingut del directori LDAP amb la comanda slapcat.">

En cas que el nom del directori no sigui el correcte, haurem de reconfigurar el servei amb la següent comanda:

```bash
sudo dpkg-reconfigure slapd
```

---

## 4️⃣ Creació d’unitats organitzatives (OU)

Ara haurem de crear dues unitats organitzatives (*OUs*): **users** i **groups**, mitjançant un fitxer `.ldif`.  

Per fer-ho, crearem l’arxiu `OU_users.ldif` amb la següent comanda:

```bash
sudo nano OU_users.ldif
```

A dins del fitxer hi afegirem el contingut següent:

```ldif
dn: ou=users,dc=innovatech26,dc=test
ou: users
objectClass: top
objectClass: organizationalUnit

dn: ou=groups,dc=innovatech26,dc=test
ou: groups
objectClass: top
objectClass: organizationalUnit
```

<img src="img/10.png" alt="Creació del fitxer OU_users.ldif per definir les unitats organitzatives d'usuaris i grups.">

Per crear finalment les OUs, executarem la comanda següent:

```bash
sudo ldapadd -D "cn=admin,dc=innovatech26,dc=test" -W -f OU_users.ldif
```

<img src="img/11.png" alt="Execució de la comanda ldapadd per afegir les OUs al directori LDAP.">

Per comprovar que les OUs s’han afegit correctament, utilitzarem la comanda següent:

```bash
ldapsearch -xLLL -b "dc=innovatech26,dc=test"
```

<img src="img/12.png" alt="Verificació de les OUs creades amb ldapsearch.">

---

## 5️⃣ Instal·lació del gestor LDAP (LAM)

Com que administrar el servidor de domini des de la línia d’ordres pot resultar complex, és recomanable utilitzar un gestor d’usuaris LDAP com **LDAP Account Manager (LAM)**.

Per instal·lar-lo, executarem la comanda següent (el paràmetre `-y` evita que apareguin missatges de confirmació durant la instal·lació):

```bash
sudo apt install ldap-account-manager -y
```

Un cop instal·lat, ens hi connectarem des de la màquina física a través de la interfície **host-only**, introduint la seva adreça IP seguida de `/lam` al navegador:

```
http://IP_DEL_SERVER/lam
```

<img src="img/13.png" alt="Accés a la interfície web del LAM des del navegador mitjançant la IP del servidor." width="750">

El primer pas és configurar el gestor per al nostre directori.  

Ens dirigirem a la part superior dreta i farem clic a **LAM configuration**.

Un cop dins, accedirem a **Edit server profiles** per començar la configuració del perfil del servidor.

<img src="img/14.png" alt="Pantalla inicial de configuració del LAM, accedint a Edit server profiles." width="750">

A continuació, apareixerà el panell d’inici de sessió, on la contrasenya per defecte és `lam`.

<img src="img/15.png" alt="Panell de login del LAM amb contrasenya per defecte lam." width="650">

En aquest apartat configurarem les opcions generals del gestor, com ara l’idioma, el compte d’administrador i altres paràmetres bàsics.

<img src="img/16.png" alt="Configuració general del servidor LDAP al LAM, idioma i compte d'administrador." width="750">

<img src="img/17.png" alt="Configuració general del servidor LDAP al LAM, idioma i compte d'administrador." width="750">

A la segona pestanya **Account Types**, definirem els **DN** dels usuaris i dels grups, incloent-hi una **OU** per als usuaris i una altra per als grups.

<img src="img/18.png" alt="Definició dels DN per a usuaris i grups a la pestanya Account Types del LAM." width="750">
<img src="img/19.png" alt="Definició dels DN per a usuaris i grups a la pestanya Account Types del LAM." width="750">

Un cop completada la configuració, guardarem els canvis fent clic al botó **Save**, situat a la part inferior esquerra (de color blau).

<img src="img/20.png" alt="Desament de la configuració del LAM fent clic a Save.">

Tot seguit, apareixerà el panell d’inici de sessió, on accedirem amb l’usuari administrador del domini:

```
Usuari: admin  
Contrasenya: p@ssw0rd
```
<img src="img/21.png" alt="Pantalla d'inici de sessió al panell d'administració amb admin/p@ssw0rd." width="750">

---

## 6️⃣ Creació de grups i usuaris

### Grups

Un cop dins del panell d’administració, hem de crear dos **grups de seguretat** al directori: `tech` i `manager`.  

Per fer-ho, anirem a **Accounts → Groups**.

<img src="img/22.png" alt="Creació dels grups de seguretat tech i manager dins del LAM." width="750">

Un cop dins d’aquest apartat, farem clic a **New group** per crear els dos grups. 

<img src="img/23.png" alt="Creació dels grups de seguretat tech i manager dins del LAM." width="750">

Després de configurar-los, premem **Save** per desar els canvis.

Finalment, ja tenim creats els dos grups al directori.

<img src="img/24.png" alt="Confirmació de la creació correcta dels grups tech i manager." width="750">

### Usuaris

Repetirem el mateix procés per crear un usuari per a cada grup, anomenats `tech01` i `manager01`.  

Per fer-ho, ens dirigirem a **Accounts → Users** i farem clic a **New user**.

<img src="img/25.png" alt="Creació d'un nou usuari tech01 al panell d'usuaris del LAM." width="750">

A l’interior del formulari haurem d’introduir la informació personal de l’usuari, com ara l’adreça, el telèfon, la fotografia i altres dades bàsiques.

<img src="img/26.png" alt="Formulari d'usuari amb informació personal i Unix per tech01." width="750">

També configurarem la informació **Unix**, necessària perquè l’usuari pugui iniciar sessió al client.  

En aquest pas, haurem de crear el **grup primari** amb el mateix nom que l’usuari.

<img src="img/27.png" alt="Formulari d'usuari amb informació personal i Unix per tech01." width="750">

Haurem d’afegir l’usuari al **grup corresponent**.  

Per fer-ho, farem clic al botó **Edit groups** i, un cop dins, mourem el grup `tech` (en aquest cas) a la secció **Selected groups** per assignar-lo correctament a l’usuari.

<img src="img/28.png" alt="Assignació de l'usuari tech01 al grup tech mitjançant Edit groups." width="750">

Finalment, haurem de crear una **contrasenya** perquè l’usuari de domini pugui iniciar sessió.  

Per fer-ho, farem clic al botó **Set password**, introduirem la contrasenya `1234` i marcarem la casella que obliga l’usuari a canviar-la en el **primer inici de sessió**.

<img src="img/29.png" alt="Configuració de la contrasenya de l'usuari tech01 amb l'opció de canvi obligatori.">

Un cop completats aquests passos, guardarem el nou usuari fent clic al botó **Save**.  

A continuació, repetirem el mateix procés amb l’usuari i el grup `manager01`, obtenint el resultat següent:

<img src="img/30.png" alt="Visualització dels dos usuaris tech01 i manager01 creats correctament." width="750">

---

## 7️⃣ Configuració del client (ZorinOS)

Per comprovar que el servidor **LDAP** funciona correctament, configurarem un **client ZorinOS**.  

A aquest client li crearem una **segona interfície de xarxa** en mode **host-only**, per tal que pugui comunicar-se amb el servidor.

<img src="img/31.png" alt="Configuració d'un client ZorinOS amb interfície host-only per connectar-se al servidor LDAP." width="750">

Un cop dins del client, haurem de **configurar el nom de l’equip** perquè formi part del mateix domini que el servidor.

Com que no disposem d’un servei **DNS**, editarem el fitxer `/etc/hosts` del client per tal que pugui resoldre el nom del servidor correctament.

<img src="img/32.png" alt="Edició de l'arxiu /etc/hosts del client per afegir el servidor de domini.">

Ara comprovarem que els noms es resolen correctament executant les comandes següents:

### Verificar el nom d’host del client

Per assegurar-nos que el nom de l’equip s’ha canviat correctament:

```bash
hostname -f
```

### Comprovar la resolució del servidor de domini

Per verificar que la resolució DNS cap al servidor de domini és correcta:

```bash
dig server.innovatech26.test
```

<img src="img/33.png" alt="Comprovació del nom d'amfitrió amb la comanda hostname -f i consulta DNS del domini server.innovatech26.test amb la comanda dig." width="750">

### Instal·lació dels mòduls d’autenticació LDAP

Per poder utilitzar el client dins del domini, hem d’instal·lar els **mòduls necessaris** amb la comanda següent:

```bash
sudo apt install libnss-ldap libpam-ldap ldap-utils nscd -y
```

A continuació, s’iniciarà el procés de configuració dels **mòduls d’autenticació**.


<img src="img/34.png" alt="Configuració inicial dels mòduls d'autenticació LDAP.">
<img src="img/35.png" alt="Configuració inicial dels mòduls d'autenticació LDAP.">
<img src="img/36.png" alt="Configuració inicial dels mòduls d'autenticació LDAP.">
<img src="img/37.png" alt="Configuració inicial dels mòduls d'autenticació LDAP.">
<img src="img/38.png" alt="Configuració inicial dels mòduls d'autenticació LDAP.">
<img src="img/39.png" alt="Configuració inicial dels mòduls d'autenticació LDAP.">
<img src="img/40.png" alt="Configuració inicial dels mòduls d'autenticació LDAP.">

Per comprovar la connectivitat amb el servidor, farem una consulta **ldapsearch** des del client amb la comanda següent:

```bash
ldapsearch -x -D "cn=admin,dc=innovatech26,dc=test" -W -H ldap://server.innovatech26.test -b "dc=innovatech26,dc=test" objectClass=posixAccount uid
```

<img src="img/41.png" alt="Comprovació de la connectivitat LDAP amb la comanda ldapsearch.">

---

## 8️⃣ Integració PAM i NSS

Ara configurarem l’arxiu `nsswitch.conf` per indicar que s’utilitzarà **LDAP** per a la gestió d’usuaris i grups.

```bash
sudo nano /etc/nsswitch.conf
```

<img src="img/42.png" alt="Edició de l'arxiu /etc/nsswitch.conf per afegir suport LDAP a usuaris i grups.">

Al fitxer `/etc/pam.d/common-password`, eliminarem la línia que contingui el terme `use_authok`.

<img src="img/43.png" alt="Modificació de l'arxiu /etc/pam.d/common-password per eliminar use_authok.">

Al fitxer `/etc/pam.d/common-session`, afegirem la línia següent per permetre la **creació automàtica dels perfils d’usuari**:

<img src="img/44.png" alt="Afegir línia a /etc/pam.d/common-session per crear perfils d'usuari.">

Ara reiniciarem el servei amb la comanda següent:

```bash
sudo systemctl restart nscd
```

Un cop el servei s’hagi reiniciat, comprovarem que detecta correctament els usuaris **LDAP** amb aquesta comanda:

```bash
getent passwd | tail
```

Podem verificar que el sistema mostra correctament els usuaris provinents del directori **LDAP**.

<img src="img/45.png" alt="Reinici del servei nscd i comprovació dels usuaris LDAP amb getent passwd.">

## 9️⃣ Inici de sessió gràfica

Per finalitzar, editarem el fitxer `/etc/pam.d/gdm-launch-environment` per permetre l’inici de sessió gràfica dels usuaris del domini.

<img src="img/46.png" alt="Edició de l'arxiu /etc/pam.d/gmd-launch-environment per permetre inici de sessió gràfic.">

Reiniciarem el client i, a la pantalla d’inici de sessió, farem clic a **Not listed** per introduir manualment un altre usuari.  

<img src="img/47.png" alt="Pantalla d'inici de sessió del client amb l'opció Not listed per introduir tech01.">

A continuació, introduirem l’usuari `tech01` per iniciar sessió amb les credencials següents:

- **Usuari:** `tech01`
- **Contrasenya:** `1234`

<img src="img/48.png" alt="Primera connexió de l'usuari tech01 i creació automàtica del directori personal.">

Després d’introduir la contrasenya, apareixerà un missatge indicant que s’està creant el **directori personal** de l’usuari, en aquest cas `/home/tech01`.

<img src="img/49.png" alt="Primera connexió de l'usuari tech01 i creació automàtica del directori personal.">

Un cop iniciada la sessió, podem comprovar que tot s’ha creat correctament.

<img src="img/50.png" alt="Sessió iniciada correctament amb l'usuari tech01 verificant el bon funcionament del domini.">

Si repetim el mateix procés amb l’usuari `manager01`, obtindrem el mateix resultat.

<img src="img/51.png" alt="Sessió iniciada correctament amb l'usuari manager01 verificant el bon funcionament del domini.">

[Tornar a enunciat](README.md)
