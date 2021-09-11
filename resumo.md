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
# Parte 5
# Parte 6
# Parte 7
# Parte 8
# Parte 9
# Parte 10