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

# How to fix "You are using a plain text ADMIN_TOKEN which is insecure.Please generate a secure Argon2 PHC string by using vaultwarden hash or argon2. See: Enabling admin page - Secure the ADMIN_TOKEN"

1. Using the Bitwarden defaults (default preset)
- Via docker on a running container
   **docker exec -it <your_container_name> /vaultwarden hash**

- Via docker and creating a temporary container
  **docker run --rm -it vaultwarden/server /vaultwarden hash**

- Using the vaultwarden binary directly
  **./vaultwarden hash**

2. It will ask you to Enter your password. Enter any strong password and confirm it. 
 
3. You will get an output look like this on your CLI:

   Output: $argon2id$v=19$m=65540,t=3,p=4$bXBGMENBZUVzT3VUSFErTzQzK25Jck1BN2Z0amFuWjdSdVlIQVZqYzAzYz0$T9m73OdD2mz9+aJKLuOAdbvoARdaKxtOZ+jZcSL9/N0 

4. Use this output in your docker/podman CLI command. For **docker-compose.yml** files, you can configure the ADMIN_TOKEN under environment variables. To prevent variable interpolation, you need to add one more '$' sign with all five occurrences of the dollar sign $ in the generated argon2 PHC string. Your output should be look like this with two dollar signs:

    e.g: ADMIN_TOKEN=$$argon2id$$v=19$$m=65540,t=3,p=4$$yK3dQ27DGtblfe5CxHCj1FQJ9Rz9PLiWMekLOzCVA18$49zBgL8vcm409EtwzPGJlO5vPNU1aoZUNfO4vPGBdvI
   
5. Go to your web admin area with yourdomain.tld/admin , Enter your password which you set in step no.2.
   
6. You have successfully done it!





