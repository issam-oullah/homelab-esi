# homelab-esi
VMware Workstation sandbox — Windows Server 2019 AD (lab.local), pfSense gateway, Ubuntu 24.04 server, Zabbix 7 supervision.
<p align="center">
<p align="center">
  <img src="header-all-vms.png" alt="Vue d'ensemble du laboratoire - 4 machines virtuelles" width="800" />
</p>

<h1 align="center">Laboratoire Infrastructure — sandbox VMware</h1>

<p align="center">
  <img alt="DC01 - Windows Server 2019" src="https://img.shields.io/badge/DC01-Windows%20Server%202019-blue" />
  <img alt="SRV01 - Ubuntu 24.04" src="https://img.shields.io/badge/SRV01-Ubuntu%2024.04-orange" />
  <img alt="FW01 - pfSense" src="https://img.shields.io/badge/FW01-pfSense%202.7.2-red" />
  <img alt="MON01 - Zabbix" src="https://img.shields.io/badge/MON01-Zabbix%207.0-green" />
</p>

## Machines & rôles

| VM    | Rôle                         | Adresse IP     | Héberge les services |
|-------|------------------------------|----------------|----------------------|
| FW01  | Passerele / pare-feu (pfSense) | 192.168.183.2 | NAT + routage host-only |
| DC01  | Contrôleur de domaine `lab.local` (AD + DNS) | 192.168.183.10 | Active Directory, DNS |
| SRV01 | Serveur GNU/Linux (Ubuntu 24.04), joint à l'AD | 192.168.183.20 | Services applicatifs |
| MON01 | Supervision (Zabbix 7)       | 192.168.183.30 | Zabbix server + Web UI |

<table>
  <tr>
    <td><img src="dc01.png" alt="DC01 - Windows Server 2019" width="400" /></td>
    <td><img src="srv01.png" alt="SRV01 - Ubuntu 24.04" width="400" /></td>
  </tr>
  <tr>
    <td><img src="fw01.png" alt="FW01 - pfSense" width="400" /></td>
    <td><img src="mon01.png" alt="MON01 - Zabbix" width="400" /></td>
  </tr>
</table>

## Plan réseau

- **Réseau interne (lab)** : `192.168.183.0/24` — vmnet1 (host-only), passerelle `192.168.183.2`
- **Accès externe** : vmnet8 (NAT) `192.168.29.x` — WAN du pare-feu pfSense
- **DNS** : DC01 (`192.168.183.10`) — domaine `lab.local`
- **Supervision** : Zabbix server sur MON01 (`192.168.183.30`), agents sur DC01 & SRV01

| Machine | IP interne | Nom DNS         |
|---------|-----------|-----------------|
| FW01    | .2        | fw01.lab.local  |
| DC01    | .10       | dc01.lab.local  |
| SRV01   | .20       | srv01.lab.local |
| MON01   | .30       | mon01.lab.local |

## Composition du domaine lab.local

- **Contrôleur de domaine :** DC01 (Windows Server 2019) — AD, DNS
- **Machines jointes au domaine :** SRV01 (Ubuntu 24.04), MON01 (Zabbix appliance)
- **OU :** `ITDept`
- **Comptes :** `issam`, `alae`

## Supervision

- **Zabbix Web UI :** `http://192.168.183.30` (login `Admin`)
- Hôtes supervisés : **SRV01** (`Linux by Zabbix agent`) et **DC01** (`Windows by Zabbix agent`)

## Sécurité & comptes

> ⚠️ Ce tableau ne doit **jamais** être committé sur un dépôt **public**.

| Élément                  | Identifiant     | Mot de passe     |
|--------------------------|-----------------|------------------|
| DC01 — admin domaine     | `LAB\Administrateur` | `Admin123@` |
| DC01 — mode restauration | —               | `LabDsrm2026$`   |
| SRV01 — compte local     | `issam`         | `issam123`       |
| FW01 — pfSense           | `admin`         | `pfsense`        |
| MON01 — root / SSH       | `root`          | `zabbix`         |
| Zabbix — Web UI          | `Admin`         | `zabbix`         |
| AD — utilisateur         | `issam`         | `issamoullah123$&@` |
| AD — utilisateur         | `alae`          | `alaeoullah123$&@`  |

## Journal technique

| Date       | Action                     | Problème                                 | Solution                                     |
|------------|----------------------------|------------------------------------------|----------------------------------------------|
| *(à compléter au fil des étapes)*

---
*Laboratoire pédagogique virtuel — VMware Workstation Pro 17.6.4.*
