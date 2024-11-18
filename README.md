# Netflix-DevSecops
This project is deployed using DevSecOps tools.

Tools Used: Kubernetes,Docker,Jenkins,Prometheus,Grafana,Azure,Argo-CD,Trivy and SonarQube.

The front end of the Netflix has been cloned from a similar project written in TypeScript and HTML.
I Have used TMDB (Movie Database) to get the movie data on the Netflix application.

Setup:

1) Two Vm's on Azure (Standard D2s v3) : One to deploy Docker,Jenkins,Trivy and Sonarqube another to deploy Monitoring tools like Grafana,Prometheus.
2) A kuberenetes cluster running in azure (AKS) 

Brief Explanation of the project.

1) We first launch the VM's, The first one (named Netflix-jenkins) has the repo cloned. We install docker get the personal API key required for the Movie database and build it along with it and push the image.
2) We then install sonarqube and Trivy on the same VM.
3) We then install Jenkins,Configure the required plugins like JDK,Eclipse,Sonarqube,Nodejs,Docker and Email. Make sure to have docker credentials setup in jenkins credentials part.
4) We build the Jenkins pipeline to pull the code from repo,Perform the analysis using sonarqube, perform analysis and scans,install dependency,build and push docker image and then push to container.
5) In the second VM(called monitoring) we install prometheus and Grafana and configure them to scrape metrics on node exporter and jenkins.
6) After test deploying this as a container we move to pushing the same to kuberentes, Deployed AKS cluster.
7) We use helm charts to deploy prometheus and node exporter.
8) We deploy Argo-cd from https://joeloduyemi.hashnode.dev/how-to-install-argocd-on-an-aks-cluster for aks.
9) We then create a new app and point the repository.
10) We then have our application running on a particular nodeport.


The project successfully deploys an end-to-end netflix clone using DevSecOps tools.

Below are some of the pictures from the project deployed.

![image](https://github.com/user-attachments/assets/f4938e36-a5e4-4d18-98c4-bcca1206307e)
![image](https://github.com/user-attachments/assets/7d0333e4-c5ff-4dd9-a699-f36a4d6d3b32)
![image](https://github.com/user-attachments/assets/e6ee8d8e-467e-41b6-aee2-01d872eba7da)
![image](https://github.com/user-attachments/assets/df302132-d6b5-4b15-887f-b29e78864050)
![image](https://github.com/user-attachments/assets/5e41ba6a-a22b-44aa-9f72-6480c721df1d)
![image](https://github.com/user-attachments/assets/4d117fa9-c37c-404b-bed8-d42c682c0fa8)
![image](https://github.com/user-attachments/assets/c70fd144-3d01-46a3-b7fb-47c8f4b6b5dc)
![image](https://github.com/user-attachments/assets/7eed8f6f-3a51-45f5-bc1b-a51410c9bb90)
![image](https://github.com/user-attachments/assets/76527077-4774-479b-9cde-c4be8020a7fc)



The above was inspired by CloudChamp Netflix Project.