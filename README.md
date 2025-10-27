# 📊 Dashboard e Análise Exploratória — Fatores Socioeconômicos no Brasil

Este repositório reúne o **dashboard interativo** e o **notebook de limpeza e exploração de dados** referentes à análise de **fatores socioeconômicos no Brasil**, com foco em indicadores de **desenvolvimento humano, desigualdade, renda, segurança pública e políticas sociais**.

Além disso, este repositório foi produzido como parte final do Desafio 1 do ZettaLab 2° edição, a fim de buscarmos responder a seguinte questão: Como poderíamos avaliar e prever/visualizar os agentes/fenômenos que mais causam 
impactos socioeconômicos no Brasil?.


O Dashboard interativo pode ser acessado a partir do link: (https://joseaugusto-1.github.io/desafio1-zettalab/dashboard.html), ele é a forma de visualização dos dados solicitadas no desafio.

O notebook jupyter e este arquivo README assim como pedido estão disponiveis neste repositório.
---

##  1. Escolha dos Dados

Os dados utilizados neste projeto foram obtidos a partir do **[IPEAData](https://www.ipeadata.gov.br/)**, uma das principais fontes públicas de informações socioeconômicas do Brasil.

Os conjuntos de dados escolhidos refletem dimensões essenciais para entender o desenvolvimento social e econômico dos estados brasileiros:

- **Bolsa Família (2005–2023)** — número de beneficiários por estado.  
- **Índice de Gini (2005–2021)** — medida de desigualdade de renda.  
- **IDH (2005–2021)** — indicador composto de desenvolvimento humano.  
- **Taxa de homicídios (2005–2023)** — indicador de segurança pública.  
- **Renda per capita (2005–2021)** — poder aquisitivo médio da população.  
- **Taxa de mortalidade (2005–2023)** — condição de saúde da população.  
- **Variação do PIB (2005–2021)** — desempenho econômico estadual.  
- **Taxa de analfabetismo e linha de pobreza (2005–2021)** — fatores educacionais e sociais.  

Os dados foram escolhidos por sua relevância para compreender **as desigualdades regionais brasileiras** e **a evolução das condições de vida** nos estados ao longo das últimas duas décadas.

---

##  2. Metodologia de Aquisição e Limpeza dos Dados

A etapa inicial do notebook realiza:

1. **Aquisição:** leitura de arquivos `.csv` exportados do IPEAData, padronizando o formato (separador `;`, codificação UTF-8).  
2. **Remoção de colunas auxiliares:** exclusão de colunas de metadados e colunas vazias.  
3. **Transformação para formato longo:** uso de `pivot_longer()` para criar colunas `Ano` e `Valor` (facilitando comparações temporais).  
4. **Padronização de nomes e tipos:** uniformização de nomes de colunas e conversão de `Ano` para fator/numérico conforme o caso.  
5. **Integração geográfica:** junção com shapefile dos estados obtido via pacote `geobr`, para uso em mapas.  
6. **Mesclagem final:** integração de todas as bases (via `reduce(full_join)`), resultando em uma tabela única com múltiplos indicadores por estado e ano.  

>  **Motivação:** Cada etapa de limpeza foi feita para garantir consistência temporal e espacial entre indicadores e permitir a visualização integrada no dashboard.

---

##  3. Estrutura do Notebook

O arquivo `codigos_desafio.ipynb`  contém as seguintes seções principais:

| Seção | Descrição |
|-------|------------|
| **1. Aquisição de Dados** | Leitura e inspeção das bases do IPEAData. |
| **2. Limpeza e Transformação** | Padronização das tabelas e pivotagem para formato longo. |
| **3. Junção das Bases** | Integração completa dos indicadores em uma única base. |
| **4. Exploração Visual** | Gráficos de dispersão, treemap, boxplots e mapas coropléticos. |
| **5. Geração de Tabelas** | Comparativo de Bolsa Família 2005–2023 e indicadores derivados. |
| **6. Análise de Correlação e Tendências** | Avaliação de relações entre variáveis socioeconômicas. |

Cada célula de código está comentada para explicar **o motivo do processamento** e **a relevância analítica do resultado**.

---

##  4. Principais Insights da Análise Exploratória

Durante a exploração dos dados, foram observados os seguintes padrões e relações:

1. **Bolsa Família e Desigualdade:**  
   Estados com maior número de beneficiários tendem a apresentar **índices de Gini mais altos**, refletindo a concentração de renda e o papel do programa como política redistributiva.  

2. **Segurança Pública:**  
   O **Amapá** foi o estado com **maior taxa de homicídios em 2023**, destacando-se negativamente no indicador.  
   O boxplot mostra forte variação regional na violência letal.  

3. **Saúde e Desenvolvimento:**  
   Existe uma **relação inversa entre IDH e taxa de mortalidade** — quanto maior o IDH, menor a mortalidade média do estado.  

4. **Desenvolvimento Econômico:**  
   Correlação positiva entre **renda per capita** e **IDH**, indicando que avanços econômicos estão associados à melhoria nas condições sociais.
   Podemos observar pelos mapas que os Estados com maior **Índice Gini**, tem menor **IDH**. 

6. **Evolução temporal:**  
   Observa-se **redução gradual da mortalidade** em praticamente todos os estados, enquanto o **índice de Gini mantém-se estável**, indicando persistência da desigualdade.

---

##  5. Dashboard Interativo

O dashboard (arquivo `.qmd`), disponivel em https://joseaugusto-1.github.io/desafio1-zettalab/dashboard.html apresenta os mesmos dados explorados aqui, com **quatro capítulos interativos**:

1. **Políticas Públicas** — Beneficiários do Bolsa Família e desigualdade.  
2. **Segurança Pública** — Taxas de homicídio e variações regionais.  
3. **Saúde** — Mortalidade e desenvolvimento humano.  
4. **Desenvolvimento e Renda** — Relações entre IDH, renda e desigualdade.

Cada página possui cor temática própria, mapas interativos e tabelas sumarizadas.

---

##  6. Fontes e Referências

- **IPEAData:** <https://www.ipeadata.gov.br/>  
- **IBGE / Atlas do Desenvolvimento Humano**  
- **Pacotes R:** `tidyverse`, `geobr`, `sf`, `plotly`, `leaflet`, `treemapify`, `DT`, `gt`  

---

##  7. Autoria e Créditos

**Autor(a):** José Augusto Andrade Souza  
**Instituição:** UFLA - Universidade Federal de Lavras
**Curso:** Bacharelado em Estatística
**Ano:** 2025  

Projeto desenvolvido para fins de **análise exploratória e visualização de dados socioeconômicos brasileiros**.  
