# Docker-Swarm

Inicializando as Máquinas e o Cluster Swarm

Depois de criar o Vagrantfile, você vai "subir" as máquinas e, em seguida, configurar o cluster.

Inicie todas as VMs:

Bash
vagrant up
Acesse a VM master e inicie o Swarm:

Bash
vagrant ssh master
docker swarm init --advertise-addr 192.168.50.10
O comando docker swarm init irá retornar um comando docker swarm join que você usará para adicionar os nós. Copie esse comando.

Saia da VM master e adicione os nós workers:
Para cada nó (node01, node02, node03), você deve acessá-lo e executar o comando de join que você copiou do master.

Bash
# Para o node01
vagrant ssh node01
# Cole o comando aqui (exemplo: docker swarm join --token <token> 192.168.50.10:2377)
exit

# Repita para o node02 e node03
vagrant ssh node02
# Cole o comando aqui
exit

vagrant ssh node03
# Cole o comando aqui
exit
Passo 3: Verificando o Cluster

Após adicionar todos os nós, volte para a máquina master para verificar o status do cluster:

Bash
vagrant ssh master
docker node ls
Se tudo deu certo, você verá os quatro nós na lista, com o master como manager e os outros como worker.
