---
comments: true
date: 2012-06-25 19:43:34
layout: post
slug: voce-conhece-tipografia-utilizando-fontes-ricas-na-web
title: Você conhece Tipografía? Utilizando fontes ricas na web.
wordpress_id: 342
author:
- guilherme
categories:
- Dicas web
- Você conhece?
tags:
- CSS
- CSS3
- Dispositivos moveis
- Fontes
- mobile
- Tipografia
---

Acredite ou não, a tipografía é um campo enorme, de grande interesse e pode ter um efeito profundo no resultado do seu trabalho. Até pouco tempo a web esteve um tanto limitada quanto ao uso de fontes, ficando restrito às que o usuário possuía em seu sistema. Agora as coisas estão um pouco melhor, porém antes mostrar como utilizar fontes mais ricas em sistemas web veremos um pouco mais sobre tipografía.




[singlepic id=20 w=320 h=240 float=right]É importante saber que um dos princípios teóricos por traz do Design Gráfico é o Equilibrio, no entanto ele nem sempre é alcançado pela uniformidade. A fonte Gill Sans possui a caracteristica de ser perceptivelmente equilibrada, mas se você perceber a espessura de suas linhas variam em diferentes pontos dos seus traços. Veja imagem ao lado.




Para avaliar uma fonte é preciso saber qual é a sua anatomia e terminologia, na imagem estão algumas delas. Não vou discutir cada detalhe, vou me restringir a abordar algumas questões que são importantes e que podem fazer grande diferença no seu trabalho.




[singlepic id=21 w=480 h=360 float=center]




Começando pelo fato de que o tamanho da fonte não é consistente entre diferentes fontes, podendo variar consideravelmente. Já a Altura-x é um parâmetro muito importante em relação a legibilidade. Costuma-se utilizar fontes com alta Altura-x (Lucida Bright ou Georgia) para paragrafos e textos mais densos pois é mais fácil de ler em tamanhos de fonte menores e em dispositivos com telas de menor resolução. Já uma Altura-x baixa (Baskerville) costuma ser usada para passar percepção de elegância, dando uma sensação de Belle Époch. Fontes com Ascendentes e Descendentes baixos tendem a ter alta Altura-x e vice e versa. Se eles forem excessivos podem atrapalhar a visualização em dispositivos de menores resolução, pois alem de comprometer a Altura-x, exigem maiores espaçamentos entre linhas.




[singlepic id=23 w=320 h=240 float=left]Tambem existem duas importantes distinções de tipos de fontes, serifs e sans serifs (sem serifs). Há quem diga que serifs devem ser utilizadas para longos blocos de texto por ajudarem a distinguir as letras, porem não existem evidências concretas disso. Já para dispositivos móveis, serifs podem ficar borradas ou não ter resolução suficiente para ficarem legíveis, por isso indica-se utilizar sans serif ou as chamadas square serifs. A maior influência em questão de legibilidade esta relacionado ao comportamento de nosso cérebro que é treinado a reconhecer as letras e portanto, aquela fonte mais comum e difundida será mais legível devido ao treinamento do cérebro.




Veja essa imagem por exemplo:




[singlepic id=22 w=320 h=240 float=]




Você leu The Cat certo? Por que não Tae cht? Tae cat? Você ja sabe a resposta.




E essa você conhecia?





> 

> 
> “De aorcdo com uma psqueisa da Unvireisadde de Cmabrigde, não ipmrota a odrem em que as lteras em uma plavara etsão, a úcina cisoa ipmotratne é que a piremira e a útimla ltreas etseajm no lguar ctreo. O rseto pdoe etasr uma ttaol bnauguça e vcoê adnia pdoreá ler sem perolbmea. Itso pruqoe a mtene haunma não lê cdaa lreta idnvidailuemtne, mas a pvrlaaa cmoo um tdoo.”
> 
> 





Acredito que essa breve apresentação sobre essas curiosidades da tipografia são suficientes para te fazer encarar as fontes de uma forma totalmente diferente e espero que para melhor (e não vá bagunçar as letras).




Agora vamos para a parte prática. Como utilizar fontes ricas em sistemas web? A maneira atualmente mais segura é utilizar o método de CSS chamado @font-face. Ela permite baixar uma determinada fonte de seu servidor para ser mostrada em uma página web mesmo que o usuário não possua a fonte instalada. A sintaxe básica é bastante simples. A propriedade font-family dentro de @font-face irá definir como você utilizará a fonte no restante do css (veja utilização em .exemplo). Além disso você precisa do arquivo da fonte e declarar de onde ele será carregado, fornecendo opcionalmente o formato.


{% gist 2990412 %}


Deve-se sempre considerar a possibilidade de não haver suporte para o formato da fonte. Quando desenvolvemos para a web devemos lembrar que ela é universal, pode ser acessada não apenas de seu smartphone ou desktop, mas de geladeiras, carros, etc. Note que após declarar a fonte “TK4F” na classe .exemplo, temos outras fontes separadas por virgula, elas são fallbacks e substituirão em ordem a fonte antecessora caso ela não possa ser carregada. Mesmo nos desktops há dores de cabeça, especialmente quanto ao formato e licensas das fontes. No final do post você encontra links para mais informações sobre os tipos e suportes cross-browsers. Além disso, você pode ver um exemplo de utilização de fontes e tambem experimentar e verificar os conceitos aprendidos nesse post em [um site que construí como exercicio](http://samuraiplayground.appspot.com/tipografia) enquanto aprendia jQuery.




**Veja mais:**






	
  * Opções de Fontes:

	
    * [http://www.fontsquirrel.com/](http://www.fontsquirrel.com/)

	
    * [http://www.fontex.org/](http://www.fontex.org/)

	
    * [http://www.google.com/webfonts/](http://www.google.com/webfonts/)

	
    * [http://www.fonts.com/web-fonts](http://www.fonts.com/web-fonts)




	
  * Suporte dos browsers aos tipos de fontes: [http://webfonts.info/wiki/index.php?title=@font-face_browser_support](http://webfonts.info/wiki/index.php?title=@font-face_browser_support)

	
  * Bulletproof @font-face: [http://paulirish.com/2009/bulletproof-font-face-implementation-syntax/](http://paulirish.com/2009/bulletproof-font-face-implementation-syntax/)


