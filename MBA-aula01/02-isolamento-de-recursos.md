# Isolamento de recursos no Docker

Vamos ver como funciona o isolamento de CPU e memória no Docker, execute o comando abaixo em uma janela do terminal

````sh
docker run -it ubuntu bash
````

Mantenha a janela do terminal com o comando acima aberto e abra outra janela de terminal, executando o comando abaixo

````sh
docker stats
````

Perceba que o Docker fará um monitoramento dos contêineres mostrando consumo de memória, CPU, uso de rede, disco e até processos em execução (PID).
Agora volte no primeiro contêiner Ubuntu e execute o seguinte comando no terminal

````sh
apt update
````

Enquanto o contêiner executa os comandos, perceba a variação de CPU e memória na outra janela. Perceba também que da forma como foi executado, o contêiner tem acesso a toda a memória e CPU da sua máquina.
Agora vamos limitar o consumo, passando dois argumentos na execução do contêiner, vá na primeira janela e digite "exit", você voltará ao terminal do Windows e execute o comando abaixo

````sh
docker run -it -c=2 -m=2G ubuntu bash
````

Desta forma limitamos o uso de CPU, a apenas 2 cores, e a memória para 2 gigas.
Vá na segunda janela de monitoramento e perceba que agora o contêiner está limitado a usar apenas o que liberamos. 
Agora pode executar os comandos do apt no Ubuntu novamente

````sh
apt update
````

Ao terminar fecha ambas as janelas. Muito fácil, certo?