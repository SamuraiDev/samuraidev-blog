---
comments: true
date: 2012-05-07 08:15:20
layout: post
slug: css-inteligente-use-sass
title: CSS inteligente, use SASS!
wordpress_id: 183
author:
- bsouza
categories:
- Dicas web
- Tutoriais
---

Bom, o post de hoje é uma dica referente a desenvolvimento web, mais especificamente de CSS. Atualmente atuo como desenvolvedor mobile e já fazia algum tempo que não desenvolvia nada web, até o final do ano passado, quando nosso cliente teve a necessidade da reescrita de um sistema web. Em nosso time não há alguém responsável somente pelo layout, mas todos tínhamos conhecimento em CSS. Logo no início do projeto sentamos e discutimos alguns padrões para o layout do sistema, mas algo me incomodava na organização do CSS. O CSS, em sua criação, veio com a intenção de padronizar o layout do seu sistema/site, fazendo um controle centralizado dos estilos evitando assim a duplicação de código que torna simples alterações em tarefas custosas. Minha incomodação era justamente com essa centralização, ela ainda não estava correta, o CSS não cumpre totalmente o seu papel de evitar repetição de código e centralizar as mudanças, pois há muitas classes com comportamentos parecidos e que na maioria das vezes quando precisamos alterá-las gostaríamos que essas alterações afetassem todos esses padrões duplicados em nossas classes, e.g. uma cor padrão ou tamanho de margens. Foi nesse instante que um colega mencionou o SASS que traz todas essas melhorias que eu queria e o CSS não me proporcionava.



## Iniciando...



O SASS é uma ferramenta desenvolvida em Ruby, por isso devemos te-lo previamente instalado. Ele utiliza basicamente um arquivo com extensão .scss e a através deste arquivo ele irá gerar o CSS comum (aquele chato que faziamos antigamente) e a partir deste momento iremos dar manutenção apenas no arquivo .scss. SASS trabalha com quatro características principais: variáveis, aninhamento (nesting), mesclas (mixins) e herança.

Depois de instalado, devemos utilizar o comando abaixo para gerar nosso CSS:


    
    
    /* style é o nome do arquivo */
    sass --watch style.scss:style.css
    



  




## Variáveis


Utilizamos as variáveis para declarar atributos que podem ser utilizados em várias propriedades de diferentes classes. Por exemplo, podemos criar uma cor padrão que será utilizada em vários dos nossos estilos, e assim centralizamos a mudança, caso ela seja necessária ao decorrer do projeto:


    
    
    $color: #cccccc;
    .box { background-color: $color; }
    



  




## Nesting


Permite que façamos alterações somente a partir de determinado seletor, vejamos um exemplo abaixo de como fariamos sem SASS e como fica com SASS:


    
    
    /* CSS */
    .box { background-color: #cccccc; }
    .box img { size: 50px; }
    
    /* SASS */
    $icon-size: 50px;
    .box { background-color: $color; img { size: $icon-size; } }
    



  




## Mixins


Utilizamos para criar estilos que podem ser aproveitados em várias classes, e assim evitamos repetição:


    
    
    $default-border-color: #000000;
    @mixin default-box { border: 1px solid $default-border-color; background-color: $color; }
    .box { @include: default-box; color: #300; }
    



  




## Herança


A partir de uma classe já definida, podemos herdar todo o seu estilo e extendê-lo para criar outra classe customizada:


    
    
    .bold-box { @extend .box; font-weight: bold; }
    



  




## Exemplo completo...



Fiz um outro exemplo, agora com todos os passos. Primeiro naveguei até um diretório que criei para o exemplo, depois criei um arquivo e o editei:


    
    vim teste.scss



  


Dentro deste arquivo criei os seguintes estilos:


    
    
    $color: #CCC;
    $font: #003;
    $padding: 5px;
    
    @mixin borders { border: 2px solid #000; }
    @mixin default-box { height: 50px; padding: $padding; background-color: $color; }
    
    .box { @include borders; @include default-box; }
    .custom-box { @extend .box; color: $font; a { color: #fff; } }
    



  


Para gerar o meu css utilizei o comando:


    
    sass --watch teste.scss:style.css



  


No meu caso, o meu SASS teve o nome de teste.sass e dei o nome de style.css ao arquivo que gerei. O meu css "compilado" ficou assim:


    
    
    .box, .custom-box {
      border: 2px solid #000;
      height: 50px;
      padding: 5px;
      background-color: #cccccc; }
    
    .custom-box {
      color: #000033; }
      .custom-box a {
        color: #fff; }
    



  


Outra coisa que eu não havia mencionado é que você pode utilizar essa sintaxe que mostramos até agora ou uma outra bastante familiar a quem já trabalhou com YAML. Para utilizar essa outra sintaxe a extensão do nosso arquivo deve ser .sass, e o mesmo exemplo ficaria assim:


    
    
    $color: #CCC
    $font: #003
    $padding: 5px
    
    @mixin borders
            border: 2px solid #000
    
    @mixin default-box
            height: 50px
            padding: $padding
            background-color: $color
    
    .box
            @include borders
            @include default-box
    
    .custom-box
            @extend .box
            color: $font
            a
                   color: #fff
    



  




## Encerrando...



O SASS possui outras características e vantagens, mas acredito que essas já são o suficiente para lhe convencer a não escrever mais o CSS de forma tradicional. Para ir mais afundo você pode consultar o tutorial do [site](http://sass-lang.com/tutorial.html).

Espero que tenham gostado e até a próxima!
