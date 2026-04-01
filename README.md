# Serre-fleurs
Pour mon projet de fin d'année en TSTI2D, je dois créer un site web avec lequel pourra interagir une carte arduino, afin de publier périodiquement des valeurs de capteurs situés dans une serre (température, humidité ...). Le site pourra proposer un affichage statistique.

Le site aura une api REST exposée pour recevoir les valeurs relevées sur les capteurs tous les x temps.
Chaque update sera enregistrée dans un fichier JSON avec la structure suivante:
"$timestamp.json":
```JSON
{
  "moist": $val,
  "temp": $val
}
```
pour les endpoints:
## PUT
endpoints réservés à la carte arduino, ils permettent à la carte arduino d'envoyer les valeurs d'humidité et de température relevées. 
- /api/moist (humidité)
- /api/temp (température)
## GET
- /api/moist?recursive = false
- /api/temp?recursive = false

soit le paramètre `recursive` (default false):
- if false:
  - donne la dernière valeur en date
- else
  - donne les dix dernières valeurs
