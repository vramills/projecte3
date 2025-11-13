# 🌐 P04: Documentació servidor DNS  

Com a membres de l'equip de **sistemes d'EverPia**, us enfronteu al repte de configurar un **servidor de noms (DNS)** com a prova de concepte per al nostre client **Digicore**.  
Actualment, el resultat de la vostra feina es troba en una màquina virtual, però l’objectiu és **publicar aquestes configuracions a GitHub** per facilitar-ne la replicació en futurs entorns.

---

## 🎯 Objectiu  
Permetre que, quan es vulgui replicar la configuració, **no calgui començar des de zero**: només caldrà descarregar els arxius al servidor Linux triat i **reiniciar el servei** per tenir el servidor completament operatiu.

---

## 🧩 Fase 1: Preparació de la Connectivitat i Extracció dels Arxius  

### ⚙️ Pas 1.1: Configuració de la Interfície Host-Only  
1. **Afegiu una segona interfície de xarxa** a la vostra màquina virtual Ubuntu Server i assigneu-li el mode **Host-Only**.  
2. Configureu-la i activeu-la.  
3. Comproveu que teniu **connectivitat** des de la màquina física (host).

### 🔐 Pas 1.2: Còpia Segura dels Fitxers Clau amb SCP  
Un cop establerta la connectivitat *Host-Only*, utilitzarem el protocol **SCP (Secure Copy Protocol)**, inclòs en el servei SSH, per transferir els fitxers de configuració a la màquina física.

#### 📂 Fitxers a copiar:
- `/etc/bind/named.conf.options`  
- `/etc/bind/named.conf.local` *(revisar que no tingui errors tipogràfics com "cof")*  
- Arxius de zones dins la carpeta `/etc/bind/zones`

#### 💻 Exemple de comanda SCP:
```bash
scp usuari@IP_VM:/etc/bind/named.conf.options .
```
> 🔸 El punt (`.`) al final indica que l’arxiu es copiarà al **directori actual** de la vostra màquina física.

---

## 🚀 Fase 2: Integració a GitHub  

### 📁 Pas 2.1: Crear Carpeta i Arxiu `README.md`  
1. Creeu la carpeta `producte04` i dins d’ella l’arxiu `README.md`.  
   > 💡 Si feu servir l’opció *New File* a GitHub, podeu escriure directament `producte04/README.md` per crear la carpeta automàticament.  
2. Al fitxer `README.md`, afegiu:  
   - 🏷️ **Títol del producte**  
   - 🧾 **Explicació del contingut**  

### ☁️ Pas 2.2: Pujar Arxius  
1. Pugeu tots els arxius de configuració a la carpeta `producte04`.  
2. Creeu la carpeta `zones` abans de pujar-hi els arxius corresponents.  
3. Podeu crear un fitxer temporal `zones/esborrar` per assegurar la creació de la carpeta, i després **elimineu-lo** quan hagueu pujat els arxius reals.

---

## ✅ Resultat Final  
Amb aquests passos, tindreu:
- Un **repositori GitHub** amb tota la configuració del servidor DNS.  
- La possibilitat de **replicar fàcilment** la configuració en qualsevol servidor Linux.  
- Una **documentació clara i estructurada** per a futurs consultors o manteniments.  

---

## 📂  Estructura de carpetes

Dins la carpeta `producte04` es troben els següents arxius:

- `named.conf.local`: Arxiu de configuració on es defineixen les zones que allotjarà el servidor.
- `named.conf.options`: Arxiu de configuració on estan definides les configuracions generals.
- Carpeta `zones/`: Conté els arxius de configuració de les zones.

## 📎  Documents
Podeu consultar tots els documents fent clic al document corresponent:
- Al arxiu [named.conf.local](named.conf.local) podeu trobar la configuració on es defineixen les zones que allotjarà el servidor.
- Al arxiu [named.conf.options](named.conf.options) podeu trobar la configuració on estan definides les configuracions generals.
- A la carpeta [zones](./zones) conté els arxius de configuració de les zones.
