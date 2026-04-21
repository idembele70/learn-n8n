    🧠 EXERCICE n8n – Mini Chatbot IA avec mémoire (mode silencieux)

    Niveau : Intermédiaire  
    Objectif : Comprendre et maîtriser les workflows IA dans n8n (Webhook + Agent + LLM + Mémoire)

    ---

    CONTEXTE

    Tu dois construire un chatbot interne accessible via HTTP.
    Ce chatbot :
    - reçoit un message utilisateur via un Webhook
    - utilise un modèle LLM (Groq)
    - conserve le contexte de la discussion
    - répond directement via HTTP
    Aucune notification externe, aucun email, aucun log → exercice sans bruit.

    ---

    POINT DE DÉPART (fourni)

    Nœuds existants :
    - Webhook (POST /chatbot)
    - AI Agent
    - Groq Chat Model (llama‑3.1‑8b‑instant)
    - Simple Memory (Window Buffer)
    - Respond to Webhook

    ---

    PARTIE 1 – COMPRÉHENSION (obligatoire)

    Sans modifier le workflow, répondre par écrit :

    1. Quel champ exact du body HTTP est utilisé comme message utilisateur ?
    2. Quel nœud fournit le modèle LLM à l’agent ?
    3. Comment est identifiée une session de discussion ?
    4. Quel est le rôle précis du nœud “Simple Memory” ?
    5. Pourquoi le mode “responseNode” est important ici ?

    ---

    PARTIE 2 – STRUCTURATION DE L’ENTRÉE UTILISATEUR

    Objectif : normaliser l’entrée pour l’agent.

    Tâches :
    1. Ajouter un nœud SET entre Webhook et AI Agent
    2. Créer un champ :
       - `user_message` → valeur = `{{$json.body.chatInput}}`
    3. Supprimer tout autre champ du JSON
    4. Modifier l’AI Agent pour qu’il utilise `user_message` comme prompt

    ---

    PARTIE 3 – PERSONNALITÉ DE L’AGENT IA

    Objectif : injecter du contexte système.

    Tâches :
    1. Dans le nœud AI Agent, définir une instruction système :
       - L’agent se comporte comme un expert n8n
       - Réponses courtes
       - Ton pédagogique
    2. Tester avec une question simple :
       - “Explique le rôle d’un webhook dans n8n”

    ---

    PARTIE 4 – MÉMOIRE CONTRÔLÉE

    Objectif : vérifier que la mémoire fonctionne réellement.

    Tâches :
    1. Envoyer successivement :
       - “Je m’appelle Ibrahima”
       - “Quel est mon prénom ?”
    2. Observer la réponse
    3. Changer `contextWindowLength` de 10 à 3
    4. Refaire le test et noter la différence

    ---

    PARTIE 5 – ROUTAGE INTELLIGENT

    Objectif : différencier les intentions.

    Tâches :
    1. Ajouter un nœud IF après le Webhook
    2. Conditions :
       - Si le message contient “bonjour” → réponse fixe : “Bonjour 👋”
       - Sinon → passer par l’AI Agent
    3. Relier les deux chemins vers Respond to Webhook

    ---

    PARTIE 6 – SORTIE CONTRÔLÉE

    Objectif : standardiser la réponse HTTP.

    Tâches :
    1. Avant Respond to Webhook, ajouter un nœud SET
    2. Construire la réponse :
       {
         "reply": "<réponse de l’agent>",
         "source": "ai-agent",
         "sessionId": "<execution.id>"
       }

    ---

    DONNÉES DE TEST

    POST /chatbot
    {
      "chatInput": "Bonjour, peux-tu m'expliquer n8n ?"
    }

    POST /chatbot
    {
      "chatInput": "De quoi parlions-nous juste avant ?"
    }

    ---

    CRITÈRES DE RÉUSSITE

    - Le chatbot répond via HTTP
    - La mémoire influence la réponse
    - Les messages simples contournent l’IA
    - Le JSON de sortie est propre et consistant

    ---

    ROUTINE D’ENTRAÎNEMENT (10 min)

    - Refaire le workflow sans regarder
    - Changer le modèle LLM
    - Modifier l’instruction système
    - Tester des pertes de contexte

    ---

    FIN DE L’EXERCICE

    Fait par **Microsoft Copilot**
