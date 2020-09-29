# Curso Git Essencial
## iniciado em 09/06/2020
## terminado em 29/09/2020

## Aula 1 Preparando tudo para começar
### Aula 1.2 instalando o JDK e o Eclipse
ambiente de desenvolvimento
- JDK 13 
- Eclipse

#### instalar o JDK 13
http://jdk.java.net
- baixar o JDK
- após o download (arquivo zip), clicar com o botao direito do mouse e extrair os arquivos.
- colocar a pasta descompactada em uma pasta de desenvolvimento, para facil localizacao.

### Aula 1.3 criando o projeto no eclipse e iniciando o controle de versão
#### preparar o eclipse para receber o git
com um projeto aberto, devemos compartilhar o projeto.
o ponto inicial do git é compartilhar o projeto:
- botao direito no projeto
- team > share project
o assistente é aberto.
- marcar use or crate repository in parent folder of project
- marcar o projeto

na pasta do seu projeto será criado uma pasta .git.
esta é a pasta que diz que o projeto esta dentro do controle do git.
o git nao mexe nos arquivos do projeto. ele opera dentro desta pasta

- clicar no botao create repository
- finish

a apartir deste momento ja estamos usando o git

no eclipse vc pode verificar que o nome do repositorio apareceu no lado do nome do projeto
junto com o nome da branch, que neste caso é a master.

na pasta do projeto, a pasta .git esta escondida, mas ela existe.

#### perspectiva git
adicionar a perspectiva git
nela será exibida os repositorios importados/criados no git no eclipse

na view do lado esquerdo, no git repository mostra os repositorios cadastradnos no eclipse

importante frisar que o working tree é onde esta o seu codigo fonte atual.

na parte do meio, nas tabs, existem funcionalidades legais.
history mostra o historico
git staging agente usa para os commits
git reflog é o log do eclipse

assim a perspectiva git esta pronta para uso.

## Aula 2 conceitos iniciais do git
### Aula 2.1 realizando stages, commits e checkout
conceitos fundamentais do git:
staging é o fato de vc juntar arquivos para criar um snapshot, que é basicamente um print do stado do projeto.
unstaged changes é a lista que corresponde aos arquivos que estao fora do controle de versao. os arquivos aqui aparecem com um ponto de interrogaçao no icone do arquivo.
os arquivos .class nao precisam ser comitados, pois eles podem ser gerados pelo compilamento dos arquivos java.
para colocar pastas ou arquivos para serem ignorados pelo git, devemos adicionalos ao arquivo .gitignore.
ao clicar no arquivo/pasta com o botao direito > team > ignore ele sera adicionado ao git ignore.
o commit é composto tambem por uma mensagem, um autor e um commiter.
para alterar as informaçoes do autori e commiter, agente pode configurar as informaçoes.
para fazer isso, na perspectiva do git, nos repositorios, no projeto, clicar com o direito e em properties.
e adicionamos uma nova entrada:
user.name e user.email

ao clicar no botao commit, os arquivos sao commitados para o repositorio local. nos arquivos que estao no controle de versao aparece um cilindro amarelo.

na aba history do git, é exibido todos os commits se vc estiver clicado no projeto e se vc estiver clicado em um arquivo, é exibido os commits que alteraram o arquivo selecionado.

 os arquivos que estao no controle de versao mas que foram alterados, no lado esquedo ndo nome do arquivo aparece um sinal de > (maior).

o commit pode ser considerado como um ponto de restauração, que vc pode regressar a este ponto no projeto, onde tudo o que estiver no projeto naquele momento em que o commit foi criado retornara.

o commit sempre sabe quem é o commit anterior a ele, assim em sequencia.

o HEAD é o commit ativo, o ultimo commit que foi realizado.
se vc retornar a algum commit mais antigo, o HEAD vai ser mudado para esse commit.

para retornar a algum commit é necessario fazer o checkout.

detached head significa que o seu commit ativo não representa o ultimo commit daquela sequencia e que não é recomendado fazer commits diretamente naquela branch, sendo recomendado criar uma nova branch.

### Aula 2.2 Executando a operação clean
imagine a seguinte situação: voce criou varias classes e/ou diretorios e o fim vc chegoua clonclusao de que nao era necessario esses arquivos ou que vc entendeu errado os requisitos. nessa caso vc quer apagar alguns arquivos ou ate mesmo tudo o que vc fez.
para isso existe o comando clean.

o comando clean permite que voce desfaça alteraçoes ainda nao commitadas.

para realizar este comando, na perspectiva do git, basta clicar no projeto com o botao direito e selecionar 
clean.

nessa fase é apresentado uma tela que pergunta se vc quer que limpe somente os arquivos ou os arquivos e pastas que vc criou.

### Aula 2.3 nomeando snapshots com tags
tags nada mais sao do que marcaçoes especiais de commits. uma versao estavel, etc.

para criar uma tag:
na aba history, clica com o botao direito no ultimo commit, e create tag.
a tela perguntará o nome da tag e uma mensagem.

### Aula 2.4 executando a operaçao revert commit
suponha que criamos uma nova classe. 
e que as alterações a esta classe foram commitadas.
imagine agora que voce quer desfazer as alteraçoes do commit. mas o commit é seguro, ou seja, não pode simplesmente ser apagado.
para isso usamos o **revert commit**.

como fazer um revert commit?
basta clicar com o botao direito no commit que voce quer reverter e selecionar **revert commit**.

repare que o git irá fazer um novo commit após o head atual. nesse novo commit ele desfaz tudo o que foi alterado no commit revertido.

desta forma é mantida a estabilidade do controle de versao e voce nao perde as alterações realizadas, caso um dia voce precise delas.

### Aula 2.5 pausando alteraçoes com stash
imagine que voce esta no meio de uma implementaçao e voce precisa parar para atender um chamado urgente. voce ainda nao terminou o que esta fazendo e o codigo pode nem estar compilando ainda mas voce precisa alterar o foco do seu trabalho para outro problema.

neste caso, o stash funcionará muito bem.
o que o stash faz é manter tudo o que voce esta fazendo guardado e retorna tudo para o estado do HEAD.

mais tarde voce pode recuperar o trabalho no ponto em que voce deixou.

como fazer um stash?
na visao do repositorio, clicar com o botao direito no projeto -> stashes -> stash changes

insira uma mensagem que será como voce se lembrará do que esta nos arquivos guardados.

como recuperar um stash?
na visao do repositorio, no projeto, aparece uma pasta chamada stashed commits. nesta pasta ficarao listados todos os stashes que voce fez.

para recuperar basta clicar com o botao direito no stash e selecionar **apply stashed changes**.

como apagar um stash?
na visao do repositorio, na pasta **stashed commits**, basta clicar com o botao direito no stash que voce quer apagar e selecionar **delete stashed commit**


### Aula 2.6 usando as funçoes de compare e replace do eclipse

o eclipse tem duas funçoes bem interessantes que trabalham junto com o git.

elas sao o compare e o replace.

o compare permite que voce compare uma classe local com a mesma classe no repositorio, seja ela na HEAD ou com um commit, entre outras.

o replace é basicamente igual, mas ele nao exibirá as diferenças, ele ira substituir o arquivo local com o arquivo indicado (HEAD ou commit ou outro disponivel).

como fazer um compare?
clicar com o botao direito no arquivo e selecionar **compare with**.
após, basta selecionar o local do arquivo que  voce quer comparar (HEAD, commit, etc)

na tela que abre, o lado esquerdo é o local e o lado direito é o arquivo no controle de versao.
nesta tela é exibida as diferenças entre os arquivos.

como fazer um replace?
clicar com o botao direito no arquivo e selecionar **replace with**.
selecionar a fonte de onde o arquivo será copiado(HEAD, commit, etc)

### Aula 3.1 Separando as linhas de desenvolvimento

branches sao 'ramos' no nosso projeto. sao ramificacoes no codigo, que permite separar o trabalho.

suponha que no nosso projeto tenha 5 commits na branch master.
se no penultimo commit criarmos uma branch a partir daquele momento, nessa nova branch nao constará o ultimo commit da branch master.

se nessa nova branch fizermos commits, a branch master nao terá essas alteraçoes (ate que realizemos um merge).

por conveção, usamos o nome **master** para a branch mais estavel do seu projeto.

quando vamos fazer uma implementaçao de uma funcionalidade, usamos branchs para realizar isso.

novamente, os nomes das branchs sao livres, sendo recomendado que se utilizem convençoes na nomenclatura.

como criar uma nova branch?
na aba historico do projeto, clicar com o botao direito no commit base da nova branch (nao precisa ser o ultimo, mas é recomendado que seja sempre o ultimo).

basta inserir o nome da branch.

OBS: quando se cria uma branch em cima de um commit anterior de outra branch, o HEAD da nova branch será movido para o commit base. essa situaçao cria um **detached head**, que o eclipse informa com um aviso.

### Aula 3.2 juntando branches com o fast forward merge

merges sao as junçoes de uma branch em outra.
existem varios tipos de merge mas neste exemplo vamos falar do fast forward.

o fast forward significa que, a branch de destino (master) está completamente alinhada com a branch de origem (a nova branch). todos os commits da master estao na nova branch e por isso, o merge irá somente integrar a nova branch na master. nisso, sera apenas 'adiantado' o head da master para o head da nova branch.

esse adiantamento, é basicamente um fast forward na branch master.

imagina que, voce cria uma nova branch baseada na branch master.

nela voce faz as alteraçoes necessarias e termina todas as alterações necessarias. 

como o master simboliza o codigo estavel, voce vai querer juntar as alteraçoes da nova branch na master.

como fazer o merge?
primeiro, vc deve fazer o checkout na branch de destino, no nosso caso, a master.

segundo, voce deve clicar com o botao direito no ultimo commit da branch que voce deseja juntar a master.

selecione merge e ele será realizado.

logo em seguida, é exibido o resultado do merge, com o tipo de merge utilizado e a lista de commits que foi juntada.

### Aula 3.3 excluindo branches que nao sao mais necessárias

a exclusao de branches é bem simples.

continuando o exemplo dado na outra aula, onde uma branch (func) foi mergeada na master.
como ela já foi mergeada, nao vamos mais precisar da branch func e ela pode ser deletada.

como deletar uma branch?
condiçao: a branch a ser deletada nao pode ser a branch atual (checkout).

clicar no ultimo commit da branch que voce quer apagar e selecione **delete branch**

se houver mais de uma branch naquele commit, ele pergunta qual branch devera ser deletada.

desta forma a branch func é deletada mas como ela foi mergeada com a master, o codigo contido nela esta tambem contido na branch master.

deletar branches mantem a limpeza no repositorio, permanecendo somente as branches ativas.


### Aula 3.4 usando o 3-way merge e resolvendo conflitos manualmente

neste exemplo vamos ver um exemplo de merge que gera conflito.

continuando com a situaçao da aula anterior, a branch master foi mergeada com a branch func e avançou. para simular o 3 way merge, vamos fazer um merge um pouco diferente. 

vamos fazer checkout na branch dados, e vamos mergear com a branch master.

como fazer este merge?
após o checkout na branch dados, clicamos com o botao direito no ultimo commit da branch master e selecionamos **merge**.

o resultado do merge, desta vez foi **conflicting**.

isso significa que houve um conflito em alguma classe na hora da junçao das duas branches e que o git nao sabe como resolver automaticamente.

o 3 way merging ocorreu poque o caminho percorrido pela master é diferente do caminho percorrido pelo dados, entao o git deve voltar no caminho da branch master, procurando o commit que existe em comum entre as duas branches.
esse commit sera chamado de c1.

o head da branch dados será o c2 e o head da branch master será o c3.

no eclipse, o projeto já nao compila mais pois o git inseriu em formado de comentario de conflito, as diferentes versoes do codigo, para que voce decida qual a versao final deverá ficar.

nos icones das classes aparecem o icone <<>> em vermelho.

no arquivo ele insere os codigos conflitantes usando <<<<<<<<<<HEAD, que irá ate os simbolos ==========
continuando ate os simbolos >>>>>>>> NOME DA BRANCH (no caso master);

a primeira parte é o que esta na sua branch atual ( a que voce fez checkout)  a segunda é a que esta na branch que voce esta tentando juntar a sua atual.

no nosso exemplo, tudo será juntado, entao apagamos os comentarios de conflito inseridos pelo git e salvamos a classe.

caso nao queiramos uma parte do codigo, apagamos ela tambem.

apos terminar a resolucao dos conflitos, vamos na aba do git staging, adicionamos as classes alteradas e o git sugere um commit message automatico. voce pode aceitar ou nao essa mensagem e a seguir voce deve clicar no botao commit.

agora foi criado um novo commit, que contem as alteraçoes todas que existiam na branch master. esse commit foi feito na branch dados. a partir deste momento, a branch dados esta com todo o historico de master mais as suas proprias alteraçoes.

o 3 way commit junta o c1, c2 e c3, junta tudo em um unico commit e sincroniza.

este commit é diferente, pois ele tem 2 'pais'. ele tem o pai da head da master e o pai da head de dados. o 3 ponto é o commit em que as duas branches estavam sincronizadas (c1).


### Aula 4.1  usando o rebase para mover um branch para outro local

imagine que voce precisa fazer um hotfix no projeto. esse hotfix precisa ser baseado na tag 1.0

voce vai la e corrige o problema. mas agora voce quer inserir o codigo do hotfix na master. mas a master esta muito mais avançada.

caso utilize o merge, ele ira fazer um novo commit, juntando todos os commits que faltam da master no hotfix e realizando o 3-way merge.

mas existe uma outra opçao, que é o rebase.

o que é o rebase?
o rebase, como o nome diz, é rebasear a branch em outra branch, ou seja, mudar o pai.

quando criamos a branch hotfix, criamos baseado na tag 1.0 (tags aqui tem o comportamento de branchs). o rebase irá pegar todos os commits da master e colocar os commits da hotfix no final, fazendo com que todos os commits da hotfix sejam movimentados para o fim e alterando o pai da hotfix para a master.

embora isso seja semelhante ao 3-way merge, ele possui algumas vantagens como por exemplo, nao será realizado um commit de merge das diferenças da master na hotfix. isso mantem o historico mais limpo.

como fazer um rebase?
primeiro devemos dar check out na branch que queremos movimentar, no caso na hotfix.
depois clicamos com o botao direito na branch que queremos que seja o pai, e selecionamos a opção "Rebase HEAD on".

### Aula 4.2 explorando as operaçoes mais comuns do interactive rebase

o rebase interativo é um rebase normal mas que permite algumas alteraçoes nos commits do historico que esta sendo rebaseado.

como fazer um rebase interativo?
fazer checkout na branch que se quer rebasear, no nosso exemplo, a branch dados.

depois, clicar com o botao direito na branch master e selecionar **interactive rebase**.

é exibida uma nova aba que contem os commits que serao rebaseados.

note que no nosso exemplo, neste momento, a branch dados tinha tres commits, dois de codigo e o ultimo de merge, criado pelo 3-way merge.

mas na aba nova somente apareceu os dois commits de codigo. isso porque o terceiro commit foi a junçao do codigo da master na dados. como foi uma junçao, todos aqueles commits que foram juntados já existem na master, logo nao precisam ser adicionados novamente.

neste nosso exemplo, iremos juntar os dois commits de codigo em um só. mas tambem explicaremos as outras opçoes.

#### squash
junta os commits selecionados e permite ediçao do commit final. 

#### pick 
escolhe o commit como ele esta

#### skip 
retira o commit do processo de rebase

#### edit
edita o commit

#### fix up
junta o commit igual o squash mas mantem a mensagem do commit anterior

#### reword
altera a mensagem de commit

continuando o nosso rebase interativo de exemplo, com o squash

o primeiro commit fica marcado como **pick**
o segundo commit fica marcado como **squash**

e clicamos em **start**

neste nosso exemplo ocorre um conflito.
o conflito deve ser resolvido para o rebase continuar, mas é igual a todas as outras resoluçoes de conflitos.

a diferença e que, apos a resolucao do conflito e a adiçao dos arquivos no **staged changes** não é preciso realizar o commit em si, bastando mandar o rebase continuar (rebase continue), na aba git staging.

a proxima janela será a de ediçao de mensagem, pois estamos fazendo um squash.

as linhas marcadas com # serao ignoradas (sao comentarios)

para continuar, apos editar a mensagem, clicar em reword

pronto, o interactive rebase terminou


### Aula 5.1 adicionando repositorios remotos e realizando o fetch

## clone
quando queremos buscar um repositorio já existente usamos a opçao 'clone'.

o clone faz exatamente o que o nome diz, ele copia um repositorio remoto para um repositorio local.

para fazer um clone em um repositorio:
no eclipse, na aba 'git repositories', clicar no link 'clone a git repository' ou no icone com uma flecha verde, um cilindro e uma nuvem.

na tela seguinte, sera perguntado a localizacao.
neste momento podemos colocar um URI do github por exemplo ou podemos colocar arquivos locais.

na proxima tela será trazida a lista de branches existentes no repositorio remoto. selecione ou de-selecione as pretendidas e clique em next.

na proxima tela é a que informa o diretorio de destino, ou seja, onde na sua maquina vai ficar armazendo o clone.

clique em finish.

ainda na aba 'git repositories', o repositorio clonado é exibido.

nele temos a pasta 'Remotes' e dentro dela a pasta 'origin'.

origin é o nome escolhido pelo git para designar o repositorio remoto.

para importar o projeto do repositorio, basta clicar com o botao direito e selecionar import projects


as alteraçoes feitas no repositorio local nao sao propagadas para o repositorio remoto, a nao ser que sejam efetuados comandos como o push.

## criar um novo branch
selecionado o projeto, clicar com o botao direito e selecionar 'create branch'

a source diz em qual branch será baseado a nova branch.

inserimos o nome da branch, deixamos marcado 'configure upstream for push e pull'

selecionamos 'rebase' no campo 'when pulling'

deixamos marcado o campo 'check out new branch'

## adicionar um repositorio remoto
em um projeto local ja existente, é possivel adicionar um repositorio remoto.

para fazer isso:
na aba 'git repositories',  no repositorio local, existe uma aba chamada 'remotes'.

clicar com o botao direito em 'remotes' e selecionar 'create remote'

deixamos o nome como origin e clicamos no botao 'create'

na proxima tela, clicamos em 'change' para podermos inserir a localizacao.

a localizacao pode ser um URI do github ou um projeto local.

para este exemplo vamos usar o repositorio local.

selecionamos a pasta onde esta o repositorio local e clicamos em 'finish' e em 'save'.

em 'remotes', o repositorio 'origin' foi criado. dentro dele tem duas vertentes, uma flecha vermelha pra cima e outra verde para baixo.

a verde sao as configuracoes de fetch, que é buscar.

a vermelha sao as de push, que é enviar.

para recuperar as alteraçoes no repositorio remoto, bast irmos na vertente de fetch, clicar com o botao direito e selecionar 'fetch'.

caso apareça um aviso 'problem ocurred -- fetch from xxxxx has encontered a problem --- nothing to fetch' precisamos configurar o fetch.

## para configurar o fetch
clicar na vertente de fetch com o botao direito e selecionar 'configure fetch'.

na tela que se abre, deveria existir um ref mapping.
como nao existe, clicamos em 'add' para realizar o mapeamento do repositorio remoto para o repositorio local (no caso o master do remoto no master do local).

no campo 'source', colocamos o nome da branch master (da origin) e no campo 'destination' colocamos o nome da branch master (do local).

clicamos em 'finish' e em 'save'

## fetch
para fazermos um fetch de uma branch remota, basta clicarmos com o botao direito na vertente de fetch. 

as alteraçoes que nao estao em nosso repositorio local sao exibidas.

o fetch busca as alteraçoes presentes na branch remota para o nosso repositorio local


### Aula 5.2 usando a operação remote push

## push
o push é enviar os dados da brach local para o repositorio remoto.

para fazer o push basta clicar na vertente de push e clicar com o botao direito em 'push'.

caso aconteça o erro de mapeamento, basta configurar o push, clicando em 'configure push' na vertente de push, como fizemos no pull, com o detalhe que agora estamos configurando a branch local para a branch remota.

fazendo de novo o passo de clicar na vertente de push e clicar com o botao direito em 'push'.

é exibido as alterçaoes locais que nao existiam no repositorio remoto.

pronto. o push para o repositorio remoto foi feito.


### Aula 6.1 criando o repositorio remoto

a criação de um repositorio no github é muito simples e nao será mencionado neste capitulo.

## configurar o usuario do git no eclipse
clicar com o botao direito no repositorio e selecionar 'properties'.

adicionar ou alterar:
user.name
e 
user.email

o github agora usa 2 way authentication

## configurar o token
Login to your Github Profile
Go to Setting
Go to Developer Setting
Click on Generate New Token
Give a name to your Token, select all the Check Boxes.
Generate the token.
Your token will be created, copy the token, and paste it in eclipse in the password section while importing project from Git. Username will be your git Username. Select HTTPS mode while importing in Eclipse.
Now you will be able to see your Branch. Pull appropriate one.


### Aula 6.2 fazendo alteraçoes locais e publicando no repositorio central

para publicar as alteraçoes locais no repositorio remoto é facil, basta que as alteraçoes locais estejam em uma branch e voce já tenha efetuado o commit.

após isso é só enviar as alteracoes.

na aba 'git repositories' na vertente de push, clicar com o botao direito e selecionar push.

uma tela é exibida mostrando os commits enviados para o repositorio remoto.

se o push for dado em branches comunitarias tipo a master, é importante sincronizar a master local com a master remota antes de realizar os commits, pois haverá diferenças caso outro desenvolvedor tenha enviado as alteraçoes antes de voce.





