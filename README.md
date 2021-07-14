# Prerequisites
## Recommended hardware Requirements
- The node running cloud defense compose environment should meet the following requirements
- At least 4 cores or 4 vCPU's
- 12-16 GB RAM
- 50 - 100 GB SSD disk or more

## Preparing the environment 
Install Docker onto to host machine following instructions at https://docs.docker.com/get-started/. Cloud Defense stack requires Docker version 20.10.x and above. It is always recommended to install the latest version of Docker. If the host is in an air-gapped environment, ensure that it can pull required docker images from  DockerHub by whitelisting appropriate ports.

## Availability of ports 
There may be some custom firewall settings especially in AWS, Azure or Google Cloud Platform. But in general the basic firewall settings should allow the below ports unless you are on an extrement secure network where ports have to be specifically opened by the security team. The Cloud Defense support team can work closely with you to find what ports work for your cloud provider in case you have a custom firewall. 

### Ports 
CloudDefense application stack requires the following ports to be available, if the required ports are not available, please make a note of them. 

| Port | Description   |
| -----|:--------------|
| 80   | Network Proxy |
| 4000 | CloudDefense Analytics Engine |
| 4200 | Web Application |
| 8083 | Scan Data |
| 8082 | Scan Server |
| 8081 | CloudDefense API Service |
| 5432 | Database |
| 8091 | Authentication Service |
| 8092 | Keycloak Server |

### How to check if the ports are available

#### OSX / Linux: 
Run the following command and ensure one of the above ports doesn't appear in the list
```
lsof -i -P -n | grep LISTEN
````

If you have a previous installation of the on Cloud Defense prem service running from previously you maye see something like below: 

![image](https://user-images.githubusercontent.com/1424635/129790772-f570384e-a33f-41e0-a186-87e1e46a6bda.png)



#### Windows: 
Coming soon 

# Installation 

## Download the required files

The two files required for deploying the services using docker. Please download them to your server onto an indenpent directory and name it accordingly (example: clouddefense-onprem-services or anything your prefer) 
1. docker-compose.yaml
2. .env 

## Docker Compose 

### Bring up the services as a daemon process
``` 
docker compose up -d 
```

This will bring up the environment. It will take few minutes to initialize the environment. Give it 5-10 minutes. One can watch the status of the environment by running the following command. 

```
docker compose ps #(only containers specific to this docker compose up)
docker ps #(all containers)
```

![image](https://user-images.githubusercontent.com/1424635/129781549-5c8883bb-5952-4408-a055-90db740db86f.png)

The output of the above command should look a list of services . Wait till the status of all the containers turns to healthy status in the STATUS column.


### Add a hosts file entry

Map the localhost IP to the domain name at which you would like to access the running CloudDefense stack by modifying the host properties file, as shown in the below screenshot. In this case, the localhost / 127.0.0.1 is being mapped cdefense.local domain. See below image for example. 

![image](https://user-images.githubusercontent.com/1424635/129781483-3334e76a-182e-4ea0-987a-7c1b35c9391f.png)


# Accessing the application

Once the environment is installed, access the  CloudDefnese console using the browser, as shown in the below screenshot. In this case, the host's IP (where the stack is installed) is mapped to cdefense.local domain. The CloudDefense console is accessible via URL http://cdefense.local/.

##CloudDefense console Login page
Register a new organization by clicking on Don't have an account? Link. This will lead to the Organization registration page.

![image](https://user-images.githubusercontent.com/1424635/129782133-994a6768-b9aa-4a8f-b184-6731d5ee2d16.png)

##CloudDefense organization registration page
Fill in all the required details like Organization Name, User Name, Email Address, and Password to register the admin/master account for the setup. This will enable the Next action button.

![image](https://user-images.githubusercontent.com/1424635/129782154-ce57d0a7-cc8a-4c72-ad1e-ed54e0930805.png)


## Next enabled view
![image](https://user-images.githubusercontent.com/1424635/129782181-8d6b4a05-9ed7-43b0-885d-35dc866f1bd8.png)
Clicking Next will register the organization and Log you in. Once the user is successfully logged in for the first, it will lead to Getting Started Page.


## Getting Started Page
Follow the Getting Started page instructions to install CLI and start using the CloudDefense security stack.
Happy Scanning!

![image](https://user-images.githubusercontent.com/1424635/129782217-d29a77d1-703a-4ef0-a705-288e1ae70a8f.png)


# Issues during deployment 

Please reach out to the Cloud Defense support team / your sales rep and we will provide support asap. 

```
docker compose logs > logs.txt
#this command captures the logs into file logs.txt in the CloudDefense 
#installation directory
```

# Bring down the services (in case you need to). 
Please run this in the same directory where you ran `docker compose up`
```
docker compose down
```





