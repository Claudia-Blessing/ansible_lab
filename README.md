# Déploiement Laravel avec Ansible

Ce playbook Ansible automatise le déploiement d'une application Laravel CRUD sur un serveur Ubuntu avec Nginx + PHP + MySQL.

## Prérequis

- Serveur Ubuntu/Debian avec accès SSH
- Ansible installé sur votre machine locale
- Clé SSH configurée pour l'utilisateur `deploy`
- Mot de passe MySQL chiffré dans `roles/mysql/vars/vault.yml`

## Configuration

### 1. Inventory
Modifiez `inventory.ini` avec vos informations serveur :
```ini
[webservers]
monserveur ansible_host=VOTRE_IP ansible_user=deploy ansible_private_key_file=~/.ssh/id_rsa
```

### 2. Variables MySQL
Le mot de passe MySQL est chiffré avec Ansible Vault. Pour le modifier :
```bash
ansible-vault edit roles/mysql/vars/vault.yml
```

### 3. Clé SSH
Assurez-vous que votre clé SSH publique est dans `files/deploy_key.pub`

## Déploiement

### Première exécution (avec vault)
```bash
ansible-playbook -i inventory.ini playbook.yml --ask-vault-pass
```

### Exécutions suivantes
```bash
ansible-playbook -i inventory.ini playbook.yml
```

## Structure du déploiement

Le playbook installe et configure :
- **Nginx** : Serveur web avec configuration Laravel
- **PHP 8.2** : Avec extensions nécessaires (MySQL, Curl, XML, etc.)
- **MySQL** : Base de données avec utilisateur dédié
- **Laravel** : Application clonée depuis GitHub et configurée

## Vérification

Après déploiement, accédez à `http://VOTRE_IP` pour voir l'application.

## Dépannage

- Vérifiez les logs : `ansible-playbook -i inventory.ini playbook.yml -v`
- Test SSH : `ssh deploy@VOTRE_IP`
- Logs Laravel : `tail -f /var/www/laravel/storage/logs/laravel.log`