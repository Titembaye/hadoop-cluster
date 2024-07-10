# Configuration du Pare-feu

## Problèmes de Pare-feu Rencontrés

Pendant le déploiement, les pare-feu ont causé des interruptions dans la communication entre les nœuds. Voici comment ces problèmes ont été résolus.

## Désactiver le Pare-feu (Option Temporaire)

Pour désactiver temporairement le pare-feu sur chaque nœud :

```bash
sudo ufw disable
 ```
Verifier le status de parfeu sur chaque noeud

```bash
sudo ufw status
 ```
Autoriser les ports necessaire

# Pour le NameNode (port par défaut 9000)
```bash
sudo ufw allow 9000
```
# Pour le ResourceManager (port par défaut 8088)
```bash
sudo ufw allow 8088
```
# Pour le DataNode (port par défaut 50010)
```bash
sudo ufw allow 50010
```

# Pour le NodeManager (port par défaut 8042)
```bash
sudo ufw allow 8042
```

# Pour le SecondaryNameNode (port par défaut 50090)
```bash
sudo ufw allow 50090
```

# Appliquer les règles
```bash
sudo ufw reload
```


