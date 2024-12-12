# Implement Github action and deploy to Azure

We already have two repositories, one for backend and one for frontend, of projects, that should be deployed to azure. 

Code should be passing tests before being able to merge. 

After merging into develop, a new docker image will be created and the new version should be deployed into an azure container app in the dev environment.

When merging into main, the new version will be deployed in the prod environment.

## The project
The project transcribes lecture recordings and summarizes them.
The backend uses flask and some functionality will be tested in unit tests.
The frontend also tests some components in tests.

## Team and responsibilities
Dominik Birngruber (k12206237)

Elias Berger (k12209123)

Lukas Werner (k12222518)


## Tasks
* Frontent Test Stage - Lukas Werner
* Backend Test Stage - Elias Berger
* Deployment Stage - Dominik Birngruber
* Dockerize Frontend - Dominik Birngruber + Lukas Werner
* Dockerize Backend - Dominik Birgruber + Elias Berger
* Define Git Flow and document rules - All together
* Presentation - All together
