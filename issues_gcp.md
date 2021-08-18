# Issue 1

Maybe transient but encountered while running `docker-compose up` 

```
Status: Downloaded newer image for cdefense/cubejs-cd:release-3.4.2
Pulling traefik (traefik:v2.0)...
ERROR: Head https://registry-1.docker.io/v2/library/traefik/manifests/v2.0: Get https://auth.docker.io/token?scope=repository%3Alibrary%2Ftraefik%3Apull&service=reg
istry.docker.io: net/http: TLS handshake timeout
```

# Issue 2: Keycloak user creation failed 

This is because the client (machine where browser is using the app)  and server (where docker compose up is running) needs to have an entry in the hosts file. This allows internal 
and externa redirection of the application via the browser. 

## GCP VM (/etc/hosts)

```
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
10.168.0.2 docker-ce-with-centos-8-stream-1-vm.us-west2-a.c.propane-ripsaw-323122.internal docker-ce-with-centos-8-stream-1-vm  # Added by Google
169.254.169.254 metadata.google.internal  # Added by Google
35.236.36.15 cdefense.local # Public IP of the GCP VM that is running docker compose up

```

## Machine where browser is accessing the VM

```
##
127.0.0.1       localhost
#127.0.0.1       cdefense.local
35.236.36.15    cdefense.local # Public IP of the GCP VM that is running docker compose up. 
255.255.255.255 broadcasthost
::1             localhost
```





