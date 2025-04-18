# LLM 10-K RAG

A RAG system to provide accurate answers based off of 10-K reports from S&P 500 companes. 

## Description

This project creates a framework to build a chat bot on top of a vector database that helps answer questions on S&P 500 companies by retreving context from their 10-K reports that was submitted to the SEC. 

## Requirements

Packages from the requirements.txt.
Ollama program
Enough computing power to run DeepSeek-R1

## Package Structure

├── GUI_Images                        # Example Image of GUI  
├── Main_Code                          
│   ├── cap_1_meta.py                 # Define S&P 500 Universe and Create Meta Fields  
│   ├── cap_2_down.py                 # Download 10-K reports  
│   ├── cap_3_store.py                # Store 10-K reports in ChromaDB database  
│   ├── cap_4_chat.py                 # Create/Run GUI for LLM  
├── Model_Evaluation                  
│   ├── response_dics                 # Responses of different RAG structures to test question set  
│   ├── score_dicts                   # Scores of the RAG's responses  <br />
│   ├── ChromaDB_Analysis.ipynb       # Analysis on ChromaDB chunking results  <br />
│   ├── generate_response_dict.ipynb  # Feeds test question set into RAGs to produce files in response_dicts <br />
│   ├── generate_score_dict.ipynb     # Evaluates the responses from response_dicts and stores the results in score_dicts <br />
│   ├── model_comparisons.ipynb       # Graphs showing comparison of various RAG structures     
├── requirements.txt                 
├── LICENSE   
└── README.md  


## Evaluation Instructions
**Instructions for Evaluation:** <br/>

To replicate graphs all that is needed to run is model_comparisons.ipynb, since all model scores are stored in the score_dicts folder.  The three other notebooks produce the files in the score_dicts folder.<br/>

**For full replication follow these steps:** <br/>

*Must run contents of Main_Code folder first*

1.	Run through create_alt_vector_stores.ipynb to create the alternate chroma db vector store
      a.	Ensure filings_path in cell 2 is set to the path of the files produced by cap_2_down.py
2.	Run through generate_responses_dict.ipynb to create the response dictionaries to use for scoring
      a.	Ensure file paths in cell 2 are set to the correct location of vector stores
3.	Run through generate_score_dict.ipynb to score the responses and produce files in score_dicts
4.	Run through model_comparisons.ipynb to generate visuals of comparisons used in report
