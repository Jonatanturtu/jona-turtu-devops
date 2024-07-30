# Introduccion Ansible

## Crear un entorno virtual:
Crear tres maquinas virtuales con multipass:
controller: controlador de ansible.
node1: nodo de aplicacion.
node2: nodo de base de datos.

```
multipass launch -n <vm-name>
```

Links:
- [Multipass](https://multipass.run/)
- [Documentacion Multipass](https://multipass.run/docs)

## tomar la shell de multipass
```bash
multipass shell <vm-name>
```
utilizar la instruccion de instalacion para ubuntu.

## Como instalar ansible:

MacOS:
```
brew install ansible
```
Linux:
```
sudo apt-get install ansible
```
Windows:
```
pip install ansible
```
Para el caso de windows es necesario tener instalado python y pip.
Links:
- [Instalar Python](https://www.python.org/downloads/)
- [Instalar Pip](https://pip.pypa.io/en/stable/installing/)
- [Instalar Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

## Verificar si ansible esta instalado

```bash
ansible --version
```

## Montar un proyecto local a la vm controller.

Dentro de la maquina controller crear el directorio project:

```bash
mkdir project
```

Luego de crear el directorio, montar el directorio local al directorio project de la vm controller.

```bash
multipass mount <path al repo ansible> controller:/home/ubuntu/project
```
Controller es el nombre de la vm.

Si resive un error para montar debe ejeeutar el siguiente comando:
```bash
multipass set local.privileged-mounts
```

Links:
- [comando mount multipass](https://multipass.run/docs/share-data-with-an-instance)

## netcat herramienta de red.

Si necesitamos comprobar que puedo acceder a un puerto en una maquina remota puedo ejecutar el siguiente comando

```bash
nc -zv <ip> <puerto>
```

## generar una ssh-key

```bash
ssh-keygen
```

## copiar la llave publica a la maquina remota
Cuando utilizamos claves publicas y privadas para conectarnos a una maquina remota, debemos copiar la llave publica a la maquina remota.

```bash
cat ~/.ssh/<file_name>.pub
```
Copiar el contenido de la llave publica y pegar en el archivo ~/.ssh/authorized_keys de la maquina remota.

Otra forma de copiar la llave publica a la maquina remota es utilizando el comando ssh-copy-id
```bash
ssh-copy-id -i ~/.ssh/<file_name>.pub ubuntu@<ip>
```

## actualizar el archivo de inventario

```txt
[webservers]
node1 ansible_host=<ip>
[webservers:vars]
ansible_user=ubuntu
ansible_ssh_private_key_file=~/.ssh/<file_name>.pub
```

## verificar la conexion de ansible con la maquina remota

```bash
ansible all -i inventory.ini -m ping
```
## como ejecutar mi playbook

```bash
ansible-playbook -i inventory.ini main.yml
```

## modulos de ansible
Links:
- [Documentacion sobre modulos](https://docs.ansible.com/ansible/latest/plugins/module.html)


