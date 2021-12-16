# packer-course-bootstrap

## Kickstart 

### Installation éléments manquants :

```
Yum install qemu-kvm
Yum install ansible
```

Activation du service libvirtd :

```
systemctl start libvirtd
```

installer également : 
```
dnf install '@Virtualization Host'
```


#### Générer le mot de passe de root

```bash
openssl passwd -6
```
La suite de caractére obtenu est a spécifier de la maniére suivante :
```ks
rootpw --iscrypted <password>
```


### Build l'image de rocky

Une fois les éléments manquants installés, nous pouvons passer au build de notre image rocky avec packer.
Pour cela, lancer la commande : 

```
packer build rocky-8.pkr.hcl
```

Le build prend en moyenne 10 à 15 minutes, durant cette période, il est possible de se connecter en VNC pour vérifier que tout ce passe bien.


## Debug

#### Augmenter le niveau de log de packer

Avant de lancer Packer définissez la variable d'environnement 'PACKER_LOG'.

```bash
export PACKER_LOG=1
```
#### Augmenter le niveau de log d'Ansible
Dans votre fichier PAcker, ajouter la configuration suivante au provisionner d'Ansible.

```hcl
    extra_arguments = [ "-vv" ]
```


## Axe d'amélioration :

Il faudrait ensuite créer un service golang-myip et activer ce dernier au démarrage de la VM.
