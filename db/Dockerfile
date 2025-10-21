FROM postgres:17.2-alpine

# Variables par défaut (uniquement pour la démo)
ENV POSTGRES_DB=db \
    POSTGRES_USER=usr \
    POSTGRES_PASSWORD=pwd

# Scripts d'initialisation exécutés au 1er démarrage
COPY initdb/ /docker-entrypoint-initdb.d/
