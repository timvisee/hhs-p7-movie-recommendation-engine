# Movie suggestor
A Spark/Hadoop application to suggest new movies to watch to a user,
based on a big data set.

The current implementation of the algorithm will follow the pseudologic below:

## Pseudo logic
This logic is custom, therefore it doesn't have a name.
Also, there doesn't seem to be a similar existing algorithm at this time.

Logic:
* Select a user we're going to suggest movies for, we call this user `CLIENT`.
* We're going to calculate the 'agreement value' for other users.
  Iterate over all other users, we'll be calling each other user `COMP`.
    * We'll be giving `COMP` a `COMP_SCORE` to determine the similarity to `CLIENT`.
    * Loop over each movie COMP watched, we'll be calling these movies `MOVIE`.
        * Skip the movie if this movie wasn't watched by `CLIENT`.
        * Calculate the distance between the rating of `CLIENT` and `COMP` on this `MOVIE`. (`|CLIENT_RATING - COMP_RATING| = DISTANCE`)
        * Normalize the distane: (`DISTANCE - MAX_RATING / 2 = DISTANCE_NORM`)
        * Add `DISTANCE_NORM` to `COMP_SCORE`. (`COMP_SCORE += DISTANCE_NORM`)
    * Loop through each `MOVIE`, and give them a `MOVIE_SCORE`.
        * Loop through all other users, we call `COMP`, and use their `COMP_SCORE`.
            * If `COMP` hasn't watched this `MOVIE`, skip.
            * Multiply the rating of COMP for this `MOVIE` by it's `COMP_SCORE` to get `COMP_MOVIE_SCORE`.
            * Append `COMP_MOVIE_SCORE` to the `MOVIE_SCORE`.
    * Sort the list of movies by their `MOVIE_SCORE`.
    * Present this list of movies to the user, as suggestions.

### Logic TODO
* Take movie genres into consideration.
