# 🧠 Exercice n8n – Gestion de demandes de support via formulaire

**Niveau : Débutant → Intermédiaire**  
**Objectif principal :** Maîtriser les formulaires, la gestion de données et la logique métier dans n8n

***

## 🎯 Contexte de l’exercice

Tu travailles comme **Test Automation Engineer** dans une équipe produit.  
L’équipe reçoit des **demandes de support internes** via un formulaire.  
Tu dois construire un workflow n8n qui :

*   Collecte les demandes via un **Form Trigger**
*   Les stocke proprement dans **Google Sheets**
*   Applique des règles simples de qualité et de structuration des données  
    ➡️ **Sans envoyer d’email, sans Slack, sans webhook externe** (exercice silencieux)

***

## 🧩 Point de départ (fourni)

Tu disposes déjà de ces éléments :

*   ✅ **Form Trigger** avec les champs :
    *   Name (obligatoire)
    *   Email (obligatoire)
    *   Request (obligatoire)
*   ✅ **Google Sheets – Append or Update**
    *   Colonnes : Name | Email | Request
    *   Matching column : Name

***

## ✅ Exercice – Partie 1 : Compréhension (obligatoire)

Sans modifier le workflow, explique **par écrit** :

1.  Quand est-ce que le formulaire déclenche le workflow ?
2.  Que se passe-t-il si une personne soumet **deux fois le même Name** ?
3.  Où sont stockées les données ?
4.  Quelle donnée permet d’identifier une ligne existante ?

🎯 Objectif : comprendre la logique **append vs update**

***

## ✅ Exercice – Partie 2 : Qualité des données

### 🎯 Objectif

Améliorer la fiabilité des données **avant** l’écriture dans Google Sheets.

### Tâches

1.  Ajoute un **nœud `IF`** entre le Form Trigger et Google Sheets
2.  La condition doit vérifier :
    *   Que l’email **contient `@`**
3.  *   ✅ Si vrai → écrire dans Google Sheets
    *   ❌ Si faux → **ne rien faire** (workflow silencieux)

💡 Astuce : utilise une condition de type *String → contains*

***

## ✅ Exercice – Partie 3 : Normalisation des données

### 🎯 Objectif

Uniformiser les données pour éviter les doublons inutiles.

### Tâches

1.  Ajoute un **nœud `Set`** avant Google Sheets
2.  Modifie les champs :
    *   `Name` → tout en **minuscules**
    *   `Email` → tout en **minuscules**
3.  Supprime tous les champs inutiles (ex : `submittedAt`, `formMode`)

💡 Objectif caché : maîtriser le **nettoyage du $json**

***

## ✅ Exercice – Partie 4 : Logique métier

### 🎯 Objectif

Catégoriser automatiquement les demandes.

### Tâches

1.  Ajoute une colonne **`Category`** dans Google Sheets
2.  Dans n8n, ajoute un **nœud `IF` ou `Switch`** :
    *   Si `Request` contient :
        *   "bug" → Category = `Bug`
        *   "access" → Category = `Access`
        *   sinon → `Other`
3.  Envoie `Category` vers Google Sheets

🎯 Compétences travaillées :

*   Expressions
*   Conditions textuelles
*   Mapping avancé

***

## ✅ Exercice – Partie 5 : Idempotence (niveau intermédiaire)

### 🎯 Objectif

Éviter les conflits liés au nom.

### Tâche

1.  Change la **matching column** :
    *   de `Name`
    *   vers `Email`
2.  Explique pourquoi **l’email est une meilleure clé**

***

## 🧪 Données de test recommandées

Utilise ces entrées dans le formulaire :

| Name     | Email          | Request            |
| -------- | -------------- | ------------------ |
| Ibrahima | <ibra@mail.fr> | access not working |
| Ibrahima | <IBRA@mail.fr> | bug on login       |
| Sarah    | sarahmail.fr   | cannot access      |

➡️ Observe :

*   Quelles lignes sont mises à jour
*   Lesquelles sont ignorées
*   Comment les catégories sont remplies

***

## 🔁 Routine d’entraînement (10–15 min)

À refaire régulièrement :

1.  Recréer le workflow **sans copier-coller**
2.  Changer :
    *   la logique de catégorisation
    *   la clé de matching
    *   les champs du formulaire
3.  Expliquer chaque nœud à voix haute (ou par écrit)

***

## 🎓 Compétences que tu développes réellement

*   Maîtrise du **Form Trigger**
*   Gestion des **données propres**
*   Logique conditionnelle
*   Google Sheets comme base de données
*   Réflexes de concepteur de workflows robustes

***

Fait par: **Microsoft Copilot**
