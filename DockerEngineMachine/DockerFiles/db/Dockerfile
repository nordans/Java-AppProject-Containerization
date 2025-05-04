FROM ubuntu:latest as fetch_code
RUN apt update && apt install git -y
RUN git clone https://github.com/hkhcoder/vprofile-project.git
RUN cd vprofile-project && git checkout containers

FROM mysql:8.0.33
ENV MYSQL_ROOT_PASSWORD="vprodbpass"
ENV MYSQL_DATABASE="accounts"
COPY --from=fetch_code vprofile-project/src/main/resources/db_backup.sql docker-entrypoint-initdb.d/db_backup.sql