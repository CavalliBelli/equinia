[readme_md.md](https://github.com/user-attachments/files/33880852/readme_md.md)
# 🐴 Equinia PWA — Scheda Abbonamento Digitalizzata

**Equinia** è una Progressive Web App (PWA) progettata per sostituire la classica scheda abbonamento cartacea per le lezioni di equitazione presso **ASD Equinia (Faenza)**.

L'applicazione consente agli allievi di monitorare le proprie crocette (lezioni usate e rimanenti), proporre date per le lezioni, registrare gli orari concordati e gestirne la disdetta nel rispetto del regolamento delle 24 ore di preavviso.

---

## 📸 Funzionalità Principali

### 🎟️ Gestione Abbonamento e Crocette
- **Contatore Crocette**: Ogni abbonamento comprende 10 crocette (lezioni).
- **Tracciamento Visivo**: Visualizzazione chiara delle crocette completate (`✅`) e disponibili (`🔲`).
- **Aggiunta Manuale**: Possibilità di aggiungere crocette a fine lezione.
- **Eliminazione Protetta**: Rimozione delle crocette riservata all'istruttrice tramite **password** (hash SHA-256).
- **Storico Operazioni**: Registro degli ultimi 20 eventi (aggiunte, eliminazioni, rinnovi, scadenze).
- **Scadenza Abbonamento**: Notifica automatica a 14 giorni dalla scadenza (durata standard: 90 giorni) con azzeramento automatico alla scadenza.

### 📅 Gestione Lezioni e Disdette (Regola delle 24h)
1. **Proponi Date**: L'allievo invia una richiesta con le sue disponibilità tramite email.
2. **Registra Date Confermate**: Una volta concordata l'ora con l'istruttrice via mail, l'allievo salva la data/ora nell'app (supporta l'inserimento multiplo di più lezioni contemporaneamente).
3. **Controllo Disdetta 24h**:
   - **Disdetta > 24 ore**: L'allievo può disdire la lezione; l'app rimuove l'impegno e apre il client email con il messaggio precompilato.
   - **Disdetta < 24 ore**: L'app **blocca la disdetta** notificando che la lezione verrà addebitata come consumata/persa.

### 📲 Funzionalità PWA
- **Installabile su Schermata Home**: Guida integrata per la registrazione dell'app su Android (Chrome) e iOS (Safari).
- **Funzionamento Offline**: Sfrutta il `localStorage` del dispositivo per preservare lo stato e i dati.
- **Tutorial Onboarding**: Guida introduttiva passo-passo al primo avvio.

---

## 🛠️ Architettura e Tecnologie

- **Frontend**: HTML5, CSS3, JavaScript Vanilla (ES6+).
- **Persistenza Dati**: `localStorage` del browser per la memorizzazione di crocette, lezioni fissate e storico.
- **Sicurezza**: Password hashing lato client tramite API nativa Web Crypto (`crypto.subtle` / SHA-256).
- **Comunicazione Email**: Formattazione dinamica di link `mailto:`.
- **Hosting**: GitHub Pages (Client-Side unicamente).

---

## 📂 Struttura localStorage

| Chiave | Tipo | Descrizione |
| :--- | :--- | :--- |
| `tot_crocette` | `number` | Numero di crocette attualmente segnate (0–10). |
| `data_inizio_abb` | `string` (ISO) | Data di avvio del blocco abbonamento corrente. |
| `storico` | `Array<string>` | Lista degli ultimi 20 eventi registrati. |
| `lezioni_confermate` | `Array<Object>` | Elenco delle lezioni con ID e timestamp `dataOra`. |
| `app_version` | `string` | Tracciamento versione app per popup aggiornamenti. |
| `tutorial_visto` | `boolean` | Flag per evitare la ripetizione del tutorial iniziale. |

---

## 🚀 Installazione e Deployment

1. Clona questa repository:
   ```bash
   git clone https://github.com/tuo-username/equinia.git
   ```
2. Carica i file su un servizio di hosting statico (es. **GitHub Pages**).
3. Apri l'indirizzo generato sul dispositivo mobile e seleziona **"Aggiungi a schermata Home"**.

---

## 🔐 Nota sulla Privacy e Sicurezza

Tutti i dati personali (nome, email e registro lezioni) risiedono **esclusivamente sul dispositivo dell'utente**. L'applicazione non utilizza backend esterni o tracciamenti di terze parti.
