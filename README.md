# TM DB

Scripts that help to store the movie database locally.

You can download info from a site [themoviedb.org](https://www.themoviedb.org/) and then use search by name or use a similar search.

## Prepare your environment

Be sure that you have Python 3 installed and if not download it from the official site [python.org](https://python.org).

```bash
python --version
#>Python 3.9.6
```

Activate a virtual environment.

```bash
python -m venv venv
. ./venv/bin/activate
# For Windows
# . .\venv\Scripts\activate
```

Install dependencies.

```bash
pip install -r requirements.txt
```

API Key can be got from the site [themoviedb.org](https://www.themoviedb.org/) after registration.
Detailed instruction is available [here](https://developers.themoviedb.org/3/getting-started/introduction).

Save this API Key in a secret place - you will need it for scripts.

## make_own_db.py

To start working with movies DB you should download it and store locally using the `make_own_db.py` script.

`make_own_db.py` script helps to download data.

```bash
python make_own_db.py
```

As a result, file `MyFilmDB.json` will be placed near your script.

Please note, that only 1000 records will be downloaded.

After that, we can go to one of the next scripts either `search_in_db.py` or `find_similar.py`. _About them below_.

## search_in_db.py

Script searches film by original title (or part of the title).

```bash
python.exe search_in_db.py
>Enter path to DataBase:MyFilmDB.json
>Enter film to search for:Life
Life in Loops (A Megacities RMX)
```

## find_similar.py

The script searches for similar movies by exact title.

Similarities are defined by the following parameter with weights:

|Parameter|Weight|
|-|-|
|Belongs to the same collection|1000|
|Genre|500|
|Original language|300|
|Budget|100|

Maximum Top 8 movies will be displayed.

```bash
python.exe find_similar.py
>Enter path to DataBase:MyFilmDB.json
>Enter film to search for:Life in Loops (A Megacities RMX)
Ariel
Four Rooms
Judgment Night
Sonntag im August
Varjoja paratiisissa
```

## Supporting scripts

### tmbd_helpers.py

Set of functions to work with [TMDB API](https://api.themoviedb.org).

### hello_api_TMDB.py

Script to check API key. Requests tmdb API with provided API Key.

If everything is OK you will see the budget for the movie "Saw II".

```bash
python hello_api_TMDB.py
4000000
```

### own_db_helpers.py

Contains a function to work with local DB.
