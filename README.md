# Simple DevOps Project

[![Image](https://github.com/yankils/Simple-DevOps-Project/blob/master/Devops_course.PNG "DevOps Project - CI/CD with Jenkins Ansible Docker Kubernetes ")](https://www.udemy.com/course/valaxy-devops/?referralCode=8147A5CF4C8C7D9E253F)

 

## Summary of my CI/CD project
### What's covered in this course?  
  * Section 1: Introduction  
  * Section 2: CI/CD pipeline using Git, Jenkins and Maven  
      1) How to setup up Jenkins server?  
      2) How to setup Jenkins to use Poll SCM to pull code from Github?  
      3) How to setup Maven in Jenkins?  
      4) How to setup a Jenkins project to automatically pull code from Github and build it?  
  * Section 3: Integrating Tomcat server in CI/CD pipeline  
      1) How to setup a tomcat server  
      2) How to integrate Tomcat with Jenkins  
      3) How to automate buiild and deploy using poll SCM  
  * Section 4: Integrating Docker in CI/CD pipeline  
      1) How to setup docker environment  
      2) How to create a tomcat container  
      3) How to fix the issue with tomcat container by copying webapps to the correct folder  
      4) How to write a docker file?  
      5) How to write a docker file to create a customized Tomcat container?  
      6) How to create a job to build and copy artificats on a dockerhosts?  
      7) How to update the dockerfile to automate the deployment process?  
      8) How to automate build and deployment on Docker container?  
  * Section 5: Integrating Ansible in CI/CD pipeline  
      1) How to setup ansible   
      2) How to integrate docker on Ansible server  
      3) How to integrate Ansible with Jenkins  
      4) How to build and create container on Ansible server  
      5) How to build and create image and container using Ansible playbook  
      6) How to copy image to docker hub  
      7) How to use Jenkins to build an image onto ansible  
      8) How to create container on dockerhost using ansible playbook  
      9) Continuous deployment of coker container using ansible playbook  
      10) Jenkins CI/CD to deploy on container using Ansible  
  * Section 6: Kubernetes on AWS  
      1) How to install Kubernetes  
      2) How to install EKS  
      3) How to setup boostrap server for eksctl  
      4) How to setup kubernetes using eksctl  
      5) Run kubernetes basic commands  
      6) Create 1st kubernetse manifest file  
      7) Create a service manifest file  
      8) Using labels and selectors.  
  * Section 7: Integrating Kubernetes in CI/CD pipeline  
      1) Write a deployment file  
      2) Use deployment and service files to create and access pod  
      3) Integrate Kubernets bootstrap server with Ansible.  
      4) Create ansible playbooks for deploy and service files  
      5) Create Jenkins deployment job for Kubernetes  
      6) CI job to create image for Kubernetes  
      7) Enable rolling update to create pod from latest docker image  
      8) Complete CI and CD job to build and deploy code on Kubernetes  
      9) Clean up Kubernetes Setup  

### Summary of the Final project
1. Overview

   1. This project automates the integration and deployment of a website with stack of technologies and achieved the goal of CI/CD and high availability. Basically you can do any updates to this webapp, and the webapp will automatically update without stopping the service.  
   2. The pipeline involves Jenkins, Ansible/Docker, Kubernetes, AWS EKS  
2. Steps
    1) [Create a jenkins server](https://github.com/BackInSchwarz/Simple-DevOps-Project/blob/master/Jenkins/Jenkins_Installation.MD)
    2) [Create an ansible server](https://github.com/BackInSchwarz/Simple-DevOps-Project/blob/master/Ansible/Ansible_installation.MD)  
    3) Create a boostrap server for Kubernetes management  
      a) create a cloud formation with one load balancer and two nodes. [Link](https://github.com/BackInSchwarz/Simple-DevOps-Project/blob/master/Kubernetes/kubernetes_setup_using_eksctl.md)
    4) Configure Jenkins server with the ability to   
      a) automatically pull code from git  
      b) automatically build the code  
      c) automatically put the aritifacts to the ansible server  
    5) Configure Ansible server with the ability to   
      a) take the artifacts and build a tomcat container with docker  
      b) publish the container to dockerhub  
      c) trigger the boostrap to rollout the new container.  
3. Execution steps    
    1) CI job  
      a) Git updates trigger Jenkins  
      b) Jenkins build and copy the files to Ansible server  
      c) Ansible run the container creation playbook  
          i) [create_image_regapp.yml](https://github.com/BackInSchwarz/Simple-DevOps-Project/blob/master/MyProject/create_image_regapp.yml)  
         ii) playbook uses the following [dockerfile](https://github.com/BackInSchwarz/Simple-DevOps-Project/blob/master/MyProject/Dockerfile) to create the container.  
    2) CD job  
      a) Ansible run the deployment playbook [kube_deploy.yml](https://github.com/BackInSchwarz/Simple-DevOps-Project/blob/master/MyProject/kube_deploy.yml)  
      b) playbook involves following kubernete manifest file to create app: [regapp-deploy.yml](https://github.com/BackInSchwarz/Simple-DevOps-Project/blob/master/MyProject/regapp-deploy.yml)  
      c) playbook involves following kubernete manifest file to create service: [regapp-service.yml](https://github.com/BackInSchwarz/Simple-DevOps-Project/blob/master/MyProject/regapp-service.yml)  


