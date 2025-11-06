Evolução da Cultura de Testes em Projetos Java Maduros
1. Contexto Geral

Este trabalho integra um estudo sobre a evolução da cultura de testes em projetos Java de código aberto, com foco na identificação de padrões e práticas associadas à maturidade do projeto.
A pesquisa tem como base o Open Source Maturity Model (OSMM), um modelo conceitual que permite caracterizar o grau de maturidade de um projeto a partir de evidências objetivas, como qualidade, processos e governança.

O objetivo central é compreender como a qualidade e o comportamento dos testes evoluem ao longo do tempo, especialmente em repositórios que apresentam histórico consolidado e práticas contínuas de manutenção e teste.

As análises são realizadas de forma longitudinal, tomando as releases como unidades de observação, de modo a acompanhar o comportamento das métricas em diferentes estágios do ciclo de vida do software.

RQ1: Como a densidade de categorias de Test Smells evolui com a maturidade do projeto (ao longo das releases)?

RQ2: Qual a relação entre o esforço de teste e o esforço de manutenção dentro de um ciclo de release?

2. RQ1 – Evolução da Densidade de Categorias de Test Smells
2.1. Objetivo

Avaliar a evolução da qualidade dos testes em projetos Java maduros, por meio da análise da densidade de Test Smells em diferentes categorias, ao longo das releases do projeto.

A métrica de densidade permite comparar projetos e versões de diferentes tamanhos, oferecendo uma visão normalizada da proporção de más práticas de teste em relação ao número total de métodos de teste existentes.

2.2. Fundamentação

A presença de Test Smells indica potenciais fragilidades no código de teste, tais como baixa legibilidade, alta complexidade, fragilidade de asserções e dificuldade de manutenção.
Estudos como o de Peruma et al. (2020), com a ferramenta tsDetect, permitem detectar automaticamente 21 tipos distintos de smells em código de teste Java.

2.3. Metodologia

O processo metodológico adotado para esta RQ envolve:

Seleção das releases analisadas:
São consideradas apenas releases major (por exemplo, 1.0.0, 2.0.0, 3.0.0), representando marcos de evolução significativa do projeto.

Detecção automática de Test Smells:
A ferramenta tsDetect é executada sobre o diretório de testes de cada release, identificando e classificando os smells em 21 categorias, tais como:

Assertion Roulette

Magic Number Test

Exception Catching/Throwing

Ignored Test

Conditional Test Logic, entre outros.

Cálculo das métricas:
Para cada categoria de smell, é calculada a densidade com base na seguinte fórmula:

𝐷
𝑒
𝑛
𝑠
𝑖
𝑑
𝑎
𝑑
𝑒
=
𝑇
𝑜
𝑡
𝑎
𝑙
 
𝑑
𝑒
 
𝑆
𝑚
𝑒
𝑙
𝑙
𝑠
 
𝑑
𝑎
 
𝐶
𝑎
𝑡
𝑒
𝑔
𝑜
𝑟
𝑖
𝑎
𝑇
𝑜
𝑡
𝑎
𝑙
 
𝑑
𝑒
 
𝑀
𝑒
ˊ
𝑡
𝑜
𝑑
𝑜
𝑠
 
𝑑
𝑒
 
𝑇
𝑒
𝑠
𝑡
𝑒
Densidade=
TotaldeM
e
ˊ
todosdeTeste
TotaldeSmellsdaCategoria
	​


Agrupamento das densidades por tipo:
As categorias são agrupadas em quatro dimensões analíticas:

Densidade de Asserções: Testes que apresentam smells relacionados ao uso incorreto de asserções.

Densidade de Código: Más práticas relacionadas à estrutura e ao estilo do código de teste.

Densidade de Exceções: Uso inadequado de blocos try-catch ou tratamento incorreto de exceções em testes.

Densidade de Fixtures: Problemas no uso e configuração de fixtures e ambientes de teste.

Análise longitudinal:
As densidades são comparadas ao longo das releases para identificar tendências de melhora, estabilidade ou deterioração na qualidade do código de teste.

2.4. Interpretação Esperada

Com base nos resultados, espera-se verificar se a maturidade do projeto (medida segundo o OSMM) está associada à redução das densidades de Test Smells.
Projetos mais maduros tendem a apresentar menor incidência relativa de más práticas de teste, indicando uma cultura mais consolidada de qualidade e manutenção preventiva.

3. RQ2 – Relação entre Esforço de Teste e Esforço de Manutenção
3.1. Objetivo

Analisar a relação entre o esforço de teste e o esforço de manutenção ao longo de cada ciclo de release, investigando se há correlação entre o aumento de atividades de teste e a redução de retrabalho ou correções posteriores.

3.2. Fundamentação

Estudos em engenharia de software sugerem que o investimento contínuo em testes automatizados pode reduzir o custo de manutenção ao longo do tempo.
Entretanto, há casos em que o aumento do esforço de teste coincide com maior esforço de manutenção, indicando possíveis gargalos de integração, refatorações constantes ou mudanças arquiteturais profundas.

3.3. Metodologia

Definição de ciclos de release:
Cada ciclo corresponde ao intervalo entre duas releases major consecutivas.

Coleta de métricas de esforço:

O tamanho total do projeto (em KLOC – thousand lines of code) é medido no início e no fim de cada ciclo.

Todos os commits realizados no ciclo são analisados.

Classificação dos commits:
Cada commit é categorizado automaticamente com base em padrões textuais (regex) presentes nas mensagens de commit, resultando nas seguintes classes:

Commits de Teste: adição ou modificação de arquivos e métodos de teste.

Commits de Correção: correções de defeitos e falhas.

Commits de Refatoração: melhorias estruturais sem alteração de comportamento.

Commits de Manutenção Geral: ajustes diversos não enquadrados nas categorias anteriores.

Agregação e correlação dos esforços:
O número total de commits de teste é comparado com o número total de commits de manutenção, permitindo identificar padrões de correlação positiva ou negativa entre ambos os tipos de esforço.

3.4. Interpretação Esperada

A análise busca determinar se há impacto mensurável do esforço de teste sobre o esforço de manutenção.
Espera-se que projetos com maior investimento em testes apresentem menor frequência de commits corretivos nos ciclos subsequentes, sugerindo uma maior estabilidade e previsibilidade do código.
