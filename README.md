# openstack-centos7 install


![OpenStack](https://www.openstack.org/software/images/diagram/overview-diagram-new.svg)



## OpenStack

OpenStack es un conjunto de herramientas de software gratuito y de código abierto que se utiliza para la computación en la nube. Es adecuado tanto para nubes públicas como privadas. OpenStack se usa para administrar y controlar el almacenamiento de la computadora, la red y otros recursos de administración a través de un tablero. Es utilizado por muchas grandes empresas para administrar su servidor en la nube. En este artículo aprenderá cómo instalar la configuración todo en uno de OpenStack Train 


## Openstack train centos7 Install

Antes de instalar y usar Openstack, se recomienda desactivar firewalld, NetworkManager y SELinux en su máquina.

```bash
systemctl stop firewalld
systemctl disable firewalld
systemctl stop NetworkManager
systemctl disable NetworkManager
```

Ahora reinicie el servicio de red para aplicar los cambios.

```bash
systemctl restart network
```

Ahora desativamos en el SELINUX


Abra el archivo /etc/selinux/config usando el comando a continuación y modifique la línea de SELINUX=enforcing a SELINUX=disabled

```bash
vi /etc/selinux/config
```
Modificamos:
```
# This file controls the state of SELinux on the system.
# SELINUX= can take one of these three values:
#     enforcing - SELinux security policy is enforced.
#     permissive - SELinux prints warnings instead of enforcing.
#     disabled - No SELinux policy is loaded.
SELINUX=disabled
# SELINUXTYPE= can take one of three values:
#     targeted - Targeted processes are protected,
#     minimum - Modification of targeted policy. Only selected processes are protected.
#     mls - Multi Level Security protection.
SELINUXTYPE=targeted
```
Y guardamos.


Si está utilizando una configuración regional que no está en inglés, asegúrese de que su /etc/environment agregue la siguientes líneas:

```bash
vi /etc/environment
```

Agregamos:

```
LANG=en_US.utf-8
LC_ALL=en_US.utf-8
```
Guardamos y reiniciamos la maquina

```bash
reboot
```
o
```bash
init 6
```

## Vamos instalar Openstack Train


```bash
yum install centos-release-openstack-train -y
```

Packstack es una utilidad de configuración de OpenStack. use el siguiente comando para instalarlo.

```bash
yum install openstack-packstack -y
```

Instalar y ejecutar OpenStack usando Packstack

```bash
packstack --allinone
```

Acceder vamos a Url http://SERVER-IP/dashboard

Nota. Recuerde que el usuario y contraseña se encuentra en el archivo /root/keystonerc_admin


