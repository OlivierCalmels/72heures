# Sac 72 h

Site : https://oliviercalmels.github.io/72heures/

Un site d'une seule page pour aider chaque foyer à constituer son sac d'évacuation d'urgence, d'après la liste du guide gouvernemental « Tous responsables » ([info.gouv.fr](https://www.info.gouv.fr/risques/se-preparer-a-une-situation-durgence)).

## Fonctionnalités

- **Checklist** classée par importance (indispensable, important, utile), avec la distinction entre la liste officielle et les alternatives.
- **Bilan des besoins vitaux** : boire, manger, avoir chaud, faire du feu, s'orienter… Chaque besoin peut être couvert de plusieurs façons, et le site indique s'il est couvert, partiel ou manquant.
- **Calcul selon le foyer** : les quantités (eau, nourriture, argent, masques…) suivent le nombre de personnes, et les articles individuels (vêtements, couvertures, lampes, sifflets…) ont une case par personne, avec prénoms facultatifs.
- **Résumé « Il vous manque »** en haut de la liste : ce qui manque, par niveau d'importance et par personne.
- **Dossier de documents** : plan familial, itinéraires d'évacuation, proches (avec suggestions), services publics, radios, numéros d'urgence, photos et scans.
- **Impression d'un bloc** du dossier et de la checklist.
- **Export pour clé USB** : une page HTML autonome qui s'ouvre sans connexion.
- **Sauvegarde complète** : « Exporter tout » produit un fichier `.json` à réimporter sur un autre navigateur.

## Données et vie privée

Rien n'est envoyé sur un serveur. Le site est entièrement statique :

| Donnée | Où elle est stockée |
|---|---|
| Cases cochées, dates de péremption, foyer, dossier texte | `localStorage`, clé `sac72h:v1` |
| Photos et scans | IndexedDB, base `sac72h`, magasin `files` (le `localStorage` est limité à environ 5 Mo) |

Les deux sont effacés quand l'utilisateur vide les données du site. D'où le bouton « Exporter tout » dans l'en-tête, et le rappel quand aucun export n'a été fait depuis 30 jours.

Format d'export :

```json
{ "app": "sac72h", "version": 1, "exportedAt": "2026-10-25T08:40:00.000Z", "state": { }, "files": [ ] }
```

## Publier sur GitHub Pages

1. Poussez ce dépôt sur GitHub.
2. Dans **Settings → Pages**, choisissez **Deploy from a branch**, branche `main`, dossier `/ (root)`.
3. Le site est en ligne quelques minutes plus tard à https://oliviercalmels.github.io/72heures/

## Configuration

- **Liens affiliés Amazon** : renseignez votre identifiant Partenaires dans la constante `AFFILIATE_TAG`, en haut du script de `index.html`.
- **Articles et besoins** : modifiez les tableaux `ITEMS` (champ `p` pour l'importance, `off` pour la liste officielle) et `NEEDS` (solutions possibles pour chaque besoin).
- **Ressources et vidéos** : tableau `RESOURCES`.

## Avertissement

Ce site n'est pas un site officiel du Gouvernement. En cas d'urgence, appelez le 112.
