# proyecto2-telematica
# Integrantes
- Juan Jose Muñoz Florez
- Luis Felipe Urquijo Vargas
- Juan Pablo Ramirez

Iniciamos creando una VPC en AWS, la cual va a tener 6 sub-redes 3 publicas y 3 privadas, esto con el fin de mantener una alta disponibilidad,
pues si por algun motivo una zona no esta funcionando podemos referinos a la otra.

![image](https://github.com/juanvx6/reto4Topicos/assets/96350704/d09f4da1-b467-4f13-87dd-7f467e51ab6e)

Luego, Creamos un cluster EKS, este cluster es donde vamos a subir toda nuestra aplicación, vamos a linkearlo con la VPC que creamos, esta VPC 
tambien debe tener un grupo de seguridad el cual puede ser por defecto o uno creado. El EKS cluster hay que crear nodos que van a contener los 
pods de nuestra app, se puede configurar por medio de cloudshell o desde la interfaz del cluster EKS.

![image](https://github.com/juanvx6/reto4Topicos/assets/96350704/4c0a044b-b59f-4494-8a98-50f6a5e8991d)

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
