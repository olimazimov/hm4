# hm4
<code>
version: "3.1"

services:
    db:
     image: postgres:latest
     ports:
      - 5432:5432
     environment:
#      POSTGRES_USER: root
      POSTGRES_PASSWORD: root
#      POSTGRES_DB: postgres
     volumes:
      - /home/olim/git/hm4/db_data:/var/lib/pgsql/data

    dbviewer1:
     image: adminer
     ports:
      - 8081:8080
     depends_on:
      - db


    dbviewer2:
     image: dpage/pgadmin4:latest
     ports:
      - 8080:80
     environment:
      PGADMIN_DEFAULT_EMAIL: olim@test.com
      PGADMIN_DEFAULT_PASSWORD: root
     depends_on:
      - db
</code>