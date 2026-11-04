# Plan d'autonomie du moteur ModProd

## Situation initiale vérifiée

Le fork contient la bibliothèque Morphe Patcher et ses sources Kotlin, mais `build.gradle.kts` déclare encore :
- `com.github.MorpheApp:ARSCLib` via JitPack ;
- `com.github.MorpheApp.smali:smali` via JitPack ;
- `https://maven.pkg.github.com/MorpheApp/registry` ;
- `group = "app.morphe"` et la publication GitHub Packages vers `MorpheApp/morphe-patcher`.

Ces éléments ne doivent **pas** être modifiés aveuglément : l'ordre de migration commence par une compilation réussie de cette base.

Le dépôt `MOD-PROD/modprod-apk-creator` utilise quant à lui le plugin Gradle `app.morphe.patches` version `2.0.0` depuis le registre `MorpheApp/registry`. Ce plugin ne provient pas directement du seul module patcher forké. **Le fork du patcher ne suffit pas à rendre toute la fabrique indépendante.**

## Étapes

1. Exécuter un build de référence reproductible `./gradlew build` sur GitHub Actions avec Java 21 ;
2. identifier les dépendances amont et leurs versions ; contrôler les licences de chaque bibliothèque ;
3. construire et stocker nos propres artefacts des bibliothèques nécessaires, y compris smali et ARSCLib si leurs licences le permettent ;
4. maintenir ou remplacer séparément le plugin Gradle de compilation de patches `app.morphe.patches` ;
5. publier les composants validés dans des packages ModProd, avec métadonnées et notices correctes ;
6. migrer `modprod-apk-creator` vers ces coordonnées après test ;
7. migrer le moteur historique d'APK Factory V2 en conservant une voie de retour ;
8. tester les APK générés (installabilité, signature, mises à jour et compatibilité Android TV).

## Garde-fous

- Aucune clé privée, secret GitHub, mot de passe de signature ou artefact utilisateur dans le dépôt.
- Pas de publication automatique tant que la chaîne de publication ModProd n'est pas validée.
- Aucune modification du site de production `apk-factory.modprod.app` ni du dépôt APK Factory V1.
- Le fork reste sous GPLv3 ; conserver ses avis d'attribution.
