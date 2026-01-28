# McpCore
Architecture de référence pour le Model Context Protocol (MCP) en .NET.

## Structure du projet
Ce repository centralise trois composants clés :
1. SimpleMCP : Serveur local (Stdio) gérant les données utilisateur et calculs géométriques.
2. RemoteMCP : Serveur distant (HTTP/SSE) agissant comme passerelle vers l'API OpenWeatherMap.
3. McpClient : Orchestrateur console capable de fusionner et d'utiliser les outils des deux serveurs.

## Architecture
Le client utilise une approche modulaire (Infrastructure et Services) pour piloter simultanément un flux de données local et une API externe via un LLM.
