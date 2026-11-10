# InvestMatch

Aplicación web educativa que recomienda productos de inversión a clientes nuevos y actuales mediante un modelo de aprendizaje automático entrenado con datos sintéticos.

**Estado:** En fase inicial de desarrollo · **Proyecto:** MBA en Ingeniería de IA Aplicada

## Qué mostrará la demostración

| Tipo de cliente | Datos de entrada | Resultado esperado |
| --- | --- | --- |
| Cliente nuevo | Respuestas a un breve cuestionario de perfil | Una lista de productos ordenada según la información proporcionada |
| Cliente actual | Información del perfil e historial sintético de inversiones, cuando esté disponible | Una lista ordenada que también puede reflejar la actividad de inversión previa |

La primera versión se centrará en fondos de inversión. Los productos de renta fija, las acciones y los fondos de inversión inmobiliaria brasileños (FII) podrán incorporarse en futuras versiones, según la disponibilidad de los datos.

## Conjunto de datos

El punto de partida es un conjunto de datos sintéticos sobre las posiciones de clientes en fondos de inversión, publicado por **felipeueta**. Antes de elegir las variables de entrada del modelo, el proyecto analizará los campos disponibles e identificará qué información puede utilizarse en ambos escenarios. Consulta el [conjunto de datos original en Kaggle](https://www.kaggle.com/datasets/felipeueta/basesintetica-fundosinvestimentos).

Las posiciones históricas pueden ayudar a identificar patrones de inversión previos. La demostración utilizará las listas ordenadas para ilustrar la búsqueda por similitud y la personalización en un contexto educativo.

## Arquitectura prevista

| Componente | Función |
| --- | --- |
| Node.js | Ejecuta el backend de la aplicación y procesa las solicitudes de recomendación. |
| TensorFlow.js | Entrena el modelo y genera vectores numéricos (embeddings) para las recomendaciones. |
| ChromaDB | Almacena los vectores generados y recupera candidatos similares para ordenarlos. |

1. **Preparar los datos.** Analizar y preprocesar las posiciones sintéticas en fondos. Definir qué variables estarán disponibles en el momento de la recomendación para cada tipo de cliente.
2. **Entrenar e indexar.** Entrenar un modelo con TensorFlow.js, exportar los vectores generados como arreglos numéricos e indexarlos en ChromaDB con identificadores que vinculen cada vector con su registro de origen.
3. **Consultar y mostrar.** Utilizar los datos proporcionados sobre el cliente para generar un vector de consulta en el mismo espacio vectorial que los vectores indexados. Consultar ChromaDB para encontrar candidatos similares y mostrar los primeros resultados en la interfaz web.

Consulta la [guía de TensorFlow.js para Node.js](https://www.tensorflow.org/js/guide/nodejs) y la [documentación de búsqueda por similitud de ChromaDB](https://docs.trychroma.com/docs/querying-collections/query-and-get).

## Hoja de ruta

- [ ] Analizar la estructura del conjunto de datos y documentar las variables seleccionadas para el modelo.
- [ ] Implementar el flujo de preparación de datos y entrenamiento con TensorFlow.js.
- [ ] Almacenar y consultar embeddings en ChromaDB.
- [ ] Crear los flujos web para clientes nuevos y actuales.
- [ ] Comparar las primeras recomendaciones con un método de referencia simple basado en popularidad, utilizando datos reservados para la evaluación, y presentar los resultados por separado para ambos flujos.
- [ ] Documentar la configuración local y publicar una demostración con perfiles de ejemplo.

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

**André de Moraes Jouval** · Proyecto de portafolio del MBA en Ingeniería de IA Aplicada
