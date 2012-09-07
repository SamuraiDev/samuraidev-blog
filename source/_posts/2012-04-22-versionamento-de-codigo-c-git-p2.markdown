---
comments: true
date: 2012-04-22 17:28:02
layout: post
slug: versionamento-de-codigo-c-git-p2
title: Versionamento de Código (c/ Git) p2
wordpress_id: 100
categories:
- Tutoriais
tags:
- Git
- GitHub
- Versionamento
---

No outro [post](http://samuraidev.com/tutoriais/versionamento-de-codigo-c-git-p1/), fiz uma introdução ao versionamento de código, falei sobre o Git e GitHub. Agora vamos ver mais de perto como essa ferramenta funciona. Ao fim desse post você vai ter visto como configurar e inicializar um repositório, realizar, gravar, desfazer e comparar mudanças, e ver o estado e historico de seus arquivos.


Se você vai utilizar o Git, seria muito legal tambem criar uma conta no [GitHub](https://github.com/). Não só porque ele oferece a hospedagem gratuita para repositórios de código livre, mas também por ser uma espécie de currículo utilizado no mercado de desenvolvimento. Além do GitHub, existem outros sites de hospedagem de repositórios para o Git, veja uma lista deles:
	
** Apenas respositórios públicos: **
	
  * [repo](http://repo.or.cz/)[.](http://repo.or.cz/)[or](http://repo.or.cz/)[.](http://repo.or.cz/)[cz](http://repo.or.cz/) é o mais antigo dos repositórios (completamente open source), hospeda apenas projetos de software livre e possui interface Gitweb (interface web padrão do GIT). O tamanho máximo não deve exceder 400M após realizar um repack (quando os dados são comprimidos em um unico arquivo).
  
  * [Gitorious](http://gitorious.org/) é outro repositório gratuito com interface web, suporte a multiplos repositórios por projeto, instalação local e open source;


** Repositórios públicos e privados: **


  * [Assembla](http://www.assembla.com/) oferece hospedagem segura e confiável, navegador de código web, onde é possivel navegar pelos changesets (revisões com alguma alteração de código), inclui bug/issue tracking e ferramentas colaborativas. Fornece repositório privado gratuito para até 1GB. Repositórios públicos são gratuitos.

  * [GitHub](https://github.com/) dispensa apresentação, é o maior site de hospedagem com mais de 1 milhão de repositórios públicos. Ele da ênfase à rede social de desenvolvedores de projetos.

  * [Bitbucket](https://bitbucket.org/) hospeda repositórios Git e Mercurial. É gratuito para repositórios privados com até 5 usuários (ou ilimitado para estudantes com email .edu), e totalmente gratuito para repositórios públicos. Tem wiki, issue tracking, entre outras funcionalidades.

** Apenas repositórios privados: **

  * [Unfuddle](http://unfuddle.com/) tem diversos planos, inclusive um gratuito. Ele é uma solução de gerenciamento de times de desenvolvedores de software. Oferece sistema de tickets, hospeda projetos com subversion ou Git, entre outras ferramentas para gerênciamento de projetos.

  * [codebase](http://www.codebasehq.com/) oferede controle de versão, sistema de tickets e acompanhamento de implantação. Possui um pacote gratuito com limitação de um projeto, 50MB, 2 usuários e sem nenhuma das ferramentas.


No outro post mostramos como instalar o Git, agora você deve criar um repositório e para isso existem basicamente duas maneiras:

  * Pegar um projeto ou repositório existente e importar para o Git.
  * Clonar um repositório Git existente.


# Inicializando um repositório em um diretório existente

Primeiro você deve navegar até o diretório do projeto e digitar o comando:
   
    $ git init

Será criado um novo subdiretório .git que contem um esqueleto de um repositório Git. Se o projeto não estava vazio, você deve adicionar todos arquivos no repositório com o comando add e em seguida realizar um commit. Assim todos seus arquivos estarão sendo “rastreados” pelo Git, exemplo:

    $ git add *.c
    $ git add README
    $ git commit -m ‘versão inicial do projeto’


# Clonando um repositório existente

Quando você deseja contribuir para um projeto existente o comando que precisará é o git clone. Se você esta familiarizado com outros sistemas de versionamento, note que esse comando se chama clone, e não checkout, porque existe uma importante diferença entre eles. Com o _git clone_, você recebe uma copia de praticamente todos dados contidos no servidor e se por acaso o disco do servidor for corrompido, é possivel usar qualquer clone de qualquer cliente para configurar o servidor no estado de quando ele foi clonado.

   $ git clone [url]

Exemplos de repositórios interessantes para serem clonados:

  * Git:    
    $ git clone https://github.com/gitster/git.git
  * Kernel Linux:
    $ git clone https://github.com/torvalds/linux.git
  * Ruby on Rails:
    $ git clone https://github.com/rails/rails.git
  * Lista de repositórios Android em: [https://github.com/android](https://github.com/android)


# Realizando mudanças no repositório

Agora que você ja sabe como criar ou clonar um projeto no Git, vamos ver como gravar mudanças no repositório. Cada arquivo do diretório do projeto pode estar em dois estados: _tracked_ ou _untracked_. _Tracked_ significa que eles estão na ultima “imagem” ou snapshot, e eles podem ser _unmodified_, _modified_, ou _staged_. Quando você clona um repositório, todos os arquivos serão _tracked_ e _unmodified_, porque você acabou de pega-los e não modificou nada ainda. A medida que você edita os arquivos eles passam a ser _modified_, porque eles mudaram desde o ultimo commit. Você então muda esses arquivos para estado _staged _(veja a seguir como fazer isso) para depois fazer um commit. Após o commit os arquivos que estavam anteriormente em staged passam a ser _unmodified _e o ciclo se reinicia. No entanto, se você criou um novo arquivo dentro do diretório do projeto, ele esta no estado _untracked_ e precisa ser adicionado ao estado _staged_ com o comando:

    $ git add [nome_do_arquivo]

E então realizar um commit com:
    
    $ git commit -m ‘comentarios do commit’

Veja uma imagem ilustrativa:

[singlepic id=8 w=320 h=240 float=center]

Um arquivo _untracked_ é como se o Git desconsiderasse esse arquivo.


## Verificando o estado de seus arquivos


Primeira coisa que vamos fazer é clonar o seguinte repositório: git@github.com:guilhermeka/Hello-Git.git


Antes de fazer qualquer alteração digite o comando:
    
    $ git status

Você deve receber a seguinte resposta do terminal:

_   # On branch master_
    _ nothing to commit (working directory clean)_


Significa que não há nada para ser comitado. Agora crie um arquivo texto qualquer no diretório e repita o comando, você deve receber o seguinte retorno:


  _# On branch master_
  _# Untracked files:_
  _# (use "git add <file>..." to include in what will be committed)_
  _#_
  _# nome_do_arquivo.txt_
  _nothing added to commit but untracked files present (use "git add" to track)_


Agora existe um arquivo que esta no estado _untracked_. Execute o comando git add no arquivo ($ git add nome_do_arquivo.txt) e veja novamente o estado.


  _# On branch master_
  _# Changes to be committed:_
  _# (use "git reset HEAD <file>..." to unstage)_
  _#_
  _# new file: nome_do_arquivo.txt_
  _#_

O arquivo agora esta no estado _staged _(quando esta pronto para o commit). Agora abra o arquivo nomes.txt, adicione seu nome ao fim da lista e salve-o. Verifique o estado do projeto novamente.


  _# On branch master_
  _# Changes to be committed:_
  _# (use "git reset HEAD <file>..." to unstage)_
  _#_
  _# new file: nome_do_arquivo.txt_
  _#_
  _# Changed but not updated:_
  _# (use "git add <file>..." to update what will be committed)_
  _#_
  _# modified: nomes.txt_
  _#_

Surgiu um novo arquivo na lista (nomes.txt) que esta no estado _modified_. Isso significa que ele foi alterado, mas se você realizar um commit agora ele não será incluido nele. Apenas os arquivos no estado _staged_ entram para o commit. Use o comando $ git add nomes.txt e verifique novamente o estado com o comando git status.

  _# On branch master_
  _# Changes to be committed:_
  _# (use "git reset HEAD <file>..." to unstage)_
  _#_
  _# new file: nome_do_arquivo.txt_
  _# modified: nomes.txt_
  _#_

Digamos que você esqueceu de colocar sua idade junto ao seu nome. Altere o arquivo e verifique novamente o estado.

  _# On branch master_
  _# Changes to be committed:_
  _# (use "git reset HEAD <file>..." to unstage)_
  _#_
  _# new file: nome_do_arquivo.txt_
  _# modified: nomes.txt_
  _#_
  _# Changed but not updated:_
  _# (use "git add <file>..." to update what will be committed)_
  _#_
  _# modified: nomes.txt_
  _#_

Veja que o arquivo nome consta em dois estados, staged e modified. Isso significa que se realizar um commit agora, o commit irá incluir apenas a versão do nomes.txt que não possui a sua idade. Você deve adiciona-lo denovo para o estado staged para incluir esses mudanças no commit. Faça isso e realize um commit.

   
    $ git add nomes.txt
    $ git commit -m ‘inclusão do nome Guilherme Kruger Araujo 25’


_*se você digitar apenas $ git commit, ele irá abrir o editor padrão do git para você inserir a mensagem de commit._

## Vendo as mudanças

Para ver as mudanças entre os arquivos que foram modificados e aqueles que estão _staged_ use o comando:
    
    $ git diff

*_esse comando usará a ferramenta configurada na __[parte](../../../../../tutoriais/versionamento-de-codigo-c-git-p1/)[ 1](../../../../../tutoriais/versionamento-de-codigo-c-git-p1/)__ desse tutorial._

Para ver as mudanças entre os arquivos staged e seu ultimo commit o comando é o seguinte:
 
    $ git diff --cached

É muito importante lembrar que o primeiro comando (git diff) não mostra as diferenças desde seu ultimo commit, apenas as diferenças dos seus arquivos que ainda não foram para o estado _staged_. Se você mudar todos arquivos para _staged_ o comando não irá retornar nada.


## Ignorando o estado staged

Se você quiser pular esses passos de adicionar arquivos para estado staged você pode simplesmente realizar o comando commit com a opção -a.
 
    $ git commit -a -m ‘Commit pulando a area staged’

Desse modo o Git automaticamente adiciona todos arquivos para _staged_ e realiza o commit.


## Removendo arquivos

Se você remover algum arquivo diretamente do diretorio, ele aparecerá sob status _modified_. Mas o git só o considera removido se você adiciona-lo para _staged _e posteriormente comitar.


  _# On branch master_
  _#_
  _# Changed but not updated:_
  _# (use "git add/rm <file>..." to update what will be committed)_
  _#_
  _# deleted: nome_do_arquivo_
  _#_


Para remove-lo diretamente utilize o comando:
    
    $ git rm nome_do_arquivo.txt

Esse comando irá tornar o arquivo _untracked_ e irá remove-lo. E você irá ve-lo da seguinte maneira no status.

  _# On branch master_
  _#_
  _# Changes to be committed:_
  _# (use "git reset HEAD <file>..." to unstage)_
  _#_
  _# deleted: nome_do_arquivo_
  _#_

Se você quiser apenas remover o arquivo da área _staged_ mas mante-lo no diretório use:
 
    $ git rm --cached nome_do_arquivo

*_o arquivo passará para o estado modificado. Esse comando apenas remove ele do estado staged. Seus arquivos continuam modificados. Considere staged como se fosse uma organização para o commit._


## Movendo arquivos

Se você mover algum arquivo o Git vai considerar que ele foi deletado e incluido um novo arquivo em uma nova localização (o mesmo se tiver renomeado). Se você quiser mover o arquivo ou renomea-lo basta usar o comando:
    
    $ git mv nome_do_arquivo_origem nome_do_arquivo_destino

Dessa forma o Git detecta se o arquivo foi renomeado ou movido, colocando-o no estado _staged_ automaticamente. Isso ocorre de forma muito semelhante a remoção de arquivos e pode parecer um pouco confuso.


## Visualizando histórico de commit

Para ver o histórico de commit execute o comando:
    
    $ git log

O resutlado será algo assim:

  _commit b0837c9d941a9e9549164aedaeb620d23d9ca6cc_
  _Author: Guilherme Araujo <gui2811@gmail.com>_
  _Date: Sat Apr 21 19:54:08 2012 -0300_
  _teste_

  _commit c5873bf79859688622b29a3d576c12e06cfd793b_
  _Author: Guilherme Araujo <gui2811@gmail.com>_
  _Date: Sat Apr 21 19:33:41 2012 -0300_
  _inclusão do nome Guilherme Kruger Araujo 25_

  _commit 6de3005ccc52f829d10ac78a2c3062796d96a135_
  _Author: Guilherme Araujo <gui2811@gmail.com>_
  _Date: Sat Apr 21 19:13:37 2012 -0300_
  _criando arquivos para o post_

  _commit c2df99536d815782a34a4bb64789e65aa4790947_
  _Author: Guilherme Araujo <gui2811@gmail.com>_
  _Date: Wed Apr 11 21:37:41 2012 -0300_
  _first commit_

Como padrão o Git coloca os commits em ordem reversa do que foram feitos, de modo que o mais recente apareça no topo. Ele tambem lista cada commit com o nome do autor, email, data, mensagem de commit e um número SHA-1 que serve para validar que os dados não foram corrompidos.

Existem diversas opções para esse comando, algumas que você pode achar interessante são -p para ver as diferenças introduzidas entre cada commit e -2 para limitar a saída para os dois ultimos commits (altere o valor de acordo com sua necessidade).


## Ferramenta grafica

Digite gitk, divitar-se.


## Mudando o ultimo commit

Ahh que droga, esqueceu de adicionar um arquivo no ultimo commit ??? Sem problemas, use:
    
    $ git add nome_arquivo
    $ git commit --amend

Esta tudo bem agora! Ele altera o commit e o Git trata ele como se você não tivesse esquecido do arquivo.


## Removendo do estado staged

Digamos que você modificou dois arquivos e gostaria de adiciona-los a diferentes commits, mas sem querer adicionou ambos ao estado staged. Use:
    
    $ git reset HEAD nome_arquivo

Assim você remove esse arquivo da área staged e ele passa a ser do estado _modified_.


## Desfazendo uma modificação

Bem simples, mas fique alerta, esse é um comando PERIGOSO! Todas as alterações feitas ao arquivos serão perdidas.
    
    $ git checkout -- nome_arquivo


# Para um próximo post

Legal, aprendemos bastante coisa! Mas para um próximo post fico devendo a parte em que trabalhamos com repositórios remotos e assim podemos efetivamente colaborar com qualquer projeto Git.


Até mais!
