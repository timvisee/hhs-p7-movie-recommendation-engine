# Movie Recommendation Engine
Our try on a movie recommendation engine in Apache Spark using Jupyter Notebook.

Our implementation uses machine learning which is trained by a given data set.
Then, the system is able to predict ratings a user will give on movies s/he
didn't watch yet.

The script consists of two parts. The first part is the dataset parsing and
machine learning training logic.  
The second part loops through all users to suggest the top 10 movies for them
based on the predicted ratings for that user on movies s/he didn't watch yet.

## Requirements
This project has various requirements:

* Spark with Hadoop, to run the Notebook with the algorithm's code.
* Data files:
    * `movies_full.csv`
    * `movies_small.csv`
    * `ratings_full.csv`
    * `ratings_train.csv`

The data files can be fetched from [movielens](https://grouplens.org/datasets/movielens/).
