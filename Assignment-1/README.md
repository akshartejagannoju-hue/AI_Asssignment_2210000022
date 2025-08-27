# Movie Semantic Search Assignment

This repository contains my solution for the semantic search on movie plots assignment.

## Project Overview

This project implements a semantic search engine for movie plots using SentenceTransformers with the all-MiniLM-L6-v2 model. The system converts movie plot descriptions into embeddings and uses cosine similarity to find the most semantically similar movies to a given query.

## Features

- **Semantic Search**: Uses advanced language models to understand the meaning behind queries
- **Cosine Similarity**: Implements similarity scoring between 0 and 1
- **Flexible Results**: Configurable number of top results (top_n parameter)
- **Automatic Embeddings**: Creates embeddings for all movie plots on initialization

## Setup

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-username/movie-search-assignment.git
   cd movie-search-assignment/assignment_1
   ```

2. **Create virtual environment**:
   ```bash
   python -m venv venv
   ```

3. **Activate virtual environment**:
   - Windows: `venv\Scripts\activate`
   - macOS/Linux: `source venv/bin/activate`

4. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

5. **Run the notebook**:
   ```bash
   jupyter notebook movie_search_results.ipynb
   ```

## Testing

Run the unit tests to verify everything works correctly:

```bash
python -m unittest tests/test_movie_search.py -v
```

Expected output: All 4 tests should pass:
- ✅ test_search_movies_output_format
- ✅ test_search_movies_relevance  
- ✅ test_search_movies_similarity_range
- ✅ test_search_movies_top_n

## Usage

### Python Script
```python
from movie_search import search_movies

# Search for movies
results = search_movies("spy thriller in Paris", top_n=3)
print(results)
```

### Jupyter Notebook
Open `movie_search_solution.ipynb` and run the cells sequentially to:
1. Import libraries
2. Load the dataset
3. Create embeddings
4. Implement and test the search function

## Example Query

Test the function with the required query:
```python
search_movies('spy thriller in Paris')
```

**Expected Results**:
1. **Spy Movie** - "A spy navigates intrigue in Paris to stop a terrorist plot." (Similarity: ~0.77)
2. **Romance in Paris** - "A couple falls in love in Paris under romantic circumstances." (Similarity: ~0.39)
3. **Action Flick** - "A high-octane chase through New York with explosions." (Similarity: ~0.26)

## Implementation Details

### Section (a): Install and Import Libraries
- sentence-transformers: For creating embeddings
- pandas: For data manipulation
- scikit-learn: For cosine similarity calculations
- numpy: For numerical operations

### Section (b): Load Movies Dataset
- Loads `movies.csv` into a pandas DataFrame
- Handles the movie titles and plot descriptions

### Section (c): Create Embeddings
- Uses all-MiniLM-L6-v2 model (384-dimensional embeddings)
- Converts all movie plots to embeddings for similarity search

### Section (d): Implement Search Function
- `search_movies(query, top_n=5)` function
- Returns DataFrame with columns: title, plot, similarity
- Results sorted by similarity score (descending)

### Section (e): Test with Query
- Tests the function with "spy thriller in Paris"
- Demonstrates semantic understanding and ranking

## Files Structure

```
assignment_1/
├── movie_search.py              # Main implementation
├── movie_search_solution.ipynb  # Jupyter notebook version
├── movies.csv                   # Sample movie dataset
├── requirements.txt             # Python dependencies
├── tests/
│   └── test_movie_search.py    # Unit tests
└── README.md                    # This file
```

## Dependencies

- sentence-transformers==5.1.0
- pandas
- scikit-learn
- numpy

## License

This project is part of the AI Systems Development assignment at IIIT Naya Raipur.
