# Supervandal &mdash; builds

Builds publiques des jeux et prototypes construits avec le moteur Supervandal.

**Page de telechargement : <https://supervandal-games.github.io/supervandal-builds/>**

## Pistes

Un projet publie une ou plusieurs **pistes** (`alpha1`, `alpha2`, `demo`...). Chaque piste
est une **application distincte** sur le telephone :

- publier deux fois sur `alpha1` &rarr; la seconde build **remplace** la premiere ;
- publier sur `alpha2` &rarr; une **seconde application**, a cote de `alpha1`.

On peut donc garder une ancienne alpha installee pendant qu'on teste la suivante.

```
https://supervandal-games.github.io/supervandal-builds/android/<projet>/                   les pistes du projet
https://supervandal-games.github.io/supervandal-builds/android/<projet>/<piste>/           page, QR code, historique
https://supervandal-games.github.io/supervandal-builds/android/<projet>/<piste>/latest.json  flux de mise a jour
```

Les binaires sont attaches aux *Releases* de ce depot ; le depot lui-meme ne contient que
le site statique, jamais de binaire versionne.

Android est la seule plateforme publiee pour l'instant. Le chemin commence par `android/`
pour qu'une build Windows vienne s'ajouter sans casser un lien deja distribue.

## Installer

1. Ouvrir <https://supervandal-games.github.io/supervandal-builds/> sur un telephone Android, ou scanner le QR code de la page.
2. Telecharger l'APK et autoriser l'installation depuis cette source si Android le demande.
3. Les mises a jour de la meme piste sont proposees directement dans le jeu au demarrage.

Ce sont des builds de test : non signees pour le Play Store, parfois cassees, et elles
ecrivent des logs verbeux. C'est le but.

## Mise a jour automatique

Chaque piste expose son `latest.json` :

```json
{
  "appName": "Coaster Train Alpha 1",
  "package": "com.supervandal.traincoaster.alpha1",
  "versionName": "1.0.2",
  "versionCode": 3,
  "apkUrl": "https://github.com/.../releases/download/...apk",
  "sha256": "..."
}
```

L'application compare `versionCode` a celui de l'APK installe au demarrage et propose
l'installation de la nouvelle version le cas echeant. Le `versionCode` est un compteur
propre a la piste : il n'a pas de rapport avec le numero de version affiche.

## Publier

Depuis le depot du moteur (prive) :

```bash
python tools/publish_android.py <projet>
```

---

Moteur, editeur et outils : [Supervandal](https://github.com/Supervandal-Games) &middot;
Site genere par `tools/publish_android.py`.
