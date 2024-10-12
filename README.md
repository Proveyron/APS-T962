# APS – Otimização de Sistemas - 962-94349
# Lucas Pereira da Silva - 2022200556

# Otimização de Carteira de Investimentos

Este projeto implementa uma otimização de carteira de investimentos usando dados financeiros históricos obtidos através da biblioteca `yfinance`. O código permite aos usuários otimizar a alocação de ativos com base em seus retornos esperados e risco (volatilidade), além de visualizar a fronteira eficiente e a evolução do retorno e risco da carteira.

## Funcionalidades Principais

1. **Coleta de Dados Financeiros**:
   - Utiliza a biblioteca `yfinance` para obter os preços ajustados históricos de uma lista de ativos.
   
2. **Otimização de Carteira**:
   - A carteira é otimizada usando a abordagem de Programação Quadrática, com a função objetivo de maximizar o retorno esperado e restrições para risco máximo e pesos dos ativos.
   
3. **Visualizações Gráficas**:
   - **Fronteira Eficiente**: Exibe a fronteira eficiente de várias combinações de pesos de ativos, mostrando a relação entre risco e retorno esperado.
   - **Alocação de Ativos**: Um gráfico de pizza mostra a distribuição dos pesos otimizados entre os ativos.
   - **Evolução de Retorno e Risco**: Exibe a evolução temporal do retorno acumulado da carteira e do risco (volatilidade) móvel anualizada.

## Estrutura do Código

### 1. Importações e Bibliotecas Utilizadas

- **yfinance**: Coleta de dados financeiros históricos.
- **numpy**: Operações matemáticas e numéricas, como cálculos de retornos e matrizes de covariância.
- **pandas**: Manipulação de dados financeiros.
- **scipy.optimize**: Otimização da função objetivo para alocação de ativos.
- **matplotlib**: Criação de gráficos para visualização dos dados e resultados.
- **ipywidgets**: Interface interativa para entrada de parâmetros do usuário.
- **IPython.display**: Utilizado para exibir widgets interativos.

### 2. Funções de Apoio

- `retorno_carteira(pesos, retornos)`: Calcula o retorno esperado da carteira com base nos pesos dos ativos.
- `risco_carteira(pesos, matriz_cov)`: Calcula o risco (volatilidade) da carteira.
- `objetivo(pesos, retornos)`: Função objetivo para maximizar o retorno esperado.
- `restricao_risco(pesos, matriz_cov, risco_maximo)`: Garante que o risco da carteira não exceda um valor máximo especificado.
- `restricao_pesos(pesos)`: Garante que a soma dos pesos seja igual a 1.
- `definir_cores_ativos(ativos)`: Atribui cores distintas aos ativos para os gráficos.
- `plotar_fronteira_eficiente(retornos, matriz_cov)`: Plota a fronteira eficiente de risco vs. retorno.
- `plotar_alocacao(pesos, ativos, cores)`: Gera um gráfico de pizza para mostrar a alocação dos ativos otimizados.
- `plotar_evolucao_retorno_risco(dados, pesos, cores, ativos)`: Exibe a evolução do retorno acumulado e do risco móvel anualizado da carteira.

### 3. Otimização da Carteira

- **Função principal: `otimizar_carteira`**:
  - Coleta dados históricos de preços ajustados usando `yfinance`.
  - Calcula retornos anuais esperados e a matriz de covariância dos ativos.
  - Define e resolve o problema de otimização com restrições de risco e soma dos pesos.
  - Plota a fronteira eficiente, a alocação ótima de ativos e a evolução do retorno e risco da carteira.

### 4. Interface Interativa

- O usuário pode inserir os ativos desejados, intervalo de datas e o risco máximo permitido através de widgets interativos:
  - **Ativos**: Inseridos como símbolos separados por vírgula (e.g., `AAPL, MSFT, GOOGL`).
  - **Data de Início e Fim**: No formato `dd/mm/aaaa`.
  - **Risco Máximo**: Um `slider` interativo que permite ajustar o valor máximo de risco.

### 5. Exemplo de Uso

Para usar o código interativo, basta seguir os passos abaixo:

1. **Inserir Ativos**: Escolher uma lista de ativos, como `AAPL, MSFT, GOOGL`.
2. **Definir Datas de Início e Fim**: Inserir o intervalo de tempo para análise, como `01/01/2020` a `01/01/2023`.
3. **Definir Risco Máximo**: Ajustar o risco máximo permitido para a carteira.
4. **Processar**: Clicar no botão para processar e gerar os resultados.

## Requisitos de Instalação

Este projeto requer as seguintes bibliotecas:

```bash
pip install yfinance numpy pandas scipy matplotlib ipywidgets
```

## Exemplo de Entrada

- **Ativos**: `AAPL, MSFT, GOOGL`
- **Data de Início**: `01/01/2020`
- **Data de Fim**: `01/01/2023`
- **Risco Máximo**: `0.2`

## Observações

- Este código assume que os dados dos ativos são corretamente baixados do Yahoo Finance, e a conexão à internet é necessária para essa operação.
- Os resultados dependem da qualidade dos dados e do intervalo de tempo escolhido.
  
## Licença

Este projeto é disponibilizado sob a licença MIT.
