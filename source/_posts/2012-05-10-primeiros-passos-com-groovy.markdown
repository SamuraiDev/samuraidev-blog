---
comments: true
date: 2012-05-10 21:44:28
layout: post
slug: primeiros-passos-com-groovy
title: Primeiros passos com Groovy
wordpress_id: 156
categories:
- Linguagens e frameworks
- Tutoriais
---

![Logo do Groovy](/wp-content/gallery/groovy/groovy-logo-medium.png)Olá pessoal, hoje vamos aprender como configurar e dar os primeiros passos com a linguagem Groovy. Ela é uma linguagem de programação dinâmica que roda na plataforma Java, ou seja, também é compilada para os famosos bytecodes Java, e foi inspirada em linguagens como Python, Ruby e Smalltalk. Ok, e o que eu ganho com isso? Agilidade no desenvolvimento e compatibilidade com códigos já escritos em Java! 
Além disso, Groovy é menos verboso e reduz o tempo de desenvolvimento em muitas das nossas tarefas corriqueiras como veremos em alguns exemplos em futuros posts.



## Instalação e configuração...



Para começar precisamos fazer o download no site do [Groovy](http://groovy.codehaus.org/Download). Se você já passou pelos passos de configuração de uma JDK, não encontrará dificuldades. Devemos descompactar o pacote num diretório qualquer (no caso do pacote binário) e adicionar o endereço completo deste diretório na variável de ambiente PATH do seu sistema. Para verificar se está tudo certo, podemos testar o seguinte comando (no Console do Linux, ou prompt do Windows) que irá apresentar a versão do Groovy que configuramos:


    
    
    [bsouza@bsouza ~]$ groovy -version
    Groovy Version: 1.8.4 JVM: 1.7.0_03
    



  




## Mão na massa!



Agora é a hora da diversão! Iremos codar nossos primeiros fontes Groovy. Uma facilidade, para quem é familiarizado com Java, é que você pode continuar utilizando a sintaxe Java e ir melhorando suas habilidades em Groovy aos poucos e assim, incorporar as facilidades do Groovy conforme vai evoluindo em seus estudos. 
Iniciaremos nossos testes com o Groovy Console, que é um editor simples onde podemos codar e testar a execução dos nossos primeiros códigos:

![Editor simples com um console que acompanha a sdk do Groovy](/wp-content/gallery/groovy/groovyconsole.png)

Para executar o Groovy Console devemos digitar no Console o comando groovyConsole. 




DICA: Java importa automaticamente todas as classes que estão no package java.lang. Groovy por sua vez, extende este comportamento incluindo os pacotes abaixo:
- java.io
- java.math
- java.net		
- java.util
- groovy.lang
- groovy.util




  


Em Groovy utilizamos a palavra reservada def para definir algo, essa definição pode ser um método, variáveis com tipagem dinâmica e até closures. Veremos a utilização desta e outras keywords principais da linguagem. Mãos à obra...




DICA: Para limpar a saida do console utilize o atalho ctrl+w e para rodar o seu script utilize ctrl+r.




  



    
    
    // definição de um tipo Integer do Java
    int numero = 5
    println numero.class
    
    // definição de uma String do Java
    String nome = "Bruno"
    println nome.class
    
    /** **************************************************************************
     * Note que em Groovy, quando temos um método que recebe apenas um parâmetro,
     * podemos ocultar os parenteses, favorecendo assim a legibilidade do código 
     * ***************************************************************************/
    
    // Define uma String em tempo de execução através do seu comportamente,o chamado 
    // Duck Typing, ou seja, se o objeto se comporta de uma pato, então ele é um pato.
    def duck = "Bruno Moraes Souza"
    println duck.class
    
    /** ****************************************************************************
     * Agora iremos definir duas classes com um relacionamento entre elas, e iremos
     * fazer mais alguns testes para ver como o Duck Typing se comporta
     * *****************************************************************************/
    
    // classe mutavel que representará um produto
    class Produto {        
        String name
        String descricao
    }
    
    /* OBS: Não estamos declarando os getters e os setters
       pois o próprio Groovy faz esse trabalho sujo para nós,
       estes são os chamados Groovy Beans. 
       
       OBS 2: Repare também, que em Groovy podemos omitir o 
       ponto e vírgula ao final de cada linha */
    
    println "" // simples quebra de linha para facilitar a visualização dos novos resultados
    
    // Instancia um objeto Tipo e popula seus dados através de setters
    def produto = new Produto() 
    produto.name = "Sistema1"
    produto.descricao = "E-Commerce escrito em Grails \\o/"
    
    // Em Groovy, podemos utilizar interpolação de Strings conforme abaixo,
    // que é prático e mais legível que uma concatenação
    println "Produto: ${produto.name}\nDescrição: ${produto.descricao}\n"
    println "${produto.class}"
    println produto
    
    /* Note que como não sobrescrevemos o método toString da classe Produto,
     * em nosso print foi retornada a implementação da classe Object. 
     * Isso mesmo, os objetos Groovy também herdam de Object! */
    
    // Vamos agora utilizar o suporte a lista de Groovy e adicionar todas os 
    // objetos que instanciamos até agora
    
    def lista = [ numero, nome, duck, produto ]
    
    // Faremos uso agora de uma das facilidades do Groovy para 
    // trabalharmos com coleções, que é o método each
    
    println "" // quebra de linha
    lista.each { println it }
    
    // note que pela chamada do método, ele recebe apenas um parâmetro, e por isso
    // não precisamos dos parênteses. Ele recebe uma closure/delegate como parâmetro 
    // que será executada para cada um dos seus elementos e a keyword it representa o elemento atual
    
    println "" // quebra de linha
    lista.each { println ((it.class == Produto) ? it.name : it) }
    
    // Para testar a real utilização do it, colocamos um operador ternário, 
    // para imprimirmos o nome do tipo, caso o elemento seja um Tipo
    
    /** 
     * Os Groovy Beans, como mencionados anteriormente, criam os getters
     * e setters para o nosso bean, porém em muitos casos gostariamos privar o acesso
     * de um setter para criarmos objetos imutáveis. Em Groovy podemos criar objetos
     * totalmente imutáveis com a anotação @Immutable antes da definição da classe */
     
    @Immutable class ProdutoImutavel {
    
        String nome
        String descricao
        
        String toString() { nome } // Sobrescrita do método toString
    }
    
    /* Na classe acima, declaramos os mesmos atributos da classe anterior, porém
     * estes são read only, e nos obrigam a utiliza um recurso bem bacana do Groovy,
     * que é um construtor dinâmico. */
    
    println ""
     
    def imutavel = new ProdutoImutavel(nome: "Mouse", descricao: "Mouse wireless")
    println "${imutavel.nome} - ${imutavel.descricao}"
    
    // Para verifica se o comportamento é mesmo o esperado, tentaremos renomear o produto
    try { imutavel.nome = "novo" } catch (Exception ex) { println ex.message }
    
    println "${imutavel.nome} - ${imutavel.descricao}"
    println imutavel // teste do toString sobrescrito
    
    println ""
    
    // Por fim um teste com um atributo dinamicamente tipado
    class Dinamico {
        def algo
    }
    
    def d = new Dinamico()
    
    // Popula algo com uma string
    d.algo = "String"
    println d.algo
    
    // Setamos uma closure que recebe dois argumentos
    d.algo = { x, y -> (x * y / 2) }
    println d.algo(3, 6)
    
    



  





Na versão estável, 1.8.6 até a presente data, há um bug relacionado ao modificador de acesso private, permitindo que métodos e atributos que utilizem o modificador continuem expostos.




  


Bom, é isso! Acredito que toda a explicação necessária para o nosso primeiro exemplo está em forma de comentário no código e basta copiá-lo e executá-lo no console.

Espero que tenham gostado e até a próxima!
