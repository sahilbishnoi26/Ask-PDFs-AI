# Ask-PDFs AI

A Streamlit app to upload PDFs, extract content, and ask questions using AI models.

## Features
- Upload multiple PDFs and extract text.
- Split text into chunks for efficient processing.
- Use OpenAI or Hugging Face models for embeddings and LLMs.
  - **Hugging Face**: `flan-t5-base` for language tasks and `hkunlp/instructor-xl` for embeddings.
  - **OpenAI**: GPT-based models for both embeddings and Q&A.
- Semantic search with FAISS for efficient retrieval.
- Conversational Q&A with context-aware responses.

## Technologies Used
- **Streamlit**: For the web interface.
- **LangChain**: Manages conversational chains and retrieval workflows.
- **FAISS**: Enables efficient vector-based similarity search.
- **Hugging Face Transformers**: Provides embeddings and LLM functionality.
- **OpenAI**: Optional alternative for embeddings and Q&A.
- **PyPDF2**: Extracts text from PDFs.

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/ask-pdfs-ai.git
   cd ask-pdfs-ai
   ```
2. Create a virtual environment and install dependencies:
   ```bash
   python -m venv venv
   source venv/bin/activate    # Linux/Mac
   venv\Scripts\activate       # Windows
   pip install -r requirements.txt
   ```
3. Set up environment variables in a `.env` file:
   ```
   HUGGINGFACEHUB_API_TOKEN=your_huggingface_api_token
   OPENAI_API_KEY=your_openai_api_key  # Optional, if using OpenAI models
   ```

## Usage
Run the app:
```bash
streamlit run pdf_chatbbot.py
```
1. Upload PDFs.
2. Select the model (OpenAI or Hugging Face).
3. Ask questions through the interface.
4. Get AI-generated answers.

## License
This project is licensed under the MIT License.
