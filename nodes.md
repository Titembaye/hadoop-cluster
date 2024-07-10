# Préparation des Nœuds

## Configuration des Hôtes

1. Modifier le fichier `/etc/hosts` sur chaque nœud :

    ```bash
    sudo nano /etc/hosts
    ```

    Ajouter les lignes suivantes :

    ```
    192.168.1.1 master
    192.168.1.2 slave01
    192.168.1.3 slave02
    ```

## Installation de Java

1. Installer Java sur chaque nœud :

    ```bash
    sudo apt update
    sudo apt install openjdk-8-jdk -y
    ```

2. Vérifier l'installation de Java :

    ```bash
    java -version
    ```

## Configuration SSH

1. Configurer l'authentification SSH sans mot de passe :

    ```bash
    ssh-keygen -t rsa -P ""
    ssh-copy-id master
    ssh-copy-id slave01
    ssh-copy-id slave02
    ```

2. Vérifier la connexion SSH :

    ```bash
    ssh master
    ssh slave01
    ssh slave02
    ```

