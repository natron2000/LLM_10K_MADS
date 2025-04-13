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
│   ├── response_dics                 # .............
│   ├── score_dicts                   # .............
│   ├── ChromaDB_Analysis.ipynb       # Analysis on ChromaDB chunking results
│   ├── generate_response_dict.ipynb  # .............
│   ├── generate_score_dict.ipynb     # .............
│   ├── model_comparisons.ipynb       # .............    
├── requirements.txt               
├── LICENSE
└── README.md
