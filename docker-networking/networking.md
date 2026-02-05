* **Create a custom user-defined bridge network called internal-net** `docker network create internal-net`
* **Launch 2 nginx Containers:**
    * **Server:** `docker run -d --name webserver --network internal-net nginx`
    * **Client:** `docker run -d --name client --network internal-net nginx`
* **Connectivity Test:**
    ```bash
    docker exec -it client bash
    apt-get update && apt-get install -y iputils-ping curl
    ping webserver  
    curl webserver  