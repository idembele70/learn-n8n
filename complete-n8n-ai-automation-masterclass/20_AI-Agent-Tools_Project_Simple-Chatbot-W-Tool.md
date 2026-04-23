```md
# 🧠 Exercice n8n – Workflow Agent IA (Niveau Débutant)

## 🎯 Objectif
Créer un workflow n8n qui répond intelligemment à un message utilisateur via un agent IA.

---

## ✅ Résultat attendu
Quand l’utilisateur envoie un message dans le chat :
- L’agent IA répond
- Il peut faire un calcul
- Il peut donner la date actuelle
- Il garde le contexte des derniers messages

---

## 🧩 Contraintes techniques
- Utiliser un **Chat Trigger**
- Utiliser un **AI Agent**
- Connecter :
  - un **LLM**
  - une **mémoire**
  - au moins **2 outils IA**

---

## 🪜 Étapes guidées

### 1️⃣ Déclencheur
- Ajouter un nœud **When chat message received**
- Ne rien configurer

---

### 2️⃣ Modèle de langage
- Ajouter un nœud **Groq Chat Model**
- Choisir un modèle GPT
- Le connecter au **AI Agent** (ai_languageModel)

---

### 3️⃣ Agent IA
- Ajouter un nœud **AI Agent**
- Relier le Chat Trigger à l’Agent

---

### 4️⃣ Mémoire
- Ajouter **Simple Memory (Buffer Window)**
- Mettre `contextWindowLength = 10`
- Connecter à l’Agent (ai_memory)

---

### 5️⃣ Outils IA
Ajouter et connecter à l’Agent :
- **Calculator**
- **Date & Time**

---

## 🧪 Tests à effectuer
Dans le chat, tester :
- `Combien fait 8 * 12 ?`
- `Quelle est la date aujourd’hui ?`
- `Répète ce que je t’ai dit avant`

---

## 🧠 Bonus (facultatif)
- Ajouter **ScraperAPI Tool**
- Demander à l’agent de récupérer une info depuis un site

---

## ✅ Validation
L’exercice est réussi si :
- L’agent répond sans erreur
- Il utilise les bons outils
- Il se souvient du contexte

---

💡 Refaire cet exercice chaque semaine en changeant les outils.
```
Fait avec **Microsoft Copilot**
