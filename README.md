# Chat-with-PDF

This project provides a "Chat with PDF" application that allows users to upload a PDF file and ask questions about its content. The application leverages an AI model to find relevant sections within the PDF and generate answers based on those sections.

---

## Features

* **PDF Text Extraction**: Extracts text content from uploaded PDF files.
* **Text Chunking**: Splits the extracted text into manageable chunks for processing.
* **Text Embedding**: Converts text chunks and user queries into numerical embeddings using a pre-trained sentence transformer model.
* **Semantic Search**: Identifies the most semantically similar text chunks to the user's query within the PDF.
* **AI-Powered Question Answering**: Generates answers to user questions based on the relevant PDF content using the Gemini API.
* **Gradio Interface**: Provides a user-friendly web interface for easy interaction.

---

## Technologies Used

* Python
* Google Generative AI (Gemini API)
* Gradio
* PyPDF2
* Sentence-Transformers (specifically "all-MiniLM-L6-v2" model)
* Scikit-learn (for cosine similarity)
* NumPy

---

## Setup and Installation

To set up and run this project locally, follow these steps:

1.  **Clone the repository (if applicable):**
    ```bash
    git clone https://github.com/Sankrityayana/Chat-with-PDF
    cd Chat-with-PDF
    ```

2.  **Install the required libraries:**
    ```bash
    pip install gradio PyPDF2 sentence-transformers scikit-learn numpy
    pip install -q -U google-genai
    ```

3.  **Obtain a Gemini API Key:**
    * Go to the [Google AI Studio](https://aistudio.google.com/app/apikey).
    * Generate an API key.

4.  **Configure your API Key:**
    * Open the `chat_with_pdf.ipynb` file.
    * Locate the line `client = genai.Client(api_key="Enter your gemini api key here")`.
    * Replace `"Enter your gemini api key here"` with your actual Gemini API key.

---

## Usage

1.  **Run the Jupyter Notebook:**
    ```bash
    jupyter notebook chat_with_pdf.ipynb
    ```

2.  **Launch the Gradio Application:**
    * Once the notebook is open, run all the cells.
    * The last cell will launch the Gradio interface, providing a public URL.

3.  **Interact with the Application:**
    * Open the provided URL in your web browser.
    * **Upload PDF**: Click on the "Upload PDF" section and select the PDF file you want to chat with.
    * **Ask a Question**: Type your question related to the PDF content in the "Ask a question about the PDF" textbox.
    * The AI will process your request and display the answer in the output section.

---

## How it Works

The application performs the following steps:
1.  **PDF Extraction and Chunking**: The `extract_text_chunks` function reads the uploaded PDF and splits its content into smaller chunks (default chunk size is 500 characters).
2.  **Embedding Generation**: The `embed_chunks` function generates vector embeddings for each text chunk using the "all-MiniLM-L6-v2" Sentence Transformer model.
3.  **Query Embedding**: When a user asks a question, its embedding is generated.
4.  **Semantic Search**: The `search_chunks` function calculates the cosine similarity between the query embedding and all chunk embeddings to find the top 3 most similar chunks.
5.  **Answer Generation**: These top chunks are then used as context for a prompt sent to the `gemini-2.5-flash` model via the Gemini API, which generates a coherent answer to the user's question.

---

## License

[Add your license information here, e.g., MIT License]
