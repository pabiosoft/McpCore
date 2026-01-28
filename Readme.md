# McpCore
Architecture de référence pour le Model Context Protocol (MCP) en .NET.

## Structure du projet
Ce repository centralise trois composants clés :
1. SimpleMCP : Serveur local (Stdio) gérant les données utilisateur et calculs géométriques.
2. RemoteMCP : Serveur distant (HTTP/SSE) agissant comme passerelle vers l'API OpenWeatherMap.
3. McpClient : Orchestrateur console capable de fusionner et d'utiliser les outils des deux serveurs.

## Architecture
Le client utilise une approche modulaire (Infrastructure et Services) pour piloter simultanément un flux de données local et une API externe via un LLM.

## Utilisation

### 1. Installation
Pour récupérer le projet et tous ses composants :
git clone --recursive git@github.com:pabiosoft/McpCore.git

### 2. Configuration
- Créer un fichier .env à la racine des projet dans /core (McpClient et RemoteMcp).
- Ajouter les clés API nécessaires (OpenAI, OpenWeatherMap).

### 3. Exécution
1. Lancer RemoteMcp (HTTP/SSE).
2. Lancer McpClient (Orchestrateur).


## Annexes

<details>
<summary> Le MCP (Model Context Protocol) en bref</summary>

### C'est quoi ? 
Le MCP est un standard ouvert qui permet aux IA (LLMs) d'accéder à des données et des outils locaux ou distants de manière sécurisée et structurée.

### À quoi ça sert ? 
Il transforme une IA "isolée" en un assistant capable de :
- Lire tes fichiers locaux.
- Interroger tes bases de données.
- Utiliser des APIs tierces.

### Exemple KISS 
- **Sans MCP** : Tu dois copier-coller la météo dans le chat.
- **Avec MCP** : L'IA appelle l'outil `get_weather` toute seule.

**Dans ce projet :**
1. **SimpleMCP** : Donne à l'IA tes coordonnées locales (i.e: Paris).
2. **RemoteMCP** : Donne à l'IA l'accès à la météo mondiale.
3. **McpClient** : Fusionne tout pour que l'IA réponde : "Il pleut à Paris, à 2km de chez toi".

</details>

<details>
<summary> Contribution et mise à jour des sous-modules</summary>

### Travailler sur un composant
Par défaut, les sous-modules sont en mode "detached HEAD". Pour contribuer :
1. `cd core/SimpleMcp`
2. `git checkout main`
3. (Modifications)
4. `git commit -m "Description"`
5. `git push origin main`

### Synchroniser le projet parent
Après avoir poussé dans un sous-module, mettez à jour le pointeur dans McpCore :
1. `cd ../..` (racine)
2. `git add core/SimpleMcp`
3. `git commit -m "Update SimpleMcp reference"`
4. `git push`

</details>

<details>
<summary>Commandes de synchronisation rapide</summary>

Pour tout mettre à jour d'un coup (pull des dernières versions de tous les modules) :
`git submodule update --remote --merge`

</details>

