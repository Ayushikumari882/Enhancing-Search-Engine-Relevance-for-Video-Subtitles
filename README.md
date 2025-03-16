# Enhancing-Search-Engine-Relevance-for-Video-Subtitles

## Background
In the fast-evolving landscape of digital content, effective search engines play a pivotal role in connecting users with relevant information. For Google, providing a seamless and accurate search experience is paramount. This project focuses on improving the search relevance for video subtitles, enhancing the accessibility of video content.

## Objective
Develop an advanced search engine algorithm that efficiently retrieves subtitles based on user queries, with a specific emphasis on subtitle content. The primary goal is to leverage natural language processing and machine learning techniques to enhance the relevance and accuracy of search results.

## Keyword-based vs Semantic Search Engines
- **Keyword Based Search Engine:** These search engines rely heavily on exact keyword matches between the user query and the indexed documents.
- **Semantic Search Engines:** Semantic search engines go beyond simple keyword matching to understand the meaning and context of user queries and documents.
- **Comparison:** While keyword-based search engines focus primarily on matching exact keywords in documents, semantic-based search engines aim to understand the deeper meaning and context of user queries to deliver more relevant and meaningful search results.

## Core Logic
To compare a user query against a video subtitle document, the core logic involves three key steps:

1. **Preprocessing of Data:** 
   - Read the given data.
   - Observe that the given data is a database file.
   - Go through the README.txt to understand what is there inside the database.
   - Take care of decoding the files inside the database.
   - Apply appropriate cleaning steps on subtitle documents (whatever is required).

2. **Vectorization:**
   - Experiment with the following to generate text vectors of subtitle documents:
     - BOW / TFIDF to generate sparse vector representations. Note that this will only help you to build a Keyword Based Search Engine.
     - BERT based “SentenceTransformers” to generate embeddings which encode semantic information. This can help us build a Semantic Search Engine.
   - **Document Chunker:** Consider the challenge of embedding large documents: Information Loss. It is often not practical to embed an entire document as a single vector, particularly when dealing with long documents.
     - Divide a large document into smaller, more manageable chunks for embedding.
     - To mitigate accidentally cutting off important text between chunks, set overlapping windows with a specified amount of tokens to overlap so there are tokens shared between chunks.
   - Store embeddings in a ChromaDB database.

3. **Retrieving Documents:**
   - Take the user's search query.
   - Preprocess the query (if required).
   - Create query embedding.
   - Using cosine distance, calculate the similarity score between embeddings of documents and user search query embedding.
   - These cosine similarity scores will help in returning the most relevant candidate documents as per user’s search query.

## Step-by-Step Process

### Part 1: Ingesting Documents
1. **Read the given data.**
2. **Observe that the given data is a database file.**
3. **Go through the README.txt to understand what is there inside the database.**
4. **Take care of decoding the files inside the database.**
5. **If you have limited compute resources, you can take a random 30% of the data.**
6. **Apply appropriate cleaning steps on subtitle documents (whatever is required).**
7. **Experiment with:**
   - BOW / TFIDF to generate sparse vector representations.
   - BERT based “SentenceTransformers” to generate embeddings which encode semantic information.
8. **Document Chunker:**
   - Divide a large document into smaller, more manageable chunks for embedding.
   - Set overlapping windows with a specified amount of tokens to overlap so there are tokens shared between chunks.
9. **Store embeddings in a ChromaDB database.**

### Part 2: Retrieving Documents
1. **Take the user's search query.**
2. **Preprocess the query (if required).**
3. **Create query embedding.**
4. **Using cosine distance, calculate the similarity score between embeddings of documents and user search query embedding.**
5. **These cosine similarity scores will help in returning the most relevant candidate documents as per user’s search query.**
