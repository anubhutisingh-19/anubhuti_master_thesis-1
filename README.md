## Master's Thesis
Enhancing the Capabilities of Large Language Models Using Knowledge Graphs in Finance.

## Table of Contents
1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Usage](#usage)
4. [Blazegraph Setup](#blazegraph-setup-optional)
5. [Python Scripts Overview](#python-scripts-overview)
6. [Generating Requirements File](#generating-requirements-file)

## Prerequisites
- Python 3.x installed
- Git for version control
- (Required) Java installed to run Blazegraph locally on Windows


### 2. **Create and activate a virtual environment (optional but recommended)**:
   ```bash
   python -m venv venv
   source venv/bin/activate    # On macOS/Linux
   venv\Scripts\activate       # On Windows
   ```

### 3. **Install required Python packages** (if a `requirements.txt` is already present):
   ```bash
   pip install -r requirements.txt
   ```

## Usage

### Install Blazegraph on Windows
1. **Download Blazegraph**  
   - Visit the [Blazegraph Releases](https://github.com/blazegraph/database/releases) page.
   - Download the `blazegraph.jar` file.

2. **Run Blazegraph**  
   1. Place the `blazegraph.jar` file in a folder (e.g., `C:\Blazegraph`).
   2. Open Command Prompt and navigate to that folder:
      ```bash
      cd C:\Blazegraph
      ```
   3. Start Blazegraph:
      ```bash
      java -server -Xmx4g -jar blazegraph.jar
      ```
   4. Once Blazegraph is running, you can access it at:
      
    http://localhost:9999/blazegraph
      
   5. Navigate to "Namespace" in the UI and create a new namespace with:
    - Name: `myGraph`
    - Mode: `triples`
    Default namespace `kb`

    Update the namespace in the blazegraph url in all the files under `blazegraph` folder.
    http://localhost:9999/blazegraph/namespace/myGraph/sparql
    
## Python Scripts Overview
Below is an overview of the key Python files and their functionalities:

### **1. ` baselineModel/`**  
Implements baseline retrieval approaches.
'BM25.ipynb' – Lexical retrieval with BM25.
'DPR.ipynb' – Dense retrieval using transformers.
'tf-idf.ipynb' – TF-IDF based baseline.
'simpleRAG.py' – A simple RAG (Retrieval-Augmented Generation) prototype using CSV data.

### **2. `blazegraph/`**  
  SPARQL query generation and evaluation using Blazegraph.
'eval.ipynb' – Approach evaluation using metrics (Precision, Recall, F1, MRR, hits@k,Rougue, Bleu, chrF).
'LLMApache.ipynb' – Query generation and validation with LLM and using Apache Jena Fuseki graph database.
'LLMBlazegraphVal.ipynb' – Batch SPARQL generation and LLM answer generation from Excel queries using Blazegraph graph database.

### **3. `kgCreation/`**  
  Knowledge graph construction and schema management.
'CompleteFINKG.ipynb' – Builds the complete financial knowledge graph from CSVs and RDF triples.
'ExtendedFinKG_Pro_anonymized.ttl' – An anonymized RDF Turtle file representing an extended version of the financial knowledge graph.
'ontology_schema.jsonld' – JSON-LD representation of the ontology used to define schema and classes in the knowledge graph.

### **4. `LangGraph/`**  
  LangGraph-based RAG pipelines.
'LG_hybrid_subgraph.ipynb' – Retrieves and processes hybrid subgraphs using LLM-assisted query parsing and subgraph ranking.
'LG_hybrid_triple.ipynb' – Focuses on triple-level retrieval and evaluation within the LangGraph pipeline.
'LG_LLMblazegraph.ipynb' – Combines LangGraph and Blazegraph to perform end-to-end retrieval and answer generation via SPARQL.

### **5. `RDF-RAG/`**  
  Final and hybridized implementation of the RDF-RAG pipeline.
'hybrid.ipynb' - Main hybrid retrieval pipeline that uses both lexical and dense retrieval (via RRF), LLM parsing, subgraph linking, and natural language generation.
'hybrid_triple.ipynb' - Variant of the hybrid model working at the triple-level rather than the subgraph level.

## Generating Requirements File
To automatically generate a `requirements.txt` file based on the libraries used in the project, you can use any of the following methods:

   Make sure all your dependencies are installed in your current Python environment, then run:
   ```bash
   pip freeze > requirements.txt
   ```
   This will create (or overwrite) a `requirements.txt` file listing the exact versions of the installed packages.
 
## **Acknowledgments**
- Siemens Energy for providing computational resources and domain expertise.
- University of Paderborn for academic support and guidance.
 
 
 