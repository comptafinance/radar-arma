# RADAR ARMA

Application de suivi des affaires ARMA pour la DR Paris, publiée par Astridsen.

## Ce que c'est

Une page unique, `index.html`, qui tourne entièrement dans le navigateur.
Aucune installation, aucun compte à créer côté utilisateur.

## Où sont les données

Elles ne sont pas dans le fichier HTML. Elles vivent dans Supabase.

- Projet : `coqlmzzlddjysxyavzof.supabase.co`
- Table : `arma_state`, une seule ligne `id = 1`
- Colonne `data` : l'état complet de l'application en JSON, plus `updated_at`

L'application relit la ligne, fusionne, puis réécrit à chaque enregistrement.
Elle interroge aussi Supabase périodiquement pour récupérer les modifications
des autres postes. Déployer une nouvelle version de `index.html` n'efface donc
aucune donnée.

La table `user_roles` sert à la gestion des droits.

Le navigateur garde une copie locale de secours sous les clés `radar_*`
du localStorage, utilisée si Supabase est injoignable.

## Publication

Le site est servi par GitHub Pages depuis la branche `main`, à la racine.
Toute modification poussée sur `main` est en ligne en une à deux minutes.

## Historique

Chaque version est conservée par git. Pour revenir à une version antérieure,
`git log` puis `git revert`. Rien ne se perd.
