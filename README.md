# Movie Recommendation System

## Overview

This project implements a movie recommendation system using a content-based approach. By leveraging textual data from movie descriptions and tags, it generates recommendations for similar movies based on cosine similarity. The system uses the TMDB (The Movie Database) dataset, which includes various movie attributes, to provide tailored movie suggestions.

## Features

- **Content-Based Recommendations**: Suggests similar movies based on their content (tags and descriptions).
- **Preprocessing**: Handles missing values, duplicates, and text preprocessing.
- **Similarity Calculation**: Uses cosine similarity to measure the similarity between movie vectors.

## Data

The dataset used in this project is sourced from TMDB, which includes two files that were concatenated based on movie titles. The final dataset has 23 columns, from which the following columns were used for the recommendation system:

- `title`
- `tags`
- `description`

## Methodology

1. **Data Concatenation**: Combined two TMDB dataset files based on movie titles.
2. **Data Preprocessing**:
   - Handled missing values and duplicates.
   - Extracted relevant information from columns.
   - Performed text preprocessing (e.g., lowercasing, stemming, removing stop words).
3. **Feature Extraction**:
   - Extracted features from the `tags` and `description` columns.
   - Vectorized the textual data using techniques such as Bag of Words.
4. **Similarity Calculation**:
   - Applied cosine similarity to determine how similar each movie is to every other movie.
5. **Recommendation**:
   - Created a function to recommend similar movies based on the cosine similarity scores.

## Installation

To get started with this project, you'll need to have Python installed along with the following libraries:

- `pandas`
- `scikit-learn`
- `numpy`

You can install the required libraries using pip:

```bash
pip install pandas scikit-learn numpy
```

## Usage

1. **Load the Dataset**: Ensure that you have the TMDB dataset files and load them into your script.
2. **Preprocess Data**: Run the preprocessing steps to clean and prepare the data.
3. **Train the Model**: Convert textual data into vectors and compute cosine similarity.
4. **Make Recommendations**: Use the `recommend(movie)` function to get similar movie recommendations.

### Example

Here's an example of how to use the `recommend(movie)` function:

```python
def recommend(movie):
    if movie not in data["title"].values:
        print(f"Movie '{movie}' not found in the dataset.")
        return

    movie_index = data[data["title"] == movie].index[0]
    distances = similarity[movie_index]
    movies_list = sorted(list(enumerate(distances)), reverse=True, key=lambda x: x[1])[1:7]

    for key, value in enumerate(movies_list):
        print(f"The Similar Movie from '{movie}' is: {data.iloc[value[0]]['title']}")
```

![Data Overview](Pictures/image_1.png)

Replace `data` with your DataFrame containing movie information and `similarity` with the cosine similarity matrix.

## Contributing

Feel free to contribute to this project by submitting pull requests, reporting issues, or suggesting improvements. Please follow standard GitHub practices and provide clear descriptions of your changes.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact

For any questions or feedback, please reach out to Waris Hayat at warishayat666@gmail.com.

