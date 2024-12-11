# LLM-based Project with LangChain

## Overview
This project demonstrates the implementation of a Language Learning Model (LLM) pipeline using LangChain. It uses embeddings and vector databases for semantic search and question answering based on a scraped dataset from the following source:

[GeeksforGeeks - What is Generative AI?](https://www.geeksforgeeks.org/what-is-generative-ai/)

## Features
- **Embedding Model**: `sentence-transformers/all-MiniLM-L6-v2` via HuggingFaceEmbeddings.
- **LLM Model**: `google/flan-t5-small` via HuggingFaceHub.
- **Vector Database**: FAISS (using the CPU version `faiss-cpu`).
- **Environment Configuration**: All sensitive information is stored in environment variables.

## Prerequisites
1. Python 3.10 or above.
2. Required Python libraries:
   - `langchain`
   - `sentence-transformers`
   - `faiss-cpu`
   - `huggingface_hub`
3. A Hugging Face account and an API token.

## Setup Instructions

### Step 1: Clone the Repository
```bash
# Clone the repository
git clone <your-repo-url>
cd <your-repo-directory>
```

### Step 2: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 3: Configure Environment Variables
1. Copy the `.env.test` file:
   ```bash
   cp .env.test .env
   ```
2. Replace placeholder values in the `.env` file with your actual credentials:
   - `HUGGINGFACEHUB_API_TOKEN`: Your Hugging Face API token.
   - Other configurations as needed for your local environment.

### Step 4: Run the Application
```bash
python app.py
```

## How It Works
1. **Data Source**: The dataset is scraped from the given GeeksforGeeks article.
2. **Embedding Generation**:
   - `sentence-transformers/all-MiniLM-L6-v2` creates embeddings for text chunks.
3. **Vector Database**:
   - FAISS is used to store and retrieve embeddings for semantic search.
4. **LLM Query**:
   - `google/flan-t5-small` is used to generate answers based on the retrieved context.

## Key Components
- **`HuggingFaceHub`**: Utilized for both embedding and LLM models. Ensure that your Hugging Face API token is valid and authorized to access these models.
- **FAISS**: Efficiently indexes the embeddings and supports fast similarity search.

## Notes
- Ensure `faiss-cpu` is installed for the vector database.
- If you encounter API rate limits or invalid token errors, verify your Hugging Face token and consider upgrading your account if needed.

## Example Usage
### Query Example
- Question: "What is generative AI?"
- Pipeline:
  1. The question is embedded using `all-MiniLM-L6-v2`.
  2. Relevant chunks are retrieved from the FAISS vector database.
  3. `google/flan-t5-small` generates an answer based on the retrieved context.

### Output
```text
Generative AI refers to artificial intelligence models capable of generating new content, such as text, images, or music, based on learned patterns from large datasets.
```

## Contributing
Feel free to fork this repository and submit pull requests for any improvements or bug fixes. For major changes, please open an issue to discuss your ideas first.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

---
Happy coding! 🚀

