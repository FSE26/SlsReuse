# SlsReuse: LLM-Powered Serverless Function Reuse

We provide our framework code, evaluation dataset, evaluation baselines, and evaluation results.

## Code of SlsReuse
Our function reuse approach consists of the following key scripts which supports different LLMs: 
- “SlsReuse_representation.py” quantifies all functions and store them in JSON format into the dataset; 
- “SlsReuse_recommend.py” discoveries and returns high similarity functions based on task requests.

The file “mapping.py” constructed a mapping table to normalize terminology.

The file “pareto.py” pured irrelevant functions based on task requirements and yielded a set of relevant candidate functions for subsequent recommendation.


## Evaluation Dataset

- The file “Serverless Function Reuse.xlsx” included 500 serverless functions ID, original names and their source links.
- We construct this evaluation dataset including 150 task queries extracted from the GitHub README. The file “Task queries.xlsx” included 150 user requests and their source link.


## Evaluation Baselines
Baseline 1: Keyword-based method in the dictionary “Baselines”
- The file “keywords_dataset.py” can extract keywords from functions in a stop word remove and stem manner and store them in JSON format into the dataset.
- The file “keywords_retrive.py” can extract keywords from user requests in a stop word remove and stem manner, and match the extracted keywords with the keywords of all functions in the JSON dataset.

Baseline 2: Embedding-based method in the “Baselines”
- The file “embedding_dataset.py” encoded the function code into a dense embedding vector using a pre-trained sentence encoderand store them in JSON format into the dataset
- The file “embedding_retrive.py” encoded the user request into a dense embedding vector using a pre-trained sentence encoder, and ranked candidate functions by computing the cosine similarity between the query embedding and the function embeddings.

Baseline 3: Customized LLM-based variant method in the “Baselines”
- The file “customized_retrive.py” leveraged LLMs to generate intent summaries without extracting multi-dimensional structural information, encoded it into semantic embeddings using a pre-trained sentence encoder and computing cosine similarity between the query embedding and candidate function embeddings to obtain recommendations.


## Evaluation Results
We provide the evaluation results about RQ1, RQ2, RQ3, and RQ4 in the directory "EvaluationResults"
- In the directory “RQ1”, the metric results and thier corresponding JSON files of keyword-based method (Baseline1) and embedding-based method (Baseline2) are provided.
- In the directory “RQ2”, the metric results and thier corresponding JSON files of customized LLM-based method (Baseline3) when repeated 5 times are provided.
- In the directory “RQ3”, the metric results and thier corresponding JSON files of SlsReuse are provided, including results of different temperatures (0, 0.2, 0.5) when repeated 5 times.
- In the directory “RQ3”, the metric results and thier corresponding JSON files of SlsReuse are provided, including results of different LLMs (Llama 3.1 (405B) Instruct Turbo, Gemini 2.0 Flash and DeepSeek V3) when repeated 5 times.