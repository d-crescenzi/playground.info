# Playground Info - Web & App Links Configuration

Sito statico per documentazione legale e verifica Android App Links del progetto **Playground**.

---

## ⚠️ Requisito Dominio per Android App Links (Produzione)

Per far sì che l'utente rientri **automaticamente e senza popup/dialog ("Apri con...")** nell'App Android dopo aver completato un pagamento su Stripe:

Android verifica l'autenticità degli App Links inviando una richiesta HTTP `GET` **esclusivamente alla radice del dominio**:
```text
https://<DOMINIO-RADICE>/.well-known/assetlinks.json
```

### Note per il Deploy in Produzione:
* **Su GitHub Pages con sotto-percorso** (`https://d-crescenzi.github.io/playground.info/`), Android cercherà il file a `https://d-crescenzi.github.io/.well-known/assetlinks.json`.
* Per abilitare l'apertura automatica su tutti i dispositivi degli utenti senza dialog:
  1. Posizionare `.well-known/assetlinks.json` nella radice del repository GitHub principale dell'utente (`username.github.io`).
  2. **Oppure** utilizzare un dominio personalizzato di primo livello dedicato (es. `https://playground.info/`).

---

## 🛠️ Approvazione Manuale su Dispositivo di Test (ADB)

Per scavalcare la verifica su dominio radice durante lo sviluppo locale:
```bash
adb shell pm set-app-links --package com.crescenzi.playground 2 d-crescenzi.github.io
```
