# 🧩 T04: Serveis de Directori. LDAP

## 📘 Descripció de la tasca

**Innovatech**, una start-up tecnològica emergent, està experimentant un ràpid creixement i pateix un **caos en la gestió dels seus usuaris i accessos**.  
Actualment, cada servei intern (servidor de fitxers, wiki de documentació, etc.) utilitza la seva pròpia base de dades d’usuaris i contrasenyes, i a més als ordinadors clients s’utilitza autenticació local.

Aquesta situació provoca diversos **problemes crítics**:

- ⚙️ **Ineficiència operativa:** cada vegada que s’incorpora o marxa un empleat, l’equip tècnic ha de crear o eliminar el compte en múltiples sistemes.  
- 🔒 **Risc de seguretat:** els usuaris sovint reutilitzen contrasenyes entre serveis per evitar l’oblit.  
- 🚫 **Manca d’escalabilitat:** a mesura que Innovatech afegeix nous serveis, el problema es fa insostenible.

El **CEO d’Innovatech** ha contactat amb **EverPia** per implementar una solució d’autenticació centralitzada.  
La proposta és utilitzar **OpenLDAP (Lightweight Directory Access Protocol)**, una solució **robusta i de codi obert**, alineada amb la filosofia de l’empresa, ja que tots els ordinadors utilitzen **GNU/Linux**.

## 🧾 Objectius del projecte

La vostra missió serà **implementar un servei OpenLDAP en un servidor Linux**.  
Això inclou:

1. 🖥️ Instal·lar el servei **OpenLDAP**.  
2. ⚙️ Configurar el **domini base** del directori.  
3. 🧱 Crear la **jerarquia d’unitats organitzatives (OUs)**.  
4. 👥 Afegir **usuaris i grups** al directori.  
5. 💻 Configurar un **equip client** perquè utilitzi el directori per autenticar usuaris.  

## 🔍 Fases del projecte

### 🧩 Fase 1: Instal·lació i configuració del servidor
- Instal·lació d’OpenLDAP i paquets necessaris.  
- Definició del domini base i estructura inicial del directori.  
- Verificació del funcionament del servei.

### 🧩 Fase 2: Creació de la jerarquia i integració d’usuaris
- Creació de les **unitats organitzatives (OUs)**.  
- Afegir **usuaris i grups** dins la jerarquia LDAP.  
- Validació de la informació al directori.

### 🧩 Fase 3: Integració amb clients Linux
- Configuració del **client Linux** per autenticar-se amb LDAP.  
- Proves d’inici de sessió amb usuaris del directori.  
- Documentació de resultats i incidències.

## 📂 Estructura de carpetes

Dins la carpeta `tasca04` es troben els següents arxius:

- `solucio.md`: Guia tècnica d’instal·lació i configuració d’OpenLDAP  
- Carpeta `img/`: Conté captures de pantalla i esquemes del procés d’instal·lació.  

## 📎  Documents
Podeu consultar tots els documents fent clic al document corresponent:
- Al arxiu [solucio](solucio.md) podeu trobar la guia.
