## Run mysql conataier with volume
docker run -d --name mysql-container-1 -e MYSQL_ROOT_PASSWORD=mypassword -e MYSQL_DATABASE=testdb -v mysql_data:/var/lib/mysql mysql:8.0

### Connect to it, create a new table, and insert some data
docker exec -it mysql-container-1 mysql -u root -pmypassword testdb
CREATE TABLE inventory (id INT, item VARCHAR(20)); INSERT INTO inventory VALUES (1, 'Docker Book'); EXIT;

### Stop and remove the container.
docker stop mysql-container-1
docker rm mysql-container-1

### Start a new container with the same volume and confirm that the data still exists.
docker run -d --name mysql-container-2 -e MYSQL_ROOT_PASSWORD=mypassword -v mysql_data:/var/lib/mysql mysql:8.0
docker exec -it mysql-container-2 mysql -u root -pmypassword testdb -e "SELECT * FROM inventory;"
