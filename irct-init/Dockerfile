FROM mysql:latest
MAINTAINER Andre Rosa <andre_rosa@hms.harvard.edu>

# NOTE: All going away. Will be replaced by small golang-alpine dynamic program -Andre

# set default variables
ENV IRCT_RESOURCE_NAME demo
ENV IRCTMYSQLADDRESS localhost
ENV IRCT_DB_CONNECTION_USER root
ENV IRCTMYSQLPASS my-secret-pw
ENV AUTH0_DOMAIN domain
ENV AUTH0_CLIENT_ID client_id
ENV TRANSMART_RESOURCE https://transmart:8080

# sci db service introduced in IRCT build 2493.hackathon
ENV SCIDB_HOST http://scidb:8080
ENV SCIDB_USER scidbuser
ENV SCIDB_PASSWORD scidbpassword

# scripts will run at startup to populate the DB
COPY init-db/ /scratch/irct/sql/

# must use shell form; docker does not parse env variables for ENTRYPOINT[] or CMD[]
ENTRYPOINT ["./scratch/irct/sql/init-db.sh", "-d", "irct"]
