# Atividade Supervisionada – Otimização de Sistemas
# Lucas Pereira da Silva - 2022200556

Este repositório implementa uma ferramenta de otimização de carteiras utilizando dados financeiros históricos e diversos métodos de análise estatística para calcular retornos e riscos, além de gerar gráficos interativos para visualização.

## Dependências

Este projeto utiliza as seguintes bibliotecas Python:
- `yfinance`: Para obtenção de dados financeiros históricos.
- `numpy`: Para cálculos numéricos eficientes.
- `pandas`: Para manipulação de dados financeiros.
- `scipy.optimize`: Para otimização de funções (usado na otimização da carteira).
- `matplotlib`: Para criação de gráficos.
- `ipywidgets`: Para criar widgets interativos para entrada de parâmetros do usuário.
- `IPython.display`: Para exibir os widgets no Jupyter Notebook.

Para instalar as dependências, execute:
```bash
pip install yfinance numpy pandas scipy matplotlib ipywidgets
```

## Funções

### 1. `retorno_carteira(pesos, retornos)`
Calcula o retorno esperado de uma carteira dada uma combinação de pesos e retornos esperados dos ativos.

### 2. `risco_carteira(pesos, matriz_cov)`
Calcula o risco (volatilidade) da carteira, dado os pesos dos ativos e a matriz de covariância dos retornos.

### 3. `objetivo(pesos, retornos)`
Função objetivo para maximizar o retorno da carteira. Retorna o valor negativo do retorno para que o otimizador minimize esta função (equivalente a maximizar o retorno).

### 4. `restricao_risco(pesos, matriz_cov, risco_maximo)`
Define uma restrição de risco máximo para a otimização. Garante que a volatilidade da carteira não ultrapasse um valor definido pelo usuário.

### 5. `restricao_pesos(pesos)`
Garante que a soma dos pesos dos ativos na carteira seja igual a 1, uma restrição essencial para uma carteira válida.

### 6. `plotar_fronteira_eficiente(retornos, matriz_cov)`
Gera um gráfico da Fronteira Eficiente com base em retornos simulados e riscos. Cada ponto no gráfico representa uma possível combinação de risco e retorno para a carteira.

### 7. `plotar_alocacao(pesos, ativos)`
Cria um gráfico de pizza que exibe a alocação percentual de ativos na carteira otimizada.

### 8. `plotar_evolucao_retorno_risco(dados, pesos)`
Exibe dois gráficos: um para o retorno acumulado da carteira e outro para a evolução do risco (volatilidade) ao longo do tempo.

### 9. `otimizar_carteira(ativos, data_inicio, data_fim, risco_maximo)`
Função principal que realiza a otimização da carteira, aplicando restrições de risco máximo e retornando a alocação ótima de ativos. Também gera gráficos de visualização para os resultados.

### 10. `processar_entrada(ativos, data_inicio, data_fim, risco_maximo)`
Processa as entradas do usuário (ativos, datas de início e fim, risco máximo) e executa a otimização da carteira com base nesses parâmetros.

## Interface Interativa

A interface permite que o usuário insira os ativos e parâmetros diretamente no Jupyter Notebook via widgets interativos.

### Parâmetros de Entrada:
- **Ativos**: Uma lista de ativos separados por vírgula, como "AAPL,MSFT,GOOGL".
- **Data de Início e Fim**: Intervalo de datas para a coleta de dados históricos.
- **Risco Máximo**: Um limite de volatilidade (risco) para a carteira otimizada.

### Botão de Processamento:
Um botão que, ao ser clicado, processa os dados inseridos e exibe a carteira otimizada, gráficos da Fronteira Eficiente e alocação de ativos.

### Exemplo de Uso

1. Execute o código e insira os parâmetros desejados nos widgets.
2. Clique no botão "Processar" para calcular e visualizar a carteira otimizada.

## Visualizações

O script gera três tipos principais de visualizações:
- **Fronteira Eficiente**: Um gráfico que mostra a relação entre risco e retorno de diferentes combinações de ativos.
- **Alocação de Ativos**: Um gráfico de pizza mostrando a distribuição dos ativos na carteira otimizada.
- **Evolução do Retorno e Risco**: Gráficos que mostram a evolução do retorno acumulado e a volatilidade ao longo do tempo.

## Observações

A ferramenta é voltada para quem deseja realizar uma análise de portfólio baseada em dados históricos e obter uma alocação de ativos eficiente sob restrições de risco.
