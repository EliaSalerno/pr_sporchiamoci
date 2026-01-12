# Guida Rapida: Formattazione e Sviluppo (Alpine Linux)

Questa guida illustra i passaggi per installare Alpine Linux e configurare un ambiente Docker/Anaconda partendo da zero.

---

## 1. Preparazione ISO
*   **Download**: Scarica la ISO di **Alpine Linux** (versione "Standard" per il terminale o "Extended" per avere più driver preinstallati) dal sito ufficiale.
*   **Media**: Scrivi la ISO su una chiavetta USB (usa tool come Rufus o BalenaEtcher).

## 2. Accesso al BIOS/UEFI
1.  **Riavvio**: Riavvia il computer.
2.  **Tasto di Accesso**: Premi ripetutamente il tasto dedicato all'accensione (solitamente `F2`, `F12`, `Canc` o `Esc`).
3.  **Configurazione**: 
    *   Disabilita il *Secure Boot* se necessario.
    *   Imposta la chiavetta USB come primo dispositivo di **Boot Priority**.
    *   Salva ed esci (`F10`).

## 3. Installazione Alpine Linux
Al caricamento della ISO, effettua il login come `root` (senza password) e avvia l'installer:
```bash
setup-alpine
```
*Segui i prompt:*
*   **Keyboard**: Seleziona il layout (es. `it`).
*   **Networking**: Configura l'interfaccia di rete e l'indirizzo IP (solitamente DHCP).
*   **Disk**: Scegli il disco di destinazione (es. `sda`) e seleziona la modalità `sys` per un'installazione persistente su disco.
*   **Password**: Imposta una password robusta per l'utente root.

## 4. Configurazione Ambiente di Sviluppo

### Opzione A: Docker (Consigliata)
Per gestire ambienti isolati e leggeri:
```bash
# Aggiorna i repository
apk update
# Installa Docker
apk add docker
# Avvia e abilita Docker al boot
rc-update add docker default
service docker start
```

### Opzione B: Anaconda (Miniconda)
Se preferisci gestire ambienti Python:
```bash
# Installa le dipendenze per script shell e glibc (Alpine usa musl)
apk add wget bash
# Scarica l'installer Miniconda
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
# Esegui l'installazione
bash Miniconda3-latest-Linux-x86_64.sh
```

---
> [!TIP]
> Per Alpine Linux, Docker è spesso la scelta migliore grazie alla sua natura "minimal" che si sposa perfettamente con l'OS.
