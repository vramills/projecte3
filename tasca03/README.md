# 🖥️ T03: Gestió flexible de discos (LVM i Storage Spaces)

Un cop superada la fase de formació, ja esteu preparats per afrontar el repte dels nostres clients.  
El bufet d’advocats **Garriga i Associats** gestiona informació legal sensible, per això cal garantir:

- 🔒 **Integritat de la informació**  
- ⚡ **Alta disponibilitat / redundància**  
- 📦 **Facilitat de gestió i escalabilitat**

L'objectiu és **dissenyar i documentar dues solucions d’emmagatzematge**: Linux i Windows, utilitzant màquines virtuals.

---

## 🐧 1. Part Linux: LVM amb Zorin OS

### Requisits

- 💾 Crear un grup de volums (VG) i un volum lògic (LV) amb **dos discos de 10 GB**.  
- 🔄 Implementar **mirror** (`lvm_mirror`) per redundància.  
- 📸 Crear **snapshots** per restauració en cas de fallada.  
- ➕ Demostrar **ampliació d'espai** dins el grup de volums.

## 🪟 2. Part Windows: Storage Spaces

### Requisits

- 💽 Crear **Storage Pool** amb 3 discos de 10 GB.  
- 🔄 Provar **mirall, paritat i mirall triple**.  
- 🖥️ Visualitzar l’estat del pool i discos a Windows.

---

## 🤝 Treball en grup i lliurament

1. Dividir-se en equips: Linux / Windows.  
2. Preparar guió individual amb comandes i documentació.  
3. Cada parella realitza la demostració.  
4. Revisió final del grup i pujada de fitxers.

## 📂  Estructura de carpetes

Dins la carpeta `tasca03` es troben els següents arxius:

- `guia_lvm.md`: Guia tècnica de Part Linux: LVM amb Zorin OS
- `guia_storage_spaces.md`: Guia tècnica de Part Windows: Storage Spaces
- Carpeta `img/`: Conté les imatges utilitzades a les guies.

## 📎  Documents
Podeu consultar tots els documents fent clic al document corresponent:
- Al arxiu [guia_lvm](guia_lvm.md) podeu trobar la guia de LVM amb Zorin OS.
- Al arxiu [guia_storage_spaces](guia_storage_spaces.md) podeu trobar la guia de Windows Storage Spaces.
