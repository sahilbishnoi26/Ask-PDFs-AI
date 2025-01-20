# Ask-PDFs AI

Ask-PDFs AI is a Streamlit application that allows users to upload multiple PDF documents, extract their content, and interact with it through a conversational AI. The system combines advanced natural language processing (NLP) models with vector-based search techniques to provide accurate and context-aware answers.

---

## Features

1. **PDF Text Extraction**:
   - Uses `PyPDF2` to extract text from uploaded PDF files.
   - Handles multi-page PDFs and merges text from multiple documents.

2. **Chunking and Vectorization**:
   - Splits extracted text into manageable chunks using `LangChain`'s `CharacterTextSplitter`.
   - Converts text chunks into embeddings using `Hugging Face Transformers` models such as `hkunlp/instructor-xl`.

3. **Efficient Retrieval**:
   - Leverages `FAISS` (Facebook AI Similarity Search) for indexing and searching through text embeddings.
   - Ensures fast and accurate retrieval of relevant document sections.

4. **Conversational AI**:
   - Uses Hugging Face models (e.g., `flan-t5-xxl`) for answering user questions based on retrieved document content.
   - Implements a conversational retrieval chain via `LangChain` for interactive Q&A.

5. **Streamlit UI**:
   - Provides an intuitive interface for uploading PDFs, asking questions, and viewing responses.
   - Displays extracted text and retrieval process details for transparency.

---

## Technical Details

### **1. Text Processing**
- Extracts text using `PyPDF2` with page-by-page parsing.
- Splits the text into chunks of 1000 characters with 200-character overlap to maintain context.

### **2. Embedding Generation**
- Generates dense vector embeddings for text chunks using Hugging Face models like `hkunlp/instructor-xl`.
- Supports customization of embedding models for specific tasks.

### **3. Vector Storage and Search**
- Indexes embeddings using FAISS for similarity-based search.
- Retrieves the most relevant text chunks based on cosine similarity.

### **4. Conversational Chain**
- Combines document retrieval and language model inference using `LangChain`.
- Chains include:
  - **Retrieval**: Selects the top relevant chunks.
  - **LLM Processing**: Summarizes or generates answers based on retrieved chunks.

### **5. Model Integration**
- Default LLM: `google/flan-t5-xxl` (can be replaced with smaller models like `flan-t5-base` for lower resource requirements).
- Supports both CPU and GPU execution.

---

## Prerequisites

1. **Python**: Version 3.8 or later.
2. **Hugging Face API Token**: Required for accessing Hugging Face models. [Get your token here](https://huggingface.co/settings/tokens).

---

## Installation

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/ask-pdfs-ai.git
cd ask-pdfs-ai
```

### 2. Set Up the Environment
```bash
python -m venv venv
source venv/bin/activate    # Linux/Mac
venv\Scripts\activate       # Windows
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Configure Environment Variables
Create a `.env` file with:
```
HUGGINGFACEHUB_API_TOKEN=your_huggingface_api_token
OPENAI_API_KEY=your_openai_api_key (optional)
```

---

## Usage

### Start the App
Run the Streamlit app:
```bash
streamlit run app_update.py
```

### Steps:
1. Upload one or more PDF files via the interface.
2. Enter a question about the content.
3. View AI-generated responses.

---

## Troubleshooting

### Common Issues
1. **API Token Missing**:
   Ensure the Hugging Face API token is properly set in the `.env` file or as an environment variable.

2. **CUDA Out of Memory**:
   - Switch to a smaller model like `flan-t5-base` or `flan-t5-large`.
   - Run the model on the CPU by removing GPU dependencies.

3. **FAISS Warnings**:
   Install FAISS with AVX2 support for optimized performance:
   ```bash
   pip install faiss-cpu
   ```

4. **Debugging Environment Variables**:
   Check if the variables are loaded:
   ```python
   import os
   print(os.getenv("HUGGINGFACEHUB_API_TOKEN"))
   ```

---

## Technologies Used
- **Streamlit**: Interactive user interface.
- **LangChain**: Framework for building chains with retrieval and language models.
- **FAISS**: Vector similarity search for efficient text retrieval.
- **Hugging Face Transformers**: State-of-the-art NLP models for embeddings and question answering.
- **PyPDF2**: Text extraction from PDFs.

---

## Roadmap
- Add support for other document formats like Word and Excel.
- Explore fine-tuning of Hugging Face models for better contextual Q&A.
- Optimize retrieval with dynamic chunking and semantic segmentation.

---

## License
This project is licensed under the MIT License.

---

## Acknowledgments
- Hugging Face for providing powerful pretrained models.
- FAISS for enabling scalable vector search.
- LangChain for simplifying conversational AI workflows.
