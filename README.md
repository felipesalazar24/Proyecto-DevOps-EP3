# Tienda de Perritos - Infraestructura y CI/CD (EP3)

## Integrantes
* Felipe [Tu Apellido]
* [Nombre de tu Dupla]

## Componentes del Clúster (AWS EKS)
* **Frontend:** Servidor web expuesto mediante un LoadBalancer público.
* **Backend:** Microservicio encargado del procesamiento de datos y API endpoints.
* **Database:** Motor MySQL persistente mapeado localmente.

## Escalabilidad y Resiliencia
* Se implementó **Horizontal Pod Autoscaler (HPA)** sobre el despliegue del Backend, configurando un umbral de disparo del **50% de uso de CPU**, con un límite elástico de entre 1 y 3 Pods en paralelo.

## Pipeline de Automatización (CI/CD)
* El flujo está orquestado mediante **GitHub Actions** (`deploy.yml`). Al realizar un `git push` a la rama `main`, el pipeline se autentica de forma segura mediante *Repository Secrets* en AWS Academy, compila las imágenes Docker del Front y Back, las aloja en **Amazon ECR** y actualiza el clúster de **Kubernetes EKS** de forma continua y sin interrupciones.