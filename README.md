# Ansible Automation

Questo repository contiene playbook Ansible per l'automazione della configurazione e manutenzione di server e macchine virtuali.

## Struttura del Progetto

- `ansible.cfg`: Configurazione Ansible
- `inventory/`: File di inventario
  - `hosts.yml`: Definizioni degli host
- `playbooks/`: Playbook Ansible
  - `bootstrap_vps.yml`: Bootstrap iniziale per VPS
  - `borg_baseline.yml`: Configurazione baseline per backup Borg
  - `borg_full.yml`: Backup completo con Borg
  - `codemachine.yml`: Configurazione per macchina di sviluppo
  - `mediavm.yml`: Configurazione per VM media
  - `siem_update.yml`: Aggiornamento del sistema SIEM
- `roles/`: Ruoli Ansible
  - `baseline_debian/`: Configurazione base per Debian
  - `bootstrap_users/`: Creazione e configurazione utenti iniziali
  - `hardening_debian/`: Rafforzamento sicurezza per Debian
  - `hardening_local_exposed/`: Rafforzamento per servizi esposti localmente
  - `hardening_vps_debian/`: Rafforzamento specifico per VPS Debian
  - `maintenance_debian/`: Manutenzione per sistemi Debian
  - `maintenance_rocky/`: Manutenzione per sistemi Rocky Linux

## Prerequisiti

- Ansible installato sul sistema di controllo
- Accesso SSH agli host target
- Chiavi SSH configurate per l'autenticazione senza password

## Come Usare i Playbook

Per eseguire un playbook, utilizzare il comando seguente:

```
ansible-playbook -i inventory/hosts.yml playbooks/<nome_del_playbook>.yml
```

Sostituisci `<nome_del_playbook>` con il nome del playbook desiderato.

### Descrizioni dei Playbook

#### bootstrap_vps.yml
Questo playbook configura un VPS appena creato con le impostazioni di base, inclusi utenti iniziali e configurazioni di sicurezza fondamentali.

**Uso:**
```
ansible-playbook -i inventory/hosts.yml playbooks/bootstrap_vps.yml
```

#### borg_baseline.yml
Configura una baseline per il backup utilizzando Borg. Include l'installazione e configurazione iniziale di BorgBackup.

**Uso:**
```
ansible-playbook -i inventory/hosts.yml playbooks/borg_baseline.yml
```

#### borg_full.yml
Esegue un backup completo del sistema utilizzando Borg. Assicurati che borg_baseline.yml sia stato eseguito prima.

**Uso:**
```
ansible-playbook -i inventory/hosts.yml playbooks/borg_full.yml
```

#### codemachine.yml
Configura una macchina per lo sviluppo di codice, installando strumenti e configurazioni necessarie per un ambiente di sviluppo.

**Uso:**
```
ansible-playbook -i inventory/hosts.yml playbooks/codemachine.yml
```

#### mediavm.yml
Configura una macchina virtuale per la gestione di media, inclusi strumenti per elaborazione e archiviazione di file multimediali.

**Uso:**
```
ansible-playbook -i inventory/hosts.yml playbooks/mediavm.yml
```

#### siem_update.yml
Aggiorna e mantiene il sistema SIEM (Security Information and Event Management), applicando patch e configurazioni di sicurezza.

**Uso:**
```
ansible-playbook -i inventory/hosts.yml playbooks/siem_update.yml
```

## Note

- Verifica sempre l'inventario `inventory/hosts.yml` prima di eseguire i playbook per assicurarti che gli host siano correttamente definiti.
- Alcuni playbook potrebbero richiedere privilegi sudo; assicurati che l'utente Ansible abbia i permessi necessari.
- Testa i playbook in un ambiente di staging prima di applicarli in produzione.

## Contributi

Per contribuire, crea una pull request con le tue modifiche.