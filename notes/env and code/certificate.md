# Certificate

Si une URL génère des erreurs de certificats.

Si c'est le cas il va falloir :
- Récupérer le certificat.
- L'ajouter sur votre poste.

## Récupérer le certificat
Dans un navigateur aller sur l'URL en question.

A gauche de la barre d'url il devrait y avoir un cadenas.
- Cliquez sur le cadenas
- "La connexion est sécurisé >"
- "Certificat Valide"

Cela va ouvrir une fenêtre d'information sur le certificat.
- Onglet détails.
- "Copier dans un fichier..."

Enregistrez le certificat sur votre poste.

## Ajouter le certificat dans votre truststore
Dans l'invite de commande: 
- {{KEYTOOL}} -import -keystore {{LOCAL_TRUSTSTORE}} -storepass changeit -alias {{ALIAS}} -file {{NEW_CERTIFICATE}}

{{KEYTOOL}} : le chemin du keytool dans votre JDK, dans mon cas : "C:\Program Files\Java\jdk1.8.0_202\bin\keytool.exe" (les guillemets sont a ajouter dans la ligne de commande).
{{LOCAL_TRUSTSTORE}} : là ou vous avez votre fichier cacert.jks, ce fichier est utiliser dans la config de votre tomcat en tant qu'argument VM, dans mon cas : C:\...\java_security\cacert.jks (pas de guillemet).
{{ALIAS}}: donner un nom au certificat (par exemple api-staging-oney-io, oui int-compte-oney)
{{NEW_CERTIFICATE}} : le chemin du certificat récupéré dans l'étape précédente, dans mon cas : C:\BaDevEnv-3.0\java_security\cap.cer (pas de guillemet? j'ai du le faire avec la seconde fois).

## Exemple
```bash
"C:\Program Files\Java\jdk1.8.0_202\bin\keytool.exe" -import -keystore C:\BaDevEnv-3.0\java_security\cacert.jks -storepass changeit -alias api-staging-oney-io -file C:\BaDevEnv-3.0\java_security\capInt.cer
```