# 🧠 Exercice n8n – Chat Agent IA avec Mémoire (silent training)

## Niveau
Débutant → Intermédiaire

---

## 🎯 Objectif pédagogique

Construire et améliorer un **agent conversationnel IA** dans n8n en utilisant :
- un **Chat Trigger**
- un **AI Agent**
- un **modèle LLM (Groq)**
- une **mémoire contextuelle**

L’exercice est **sans bruit** :
- pas d’email
- pas de notification
- pas de webhook sortant
- uniquement des réponses de chat

---

## 🧩 Workflow de départ (fourni)

Nœuds déjà présents :
- `When chat message received`
- `AI Agent`
- `Groq Chat Model (llama-3.3-70b)`
- `Memory Buffer Window`

---

## ✅ Partie 1 – Compréhension du workflow

Sans modifier le workflow, répondre par écrit :

1. Quel événement déclenche l’exécution du workflow ?
2. Quel nœud est responsable du raisonnement IA ?
3. Quel rôle joue le modèle Groq dans ce workflow ?
4. À quoi sert la mémoire contextuelle ?
5. Que représente la valeur `contextWindowLength = 10` ?

---

## ✅ Partie 2 – Personnalité de l’agent

### Objectif
Donner un comportement clair et constant à l’agent.

### Tâches

1. Ouvrir le nœud **AI Agent**
2. Ajouter une instruction système indiquant que l’agent :
   - est **expert n8n**
   - répond de manière **courte et structurée**
   - utilise un **ton pédagogique**
3. Tester avec le message :
   - `Explique ce qu’est un Chat Trigger dans n8n`

---

## ✅ Partie 3 – Test de la mémoire

### Objectif
Vérifier que l’agent se souvient du contexte.

### Tâches

1. Envoyer successivement les messages :
   - `Je m'appelle Ibrahima`
   - `Quel est mon prénom ?`
2. Observer la réponse
3. Modifier `contextWindowLength` à **3**
4. Refaire le test et noter les différences

---

## ✅ Partie 4 – Normalisation des entrées

### Objectif
Améliorer la qualité du prompt envoyé à l’agent.

### Tâches

1. Ajouter un nœud **Set** entre le Chat Trigger et l’Agent
2. Créer un champ :
   - `clean_message` = message utilisateur en minuscules
3. Supprimer tous les autres champs
4. Configurer l’Agent pour utiliser uniquement `clean_message`

---

## ✅ Partie 5 – Routage simple sans bruit

### Objectif
Empêcher l’IA de répondre inutilement.

### Tâches

1. Ajouter un nœud **IF** avant l’Agent
2. Conditions :
   - si le message contient `bonjour`
     - réponse fixe : `Bonjour 👋`
   - sinon
     - passer par l’AI Agent
3. Les deux chemins doivent retourner un message de chat

---

## 🧪 Scénarios de test

- `Bonjour`
- `C’est quoi la memory buffer window ?`
- `De quoi parlions-nous avant ?`

---

## ✅ Critères de réussite

- Le chat répond à chaque message
- L’agent conserve le contexte
- Les messages simples contournent l’IA
- Aucun bruit externe n’est généré

---

## 🔁 Routine d’entraînement (10 minutes)

- Changer le modèle LLM
- Modifier la mémoire (0, 3, 10)
- Ajuster la personnalité de l’agent
- Recréer le workflow sans regarder

---

## 🎓 Compétences développées

- Chat Trigger n8n
- Agents IA LangChain
- Mémoire conversationnelle
- Prompt engineering
- Logique conditionnelle silencieuse

---

## ✅ Fin de l’exercice
