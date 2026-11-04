# ModProd Patcher

Fork indépendant de la bibliothèque open source [Morphe Patcher](https://github.com/MorpheApp/morphe-patcher), maintenu pour **APK Factory V2** par MOD-PROD.

> **État : étape de préparation / validation.** Le dépôt est une copie du moteur de patch, mais son build utilise encore certaines dépendances de l'écosystème Morphe. Il ne remplace pas encore le moteur de production d'APK Factory V2.

## Rôle

- Modifier le bytecode Dalvik des applications Android ;
- modifier leurs ressources et fichiers APK ;
- permettre les patches Kotlin de `MOD-PROD/modprod-apk-creator` ;
- reconstruire une chaîne de compilation contrôlée par ModProd.

## État de l'indépendance

- Sources du moteur disponibles dans ce dépôt : **oui**.
- Tests de build sur GitHub Actions : **configurés** ; consulter Actions pour les résultats.
- Publication Maven ModProd : **non activée**.
- Suppression complète des dépendances amont : **non réalisée**.
- Remplacement du CLI Morphe dans APK Factory V2 : **non réalisé**.

Les versions des dépendances sont dans `gradle/libs.versions.toml`. Les coordonnées Gradle `app.morphe` et les packages JVM restent provisoirement identiques à l'amont pour assurer la compatibilité binaire. **Cela n'autorise pas l'utilisation de la marque Morphe pour identifier ce fork.**

## Tests

Les workflows GitHub Actions exécutent `./gradlew test build` à chaque push sur `main`.
La publication héritée de Morphe est désactivée dans ce fork en attendant notre pipeline de publication contrôlé.

## Licence et attribution

Ce logiciel dérive de Morphe Patcher, lui-même issu de travaux antérieurs de ReVanced. Il reste sous **GNU GPLv3**. Les fichiers [LICENSE](LICENSE) et [NOTICE](NOTICE) d'origine sont conservés. Les marques et logos de Morphe ne sont pas réutilisés comme identité du fork.

Voir [AUTONOMIE.md](AUTONOMIE.md) pour le plan technique.
