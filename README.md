# Helm Demo with Node.js App

In this assingment I have created sample demo app and created a dockerfile and tried to deploy it through kubernetes .

### Step 1

- Created Node.js app and run it locally
- Dockerised it using Dockerfile and Podman
- Created image and container successfully to test the application
- Created node pool for EKS 
- Pushed the image to ECR

### Step 2 

- used `helm create` command to create a chart file 
- install nginx ingress controller through helm

### Step 3
- Made the required changes and installed the app through helm
- all the apps and kubernetes resources are up and running
- host and loadbalancer address has also been assigned

## Challenges

- Since host name was needed to bind the loadbalancer dns a record with ingress , I didn't have any public DNS Server to create a CNAME and show the app running . I didn't have IP and hence I cant use host as well to show the app running

## deployment for a production environment

- Horizontal Pod Autoscaler will be needed
- Layer 7 load balancer need to be used
- Use Private EKS cluster
- Use image vunerability scanner like trivy
- store images at private ECR or dockerhub or other private repository
- Use RBAC
- Use Cluster Autoscaler
- Use WAF with Layer 7 LB
- Replicas count should be more than 1 
- May use Blue green deployment strategy
- enable resource quotas
- Use liveness and readiness probes
- pod Disruption budget

To run this application : 

- *Dockerize the app with given Dockerfile*
  ``` 
  docker build -t nodeapp:v1 <path to Dockerfile>
  ```
- *Install the helm chart of ingress controller*


  ```
  helm install my-release oci://ghcr.io/nginxinc/charts/nginx-ingress --version 1.2.0
  ```


- Install the app using helm 
  go to helm/demo-app/ folder

 
   ```
   helm install <release-name> .
   ```

- To check release


   ```
   helm list
   ```
- To update after a change 


    ```
    helm upgrade --install demo-app .
    ```
- To see the release


  ```
   helm history demo-app
  ```
- To rollback to previous release


   ```
  helm rollback demo-app <REVISION NO>
   ```
![Screenshot (2)](https://github.com/SaumyaBhushan/helm-node-demo/assets/76432998/0e415a87-b3f1-4ff0-8bf3-00509b4e3e10)

![Screenshot (3)](https://github.com/SaumyaBhushan/helm-node-demo/assets/76432998/1903ac27-1a84-4751-8512-0c66e548bc72)


   
