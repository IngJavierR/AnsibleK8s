# Ansible

## Instalación

_Instalación de Ansible:_

### Pre-requisitos

_Generar un usuario con permisos de administrador:_

```bash
sudo adduser username
passwd username
sudo gpasswd -a username wheel
```

_Conectar mediante ssh:_

```bash
ssh-keygen
ssh-copy-id user@ipdaddres
```

### Habilitar Ambiente

_Habilitar un servidor completo:_

```bash
# Instalar herramientas

ansible-playbook install.yml --limit serversdev

# Instalar plugins de jenkins

ansible-playbook jenkins-plugins-playbook.yml --limit serversdev

# Configurar Jenkins Slave y notificaciones
https://medium.com/appgambit/integrating-jenkins-with-slack-notifications-4f14d1ce9c7a

https://yallalabs.com/devops/how-to-add-linux-slave-node-agent-node-jenkins/
```

_Habilitar por partes:_

```bash
# Instalar jenkins
ansible-playbook jenkins-playbook.yml --limit serverstest
# Instalar jenkins plugins
ansible-playbook jenkins-plugins-playbook.yml --limit serverstest
# Instalar Kubernetes
ansible-playbook kubernetes/prerequisites.yml --limit serverstest
ansible-playbook kubernetes/setting_up_nodes.yml --limit serverstest
ansible-playbook kubernetes/configure_master_node.yml --limit serverstest
# Instalar Netcore, SonarScanner, Chrome, Liquibase
ansible-playbook utils.yml --limit serverstest
```

### Herramientas

_Para la instalación se necesita:_

* [Docker](https://docs.docker.com/install/)  

### Contributors

_Aquí van los colaboradores:_

Javier Rodríguez  
[francisco.rodriguez@axity.com]
