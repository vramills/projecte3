# ⚙️ T06: Fonaments del servei DNS

Com a membres cada cop més integrats de l'equip tècnic de la consultora **EverPia**, teniu davant un nou repte.

El vostre client, una empresa de màrqueting digital (**DigiCore**), experimenta de tant en tant **errors de connectivitat** a certes aplicacions.  
El seu equip tècnic sospita que la causa principal podria ser una **resolució de noms (DNS)** incorrecta o massa lenta.

Se us ha encarregat **realitzar una auditoria teòrica i pràctica del servei DNS**, amb l’objectiu de:

- Formar el personal tècnic del client.  
- Oferir **eines de diagnosi ràpides** per detectar i resoldre problemes de DNS.

---

## 🧠 Fase Teòrica: Sessió Formativa

Com a part d’aquesta formació, caldrà **elaborar material formatiu** per al personal tècnic del client.

Per garantir la màxima qualitat en els continguts, els **directors tècnics d’EverPia** han preparat **sessions prèvies** perquè domineu els conceptes necessaris sobre DNS abans de la presentació.

### 🎥 Activitat de la fase teòrica

Un cop assimilat el contingut, haureu de preparar una **píndola formativa en format vídeo** (d’entre **10 i 15 minuts**) que:

- Expliqui de manera breu però clara els **conceptes fonamentals del servei DNS**.  
- Inclogui exemples o esquemes visuals per reforçar l’explicació.  
- Estigui orientada a un públic tècnic amb coneixements bàsics de xarxes.

### 🧩 Temes suggerits

- Què és el DNS i com funciona.  
- Jerarquia del sistema DNS (Root, TLD, autoritatius).  
- Tipus de registres DNS (A, AAAA, CNAME, MX, NS, PTR...).  
- Resolució directa i inversa.  
- Caché DNS i TTL.  
- Servidors DNS públics vs privats.  
- Diagnosi i eines habituals.

---

## 🧪 Fase Pràctica: Diagnosi de Noms (Auditoria amb CLI)

En aquesta fase, haureu de **demostrar l’ús de les principals utilitats de diagnosi DNS** en els diferents sistemes operatius que utilitza el client:

- **Linux / macOS**  
- **Windows**

Per a cada eina, executeu les **comandes indicades** contra el **domini especificat** i **captureu/analitzeu els resultats**.

---

## 💻 Entorn de treball

Per a la demostració pràctica, cal utilitzar un **equip Zorin OS** amb les següents característiques de xarxa:

- **Primera interfície:** NAT  
- **Segona interfície:** Adaptador pont (Bridge Adapter)  
- **Configuració IP:** segons les indicacions dels vostres responsables

---

## 📂  Estructura de carpetes

Dins la carpeta `tasca06` es troben els següents arxius:

- `video.md`: Vídeo formatiu sobre el DNS.
- `guia.md`: Guia tècnica de la Fase 2 amb instruccions pas a pas per a l’eina seleccionada.
- Carpeta `img/`: Conté les imatges utilitzades a la guia.

## 📎  Documents

Podeu consultar tots els documents fent clic al document corresponent:
- Al arxiu [vídeo](video.md) podeu trobar el link al video.
- Al arxiu [guia](guia.md) podeu trobar la guia.
