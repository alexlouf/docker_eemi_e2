# DOCKER EEMI E1

Upgrade form mariadb:10.1 to mariadb 10.3

## Installation

```bash
git clone https://github.com/alexlouf/docker_eemi_e2.git
```

## Usage

```bash
cd *installation_folder*
docker-compose up mariadb101
```

On a 2nd terminal :
```bash
docker exec -it mariadb101 bash
mysql -p
```

Le password mysql est "root"

```mysql
CREATE DATABASE upgrade;
USE upgrade;
CREATE TABLE test(id INT NOT NULL AUTO_INCREMENT, test_name VARCHAR(100) NOT NULL, PRIMARY KEY ( id ));
INSERT INTO test(test_name) VALUES ("Bonjour");
SELECT * FROM test;
```

On peut voir notre ligne nouvellement créée. \
On retourne dans notre terminal initial avec mariadb attaché et on le kill avec CTRL+C (windows/Linux) CMND+C (Mac)
\

On lance notre nouvelle image de mariadb à jour
 ```bash
 docker-compose up mariadb103
 ```
 
 Dans un second terminal :
 ```bash
 docker exec -it mariadb103 bash
 mysql -p
 ```
 
Le password mysql est "root"

On vérifie que notre ancienne insertion est encore en ligne :

```mysql
SELECT * FROM upgrade.test;
```

Et on se retrouve bien avec les mêmes data mais avec mariadb à jour.