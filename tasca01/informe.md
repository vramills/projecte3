# Informe tècnic: Gestor de contrasenyes
**Data:** 21/10/2025  
**Autor:** Víctor Rodríguez Amills | SMX2B | Seguretat informàtica  

<img src="img/logo_fp.png" alt="Logo de FP de Escola Pia Santa Anna" width="150">

## Índex
- [1. Introducció i Justificació](#1-introducció-i-justificació)  
  - [1.1. Riscos associats a les contrasenyes febles o reutilitzades](#11-riscos-associats-a-les-contrasenyes-febles-o-reutilitzades)  
  - [1.2. Funció del gestor de contrasenyes](#12-funció-del-gestor-de-contrasenyes)  
- [2. Comparativa tècnica entre opcions](#2-comparativa-tècnica-entre-opcions)  
- [3. Avantatges i inconvenients](#3-avantatges-i-inconvenients)  
- [4. Recomanació final](#4-recomanació-final)

---

## 1. Introducció i Justificació

L’empresa EverPia ha patit recentment un atac de ciberseguretat que ha provocat una fuga d’informació confidencial (data breach).  
La investigació interna ha revelat que la causa va ser el compromís d’un compte d’un tècnic a causa de l’ús d’una contrasenya feble o reutilitzada.

Aquest tipus de vulnerabilitat és un dels principals vectors d’atac actuals i pot tenir conseqüències molt greus:
- Pèrdua de dades sensibles o propietat intel·lectual.
- Interrupcions dels serveis essencials.
- Dany reputacional i pèrdua de confiança dels clients.
- Sancions legals per incompliment de normatives de protecció de dades.

### 1.1. Riscos associats a les contrasenyes febles o reutilitzades
- Atac de diccionari: els atacants proven contrasenyes comunes o predefinides (com “123456”, “password”, “admin”, etc.) fins que troben una coincidència.
- Credential stuffing: quan una contrasenya filtrada d’un altre servei és reutilitzada, els atacants poden accedir a múltiples comptes.
- Phishing o enginyeria social: mitjançant correus o webs falses, els atacants enganyen els usuaris per obtenir les seves credencials.
- Brute force: intents automatitzats de provar totes les combinacions possibles fins a trobar la correcta.

### 1.2. Funció del gestor de contrasenyes
Per mitigar aquests riscos, la Direcció Tècnica d’EverPia ha decidit implantar un gestor de contrasenyes corporatiu.

Un gestor de contrasenyes permet:
- Generar contrasenyes úniques, llargues i complexes per a cada compte.
- Emmagatzemar-les de forma xifrada i segura.
- Facilitar l’accés a aquestes credencials des de diversos dispositius.
- Evitar la reutilització de contrasenyes entre serveis.
- Permetre la revocació i control centralitzat d’accessos.

Aquesta mesura redueix dràsticament el risc d’incidents similars al que ha afectat l’empresa.

---

## 2. Comparativa tècnica entre opcions

A continuació es presenta una comparativa entre dues eines representatives del mercat: Bitwarden (online) i KeePassXC (offline).

| Característica          | Bitwarden (Online)                                            | KeePassXC (Offline)                          |
|-------------------------|---------------------------------------------------------------|----------------------------------------------|
| Model d’emmagatzematge  | Núvol (servidors Bitwarden o autoalbergats)                   | Local (fitxer .kdbx xifrat)                  |
| Xifratge                | AES-256 + PBKDF2-SHA256, end-to-end                           | AES-256 amb xifratge local                   |
| Codi obert              | Sí (auditat públicament)                                      | Sí (GPLv3)                                   |
| Sincronització          | Automàtica entre dispositius                                  | Manual (cal copiar l’arxiu)                  |
| Accessibilitat          | Web, app mòbil, escriptori, extensió navegador                | Escriptori (Windows/Linux/macOS)             |
| Funcions addicionals    | Compartició segura, 2FA, generador d’OTP                      | Portable, sense dependència del núvol        |
| Cost                    | Model freemium (gratuït + premium opcional)                   | Gratuït                                      |
| Gestió corporativa      | Administració d’usuaris, rols i grups                         | Limitada, ús individual                      |
| Facilitat d’ús          | Molt alta                                                     | Mitjana (perfil tècnic)                      |
| Dependència d’Internet  | Sí (per sincronitzar)                                         | No                                           |

---

## 3. Avantatges i inconvenients

### Bitwarden (Alternativa Online)
Avantatges:
- Sincronització automàtica entre tots els dispositius.
- Interfície moderna i intuïtiva.
- Xifratge end-to-end verificable.
- Compatible amb navegadors i dispositius mòbils.
- Permet una gestió centralitzada dels usuaris i grups.

Inconvenients:
- Depèn d’un servei extern o d’un servidor propi si s’autoalberga.
- Necessita connexió a Internet per a la sincronització.

### KeePassXC (Alternativa Offline)
Avantatges:
- Control total sobre l’arxiu de contrasenyes.
- Sense dependència d’Internet ni servidors externs.
- Completament gratuït i de codi obert.
- Pot funcionar des d’una memòria USB.

Inconvenients:
- Sincronització manual i més complexa.
- Major risc de pèrdua de dades si no es fan còpies de seguretat regulars.
- Interfície menys intuïtiva i enfocada a usuaris tècnics.

---

## 4. Recomanació final

Després de l’anàlisi tècnica, es recomana implantar **Bitwarden** com a gestor de contrasenyes corporatiu per a EverPia.

Justificació:
- Ofereix xifratge de punta a punta (end-to-end), garantint que només els usuaris autoritzats poden accedir a les dades.
- Permet sincronitzar de manera segura les credencials entre equips i dispositius, adaptant-se a entorns híbrids (oficina i teletreball).
- És una solució de codi obert i auditable, que assegura transparència i confiança.
- Facilita la gestió d’usuaris i grups dins d’un entorn corporatiu.
- Disposa d’una versió gratuïta suficient per a la majoria d’usos i opcions premium per a necessitats avançades.

Per tant, Bitwarden és la millor opció per millorar la seguretat, l’eficiència i la gestió de contrasenyes dins de l’empresa.

[Tornar a enunciat](README.md)
