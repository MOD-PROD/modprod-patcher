# Compatibilité binaire du moteur

Référence : `api/morphe-patcher.api` (mise à jour uniquement avec deux signatures **supplémentaires**, après comparaison du diff GitHub Actions ; les anciennes déclarations ont été conservées).

Les sources du fork avaient quatre différences au contrôle `apiCheck` :
- `Patcher.invoke(): Flow<PatchResult>` supprimée au profit de l'overload avec callback ;
- `BytecodePatch.toString()`, `RawResourcePatch.toString()` et `ResourcePatch.toString()` absentes en tant que méthodes déclarées dans les classes finales.

La correction ajoute un vrai overload `invoke()` qui délègue à l'implémentation avec callback, et réintroduit les trois overrides `toString()`, sans modifier le comportement.

Le CI exécute **`apiCheck` sans `continue-on-error`**. Un artefact JAR n'est publié par le workflow que lorsque `test`, `jar` et `apiCheck` réussissent. Les tests d'intégration avec les patches ModProd et le CLI restent une étape distincte à valider.

L'annotation `@JvmOverloads` produit la surcharge JVM à zéro argument et conserve la fonction Kotlin originale avec callback, pour préserver le comportement de MockK et des clients existants.
