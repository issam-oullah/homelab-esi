# homelab-esi
VMware Workstation sandbox — Windows Server 2019 AD (lab.local), pfSense gateway, Ubuntu 24.04 server, Zabbix 7 supervision.
<p align="center">
  <img src="<img width="555" height="116" alt="image" src="https://github.com/user-attachments/assets/db7d9ad4-9105-43dc-85b0-41a310aa2bfc" />
" alt="Lab overview" width="800" />
</p>

<h1 align="center">Laboratoire Infrastructure — sandbox VMware</h1>

<p align="center">
  <img alt="Windows Server 2019" src="<img width="959" height="479" alt="image" src="https://github.com/user-attachments/assets/2dd17c19-c71c-4168-b82a-5813d2eec0f3" />
" />
  <img alt="Ubuntu" src="<img width="833" height="448" alt="image" src="https://github.com/user-attachments/assets/9d057986-223b-40de-83f0-b755f6e10840" />
" />
  <img alt="pfSense" src="<img width="890" height="448" alt="image" src="https://github.com/user-attachments/assets/2d7b5557-0436-4f71-9716-da52106e3d35" />
" />
 <img alt="zabbix" src="<img width="890" height="448" alt="image" src=" <img alt="pfSense" src="<img width="890" height="448" alt="image" src="https://github.com/user-attachments/assets/2d7b5557-0436-4f71-9716-da52106e3d35" />
" />" />
" />
</p>

## Architecture

| VM    | Rôle                 | Adresse IP      | Réseau     |
|-------|----------------------|-----------------|------------|
| FW01  | Passerelle (pfSense) | 192.168.183.2   | host-only  |
| DC01  | AD / DNS / `lab.local` | 192.168.183.10 | host-only |
| SRV01 | Serveur Ubuntu (AD join) | 192.168.183.20 | host-only |
| MON01 | Supervision Zabbix   | 192.168.183.30  | host-only |

- **Réseau lab** : `192.168.183.0/24` (vmnet1), passerelle `pfSense` via NAT (`vmnet8 192.168.29.x`)
- **DNS** : DC01 (`192.168.183.10`) — domaine `lab.local`

## Comptes & accès

| Élément | Identifiant | Mot de passe |
|---|---|---|
| DC01 (admin domaine) | `LAB\Administrateur` | `Admin123@` |
| DC01 (DSRM) | — | `LabDsrm2026$` |
| SRV01 (local) | `issam` | `issam123` |
| FW01 (pfSense) | `admin` | `pfsense` |
| MON01 (root/SSH) | `root` | `zabbix` |
| Zabbix web UI | `Admin` | `zabbix` |
| AD — `issam` | `issam` | `issamoullah123$&@` |
| AD — `alae` | `alae` | `alaeoullah123$&@` |

> ⚠️ **Attention** : ne pas committer ce tableau en clair sur un repo public — utilisez un **`.gitignore`** ou un repo privé.

## Quick tour
- Zabbix UI : https://192.168.183.30 (ou http)
- pfSense : https://192.168.183.2

## Journal technique
| Date | Action | Problème | Solution |
|---|---|---|---|
| *(à remplir au fil du travail)*
