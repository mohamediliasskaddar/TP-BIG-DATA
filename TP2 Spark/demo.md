
# Rapport de Démonstration Spark


## 1. Préparation de l’environnement

Avant la démonstration, certains fichiers peuvent être supprimés pour garantir la clarté des résultats.

### 1.1 Fichiers de sortie précédents

Dans les projets WordCount ou Streaming, les dossiers de sortie tels que `out` ou `file1.count` peuvent contenir des résultats des exécutions précédentes. Pour repartir sur une base propre, ces fichiers peuvent être supprimés :

```bash
rm -r src/main/resources/out
hdfs dfs -rm -r /user/root/output
````

### 1.2 Fichiers temporaires Spark (optionnel)

Spark crée des fichiers temporaires pour gérer les micro-batches dans le répertoire `/tmp`. Ces fichiers peuvent être supprimés afin d’améliorer la lisibilité de la console lors de la démonstration :

```bash
rm -r /tmp/temporary-*
```

### 1.3 Logs anciens

Si la sortie des jobs Spark est redirigée vers un fichier (par exemple `out`), il est recommandé de supprimer le fichier existant pour que le nouveau contienne uniquement les résultats de la démonstration :

```bash
rm out
```

---

## 2. Éléments à conserver

Certains éléments ne doivent pas être supprimés afin d’assurer le bon fonctionnement de la démonstration :

* Le code Java : `WordCountTask.java` et `Stream.java`
* Le fichier JAR Maven généré (ex. `stream-1.jar`)
* Les dépendances Maven dans le répertoire `target/` ainsi que le fichier `pom.xml`
* Les répertoires source du projet : `src/main/java` et `src/main/resources`
* Les démons Hadoop et YARN si la démonstration est effectuée sur un cluster (le script `start-hadoop.sh` doit être actif)
* La commande `nc -lk 9999` durant l’exécution du streaming

---

## 3. Procédure recommandée pour une démonstration propre

1. Arrêter tous les jobs Spark en cours d’exécution (Ctrl-C)
2. Supprimer les anciens fichiers de sortie (`out`, `file1.count`)
3. Lancer en premier la commande pour créer le flux de données :

```bash
nc -lk 9999
```

4. Exécuter ensuite le job Spark avec `spark-submit` :

```bash
spark-submit --class spark.streaming.tp22.Stream --master local stream-1.jar > out
```

5. Saisir quelques messages dans le terminal `nc` pour générer le flux de données et observer la sortie dans la console ou le fichier `out`.

---
