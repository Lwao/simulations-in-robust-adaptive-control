# Resumo em controle adaptativo robusto: aspectos teóricos

## Parte 1
Limitações no projeto tradicional de controladores:
- Parâmetros desconhecidos ou conhecidos com incertezas;
- Parâmetros da planta variantes com o tempo;
- Planta trabalhada é uma aproixmação para um determinado ponto de operação;

O **controle adaptativo** trata do controle de plantas com parâmetros desconhcidos, parcialmente conhecidos ou variantes no tempo.

## Parte 2

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

**Cibtrike adaptativo robusto**: controle adapatativo que preserva as propriedades do sistema de controle na presença de pertubações, ruídos e/ou dinâmica não modelada da planta (dinâmica rápida de natureza parasita que é desprezada na modelagem da planta).

## Parte 3
## Parte 4
## Parte 5
## Parte 6
## Parte 7
## Parte 8
## Parte 9
## Parte 10