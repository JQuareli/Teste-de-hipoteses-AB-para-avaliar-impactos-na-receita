# Testando Hipóteses com Teste A/B

## Análise de Dados

Este repositório contém dados coletados, limpados e analisados para avaliar o impacto de diferentes ações na conversão e receita de uma loja online. Além disso, foram realizados testes A/B para comparar o desempenho de diferentes grupos e priorizar implementações.

## Índice

- [Metodologia](#metodologia)
- [Bibliotecas Utilizadas](#bibliotecas-utilizadas)
- [Conclusões](#conclusões)
- [Como Utilizar](#como-utilizar-este-repositório)
- [Como Contribuir](#como-contribuir)

## Metodologia

### Coleta e Pré-processamento de Dados

Os dados utilizados para esta análise foram coletados de diversas fontes e compreendem diferentes aspectos do funil de conversão de uma loja online. Os conjuntos de dados incluem informações sobre hipóteses de melhoria, pedidos de clientes e visitas ao site.

1. **Descrição dos Dados**:
    - `hypotheses_us.csv`: Contém nove hipóteses com variáveis como `Reach`, `Impact`, `Confidence` e `Effort`.
    - `orders_us.csv`: Inclui detalhes dos pedidos realizados, como `transactionId`, `visitorId`, `date`, `revenue` e `group` (grupo A/B).
    - `visits_us.csv`: Registra as visitas ao site, com variáveis como `date`, `group` e `visits`.

Os dados foram limpos e organizados utilizando a biblioteca Pandas do Python para garantir a precisão das análises subsequentes. Durante o pré-processamento, foram identificados e corrigidos erros, como visitantes presentes em ambos os grupos de teste A/B.

### Análise Exploratória de Dados (EDA)

Visualizações gráficas foram criadas utilizando Matplotlib para identificar padrões e tendências nos dados. A EDA incluiu:
- Gráficos de receita acumulada por grupo.
- Gráficos do tamanho médio acumulado do pedido por grupo.
- Análise de taxas de conversão diárias e cumulativas.
- Identificação de anomalias através de gráficos de dispersão e percentis.

### Priorização de Hipóteses

Para priorizar as hipóteses de melhorias na receita, aplicamos dois frameworks de priorização:

1. **Framework ICE**:
    - Calcula o valor de `ICE` como:
      ```
      ICE = (Impact * Confidence) / Effort
    - Classifica as hipóteses com base em seu valor de ICE.

2. **Framework RICE**:
    - Calcula o valor de RICE como:
      ```
      RICE = (Reach * Impact * Confidence) / Effort
      ```
    - Classifica as hipóteses com base em seu valor de RICE.

Comparamos os resultados dos frameworks ICE e RICE para entender como a inclusão do alcance (`Reach`) influencia a priorização das hipóteses e justificamos as mudanças observadas.

### Testes A/B

Para avaliar o impacto das diferentes ações, realizamos testes A/B nos grupos de usuários utilizando a biblioteca SciPy do Python:

1. **Comparação de Grupos**:
    - Calculamos e comparamos a receita acumulada e o tamanho médio dos pedidos entre os grupos A e B.
    - Analisamos as taxas de conversão diárias e cumulativas.

2. **Testes Estatísticos**:
    - **Teste U de Mann-Whitney**: Utilizado quando não podemos assumir que as distribuições das amostras são normais.

3. **Identificação de Anomalias**:
    - Calculamos os percentis 95 e 99 para o número de pedidos por usuário e preços dos pedidos.
    - Definimos pontos de corte para identificar e tratar anomalias.

As conclusões foram baseadas nas análises estatísticas dos dados brutos e filtrados, proporcionando insights sobre a eficácia das ações testadas.

## Bibliotecas Utilizadas

As seguintes bibliotecas Python foram utilizadas para análise de dados e visualização:

- [Pandas](https://pandas.pydata.org/)
- [Matplotlib](https://matplotlib.org/)
- [SciPy](https://scipy.org/)
- [Statistics](https://docs.python.org/3/library/statistics.html)
- [Seaborn](https://seaborn.pydata.org/)

## Conclusões

### RICE

Com base na análise de dados e na aplicação do método RICE, concluímos que adicionar um formulário de assinatura em todas as páginas da loja online tem um potencial significativo de impacto na receita. O cálculo do RICE indicou que essa ação possui um alto potencial de retorno sobre o investimento.

### Testes A/B

Nos testes A/B, o grupo B apresentou um volume de vendas maior do que o grupo A. No entanto, não houve diferença significativa na receita entre os dois grupos. Se a empresa busca aumentar o volume de vendas, deve focar nas estratégias utilizadas pelo grupo B.

## Como utilizar este repositório

Para utilizar, basta clonar o repositório e instalar o arquivo requirements.txt em um ambiente Python. Os scripts são bem documentados e podem ser facilmente adaptados para outras análises de dados.

## Como Contribuir

Se você deseja contribuir para este projeto, siga estas etapas:

1. Faça um fork do repositório.
2. Crie uma branch para sua feature (`git checkout -b feature/nova-feature`).
3. Commit suas mudanças (`git commit -m 'Adiciona nova feature'`).
4. Push para a branch (`git push origin feature/nova-feature`).
5. Abra um Pull Request.
