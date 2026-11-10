# InvestMatch

An educational web application that recommends investment products to new and existing clients using a machine learning model trained on synthetic data.

**Status:** Early development · **Project:** Applied AI Engineering MBA

## What the demo will show

| Client scenario | Inputs | Expected output |
| --- | --- | --- |
| New client | Answers to a short profile questionnaire | A ranked list of products based on the information provided |
| Existing client | Profile information and synthetic investment history, when available | A ranked list that can also reflect past investment activity |

The first version will focus on investment funds. Fixed income, equities, and Brazilian real estate investment funds (FIIs) are candidates for future versions, depending on data availability.

## Dataset

The starting point is a synthetic dataset of client investment fund positions published by **felipeueta**. Before choosing the model inputs, the project will inspect the available fields and identify which signals can be used for both client scenarios. See the [source dataset on Kaggle](https://www.kaggle.com/datasets/felipeueta/basesintetica-fundosinvestimentos).

Historical positions can provide a signal of past behavior. The demo will use the resulting rankings to illustrate similarity and personalization in an educational setting.

## Planned architecture

| Component | Role |
| --- | --- |
| Node.js | Runs the application backend and handles recommendation requests. |
| TensorFlow.js | Trains the model and produces numerical vectors (embeddings) for recommendation. |
| ChromaDB | Stores the generated vectors and retrieves similar candidates for ranking. |

1. **Prepare the data.** Inspect and preprocess the synthetic fund positions. Define which features are available at recommendation time for each client scenario.
2. **Train and index.** Train a model with TensorFlow.js, export the generated vectors as numeric arrays, and index them in ChromaDB with IDs that link each vector back to its source record.
3. **Retrieve and display.** Use the submitted client information to generate a query vector in the same embedding space as the indexed vectors. Query ChromaDB for similar candidates and display the top results in the web interface.

See the [TensorFlow.js guide for Node.js](https://www.tensorflow.org/js/guide/nodejs) and [ChromaDB similarity search documentation](https://docs.trychroma.com/docs/querying-collections/query-and-get).

## Roadmap

- [ ] Inspect the dataset schema and document the selected model features.
- [ ] Implement the data preparation and TensorFlow.js training pipeline.
- [ ] Store and query embeddings in ChromaDB.
- [ ] Build the new-client and existing-client web flows.
- [ ] Compare the top recommendations with a simple popularity baseline using held-out data, and report results separately for the two flows.
- [ ] Document the local setup and publish a demo with sample profiles.

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

## Author

**André de Moraes Jouval** · Applied AI Engineering MBA portfolio project
