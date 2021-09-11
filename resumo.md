---
title:
- Resumo em controle adaptativo robusto: aspectos teóricos
author:
- Levy G. S. Galvão
numbersections: true
output:
    pdf_document:
        template: NULL
---

<!-- pandoc clp.md -o out.pdf -->

# Parte 1
Limitações no projeto tradicional de controladores:
- Parâmetros desconhecidos ou conhecidos com incertezas;
- Parâmetros da planta variantes com o tempo;
- Planta trabalhada é uma aproixmação para um determinado ponto de operação;

O **controle adaptativo** trata do controle de plantas com parâmetros desconhcidos, parcialmente conhecidos ou variantes no tempo.

# Parte 2

A ideia do **controle adaptativo** gira em torno da ideia de que a entrada e a saída da planta possuem informações sobre suas características e o controlador pode aprender o comportamento da planta a partir delas, permitindo a correção de seus parâmetros.

As abordagens clássicas são:
- Controle adaptativo por modelo de referência (MRAC);
- Controle adaptativo por posicionamento de polos (APPC);

1. Controle adaptativo por modelo de referência (MRAC):
    - Um *modelo de referência* especifica os requisitos de desempenho da planta em malha fechada;
    - A condição de *matching* é obtida quando quando a planta em malha fechada se comporta como o modelo de referência;
    - O *matching* é alcançado quando há o cancelamento dos zeros da função de transferência (FT) da planta por polos do controlador, fazendo com que o controlador introduza os zeros do modelo de referência e a mudança dos polos da planta em malha fechada para os polos do modelo de referência;
    - A restrição é que a planta deve ser de fase mínima (zeros no SPE), pois o cancelamento perfeito de polos e zeros é impossível;
    - Implementado na abordagem direta: os parâmetros do controlador são estiamdos diretamente;
    - Necessidade de obtenção de um modelo parametrizado para a planta em função dos parâmetros corretos do controlador;

2. Controle adaptativo por posicionamento de polos (APPC):
    - Os requisitos de desempenho são especificados pelo posicionamento dos polos da planta em malha fechada em locais desejados;
    - Implementado na abordagem indireta: os parâmetros da plnata são estimados e, a partir deles, os parâmetros do controlador são calculados;

**Princípio de equivalência à certeza**: o projeto do modelo do controlador trata as estiamtivas dos parâmetros do controlador como  se elas fossem os verdadeiros parâmetros. Isso se justifica, pois se as estimativas dos parâmetros do controlador covnergem para os seus valores verdadeiros, o desempenho do controlador adaptativo tende ao que seria obtido para o controlador projeto considerando parâmetros da planta conhecidos.

**Controle adaptativo robusto**: controle adapatativo que preserva as propriedades do sistema de controle na presença de pertubações, ruídos e/ou dinâmica não modelada da planta (dinâmica rápida de natureza parasita que é desprezada na modelagem da planta).

# Parte 3

**MRAC**:
- Parâmetros da planta e controlador desconhecidos;
- Necessidade de estimar os parâmetros do controlador de forma direta para o cálculo do sinal de controle;

**Hipóteses**:
- Modelo de referência estritamente real positivo (ERP), sendo este estável ($M(s)$ estável) e que sua parte real seja positiva ($\Re[M(j\omega)]$>0).
- Constantes proporcionais da planta e do modelo de referência devem ter o mesmo sinal;

**Teoria da estabilidade de Lyapunov**: os termos de energia em um sistema muitas vezes assumem a forma de $\frac{1}{2}kx^2$.

**Funções definidas (semi-definidas) positivas (negativas)**:
- $V(x)$ é definida POSITIVA se $V(x)>0$ para $x \neq 0$ e $V(0)=0$. Nomenclatura: $V(x)>0$;
- $V(x)$ é semi-definida POSITIVA se $V(x) \geq 0$ para $x \neq 0$ e $V(0)=0$. Nomenclatura: $V(x) \geq 0$;
- $V(x)$ é definida NEGATIVA se $V(x)<0$ para $x \neq 0$ e $V(0)=0$. Nomenclatura: $V(x)<0$;
- $V(x)$ é semi-definida NEGATIVA se $V(x) \leq 0$ para $x \neq 0$ e $V(0)=0$. Nomenclatura: $V(x) \leq 0$;

**Estado de equilíbrio**: O estado de equilíbrio no topo de uma senoide é instável, enquanto que em seu vale é estável.

**Estabilidade e estabilidade assintótica**:

**Teoremas de Lyapunov**:
- Se para um sistema existe uma função definida positiva e continuamente diferenciável, tal que sua derivada em qualquer conto é uma função semi-definida negativa, então a origem é um estado de equilíbrio;
- Porém se a derivada for uma função definida negativa, o estado de equilíbrio é assintoticamente estável;

**Aplicação da teoria de Lyapunov em controle adaptativo**:
1. Para o erro da planta com o modelo de referência e parâmetros do controladores serem estáveis, significa que estes devem ser uniformemente limitados (UL);
2. Para uma referência estável e um modelo de referência estável, implica que este será UL;
3. Como o erro e o modelo de referência são UL, a planta também será UL;
4. Como o erro, planta e referência são UL e a variação dos parâmetros depende deles, então estes também são UL;
5. O mesmo vale para a variação do erro;
6. Como $V$ é uma função definida positiva e tem mínimo nulo e sua derivada é uma função semi-definida negativa, então seu valor final é finito;
7. A integral do quadrado do erro de zero a infinito é um valor finito;
8. Pelo lema de Barbalat, o erro tende a zero e, consequentemente, a variação dos parâmetros tende a cessar.

A saída da planta tende a acompanhar o modelo de referência pois o erro de saída tende a zero e a adaptação dos parâmetros tende a parar. Assim não há garantia de que os erros paramétricas tendam a zero.

# Parte 4

**Exemplos de Rohrs**: estes mostram que com as leis de adaptação integrais permitem desempenho satisfatório para a planta nominal, porem o desmeepnho é deteriorado na presença de dinâmica não modelada, interferências externas ou ruídos, podendo até instabilizar a planta.

**Causas de instabilização em sistemas adaptativos**:
1. Ausência de uma referência persistentemente excitante:
    - Permite a convergência dos parâmetros do ssitema nominal;
    - Previne o desvio dos parâmetros devido a dinâmica não modelada e distúrbios (ou ruídos) externos;
2. Presença de sinais com alta frequência e com grande amplitude originários de referências persistentemente excitantes ou de distúrbios (ou ruídos) externos:
    - A interação dos sinais com alta frequência com os modos da dinâmica não modelada pode levar a um fenômeno semelhante à ressonância.
3. Utilização de referência constante e com grande amplitude e de um algoritmo de adaptação não normalizado na presença de dinâmica não modelada.

**Sinal persistentemente excitante (sinal P.E.)**: este permite que quando utilizado em uma dada planta garanta que os parâmetros adaptativos tendam aos valores corretos, pois este é um sinal de baixa amplitude e com banda de frequência próxima da frequência de corte da planta (uma oitava abaixo ou acima) para que permita excitar todos os modos de excitação da planta.

**Busca de robustez em sistemas adaptativos**: sistemas exponencialmente estáveis podem tolerar distúrbios e dinâmica não modelada dentro de certos limites. Essa propriedade de estabilidade exponencial é presente quando no transitório encontram-se termos na forma de uma exponencial com decaimento.

1. Primeira estratégia - utilização de um sinal de referência P.E.:
    - A utilização de uma referência P.E. garante que os parâmetros do controlador convirjam para os ideais;
    - Porém nem todos os sistemas suportam oscilações;
    - Assim deve-se buscar modificações nas leis de adaptação originais para preservar a estabilidade;
    - As ideias podem ser limitar os parâmetros do controaldor ou neutralizar os desvios paramétricos da eleminação da ação integral nas leis de adaptação;
2. Segunda estratégia - zona morta:
    - Parar o ajuste dos parâmetros do controlador quando a excitação for insuficiente para distinguir entre os sinais de referência e saída e o ruído;
3. Terceira estratégia - limitação dos parâmetros adaptativos:
    - Confinar os parâmetros em uma bola do espaço paramétrico, evitando cessar o ajuste dos parâmetros;
4. Quarta estratégia - normalização:
    - A normalização evita o crescimento do módulo dos parâmetros do controlador, evitando que o sinal de controle cresça em demasia;
5. Quinta estratégia - modificação sigma com fator de esquecimento:
    - O fator de esquecimento permite que informaçõe mais recentes possuam mais importância que informações mais antigas;
    - Um problema atrelado à essa estratégia é o fenômeno de "bursting";
    - O "bursting" consiste em oscilações intermitentes e de grande amplitude intercaladas e de comportamento aparentemente estável;
6. Sexta estratégia - modificação sigma com normalização:
    - Esta estratégia complementa a anterior para evitar o fenômeno de "bursting"
7. Sétima estratégia - projeção:
    - A projeção evita o crescimento do módulos dos parâmetros do controlador, porém diferente do caso da normalização que os limita de acordo com os sinais de referência e de saída da planta, este utiliza um fator constante de limitação;

Em geral essas técnicas de controle adaptativo robusto apresentam transitórios lentos e oscilatórios.

# Parte 5


# Parte 6
# Parte 7
# Parte 8
# Parte 9
# Parte 10