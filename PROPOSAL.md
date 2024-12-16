# Implement Github action and deploy to Azure

We already have two repositories, one for backend and one for frontend, of projects, that should be deployed to azure. 

Code should be passing tests before being able to merge. 

After merging into develop, a new docker image will be created and the new version should be deployed into an aks cluster in the dev environment.

When merging into main, the new version will be deployed in the prod environment.

## Deployment Strategy

We will use rolling deployment to always keep the application available. For this we will use the rolling update strategy in our deployment.

## The project
The project transcribes lecture recordings and summarizes them.
The backend uses flask and some functionality will be tested in unit tests.
The frontend also tests some components in tests.

## Team and responsibilities
Dominik Birngruber (k12206237)

Elias Berger (k12209123)

Lukas Werner (k12222518)

## Workflow
![image](https://github.com/user-attachments/assets/17d93a2a-dbb8-4e70-b970-fb2387aa3176)


## Milestones

### Github actions pipeline configured

* Stages configured correctly and deployment works
* The appropriate deployment pipeling runs on the merge request

### Rolling update working
* when a new deployment is done, there is no outage of the service
* This is done with configuring the deployment strategy

### AKS (Azure Kubernetes service) is set up
* a container registry and aks cluster exist

## Tasks
* Frontent Test Stage - Lukas Werner
* Backend Test Stage - Elias Berger
* Deployment Stage - Dominik Birngruber
* Dockerize Frontend - Dominik Birngruber + Lukas Werner
* Dockerize Backend - Dominik Birgruber + Elias Berger
* Define Git Flow and document rules - All together
* Presentation - All together
