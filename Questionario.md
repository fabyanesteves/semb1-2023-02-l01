# Questionário Sistemas Embarcados I

## 1. Explique brevemente o que é compilação cruzada (***cross-compiling***) e para que ela serve.
A compilação cruzada é quando um programa é compilado em alguma plataforma ou sistema operacional diferente da qual ele seria executado; Ela serve para desenvolver softwares para diferentes plataformas com recursos diferentes da qual a plataforma o desenvolvedor está utilizando.

## 2. O que é um código de inicialização ou ***startup*** e qual sua finalidade?
O código de inicialização são instruções que serão executadas quando o sistema inicia ou o programa é executado. Com a finalidade de preparar o ambiente o qual o programa principal será executado. 

## 3. Sobre o utilitário **make** e o arquivo **Makefile responda**:

#### (a) Explique com suas palavras o que é e para que serve o **Makefile**.
Makefile é um arquivo de texto que possui as instruções para automatizar o processo de compilação, é ele que decide as "regras" para que o programa seja compilado. 

#### (b) Descreva brevemente o processo realizado pelo utilitário **make** para compilar um programa.
O make verifica primeiramente as dependências de cada arquivo fonte, mas se precisar, ela recompila os arquivos que foram modificados.

#### (c) Qual é a sintaxe utilizada para criar um novo **target**?
targets: prerequisites                                                                                                         recipe                                                                                    

#### (d) Como são definidas as dependências de um **target**, para que elas são utilizadas?
As dependências são definidas após o nome TARGET. Elas são utilizadas para representar arquivos ou outros targets que o atual depende para ser feito; Então o make usa essas dependências para definir a ordem de compilação do programa.

#### (e) O que são as regras do **Makefile**, qual a diferença entre regras implícitas e explícitas?
As regras do make-file são instruções de como o programa deve ser compilado. Regras implícitas são criadas pelo próprio MAKE. Regras explícitas são criadas pelo desenvolvedor.
## 4. Sobre a arquitetura **ARM Cortex-M** responda:

### (a) Explique o conjunto de instruções ***Thumb*** e suas principais vantagens na arquitetura ARM. Como o conjunto de instruções ***Thumb*** opera em conjunto com o conjunto de instruções ARM?
É a versão compactada do conjunto de instruções ARM original. Sua principal vantagem é utilizar apenas 16 bits para economizar espaço, melhorando a eficiência da memoria. O thumb opera em conjunto com o ARM original, aproveitando as vantagens de ambos conjuntos de instruções.

### (b) Explique as diferenças entre as arquiteturas ***ARM Load/Store*** e ***Register/Register***.
A arquitetura ARM Load/Store acessa a memoria das operações de processamento pois ela as separa explicitamente; Utilizando do Load e Store para acessar a memoria. A arquitetura Register/Register as operações para acesso de memoria são em conjunto das operações de processamento; A qual utiliza registradores de dados para acesso direto da memoria.

### (c) Os processadores **ARM Cortex-M** oferecem diversos recursos que podem ser explorados por sistemas baseados em **RTOS** (***Real Time Operating Systems***). Por exemplo, a separação da execução do código em níveis de acesso e diferentes modos de operação. Explique detalhadamente como funciona os níveis de acesso de execução de código e os modos de operação nos processadores **ARM Cortex-M**.
Existe o Privileged Mode, o qual deixa o software com acesso total as instruções do processador, tendo total controle do sistema quando executado nesse modo. O outro acesso é o Unprivileged Mode, o qual restringe o software a algumas instruções, e devido a isso, não pode executar certos comandos do sistema. O modo de operação Thread Mode é utilizado em execuções normais de tasks do usuário ou sistema, onde exceções e interrupções são tratados de acordo com a prioridade. O modo Handler Mode é ativado quando uma interrupção ocorre dando prioridade ao tratamento desses enventos comparados com a execução normal.  

### (d) Explique como os processadores ARM tratam as exceções e as interrupções. Quais são os diferentes tipos de exceção e como elas são priorizadas? Descreva a estratégia de **group priority** e **sub-priority** presente nesse processo.
As interrupções são tratadas pelo sistema de prioridade em níveis de exceção e grupos de prioridade. Existem diversos tipos, como reset, IRQ, FIQ, SVC, onde cada um tem sua prioridade. Serão criados grupos com as interrupções em níveis de prioridade, e dentro desses grupos, prioridades adicionais são criadas. O grupo é denomindado de Group Priority e as propriedades adicionais são as Sub-Priority.

### (e) Qual a diferença entre os registradores **CPSR** (***Current Program Status Register***) e **SPSR** (***Saved Program Status Register***)?
O SPSR é temporário e salva o estado do processador antes de ser alterado por uma execução ou interrupção. Já o CPSR salva o estado atual do processador durante o processo de execução do programa.

### (f) Qual a finalidade do **LR** (***Link Register***)?
O Link Register armazena o endereço de retorno de uma função, a qual permite que o programa volte a instrução de chamada quando concluir a sub-rotina ou função. 

### (g) Qual o propósito do Program Status Register (PSR) nos processadores ARM?
O PSR armazena informações sobre o estado atual do processador e as informações importantes para o controle e o gerenciamento do mesmo. 

### (h) O que é a tabela de vetores de interrupção?
A tabela de vetores é responsável por mapear os endereços de entrada de todas as interrupções suportadas pelo processador. 

### (i) Qual a finalidade do NVIC (**Nested Vectored Interrupt Controller**) nos microcontroladores ARM e como ele pode ser utilizado em aplicações de tempo real?

### (j) Em modo de execução normal, o Cortex-M pode fazer uma chamada de função usando a instrução **BL**, que muda o **PC** para o endereço de destino e salva o ponto de execução atual no registador **LR**. Ao final da função, é possível recuperar esse contexto usando uma instrução **BX LR**, por exemplo, que atualiza o **PC** para o ponto anterior. No entanto, quando acontece uma interrupção, o **LR** é preenchido com um valor completamente  diferente,  chamado  de  **EXC_RETURN**.  Explique  o  funcionamento  desse  mecanismo  e especifique como o **Cortex-M** consegue fazer o retorno da interrupção. 

### (k) Qual  a  diferença  no  salvamento  de  contexto,  durante  a  chegada  de  uma  interrupção,  entre  os processadores Cortex-M3 e Cortex M4F (com ponto flutuante)? Descreva em termos de tempo e também de uso da pilha. Explique também o que é ***lazy stack*** e como ele é configurado. 


## Referências

### Básicas

[1] [STM32F411xC Datasheet](https://www.st.com/resource/en/datasheet/stm32f411ce.pdf)

[2] [RM0383 Reference Manual](https://www.st.com/resource/en/reference_manual/rm0383-stm32f411xce-advanced-armbased-32bit-mcus-stmicroelectronics.pdf)

[3] [Using the GNU Compiler Collection (GCC)](https://gcc.gnu.org/onlinedocs/gcc/index.html)

[4] [GNU Make](https://www.gnu.org/software/make/manual/html_node/index.html)

### Vídeos Microsoft Teams

[5] [05 - Introdução à arquitetura de computadores](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[6] [06 - Arquitetura Cortex-M Parte 1/2](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[7] [07 - Arquitetura Cortex-M Parte 2/2](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[8] [08 - Microcontroladores STM32](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[9] [10 - Introdução à arquitetura de computadores](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

### Material Suplementar

[5] [A General Overview of What Happens Before main()](https://embeddedartistry.com/blog/2019/04/08/a-general-overview-of-what-happens-before-main/)
 
[6] [Bare metal embedded lecture-1: Build process](https://youtu.be/qWqlkCLmZoE?si=mn5yDnJYudQ1PpZH)
 
[7] [Bare metal embedded lecture-2: Makefile and analyzing relocatable obj file](https://youtu.be/Bsq6P1B8JqI?si=yuNLPj3JQ-2IT1yo)
 
[8] [Bare metal embedded lecture-3: Writing MCU startup file from scratch](https://youtu.be/2Hm8eEHsgls?si=c27MpZ47ApiMSwHR)
 
[9] [Lecture 15: Booting Process](https://youtu.be/3brOzLJmeek?si=MsHRUEJP8zofjwJQ)
