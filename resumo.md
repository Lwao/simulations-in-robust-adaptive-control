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

**Sistemas com estrutura variável**: sistemas cuja estrutura pode ser alterada por dispositivos de chaveamento.

Para alcançar uma reta $s(x)=0$, deve-se ter $s(x)\cdot \dot{s}(x)<0$, isso é garantido por:
- $s(x)>0$ e $\dot{s}(x)<0$, ou seja, a função está acima da reta e decresce para se aproximar;
- $s(x)<0$ e $\dot{s}(x)>0$, ou seja, a função está abaixo da reta e cresce para se aproximar;

Uma trajetória que alcança $s(x)=0$ não sai mais dela (condição de invariância), fazendo com que a trajetória seja forçada a deslizar sobre a reta, apresentando um modo deslizante ("sliding mode") sobre esta superfície.

*Deslizamento ideal*: frequência de chaveamento infinita. Há uma redução na ordem da dinâmica do sistema.

*Deslizamento real*: frequência de chaveamento elevada, mas finita. O sinal de controle apresentará um chaveamento com frequência elevada,a carretando o fenômeno de "chattering".

Estratégias de simplificação podem ser aplicadas para reduzir o número de relés, gerando uma lei compacta, mas de mesma robustez.

**Controle equivalente**: é o valor obtido para o sinal de referência durante o deslizamento e é uma valor contínuo que mantém a trajetória sobre a reta de deslizamento na ausência de dinâmica não modela e pertubações.

**Obtenção prática do controle equivalente**: pode ser obtido como o valor médio do sinal de controle através da passagem por um filtro passa-baixa com frequência de corte suficientemente alta (filtro de valor médio) na ausência de dinâmica não modelada e pertubações. 

OBS: O corte do filtro deve ser maior que o corte da planta, mas menor que a frequência de chaveamento.

**Solução de Filippov**: ajuste por coeficientes complementares para que a curva seja tangente à trajetória no deslizamento ideal.

**Problemas relacionados**: 
- Necessidade de medição das variáveis de estado;
- Fenômeno de "chattering";


# Parte 6

8. Oitava estratégia - controle por modelo de referência e estrutura vairável (VS-MRAC):
    - Obtenção de robustez com excelente desempenho transitório;
    - Ao avaliar a estabilidade pela teoria de Lyapunov, considera-se substituir as leis integrais de adaptação por leis chaveadas e obter um modo deslizante ao entorno do ponto de erro nulo;
    - Condição de deslizamento: $e_0 \dot{e}_0 < 0$;
    - O estado de equilíbrio $e_0=0$ é assintoticamente estável e $e_0$ é UL;
    - A superfície de deslizamento $e_0=0$ é alcançada em tempo finito;
    - Ao atingir o deslizamento, o erro se torna nulo e, consequentemente a variação do erro também será nula, tornando o sinal de controle igual ao sinal de controla para a condição de "matching";

# Parte 7

**Simplificações do VS-MRAC**:
- VS-MRAC compacto: uso de um relé com amplitude variável;
- VS-MRAC a relé: uso de um relé com amplitude constante;
- Utilização de um controle nominal (redução na amplitude dos relés): antes a ampltiude dos relés deveria ser maior que os parâmetros ideais do controlador, causando maior sinal de controle, porém com esse ajuste a amplitude dos relés pode ser reduzida;
- Relação entre MRAC e VS-MRAC:
  - Lei para o MRAC com modificação sigma (termo de esquecimento) e uma normalização (termo de aprendizagem);
  - A combinação garante combinar o melhor das duas técnicas de controle adaptativo robusto:
    - MRAC com transitório lento e oscilatório, mas o controle é suave em regime permanente;
    - VS-MRAC com transitório rápido e pouco osiclatório, mas sinal de controle chaveado em alta frequência ("chattering") em regime permanente;
    - Para $\mu=0$, tem-se a lei para o VS-MRAC;
    - Para $\mu \Rightarrow 0$, tem-se o caso limite do MRAC quando tanto o processo de aprendizagem quanto o processo de esquecimento são instantâneos;
- DMARC (controle adapatativo em modo dual):
  - Para um erro grande, tem-se $\mu \Rightarrow 0$, consequentemente o comportamento do VS-MRAC;
  - Para um erro pequeno, tem-se $\mu \Rightarrow 1$, consequentemente o comportamento do MRAC com modificação sigma e normalização;
  - $L$ grande aumenta a influência do MRAC e $L$ pequeno aumenta a influência do VS-MRAC;

**Redução do chattering**:
- DMARC;
- Utilização de relé modificado (com região linear):
  - Um relé puro possui transições abruptas (chaveamento com frequência tendendo ao infinito durante o deslizamento);
  - Implementação de região linear durante a transição para que a frequência de chaveamento diminua com a diminuição a inclinação da curva de transição;
  - Diminuição da inclinação pode acarretar:
    - possibilidade erro de saída $e_0$ maior;
    - possibilidade de instabilização na região linear;
    - maior robustez em relação a atrasos de chaveamento do relé;
    - possibilidade de evitar a excitação da dinâmica não modelada da planta;
- Introdução de um compensador PI com saturação:
  - A região linear leve ao surgimento de erro na saída da planta em regime permanente;
  - Quando a referência ou o distúrbio são do tipo degrau, o erro em regime pode ser compensador por um compensador PI;
  - Este evita a deterioração do comportamento transitório do sistema;
  - Sua implementação deve possuir saturação por uma técnica de "anti-reset wind-up";
- Utilização de relé com zona morta;
- Utilização de relé com histerese;
- Substituição do controle $u$ pelo controle equivalente $u_{eq}$;
- Utilização da função tangente hiperbólica;

# Parte 8

**Efeito de distúrbio na entrada da planta**: Durante o deslizamento o sinal de controle é igual ao sinal de controle para a condição de "matching" menos o valor do distúrbio, implicando que o sinal de controle anula o efeito do distúrbio.

**Efeito da dinâmica não modelada da planta**: a dinâmica parasita é muito rápida e é desprezada na modelagem da planta. Ela influencia o comportamento da planta no sentido de que o erro de saída passa a tender para um domínio residual da ordem de $\sqrt{\mu}$.

**Efeito de ruídos de medição**: o efeito de um sinal de alta frequência adicionado à entrada de um relé é o de diminuir o ganho efetivo do relé. Assim, as propriedades de invariância de um sistema com estrutura variável (manutenção da trajetória sobre a superfície de deslizamento) são bastante deterioradas pelo aumento da amplitude do sinal de alta frequência. A SOLUÇÃO é a filtragem do erro de saída, oscasionando o aumento da complexidade do algoritmo (aumentando a ordem da planta devido ao filtro).

# Parte 9

**Controle adaptativo por posicionamento de polos (APPC) ou controle auto-ajustável (STC)**: 
 - Implementado na forma indireta;
 - O APPC é constituído de uma controlador por posicionamento de polos (PPC) e um estiamdor de parâmetros;
 - Escolher o sinal de controle tal que o polo de malha fechada seja o desejado e o sinal de controle e a saída da planta sejam UL e a saída da planta rastreie o sinal de referência;

**Controle adaptativo por posicionamento de polos e estrutura variável (VS-APPC)**:
 - Escolher o sinal de controle tal que o polo de malha fechada seja o desejado e o sinal de controle e a saída da planta sejam UL e a saída da planta rastreie o sinal de referência;

# Parte 10

**Controle adaptativo por posicionamento de polos (APPC) ou controle auto-ajustável (STC)**: 
 - Implementado na forma indireta;
 - O APPC é constituído de uma controlador por posicionamento de polos (PPC) e um estiamdor de parâmetros;
 - Escolher o sinal de controle tal que o polo de malha fechada seja o desejado e o sinal de controle e a saída da planta sejam UL e a saída da planta rastreie o sinal de referência;

**Controle adaptativo por posicionamento de polos e estrutura variável (VS-APPC)**:
 - Escolher o sinal de controle tal que o polo de malha fechada seja o desejado e o sinal de controle e a saída da planta sejam UL e a saída da planta rastreie o sinal de referência;