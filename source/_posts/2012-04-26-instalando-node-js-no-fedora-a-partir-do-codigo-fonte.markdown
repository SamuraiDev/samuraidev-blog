---
comments: true
date: 2012-04-26 19:21:09
layout: post
slug: instalando-node-js-no-fedora-a-partir-do-codigo-fonte
title: Instalando node.js no Fedora a partir do código fonte
wordpress_id: 139
categories:
- Linguagens e frameworks
- Tutoriais
tags:
- Fedora
- Git
- Node.js
- Source Code
- V8
author: "Guilherme Kruger Araujo"
---

O node.js é uma plataforma para construir, de uma forma fácil, aplicações de alta escalabilidade (como um servidor web). Construido sobre o [V8](http://pt.wikipedia.org/wiki/V8_%28JavaScript%29), Node.js usa um modelo orientado a eventos com entradas/saídas assíncronas (que não bloqueiam o servidor). Mas para que você consiga instalar o Node.js no Fedora, primeiro terá que instalar os seguintes pacotes:
    
{% img left /images/node-js.jpg %}

    # yum install openssl-devel
    # yum install gcc
    # yum install gcc-c++


Para pegar o código fonte você pode clonar pelo git ou buscar no site [http://nodejs.org/](http://nodejs.org/)
Pelo git:

    
    $ git clone git://github.com/joyent/node.git


É importante destacar que você estará pegando a mais recente versão do código no repositório. Se quiser uma versão anterior (provavelmente mais estável) busque pelas tags do programa e faça um checkout dessa tag.

    
    $ git tag
    $ git checkout [nome_da_tag]


Agora que você tem o código, navegue até a pasta node e prossiga com a instalação:

    
    $ cd node
    # ./configure
    # make -j2

Se você se deparar com o erro: "fatal error: gnu/stubs-64.h: No such file or directory" execute o seguinte comando:

    
    # yum install glibc-devel.x86_64


Termine a instalação:

    
    # make install


Adicione usr local ao PATH

    
    # export PATH=$PATH:/usr/local/bin:/usr/local


Execute o comando visudo para editar /etc/sudoers

    
    # visudo


Procure a linha que contem "Defaults secure_path=/sbin:/bin:/usr/sbin:/usr/bin" e adicione ao fim da linha ":/usr/local/bin" sem os parenteses. Você faz isso indo com cursor até o fim da linha, digite "i", escreva ":/usr/local/bin" e então, para salvar, aperte ESC e digite "wq", ENTER.

Para verificar a versão instalada:

    
    $ node -v


Pronto!
