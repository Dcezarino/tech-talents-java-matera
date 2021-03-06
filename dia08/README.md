# Dia 8

## 1 - Introdução a POO (Programação orientada a objetos)

### 1.1 - POO? O que é isso?

* Programação Orientada a Objetos, é um paradigma de programação criado nos anos 70 por Alan Kay, que tem como objetivo aproximar o mundo real do digital. Através de conceitos como objetos classes e outros.

### 1.2 - Histórico da programação

* As primeiras linguagens de programação são chamadas de baixo nível, onde era preciso programar instruções que somente o computador entenderia.

* Logo após começaram a surgir as primeiras linguagens de programação que humanos conseguiam ler e estruturar, linguagens como Assembly era famosas nessa época, era o surgimento da programação Linear.

````assembly
.MODEL SMALL ;modelo de memória
.STACK ;espaço de memória para instruções do programa na pilha
.CODE ;as linhas seguintes são instruções do programa
mov ah,01h ;move o valor 01h para o registrador ah
mov cx,07h ;move o valor 07h para o registrador cx
int 10h ;interrupção 10h
mov ah,4ch ;move o valor 4ch para o registrador ah
int 21h ;interrupção 21h
.DATA
x db 1
END ;finaliza o código do programa
````

* Com o surgimento de linguagens como Fortran, a era da programação estruturada começou, com o surgimento do Fortran, era mais simples construir programas, e construir sistemas mais complexos.
  
````fortran
      program moedas
      implicit none
C 
      integer i
      real reais, dollar, euro, dlrrl, eurrl
C relações dolar por real e euro por real
      data dlrrl, eurrl / 0.42768, 0.48715 /
C     constante do tipo ´real´
C 
C strings representando especificadores de formato
      character *30 form1, form2, sep *(*), line
      parameter ( sep = " ======== " )
      data form1     / "(1x,2(a12,5x,'|'),a12)" /
      data form2     / "(1x,2(f12.3,5x,'|'),f12.3)" /
      data line   / "(1x,49('-'))" /
C       
      write (*,*)  sep, "Tabela de conversao de moedas", sep
      write (*, line)
      write (*, form1 ) "Real","Dollar", "Euro"
      write (*, line)
C
C SINTAXE Fortran 77 puro:
C     do 100 i = 1, 10
C
      do i = 1, 10
        reais = i * 1.0
        dollar = reais * dlrrl
        euro     = reais * eurrl
        write (*, form2 ) reais, dollar, euro
C
C SINTAXE Fortran 77 puro:
C 100 continue
C  
      end do
      
      end program moedas

````

* Com o surgimento de linguagens com C surgiu a programação modular, facilitando ainda mais a maneira de criação de sistemas. Sendo popular até hoje principalmente para programação embarcada

````c
#include <stdio.h>
#include <conio.h>
void main()
{
   float NotaDaP1, NotaDaP2;
   float Media;
 
   clrscr();     // Limpa a tela
   NotaDaP1 = 6.6;  // Atribuição do Valores das médias
   NotaDaP2 = 8.2;

   Media = (NotaDaP1 + NotaDaP2) / 2.0;

   printf("Média Final : %6.3f", Media); 
      // No momento da execução sinal %6.3f vai ser substituído 
      // pelo valor da variável Media
        // Média Final :  7.400
   getch();      // espera que o usuário pressione uma tecla
}
````

* Finalmente chegamos a programação orientada a objetos, onde facilitou ainda mais a criação de sistemas com o surgimento de agrupamentos de dados agrupados menores e classes e objetos. A primeira linguagem a surgir com esse paradigma foi uma linguagem chamada Smalltalk, e influenciou diversas linguagens futuras como Java, C++ e muitas outras

````smalltalk
Integer extend [

  "Traduzido da versão em C"
  isPerfectC [ |tot| tot := 1.
     (2 to: (self sqrt) + 1) do: [ :i |
        (self rem: i) = 0
        ifTrue: [ |q|
                  tot := tot + i.
                  q := self // i.
                  q > i ifTrue: [ tot := tot + q ]
        ]
     ].
     ^ tot = self
  ]

  "Outra maneira"
  isPerfect [
     ^ ( ( ( 2 to: self // 2 + 1) select: [ :a | (self rem: a) = 0 ] )
         inject: 1 into: [ :a :b | a + b ] ) = self
  ]
]

````

### 1.3 - Quem criou?

* OO(Orientação a Objetos) foi pensada e idealizada por Alan Kay. Com sua formação em Matemática e Biologia, Kay começou a trabalhar com computação na decada de 70 onde trabalhou em empresas como Xerox e Apple. Em seu trabalho na Xerox, Alan contribuiu para a criação de diversas invenções que mudaram o rumo da computação até hoje como o mouse, interface gráfica e o padrão Ethernet.

* Uma de suas invenções foi o Dynabook, um protótipo de computador onde parecido com um caderno (ou notebook em inglês) tinha a característica de ter uma tela na parte superior e um teclado na parte inferior. Alan queria que com essa invenção estudantes pudessem desenvolver novas habilidades e facilitar o aprendizado.

* Porém para a criação do Dynabook, Alan não poderia utilizar as linguagens da atualidade, para isto ele precisava criar uma nova linguagem que fosse mais adaptável e simples de se utilizar, onde tudo se comportasse como objetos. Surgia assim o Smalltalk.

* Alan criou um postulado de como deveria ser o computador ideal: "o computador ideal deveria funcionar como um organismo vivo, isto é, cada "célula" comportar-se-ia relacionando-se com outras a fim de alcançar um objetivo, contudo, funcionando de forma autônoma. As células poderiam também reagrupar-se para resolver um outro problema ou desempenhar outras funções."

### 1.4 - Diferenças entre paradigmas

* Em paradigmas não orientados a objetos, eram utilizados conjuntos globais de dados e vários procedimentos modulares ou estruturados, onde eles precisam filtrar dados para inicialmente trabalhar com eles.
  
* Isso faz com que os dados fiquem mais difíceis, os dados são globais, ou seja, não existe bem uma separação de fato. Por isto, cada função ou procedimento, deve filtrar quais dados vão ser utilizados para se utilizar.

* OO foi pensado para se trabalhar com dados menores, e mais encapsulados em uma estrutura que chamamos de objetos. E sendo assim, temos procedimentos que usam apenas esses dados.

### 1.5 - Linguagens que utilizam POO

* C++
* Java
* PHP
* Python
* Ruby
* C#
* Swift
* Kotlin

### 1.6 - Vantagens de se utilizar POO

Temos 6 principais vantagens

* C -> confiável

 o isolamento entre as partes, gera software seguro. Ao alterar uma parte, nenhuma outra é afetada

* O -> Oportuno

 Ao dividir tudo em partes, várias delas podem ser desenvolvidas em paralelo

* M -> Manutenível

 Atualizar um software é mais fácil. Uma pequena modificação vai beneficiar todas as partes que usarem o objeto

* E -> Extensível

 O software não é estático. Ele deve crescer para permanecer útil

* R -> Reutilizável

 Podemos usar objetos de um sistema que criamos, em um outro sistema futuro

* N -> Natural

 Algo mais fácil de entender. Você se preocupa mais na funcionalidade do que nos detalhes de implementação.

## 2 - Fundamentos de POO

### 2.1 - Fundamentos - Abstração

* Uma das definições do dicionário Michaelis, que mais se encaixa em nosso contexto é: "Processo pelo qual se isolam características de um objeto,considerando os que tenham em comum certos grupos de objetos"

* O que tiramos desta definição é que devemos nos preocupar com características menos importantes. Concentrando assim em aspectos essenciais.

* Portanto, por sua natureza, abstrações são incompleta e imprecisas, mas isto não quer dizer que ela perde sua utilidade.

* Por exemplo: Se uma fabrica de cadeiras pensa em fabricar e vender suas cadeiras que um dia ela vai vender, ela pode inicialmente pensar em uma cadeira mais abstrata, dessa forma, o processo de produção seria mais simples, pois ela não saberá inicialmente que tipos de cadeiras vão vender e quais fabricar. A cadeira poderia ter um assento, 4 pés e um encosto.

* A partir disto ela poderia criar cadeiras de praia, cadeiras para aulas e ate mesmo cadeiras mais modernas, de diversos tipos. E a medida que poderia vir demanda ela adaptaria sua linha de produção

* Esse processo de inicialmente se pensar mais abstrato e posteriormente se adaptar também é conhecido como abstração e especialização, respectivamente.

### 2.2 - Fundamentos - Reúso

* A pior pratica em programação é a repetição de código. Levando a um código frágil e que pode facilmente gerar resultados inesperados e propícios. Quando há uma atualização facilmente pode-se esquecer de atualizar alguma parte e isso levará a varias inconsistências em diversas partes da aplicação.
  
* Para alcançar este fundamento, OO provê conceitos que visam facilitar sua aplicação. Entretanto, o fato de se usar OO por só não levara ao reúso, è preciso trabalhar de forma eficiente, para aplicar conceitos de herança e composição, por exemplo.

* Na herança é possível criar classes baseadas em outras classes. Como consequência disso, ocorre o reaproveitamento de código -dados e comportamentos-. Uma vez que a classe filha (que é como chamamos a classe criada baseada em outra) além de reaproveitar o código da classe mãe (que é como chamamos a classe base) pode adicionar seus propiás códigos.

* Já na composição,uma classe pede a outra para fazer o que ela não pode fazer por si só. Desta forma, a composição permite a troca multa de código, culminando em evitar a repetição de código.

* Estes contanto são as formas mais básicas e base para o reúso em linguagens orientadas a objetos.

### 2.3 - Fundamentos Encapsulamento

* Seria pelo menos desesperador se fosse-mos ao medico com um simples resfriado e no final da consulta ele passe esta receita para nos receitar-mos.
  
```markdown
**Receituário medico (complexo)**
  * 400mg de ácido acetilsalicílico
  * 1mg de maleato de dexclorfeniramina
  * 10mg de cloridrato de fenilefrina
  * 30mg de cafeína.
*Misturar bem e ingerir com água. Repetir em momentos de crise*
```  

* Onde vamos achar essas substancias? Será que é vendido tão pouco assim? Como misturá-las? Tarefa difícil não acha?

* Desta forma os médicos passam de forma mais simples e uma capsula, onde todas essas substancias estão encapsuladas, ou seja, já estão prontas para utilização.

* Cpm isto não é preciso se preocupar com diversas questões que envolvem as substancias, somente utiliza-las. 

````markdown
**RECEITUÁRIO (ENCAPSULADO)**
1 comprimido de Resfriol. Ingerir com água. Repetir em momentos de crise.
````

* Esta mesma ideia se aplica em Orientação a Objetos. Desta forma podemos esconder complexidade de uma implementação. E assim, somente nos preocuparmos em utilizar-mos.

## 3 - Exercícios

1. Por que é importante se preocupar com a abstração?
2. O que é encapsulamento e qual sua importância em Orientação a objetos?

