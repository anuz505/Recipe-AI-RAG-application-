# Recipe AI - RAG Application

A Recipe AI assistant powered by Retrieval-Augmented Generation (RAG) that helps users discover and learn about various dishes from around the world. This application uses semantic search to find relevant recipe information and provides intelligent answers about cooking methods, ingredients, and culinary techniques.

## 🍳 Features

- **Intelligent Recipe Search**: Uses semantic search with sentence transformers to find relevant recipes
- **Multi-LLM Support**: Supports multiple language models via Groq API
- **Interactive Web Interface**: Built with Streamlit for a user-friendly experience
- **Conversation Tracking**: Stores conversations and user feedback in a local database
- **Real-time Monitoring**: Displays response times, relevance scores, and token usage
- **Feedback System**: Users can provide thumbs up/down feedback on responses
- **Recipe Filtering**: Filter conversations by relevance (relevant, partly relevant, non-relevant)

## 🏗️ Architecture

The application follows a RAG (Retrieval-Augmented Generation) architecture:

1. **Data Storage**: Recipe data stored in CSV format with comprehensive dish information
2. **Vector Database**: Pinecone used for semantic search capabilities
3. **Embedding Model**: `all-MiniLM-L6-v2` sentence transformer for encoding queries
4. **LLM Integration**: Groq API for generating contextual responses
5. **Web Interface**: Streamlit for the user-facing application
6. **Database**: PostgreSQL for conversation and feedback storage

## 📁 Project Structure

```
RecipeAI/
├── app/
│   ├── app.py              # Main Streamlit application
│   ├── assistant.py        # RAG logic and LLM integration
│   ├── db.py              # Database operations
│   ├── requirements.txt    # Python dependencies
│   └── course_assistant.db # PostgreSQL database
├── data/
│   ├── clean.csv          # Cleaned recipe dataset
│   ├── unclean_2.csv      # Raw recipe data
│   └── rag-eval-*.csv     # Evaluation results
├── notebooks/
│   ├── generation_and_evaluations_of_retrieval.ipynb
│   └── generation_embeds_and_test.ipynb
└── newenv/                # Virtual environment
```

## 🚀 Quick Start

### Prerequisites

- Python 3.8+
- Pinecone API key
- Groq API key

### Installation

1. **Clone the repository**

   ```bash
   git clone <repository-url>
   cd RecipeAI
   ```

2. **Set up virtual environment**

   ```bash
   python -m venv newenv
   newenv\Scripts\activate  # On Windows
   # source newenv/bin/activate  # On macOS/Linux
   ```

3. **Install dependencies**

   ```bash
   cd app
   pip install -r requirements.txt
   ```

4. **Environment Configuration**
   Create a `.env` file in the root directory:

   ```env
   GROQ_API_KEY=your_groq_api_key_here
   PINECONE_API_KEY=your_pinecone_api_key_here
   PINECONE_INDEX_NAME=semantic-search
   ```

5. **Run the application**

   ```bash
   streamlit run app.py
   ```

6. **Access the application**
   Open your browser and navigate to `http://localhost:8501`

## 🔧 Configuration

### Environment Variables

- `GROQ_API_KEY`: Your Groq API key for LLM access
- `PINECONE_API_KEY`: Your Pinecone API key for vector database
- `PINECONE_INDEX_NAME`: Name of your Pinecone index (default: "semantic-search")

### Model Configuration

The application uses:

- **Embedding Model**: `all-MiniLM-L6-v2` (can be changed in `assistant.py`)
- **LLM Provider**: Groq (currently the only supported provider)
- **Vector Database**: Pinecone for semantic search

## 📊 Data

The application works with a comprehensive recipe dataset containing:

- **Recipe Name**: Name of the dish
- **Country**: Origin country of the recipe
- **Ingredients**: List of required ingredients
- **Instructions**: Step-by-step cooking instructions
- **Meal Type**: Main course, side dish, etc.
- **Spice Level**: Heat level of the dish
- **Cooking Time**: Time required in minutes
- **Vegetarian**: Whether the dish is vegetarian
- **Cooking Method**: Primary cooking technique
- **Serving Temperature**: Hot, cold, or room temperature

## 🎯 Usage

1. **Ask Questions**: Type recipe-related questions in the input field
2. **Get Answers**: The AI will search for relevant recipes and provide detailed answers
3. **Monitor Performance**: View response times, relevance scores, and token usage
4. **Provide Feedback**: Use thumbs up/down buttons to rate responses
5. **Browse History**: View recent conversations and filter by relevance

### Example Questions

- "How do I make Ethiopian Doro Wat?"
- "What are some spicy Indian dishes?"
- "Show me vegetarian recipes from Italy"
- "What ingredients do I need for sushi?"

## 🔍 Evaluation

The project includes Jupyter notebooks for:

- **Retrieval Evaluation**: Testing the effectiveness of semantic search
- **Generation Quality**: Evaluating LLM response quality
- **Performance Metrics**: Analyzing response times and relevance scores

## 🛠️ Development

### Adding New Features

1. **New LLM Providers**: Extend the `qa_function` in `assistant.py`
2. **Database Schema**: Modify `db.py` for new data fields
3. **UI Components**: Update `app.py` for interface changes

### Running Tests

```bash
# Run evaluation notebooks
jupyter notebook notebooks/generation_and_evaluations_of_retrieval.ipynb
```

## 📈 Monitoring

The application provides real-time monitoring:

- **Response Time**: Time taken to generate answers
- **Relevance Score**: Semantic similarity score
- **Token Usage**: Number of tokens consumed
- **Feedback Statistics**: User satisfaction metrics

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🐛 Troubleshooting

### Common Issues

1. **Pinecone Connection Error**

   - Verify your API key and index name
   - Check if the index exists in your Pinecone dashboard

2. **Groq API Issues**

   - Ensure your API key is valid
   - Check API rate limits

3. **Database Errors**
   - Delete `course_assistant.db` to reset the database
   - Ensure proper write permissions

## 🔮 Future Enhancements

- Support for more LLM providers (OpenAI, Anthropic)
- Recipe image generation
- Nutritional information integration
- Multi-language support
- Advanced filtering options
- Recipe recommendation system

---

Built with ❤️ using Streamlit, Pinecone, and Groq
