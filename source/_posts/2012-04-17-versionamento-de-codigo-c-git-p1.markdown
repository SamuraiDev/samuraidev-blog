---
comments: true
date: 2012-04-17 16:54:18
layout: post
slug: versionamento-de-codigo-c-git-p1
title: Versionamento de Código (c/ Git) p1
wordpress_id: 66
author:
- guilherme
categories:
- Tutoriais
tags:
- Git
- GitHub
- Linus Trovalds
- Versionamento
---

Se você é um desenvolvedor entusiasta e gosta de estar por dentro das novidades desse mundo, vai encontrar aqui no SamuraiDev uma fonte riquissíma e abrangente sobre tecnologias e ferramentas de desenvolvimento, assim como debates e novidades envolvendo o tema.


Como muitos dos posts serão no estilo [DIY](http://pt.wikipedia.org/wiki/DIY), acredito que não existe uma melhor maneira de começar do que apresentar uma ferramenta que revolucionou a cultura do Desenvolvimento de Software. O [GitHub](https://github.com/)! Ele é uma plataforma social para o desenvolvimento de software construido ao redor do [Git](http://pt.wikipedia.org/wiki/Git), e traz uma nova abordagem para a escrita e compartilhamento de código. Enquanto o Git cuida da parte técnica, como fork e merge, o GitHub trata das questões sociais como requisições para pulls e o rastreamento de forks.


É interessante destacar que o Git foi criado por [Linus Trovalds](http://pt.wikipedia.org/wiki/Linus_Torvalds). Em uma divertida palestra para o Google Tech Talk, nomeada [Linus Trovalds on git](http://www.youtube.com/watch?v=4XpnKHJAok8), ele fala sobre as motivações de sua criação. Se por acaso você não deseja assistir aos 110 minutos de palestra, vou resumi-la rapidamente e introduzir o que é, e o que existe, em relação a versionamento de código.


Em um jogo rápido, um sistema de versionamento de código é uma ferramenta que você gostaria de ter caso não desenvolva sozinho e isolado no mundo (e mesmo desenvolvendo sozinho pode fazer bom uso do Git). Ele serve para gerênciar diferentes versões no desenvolvimento de software (ou de um documento qualquer), permitindo guardar históricos de código-fonte e documentação, criar diferentes linhas de desenvolvimento, marcar e resgatar versões estáveis, facilitando especialmente o desenvolvimento em equipes.


Em relação aos tipos de sistemas de versionamentos podemos separa-los em dois tipos: Centralizados e Descentralizados. No primeiro time dois exemplos são [CVS](http://pt.wikipedia.org/wiki/CVS) e [Subversion](http://pt.wikipedia.org/wiki/Subversion), muito criticados por Linus. E no outro estão [Mercurial](http://pt.wikipedia.org/wiki/Mercurial), BitKeeper e o Git. Se quiser existe uma [lista na Wiki](http://en.wikipedia.org/wiki/List_of_revision_control_software).


Segundo o próprio Linus, que ainda coordena o desenvolvimento do kernel Linux, o BitKeeper foi o primeiro sistema de versionamento existente que valia a pena usar. Para o criador do Linux, as caracteristicas básicas para tal sistema são necessariamente as seguintes:
	

**Distribuido: **Não é possível depender de um servidor centralizado, por varios motivos, que incluem conectividade, segurança e logistica. Se faltar conexão, ou houver problemas com o servidor central, todo o desenvolvimento é prejudicado. Na computação conhecemos isso como [Ponto Unico de Falha](http://pt.wikipedia.org/wiki/Ponto_%C3%BAnico_de_falha). Por isso um sistema distribuido é muito importante.


**Performance: **No Git, cada desenvolvedor possui uma copia local de toda história de desenvolvimento e pode trabalhar offline nessa copia. Isso permite realizar quase todas operações localmente, gerando um ganho enorme de performance. A maioria das operações parecem quase instantâneas.


**Confiabilidade**: Além disso, tudo o que é colocado no repositório deve ser confiável, de modo que você saiba, com certeza, que o que deixou nele não foi corrompido ou adulterado. O Git verifica a integridade de tudo que é armazenado com [SHA-1](http://pt.wikipedia.org/wiki/SHA1), o que torna impossível alterar algum dado sem que o Git saiba. Se por acaso forem perdidas informações o Git irá detectar.


# Instalando o Git

Como essa apresentação ja foi bastante longa, nessa primeira parte vou apenas mostrar como instalar o Git em seu sistema operacional.


**Linux**

No Fedora:
    
    $ yum install git-core

Debian-based (Ubuntu):
    
    $ apt-get install git-core


**Mac**

Faça o download de: [http://code.google.com/p/git-osx-installer](http://code.google.com/p/git-osx-installer)

Instale!


**Windows**

Faça o download de: [http://code.google.com/p/msysgit](http://code.google.com/p/msysgit)

Instale!


Facil né?! Mas antes de terminar, existem algumas configurações que você deve fazer ao menos uma vez (e poderá muda-las depois).


**Identidade**

A primeira delas é configurar sua identidade, que será incluida permanentemente em cada commit. É preciso realizar isso apenas uma vez se você passar a opção --global.

    
    $ git config --global user.name "Samurai Dev"
    $ git config --global user.email samurai@samuraidev.com


**Editor**

É bom configurar seu editor padrão, caso contrário, provavelmente utilizará o Vi ou Vim. Digamos que você deseje utilizar o emacs.

    
   $ git config --global core.editor emacs


**Ferramenta de Diff**

Configure também uma ferramenta para resolver os conflitos de merge.

   $ git config --global merge.tool vimdiff


**Finalmente**

Verifque as configurações com o comando: git config --list

Se precisar de ajuda use:
    
   $ git help comando
   $ git comando --help
   $ man git-comando

Se por acaso precisar de uma ajuda pessoal, um bom lugar para se encontrar é nos canais #git e #github no server Freenode (irc.freenode.net)

Nos próximos posts vou explicar mais detalhadamente o funcionamento do Git.

Se você não quiser esperar, deixo um Quick Start e alguns links interessantes.


**Links**:

[Pro Git](http://progit.org/)

[Git Cheat Sheet](http://byte.kde.org/%7Ezrusin/git/git-cheat-sheet-medium.png)

[Git Site Oficial](http://git-scm.com/)

[Everyday GIT](http://schacon.github.com/git/everyday.html)

[Git for computer scientists](http://eagain.net/articles/git-for-computer-scientists/)
