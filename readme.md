# Pasos para linux y mac: 

## Crear la imagen para la base de datos oracle
* `docker build oracle-db/Dockerfile -t oracledb`
* `docker run -d -p 49166:8080 -p 49161:1521 --name oracledbContainer  -e ORACLE_ALLOW_REMOTE=true oracledb`

## crear php imagen y container
*   `cd oracle-php-client`
* `docker build . -t oraclephpclient`
* `cd test`
* `docker run -p 5555:80 -p 49555:1521  --link oracledbContainer:oracledb   --name oraclephpclientContainer  -d -v <path_folder>:/var/www/html  oraclephpclient`
* go to http://0.0.0.0:5555