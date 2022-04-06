version: "3.8"

services:
  db:
    image : mysql
    container_name: db
    restart : always
    environment:
      - MYSQL_DATABASE=db
      - MYSQL_USER=user
      - MYSQL_PASSWORD=user123
      - MYSQL_ROOT_PASSWORD=innocent
    ports :
      - 3306:3306
    expose  :
    # Opens port 3306 on the container
      - '3306'
    volumes :
      - database:/var/lib/mysql
    networks:
      - mysql_network
    
  grafana :
    image : grafana/grafana
    container_name: grafana
    ports :
      - 3000:3000
    networks:
      - mysql_network

volumes:
  database:
    name: database

networks:
  mysql_network:
    name: mysql_network