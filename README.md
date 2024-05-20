# proyecto2-telematica
# Integrantes
- Juan Jose Muñoz Florez
- Luis Felipe Urquijo Vargas
- Juan Pablo Ramirez

En este proyecto, implementaremos una aplicación de WordPress utilizando MicroK8s. Para ello, hemos optado por utilizar Google Cloud Platform (GCP), donde hemos creado instancias para actuar como nodo master y nodos worker, donde ejecutaremos MicroK8s. Esta herramienta nos facilita la creación de un clúster de Kubernetes personalizado. Además, hemos intentado configurar una máquina adicional como servidor NFS para garantizar la persistencia de los datos de WordPress y la base de datos en caso de que algún pod falle.

![image](https://github.com/juanvx6/proyecto2-telematica/assets/96350704/19076f3a-cd7a-4674-9c6f-6c09c6bdd926)
![image](https://github.com/juanvx6/proyecto2-telematica/assets/96350704/6762f1e9-702c-4b41-bbb1-68938099b8a2)
![image](https://github.com/juanvx6/proyecto2-telematica/assets/96350704/fa5293c4-3304-46cf-8209-ed5ec4163da6)

Luego, Creamos un cluster EKS, este cluster es donde vamos a subir toda nuestra aplicación, vamos a linkearlo con la VPC que creamos, esta VPC 
tambien debe tener un grupo de seguridad el cual puede ser por defecto o uno creado. El EKS cluster hay que crear nodos que van a contener los 
pods de nuestra app, se puede configurar por medio de cloudshell o desde la interfaz del cluster EKS.

![image](https://github.com/juanvx6/proyecto2-telematica/assets/96350704/7e25732d-41a3-4968-940d-e311f761d1c8)

Para la configuración de kubernetes, ingresamos al cluster utilizando el comando:
- aws eks --region us-east-1 update-kubeconfig --name reto4T

Ya con esto estamos linkeados con el cluster de kubernetes.
Luego pegamos todos los archivos de este repositorio en una carpeta llamada "wordpress", ejecutamos el comando:

- kubectl apply -f wordpress

Esto va a generar todos los servicios y despliegues necesarios que estan configurados en los archivos .yaml, donde se encuentra:

- Balanceador de carga
- Servicio de base de datos
- Wordpress
- Configuraciones de volumen, paths, direcciones, etc.

Formando la aplicación de kubernetes.
Nota: No generamos el servicio NFS.
