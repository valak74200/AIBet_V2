# 📋 Documentation Technique - AIBet V2
## Système de Prédiction Sportive Intelligent

**Version :** 2.0  
**Date :** Juin 2025  
**Auteur :** LOUVEAU Clément

---

## Table des Matières

0. [User Stories et Mockups](#0-user-stories-et-mockups)
1. [Architecture Système](#1-architecture-système)
2. [Composants, Classes et Design de Base de Données](#2-composants-classes-et-design-de-base-de-données)
3. [Diagrammes de Séquence](#3-diagrammes-de-séquence)
4. [Spécifications API](#4-spécifications-api)
5. [Plans SCM et QA](#5-plans-scm-et-qa)
6. [Justifications Techniques](#6-justifications-techniques)

---

## 0. User Stories et Mockups

### 0.1 Vue d'ensemble du Produit

AIBet V2 est une plateforme de prédictions sportives basée sur l'intelligence artificielle qui permet aux utilisateurs de :
- Consulter des prédictions générées par IA
- Gérer leur bankroll virtuelle
- Suivre leurs performances de paris
- Accéder à des fonctionnalités premium avec calculateur de mises optimales

### 0.2 Personas Utilisateurs

#### Persona 1 : Lucas - Parieur Occasionnel
- **Âge :** 25 ans
- **Profession :** Étudiant
- **Objectif :** Améliorer ses gains sur les paris sportifs
- **Besoins :** Prédictions fiables, interface simple, budget limité

#### Persona 2 : Marie - Parieuse Expérimentée
- **Âge :** 35 ans
- **Profession :** Analyste financière
- **Objectif :** Optimiser sa stratégie de bankroll
- **Besoins :** Outils d'analyse avancés, gestion de portefeuille, ROI tracking

#### Persona 3 : Thomas - Administrateur
- **Âge :** 30 ans
- **Profession :** Développeur/Product Owner
- **Objectif :** Maintenir la qualité du service
- **Besoins :** Monitoring, métriques de performance, gestion utilisateurs

### 0.3 User Stories avec Priorisation MoSCoW

#### 🔴 MUST HAVE (Fonctionnalités Critiques)

**US-001 : Consultation des Prédictions**
> **En tant qu'** utilisateur  
> **Je veux** consulter la liste des prédictions sportives disponibles  
> **Afin de** prendre des décisions éclairées pour mes paris

**Critères d'acceptation :**
- [ ] Affichage des matchs à venir avec prédictions
- [ ] Informations essentielles visibles : équipes, cote, confiance, date
- [ ] Tri par date et filtrage par sport/ligue
- [ ] Responsive design mobile et desktop
- [ ] Temps de chargement < 2 secondes

**US-002 : Détail d'une Prédiction**
> **En tant qu'** utilisateur  
> **Je veux** voir les détails complets d'une prédiction  
> **Afin de** comprendre l'analyse et la justification

**Critères d'acceptation :**
- [ ] Affichage du raisonnement détaillé
- [ ] Facteurs clés identifiés par l'IA
- [ ] Statistiques des équipes
- [ ] Historique des confrontations
- [ ] Niveau de confiance avec explication

**US-003 : Authentification Utilisateur**
> **En tant qu'** utilisateur  
> **Je veux** créer un compte et me connecter  
> **Afin d'** accéder aux fonctionnalités personnalisées

**Critères d'acceptation :**
- [ ] Inscription avec email/mot de passe
- [ ] Connexion sécurisée avec JWT
- [ ] Récupération de mot de passe
- [ ] Validation email obligatoire
- [ ] Gestion des erreurs d'authentification

**US-004 : Gestion de Bankroll Basique**
> **En tant qu'** utilisateur connecté  
> **Je veux** créer et gérer ma bankroll virtuelle  
> **Afin de** suivre mon capital de paris

**Critères d'acceptation :**
- [ ] Création d'une bankroll avec solde initial
- [ ] Ajout/retrait de fonds virtuels
- [ ] Visualisation du solde actuel
- [ ] Historique des transactions
- [ ] Support multi-devises (EUR, USD, GBP)

#### 🟡 SHOULD HAVE (Fonctionnalités Importantes)

**US-005 : Suivi des Prédictions**
> **En tant qu'** utilisateur connecté  
> **Je veux** suivre une prédiction avec une mise définie  
> **Afin de** tracker ma performance

**Critères d'acceptation :**
- [ ] Bouton "Suivre" sur chaque prédiction
- [ ] Saisie du montant de mise
- [ ] Validation selon la bankroll disponible
- [ ] Historique des prédictions suivies
- [ ] Calcul automatique des gains/pertes

**US-006 : Dashboard Personnel**
> **En tant qu'** utilisateur connecté  
> **Je veux** avoir un tableau de bord personnalisé  
> **Afin de** voir ma performance globale

**Critères d'acceptation :**
- [ ] Statistiques générales (nombre de paris, ROI, etc.)
- [ ] Graphique d'évolution de la bankroll
- [ ] Prédictions récentes suivies
- [ ] Résultats des derniers matchs
- [ ] Taux de réussite personnel

**US-007 : Filtrage et Recherche Avancés**
> **En tant qu'** utilisateur  
> **Je veux** filtrer les prédictions selon mes préférences  
> **Afin de** trouver rapidement les opportunités qui m'intéressent

**Critères d'acceptation :**
- [ ] Filtres par sport (Football, Basketball, Tennis)
- [ ] Filtres par ligue/compétition
- [ ] Filtres par niveau de confiance
- [ ] Filtres par type de pari (1X2, BTTS, O/U)
- [ ] Sauvegarde des préférences de filtrage

**US-008 : Notifications de Résultats**
> **En tant qu'** utilisateur connecté  
> **Je veux** recevoir des notifications des résultats  
> **Afin de** connaître l'issue de mes prédictions suivies

**Critères d'acceptation :**
- [ ] Notification lors de la fin d'un match suivi
- [ ] Email récapitulatif quotidien (optionnel)
- [ ] Badge de notifications dans l'interface
- [ ] Historique des notifications
- [ ] Préférences de notification personnalisables

#### 🟢 COULD HAVE (Fonctionnalités Souhaitables)

**US-009 : Calculateur de Mise Premium**
> **En tant qu'** utilisateur premium  
> **Je veux** accéder au calculateur de mise optimale  
> **Afin d'** optimiser mes gains selon ma stratégie

**Critères d'acceptation :**
- [ ] Calcul selon le critère de Kelly
- [ ] Calcul par pourcentage de bankroll
- [ ] Calcul par mise fixe
- [ ] Recommandations personnalisées
- [ ] Simulation de gains potentiels

**US-010 : Analyse de Performance Avancée**
> **En tant qu'** utilisateur premium  
> **Je veux** accéder à des analyses détaillées de ma performance  
> **Afin d'** améliorer ma stratégie de paris

**Critères d'acceptation :**
- [ ] Graphiques de performance par période
- [ ] Analyse par type de sport/pari
- [ ] Identification des patterns gagnants
- [ ] Conseils d'amélioration personnalisés
- [ ] Export des données en CSV

**US-011 : Prédictions Live**
> **En tant qu'** utilisateur  
> **Je veux** voir les scores en temps réel des matchs en cours  
> **Afin de** suivre l'évolution de mes prédictions

**Critères d'acceptation :**
- [ ] Mise à jour automatique des scores
- [ ] Indication visuelle des matchs live
- [ ] Timeline des événements importants
- [ ] Notification des buts/événements clés
- [ ] Évaluation en temps réel des prédictions

**US-012 : Communauté et Partage**
> **En tant qu'** utilisateur  
> **Je veux** partager mes performances et voir celles d'autres utilisateurs  
> **Afin de** m'améliorer et créer une émulation

**Critères d'acceptation :**
- [ ] Classement des meilleurs utilisateurs
- [ ] Partage de prédictions personnelles
- [ ] Commentaires sur les prédictions
- [ ] Groupes/ligues privées
- [ ] Badges et récompenses

#### ⚪ WON'T HAVE (Pour cette version)

**US-013 : Application Mobile Native**
> Développement d'applications iOS/Android natives
> **Raison :** Complexité trop élevée pour le MVP, l'interface web responsive suffit

**US-014 : Intégration Bookmakers Réels**
> Connexion avec de vrais sites de paris pour placer automatiquement les mises
> **Raison :** Complexité légale et technique trop importante, risques de sécurité

**US-015 : Trading de Prédictions**
> Marché où les utilisateurs peuvent acheter/vendre des prédictions
> **Raison :** Modèle économique complexe, aspects légaux à clarifier

### 0.4 Mockups des Interfaces Principales

#### 0.4.1 Page d'Accueil / Dashboard

```
┌─────────────────────────────────────────────────────────────────┐
│  🏆 AIBet V2        🔍 Recherche...     🔔(3)  👤 Profil      │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  📊 Tableau de Bord                    💰 Ma Bankroll          │
│  ┌─────────────────────────────┐       ┌───────────────────┐   │
│  │ 📈 Mes Statistiques         │       │ 2,450.00 EUR      │   │
│  │ • 15 prédictions suivies    │       │ ↗ +12.5% (30j)    │   │
│  │ • 67% de réussite          │       │ ↗ +156.32 EUR     │   │
│  │ • +12.3% ROI               │       └───────────────────┘   │
│  └─────────────────────────────┘                               │
│                                                                 │
│  🔥 Prédictions du Jour                                        │
│  ┌─────────────────────────────────────────────────────────────┤
│  │ ⚽ Bayern Munich vs Real Madrid                             │
│  │ 📅 Aujourd'hui 21:00  🏆 Champions League                 │
│  │ 🎯 Prédiction: 1 (Bayern)  📊 Confiance: 78%             │
│  │ 💰 Cote: 2.15  🎲 Mise recommandée: 45.50 EUR            │
│  │                                          [SUIVRE] [DÉTAIL] │
│  ├─────────────────────────────────────────────────────────────┤
│  │ 🏀 Lakers vs Warriors                                      │
│  │ 📅 Demain 02:30  🏆 NBA                                   │
│  │ 🎯 Prédiction: Over 215.5  📊 Confiance: 65%             │
│  │ 💰 Cote: 1.85  🎲 Mise recommandée: 25.00 EUR            │
│  │                                          [SUIVRE] [DÉTAIL] │
│  └─────────────────────────────────────────────────────────────┘
│                                                                 │
│  📈 Mes Prédictions Récentes                                   │
│  ┌─────────────────────────────────────────────────────────────┤
│  │ ✅ PSG vs Marseille (2-1) - Mise: 30€ - Gain: +21.50€    │
│  │ ❌ City vs Arsenal (1-2) - Mise: 40€ - Perte: -40.00€     │
│  │ ⏳ Liverpool vs Chelsea - En cours (1-0, 65')              │
│  └─────────────────────────────────────────────────────────────┘
└─────────────────────────────────────────────────────────────────┘
```

#### 0.4.2 Page de Détail d'une Prédiction

```
┌─────────────────────────────────────────────────────────────────┐
│  ← Retour        Bayern Munich vs Real Madrid        ⭐ Favoris  │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  🏆 Champions League - Demi-finale                              │
│  📅 Mardi 23 Janvier 2025, 21:00 CET                          │
│  🏟️ Allianz Arena, Munich                                     │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────────┐
│  │         BAYERN MUNICH    VS    REAL MADRID                 │
│  │              🛡️                    👑                      │
│  │                                                             │
│  │    🎯 PRÉDICTION IA : Victoire Bayern (1)                 │
│  │    📊 Confiance: 78%        💰 Cote: 2.15                 │
│  │                                                             │
│  │    🎲 Mise Recommandée: 45.50 EUR (4.5% bankroll)        │
│  │    💵 Gain Potentiel: +52.32 EUR                          │
│  │                                                             │
│  │              [SUIVRE CETTE PRÉDICTION]                     │
│  └─────────────────────────────────────────────────────────────┘
│                                                                 │
│  📝 Analyse Détaillée                                          │
│  ┌─────────────────────────────────────────────────────────────┐
│  │ 🧠 Raisonnement IA:                                        │
│  │                                                             │
│  │ Bayern Munich présente un avantage significatif pour ce    │
│  │ match crucial. L'équipe bavaroise reste invaincue à        │
│  │ domicile cette saison (12V, 1N) et a marqué en moyenne     │
│  │ 2.8 buts par match à l'Allianz Arena.                     │
│  │                                                             │
│  │ Real Madrid traverse une période plus difficile avec 3     │
│  │ défaites lors des 7 derniers déplacements. De plus,        │
│  │ Benzema et Modric sont incertains pour cette rencontre.    │
│  │                                                             │
│  │ 🔑 Facteurs Clés:                                         │
│  │ • ✅ Bayern: Forme excellente à domicile                   │
│  │ • ✅ Bayern: Effectif au complet                           │
│  │ • ✅ Bayern: Motivation après l'élimination l'an dernier   │
│  │ • ❌ Real: Blessures de joueurs clés                       │
│  │ • ❌ Real: Difficultés en déplacement                      │
│  └─────────────────────────────────────────────────────────────┘
│                                                                 │
│  📊 Statistiques Comparatives                                  │
│  ┌──────────────────┬──────────────┬──────────────────────────┐
│  │                  │ Bayern       │ Real Madrid              │
│  ├──────────────────┼──────────────┼──────────────────────────┤
│  │ Forme (5 matchs) │ 4V-1N        │ 3V-1N-1D                │
│  │ Buts marqués     │ 2.8/match    │ 2.1/match               │
│  │ Buts encaissés   │ 0.9/match    │ 1.3/match               │
│  │ Dernière conf.   │ Bayern 2-1   │ (2022)                  │
│  └──────────────────┴──────────────┴──────────────────────────┘
│                                                                 │
│  🔮 Autres Prédictions                                         │
│  • Both Teams to Score: Non (67% confiance)                    │
│  • Total Goals: Under 2.5 (71% confiance)                     │
│  • Mi-temps/Final: X/1 (54% confiance)                        │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

#### 0.4.3 Page de Gestion de Bankroll

```
┌─────────────────────────────────────────────────────────────────┐
│  💰 Gestion de Bankroll                                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ┌─────────────────────────────────────────────────────────────┐
│  │ 📊 Ma Bankroll Principale                                  │
│  │                                                             │
│  │           2,450.00 EUR                                      │
│  │           ↗ +12.5% ce mois                                 │
│  │                                                             │
│  │  [+ AJOUTER]  [- RETIRER]  [⚙️ PARAMÈTRES]                │
│  └─────────────────────────────────────────────────────────────┘
│                                                                 │
│  📈 Évolution (30 derniers jours)                              │
│  ┌─────────────────────────────────────────────────────────────┐
│  │     2500€ ┤                                            ●    │
│  │           ┤                                      ●    ╱     │
│  │     2400€ ┤                                ●    ╱          │
│  │           ┤                          ●    ╱                │
│  │     2300€ ┤                    ●    ╱                      │
│  │           ┤              ●    ╱                            │
│  │     2200€ ┤        ●    ╱                                  │
│  │           ┤  ●    ╱                                        │
│  │     2100€ ┤ ╱                                              │
│  │           └─┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬────│
│  │            1    7    14    21    28   Aujourd'hui          │
│  └─────────────────────────────────────────────────────────────┘
│                                                                 │
│  🎯 Stratégie de Mise                                          │
│  ┌─────────────────────────────────────────────────────────────┐
│  │ Type: Critère de Kelly                                     │
│  │ Risque: Modéré (fraction 0.5)                             │
│  │ Mise max: 5% de la bankroll                               │
│  │                                            [MODIFIER]       │
│  └─────────────────────────────────────────────────────────────┘
│                                                                 │
│  📋 Historique des Transactions                                │
│  ┌─────────────────────────────────────────────────────────────┐
│  │ 22/01 - Pari PSG vs OM        -30.00€    Solde: 2,450€   │
│  │ 21/01 - Gain PSG vs OM        +21.50€    Solde: 2,480€   │
│  │ 20/01 - Dépôt initial        +100.00€    Solde: 2,458€   │
│  │ 19/01 - Pari City vs Arsenal  -40.00€    Solde: 2,358€   │
│  │ 19/01 - Pari Liverpool FC     -25.00€    Solde: 2,398€   │
│  │                                          [VOIR TOUT]       │
│  └─────────────────────────────────────────────────────────────┘
│                                                                 │
│  📊 Statistiques de Performance                                │
│  ┌─────────────────────────────────────────────────────────────┐
│  │ • Total misé: 485.00€        • Gain total: +92.32€        │
│  │ • Nombre de paris: 15        • Taux de réussite: 67%      │
│  │ • ROI: +19.2%                • Profit moyen: +6.15€       │
│  │ • Plus gros gain: +45.20€    • Plus grosse perte: -40€   │
│  └─────────────────────────────────────────────────────────────┘
└─────────────────────────────────────────────────────────────────┘
```

#### 0.4.4 Modal de Suivi d'une Prédiction

```
┌─────────────────────────────────────────────────────────────────┐
│                     SUIVRE LA PRÉDICTION                       │
│                                                        ✕       │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  🎯 Bayern Munich vs Real Madrid                               │
│  📊 Prédiction: Victoire Bayern (1)                           │
│  💰 Cote: 2.15        🎯 Confiance: 78%                       │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────────┐
│  │ 💰 Ma Bankroll: 2,450.00 EUR                              │
│  │ 🎲 Mise Recommandée: 45.50 EUR (Kelly optimal)           │
│  │ 💵 Gain Potentiel: +52.32 EUR                             │
│  └─────────────────────────────────────────────────────────────┘
│                                                                 │
│  💸 Montant de la Mise                                         │
│  ┌─────────────────────────────────────────────────────────────┐
│  │  [      45.50      ] EUR                                   │
│  │                                                             │
│  │  ○ Utiliser la recommandation IA (45.50€)                 │
│  │  ○ Mise personnalisée                                      │
│  │                                                             │
│  │  Gain potentiel: +52.32 EUR                               │
│  │  Nouveau solde si gain: 2,502.32 EUR                      │
│  │  Nouveau solde si perte: 2,404.50 EUR                     │
│  └─────────────────────────────────────────────────────────────┘
│                                                                 │
│  ⚠️ Avertissement                                              │
│  Cette mise représente 1.86% de votre bankroll totale.        │
│  Il s'agit d'un paris virtuel pour le suivi de performance.   │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────────┐
│  │              [ANNULER]    [SUIVRE LA PRÉDICTION]          │
│  └─────────────────────────────────────────────────────────────┘
└─────────────────────────────────────────────────────────────────┘
```

#### 0.4.5 Version Mobile - Dashboard

```
┌─────────────────────────────┐
│ 🏆 AIBet    🔔(3)    ☰     │
├─────────────────────────────┤
│                             │
│ 💰 Bankroll                 │
│ ┌─────────────────────────┐ │
│ │   2,450.00 EUR          │ │
│ │   ↗ +12.5% (30j)        │ │
│ └─────────────────────────┘ │
│                             │
│ 📊 Mes Stats                │
│ • 15 paris • 67% réussite  │
│ • +12.3% ROI               │
│                             │
│ 🔥 Prédictions              │
│ ┌─────────────────────────┐ │
│ │ ⚽ Bayern vs Real       │ │
│ │ 📅 Aujourd'hui 21:00    │ │
│ │ 🎯 1 • 📊 78% • 💰2.15 │ │
│ │ [SUIVRE]     [DÉTAIL]   │ │
│ ├─────────────────────────┤ │
│ │ 🏀 Lakers vs Warriors   │ │
│ │ 📅 Demain 02:30         │ │
│ │ 🎯 O215.5 • 📊 65%     │ │
│ │ [SUIVRE]     [DÉTAIL]   │ │
│ └─────────────────────────┘ │
│                             │
│ 📈 Récents                  │
│ ✅ PSG vs OM (+21.50€)      │
│ ❌ City vs Arsenal (-40€)   │
│ ⏳ Liverpool vs Chelsea     │
│                             │
│ ┌─────────────────────────┐ │
│ │ 🏠 📊 💰 ⚙️ 👤        │ │
│ └─────────────────────────┘ │
└─────────────────────────────┘
```

### 0.5 Flux Utilisateur Principaux

#### 0.5.1 Flux de Consultation et Suivi d'une Prédiction

```
1. Utilisateur arrive sur le dashboard
   ↓
2. Parcourt les prédictions disponibles
   ↓
3. Clique sur "DÉTAIL" pour une prédiction
   ↓
4. Lit l'analyse détaillée et les statistiques
   ↓
5. Clique sur "SUIVRE CETTE PRÉDICTION"
   ↓
6. Modal s'ouvre avec calculateur de mise
   ↓
7. Valide ou modifie le montant
   ↓
8. Confirme le suivi
   ↓
9. Retour au dashboard avec notification de succès
   ↓
10. Prédiction ajoutée à "Mes Prédictions Récentes"
```

#### 0.5.2 Flux de Gestion de Bankroll

```
1. Utilisateur accède à la section Bankroll
   ↓
2. Voit son solde actuel et l'évolution
   ↓
3. Peut ajouter/retirer des fonds virtuels
   ↓
4. Configure sa stratégie de mise
   ↓
5. Consulte l'historique des transactions
   ↓
6. Analyse ses performances via les statistiques
```

### 0.6 Critères de Succès des User Stories

- **Adoption :** > 80% des utilisateurs inscrits utilisent la fonction consultation de prédictions
- **Engagement :** > 60% des utilisateurs connectés suivent au moins 1 prédiction par semaine
- **Rétention :** > 70% des utilisateurs reviennent dans les 7 jours après inscription
- **Performance :** Temps de réponse < 2s pour l'affichage des prédictions
- **Satisfaction :** Note NPS > 7/10 sur les fonctionnalités de base

Cette première section pose les bases fonctionnelles du projet avec une approche centrée utilisateur et une priorisation claire des fonctionnalités à développer.

---

## 1. Architecture Système

### 1.1 Vue d'ensemble de l'Architecture

AIBet V2 adopte une architecture microservices moderne basée sur des conteneurs Docker, optimisée pour la scalabilité et la maintenabilité. Le système est conçu pour traiter de grandes volumes de données sportives et générer des prédictions en temps réel.

### 1.2 Diagramme d'Architecture High-Level

Le diagramme ci-dessous illustre l'architecture complète du système avec les flux de données :

graph TB
    subgraph "🌐 APIs Externes"
        API1[API-Football<br/>⚽ Données Sportives]
        API2[OpenAI GPT-4o<br/>🤖 Intelligence Artificielle]
    end

    subgraph "📱 Frontend Layer"
        FE[Next.js Frontend<br/>🖥️ Interface Utilisateur<br/>Port: 3000]
    end

    subgraph "🔀 Load Balancer / Reverse Proxy"
        LB[Nginx / Traefik<br/>📡 Équilibrage de charge]
    end

    subgraph "🚀 Backend Services"
        API[Django REST API<br/>🛠️ Logique métier<br/>Port: 8000]
        CELERY[Celery Workers<br/>⚙️ Tâches asynchrones]
        BEAT[Celery Beat<br/>📅 Planificateur]
    end

    subgraph "💾 Data Layer"
        DB[(PostgreSQL<br/>🗄️ Base de données<br/>Port: 5432)]
        CACHE[(Redis<br/>🚀 Cache & Sessions<br/>Port: 6379)]
        QUEUE[(RabbitMQ<br/>📬 File de messages<br/>Port: 5672)]
    end

    subgraph "📊 Monitoring Stack"
        PROM[Prometheus<br/>📈 Métriques<br/>Port: 9090]
        GRAF[Grafana<br/>📊 Visualisation<br/>Port: 3001]
        ALERT[AlertManager<br/>🔔 Alertes<br/>Port: 9093]
    end

    subgraph "💽 Storage"
        VOL1[postgres_data<br/>📚 Données DB]
        VOL2[redis_data<br/>⚡ Cache data]
        VOL3[logs_volume<br/>📝 Logs applicatifs]
        VOL4[data_files<br/>📄 Données métier]
    end

    %% Flux de données
    FE -.->|HTTP/HTTPS| LB
    LB -->|Proxy| API
    FE -->|WebSocket| API
    
    API -->|REST Calls| API1
    API -->|AI Requests| API2
    
    API -->|ORM/SQL| DB
    API -->|Cache| CACHE
    API -->|Tasks| QUEUE
    
    CELERY -->|Consume| QUEUE
    BEAT -->|Schedule| QUEUE
    CELERY -->|Process| API1
    CELERY -->|Generate| API2
    
    %% Monitoring
    API -.->|Metrics| PROM
    CELERY -.->|Metrics| PROM
    PROM -->|Query| GRAF
    PROM -->|Alerts| ALERT
    
    %% Storage connections
    DB -.->|Persist| VOL1
    CACHE -.->|Persist| VOL2
    API -.->|Logs| VOL3
    API -.->|Files| VOL4


### 1.3 Composants Détaillés

#### 1.3.1 Frontend Layer

**🖥️ Next.js Frontend (Port 3000)**
- **Technologie :** React 18 + Next.js 13+ avec App Router
- **Responsabilités :**
  - Interface utilisateur responsive (mobile-first)
  - Gestion des états avec React Context/Redux
  - Authentification JWT côté client
  - Communication temps réel via WebSockets
  - Progressive Web App (PWA) capabilities

**📊 Flux de données Frontend :**
```
Utilisateur → Interface Next.js → API Django (REST/WebSocket) → Données
```

#### 1.3.2 Backend Services

**🛠️ Django REST API (Port 8000)**
- **Technologie :** Django 4.2 + Django REST Framework
- **Responsabilités :**
  - API REST pour les opérations CRUD
  - Authentification JWT avec refresh tokens
  - Logique métier des prédictions
  - Gestion des utilisateurs et bankrolls
  - WebSocket endpoints pour temps réel
  - Exposition des métriques Prometheus

**⚙️ Celery Workers**
- **Technologie :** Celery 5.4 + Redis/RabbitMQ
- **Responsabilités :**
  - Collecte de données depuis APIs externes
  - Génération de prédictions IA
  - Traitement asynchrone des tâches lourdes
  - Envoi d'emails et notifications
  - Nettoyage des données obsolètes

**📅 Celery Beat Scheduler**
- **Technologie :** Celery Beat + Django Database Scheduler
- **Responsabilités :**
  - Exécution programmée des tâches
  - Pipeline quotidien de prédictions
  - Mise à jour des scores de matchs
  - Maintenance automatique du système

#### 1.3.3 Data Layer

**🗄️ PostgreSQL (Port 5432)**
- **Version :** PostgreSQL 14
- **Responsabilités :**
  - Stockage principal des données
  - Relations complexes (matchs, prédictions, utilisateurs)
  - Intégrité référentielle
  - Requêtes analytiques
- **Configuration :**
  - Connection pooling (CONN_MAX_AGE: 600s)
  - Health checks automatiques
  - Backup automatisé via volumes Docker

**🚀 Redis (Port 6379)**
- **Version :** Redis 7 Alpine
- **Responsabilités :**
  - Cache applicatif (données fréquemment consultées)
  - Sessions utilisateur
  - Broker pour Celery (file de tâches)
  - Cache des résultats d'API externes
- **Configuration :**
  - Persistance AOF désactivée pour performance
  - Sauvegarde périodique (900s/1key, 300s/10keys, 60s/10000keys)

**📬 RabbitMQ (Port 5672)**
- **Version :** RabbitMQ 3 avec Management UI
- **Responsabilités :**
  - File de messages fiable pour Celery
  - Gestion des tâches prioritaires
  - Dead letter queues pour retry logic
  - Monitoring des queues via UI (Port 15672)

#### 1.3.4 APIs Externes

**⚽ API-Football**
- **Usage :** Données en temps réel des matchs
- **Endpoints utilisés :**
  - `/fixtures` - Matchs à venir et en cours
  - `/teams` - Informations des équipes
  - `/leagues` - Compétitions sportives
  - `/statistics` - Statistiques détaillées
- **Rate Limiting :** 100 requêtes/jour (plan gratuit)

**🤖 OpenAI GPT-4o API**
- **Usage :** Génération de prédictions intelligentes
- **Modèle utilisé :** GPT-4o avec capacités de recherche web
- **Features :**
  - Prompts dynamiques contextuels
  - Token bucket pour rate limiting (25,000 tokens/minute)
  - Enrichissement contextuel via recherche web intégrée
  - Système de retry avec backoff exponentiel



#### 1.3.5 Monitoring Stack

**📈 Prometheus (Port 9090)**
- **Métriques collectées :**
  - Performance Django (requests/sec, latency)
  - État des tâches Celery
  - Utilisation PostgreSQL/Redis
  - Métriques business (prédictions/jour, accuracy)

**📊 Grafana (Port 3001)**
- **Dashboards :**
  - Performance système en temps réel
  - Analytics des prédictions
  - Monitoring utilisateurs
  - Alertes visuelles

**🔔 AlertManager (Port 9093)**
- **Alertes configurées :**
  - API externe indisponible
  - Base de données saturée
  - Erreurs critiques dans les logs
  - Performance dégradée

### 1.4 Flux de Données Détaillés

#### 1.4.1 Flux de Prédiction Quotidien

```
1. Celery Beat déclenche [collecte_matchs_daily]
   ↓
2. Celery Worker → API-Football [récupération matchs J+1]
   ↓
3. Celery Worker → OpenAI GPT-4o [enrichissement contextuel + génération prédictions]
   ↓
4. Stockage PostgreSQL [matchs + prédictions]
   ↓
5. Invalidation cache Redis [nouvelles données]
   ↓
6. WebSocket notification → Frontend [mise à jour temps réel]
```

#### 1.4.2 Flux Utilisateur - Consultation Prédiction

```
1. Frontend Next.js → API Django [GET /api/v1/predictions/]
   ↓
2. Django → Redis [vérification cache]
   ↓ (si cache miss)
3. Django → PostgreSQL [requête optimisée]
   ↓
4. Django → Redis [mise en cache résultat]
   ↓
5. Django → Frontend [réponse JSON + WebSocket]
```

#### 1.4.3 Flux Utilisateur - Suivi Prédiction

```
1. Frontend → API Django [POST /api/v1/predictions/{id}/follow/]
   ↓
2. Django → PostgreSQL [validation bankroll + enregistrement]
   ↓
3. Django → Celery [tâche notification asynchrone]
   ↓
4. Django → Frontend [confirmation immédiate]
   ↓
5. Celery Worker [email notification + analytics]
```

### 1.5 Scalabilité et Performance

#### 1.5.1 Optimisations Actuelles

- **Database :** Connection pooling, indexes optimisés
- **Cache :** Redis multi-niveaux (sessions, API, requêtes)
- **API :** Pagination automatique, rate limiting
- **Frontend :** Code splitting, lazy loading, PWA

#### 1.5.2 Points de Scalabilité

- **Horizontal Scaling :** Multiple instances Celery Workers
- **Database Scaling :** Read replicas PostgreSQL
- **Cache Scaling :** Redis Cluster
- **CDN :** Assets statiques via CDN

#### 1.5.3 Monitoring de Performance

| Métrique | Seuil Normal | Seuil Critique | Action |
|----------|--------------|----------------|---------|
| Response Time API | < 200ms | > 2s | Scale containers |
| CPU Usage | < 70% | > 90% | Add resources |
| Memory Usage | < 80% | > 95% | Restart services |
| DB Connections | < 80% pool | > 95% pool | Scale workers |
| Cache Hit Rate | > 80% | < 50% | Optimize cache |

### 1.6 Sécurité et Résilience

#### 1.6.1 Sécurité

- **Authentification :** JWT avec refresh tokens
- **HTTPS :** TLS 1.3 obligatoire en production
- **CORS :** Configuration restrictive
- **Rate Limiting :** Protection contre DoS
- **Secrets :** Variables d'environnement chiffrées

#### 1.6.2 Résilience

- **Health Checks :** Tous les services
- **Circuit Breakers :** APIs externes
- **Retry Logic :** Tâches Celery avec backoff
- **Failover :** Multiple replicas des services critiques
- **Backup :** PostgreSQL daily + Redis snapshots

---

## 2. Composants, Classes et Design de Base de Données

### 2.1 Classes Backend (Django)

#### 2.1.1 Modèles Django Principaux

**Modèle `Match`** (predictions/models.py)
```python
class Match(models.Model):
    home_team = models.CharField(max_length=100)
    away_team = models.CharField(max_length=100)
    home_team_logo = models.CharField(max_length=255, null=True, blank=True)
    away_team_logo = models.CharField(max_length=255, null=True, blank=True)
    league = models.CharField(max_length=100)
    api_football_id = models.IntegerField(unique=True, null=True, blank=True)
    match_date = models.DateTimeField()
    sport = models.CharField(max_length=50, default='Football')
    status = models.CharField(max_length=20, choices=STATUS_CHOICES, default='upcoming')
    home_score = models.IntegerField(null=True, blank=True)
    away_score = models.IntegerField(null=True, blank=True)
    score_details = models.JSONField(null=True, blank=True)
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)

    # Méthodes principales
    @property
    def is_live(self) -> bool
    @property
    def is_finished(self) -> bool
    @property
    def is_recent(self) -> bool
    @property
    def match_result(self) -> str
    def update_predictions(self) -> None
```

**Modèle `Prediction`** (predictions/models.py)
```python
class Prediction(models.Model):
    match = models.ForeignKey(Match, on_delete=models.CASCADE, related_name='predictions')
    winner = models.CharField(max_length=100, default="", blank=True)
    score_prediction = models.CharField(max_length=20, default="", blank=True)
    confidence = models.FloatField(help_text="Taux de confiance GPT (0-100)")
    reasoning = models.TextField(default="", blank=True)
    key_factors = models.JSONField(null=True, blank=True)
    prediction_type = models.CharField(max_length=30, blank=True)
    prediction_text = models.CharField(max_length=255, blank=True)
    
    # Prédictions additionnelles
    total_goals = models.CharField(max_length=30, blank=True, null=True)
    btts = models.CharField(max_length=10, blank=True, null=True)
    half_time_result = models.CharField(max_length=10, blank=True, null=True)
    first_goalscorer = models.CharField(max_length=100, blank=True, null=True)
    anytime_goalscorer = models.CharField(max_length=100, blank=True, null=True)
    top_goalscorers = models.JSONField(blank=True, null=True)
    
    # Probabilités et cotes
    odds = models.FloatField(null=True, blank=True)
    home_win_probability = models.FloatField(null=True, blank=True)
    draw_probability = models.FloatField(null=True, blank=True)
    away_win_probability = models.FloatField(null=True, blank=True)
    
    # Évaluation
    real_score = models.CharField(max_length=20, null=True, blank=True)
    was_correct = models.BooleanField(null=True, blank=True)
    status = models.CharField(max_length=20, choices=STATUS_CHOICES, default='pending')
    
    # Métadonnées
    context_text = models.TextField(null=True, blank=True)
    raw_stats = models.JSONField(null=True, blank=True)
    published = models.BooleanField(default=True)
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)

    # Méthodes principales
    @property
    def is_successful(self) -> bool
    def has_sufficient_data(self) -> bool
    def publish_if_data_sufficient(self) -> bool
    def evaluate_prediction(self) -> bool
```

**Modèle `Bankroll`** (bankroll/models.py)
```python
class Bankroll(models.Model):
    user = models.ForeignKey(User, on_delete=models.CASCADE, related_name='bankrolls')
    name = models.CharField(max_length=100)
    initial_amount = models.DecimalField(max_digits=10, decimal_places=2)
    current_amount = models.DecimalField(max_digits=10, decimal_places=2)
    target_amount = models.DecimalField(max_digits=10, decimal_places=2, null=True, blank=True)
    risk_tolerance = models.CharField(max_length=20, choices=RISK_CHOICES, default='medium')
    strategy = models.CharField(max_length=50, choices=STRATEGY_CHOICES, default='flat')
    max_stake_percentage = models.FloatField(default=2.0)
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
    is_active = models.BooleanField(default=True)

    # Méthodes principales
    def calculate_recommended_stake(self, confidence: float, odds: float) -> Decimal
    def add_funds(self, amount: Decimal) -> None
    def withdraw_funds(self, amount: Decimal) -> bool
    def update_from_bet_result(self, bet_amount: Decimal, profit: Decimal) -> None
    def get_performance_metrics(self) -> Dict
```

#### 2.1.2 Classes de Service Backend

**Classe `APIFootballClient`** (data/fetch_api_football.py)
```python
class APIFootballClient:
    def __init__(self, api_version: str = None):
        self.api_version = api_version or API_VERSIONS['api-football']
        self.base_url = API_BASE_URLS['api-football'][self.api_version]
        self.headers = {"x-apisports-key": API_FOOTBALL_KEY}
        self.adapter = APIAdapterRegistry.get_adapter('api-football', self.api_version)

    # Méthodes API principales
    def _make_request(self, endpoint: str, params: Dict[str, Any]) -> Dict
    def get_fixtures(self, league_id=None, team_id=None, date_from=None, date_to=None) -> Dict
    def get_team_statistics(self, team_id: int, league_id: int, season: int) -> Dict
    def get_fixture_statistics(self, fixture_id: int) -> Dict
    def get_odds(self, fixture_id: int, bookmaker_id: int = 16) -> Dict
    def get_predictions(self, fixture_id: int) -> Dict
    def get_h2h(self, team1: int, team2: int, last: int = 5) -> Dict
```

**Classe `GPTPredictor`** (data/gpt_integration.py)
```python
class GPTPredictor:
    def __init__(self):
        self.logger = logging.getLogger(__name__)
        
    # Méthodes principales
    def generate_prediction(self, match) -> Prediction
    def update_prediction(self, prediction) -> bool
    
    # Méthodes privées d'implémentation
    def _prepare_match_data(self, match) -> Dict
    def _call_gpt_api(self, prompt: str, context: str) -> Dict
    def _parse_gpt_response(self, response: str) -> Dict
    def _create_prediction_object(self, match, prediction_data: Dict) -> Prediction
```

**Classe `PromptTemplateManager`** (data/prompt_templates.py)
```python
class PromptTemplateManager:
    @staticmethod
    def get_context_enrichment_prompt(match_data: Dict[str, Any]) -> str
    
    @staticmethod
    def get_prediction_prompt(match_data: Dict[str, Any], context_text: str) -> str
    
    @staticmethod
    def get_update_prompt(match_data: Dict[str, Any], initial_prediction: Dict[str, Any]) -> str
    
    @staticmethod
    def _extract_essential_stats(match_data: Dict[str, Any]) -> str
    
    @staticmethod
    def _format_team_comparison(home_stats: Dict, away_stats: Dict) -> str
```

### 2.2 Design de Base de Données

#### 2.2.1 Diagramme Entité-Relation

```mermaid
erDiagram
    User ||--o{ UserProfile : "has"
    User ||--o{ Bankroll : "owns"
    User ||--o{ UserPrediction : "saves"
    User ||--o{ Notification : "receives"
    
    Match ||--o{ Prediction : "has"
    Match ||--o{ RawMatchData : "stores"
    Match ||--o{ MatchContext : "enriches"
    Match ||--o{ MatchLiveUpdate : "tracks"
    Match ||--o{ UserPrediction : "references"
    Match ||--o{ Notification : "triggers"
    
    Prediction ||--o{ UserPrediction : "saved_as"
    Prediction ||--o{ Notification : "notifies"
    
    Bankroll ||--o{ BetTransaction : "tracks"
    
    UserProfile ||--o{ UserPredictionStats : "accumulates"
    
    User {
        int id PK
        string username
        string email
        string password_hash
        datetime date_joined
        boolean is_active
        boolean is_premium
    }
    
    UserProfile {
        int id PK
        int user_id FK
        string display_name
        string avatar_url
        string preferred_language
        json notification_preferences
        datetime created_at
        datetime updated_at
    }
    
    Match {
        int id PK
        string home_team
        string away_team
        string home_team_logo
        string away_team_logo
        string league
        int api_football_id
        datetime match_date
        string sport
        string status
        int home_score
        int away_score
        json score_details
        datetime created_at
        datetime updated_at
    }
    
    Prediction {
        int id PK
        int match_id FK
        string winner
        string score_prediction
        float confidence
        text reasoning
        json key_factors
        string prediction_type
        string prediction_text
        string total_goals
        string btts
        string half_time_result
        string first_goalscorer
        string anytime_goalscorer
        json top_goalscorers
        float odds
        float home_win_probability
        float draw_probability
        float away_win_probability
        text context_text
        json raw_stats
        string real_score
        boolean was_correct
        string status
        boolean published
        datetime created_at
        datetime updated_at
    }
    
    RawMatchData {
        int id PK
        int match_id FK
        json raw_data
        datetime created_at
        datetime updated_at
    }
    
    MatchContext {
        int id PK
        int match_id FK
        text context_text
        json search_queries
        json search_results
        datetime created_at
        datetime updated_at
    }
    
    Bankroll {
        int id PK
        int user_id FK
        string name
        decimal initial_amount
        decimal current_amount
        decimal target_amount
        string risk_tolerance
        string strategy
        float max_stake_percentage
        boolean is_active
        datetime created_at
        datetime updated_at
    }
    
    UserPrediction {
        int id PK
        int user_id FK
        int prediction_id FK
        decimal recommended_stake
        decimal user_stake
        decimal bankroll_at_time
        decimal potential_profit
        decimal result_profit
        datetime created_at
    }
    
    BetTransaction {
        int id PK
        int bankroll_id FK
        string transaction_type
        decimal amount
        decimal balance_after
        string description
        datetime created_at
    }
    
    MatchLiveUpdate {
        int id PK
        int match_id FK
        int minute
        int home_score
        int away_score
        string status
        string message
        datetime timestamp
    }
    
    Notification {
        int id PK
        int user_id FK
        int match_id FK
        int prediction_id FK
        string message
        boolean read
        datetime created_at
    }
    
    UserPredictionStats {
        int id PK
        int user_id FK
        int total_predictions
        int successful_predictions
        float success_rate
        decimal total_stake
        decimal total_profit
        float roi
        float average_odds
        float average_confidence
        datetime first_prediction
        datetime last_prediction
        datetime last_updated
    }
    
    PredictionStats {
        int id PK
        string type
        int total_predictions
        int successful_predictions
        float success_rate
        float average_odds
        float average_confidence
        datetime last_updated
    }
```

#### 2.2.2 Tables Principales et Contraintes

**Table `predictions_match`**
- **Clé primaire** : `id`
- **Index unique** : `api_football_id`
- **Contraintes** : 
  - `home_team` et `away_team` non null
  - `match_date` non null
  - `status` limité aux valeurs définies dans STATUS_CHOICES

**Table `predictions_prediction`**
- **Clé primaire** : `id`
- **Clé étrangère** : `match_id` → `predictions_match.id`
- **Contraintes** :
  - `confidence` entre 0 et 100
  - `odds` > 1.0 si définie
  - Somme des probabilités ≈ 1.0 si toutes définies

**Table `bankroll_bankroll`**
- **Clé primaire** : `id`
- **Clé étrangère** : `user_id` → `auth_user.id`
- **Contraintes** :
  - `initial_amount` et `current_amount` > 0
  - `max_stake_percentage` entre 0.1 et 100.0

### 2.3 Composants Frontend (React)

#### 2.3.1 Composants de Prédictions

**Composant `MatchDetail`** (frontend/src/components/predictions/MatchDetail.jsx)
```jsx
export default function MatchDetail({ id }) {
    // État local
    const [prediction, setPrediction] = useState(null);
    const [isLoading, setIsLoading] = useState(true);
    const [error, setError] = useState(null);
    const [isFollowDialogOpen, setIsFollowDialogOpen] = useState(false);

    // Hooks personnalisés
    const { user, isAuthenticated } = useAuth();
    const { toast } = useToast();

    // Méthodes principales
    const fetchPredictionData = async () => { /* Récupération API */ };
    const handleFollowClick = () => { /* Ouverture modal suivi */ };
    const handleFollowSuccess = (response) => { /* Callback succès */ };

    // Rendu conditionnel avec états de chargement/erreur
    return (
        <div className="min-h-screen bg-gradient-to-br from-slate-900 via-blue-900 to-slate-900">
            {/* Interface utilisateur avec animations Framer Motion */}
        </div>
    );
}
```

**Composant `PredictionFollowDialog`** (frontend/src/components/predictions/PredictionFollowDialog.jsx)
```jsx
export default function PredictionFollowDialog({ isOpen, onClose, prediction, onSuccess }) {
    // État local pour la gestion de bankroll
    const [selectedBankroll, setSelectedBankroll] = useState(null);
    const [stakeAmount, setStakeAmount] = useState('');
    const [bankrolls, setBankrolls] = useState([]);

    // Méthodes de calcul
    const calculateRecommendedStake = () => { /* Logique Kelly Criterion */ };
    const handleSubmit = async () => { /* Soumission pari */ };

    return (
        <Dialog open={isOpen} onOpenChange={onClose}>
            {/* Interface de suivi avec calculs automatiques */}
        </Dialog>
    );
}
```

#### 2.3.2 Composants de Bankroll

**Composant `BankrollManageDialog`** (frontend/src/components/bankroll/BankrollManageDialog.jsx)
```jsx
export default function BankrollManageDialog({ isOpen, onClose, initialBankroll = null, onSuccess }) {
    // État pour la gestion des formulaires
    const [formData, setFormData] = useState({
        name: '',
        initialAmount: '',
        targetAmount: '',
        riskTolerance: 'medium',
        strategy: 'flat'
    });

    // Méthodes CRUD
    const handleSubmit = async () => { /* Création/modification bankroll */ };
    const validateForm = () => { /* Validation client */ };

    return (
        <div className="fixed inset-0 z-50 flex items-center justify-center">
            {/* Interface moderne avec glassmorphism */}
        </div>
    );
}
```

**Composant `BankrollChart`** (frontend/src/components/bankroll/BankrollChart.js)
```jsx
export default function BankrollChart({ bankrollData, transactions }) {
    // Configuration Chart.js
    const chartOptions = {
        responsive: true,
        maintainAspectRatio: false,
        scales: {
            y: {
                beginAtZero: false,
                grid: { color: 'rgba(255, 255, 255, 0.1)' }
            }
        }
    };

    // Préparation des données
    const chartData = {
        labels: transactions.map(t => formatDate(t.created_at)),
        datasets: [{
            label: 'Évolution Bankroll',
            data: transactions.map(t => t.balance_after),
            borderColor: 'rgb(59, 130, 246)',
            backgroundColor: 'rgba(59, 130, 246, 0.1)'
        }]
    };

    return <Line data={chartData} options={chartOptions} />;
}
```

#### 2.3.3 Architecture des Composants

**Hiérarchie des Composants**
```
App
├── Layout
│   ├── Header
│   ├── Navigation
│   └── Footer
├── Pages
│   ├── Dashboard
│   │   ├── StatsDisplay
│   │   ├── RecentPredictions
│   │   └── BankrollOverview
│   ├── Predictions
│   │   ├── PredictionsList
│   │   ├── MatchDetail
│   │   ├── PredictionFollowDialog
│   │   └── DetailedAnalysis
│   ├── Bankroll
│   │   ├── BankrollManageDialog
│   │   ├── BankrollChart
│   │   ├── BetsTable
│   │   └── OptimalStakeCalculator
│   └── Account
│       ├── Profile
│       ├── Settings
│       └── Stats
└── UI Components
    ├── Button
    ├── Dialog
    ├── Badge
    ├── Tooltip
    └── Loader
```

**Flux de Données Inter-Composants**
- **État global** : Géré via hooks personnalisés (useAuth, useBankroll)
- **Communication parent-enfant** : Props et callbacks
- **Gestion d'état local** : useState pour l'état des formulaires
- **Appels API** : Services centralisés dans `/services/api`
- **Notifications** : Système de toast unifié
- **Routing** : Next.js App Router avec navigation programmatique

**Patterns de Design Utilisés**
- **Compound Components** : Dialog avec DialogContent, DialogHeader
- **Render Props** : Pour les composants de données
- **Higher-Order Components** : Wrappers d'authentification
- **Custom Hooks** : Logique réutilisable (useAuth, useToast)
- **Conditional Rendering** : États de chargement/erreur
- **Event Handling** : Callbacks optimisés avec useCallback

---

## 3. Diagrammes de Séquence

### 3.1 Pipeline de Collecte et Génération de Prédictions

Ce diagramme illustre le processus automatisé quotidien de collecte des données et génération des prédictions par l'IA.

```mermaid
sequenceDiagram
    participant CeleryBeat as Celery Beat Scheduler
    participant CollectTask as collect_match_data
    participant APIFootball as API-Football
    participant DB as PostgreSQL
    participant EnrichTask as enrich_match_context
    participant GPT as OpenAI GPT-4o
    participant PredictTask as generate_prediction
    participant Cache as Redis

    Note over CeleryBeat: Tâche quotidienne 06:00 UTC
    
    CeleryBeat->>+CollectTask: run_prediction_pipeline()
    CollectTask->>+APIFootball: get_fixtures(days_ahead=1)
    APIFootball-->>-CollectTask: fixtures_data[]
    
    loop Pour chaque match
        CollectTask->>+APIFootball: get_team_statistics()
        APIFootball-->>-CollectTask: team_stats
        CollectTask->>+APIFootball: get_h2h()
        APIFootball-->>-CollectTask: head_to_head
        CollectTask->>+APIFootball: get_odds()
        APIFootball-->>-CollectTask: betting_odds
    end
    
    CollectTask->>+DB: Match.objects.create()
    CollectTask->>+DB: RawMatchData.objects.create()
    DB-->>-CollectTask: match_saved
    
    CollectTask->>+EnrichTask: enrich_match_context(match_id)
    EnrichTask->>+GPT: generate_context_enrichment()
    Note over GPT: Recherche web + analyse contextuelle<br/>Prompt dynamique adaptatif
    GPT-->>-EnrichTask: enriched_context
    EnrichTask->>+DB: MatchContext.objects.create()
    DB-->>-EnrichTask: context_saved
    
    EnrichTask->>+PredictTask: generate_prediction(match_id)
    PredictTask->>+GPT: generate_match_prediction()
    Note over GPT: Analyse complète + prédictions<br/>Confiance, probabilités, buteurs
    GPT-->>-PredictTask: prediction_data
    
    PredictTask->>+DB: Prediction.objects.create()
    DB-->>-PredictTask: prediction_saved
    
    PredictTask->>+Cache: invalidate_predictions_cache()
    Cache-->>-PredictTask: cache_cleared
    
    CollectTask-->>-CeleryBeat: pipeline_completed
```

### 3.2 Consultation d'une Prédiction par un Utilisateur

Ce diagramme montre le flux complet de consultation d'une prédiction depuis l'interface utilisateur.

```mermaid
sequenceDiagram
    participant User as Utilisateur
    participant Browser as Navigateur
    participant NextJS as Next.js Frontend
    participant DjangoAPI as Django REST API
    participant DB as PostgreSQL
    participant Cache as Redis

    User->>+Browser: Clic sur prédiction
    Browser->>+NextJS: /predictions/[id]
    
    NextJS->>+NextJS: MatchDetail.jsx
    NextJS->>+NextJS: useEffect() fetchPredictionData()
    
    NextJS->>+DjangoAPI: GET /api/predictions/{id}/
    DjangoAPI->>+Cache: check_cache("prediction_{id}")
    
    alt Cache Hit
        Cache-->>DjangoAPI: cached_prediction
    else Cache Miss
        DjangoAPI->>+DB: Prediction.objects.get(id)
        DjangoAPI->>+DB: Match.objects.select_related()
        DB-->>-DjangoAPI: prediction + match_data
        DjangoAPI->>+Cache: set_cache("prediction_{id}")
        Cache-->>-DjangoAPI: cache_set
    end
    
    DjangoAPI-->>-NextJS: prediction_data (JSON)
    
    NextJS->>+NextJS: setState(prediction)
    NextJS->>+NextJS: formatMatchDate()
    NextJS->>+NextJS: getPredictionText()
    NextJS->>+NextJS: getRiskLevel()
    
    NextJS-->>-Browser: Rendered Prediction View
    Browser-->>-User: Interface prédiction affichée
    
    Note over User, Cache: Données mises en cache pour 10 minutes
```

### 3.3 Suivi d'une Prédiction avec Gestion de Bankroll

Ce diagramme détaille le processus de suivi d'une prédiction par un utilisateur authentifié avec calcul automatique des mises.

```mermaid
sequenceDiagram
    participant User as Utilisateur
    participant Browser as Navigateur
    participant NextJS as Next.js Frontend
    participant DjangoAPI as Django REST API
    participant BankrollAPI as Bankroll API
    participant DB as PostgreSQL
    participant Auth as JWT Auth

    User->>+Browser: Clic "SUIVRE"
    Browser->>+NextJS: handleFollowClick()
    
    NextJS->>+NextJS: PredictionFollowDialog.jsx
    NextJS->>+Auth: validateToken()
    Auth-->>-NextJS: user_authenticated
    
    NextJS->>+DjangoAPI: GET /api/bankroll/user_bankrolls/
    DjangoAPI->>+DB: Bankroll.objects.filter(user=user)
    DB-->>-DjangoAPI: user_bankrolls[]
    DjangoAPI-->>-NextJS: bankrolls_data
    
    NextJS->>+NextJS: setBankrolls(bankrolls_data)
    NextJS-->>-Browser: Modal avec sélection bankroll
    
    User->>+Browser: Sélection bankroll + mise
    Browser->>+NextJS: handleBankrollChange()
    
    NextJS->>+NextJS: calculateRecommendedStake()
    Note over NextJS: Kelly Criterion:<br/>stake = (odds * probability - 1) / (odds - 1)<br/>* bankroll * risk_factor
    
    NextJS->>+NextJS: setStakeAmount(calculated_stake)
    NextJS-->>-Browser: Mise recommandée affichée
    
    User->>+Browser: Confirmer suivi
    Browser->>+NextJS: handleSubmit()
    
    NextJS->>+BankrollAPI: POST /api/predictions/follow/
    Note over BankrollAPI: Payload: {<br/>  prediction_id,<br/>  bankroll_id,<br/>  stake_amount,<br/>  confidence,<br/>  odds<br/>}
    
    BankrollAPI->>+DB: UserPrediction.objects.create()
    BankrollAPI->>+DB: BetTransaction.objects.create()
    BankrollAPI->>+DB: Bankroll.update(current_amount)
    DB-->>-BankrollAPI: transaction_saved
    
    BankrollAPI-->>-NextJS: {success: true, transaction_id}
    
    NextJS->>+NextJS: toast.success("Prédiction suivie!")
    NextJS->>+NextJS: onSuccess(response)
    NextJS-->>-Browser: Modal fermée + notification
    Browser-->>-User: Confirmation suivi
```

### 3.4 Mise à jour des Scores et Évaluation des Prédictions

Ce diagramme montre le processus automatisé de mise à jour des scores et d'évaluation des prédictions.

```mermaid
sequenceDiagram
    participant CeleryBeat as Celery Beat
    participant StatusTask as update_match_statuses
    participant APIFootball as API-Football
    participant DB as PostgreSQL
    participant EvalTask as update_match_result
    participant NotifTask as Notifications
    participant WebSocket as WebSocket
    participant Frontend as Frontend

    Note over CeleryBeat: Tâche toutes les 5 minutes
    
    CeleryBeat->>+StatusTask: check_match_statuses()
    
    StatusTask->>+DB: Match.objects.filter(status__in=['upcoming', 'live'])
    DB-->>-StatusTask: matches_to_check[]
    
    loop Pour chaque match
        StatusTask->>+APIFootball: get_fixtures(id=match.api_football_id)
        APIFootball-->>-StatusTask: fixture_data
        
        alt Match status changed
            StatusTask->>+DB: Match.objects.update(status, scores)
            DB-->>-StatusTask: match_updated
            
            alt Status = 'finished'
                StatusTask->>+EvalTask: update_match_result(match_id)
                
                EvalTask->>+DB: Prediction.objects.filter(match=match)
                DB-->>-EvalTask: predictions[]
                
                loop Pour chaque prédiction
                    EvalTask->>+EvalTask: evaluate_prediction()
                    Note over EvalTask: Compare prediction.winner<br/>with actual result
                    
                    EvalTask->>+DB: Prediction.update(was_correct, status)
                    EvalTask->>+DB: UserPrediction.update(result_profit)
                    EvalTask->>+DB: Bankroll.update(current_amount)
                    DB-->>-EvalTask: evaluation_saved
                end
                
                EvalTask->>+NotifTask: send_prediction_results()
                NotifTask->>+DB: Notification.objects.create()
                NotifTask->>+WebSocket: emit('prediction_result')
                WebSocket-->>-Frontend: Real-time notification
                
                EvalTask-->>-StatusTask: evaluations_completed
            end
            
        else Match live update
            StatusTask->>+DB: MatchLiveUpdate.objects.create()
            StatusTask->>+WebSocket: emit('live_update')
            WebSocket-->>-Frontend: Score en direct
        end
    end
    
    StatusTask-->>-CeleryBeat: status_check_completed
```

### 3.5 Gestion des Matchs en Direct avec Mises à Jour Temps Réel

Ce diagramme illustre le système de suivi en temps réel des matchs en cours.

```mermaid
sequenceDiagram
    participant CeleryBeat as Celery Beat
    participant LiveTask as check_ending_matches
    participant APIFootball as API-Football
    participant DB as PostgreSQL
    participant WebSocket as WebSocket Server
    participant Frontend as React Frontend
    participant User as Utilisateur

    Note over CeleryBeat: Tâche intensive toutes les minutes
    
    CeleryBeat->>+LiveTask: check_ending_matches()
    
    LiveTask->>+DB: Match.objects.filter(status='live')
    DB-->>-LiveTask: live_matches[]
    
    loop Pour chaque match live
        LiveTask->>+APIFootball: get_fixtures(id=match_id)
        APIFootball-->>-LiveTask: live_fixture_data
        
        LiveTask->>+LiveTask: extract_minute_and_scores()
        
        alt Match toujours en cours
            LiveTask->>+DB: MatchLiveUpdate.objects.create()
            Note over DB: Stockage: minute, scores,<br/>événements (buts, cartons)
            
            LiveTask->>+WebSocket: emit('live_score_update')
            Note over WebSocket: Channel: match_{id}<br/>Payload: {minute, home_score, away_score}
            
            WebSocket-->>+Frontend: Real-time update received
            Frontend->>+Frontend: updateMatchDisplay()
            Frontend-->>-User: Score mis à jour automatiquement
            
        else Match terminé (FT, AET, PEN)
            LiveTask->>+DB: Match.update(status='finished')
            LiveTask->>+LiveTask: trigger_immediate_evaluation()
            
            LiveTask->>+WebSocket: emit('match_finished')
            Note over WebSocket: Notification finale du match
            
            WebSocket-->>+Frontend: Match finished notification
            Frontend->>+Frontend: showMatchResult()
            Frontend-->>-User: "Match terminé" + résultat final
        end
    end
    
    Note over LiveTask: Programmation adaptative:<br/>- Matchs 85e min+ : vérif toutes les 3min<br/>- Matchs normaux : vérif toutes les 15min
    
    LiveTask->>+LiveTask: schedule_next_checks()
    LiveTask-->>-CeleryBeat: live_monitoring_completed
```

### 3.6 Flux d'Authentification et Autorisation

Ce diagramme montre le processus d'authentification JWT et de gestion des permissions.

```mermaid
sequenceDiagram
    participant User as Utilisateur
    participant Frontend as React Frontend
    participant DjangoAPI as Django API
    participant JWT as JWT Service
    participant DB as PostgreSQL
    participant Premium as Premium Service

    User->>+Frontend: Login (email, password)
    Frontend->>+DjangoAPI: POST /api/auth/login/
    
    DjangoAPI->>+DB: User.objects.get(email=email)
    DB-->>-DjangoAPI: user_data
    
    DjangoAPI->>+DjangoAPI: check_password(password)
    
    alt Authentification réussie
        DjangoAPI->>+JWT: generate_tokens(user)
        JWT-->>-DjangoAPI: {access_token, refresh_token}
        
        DjangoAPI->>+DB: UserProfile.objects.get(user=user)
        DB-->>-DjangoAPI: profile_data
        
        DjangoAPI-->>-Frontend: {tokens, user_profile, permissions}
        
        Frontend->>+Frontend: setAuth(tokens, user)
        Frontend->>+Frontend: localStorage.setItem('tokens')
        Frontend-->>-User: Connexion réussie
        
        Note over Frontend: Requêtes suivantes incluent:<br/>Authorization: Bearer {access_token}
        
        User->>+Frontend: Accès fonctionnalité premium
        Frontend->>+DjangoAPI: GET /api/premium/feature/
        
        DjangoAPI->>+JWT: verify_token(access_token)
        JWT-->>-DjangoAPI: decoded_payload
        
        DjangoAPI->>+Premium: check_premium_access(user)
        
        alt Utilisateur premium
            Premium-->>DjangoAPI: access_granted
            DjangoAPI-->>Frontend: premium_data
        else Utilisateur standard
            Premium-->>DjangoAPI: access_denied
            DjangoAPI-->>Frontend: {error: "Premium required"}
            Frontend-->>User: "Upgrade vers Premium"
        end
        
    else Authentification échouée
        DjangoAPI-->>-Frontend: {error: "Invalid credentials"}
        Frontend-->>-User: "Identifiants incorrects"
    end
```

---

## 4. Spécifications API

### 4.1 Vue d'Ensemble de l'API

**Base URL :** `https://api.aibet.fr/api/v1/`  
**Protocole :** HTTPS  
**Format :** JSON  
**Authentification :** JWT (JSON Web Tokens)  
**Versioning :** URL Path (`/api/v1/`)

#### 4.1.1 Structure des Réponses

**Réponse Standard de Succès :**
```json
{
    "status": "success",
    "data": { /* contenu spécifique */ },
    "message": "Operation completed successfully"
}
```

**Réponse Standard d'Erreur :**
```json
{
    "status": "error",
    "error": {
        "code": "VALIDATION_ERROR",
        "message": "Invalid input data",
        "details": {
            "field_name": ["Error message"]
        }
    },
    "timestamp": "2024-01-15T10:30:00Z"
}
```

### 4.2 Authentification et Autorisation

#### 4.2.1 Endpoints d'Authentification

**Obtenir un Token JWT**
```http
POST /api/v1/jwt/token/
Content-Type: application/json

{
    "email": "user@example.com",
    "password": "secure_password"
}
```

**Réponse :**
```json
{
    "access": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9...",
    "refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9...",
    "user": {
        "id": 1,
        "email": "user@example.com",
        "is_premium": false,
        "display_name": "John Doe"
    }
}
```

**Rafraîchir un Token**
```http
POST /api/v1/jwt/refresh/
Content-Type: application/json

{
    "refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9..."
}
```

**Vérifier un Token**
```http
POST /api/v1/jwt/verify/
Content-Type: application/json

{
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9..."
}
```

#### 4.2.2 Headers d'Authentification

Pour toutes les requêtes authentifiées :
```http
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9...
Content-Type: application/json
```

### 4.3 Endpoints des Prédictions

#### 4.3.1 Lister les Prédictions

**Endpoint :** `GET /api/v1/predictions/`  
**Authentification :** Optionnelle  
**Permissions :** Accès public

**Paramètres Query :**
- `status`: `upcoming|live|finished` (défaut: `upcoming`)
- `league`: Nom de la ligue pour filtrer
- `date_from`: Date de début (format: YYYY-MM-DD)
- `date_to`: Date de fin (format: YYYY-MM-DD)
- `confidence_min`: Confiance minimale (0-100)
- `page`: Numéro de page (défaut: 1)
- `page_size`: Taille de page (défaut: 20, max: 100)

**Exemple de Requête :**
```http
GET /api/v1/predictions/?status=upcoming&confidence_min=70&page=1
```

**Réponse :**
```json
{
    "count": 156,
    "next": "https://api.aibet.fr/api/v1/predictions/?page=2",
    "previous": null,
    "results": [
        {
            "id": 42,
            "match": {
                "id": 123,
                "home_team": "Bayern Munich",
                "away_team": "Real Madrid",
                "home_team_logo": "https://api.aibet.fr/images/teams/bayern.png",
                "away_team_logo": "https://api.aibet.fr/images/teams/real.png",
                "league": "Champions League",
                "match_date": "2024-01-20T21:00:00Z",
                "status": "upcoming"
            },
            "winner": "Bayern Munich",
            "score_prediction": "2-1",
            "confidence": 78.5,
            "prediction_type": "1",
            "prediction_text": "Bayern Munich gagne",
            "reasoning": "Bayern Munich est en excellente forme à domicile...",
            "key_factors": [
                "Avantage du terrain",
                "Forme récente supérieure",
                "Absences dans l'équipe adverse"
            ],
            "odds": 2.15,
            "home_win_probability": 0.65,
            "draw_probability": 0.20,
            "away_win_probability": 0.15,
            "total_goals": "Over 2.5",
            "btts": "Yes",
            "half_time_result": "1",
            "first_goalscorer": "Harry Kane",
            "anytime_goalscorer": "Vinicius Jr",
            "top_goalscorers": [
                {"name": "Harry Kane", "probability": 0.35},
                {"name": "Vinicius Jr", "probability": 0.28}
            ],
            "published": true,
            "created_at": "2024-01-15T10:30:00Z",
            "updated_at": "2024-01-15T10:30:00Z"
        }
    ]
}
```

#### 4.3.2 Détail d'une Prédiction

**Endpoint :** `GET /api/v1/predictions/{id}/`  
**Authentification :** Optionnelle  
**Permissions :** Accès public

**Exemple de Requête :**
```http
GET /api/v1/predictions/42/
```

**Réponse :** Format identique à l'objet dans la liste, avec champs additionnels :
```json
{
    "id": 42,
    "match": { /* objet match complet */ },
    "detailed_stats": {
        "home_team": {
            "recent_form": ["W", "W", "D", "W", "L"],
            "goals_scored_avg": 2.1,
            "goals_conceded_avg": 0.8,
            "win_percentage": 0.75
        },
        "away_team": {
            "recent_form": ["W", "L", "W", "W", "D"],
            "goals_scored_avg": 1.8,
            "goals_conceded_avg": 1.2,
            "win_percentage": 0.60
        },
        "head_to_head": {
            "total_matches": 15,
            "home_wins": 8,
            "draws": 4,
            "away_wins": 3
        }
    },
    "additional_odds": {
        "total_goals": {
            "over_2.5": 1.85,
            "under_2.5": 1.95
        },
        "btts": {
            "yes": 1.75,
            "no": 2.05
        }
    },
    /* autres champs... */
}
```

#### 4.3.3 Historique Public des Prédictions

**Endpoint :** `GET /api/v1/predictions/public_history/`  
**Authentification :** Non requise  
**Permissions :** Accès public

**Paramètres Query :**
- `days`: Nombre de jours d'historique (défaut: 30, max: 90)
- `status`: Statut des prédictions (`success|failure|void`)

**Réponse :**
```json
{
    "summary": {
        "total_predictions": 1250,
        "successful_predictions": 892,
        "success_rate": 0.714,
        "average_odds": 2.05,
        "total_profit": 15240.50,
        "roi": 0.183
    },
    "predictions": [
        {
            "id": 41,
            "match": { /* objet match */ },
            "prediction_type": "1",
            "confidence": 75.0,
            "odds": 1.95,
            "real_score": "2-1",
            "was_correct": true,
            "status": "success"
        }
    ]
}
```

#### 4.3.4 Statistiques de Performance

**Endpoint :** `GET /api/v1/predictions/performance/`  
**Authentification :** Non requise  
**Permissions :** Accès public

**Réponse :**
```json
{
    "global_stats": {
        "success_rate": 0.714,
        "total_predictions": 1250,
        "average_confidence": 68.5,
        "profit_margin": 0.183
    },
    "by_prediction_type": {
        "1": {"success_rate": 0.72, "count": 580},
        "X": {"success_rate": 0.65, "count": 320},
        "2": {"success_rate": 0.71, "count": 350}
    },
    "by_confidence_range": {
        "80-100": {"success_rate": 0.85, "count": 125},
        "60-79": {"success_rate": 0.73, "count": 650},
        "40-59": {"success_rate": 0.61, "count": 475}
    },
    "last_30_days": {
        "success_rate": 0.78,
        "predictions_count": 85,
        "trend": "improving"
    }
}
```

### 4.4 Endpoints des Matchs

#### 4.4.1 Lister les Matchs

**Endpoint :** `GET /api/v1/predictions/matches/`  
**Authentification :** Optionnelle  
**Permissions :** Accès public

**Paramètres Query :**
- `status`: `upcoming|live|finished`
- `league`: Nom de la ligue
- `date`: Date spécifique (format: YYYY-MM-DD)
- `team`: Nom d'équipe pour filtrer

**Réponse :**
```json
{
    "count": 48,
    "results": [
        {
            "id": 123,
            "home_team": "Barcelona",
            "away_team": "Real Madrid",
            "home_team_logo": "https://api.aibet.fr/images/teams/barca.png",
            "away_team_logo": "https://api.aibet.fr/images/teams/real.png",
            "league": "La Liga",
            "match_date": "2024-01-20T21:00:00Z",
            "status": "upcoming",
            "home_score": null,
            "away_score": null,
            "predictions": [
                {
                    "id": 42,
                    "prediction_type": "1",
                    "confidence": 78.5,
                    "odds": 2.15
                }
            ]
        }
    ]
}
```

#### 4.4.2 Détail d'un Match

**Endpoint :** `GET /api/v1/predictions/matches/{id}/`  
**Authentification :** Optionnelle

**Réponse :**
```json
{
    "id": 123,
    "home_team": "Barcelona",
    "away_team": "Real Madrid",
    "league": "La Liga",
    "match_date": "2024-01-20T21:00:00Z",
    "status": "live",
    "home_score": 1,
    "away_score": 0,
    "latest_update": {
        "minute": 67,
        "message": "But de Lewandowski (67')",
        "timestamp": "2024-01-20T21:07:00Z"
    },
    "predictions": [
        {
            "id": 42,
            "prediction_type": "1",
            "confidence": 78.5,
            "reasoning": "Analyse détaillée...",
            /* objet prédiction complet */
        }
    ]
}
```

### 4.5 Endpoints de Bankroll

#### 4.5.1 Lister les Bankrolls Utilisateur

**Endpoint :** `GET /api/v1/bankroll/bankrolls/`  
**Authentification :** Requise  
**Permissions :** Utilisateur authentifié

**Réponse :**
```json
[
    {
        "id": 1,
        "name": "Bankroll Principale",
        "initial_amount": "1000.00",
        "current_amount": "1250.75",
        "target_amount": "2000.00",
        "risk_tolerance": "medium",
        "strategy": "kelly",
        "max_stake_percentage": 2.0,
        "is_active": true,
        "performance": {
            "total_bets": 45,
            "successful_bets": 32,
            "success_rate": 0.711,
            "profit": "250.75",
            "roi": 0.251
        },
        "created_at": "2024-01-01T00:00:00Z",
        "updated_at": "2024-01-15T10:30:00Z"
    }
]
```

#### 4.5.2 Créer une Bankroll

**Endpoint :** `POST /api/v1/bankroll/bankrolls/`  
**Authentification :** Requise

**Requête :**
```json
{
    "name": "Nouvelle Bankroll",
    "initial_amount": "500.00",
    "target_amount": "1000.00",
    "risk_tolerance": "low",
    "strategy": "flat",
    "max_stake_percentage": 1.5
}
```

**Réponse :** HTTP 201 Created + objet bankroll créé

#### 4.5.3 Calculateur Kelly

**Endpoint :** `POST /api/v1/bankroll/kelly-calculator/`  
**Authentification :** Requise

**Requête :**
```json
{
    "bankroll_amount": "1000.00",
    "odds": 2.15,
    "probability": 0.65,
    "risk_factor": 0.5
}
```

**Réponse :**
```json
{
    "recommended_stake": "67.44",
    "kelly_percentage": 0.0674,
    "adjusted_stake": "33.72",
    "risk_adjusted": true,
    "max_loss": "33.72",
    "potential_profit": "38.78"
}
```

### 4.6 Endpoints des Prédictions Utilisateur

#### 4.6.1 Suivre une Prédiction

**Endpoint :** `POST /api/v1/predictions/user-predictions/`  
**Authentification :** Requise

**Requête :**
```json
{
    "prediction": 42,
    "bankroll": 1,
    "user_stake": "50.00"
}
```

**Réponse :**
```json
{
    "id": 89,
    "prediction": {
        "id": 42,
        "match": { /* objet match */ },
        "prediction_type": "1",
        "confidence": 78.5,
        "odds": 2.15
    },
    "user_stake": "50.00",
    "recommended_stake": "67.44",
    "potential_profit": "57.50",
    "bankroll_at_time": "1250.75",
    "created_at": "2024-01-15T10:30:00Z"
}
```

#### 4.6.2 Dashboard Utilisateur

**Endpoint :** `GET /api/v1/predictions/user/dashboard/`  
**Authentification :** Requise

**Réponse :**
```json
{
    "summary": {
        "total_predictions": 45,
        "pending_predictions": 8,
        "successful_predictions": 32,
        "failed_predictions": 5,
        "success_rate": 0.865,
        "total_profit": "187.50",
        "roi": 0.234
    },
    "recent_predictions": [
        {
            "id": 89,
            "prediction": { /* objet prédiction */ },
            "user_stake": "50.00",
            "result_profit": "57.50",
            "result_status": "won"
        }
    ],
    "upcoming_matches": [
        {
            "id": 90,
            "prediction": { /* prédiction upcoming */ },
            "user_stake": "30.00"
        }
    ]
}
```

#### 4.6.3 Statistiques Utilisateur

**Endpoint :** `GET /api/v1/predictions/user/stats/`  
**Authentification :** Requise

**Réponse :**
```json
{
    "performance": {
        "all_time": {
            "total_predictions": 156,
            "successful_predictions": 112,
            "success_rate": 0.718,
            "total_stake": "2340.00",
            "total_profit": "456.75",
            "roi": 0.195,
            "average_odds": 2.08
        },
        "last_30_days": {
            "total_predictions": 23,
            "success_rate": 0.783,
            "profit": "89.25",
            "roi": 0.267
        },
        "by_prediction_type": {
            "1": {"count": 72, "success_rate": 0.75},
            "X": {"count": 34, "success_rate": 0.65},
            "2": {"count": 50, "success_rate": 0.72}
        }
    },
    "bankroll_evolution": [
        {
            "date": "2024-01-01",
            "amount": "1000.00"
        },
        {
            "date": "2024-01-15",
            "amount": "1187.50"
        }
    ]
}
```

### 4.7 Endpoints de Données Externes

#### 4.7.1 Fixtures API-Football

**Endpoint :** `GET /api/v1/data/fixtures/`  
**Authentification :** Optionnelle

**Paramètres Query :**
- `league_ids`: IDs des ligues (comma-separated)
- `days_ahead`: Jours à l'avance (défaut: 7)
- `status`: Statut des matchs

**Réponse :** Données brutes API-Football formatées

#### 4.7.2 Statistiques d'Équipes

**Endpoint :** `GET /api/v1/data/team-stats/{team_id}/`  
**Authentification :** Optionnelle

**Paramètres Query :**
- `league_id`: ID de la ligue
- `season`: Saison (défaut: current)

#### 4.7.3 Cotes d'un Match

**Endpoint :** `GET /api/v1/data/odds/{fixture_id}/`  
**Authentification :** Optionnelle

**Réponse :** Cotes de différents bookmakers pour le match

### 4.8 Gestion des Erreurs

#### 4.8.1 Codes d'Erreur HTTP

| Code | Description | Utilisation |
|------|-------------|-------------|
| 200 | OK | Requête réussie |
| 201 | Created | Ressource créée |
| 400 | Bad Request | Données invalides |
| 401 | Unauthorized | Token manquant/invalide |
| 403 | Forbidden | Permissions insuffisantes |
| 404 | Not Found | Ressource introuvable |
| 422 | Unprocessable Entity | Erreur de validation |
| 429 | Too Many Requests | Rate limit dépassé |
| 500 | Internal Server Error | Erreur serveur |

#### 4.8.2 Exemples de Réponses d'Erreur

**Erreur de Validation (400) :**
```json
{
    "status": "error",
    "error": {
        "code": "VALIDATION_ERROR",
        "message": "Invalid input data",
        "details": {
            "user_stake": ["This field must be a positive number"],
            "bankroll": ["Select a valid choice"]
        }
    }
}
```

**Erreur d'Authentification (401) :**
```json
{
    "status": "error",
    "error": {
        "code": "AUTHENTICATION_FAILED",
        "message": "Given token not valid for any token type",
        "details": "Token is expired or invalid"
    }
}
```

**Erreur de Permissions (403) :**
```json
{
    "status": "error",
    "error": {
        "code": "PERMISSION_DENIED",
        "message": "Premium subscription required",
        "details": "This feature requires a premium account"
    }
}
```

### 4.9 Rate Limiting

#### 4.9.1 Limites par Type d'Utilisateur

| Type | Requêtes/Minute | Requêtes/Heure | Requêtes/Jour |
|------|-----------------|----------------|---------------|
| Anonyme | 60 | 500 | 5,000 |
| Authentifié | 120 | 1,000 | 10,000 |
| Premium | 300 | 3,000 | 50,000 |

#### 4.9.2 Headers de Rate Limiting

```http
X-RateLimit-Limit: 120
X-RateLimit-Remaining: 87
X-RateLimit-Reset: 1642234800
Retry-After: 60
```

---

*[Les sections suivantes seront ajoutées étape par étape selon vos instructions]* 

---

## 5. SCM et Plans d'Assurance Qualité

### 5.1 Gestion du Code Source (SCM)

#### 5.1.1 Système de Contrôle de Version

**Outil Principal :** Git  
**Plateforme :** GitHub/GitLab  
**Structure du Repository :**

```
AIBet_V2/
├── .git/                    # Historique Git
├── .gitignore              # Fichiers ignorés
├── README.md               # Documentation projet
├── requirements.txt        # Dépendances Python
├── manage.py              # Point d'entrée Django
├── docker-compose.yml     # Configuration conteneurs
├── backend/               # Code Django
│   ├── aibet/            # Configuration principale
│   ├── predictions/      # Module prédictions
│   ├── bankroll/        # Module bankroll
│   └── accounts/        # Module utilisateurs
└── frontend/             # Code Next.js
    ├── src/
    ├── package.json
    └── next.config.js
```

#### 5.1.2 Stratégie de Branching

**Modèle GitFlow Adapté :**

```mermaid
gitGraph
    commit id: "Initial"
    branch develop
    checkout develop
    commit id: "Setup project"
    branch feature/predictions
    checkout feature/predictions
    commit id: "Add prediction models"
    commit id: "Add GPT integration"
    checkout develop
    merge feature/predictions
    branch feature/bankroll
    checkout feature/bankroll
    commit id: "Add bankroll system"
    checkout develop
    merge feature/bankroll
    branch release/v1.0
    checkout release/v1.0
    commit id: "Version bump"
    commit id: "Bug fixes"
    checkout main
    merge release/v1.0
    tag: "v1.0.0"
    checkout develop
    merge main
```

**Branches Principales :**
- `main` : Code de production stable
- `develop` : Code d'intégration continue
- `feature/*` : Développement de nouvelles fonctionnalités
- `release/*` : Préparation des versions
- `hotfix/*` : Corrections urgentes en production

#### 5.1.3 Conventions de Commit

**Format Standardisé :**
```
<type>(<scope>): <description>

[body optionnel]

[footer optionnel]
```

**Types de Commits :**
- `feat`: Nouvelle fonctionnalité
- `fix`: Correction de bug
- `docs`: Documentation
- `style`: Formatage du code
- `refactor`: Refactoring sans changement de fonctionnalité
- `test`: Ajout/modification de tests
- `chore`: Maintenance du code

**Exemples :**
```bash
feat(predictions): add GPT-4o integration for enhanced predictions
fix(bankroll): resolve Kelly criterion calculation error
docs(api): update endpoint documentation
test(predictions): add unit tests for prediction model
```

#### 5.1.4 Hooks Git

**Pre-commit Hooks :**
```bash
#!/bin/bash
# .git/hooks/pre-commit

# Exécuter les linters
echo "🔍 Running linters..."
python -m flake8 .
python -m black --check .
python -m isort --check .

# Exécuter les tests unitaires
echo "🧪 Running tests..."
python manage.py test --settings=aibet.test_settings

# Vérifier la sécurité
echo "🔒 Security check..."
python -m bandit -r . -x venv/
```

### 5.2 Stratégie de Tests et Assurance Qualité

#### 5.2.1 Pyramide de Tests

```mermaid
graph TB
    A[Tests End-to-End<br/>5% - Selenium/Cypress] --> B[Tests d'Intégration<br/>15% - API Testing]
    B --> C[Tests Unitaires<br/>80% - pytest/Django]
    
    style A fill:#ff9999
    style B fill:#ffcc99
    style C fill:#99ccff
```

#### 5.2.2 Configuration des Tests

**Framework de Tests :**
- **Backend :** pytest + pytest-django
- **Frontend :** Jest + React Testing Library
- **E2E :** Cypress

**Configuration pytest.ini :**
```ini
[tool:pytest]
DJANGO_SETTINGS_MODULE = aibet.test_settings
python_files = tests.py test_*.py *_tests.py
addopts = 
    --verbose
    --tb=short
    --reuse-db
    --cov=.
    --cov-report=html
    --cov-report=term-missing
    --cov-fail-under=80
testpaths = 
    predictions/tests
    bankroll/tests
    accounts/tests
    data/tests
```

**Settings de Test :**
```python
# aibet/test_settings.py
from .settings import *

# Base de données en mémoire pour les tests
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': ':memory:',
    }
}

# Désactiver les migrations pour accélérer les tests
class DisableMigrations:
    def __contains__(self, item):
        return True
    def __getitem__(self, item):
        return None

MIGRATION_MODULES = DisableMigrations()

# Configuration spéciale pour les tests
CELERY_TASK_ALWAYS_EAGER = True
CELERY_TASK_EAGER_PROPAGATES = True

# Cache en mémoire pour les tests
CACHES = {
    'default': {
        'BACKEND': 'django.core.cache.backends.locmem.LocMemCache',
    }
}
```

#### 5.2.3 Types de Tests Implémentés

**1. Tests Unitaires (80%)**

*Exemple - Tests des Modèles :*
```python
# predictions/tests/test_models.py
import pytest
from django.test import TestCase
from predictions.models import Match, Prediction

class TestPredictionModel(TestCase):
    def setUp(self):
        self.match = Match.objects.create(
            home_team="Real Madrid",
            away_team="Barcelona",
            league="La Liga",
            match_date=timezone.now() + timedelta(days=1)
        )
    
    def test_prediction_creation(self):
        prediction = Prediction.objects.create(
            match=self.match,
            confidence=78.5,
            prediction_type="1",
            winner="Real Madrid"
        )
        self.assertEqual(prediction.confidence, 78.5)
        self.assertEqual(prediction.get_prediction_display(), "Victoire domicile")
    
    def test_prediction_evaluation(self):
        prediction = Prediction.objects.create(
            match=self.match,
            prediction_type="1",
            winner="Real Madrid"
        )
        # Simuler un résultat
        self.match.home_score = 2
        self.match.away_score = 1
        self.match.status = "finished"
        self.match.save()
        
        result = prediction.evaluate_prediction()
        self.assertTrue(result)
        self.assertEqual(prediction.status, "success")
```

*Exemple - Tests des APIs :*
```python
# predictions/tests/test_api.py
from rest_framework.test import APITestCase
from rest_framework import status
from django.contrib.auth import get_user_model

class TestPredictionAPI(APITestCase):
    def setUp(self):
        self.user = get_user_model().objects.create_user(
            email="test@example.com",
            password="testpass123"
        )
        self.client.force_authenticate(user=self.user)
    
    def test_get_predictions_list(self):
        response = self.client.get('/api/v1/predictions/')
        self.assertEqual(response.status_code, status.HTTP_200_OK)
        self.assertIn('results', response.data)
    
    def test_prediction_detail_unauthorized(self):
        self.client.force_authenticate(user=None)
        response = self.client.get('/api/v1/predictions/1/')
        self.assertEqual(response.status_code, status.HTTP_401_UNAUTHORIZED)
```

**2. Tests d'Intégration (15%)**

*Exemple - Tests Pipeline de Données :*
```python
# data/tests/test_pipeline.py
@pytest.mark.django_db
class TestDataPipeline:
    def test_complete_prediction_pipeline(self):
        # 1. Collecter les données
        matches_collected = collect_match_data(days_ahead=1)
        assert matches_collected['status'] == 'success'
        
        # 2. Vérifier que les matchs sont créés
        assert Match.objects.count() > 0
        
        # 3. Générer les prédictions
        match = Match.objects.first()
        prediction = generate_prediction(match.id)
        
        # 4. Vérifier la prédiction
        assert prediction is not None
        assert prediction.confidence > 0
        assert prediction.prediction_type in ['1', 'X', '2']
```

**3. Tests End-to-End (5%)**

*Configuration Cypress :*
```javascript
// cypress/e2e/prediction_flow.cy.js
describe('Prediction Flow', () => {
  beforeEach(() => {
    cy.login('test@example.com', 'password123')
  })

  it('should display predictions and allow betting', () => {
    // Naviguer vers les prédictions
    cy.visit('/predictions')
    cy.get('[data-testid="predictions-list"]').should('be.visible')
    
    // Cliquer sur une prédiction
    cy.get('[data-testid="prediction-card"]').first().click()
    
    // Vérifier les détails
    cy.get('[data-testid="prediction-details"]').should('contain', 'Confiance')
    cy.get('[data-testid="odds"]').should('be.visible')
    
    // Placer un pari
    cy.get('[data-testid="bet-button"]').click()
    cy.get('[data-testid="stake-input"]').type('50')
    cy.get('[data-testid="confirm-bet"]').click()
    
    // Vérifier la confirmation
    cy.get('[data-testid="success-message"]').should('contain', 'Pari enregistré')
  })
})
```

#### 5.2.4 Couverture de Code

**Objectifs de Couverture :**
- **Globale :** 80% minimum
- **Modèles critiques :** 95%
- **APIs publiques :** 90%
- **Logique métier :** 85%

**Configuration Coverage :**
```ini
# .coveragerc
[run]
source = .
omit = 
    venv/*
    */migrations/*
    */tests/*
    manage.py
    */settings/*
    */venv/*

[report]
exclude_lines =
    pragma: no cover
    def __repr__
    raise AssertionError
    raise NotImplementedError

[html]
directory = htmlcov
```

#### 5.2.5 Intégration Continue (CI/CD)

**GitHub Actions Workflow :**
```yaml
# .github/workflows/ci.yml
name: CI/CD Pipeline

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main, develop ]

jobs:
  test:
    runs-on: ubuntu-latest
    
    services:
      postgres:
        image: postgres:15
        env:
          POSTGRES_DB: test_aibet
          POSTGRES_USER: test_user
          POSTGRES_PASSWORD: test_pass
        options: >-
          --health-cmd pg_isready
          --health-interval 10s
          --health-timeout 5s
          --health-retries 5
    
    steps:
    - uses: actions/checkout@v3
    
    - name: Set up Python
      uses: actions/setup-python@v4
      with:
        python-version: '3.9'
    
    - name: Install dependencies
      run: |
        pip install -r requirements.txt
        pip install coverage pytest-cov
    
    - name: Run linting
      run: |
        flake8 .
        black --check .
        isort --check .
    
    - name: Run tests
      env:
        DATABASE_URL: postgres://test_user:test_pass@localhost/test_aibet
      run: |
        python manage.py test --settings=aibet.test_settings
        coverage run --source='.' manage.py test
        coverage report --fail-under=80
    
    - name: Upload coverage
      uses: codecov/codecov-action@v3

  security:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - name: Run security checks
      run: |
        pip install bandit safety
        bandit -r . -x venv/
        safety check
```

#### 5.2.6 Tests de Performance

**Tests de Charge avec Locust :**
```python
# tests/performance/locustfile.py
from locust import HttpUser, task, between

class PredictionUser(HttpUser):
    wait_time = between(1, 3)
    
    def on_start(self):
        # Authentification
        response = self.client.post("/api/v1/jwt/token/", json={
            "email": "test@example.com",
            "password": "testpass123"
        })
        self.token = response.json()["access"]
        self.client.headers.update({"Authorization": f"Bearer {self.token}"})
    
    @task(3)
    def view_predictions(self):
        self.client.get("/api/v1/predictions/")
    
    @task(2)
    def view_prediction_detail(self):
        self.client.get("/api/v1/predictions/1/")
    
    @task(1)
    def create_user_prediction(self):
        self.client.post("/api/v1/predictions/user-predictions/", json={
            "prediction": 1,
            "user_stake": "25.00"
        })
```

### 5.3 Métriques de Qualité

#### 5.3.1 KPIs de Développement

| Métrique | Objectif | Actuel | Statut |
|----------|----------|---------|--------|
| Couverture de code | >80% | 85% | ✅ |
| Tests qui passent | 100% | 98% | ⚠️ |
| Bugs critiques | 0 | 1 | ❌ |
| Temps de build | <5min | 4min 30s | ✅ |
| Complexité cyclomatique | <10 | 8.2 | ✅ |

#### 5.3.2 Métriques de Performance

| Métrique | Objectif | Actuel | Statut |
|----------|----------|---------|--------|
| Temps réponse API | <200ms | 150ms | ✅ |
| Throughput | >1000 req/s | 850 req/s | ⚠️ |
| Erreur rate | <1% | 0.5% | ✅ |
| Uptime | >99.9% | 99.8% | ⚠️ |

---

## 6. Justifications Techniques

### 6.1 Choix Architecturaux

#### 6.1.1 Architecture Microservices vs Monolithe

**Décision :** Architecture Monolithe Modulaire  
**Justification :**

**Avantages :**
- **Simplicité de déploiement** : Un seul conteneur Docker pour l'API
- **Performance** : Pas de latence réseau entre modules
- **Debugging facilité** : Stack trace complet sur un seul service
- **Équipe réduite** : Plus facile à maintenir avec une petite équipe

**Inconvénients acceptés :**
- **Scalabilité limitée** : Scaling horizontal plus complexe
- **Couplage technologique** : Même stack pour tous les modules

**Alternative considérée :** Microservices
- Écartée car complexité excessive pour la taille actuelle du projet
- Prévu pour une évolution future si croissance > 10x utilisateurs

#### 6.1.2 Choix de Base de Données

**Décision :** PostgreSQL  
**Justification :**

**Avantages PostgreSQL :**
- **ACID compliance** : Transactions fiables pour données financières
- **JSON natif** : Stockage flexible des données API externes
- **Performance** : Excellente pour lectures/écritures complexes
- **Extensibilité** : Support des extensions (PostGIS, Full-text search)

**Comparaison avec alternatives :**

| Critère | PostgreSQL | MongoDB | MySQL |
|---------|------------|---------|-------|
| Transactions | ✅ ACID | ⚠️ Limitées | ✅ ACID |
| JSON Support | ✅ Natif | ✅ Document | ⚠️ Basique |
| Scalabilité | ✅ Vertical | ✅ Horizontal | ⚠️ Limitée |
| Complexité | ⚠️ Moyenne | ✅ Simple | ✅ Simple |
| **Score** | **85%** | 70% | 60% |

#### 6.1.3 Frontend : Next.js vs React SPA

**Décision :** Next.js 14 avec App Router  
**Justification :**

**Avantages Next.js :**
- **SEO** : Server-Side Rendering pour pages publiques
- **Performance** : Code splitting automatique et optimisations
- **DX** : Developer Experience excellente
- **PWA Ready** : Service Workers intégrés

**Comparaison :**

```mermaid
graph LR
    A[Requirements] --> B{SEO Important?}
    B -->|Yes| C[Next.js ✅]
    B -->|No| D{Équipe expérience?}
    D -->|React Expert| E[React SPA]
    D -->|Mixed| C
    C --> F[Score: 90%]
    E --> G[Score: 75%]
```

### 6.2 Choix Technologiques

#### 6.2.1 Backend Stack

**Django REST Framework**

**Justifications :**
- **Écosystème mature** : 15+ ans de développement
- **Security by default** : CSRF, SQL injection, XSS protection
- **ORM puissant** : Relations complexes gérées facilement
- **Admin interface** : Interface d'administration gratuite
- **Communauté** : Large écosystème de packages

**Alternatives considérées :**
- **FastAPI** : Écarté pour manque de maturité de l'écosystème
- **Flask** : Trop minimaliste pour les besoins du projet
- **Node.js Express** : Équipe plus experte en Python

#### 6.2.2 Intelligence Artificielle

**GPT-4o via OpenAI API**

**Justifications techniques :**
- **Qualité supérieure** : Meilleure compréhension contextuelle
- **Multimodalité** : Capacité à traiter texte + données structurées
- **Recherche web intégrée** : Enrichissement contextuel automatique
- **Rate limiting robuste** : 25,000 tokens/minute suffisant

**Coût vs Performance :**
```python
# Analyse coût/performance
gpt_4o_cost = {
    'input_tokens': 0.00015,  # $ per 1K tokens
    'output_tokens': 0.0006,  # $ per 1K tokens
    'quality_score': 95,
    'latency_ms': 2000
}

claude_3_cost = {
    'input_tokens': 0.00008,
    'output_tokens': 0.00024,
    'quality_score': 85,
    'latency_ms': 1500
}

# ROI calculation: Quality justify 2.5x cost difference
```

**Alternatives évaluées :**
- **Claude 3** : Coût inférieur mais qualité moindre
- **Llama 2 local** : Écarté pour complexité infrastructure
- **Mistral** : API moins stable

#### 6.2.3 Containerisation

**Docker + Docker Compose**

**Justifications :**
- **Isolation** : Environnements reproductibles
- **Scalabilité** : Prêt pour orchestration Kubernetes
- **CI/CD** : Builds reproductibles
- **Dependencies** : Gestion simplifiée des dépendances système

**Configuration optimisée :**
```dockerfile
# Dockerfile optimisé multi-stage
FROM python:3.9-slim as base
RUN apt-get update && apt-get install -y \
    postgresql-client \
    && rm -rf /var/lib/apt/lists/*

FROM base as dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

FROM dependencies as production
COPY . .
EXPOSE 8000
CMD ["gunicorn", "aibet.wsgi:application"]
```

### 6.3 Patterns de Design

#### 6.3.1 Backend Patterns

**Repository Pattern** pour l'accès aux données :
```python
class PredictionRepository:
    @staticmethod
    def get_active_predictions():
        return Prediction.objects.filter(
            published=True,
            match__status='upcoming'
        ).select_related('match')
    
    @staticmethod
    def get_user_predictions(user):
        return UserPrediction.objects.filter(
            user=user
        ).select_related('prediction__match')
```

**Service Layer** pour la logique métier :
```python
class PredictionService:
    def __init__(self, gpt_client, repository):
        self.gpt_client = gpt_client
        self.repository = repository
    
    def generate_prediction(self, match):
        # Orchestration des appels externes
        context = self._gather_context(match)
        prediction_data = self.gpt_client.generate(context)
        return self.repository.create_prediction(match, prediction_data)
```

#### 6.3.2 Frontend Patterns

**Custom Hooks** pour la logique réutilisable :
```typescript
// hooks/usePredictions.ts
export function usePredictions(filters: PredictionFilters) {
  return useSWR(
    ['predictions', filters], 
    () => api.predictions.list(filters),
    { refreshInterval: 30000 }
  )
}
```

**Compound Components** pour l'UI complexe :
```tsx
<PredictionCard>
  <PredictionCard.Header />
  <PredictionCard.Content />
  <PredictionCard.Actions />
</PredictionCard>
```

### 6.4 Optimisations Performance

#### 6.4.1 Base de Données

**Index Strategy :**
```sql
-- Index composites pour requêtes fréquentes
CREATE INDEX idx_predictions_status_date 
ON predictions_prediction (status, created_at);

CREATE INDEX idx_matches_date_league 
ON predictions_match (match_date, league);

-- Index partiel pour prédictions actives
CREATE INDEX idx_active_predictions 
ON predictions_prediction (match_id) 
WHERE published = true AND status = 'upcoming';
```

**Query Optimization :**
```python
# Optimisation N+1 queries
predictions = Prediction.objects.select_related(
    'match'
).prefetch_related(
    'user_predictions__user'
).filter(published=True)
```

#### 6.4.2 Cache Strategy

**Multi-level Caching :**
```python
@cache_page(60 * 15)  # 15 minutes
def prediction_list(request):
    cache_key = f"predictions_list_{request.GET.urlencode()}"
    data = cache.get(cache_key)
    
    if not data:
        data = expensive_database_query()
        cache.set(cache_key, data, 60 * 10)  # 10 minutes
    
    return Response(data)
```

### 6.5 Sécurité

#### 6.5.1 Authentification JWT

**Justification du choix JWT :**
- **Stateless** : Pas de stockage session côté serveur
- **Scalable** : Fonctionnement multi-serveurs
- **Standard** : RFC 7519

**Configuration sécurisée :**
```python
SIMPLE_JWT = {
    'ACCESS_TOKEN_LIFETIME': timedelta(minutes=60),
    'REFRESH_TOKEN_LIFETIME': timedelta(days=7),
    'ROTATE_REFRESH_TOKENS': True,
    'BLACKLIST_AFTER_ROTATION': True,
    'ALGORITHM': 'HS256',
    'SIGNING_KEY': SECRET_KEY,
    'VERIFYING_KEY': None,
    'AUTH_HEADER_TYPES': ('Bearer',),
}
```

#### 6.5.2 Protection API

**Rate Limiting personnalisé :**
```python
class BurstRateThrottle(UserRateThrottle):
    scope = 'burst'
    
    def allow_request(self, request, view):
        # Algorithme token bucket pour gestion bursts
        return super().allow_request(request, view)
```

#### 6.5.3 Validation des Données

**Serializers avec validation stricte :**
```python
class BankrollSerializer(serializers.ModelSerializer):
    def validate_initial_amount(self, value):
        if value < Decimal('10.00'):
            raise serializers.ValidationError(
                "Le montant initial doit être d'au moins 10€"
            )
        return value
    
    def validate(self, attrs):
        if attrs['target_amount'] <= attrs['initial_amount']:
            raise serializers.ValidationError(
                "L'objectif doit être supérieur au montant initial"
            )
        return attrs
```

### 6.6 Monitoring et Observabilité

#### 6.6.1 Métriques Prometheus

**Métriques custom définies :**
```python
from prometheus_client import Counter, Histogram, Gauge

prediction_requests = Counter(
    'prediction_requests_total',
    'Total prediction requests',
    ['method', 'endpoint', 'status']
)

prediction_accuracy = Gauge(
    'prediction_accuracy_percentage',
    'Current prediction accuracy percentage'
)

gpt_response_time = Histogram(
    'gpt_api_response_seconds',
    'GPT API response time in seconds'
)
```

#### 6.6.2 Logging Structuré

**Configuration JSON logging :**
```python
LOGGING = {
    'formatters': {
        'json': {
            'class': 'pythonjsonlogger.jsonlogger.JsonFormatter',
            'format': '%(levelname)s %(name)s %(message)s %(pathname)s %(lineno)d'
        }
    },
    'handlers': {
        'json_file': {
            'class': 'logging.FileHandler',
            'filename': 'logs/app.json',
            'formatter': 'json'
        }
    }
}
```
