# Supervandal &mdash; builds

Builds Android publiques des jeux et prototypes construits avec le moteur Supervandal.

**Page de telechargement : <https://supervandal-games.github.io/supervandal-builds/>**

Chaque projet a sa propre page, son propre historique et son propre flux de mise a
jour. Les APK sont attaches aux *Releases* de ce depot ; le depot lui-meme ne
contient que le site statique, jamais de binaire versionne.

## Installer

1. Ouvrir <https://supervandal-games.github.io/supervandal-builds/> sur un telephone Android (ou scanner le QR code de la page).
2. Telecharger l'APK et autoriser l'installation depuis cette source si Android le demande.
3. Les mises a jour suivantes sont proposees directement dans le jeu au demarrage.

Ce sont des builds de test : non signees pour le Play Store, parfois cassees, et
elles ecrivent des logs verbeux. C'est le but.

## Mise a jour automatique

Chaque projet expose `https://supervandal-games.github.io/supervandal-builds/<projet>/latest.json` :

```json
{
  "versionName": "0.4.358",
  "versionCode": 43580,
  "apkUrl": "https://github.com/.../releases/download/...apk",
  "sha256": "..."
}
```

L'application compare `versionCode` a celui de l'APK installe au demarrage et
propose l'installation de la nouvelle version le cas echeant.

## Publier

Depuis le depot du moteur (prive) :

```bash
python tools/publish_android.py <projet>
```

---

Moteur, editeur et outils : [Supervandal](https://github.com/Supervandal-Games) &middot;
Site genere par `tools/publish_android.py`.
