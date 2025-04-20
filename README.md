# LLM 10-K RAG

A RAG system to provide accurate answers based off of 10-K reports from S&P 500 companies. 

## Description

This project creates a framework to build a chatbot on top of a vector database that helps answer questions on S&P 500 companies by retreving context from their 10-K reports that was submitted to the SEC. 

## Requirements

Packages from the requirements.txt.
Ollama program
all-minilm & Llama 3.2 downloaded
Enough computing power to run Llama 3.2

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

## RAG Model Instructions
*To run through the main code there is a little bit of setup to do:* <br />

**1. Ollama Setup** <br />
First, download Ollama from their site. Next you will need to “pull” the models’ files. In our code we use all-minilm for embedding and llama3.2 for the large language model. Be sure your device 1- has the appropriate amount of space available to save the model and 2- has the appropriate amount of memory to 
run the model. You can pull the models from your command prompt by running ollama pull [model name]. There is no need to “serve” the models yet, our python 
code takes care of that. <br />

**2. cap_1_meta.py** <br />
Next you will want to install the libraries listed in the requirements file. For the first code file, cap_1_meta, we used a .env file to hold API key but you can hardcode it if you don’t feel like taking that extra step. You will need the API key to interact with the SEC files. Feel free to adjust the year ranges or even pull your own choice of companies. Those options can be tweaked within the python file itself. This file gathers all the necessary information to prepare for downloading the actual 10Ks.

**3. cap_2_down.py** <br />
The second file to run is cap_2_down. We again used a .env to setup the API key. This file gets the filings from the SEC and could take some time to run.

**4. cap_3_store.py** <br />
Cap_3_store builds out our vector database. It will handle launching Ollama, chunking the documents, embedding the chunks, and storing them with ChromaDB. If you decided to go with a different embedding model, be sure to adjust it within the main function. <br />

**5. cap_4_chat.py** <br />
Cap_4_chat is what launches our program. If you are using different models, be sure to adjust them. If you changed any file or directory names in the previous files, be sure to update them here as well.  A window should pop up after running this file where you can ask the RAG questions

## Evaluation Instructions
**Instructions for Evaluation:** <br/>

To replicate comparison graphs all that is needed to run is model_comparisons.ipynb, since all model scores are stored in the score_dicts folder.  The three other notebooks create the vector stores, files in the response_dicts folder, and produce the files in the score_dicts folder whcih are used in the model comparisons.<br/>

**For full replication follow these steps:** <br/>

**Must run contents of Main_Code folder first.**<br/>
*Required Ollama Models: all-minilm, llama3.2,deepseek-r1,and mistral-nemo*
1.	Run through create_alt_vector_stores.ipynb to create the alternate chroma db vector store *(This file will take a long time to run)* <br/>
   Ensure file path in cell 2 is set to the path of the files produced by cap_2_down.py <br />
2.	Run through generate_responses_dict.ipynb to create the response dictionaries to use for scoring <br />
   Ensure file paths in cell 2 are set to the correct location of vector stores <br />
3.	Run through generate_score_dict.ipynb to score the responses and produce files in score_dicts <br />
4.	Run through model_comparisons.ipynb to generate visuals of comparisons used in report<br />
5.  Run ChromaDB_Analysis.ipynb to produce comparison files <br />
    *Will need to ensure file paths match up to the correct filepaths produced by cap_3_down.py and create_alt_vector_stores.ipynb*


## Data Access

List of SP500 companies came from iShares by BlackRock: https://www.ishares.com/us 

SEC Filings came from the SEC-API by D2V https://sec-api.io/ 
