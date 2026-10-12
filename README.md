# ☁️ Infrastructure Cloud Privée Sécurisée

> Conception, virtualisation et sécurisation d'une infrastructure cloud privée basée sur **Proxmox VE, OpenStack, Active Directory, FortiGate et Veeam**.

![Proxmox](https://img.shields.io/badge/Proxmox-VE-E57000?logo=proxmox&logoColor=white)
![OpenStack](https://img.shields.io/badge/OpenStack-Cloud%20priv%C3%A9-ED1944?logo=openstack&logoColor=white)
![Windows Server](https://img.shields.io/badge/Windows%20Server-AD%20%7C%20DNS%20%7C%20DHCP-0078D4?logo=windows&logoColor=white)
![Fortinet](https://img.shields.io/badge/FortiGate-Pare--feu-EE3124?logo=fortinet&logoColor=white)
![Veeam](https://img.shields.io/badge/Veeam-Backup-00B336)

---

## 📌 Contexte et problématique

Les infrastructures traditionnelles montrent leurs limites : gestion fragmentée des ressources, provisionnement manuel, absence de politique de sécurité unifiée, pas de gestion centralisée des identités, et une reprise après sinistre limitée.

Ce projet propose une **architecture hybride** qui combine la robustesse de la virtualisation sur site avec l'agilité d'un **cloud privé IaaS**, le tout sécurisé et sauvegardé.

## 🎯 Objectifs

- Mettre en place une plateforme de virtualisation (**Proxmox VE**)
- Déployer un cloud privé IaaS (**OpenStack** : Keystone, Nova, Neutron, Glance, Cinder, Horizon)
- Centraliser les identités avec **Active Directory, DNS et DHCP** sous Windows Server
- Appliquer le **hardening** de Windows Server et d'Active Directory
- Protéger le périmètre avec **FortiGate** (filtrage, VLAN, VPN SSL)
- Garantir la continuité de service avec **Veeam Backup & Replication** et un PRA

## 🏗️ Architecture

Modèle de **défense en profondeur** avec trois zones : externe (WAN), interne segmentée (VLAN) et DMZ.

| Zone | Sous-réseau | Fonction |
|---|---|---|
| Management | 192.168.1.0/24 | Administration de l'infrastructure |
| DMZ | 192.168.2.0/24 | Services exposés (Web, Reverse Proxy Nginx, Monitoring) |
| IT | 10.10.10.0/24 | Équipe technique |
| Marketing | 10.10.20.0/24 | Communication |
| RH | 10.10.30.0/24 | Ressources humaines |
| Invités | 10.10.40.0/24 | Accès visiteurs |
| Usine | 10.10.50.0/24 | Systèmes industriels |
| Production | 10.10.60.0/24 | Applications critiques |
| Ventes | 10.10.70.0/24 | Commercial |
| Admins | 10.10.80.0/24 | Supervision sécurité |
| SSL VPN | 10.10.90.0/24 | Accès distant |

> 📷 *Ajoutez ici le schéma d'architecture globale :* `![Architecture](images/architecture.png)`

## 🧰 Technologies

| Couche | Technologie |
|---|---|
| Virtualisation | Proxmox VE (serveur dédié, RAID) |
| Cloud privé | OpenStack sur Ubuntu Server |
| Annuaire & services | Windows Server — AD DS, DNS, DHCP, GPO |
| Automatisation | PowerShell (création d'utilisateurs depuis un CSV) |
| Sécurité réseau | FortiGate — VLAN, règles de filtrage, VPN SSL, NAT |
| Sauvegarde | Veeam Backup & Replication |

## 🔧 Réalisations

1. **Proxmox VE** : installation sur serveur dédié, configuration RAID, ponts réseau, NAT et routage.
2. **OpenStack** : déploiement dans une VM, accès Horizon, création de réseaux privés, sous-réseaux, routeurs et instances.
3. **Windows Server** : IP statique, DNS, promotion en contrôleur de domaine, OU, groupes de sécurité.
4. **Automatisation PowerShell** : import d'utilisateurs et de groupes depuis un fichier CSV.
5. **Hardening** : GPO de sécurité, audit des comptes à privilèges et des politiques de mot de passe.
6. **FortiGate** : segmentation par VLAN, politiques de filtrage, VPN SSL.
7. **Veeam** : jobs planifiés, tests de restauration, plan de reprise d'activité (PRA).

## 📁 Structure du dépôt

```
.
├── README.md
├── docs/
│   └── Rapport_Projet.pdf      # Rapport complet (143 pages)
├── scripts/
│   └── powershell/                  # Scripts AD / DNS (CSV → utilisateurs)
├── configs/                         # Configurations anonymisées
└── images/                          # Schémas et captures
```

## 📄 Rapport complet

👉 [Télécharger la documentation du projet (PDF)](docs/Rapport_Projet.pdf)

Contenu : Virtualisation · Cloud Computing · Étude comparative · Conception · Mise en œuvre · Sécurisation & continuité de service.

## 👥 Auteurs

- **Omar Chmacha** — [GitHub](https://github.com/VOTRE-PSEUDO)
- **Ayoub Chemsi** — [GitHub](https://github.com/ayoubchemsi4-alt)

## ⚠️ Avertissement

Projet à but d'apprentissage et de démonstration. Les adresses IP publiques, identifiants et données sensibles ont été retirés ou anonymisés.

## 📜 Licence

Contenu publié à titre pédagogique — © 2026 Omar Chmacha & Ayoub Chemsi. Tous droits réservés (ou choisissez une licence, ex. [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.fr)).

---

⭐ *N'hésitez pas à laisser une étoile si ce projet vous est utile !*
