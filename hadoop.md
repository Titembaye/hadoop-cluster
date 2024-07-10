# Installation et Configuration de Hadoop

## Téléchargement et Installation de Hadoop

1. Télécharger Hadoop sur le nœud master :

    ```bash
    wget https://downloads.apache.org/hadoop/common/hadoop-3.3.1/hadoop-3.3.1.tar.gz
    tar -xzvf hadoop-3.3.1.tar.gz
    mv hadoop-3.3.1 /usr/local/hadoop
    ```

2. Configurer les variables d'environnement :

    ```bash
    nano ~/.bashrc
    ```

    Ajouter les lignes suivantes :

    ```bash
    export HADOOP_HOME=/usr/local/hadoop
    export HADOOP_INSTALL=$HADOOP_HOME
    export HADOOP_MAPRED_HOME=$HADOOP_HOME
    export HADOOP_COMMON_HOME=$HADOOP_HOME
    export HADOOP_HDFS_HOME=$HADOOP_HOME
    export YARN_HOME=$HADOOP_HOME
    export HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native
    export PATH=$PATH:$HADOOP_HOME/sbin:$HADOOP_HOME/bin
    ```

3. Appliquer les modifications :

    ```bash
    source ~/.bashrc
    ```

## Configuration des Fichiers Hadoop

1. Modifier `core-site.xml` :

    ```bash
    nano $HADOOP_HOME/etc/hadoop/core-site.xml
    ```

    Ajouter :

    ```xml
    <configuration>
        <property>
            <name>fs.defaultFS</name>
            <value>hdfs://master:9000</value>
        </property>
    </configuration>
    ```

2. Modifier `hdfs-site.xml` :

    ```bash
    nano $HADOOP_HOME/etc/hadoop/hdfs-site.xml
    ```

    Ajouter :

    ```xml
    <configuration>
        <property>
            <name>dfs.replication</name>
            <value>2</value>
        </property>
    </configuration>
    ```

3. Modifier `yarn-site.xml` :

    ```bash
    nano $HADOOP_HOME/etc/hadoop/yarn-site.xml
    ```

    Ajouter :

    ```xml
    <configuration>
        <property>
            <name>yarn.resourcemanager.hostname</name>
            <value>master</value>
        </property>
    </configuration>
    ```

4. Modifier `mapred-site.xml` :

    ```bash
    cp $HADOOP_HOME/etc/hadoop/mapred-site.xml.template $HADOOP_HOME/etc/hadoop/mapred-site.xml
    nano $HADOOP_HOME/etc/hadoop/mapred-site.xml
    ```

    Ajouter :

    ```xml
    <configuration>
        <property>
            <name>mapreduce.framework.name</name>
            <value>yarn</value>
        </property>
    </configuration>
    ```

## Démarrage des Services Hadoop

1. Formater le NameNode :

    ```bash
    hdfs namenode -format
    ```

2. Démarrer les services Hadoop :

    ```bash
    start-dfs.sh
    start-yarn.sh
    ```

3. Vérifier le statut des services :

    ```bash
    jps
    ```

