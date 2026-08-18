# Respostas — Evolução das Principais Linguagens de Programação (Cap. 2, Sebesta)

Respostas autorais para 10 das 20 questões da lista (5 do primeiro bloco, 5 do segundo), com base na leitura do capítulo 2 do livro.

---

## Questão 1

**A genealogia das linguagens não é uma escada de progresso.**
Objetivos: obj01, obj05 · Referência: Sebesta, cap. 2, p.50 (l.20-31) e p.51 (Figura 2.1)

Essa frase incomoda quem está acostumado a pensar em tecnologia como uma linha reta, em que cada versão "vence" a anterior. A árvore genealógica do capítulo mostra outra coisa: Fortran, ALGOL e Lisp nascem quase juntas, no fim dos anos 1950, e nenhuma delas apaga a outra — elas simplesmente seguem em ramos paralelos, porque atendem a necessidades diferentes. Fortran cresce no eixo do cálculo numérico, Lisp no eixo simbólico/IA, e décadas depois ainda coexistem.

Dois fatores explicam por que a influência não implica substituição. O primeiro é o domínio de aplicação: uma linguagem que resolve bem um problema específico (COBOL para processamento comercial, por exemplo) continua sendo usada mesmo quando surgem linguagens "mais modernas", porque o domínio que a originou não desapareceu. O segundo é o contexto institucional de cada projeto: Fortran nasce dentro da IBM, pressionada por um mercado de hardware caro que precisava provar que compilar valia a pena; Ada nasce de uma exigência do Departamento de Defesa dos EUA por confiabilidade em sistemas críticos. Como os contextos são diferentes, as linguagens absorvem ideias umas das outras (Ada bebe de Pascal e ALGOL, por exemplo) sem que isso signifique que uma projeta a extinção da outra.

---

## Questão 3

**Short Code, Speedcoding e os sistemas A-0/A-1/A-2.**
Objetivos: obj01, obj02 · Referência: Sebesta, cap. 2, p.54-55

As três soluções atacam o mesmo problema — programar em código de máquina era lento e cheio de erros — mas de maneiras bem diferentes entre si.

Short Code (Mauchly, 1949, para o BINAC/UNIVAC I) era, na prática, um interpretador puro: expressões matemáticas eram codificadas em pares de bytes e avaliadas diretamente pela máquina, sem gerar código objeto. Funcionava, mas custava caro em desempenho — cerca de 50 vezes mais lento que rodar em código de máquina puro.

Speedcoding (Backus, 1954, para o IBM 701) também era um interpretador, só que mais ambicioso: transformava o 701 em uma espécie de calculadora virtual de ponto flutuante com três endereços, incluindo operações como raiz quadrada e logaritmo que o hardware não tinha nativamente. O ganho de produtividade era real — Backus dizia que tarefas de duas semanas em código de máquina caíam para poucas horas —, mas o preço era memória: sobravam apenas 700 palavras utilizáveis depois de carregar o interpretador.

Já os sistemas A-0, A-1 e A-2, da equipe de Grace Hopper na UNIVAC (1951-1953), funcionavam de um jeito mais parecido com um "linker com macros": expandiam um pseudocódigo em sub-rotinas de código de máquina já prontas, em vez de interpretar linha a linha.

Chamá-los simplesmente de "compiladores modernos" seria impreciso porque nenhum deles faz o que esperamos de um compilador atual: análise sintática completa de uma linguagem de alto nível, geração de código otimizado e tradução (não interpretação) para código de máquina. Short Code e Speedcoding são interpretadores; os sistemas A-x são, na melhor das hipóteses, expansores de macro. O termo "compilador" ali aparece sempre entre aspas no próprio texto do Sebesta, e por um bom motivo.

---

## Questão 5

**Lisp e Fortran: domínios, dados e estilo de computação.**
Objetivos: obj02, obj03 · Referência: Sebesta, cap. 2, p.56-58 (Fortran) e p.62-64 (Lisp)

Fortran nasce dentro da IBM para resolver um problema concreto: fazer o IBM 704 rodar cálculo científico sem sacrificar desempenho. Por isso sua estrutura de dados básica são escalares e vetores numéricos, e seu estilo é fortemente imperativo — sentenças de atribuição, laços `Do`, controle de fluxo baseado nas próprias instruções do 704. Programar em Fortran é dizer ao computador, passo a passo, como calcular algo.

Lisp nasce em outro planeta: o laboratório de McCarthy, voltado para inteligência artificial, onde o problema era manipular símbolos e listas, não números. A resposta foi radical — só existem dois tipos de estrutura de dados, átomos e listas, e código e dado compartilham a mesma representação. O estilo deixa de ser "sequência de comandos" e passa a ser funcional: computação é aplicação de função, frequentemente via recursão, sem depender de atribuição destrutiva de variáveis.

A diferença mais reveladora é essa simetria entre código e dado em Lisp, que não existe em Fortran — é o que depois vai permitir coisas como um programa Lisp escrever ou modificar outro programa Lisp, algo essencial para IA simbólica e impensável no modelo imperativo-numérico de Fortran.

---

## Questão 7

**COBOL: domínio comercial, legibilidade, registros e FLOW-MATIC.**
Objetivos: obj01, obj02, obj04 · Referência: Sebesta, cap. 2, p.72-74

COBOL foi desenhada para um público que não era formado por cientistas ou engenheiros, e sim por gerentes e analistas de negócio que precisavam, no mínimo, conseguir ler o código para auditá-lo. Isso explica a sintaxe extensa e quase em inglês corrido: não é um acidente estético, é uma resposta direta ao público-alvo.

O domínio — processamento de registros comerciais, folha de pagamento, faturamento — também molda a linguagem por dentro. Diferente de Fortran, cujo tipo de dado central é o número, COBOL organiza tudo em torno de registros hierárquicos, porque é assim que dados de negócio (um cliente com vários pedidos, um pedido com vários itens) naturalmente se estruturam.

E nada disso surge do zero: COBOL 60 é, em boa parte, uma elaboração de FLOW-MATIC, a linguagem que Grace Hopper já vinha desenvolvendo desde 1953 especificamente para aplicações comerciais na UNIVAC. A verbosidade legível, a ideia de comandos que soam como instruções em português (ou inglês), e até estruturas de dados já estavam ali antes de existir o nome COBOL — o comitê de 1959 herdou e formalizou muito dessa base.

---

## Questão 9

**APL, SNOBOL e SIMULA 67: focos distintos.**
Objetivos: obj02, obj03 · Referência: Sebesta, cap. 2, p.85-86

As três seguem direções que quase não se cruzam.

APL, criada por Kenneth Iverson por volta de 1960, nasceu originalmente não para ser implementada, mas como uma notação para descrever arquiteturas de computadores. Isso explica seu traço mais marcante: um conjunto enorme de operadores muito poderosos, que permitem expressar em uma linha o que outras linguagens fariam em várias — ao custo de ficar difícil de ler. Sua contribuição duradoura é menos sobre adoção em massa e mais sobre ter mostrado até onde a expressividade de operadores pode ir; ecoa hoje em linguagens como J.

SNOBOL foca em processamento de texto: seu núcleo é uma coleção de operações de casamento de padrões em strings, pensada para manipular dados textuais de forma muito mais direta do que Fortran ou COBOL jamais fizeram. Sua herança mais visível está em linguagens de correspondência de padrões que vieram depois, como o Icon.

SIMULA 67 é a mais silenciosamente influente das três. Construída como extensão de ALGOL 60, ela introduz classes e corrotinas para simular sistemas do mundo real — e é exatamente essa ideia de agrupar dados e comportamento em uma "classe" que, décadas depois, vira a espinha dorsal da programação orientada a objetos em Smalltalk, C++ e Java. Nenhuma linguagem nesta lista foi um sucesso comercial, mas SIMULA 67 é, sem exagero, a avó da OOP.

---

## Questão 12

**Base Prolog: dois fatos, uma regra, uma consulta.**
Objetivos: obj02, obj03 · Referência: Sebesta, cap. 2, p.93

Uma base bem simples, em linguagem natural, poderia ser assim:

- Fato 1: bob é pai de darcie.
- Fato 2: darcie é mãe de ana.
- Regra: X é avô de Y se X é pai de algum Z, e Z é mãe de Y.
- Consulta: bob é avô de ana?

O que faz isso ser programação lógica, e não apenas um banco de dados com um `SELECT`, é o caminho que o sistema percorre para responder à consulta. Em um banco de dados tradicional, "avô" teria que estar armazenado como um fato explícito, ou alguém teria escrito um algoritmo passo a passo para calculá-lo. Em Prolog, ninguém disse ao computador *como* chegar à resposta — só descrevemos a relação lógica entre pai, mãe e avô, e deixamos que o motor de inferência do Prolog faça o trabalho de unificação e busca (resolução) para encadear os fatos através da regra até provar (ou refutar) a consulta.

Ou seja: o programador declara relações e deixa a estratégia de busca por conta do interpretador. Isso é o oposto de um `SELECT` num banco relacional, que apenas recupera o que já está lá — em Prolog, "avô" é uma verdade derivada, não armazenada.

---

## Questão 14

**Objetos em Smalltalk, C++ e Java.**
Objetivos: obj02, obj03 · Referência: Sebesta, cap. 2, p.98-99 (Smalltalk), p.103-105 (C++/Java)

Smalltalk leva a ideia de objeto ao extremo: absolutamente tudo — de um inteiro simples a um sistema inteiro — é um objeto, e toda computação acontece por um único mecanismo, o envio de mensagens entre objetos. Não existe "modo procedural de escape"; é OOP pura, sem mistura.

C++ escolhe outro caminho, condicionado por uma decisão de origem: manter compatibilidade retroativa com C. Isso trouxe adoção mais fácil (programadores de C podiam migrar aos poucos), mas também obrigou a linguagem a carregar os riscos do C — ponteiros, gerência manual de memória, coerções implícitas perigosas. C++ vira, assim, uma linguagem híbrida: você pode escrever OOP puro ou continuar programando quase como em C dentro do mesmo arquivo.

Java parte de C++, mas inverte a lógica: em vez de preservar compatibilidade com C, os projetistas retiraram deliberadamente os recursos mais inseguros (parte das coerções automáticas, aritmética de ponteiros livre) para priorizar confiabilidade. A estratégia de portabilidade segue a mesma lógica de "simplicidade acima de tudo": Java compila para um formato intermediário (bytecode) executado por uma máquina virtual (JVM) em qualquer plataforma que a implemente. O preço inicial foi desempenho — a primeira JVM era pelo menos dez vezes mais lenta que código C equivalente —, resolvido depois com compiladores just-in-time. É um trade-off clássico: abrir mão de velocidade bruta em troca de "escreva uma vez, rode em qualquer lugar", o que combinou perfeitamente com o momento em que a Web pedia código que rodasse em navegadores diferentes.

---

## Questão 16

**Perl, JavaScript, PHP, Python, Ruby e Lua em três eixos.**
Objetivos: obj01, obj03 · Referência: Sebesta, cap. 2, p.107-113

É tentador jogar essas seis linguagens no mesmo saco só porque todas são "de scripting", mas olhando por domínio inicial, estruturas de dados e estratégia de implementação, elas se separam bastante.

**Domínio inicial**: Perl nasceu como ferramenta de administração de sistemas UNIX (combinando `sh` e `awk`), só depois virou popular para CGI na Web. JavaScript nasceu especificamente para rodar dentro do navegador e manipular páginas HTML. PHP nasceu para gerar HTML dinamicamente no lado servidor. Python nasceu como linguagem de propósito geral, sem foco único em Web. Ruby nasceu da insatisfação pessoal de Matsumoto com Perl e Python, também de propósito geral. Lua nasceu para ser embutida dentro de outras aplicações (como motores de jogos), não para rodar sozinha.

**Estruturas de dados**: Perl se destaca pelos vetores associativos ("hashes"); JavaScript usa objetos com protótipos (sem herança clássica) e vetores de tamanho dinâmico; PHP mistura vetor indexado e associativo numa única estrutura; Python tem listas e dicionários como cidadãos de primeira classe, além de suporte real a classes; Ruby não tem "estruturas soltas" — até números são objetos, tudo passa por métodos; Lua usa uma única estrutura, a *table*, para simular vetores, registros e até objetos.

**Estratégia de implementação**: Perl e PHP são interpretados no servidor (PHP inclusive gera HTML como saída); JavaScript é interpretado embutido no navegador; Python e Ruby têm interpretadores extensíveis por C, pensados para uso geral; Lua foi desenhada desde o início para ser um interpretador leve, embarcável dentro do código C de outra aplicação — bem diferente de rodar como programa autônomo.

O ponto chave: "scripting" descreve muito mais o estilo (interpretado, tipagem dinâmica) do que o propósito. O propósito de cada uma vem do problema que motivou sua criação, e esses problemas eram bem diferentes entre si.

---

## Questão 18

**XSLT e JSP: entrada, processamento e saída.**
Objetivos: obj02, obj03 · Referência: Sebesta, cap. 2, p.116-118

XSLT recebe dois documentos XML como entrada: um com os dados propriamente ditos e outro que é a folha de estilo XSLT, contendo *templates* — padrões que casam com nós específicos da árvore XML de dados. O processamento consiste em varrer o documento de entrada aplicando, a cada nó encontrado, as instruções de transformação associadas ao template correspondente; a linguagem ainda oferece construções de mais baixo nível, como laços do tipo `<for-each>`, para casos que o casamento de padrões sozinho não resolve. A saída é um novo documento — pode ser outro XML, HTML ou texto puro.

JSP segue uma lógica diferente: a "entrada" é uma página que mistura HTML estático com trechos de código Java, apoiada em servlets (classes Java que rodam no servidor). O processamento acontece em duas etapas — a JSP é primeiro traduzida para um servlet Java e depois executada a cada requisição. A saída é HTML gerado dinamicamente, montado conforme a lógica Java embutida na página é executada.

Ambas merecem o rótulo de "linguagens híbridas de marcação-programação" pelo mesmo motivo, ainda que por caminhos opostos: XSLT parte de uma linguagem de marcação (XML) e incorpora construções de programação (casamento de padrões, laços) para ganhar poder de transformação; JSP parte do lado oposto, incorporando uma linguagem de programação completa (Java) dentro de um documento de marcação (HTML). O resultado, nos dois casos, é um documento que não é puramente declarativo nem puramente imperativo.

---

## Questão 20

**Estudo de caso: cálculo científico, regras declarativas, Web interativa e firmware restrito.**
Objetivos: obj01, obj02, obj03, obj04, obj05 · Referência: Sebesta, cap. 2, p.56-118 (síntese)

Para cálculo científico, a família Fortran ainda é a escolha natural. Desde 1957 ela foi desenhada especificamente em torno de desempenho numérico — décadas de otimização de compiladores voltados a operações de ponto flutuante e vetores dão a ela uma vantagem que linguagens generalistas não recuperam facilmente, mesmo hoje em computação de alto desempenho.

Para regras declarativas, a escolha é Prolog. É literalmente o que a linguagem foi criada para fazer em 1972: representar fatos e regras e deixar que o motor de resolução busque as respostas, em vez de o programador descrever o algoritmo passo a passo. Sistemas especialistas e motores de regras de negócio se beneficiam exatamente dessa separação entre "o que é verdade" e "como descobrir".

Para uma aplicação Web interativa, JavaScript é incontornável no lado cliente — é a única linguagem embutida em todo navegador desde meados dos anos 1990, e sua capacidade de manipular a árvore de documento dinamicamente é o que torna uma página "interativa" em vez de estática. Historicamente ela nasceu junto com essa necessidade, não foi adaptada depois.

Para firmware restrito, C continua sendo a referência. Criada por Ritchie em 1972 justamente como linguagem de sistemas portátil, próxima do hardware e sem runtime pesado, ela foi usada para escrever o próprio UNIX — e seguiu como padrão de fato em ambientes embarcados, onde memória e previsibilidade importam mais do que conveniência de escrita.

Dois trade-offs relevantes: primeiro, a mesma proximidade com o hardware que faz do C a escolha certa em firmware é o que a torna arriscada — a gerência manual de memória custa segurança que uma linguagem como Java, por exemplo, resolveria à custa de um runtime que o firmware simplesmente não tem espaço para carregar. Segundo, a especialização de Fortran em cálculo numérico é uma faca de dois gumes: excelente no seu nicho, mas sem suporte natural para as interfaces interativas que uma aplicação Web exige — não à toa, ninguém propõe Fortran para o front-end de um site.
