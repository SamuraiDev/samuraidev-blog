---
comments: true
date: 2012-07-04 19:30:35
layout: post
slug: voce-conhece-ruby
title: Você conhece Ruby?
wordpress_id: 367
author:
- bsouza
categories:
- Linguagens e frameworks
- Você conhece?
tags:
- Matz
- Ruby
- RubyGem
- RVM
- Você Conhece?
---

[singlepic id=28]



Em mais um episodio da nossa serie "Voce conhece?",  apresentarei a linguagem Ruby. Porem nao entraremos em codigo desta vez, deixaremos esta tarefa para os proximos posts, hoje iremos focar na historia e no ecossistema Ruby.





## Um pouco de historia





Ruby nasceu no Japao! Começou a ser escrita por [Yukihiro Matsumoto](http://en.wikipedia.org/wiki/Yukihiro_Matsumoto), mais conhecido como Matz, em 24 de fevereiro de 1993. Matz conhecia muitas linguagens, mas nao estava completamente satisfeito com elas. Achava-as feias, difices e complexas, entao resolveu criar sua propria linguagem. Para isso, Matz misturou partes das suas linguagens favoritas (como Perl, Smalltalk, Lisp, Ada e Eiffel), criando uma linguagem que equilibra programaçao funcional com imperativa. Além disso, Ruby é uma linguagem interpretada, puramente orientada a objetos com tipagem forte e dinamica, possui uma poderosa capacidade de [metaprogramaçao](http://pt.wikipedia.org/wiki/Metaprograma%C3%A7%C3%A3o) e pode facilmente ser usada para criaçao de DSLs ([Domain Specific Language](http://en.wikipedia.org/wiki/Domain-specific_language)). Com todas essas caracteristicas, Matz conseguiu criar uma linguagem simples, pratica e muito expressiva!





CURIOSIDADE: Matz ganhou em 2011 o [FSF Free Software Awards](https://www.fsf.org/news/2011-free-software-awards-announced) pelo sua dedicaçao ao software livre nos ultimos 20 anos, contribuindo com o Ruby, projeto GNU e outros projetos open source.



  



## Interpretadores





O primeiro interpretador de Ruby foi o MRI (Matz Ruby Interpretr ou CRuby, pois e escrito em C). Com a popularizaçao da linguagem (que se deve em grande parte ao [Rails](http://rubyonrails.org/)), começaram a surgir outras  implementaçoes do interpretador, que deixaram de ser simples interpretadores e passaram a basear-se, na maioria, em Maquinas virtuais. Gostaria de destacar aqui o [JRuby](http://jruby.org/) e o [IronRuby](http://www.ironruby.net/), implementaçao da linguagem para rodar na JVM (maquina virtual do Java) e plataforma Microsoft (.Net), respectivamente. O fato curioso e que o JRuby e considerado por muitos a implementaçao mais rapida da linguagem. O IronRuby e mantido pela propria Microsoft (e e um dos primeiros projetos verdadeiramente open source da empresa).


  


## RVM





Em uma explicaçao minimalista podemos dizer que o [RMV](https://rvm.io/) (Ruby Version Manager) e uma ferramenta de linha de comando para gerenciamento de versoes Ruby. Com ele podemos ter varias versoes do Ruby (chamadas de Rubies pelo RVM) instaladas e alterar a que estamos utilizando muito facilmente. Podemos tambem criar gemsets, que sao ambientes separadas para organizarmos nossos projetos. Por exemplo, se eu tiver o ruby 1.8.6 e o jruby instalados, havera dois gemsets (um para cada um), entao posso ter uma versao diferente do rails em cada um. No caso tambem poderiamos criar um gemset para trabalhar com Rails 2 e outro para Rails 3, bastando assim uma rapida alteraçao via RVM para trocarmos de ambiente. Se voce ainda nao tem o Ruby instalado sugiro que ja comece instalando via rvm.






    
  * [Post interessante do Akita (um dos primeiros evangelistas de Ruby no Brasil) sobre o RVM](http://akitaonrails.com/2010/01/01/limpando-meu-ambiente-de-desenvolvimento)


    
  * [Post do Emerson Macedo (do Globo.com) sobre o gerenciamento do ambiente com RVM.](http://codificando.com/2010/07/gerencie-ambiente-ruby-rvm/)





OBS: O RVM nao roda em Windows. Nesse caso a alternativa e utilizar o           [pik](https://github.com/vertiginous/pik/). [Aqui](https://rvm.io/os/) voce pode encontrar a lista de sistemas suportados pelo RVM. 
[editado] Achei na própria documentação do Ruby este link para [instalar RVM no Windows com Cygwin](http://blog.developwithpassion.com/2012/03/30/installing-rvm-with-cygwin-on-windows/).






## IRB





O IRB (Interactive Ruby Shell) e um console interativo onde podemos fazer alguns testes com a linguagem. Tendo um ambiente corretamente configurado, basta digitar irb no terminal para inicia-lo.



[singlepic id=27]



## RubyGems





As RubyGems, ou simplesmente Gems, sao pacotes que contem uma biblioteca ou aplicaçao Ruby. Existe tambem a aplicaçao RubyGems (ferramenta de linha de comando) que e um gerenciador de pacotes e foi amplamente adotado pela comunidade Ruby. Com ele podemos de maneira muito simples baixar, instalar e manipular uma gem em nosso sistema.







  1. [Instalaçao do RubyGems](http://docs.rubygems.org/read/chapter/3)


  2. [Post do Nando Vieira sobre como criar uma RubyGem](http://simplesideias.com.br/criando-sua-propria-rubygem/)
  3. [Post do Akita falando sobre RubyGems](http://akitaonrails.com/2009/02/02/entendendo-rubygems)




## Algumas Gems







  * [Bundler](http://gembundler.com/): Gerenciador de dependencias.


  * [Capistrano](https://github.com/capistrano/capistrano/): Ferramenta para executar comandos/scripts paralelamente em maquinas remotas (via SSH).


  * [Rake](http://rake.rubyforge.org/): Ferramenta para automatizar a construçao da aplicaçao.


  * [Rack](http://rack.github.com/): Simples interface entre um servidor Web (com suporte a Ruby) e um framework Web Ruby. O [Sinatra](http://www.sinatrarb.com/) e o [Rails](http://rubyonrails.org/) sao exemplos de framework que o utilizam.


  * [Cucumber](http://cukes.info/) e [RSpec](http://rspec.info/): Ambos sao frameworks para testes que seguem o [BDD](http://pt.wikipedia.org/wiki/Behavior_Driven_Development).


  * [EventMachine](https://github.com/eventmachine/eventmachine/wiki/):Biblioteca que fornece operaçoes de entrada e saida orientada a eventos. Feito para combater o problema [C10k](http://en.wikipedia.org/wiki/C10k_problem).


  * [DataMapper](http://datamapper.org/) e [ActiveRecord](http://ar.rubyonrails.org/): Dois frameworks [ORM](http://en.wikipedia.org/wiki/Object-relational_mapping).


  * [TorqueBox](http://torquebox.org/): Servidor de aplicaçao Ruby escrito em cima do [JBoss AS](http://www.jboss.org/jbossas) com suporte para qualquer aplicaçao Rack.
 

[singlepic id=25]



## IDE





Ate existem algumas [IDEs](http://pt.wikipedia.org/wiki/Ambiente_de_Desenvolvimento_Integrado) para Ruby, mas a comunidade nao e muito fa. Confesso que a pouco tempo atras tentei montar novamente um ambiente com [Eclipse](http://www.eclipse.org/) e o [DLTK](http://www.eclipse.org/dltk/), porem, com a simplicidade de Ruby ficamos livre de uma ferramenta como essa, podendo adotar apenas um editor de texto simples (como o [Sublime Text](http://samuraidev.com/tutoriais/dica-de-editor-simples-sublimetext/)) e o terminal. Na verdade o Sublime é uma alternativa mais user-friendly, o comum mesmo é vermos o pessoal utilizando [VI](http://en.wikipedia.org/wiki/Vi) ou [Emacs](http://www.gnu.org/software/emacs/) no Linux e [TextMate](http://macromates.com/) no Mac.





## Finalizando...





Entao, tentei fazer uma introduçao rapida ao mundo Ruby de uma forma que eu gostaria de visto quando comecei. Logo que iniciamos o estudo de uma nova linguagem/plataforma somos bombardeados com nomes de aplicaçoes e frameworks, nessa hora paramos para pensar pra qual lado devemos correr primeiro. Espero que tenham gostado e ate a proxima!
