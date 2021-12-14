# packer-course-bootstrap

## Kickstart 

### Installation éléments manquant :

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
