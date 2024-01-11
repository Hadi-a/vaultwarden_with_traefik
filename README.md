Prerequisite to deploy Vaultwarden,
- Docker
- Docker-Compose 
- Traefik proxy

Create a new folder called "vaultwarden":

**mkdir vaultwarden**

and switch into that folder with:

**cd vaultwarden**

Create a new file called "docker-compose.yml":

**nano docker-compose.yml**

Copy the configurations from docker-compose.yml file into your newly created docker-compose.yml file and change the domain and network settings according to yours, and save it.

run **docker-compose up -d** to pull and install Vaultwarden. 

Your domain is the login page for you to begin.

![image](https://github.com/Hadi-a/vaultwarden_with_traefik/assets/47814388/4c190d04-9737-4adc-ba0a-18574c4c7d6a)




 => To access the admin area the url would be your **yourdomain.tld/admin** 
