<div align="center">

<img src="assets/icon.png" width="68" alt="OPSEC Pro"/>

# OPSEC Pro

Édition Observatoire · `RELEASE` · Windows 10 / 11 (x64)

Client natif de gestion de présence, d'observabilité réseau et d'administration locale multi-comptes pour Discord.

[Télécharger l'installeur](https://github.com/ellecrydansmesdm/opsec-pro/releases/latest) · [Notes de version](https://github.com/ellecrydansmesdm/opsec-pro/releases) · [Support Discord](https://discord.gg/W2YgEStqJ4)

</div>

---

<p align="center">
  <img src="assets/gallery/01-overview.png" width="100%" alt="OPSEC Pro RELEASE — Vue d'ensemble Observatoire"/>
</p>

## Présentation

OPSEC Pro regroupe dans une interface native Windows la gestion de profil et de présence temps réel, le maintien vocal compatible DAVE, des outils d'entretien de compte et un centre de diagnostic réseau complet.

L'interface repose sur le système visuel **Observatoire** (rendu WebGL2 à cadence adaptative, transitions instantanées sans rechargement de vue, respect de `prefers-reduced-motion`, interface en français et en anglais). Toutes les données sensibles stockées par l'application sont chiffrées localement via l'API système **Windows DPAPI** (`Electron safeStorage`).

## Fonctionnalités distribuées

### Vue d'ensemble (`Overview`)
- État du compte actif, suivi des paliers Nitro et Boost, compteurs de serveurs et de relations.
- Bascule rapide entre comptes enregistrés, mode privé (masquage visuel des données sensibles), protection silencieuse et centre de notifications en direct.

### Présence & Audio (`Presence`)
- **Identity** — Statut personnalisé, biographie, Rich Presence (`RPC`), tag de serveur et rotation programmée avec variables dynamiques.
- **Spotify** — Synchronisation des paroles en temps réel via `LRCLIB` et la session média locale Windows (`GSMTC`), avec éditeur de séquences personnalisées.
- **Badges** — Consultation détaillée des badges Discord et prévisualisation locale des paliers d'ancienneté.
- **Voice** — Connexion vocale persistante avec reconnexion plafonnée, lecteur audio Opus local et prise en charge du protocole de chiffrement vocal de bout en bout **DAVE** (`@snazzah/davey`).

### Gestion & Automatisation (`Management` · `Automation`)
- **Purge & Cleanup** — Suppression sélective de vos propres messages par salon ou serveur avec aperçu préalable, et nettoyage contrôlé des serveurs ou conversations privées.
- **Cloner** — Sauvegarde locale de l'architecture d'un serveur (rôles, catégories, salons, permissions), comparaison par diff et restauration non destructive par défaut.
- **Auto Responder & Macros** — Règles de réponse conditionnelles avec simulateur hors ligne intégré, et scénarios multi-étapes dotés d'un instantané de profil restaurable en cas d'annulation.
- **Filtrage local & Suivi** — Détection locale de motifs par expressions régulières sécurisées (file de revue manuelle sans signalement automatisé) et suivi passif d'échéances de concours.

### Outils & Réseau (`Tools` · `Network`)
- **Usernames, Vanity & Groups** — Vérification de disponibilité d'identifiants et d'URL personnalisées avec notifications Webhook, gestion de groupes et garde **Sentinel**.
- **Diagnostics réseau** — Cartographie effective des moteurs de transport (session Chromium, client Node HTTP/HTTPS, passerelle WebSocket, flux vocal UDP/DAVE), sondes DNS et TLS à la demande, et routage proxy `HTTP` / `SOCKS5` par compte.

### Journal & Paramètres (`Journal` · `Settings`)
- **Journal** — Flux d'événements en direct, historique d'activité, consommation CPU/RAM par processus Electron et journal d'erreurs local expurgé des secrets (`JSON` / `CSV` / `TXT`).
- **Paramètres** — Profils de performance GPU/CPU, personnalisation visuelle et sonore, coffre multi-comptes chiffré, registre des commandes locales et sauvegardes de configuration vérifiées par empreinte `SHA-256`.

## Aperçu

<p align="center">
  <img src="assets/gallery/04-presence.png" width="49%" alt="Présence et rotation de profil"/>
  <img src="assets/gallery/06-network.png" width="49%" alt="Observabilité réseau et transports"/>
</p>
<p align="center">
  <img src="assets/gallery/07-journal.png" width="49%" alt="Journal temps réel et télémétrie"/>
  <img src="assets/gallery/08-settings-appearance.png" width="49%" alt="Studio Observatoire WebGL2"/>
</p>

## Installation

Prérequis : **Windows 10 ou Windows 11 (64 bits)**.

1. Téléchargez **`OPSEC-Pro-RELEASE-Setup.exe`** et **`OPSEC-Pro-RELEASE-Setup.exe.sha256`** depuis la page [Releases](https://github.com/ellecrydansmesdm/opsec-pro/releases/latest).
2. Vérifiez l'empreinte `SHA-256` du fichier dans PowerShell avant exécution :
   ```powershell
   Get-FileHash .\OPSEC-Pro-RELEASE-Setup.exe -Algorithm SHA256
   ```
   Comparez la valeur obtenue avec le contenu du fichier `.sha256` associé à la release.
3. Lancez `OPSEC-Pro-RELEASE-Setup.exe` pour installer l'application dans votre session utilisateur.

## Activation par licence

L'accès à l'application est protégé par une clé de licence individuelle au format `OPSEC-…` :

- **Premier lancement** : une connexion Internet est requise pour valider la clé en `HTTPS` (`TLS 1.3`) et l'associer à l'identifiant matériel du poste (`HWID`).
- **Poste unique** : chaque licence active est liée à une seule machine à la fois. En cas de changement de matériel ou de réinstallation système, une réinitialisation `HWID` peut être demandée auprès du support.
- **Mode hors ligne** : une fois la licence validée sur le poste, l'application autorise un fonctionnement hors connexion pendant une période maximale de **7 jours** avant d'exiger une nouvelle vérification serveur.

## Sécurité locale & Intégrité

- **Chiffrement au repos** : jetons de session, identifiants de proxys, webhooks et clés d'API tierces sont chiffrés localement par **Windows DPAPI** et ne sont jamais transmis aux serveurs de licence.
- **Cloisonnement d'exécution** : `contextIsolation`, `sandbox` Chromium, politique `Content-Security-Policy` stricte, vérification de l'émetteur sur chaque canal IPC et contrôle de licence côté processus principal.
- **Intégrité binaire** : Electron Fuses verrouillés (`EnableEmbeddedAsarIntegrityValidation`, `OnlyLoadAppFromAsar`, `EnableCookieEncryption`, désactivation de `RunAsNode` et des arguments d'inspection).

## Conditions d'utilisation & Support

L'utilisation d'un client tiers connecté à un compte utilisateur contrevient aux Conditions d'Utilisation de Discord et peut entraîner des mesures de restriction sur les comptes concernés. L'utilisateur demeure seul responsable de l'usage qu'il fait du logiciel et du respect des règles des plateformes tierces.

- **Support, licences et réinitialisation HWID** : [https://discord.gg/W2YgEStqJ4](https://discord.gg/W2YgEStqJ4)
- **Téléchargements officiels** : [https://github.com/ellecrydansmesdm/opsec-pro/releases](https://github.com/ellecrydansmesdm/opsec-pro/releases)
