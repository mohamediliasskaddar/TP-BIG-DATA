## Recap: Quick Recap for Demonstration Commands

### Cmd 1
```bash
hdfs dfs -tail out-spark/part-00000
````

### Cmd 2: Master Container

```bash
nc -lk 9999
```

### Cmd 3: Master Container

```bash
spark-submit --class spark.streaming.tp22.Stream --master local stream-1.jar > out
```

### Cmd 4

```bash
Ctrl + C
```

### Cmd 5

```bash
cat out
```