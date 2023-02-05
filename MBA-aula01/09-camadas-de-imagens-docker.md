# Entendendo as camadas de imagem Docker

Execute o seguinte comando, baixando uma imagem de nginx em sua máquina

````sh
docker pull nginx:stable-alpine
````

Baixamos a imagem do Docker Hub, agora execute o comando abaixo

````sh
docker history nginx:stable-alpine
````

Perceba as camadas da imagem, este é um servidor web construído em cima do sistema operacional Alpine.<br>
Note também, que a última camada da imagem nginx, aponta para o hash de outra imagem que é o Alpine.