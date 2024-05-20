# proyecto2-telematica
# Integrantes
- Juan Jose Muñoz Florez
- Luis Felipe Urquijo Vargas
- Juan Pablo Ramirez

## Requerimientos del Proyecto

- **Implementación en grupo**.
- **Despliegue en GCP o AWS**. Cada estudiante recibirá una invitación para unirse a la nube GCP.
- **Despliegue de un clúster Kubernetes con Microk8s en al menos tres (3) máquinas virtuales**.
- **No utilizar un clúster como servicio gestionado por el proveedor**.


En este proyecto, implementaremos una aplicación de WordPress utilizando MicroK8s. Para ello, hemos optado por utilizar Google Cloud Platform (GCP), donde hemos creado instancias para actuar como nodo master y nodos worker, donde ejecutaremos MicroK8s. Esta herramienta nos facilita la creación de un clúster de Kubernetes personalizado. Además, hemos intentado configurar una máquina adicional como servidor NFS para garantizar la persistencia de los datos de WordPress y la base de datos en caso de que algún pod falle.

## Pasos Realizados

### 1. Configuración de las Máquinas Virtuales

Se crearon tres instancias en AWS con los siguientes nombres:
- `microk8s-master`
- `microk8s-worker-01`
- `microk8s-worker-02`
- `NFS`
![image](https://github.com/juanvx6/proyecto2-telematica/assets/96350704/19076f3a-cd7a-4674-9c6f-6c09c6bdd926)
Cada instancia fue configurada con los siguientes comandos:

```sh
sudo apt update && sudo apt upgrade -y
sudo apt install snapd
sudo snap install microk8s --classic
```
### 2. Activación de Servicios en Microk8s

En cada instancia, se ejecutaron los siguientes comandos para activar servicios adicionales:

sudo microk8s enable dashboard
sudo microk8s enable dns
sudo microk8s enable registry
sudo microk8s enable istio
sudo microk8s dashboard-proxy
![image](https://github.com/juanvx6/proyecto2-telematica/assets/96350704/6762f1e9-702c-4b41-bbb1-68938099b8a2)
![image](https://github.com/juanvx6/proyecto2-telematica/assets/96350704/fa5293c4-3304-46cf-8209-ed5ec4163da6)

### 3. Configuración del Clúster

En microk8s-master ejecutamos el siguiente comando dos veces para obtener los tokens de unión de nodos

```sh
sudo microk8s add-node
```

### 4. Configuración de Archivos YAML
Se configuraron los archivos YAML necesarios para el despliegue de la aplicación y otros recursos en el clúster.

### 5. Configuración del Servidor NFS
Aunque configuramos los archivos YAML, encontramos problemas con la configuración del servidor NFS. Este aspecto no fue completado exitosamente.

![image](https://github.com/juanvx6/proyecto2-telematica/assets/96350704/0a71e8f3-1dcc-4653-8219-3228938488a5)


### Aspectos Cumplidos
- Creación y configuración de máquinas virtuales en GCP.
- Instalación y configuración de Microk8s en cada instancia.
- Activación de servicios adicionales en Microk8s (dashboard, dns, registry, istio).
- Configuración del clúster de alta disponibilidad con Microk8s.
- Despliegue de la aplicación mediante archivos YAML.
- Configuración de wordpress
- Configuración del balanceador de carga entre los servicios de wordpress

### Aspectos No Cumplidos
- Configuración y funcionamiento del servidor NFS para volúmenes compartidos.
- Certificado SSL con let's encrypt

