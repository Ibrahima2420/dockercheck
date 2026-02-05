## Docker Basics & CLI

* **Pull Image:** `docker pull nginx`

* **Run Container:** `docker run -d --name nginx-container -p 8080:80 nginx`

* **Exec & View:** `docker exec nginx-container bash `
                    `ls /usr/share/nginx/html`

* **Restart:** `docker restart nginx-container`

* **Cleanup:** `docker rm -f nginx-container && docker rmi nginx`