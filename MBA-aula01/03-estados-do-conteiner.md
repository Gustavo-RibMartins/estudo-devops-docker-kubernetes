# Trabalhando com estados de contêineres Docker

Com o comando abaixo baixamos uma imagem do Docker Hub para a máquina local

````sh
docker pull alpine
````

Crie o contêiner e deixe-o pronto para execução

````sh
docker create -it --name=exemplo alpine sh
````

Execute o seguinte comando, listando todos os contêineres parados ou não em sua máquina

````sh
docker ps -a
````

Perceba que o contêiner está criado mas não está em execução. Agora "ligue" o contêiner

````sh
docker start exemplo
````

E execute, listando contêineres em execução

````sh
docker ps
````

Perceba que o contêiner está iniciado.
Agora vamos parar o container

````sh
docker stop exemplo
````

Execute o seguinte comando novamente

````sh
docker ps -a
````

E perceba que o contêiner não está mais em execução, ele está parado, como se tivesse sido "desligado", basta executar o comando abaixo para iniciar ele novamente.

````sh
docker start exemplo
````

Agora vamos executar uma pausa no contêiner

````sh
docker pause exemplo
````

E execute

````sh
docker ps
````

Perceba que o contêiner está parado, mas não "desligou", ou seja tudo que estiver em memória será mantido, diferente do comando stop que descarta a memória do contêiner, porém este contêiner não usa mais CPU, pois ele não está mais em execução.
Basta executar o comando abaixo para ele voltar a executar.

````sh
docker unpause exemplo
````

Assim passamos por todos os estados de um contêiner Docker.