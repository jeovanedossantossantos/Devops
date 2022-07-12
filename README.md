# Devops

<img width="700px" src="https://img.mandic.com.br/blog/2018/02/devops-process.png"/>

# O que é o DOCKER?

<img width="500px" height="400px" src="https://programmer.group/images/article/41101b13d9a5c14312941dc56b5f483b.jpg"/>

"Docker é um conjunto de produtos de plataforma como serviço que usam virtualização de nível de sistema operacional para entregar software em pacotes chamados contêineres. Os contêineres são isolados uns dos outros e agrupam seus próprios softwares, bibliotecas e arquivos de configuração."

<h2>O Docker torna o desenvolvimento eficiente e previsível</h2>
<p>O Docker elimina tarefas de configuração repetitivas e mundanas e é usado em todo o ciclo de vida de desenvolvimento para desenvolvimento de aplicativos rápido, fácil e portátil – desktop e nuvem. A plataforma abrangente de ponta a ponta do Docker inclui UIs, CLIs, APIs e segurança que são projetados para trabalhar juntos em todo o ciclo de vida de entrega do aplicativo.</p>

<a href="https://www.docker.com/">Mais informações</a>

# VIRTUALIZAÇÃO
<img width="500px" height="400px" src="./img/00.png"/>
Na virtualização eu tenho como base a minha infraestrutura. Logo assim tenho a virtualização, por cima dela eu tenho a minha infravirtual onde eu escolho quanto de recurso eu vou destinar para cada maquina. Seguindo, temos o sistema operacionar e aplicação.

O grande problema para esse metodo é que, para cada maquina virtual é preciso instalar e gerenciar o sistema operacionar e seus recusros.

# CONTENIZAÇÃO

<img width="500px" height="400px" src="./img/01.png"/>

Nesse método, temos a camada de infrastrutura, o sistema operacional e encima dele temos o container Runtime(O CRI vem de Container Runtime Interface, que é um plugin que expõe uma interface que permite que um Kubelet (agent que roda dentro de cada nó dentro de um cluster do Kubernetes) use diferentes tipos de runtime compatíveis com a especificação da OCI sem precisar de recompilação ou reinicialização.) e com ele temos a execução dos containes que executam os processos.

# O QUE SÃO AS IMAGENS?

São os templeates que são gerados para criar e executar um container.

# ARQUITETURA DO DOCKER?

<img width="600px" height="400px" src="./img/02.png"/>

Ele é formado por três componentes. Docker daemon, docker client e docker registry.

<ul>
<li>[ ] Docker daemon
<p>É o componente que gerencia os objetos do docker, como as imagens, os containes, networks e os volumes. E todo o processo de execução dos containers acontece nele.</p>
</li>
<li>[ ] Docker client
<p>E para se comunicar com o docker daemon tem o docker client, que é o docker cli, ferrramenta de linha de comando.</p>
</li>
<li>[ ] Docker registry
<p>É o repositotio de imagens onde se armazena e distribuir as imagens que vão criar e executar os meus containers.</p>
</li>
</ul>

# COMANDOS

<ul>
<li>[x] docker : verificando se está instalado</li>
<li>[x] docker container run <nome-da-imagem>: crinado um container</li>
<li>[x] docker container run --name <nome-do-container> <nome-da-imagem>: crinado um container</li>
<li>[x] docker container ls: listando os containers que estão em execução</li>
<li>[x] docker container ls -a: listando todos containers</li>
<li>[x] docker container rm <id-container>: apagar containers</li>
<li>[x] docker container run -it <nome-da-imagem> /bin/bash : crinado um container no modo interativo</li>
<li>[x] docker container run -d nginx : executando em modo dimo, liberando o terminal</li>
<li>[x] docker container exec -it /bin/bahs : executando o contianer</li>
<li>[x] docker container ls -a -q : devolve os ids dos containers</li>
<li>[x] docker container run -d -p 5432:5432 -e POSTGRES_DB=aula-iniciativa -e POSTGRES_USER=iniciativadevops -e POSTGRES_PASSWORD=123456  postgres : iniciando um container e definindo as variveis de hambiente</li>

</ul>

# CRIANDO O DOCKERFILE

        FROM ubuntu //imagem base
        RUN apt update // atualiza a imagem 
        RUN apt install curl --yes // inatala o pacote curl
<ul>
<li>[x] docker build -t <nome-da-sua-imagem> <contexto> (. ou -f caminho-do-seu-arquivo)</li>
<li>[x] docker build -t <nome-da-sua-imagem> <contexto> --no-cahed</li>
<li>[x] docker image prune : excluir as imagens que não estão sendo usadas</li>
<li>[x] docker tag ubuntu-curl jeovanedos2santos/ubuntu-curl:v1 -> renomeando uma imagem</li>
<li>[x] docker login -> login no docker</li>
<li>[x] docker push <nome-do-repositorio> -> mandando para o docker a sua imagem</li>

</ul>

# OUTROS COMANDOS

<img width="700px" src="./img/03.png"/>

# CAMADAS

<div display="flex">
<img width="400px" height="400px" src="./img/04.png"/>
<img width="400px" height="400px" src="./img/5.png"/>
<img width="400px" height="400px" src="./img/6.png"/>
</div>

# NOMEANDO SUA IMAGEM 

        Namespace/Repositório:Tag
        jeovanedos2santos/ubuntu-curl:v1

Quando não coloca a tag isso significa que está subindo a versão mais atual

# ARQUIVO DOCKER
<ul>
<li>
<h2>Docker Images</h2>    

        FROM name_imagen:version
 
Aqui estamos usando uma imagem do docker hub. Isto, é um container pré-formatado do docker que permite que você monte sua máquina a partir daquela configuração inicial.
</li>
<li>
<h2>Environment Variables (Variáveis de ambiente)</h2>  
        
        ENV environment_variables
 
Você pode criar todas as variáveis de ambiente que quiser com o ENV.
</li>
<li>
<h2>Run Commands</h2>    

        RUN comando_a_ser_execultado

No RUN você deve passar quais comandos o docker devera executar para que as configurações inicias de um projeto funcione.
Exemplo: npm i, npm install, yarn, npm run start etc. Também pode ser passando comandos de migrate. 
</li>
<li>
<h2>Workdir</h2>    

        WORKDIR caminho_do_diretorio_onde_vai_roda_os_comandos
        
Workdir é uma instrução para mostrar ao docker em qual diretório ele vai rodar os comandos a partir dali.
</li>
<li>
<h2>COPY e ADD</h2>    

Copy e ADD são basicamente a mesma cosia. Ambos copiam um arquivo do seu computador (o Host) dentro do container (o Guest). No meu exemplo, estou apenas copiando o requirements para dentro do docker, para que eu possa dar pip install nos pacotes.
</li>
<li>
<h2>EXPOSE</h2>  

        EXPOSE 8000
        
Expose é para mapear uma porta do Guest (o Container) para o Host (seu computador)
</li>
</ul>

#ARQUIVO DOCKER-COMPONSE
O compose é uma ferramenta para rodar múltiplos containers do docker. Só precisa criar um arquivo yml na pasta do seu projeto com o nome docker-compose.yml

        version: '3.3'

        services:
          # Postgres
          db:
            image: postgres
            environment:
              - POSTGRES_USER=postgres
              - POSTGRES_PASSWORD=postgres
              - POSTGRES_DB=postgres

          web:
            build: .
            command: ["./run_web.sh"]
            volumes:
              - .:/webapps
            ports:
              - "8000:8000"
            links:
              - db
            depends_on:
              - db
<ul>
<li>
<h2>LINKS</h2> 

        links:
          - db
          
Você pode se referir a outro container que pertence ao seu arquivo docker-compose utilizando o nome dele. Como criamos um container com o nome db para o Postgres nós podemos criar um link para ele no nosso container chamado web. Pode ver que no settings.py nós colocamos ‘db‘ como host.
</li>
<li>
<h2>DEPENDS_ON</h2>   

        depends_on:
          - db

Dependência expressa entre serviços.
</li>
<li>
<h2>Command</h2>    
Command é o comando padrão que o docker vai rodar logo depois que você subir, ou seja, colocar os containeres para funcionar.

</li>

</ul>
 
# CRIANDO UM CONTAINER COMO O DOCKER COMPOSE
        
        docker compose up --build -> crinado uma novo container com as imagens

# PRIMEIRO PROJETO: CONVERSÃO DE TEMPERATURA

<p>Dentro do diretorio src crie um arquivo "Dockerfile" e dentro dele coloque os seguintes comandos para definir a sua imagem.</p>

        FROM node:16.15.0           -> imagem base será o node
        WORKDIR /app                -> criar um diretorio app
        COPY ./package*.json ./     -> copia o package.json e o  package-lock.json
        RUN npm install             -> baixa as dependencia do projeto 
        COPY . .                    -> copia o restande dos arquivos
        EXPOSE 8080                 -> definindo a porta que o projeto ira roda
        CMD ["node", "server.js"]   -> definifo os comandos para o projeto roda

<p>Apos execute as seguintes linhas de comandos(execute dentro do diretorio src)</p>

        docker build -t <namespace>/<name-repositorio>:versão
        docker container run -d -p porta-d-sua-maquina:porta-do-container <namespace>/<name-repositorio>:versão

<a href="https://docs.docker.com/get-started/overview/">Documentação do docker</a><br/>
<a href="https://fernandofreitasalves.com/criando-um-container-docker-para-um-projeto-django-existente/">Mais detalhes</a>
       
 # NEM TUDO SÃO FLORES
        
<p>Para cada solução existe um novo problema. Com o atual cenario de clud e micro-serviçõs é necessario mais do que apenas isolamento de processos para a execução das aplicações.</p>
<p>É preciso carantir que se um container estiver com uma mal funcionameto, é importande que ele seja encerrado e ser criado outro em seu lugar.</p>
<p>E isso o docker não faz. </p>
<p>É preciso também ser capaz de replicar os containers para distribuir as cargas de requisições entre eles.</p>
<p>E isso o docker não faz. </p>

Para solucionar esse problema existe o KUBERNETS.

# O que é KUBERNETS?

<img width="500px" height="400px" src="https://kubernetes.io/images/favicon.png"/>

<p>Kubernetes é um sistema de orquestração de contêineres open-source que automatiza a implantação, o dimensionamento e a gestão de aplicações em contêineres. Ele foi originalmente projetado pelo Google e agora é mantido pela Cloud Native Computing Foundation.</p>
<p>É uma plataforma open source que automatiza as operações dos containers Linux. O Kubernetes elimina grande parte dos processos manuais necessários para implantar e escalar as aplicações em containers.</p>