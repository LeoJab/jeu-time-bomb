# 💣 Time Bomb · ChadGangGames

Adaptation web de Time Bomb pour le hub ChadGangGames. Tout le jeu tient dans `index.html` : pas de build, pas de serveur.

## Contenu
- `index.html` : le jeu (HTML/CSS/JS, sons synthétisés en WebAudio, effets sur canvas)
- `chadgang.json` : la fiche du jeu pour le hub
- `cover.png` : l'image de couverture (1280×720)

## Modes
- **En ligne (dans le hub)** : « Créer une salle » donne un code de 4 lettres, et les potes rejoignent via le bouton Inviter du hub ou en tapant le code. L'hôte (premier arrivé) peut ajouter des bots pour compléter la table (4 à 8 joueurs).
- **Entraînement** : solo contre des bots, ça marche aussi hors du hub. La partie est sauvegardée dans le navigateur.

## Fonctionnement réseau
- L'hôte de la salle arbitre : les joueurs envoient leurs actions, l'hôte les valide et diffuse l'état complet versionné (`keep: true`).
- Si l'hôte part, le joueur suivant de la liste reprend automatiquement l'arbitrage et les bots.
- Recharger la page ramène dans la partie en cours.
- Un joueur déconnecté peut être remplacé : l'hôte peut lancer les coupes sans attendre son annonce, ou couper au hasard à sa place s'il avait la pince.
- L'état est brouillé dans les messages, mais pas chiffré : un petit malin qui fouille la console pourrait tricher. Entre potes, ça passe 😉

## Mettre en ligne
```bash
git init && git add . && git commit -m "Time Bomb"
git branch -M main
git remote add origin https://github.com/<toi>/jeu-time-bomb.git
git push -u origin main
```
Puis dans le hub : **Admin → Jeux → Ajouter le jeu**, et coller le lien du dépôt.
