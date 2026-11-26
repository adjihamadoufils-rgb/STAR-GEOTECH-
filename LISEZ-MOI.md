# STAR GEOTECH – projet APK

Ce dossier enveloppe l'application web `www/index.html` dans une application Android (Capacitor).
L'APK obtenu est une version **debug** : installable sur votre téléphone, mais pas publiable sur le Play Store.

**Important : je n'ai pas pu compiler cet APK moi-même.** Les versions des outils sont à confirmer au premier build.

## Méthode A – GitHub (sans installer Android Studio)
1. Créez un compte gratuit sur github.com, puis un nouveau dépôt.
2. Envoyez-y **tout le contenu** de ce dossier, en gardant le dossier `.github/workflows` (le fichier `android.yml`).
3. Onglet **Actions** → **Build APK** → **Run workflow**. Attendez la fin (quelques minutes).
4. Ouvrez l'exécution terminée, téléchargez l'artefact **STAR-GEOTECH-apk** (un zip contenant `app-debug.apk`).
5. Copiez `app-debug.apk` sur le téléphone et ouvrez-le. Autorisez l'installation depuis cette source si Android le demande.

## Méthode B – ordinateur avec Android Studio (et Node 20)
```
npm install
npx cap add android
npx capacitor-assets generate --android
npx cap sync android
npx cap open android
```
Dans Android Studio : *Build → Build Bundle(s) / APK(s) → Build APK(s)*.

## Ce qui change dans la version APK
- **Export JSON, CSV et rapports** : un menu de partage Android s'ouvre (enregistrer dans Fichiers, Drive, WhatsApp…).
- **Rapport PDF** : le bouton « Partager le rapport » envoie un fichier HTML ; ouvrez-le dans Chrome puis *Imprimer → Enregistrer au format PDF*.
- Les données restent dans l'application. **Exportez une sauvegarde avant de désinstaller ou de mettre à jour.**

## Mettre à jour l'application
Remplacez `www/index.html` par la nouvelle version, puis relancez le workflow (ou la méthode B).

## Pour une publication sur le Play Store
Il faut une version *release* signée avec votre propre clé : non couverte ici.
