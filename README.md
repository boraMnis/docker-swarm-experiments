# docker-swarm-experiments
Repositório pra teste do docker swarm 

# Criando o portainer:

## Criação do volume para o portainer
~ docker volume create portainer_data

# Criação do portainer em con
~ docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:lts 

# Logar no navegador com: https://localhost:9443/

## Criação do agent em container. Caso precise:
~ docker run -d -p 9001:9001 --name portainer_agent --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v /var/lib/docker/volumes:/var/lib/docker/volumes -v /:/host portainer/agent:2.27.4
