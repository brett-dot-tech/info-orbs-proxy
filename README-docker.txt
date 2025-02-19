# ===========
# INSTALL
# ===========
# Build
docker build -t parqet-proxy .

# Install (daemon mode, listen at host's port 8010)
docker run -d -p 8010:8080 --restart unless-stopped --name parqet-proxy parqet-proxy


# ===========
# UPDATE
# ===========
docker stop parqet-proxy
docker rm parqet-proxy
docker build -t parqet-proxy .
docker run -d -p 8010:8080 --restart unless-stopped --name parqet-proxy parqet-proxy


# OPTIONAL: USE DOCKER VOLUMES for faster development (this will use the .py directly)
docker run -d -p 8010:8080 --restart unless-stopped --name parqet-proxy -v "$(pwd):/app" parqet-proxy




# ===========
# CHECK
# ===========
# Check logs
docker logs parqet-proxy

# Check running processes
docker ps