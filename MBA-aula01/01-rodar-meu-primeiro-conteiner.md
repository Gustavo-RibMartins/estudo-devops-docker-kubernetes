# Rode seu primeiro contêiner Docker

Abra o terminal e execute o seu primeiro contêiner "hello-world"

````sh
docker run hello-world
````

Analise a saída e percebe que duas ações foram feitas pelo Docker, baixar a imagem para sua máquina e executar o contêiner. Agora execute o comando abaixo

````sh
docker pull ubuntu
````

Perceba que a imagem do Ubuntu foi baixada do Docker Hub para sua máquina local, execute o comando de listagem de imagens

````sh
docker images
````

Vamos executar um contêiner baseado na imagem do Ubuntu e acessá-lo enquanto ele está em execução

````sh
docker run -it ubuntu bash
````

Perceba que após este comando você está dentro do contêiner do Ubuntu, em ambiente Linux. Para sair basta digitar "exit".
Muito bem você acabou de executar seus primeiros contêineres.