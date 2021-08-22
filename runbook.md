# Runbook for docker based on prem deployment. 

## Steps 

- Start with docker-compose up (because this takes time)
- While this is running, change the etc hosts in the client machine to use cdefense.local (or any other preferred name). That should be the same name as the CD_SERVER_HOST in the .env file. 
- download the CLI on the client and install the pre-requisites 
  - https://github.com/CloudDefenseAI/cd#language
- change SCAN_URL to point to http://cdefense.local (or preferred name) in the client machine. 
- Questions: What languages do you use for development? 
  - lets pick a couple projects to run the scan on. Do you have them locally, if not lets clone the projects. 
  - Install pre-requisites. 

Note: If we used the CD_SERVER_HOST as the public IP of the server itself, the /etc/hosts step is not necessary. 

## Image names on various cloud services that come pre-built with docker compose:
### Google Cloud 
- Ubuntu: docker-compose-ubuntu20-1 

## Docker Installation (On the client for SAST, DAST) or for running the server. 
### Mac
- https://docs.docker.com/desktop/mac/install/
### Windows 
- https://docs.docker.com/desktop/windows/ 
### Linux 
- Many Flavors: https://docs.docker.com/engine/install/ 
