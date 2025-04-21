# docker-swarm-experiments
Repositório pra teste do docker swarm 

Criando o portainer:
$ docker volume create portainer_data   # Criação do volume pro portainer

# Criação do container server do portainer gráfico 
$ docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:lts 

# Logar no navegador com: https://localhost:9443/
