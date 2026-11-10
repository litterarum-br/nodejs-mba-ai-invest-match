# InvestMatch

Aplicação web educacional que recomenda produtos de investimento a clientes novos e da base usando um modelo de aprendizado de máquina treinado com dados sintéticos.

**Status:** Em fase inicial de desenvolvimento · **Projeto:** MBA em Engenharia de IA Aplicada

## O que a demonstração vai mostrar

| Cenário do cliente | Dados de entrada | Resultado esperado |
| --- | --- | --- |
| Cliente novo | Respostas a um questionário curto sobre o perfil | Uma lista de produtos ordenada com base nas informações fornecidas |
| Cliente da base | Informações de perfil e histórico sintético de investimentos, quando disponível | Uma lista ordenada que também pode refletir o histórico de investimentos |

A primeira versão terá foco em fundos de investimento. Renda fixa, ações e fundos de investimento imobiliário (FIIs) poderão ser incluídos em versões futuras, conforme a disponibilidade dos dados.

## Base de dados

O ponto de partida é uma base sintética de posições de clientes em fundos de investimento, publicada por **felipeueta**. Antes de escolher as variáveis de entrada do modelo, o projeto vai analisar os campos disponíveis e identificar quais informações podem ser usadas nos dois cenários. Consulte a [base de dados original no Kaggle](https://www.kaggle.com/datasets/felipeueta/basesintetica-fundosinvestimentos).

As posições históricas podem ajudar a identificar padrões de investimento anteriores. A demonstração usará as listas ordenadas para ilustrar a busca por similaridade e a personalização em um contexto educacional.

## Arquitetura planejada

| Componente | Função |
| --- | --- |
| Node.js | Executa o backend da aplicação e processa as solicitações de recomendação. |
| TensorFlow.js | Treina o modelo e gera vetores numéricos (embeddings) para as recomendações. |
| ChromaDB | Armazena os vetores gerados e recupera candidatos semelhantes para a classificação. |

1. **Preparar os dados.** Analisar e pré-processar as posições sintéticas em fundos. Definir quais variáveis estarão disponíveis no momento da recomendação em cada cenário.
2. **Treinar e indexar.** Treinar um modelo com TensorFlow.js, exportar os vetores gerados como arrays numéricos e indexá-los no ChromaDB com identificadores que associem cada vetor ao registro de origem.
3. **Consultar e exibir.** Usar os dados informados sobre o cliente para gerar um vetor de consulta no mesmo espaço vetorial dos vetores indexados. Consultar o ChromaDB para encontrar candidatos semelhantes e exibir os primeiros resultados na interface web.

Consulte o [guia do TensorFlow.js para Node.js](https://www.tensorflow.org/js/guide/nodejs) e a [documentação de busca por similaridade do ChromaDB](https://docs.trychroma.com/docs/querying-collections/query-and-get).

## Roadmap

- [ ] Analisar a estrutura da base e documentar as variáveis selecionadas para o modelo.
- [ ] Implementar o fluxo de preparação de dados e treinamento com TensorFlow.js.
- [ ] Armazenar e consultar embeddings no ChromaDB.
- [ ] Criar os fluxos web para clientes novos e da base.
- [ ] Comparar as primeiras recomendações com uma referência simples baseada em popularidade, usando dados reservados para avaliação, e apresentar os resultados separadamente para os dois fluxos.
- [ ] Documentar a configuração local e publicar uma demonstração com perfis de exemplo.

## Project Structure

- `index.html` - Main HTML file for the application
- `index.js` - Entry point for the application
- `view/` - Contains classes for managing the DOM and templates
- `controller/` - Contains controllers to connect views and services
- `service/` - Contains business logic for data handling
- `data/` - Contains JSON files with user and product data

## Setup and Run

1. Install dependencies:
```
npm install
```

2. Start the application:
```
npm start
```

3. Open your browser and navigate to `http://localhost:3000`

## Autor

**André de Moraes Jouval** · Projeto de portfólio do MBA em Engenharia de IA Aplicada
