# DEMO RAG

## Whats this ?
This is a RAG demo to ask questions to an LLM about pdfs docs

## How does it works ?
It works by using a prompt to search in a vectorial db, chunks of docs then using a LLM with this result to add context to the question.
By doing this we can generate prompts that does not include the whole context of a doc but only getting the revelants part allowing better performances and preventing training every time new data is added (only the db need to be updated).

Here's a cool article about embeddings and vector db https://www.cloudflare.com/learning/ai/what-are-embeddings/

## How do i setup this ?
First you will need :
- python 3
- Ollama
    - mistral pulled `ollama pull mistral`
    - nomic-embed-text pulled `ollama pull nomic-embed-text`

then create a VENV (to isolate this project) (great way to do this is by using vscode great extension `donjayamanne.python-environment-manager`)

Inside the new venv env execute `pip install -r .\requirements.txt`

now you can add pdfs into the data folder (right now there is the rules of the game complot in french but you can delete it and add any pdfs)

After adding the pdfs you need to run the `populate_database.py`

When it's done a new folder called "chroma" should appear it's the vector db (black magic only the most bearded one comprehend)

you can then run the script `query_data.py` with your question, like this : `python .\query_data.py "Peut tu m'expliquer les règles de complot"`

depending on the model used and the pdfs/prompt quality the response may be wrong but should be revelant anyway (not production ready just a demo remember).

## Can i use others types of data ?
Yes and it's not that hard, langchain happen to allow uses of different types of doc loaders.
One of them is a json loader (so you may use an api to generate your chromadb) 
https://python.langchain.com/v0.1/docs/modules/data_connection/document_loaders/json/


## Credits
original repo : https://github.com/pixegami/rag-tutorial-v2/
changes : Adapted code to updated dependencies.
