#Runbook for docker based on prem deployment. 

##Image names on various cloud services that come pre-built with docker compose:
### Google Cloud 
- Ubuntu: docker-compose-ubuntu20-1 

If the customers don't pick the image with docker. We need manual steps to install docker. 
- https://docs.docker.com/engine/install/ubuntu/
- Go to "Set up the repository"
- Then go to "Install Docker Engine"
- Download docker-compose binary. 

## Steps 

1. Start with docker-compose up (because this takes time)
2. While this is running
- change the etc hosts in the client machine to use cdefense.local (or any other preferred name). That should be the same name as the CD_SERVER_HOST in the .env file. 
- download the CLI on the client
- change SCAN_URL to point to http://cdefense.local (or preferred name) in the client machine. 
- Question for customer: what languages do you use for development. lets pick a couple projects to run the scan on. Do you have them locally, if not lets clone the projects. Do this while docker compose is running. 
