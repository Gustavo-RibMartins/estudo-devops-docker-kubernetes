# Entendendo processos em contêineres Docker

Agora vamos visualizar os processos dentro de contêineres Docker, rode o comando abaixo

````sh
docker run -d nginx
````

Quando contêiner nginx estiver rodando, execute este outro comando e perceba que o nginx criou vários PIDs (process ids) dentro do contêiner para que o servidor web funcione

````sh
docker stats
````

Digite crtl+c para sair do monitoramento e vamos melhorar os experimentos, execute as linhas abaixo

````sh
docker create -it --name=processo-so ubuntu bash
docker start processo-so
````

Agora subimos um Ubuntu com um programa rodando "bash", portanto abra outra janela de terminal e execute

````sh
docker stats
````

Podemos notar, neste terminal de monitoramento, que existe apenas um processo rodando no contêiner. Volte ao terminal anterior e execute

````sh
docker exec -it processo-so bash
````

Agora estamos dentro do contêiner, o comando "exec" criou outro processo dentro do contêiner para rodar mais uma instância do "bash". Volte ao terminal de monitoramento e veja que agora o Ubuntu tem dois processos rodando.<br>
Lembre-se, um contêiner precisa de ao menos um processo rodando, caso o último processo termine, o contêiner irá "desligar".<br>
Caso você vá até o terminal dentro do contêiner e execute o comando "exit", seu contêiner voltará a ter um processo rodando.