# MoviesDatabase API

## API Overview
The MoviesDatabase API provides comprehensive and up-to-date information on over 9 million titles (movies, series, and episodes) and 11 million actors, crew, and cast members. It includes trailers, awards, biographies, ratings, seasons, episodes, and much more. The API is designed to help developers access structured entertainment data efficiently.

## API Version
Version: 1.0

## Available Endpoints

### Titles
- **`/titles`** – Retrieve an array of titles filtered and sorted using query parameters.  
- **`/x/titles-by-ids`** – Retrieve multiple titles using an array of IMDb IDs.  
- **`/titles/{id}`** – Retrieve details of a specific title using its IMDb ID.  
- **`/titles/{id}/ratings`** – Retrieve ratings and number of votes for a title.  
- **`/titles/series/{id}`** – Retrieve all episodes for a series.  
- **`/titles/seasons/{id}`** – Retrieve the total number of seasons for a series.  
- **`/titles/series/{id}/{season}`** – Retrieve episodes for a specific season.  
- **`/titles/episode/{id}`** – Retrieve details of a specific episode.  
- **`/titles/x/upcoming`** – Retrieve upcoming titles.  

### Search
- **`/titles/search/keyword/{keyword}`** – Search titles by keyword.  
- **`/titles/search/title/{title}`** – Search titles by title or partial title (`exact` query optional).  
- **`/titles/search/akas/{aka}`** – Search titles by AKA (exact, case-sensitive).  

### Actors
- **`/actors`** – Retrieve a list of actors (supports `limit` and `page`).  
- **`/actors/{id}`** – Retrieve details of a specific actor by IMDb ID.  

### Utils
- **`/title/utils/titleType`** – Retrieve available title types.  
- **`/title/utils/genres`** – Retrieve available genres.  
- **`/title/utils/lists`** – Retrieve predefined lists for the `list` query parameter.  

## Query Parameters
- **info**: `STRING` – default `mini_info`. Options: `base_info`, `mini_info`, `image`, `creators_directors_writers`, `revenue_budget`, `extendedCast`, `rating`, `awards`, or any key of the title object.  
- **limit**: `NUMBER` – default `10`, max `50`. Number of results per page.  
- **page**: `NUMBER` – default `1`. Pagination page number.  
- **titleType**: `STRING` – filter by type, options from `/title/utils/titleType`.  
- **startYear / endYear**: `NUMBER` – filter by release year range.  
- **year**: `NUMBER` – filter by exact release year (cannot be combined with startYear/endYear).  
- **genre**: `STRING` – filter by genre (case-sensitive, options from `/title/utils/genres`).  
- **sort**: `STRING` – options: `year.incr` (ascending), `year.decr` (descending).  
- **exact**: `BOOLEAN` – only for title search, default `false`.  
- **list**: `STRING` – predefined lists, max 50 entries. Options: `titles`, `most_pop_movies`, `most_pop_series`, `top_boxoffice_200`, `top_boxoffice_last_weekend_10`, `top_rated_250`, `top_rated_english_250`, `top_rated_lowest_100`, `top_rated_series_250`.  

## Request and Response Format
- **Request Example**:
```http
GET /titles?limit=5&genre=Action&sort=year.decr
Host: api.moviesdatabase.com
Authorization: Bearer YOUR_API_KEY
