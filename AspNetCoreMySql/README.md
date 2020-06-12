## This project demonstrate how to Dockerizing your dotnetcore with Docker and MySql

### I needed this command during the demo

dotnet add package Pomelo.EntityFrameworkCore.MySql
docker run -p 3306:3306 --name mysqldb -e MYSQL_ROOT_PASSWORD=secret -d mysql.0.0
