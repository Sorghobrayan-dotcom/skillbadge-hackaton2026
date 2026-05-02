# SkillBadge — Le Registre Souverain des Compétences Numériques

> **MIABE Hackathon 2026 · Burkina Faso**  
> *Bâtir depuis l'Afrique. Révolutionner pour le monde.*

---

## Description de la solution

**SkillBadge** est une plateforme de certification de compétences numériques ancrée sur la blockchain Polygon. Elle permet à des apprenants de faire valider leurs compétences par des formateurs certifiés, qui émettent des **badges NFT infalsifiables** (token ERC-1155) avec un hash de transaction vérifiable.

Le problème qu'elle résout est simple : au Burkina Faso comme dans toute l'Afrique de l'Ouest, les compétences numériques sont difficiles à prouver et à vérifier. Les CV sont déclaratifs, les diplômes papier sont falsifiables. SkillBadge crée un **registre souverain décentralisé** où chaque compétence est prouvée, horodatée et vérifiable par n'importe quel recruteur.

La plateforme connecte **trois acteurs** :

| Rôle | Description |
|------|-------------|
|  **Apprenant** | Soumet des projets, reçoit des badges certifiés, gère son portfolio blockchain |
|  **Formateur** | Évalue les projets, émet les badges NFT, suit l'historique on-chain |
|  **Recruteur** | Vérifie les portfolios par ID, recrute les talents, certifie les expériences terrain |

---

## Technologies utilisées

| Composant | Technologie |
|-----------|-------------|
| Frontend | React 18 (mode UMD, sans bundler) |
| Langage | JavaScript (JSX via Babel Standalone) |
| Style | CSS personnalisé — design system complet (variables, animations, responsive) |
| Typographies | DM Sans · DM Mono · Fraunces (Google Fonts) |
| Blockchain | Polygon Mainnet (simulation — hash 0x... · tokenId SKB-XXXXX) |
| Standard NFT | ERC-1155 (badges standards) · Type "terrain" (badges expérience) |
| Stockage | localStorage (registre local simulant la persistance on-chain) |
| Hébergement | Single HTML file — zéro dépendance npm, zéro build step |

---

## Instructions d'installation et d'utilisation

### Prérequis
Aucun. Un navigateur suffit.

### Lancer le projet

**Option 1 — Directement dans le navigateur**
```
1. Télécharger le fichier skillbadge_v6.html
2. Double-cliquer pour l'ouvrir dans votre navigateur

```

**Option 2 — Cloner le repo**
```bash
git clone https://github.com/Sorghobrayan-dotcom/skillbadge-hackaton2026.git
cd skillbadge-hackaton2026
# Ouvrir skillbadge_v6.html dans votre navigateur
```

### Comptes de démonstration

| Rôle | Email | Mot de passe | Info |
|------|-------|--------------|------|
| Apprenant | salimata@skillbadge.bf | pass123 | ID: `X670&gm` |
| Recruteur | sarah@tech.bf | pass123 | Entreprise: TechBF |
| Formateur | marcus@ecole.bf | pass123 | Code: `FORM-2026-X9` |

> **Note :** Les données sont stockées dans le localStorage du navigateur. Pour réinitialiser l'état de démo, aller dans **Mon Compte → Réinitialiser les données**.

---

## Fonctionnalités principales développées

###  Espace Apprenant

- **Portfolio certifié** — Grille de badges NFT cliquables avec tokenId, hash blockchain, score /100 et projet associé
- **Soumission de projets** — Formulaire (titre, description, technologies, lien GitHub) avec notification automatique aux formateurs
- **Suivi des projets** — Statuts en temps réel : En attente / Validé / Refusé (avec motif)
- **Notifications** — 4 types : badge attribué , projet refusé, commentaire formateur , offre d'emploi 
- **Score dynamique** — Calculé automatiquement : `nb_badges × 150 + nb_EXPERT × 100 + nb_INTER × 50`
- **ID Recruteur personnel** — Identifiant unique (ex: `X670&gm`) à communiquer aux recruteurs pour accès au dossier
- **Explorateur de talents** — Voir tous les apprenants inscrits, filtrer par nom ou domaine

###  Espace Formateur

- **Dashboard** — Statistiques globales (badges émis, projets en attente, apprenants) + répartition par domaine
- **Validation de projets** — Pour chaque projet en attente : lire la description, consulter le lien GitHub, voir les commentaires précédents
- **Émission de badge NFT** — Choisir titre, domaine, niveau (DÉBUTANT / INTERMÉDIAIRE / EXPERT), score /100, appréciation textuelle → émission on-chain
- **Refus motivé** — Rejeter un projet avec un motif rédigé, apprenant notifié automatiquement
- **Commentaires** — Laisser un retour écrit sur un projet sans forcément valider, apprenant notifié
- **Projets notés** — Historique de tous les projets évalués (validés ou refusés) avec badges et commentaires associés
- **Historique blockchain** — Tableau de toutes les transactions on-chain : date, apprenant, badge, niveau, hash TX, statut "Confirmé"

### Espace Recruteur

- **Vérification de portfolio** — Accès par ID unique du candidat uniquement (protection vie privée : impossible de chercher par nom ou email)
- **Vue portfolio complète** — Photo, badges NFT, projets validés, liens GitHub, hash blockchain, mention "Vérifié on-chain · Polygon Mainnet"
- **Explorateur de talents** — Grille de tous les apprenants avec photo, score, badges, wallet ; filtres par nom et domaine
- **Envoi d'offres d'emploi** — Depuis l'explorateur : titre du poste + message personnalisé → notification immédiate à l'apprenant
- **Suivi des offres** — Historique de toutes les offres envoyées
- **Badge Terrain Expert**  — Fonctionnalité exclusive : certifier une expérience professionnelle réelle d'un apprenant ayant travaillé dans l'entreprise (poste, domaine, durée, appréciation) → Badge NFT immuable de type "terrain", score 100/100

### 🔗 Système Blockchain

- Chaque badge génère un **tokenId unique** (format `SKB-XXXXX`) et un **hash de transaction** (format `0x...`)
- Les badges Terrain ont un tokenId spécial (`SKB-TXXXXX`) et sont marqués comme immuables
- Indicateur "Vérifié on-chain · Polygon Mainnet" sur chaque badge
- Système de notifications en temps réel (4 types : `badge_awarded`, `projet_rejected`, `comment`, `offer`)

---

## Données pré-chargées (démo)

- **10 apprenants** : Salimata, Ahmed, Fatima, Ibrahim, Aminata, Moussa, Aïssata, Seydou, Mariam, Issouf
- **8 badges pré-émis** : React.js EXPERT, PostgreSQL EXPERT, Docker INTERMÉDIAIRE, Python Data Science EXPERT, Node.js INTERMÉDIAIRE, UI/UX DÉBUTANT, Cybersécurité EXPERT, Flutter INTERMÉDIAIRE
- **3 projets Salimata** : 2 validés + 1 en attente (démontrable en live)

---

## Équipe

**Youngtech** — MIABE Hackathon 2026 · Burkina Faso

---


