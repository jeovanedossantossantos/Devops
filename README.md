# Devops

<img src="https://img.mandic.com.br/blog/2018/02/devops-process.png"/>

# O que é o DOCKER?

<img src="https://programmer.group/images/article/41101b13d9a5c14312941dc56b5f483b.jpg"/>

"Docker é um conjunto de produtos de plataforma como serviço que usam virtualização de nível de sistema operacional para entregar software em pacotes chamados contêineres. Os contêineres são isolados uns dos outros e agrupam seus próprios softwares, bibliotecas e arquivos de configuração."

<h2>O Docker torna o desenvolvimento eficiente e previsível</h2>
<p>O Docker elimina tarefas de configuração repetitivas e mundanas e é usado em todo o ciclo de vida de desenvolvimento para desenvolvimento de aplicativos rápido, fácil e portátil – desktop e nuvem. A plataforma abrangente de ponta a ponta do Docker inclui UIs, CLIs, APIs e segurança que são projetados para trabalhar juntos em todo o ciclo de vida de entrega do aplicativo.</p>

<a href="https://www.docker.com/">Mais informações</a>

# VIRTUALIZAÇÃO
<img src="./img/00.png"/>
Na virtualização eu tenho como base a minha infraestrutura. Logo assim tenho a virtualização, por cima dela eu tenho a minha infravirtual onde eu escolho quanto de recurso eu vou destinar para cada maquina. Seguindo, temos o sistema operacionar e aplicação.

O grande problema para esse metodo é que, para cada maquina virtual é preciso instalar e gerenciar o sistema operacionar e seus recusros.

# CONTENIZAÇÃO

<img src="./img/01.png"/>

Nesse método, temos a camada de infrastrutura, o sistema operacional e encima dele temos o container Runtime(O CRI vem de Container Runtime Interface, que é um plugin que expõe uma interface que permite que um Kubelet (agent que roda dentro de cada nó dentro de um cluster do Kubernetes) use diferentes tipos de runtime compatíveis com a especificação da OCI sem precisar de recompilação ou reinicialização.) e com ele temos a execução dos containes que executam os processos.

# O QUE SÃO AS IMAGENS?

São os templeates que são gerados para criar e executar um container.

# ARQUITETURA DO DOCKER?

<img src="./img/02.png"/>

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