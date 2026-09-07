# Modèles Word des modules de génération

Les modules de génération en lot du Back-Office cherchent leur modèle ici, à
côté de l'application. Un modèle déposé dans ce dossier est chargé tout seul
pour tout le monde. Tant qu'il est absent, chacun doit le déposer à la main à
chaque session.

## Fichiers attendus

| Nom exact | Module |
|---|---|
| `Modele_PPS_RADAR_tokenise.docx` | PPS |
| `Modele_avenant_DIE.docx` | Avenant DIE |
| `Modele_FDO.docx` | FDO |

Le nom compte : c'est celui que le module va chercher.

## Comment déposer un modèle

Copier le fichier dans ce dossier, puis pousser :

    git add modeles/
    git commit -m "Modele PPS"
    git push

Compter une minute avant qu'il soit en ligne.

## Ce qu'un modèle doit contenir

Les valeurs variables sont remplacées par des jetons `{{NOM_DU_CHAMP}}`. Un
jeton doit tenir dans un seul morceau de texte Word : le taper d'une traite,
sans changer de police ni de casse au milieu, sinon Word le coupe en deux et
la substitution ne le voit plus.

Jetons du PPS :

`{{N_AFFAIRE}}` `{{COMMUNE}}` `{{ADRESSE}}` `{{ENTREPRISE}}` `{{N_COMMANDE}}`
`{{N_ECC}}` `{{DATE_DEBUT}}` `{{DATE_FIN}}` `{{VALIDITE_DEBUT}}`
`{{VALIDITE_FIN}}` `{{DATE_MEO}}` `{{DATE_REUNION_PREALABLE}}`
`{{DATE_INSPECTION}}` `{{CHARGE_AFFAIRES}}` `{{MAITRE_OEUVRE}}`
`{{QUALITE_REPRESENTANT_EE}}` `{{REDACTEUR}}` `{{DATE_REDACTION}}`
`{{SIGNATAIRE_ENEDIS}}` `{{INTERLOCUTEUR_ENEDIS}}` `{{TEL_INTERLOCUTEUR}}`
`{{MAIL_INTERLOCUTEUR}}` `{{PARTICIPANT_INSPECTION}}` `{{FONCTION_PARTICIPANT}}`

Un jeton peut revenir plusieurs fois, toutes ses occurrences sont remplies.

La capture APS de la page 12 n'est pas un jeton texte : c'est l'image
`word/media/image4.png` du modèle, écrasée à chaque génération. Elle doit
rester une image de remplacement neutre dans le modèle.

## Ce que le module ne fait pas

Il ne reconstruit pas le document. Il ouvre le .docx, remplace des chaînes
dans `word/document.xml`, écrase les images, et referme. La mise en page, les
styles, les signets et les images du modèle sont donc rendus tels quels.
