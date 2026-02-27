## Relancement du job

Hadoop ne permet pas d’écraser un dossier output.

l'erreur :

Output directory already exists

```
hdfs dfs -rm -r /user/root/output
```
puis relance :
```
hadoop jar wordcount.jar /user/root/input /user/root/output
```

## env preparation for java 8 && mvn 
```
> $env:JAVA_HOME="C:\Program Files\Java\jdk1.8.0_202"
> $env:Path="$env:JAVA_HOME\bin;$env:Path"
> java -version
java version "1.8.0_202"
Java(TM) SE Runtime Environment (build 1.8.0_202-b08)
Java HotSpot(TM) 64-Bit Server VM (build 25.202-b08, mixed mode)
```