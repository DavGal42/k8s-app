# Kubernetes Application with Helm and ArgoCD

This project contains a microservices-based application deployed in Kubernetes using Helm charts and ArgoCD application.

## Project Structure

```bash
app/
    └── app.yml
myapp-chart/
    ├── templates/
        ├── backend/
            ├── backend-configMap.yml
            ├── backend-deploy.yml
            ├── backend-secret.yml
            └── backend-service.yml
        ├── frontend/
            ├── frontend-deploy.yml
            └── frontend-service.yml
        ├── postgres/
            ├── postgres-config.yml
            ├── postgres-deploy.yml
            ├── postgres-secret.yml
            └── postgres-service.yml
        ├── ingress.yml
        └── namespace.yml
    ├── .helmignore
    ├── Chart.yaml
    └── values.yaml
values/
    ├── dev-values.yml
    └── prod-values.yml
```

## Installation Guide

- Using Helm
  
  - Install Helm
  
  - Install the chart
  
    - In the `dev` environment
    
      ```bash
       helm install myapp ./myapp-chart \
         -f values/dev-values.yml \
         --create-namespace \
         --namespace dev
      ```
    
    - For production:
    
      ```bash
        helm install myapp ./myapp-chart \
          -f values/prod-values.yml \
          --create-namespace \
          --namespace prod
      ```

- Using ArgoCD

  - Install ArgoCD
  - Create an ArgoCD application

     ```bash
     kubectl apply -f app.yml
     ```
