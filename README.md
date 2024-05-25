# Movie-Genre-Classification

---

# Movie Genre Prediction

This project aims to predict the genres of movies based on their plot summaries using machine learning techniques. The data is derived from two datasets: one containing movie metadata and another containing plot summaries.

## Table of Contents

- [Installation](#installation)
- [Data](#data)
- [Preprocessing](#preprocessing)
- [Model Training](#model-training)
- [Prediction](#prediction)
- [Evaluation](#evaluation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Installation

Clone the repository:

```bash
git clone https://github.com/your_username/movie-genre-prediction.git
cd movie-genre-prediction
```

Install the required packages:

```bash
pip install -r requirements.txt
```

## Data

The project uses two datasets:
1. `movie_metadata.tsv`: Contains metadata of movies.
2. `plot_summaries.tsv`: Contains plot summaries of movies.

Place these datasets in the root directory of the project.

## Preprocessing

The preprocessing steps include:
1. **Loading Data**: Load the datasets into pandas DataFrames.
2. **Merging Data**: Merge the metadata and plot summaries on `movie_id`.
3. **Cleaning Genres**: Convert genre information from JSON format to a list of genres.
4. **Removing Empty Genres**: Remove rows where the genre list is empty.
5. **Text Cleaning**: Clean the plot summaries by removing non-alphabetic characters, converting to lowercase, and removing stopwords.
6. **Stemming**: Apply stemming to the cleaned plot summaries.

## Model Training

1. **Feature Extraction**: Use `TfidfVectorizer` to convert plot summaries into TF-IDF features.
2. **Model**: Train a One-vs-Rest Logistic Regression model on the TF-IDF features.
3. **Threshold Adjustment**: Adjust the probability threshold to improve F1-score.

## Prediction

A function `predict_genre_tags` is provided to predict the genres of a given plot summary. The function preprocesses the text and uses the trained model to predict genres.

## Evaluation

The model's performance is evaluated using the F1-score (micro-average).

## Usage

To predict the genres of a movie plot, you can use the `predict_genre_tags` function:

```python
from predict import predict_genre_tags

plot_summary = "Your plot summary here."
predicted_genres = predict_genre_tags(plot_summary)
print("Predicted genres:", predicted_genres)
```

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request with your changes. Ensure that your code adheres to the project's coding standards.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

### Example Usage

Here's how you can use the `predict_genre_tags` function with a plot summary:

```python
# Example Plot Summaries
plot_summary_1 = "After winning a trip on the RMS Titanic during a dockside card game, American Jack Dawson spots the society girl Rose DeWitt Bukater who is on her way to Philadelphia to marry her rich snob fiancé Caledon Hockley. Rose feels helplessly trapped by her situation and makes her way to the aft deck and thinks of suicide until she is rescued by Jack. Cal is therefore obliged to invite Jack to dine at their first-class table where he suffers through the slights of his snobbish hosts. In return, he spirits Rose off to third-class for an evening of dancing, giving her the time of her life. Deciding to forsake her intended future all together, Rose asks Jack, who has made his living making sketches on the streets of Paris, to draw her in the nude wearing the invaluable blue diamond Cal has given her. Cal finds out and has Jack locked away. Soon afterwards, the ship hits an iceberg and Rose must find Jack while both must run from Cal even as the ship sinks deeper into the freezing water."
predicted_genre_1 = predict_genre_tags(plot_summary_1)
print('Predicted genres:', predicted_genre_1)

plot_summary_2 = "On the lush alien world of Pandora live the Na'vi, beings who appear primitive but are highly evolved. Because the planet's environment is poisonous, human/Na'vi hybrids, called Avatars, must link to human minds to allow for free movement on Pandora. Jake Sully (Sam Worthington), a paralyzed former Marine, becomes mobile again through one such Avatar and falls in love with a Na'vi woman (Zoe Saldana). As a bond with her grows, he is drawn into a battle for the survival of her world."
predicted_genre_2 = predict_genre_tags(plot_summary_2)
print('Predicted genres:', predicted_genre_2)
```

### Author

- Yogesh Thakre (https://github.com/yogeshthakre07)

