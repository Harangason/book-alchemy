# Book Alchemy

Flask library app for managing fantasy books, authors, ratings, search, sorting, detail pages, and delete/edit flows.

## Features

- Add authors with name, birth date, and date of death.
- Add books with ISBN, title, publication date, author, and rating from 1 to 10.
- Show the library on the home page with title, author, rating, and OpenLibrary cover image.
- Sort books by title or author.
- Search books by title using a SQL `LIKE` query.
- Open detail pages for books and authors.
- Edit books, including author, date, ISBN, title, and rating.
- Delete books from the library.
- Delete authors and cascade-delete their books.

## Project Structure

```text
book-alchemy-de/
  app.py
  data/
    data_models.py
    library.sqlite
  static/
    css/
      add_author.css
      add_book.css
      detail.css
      edit_book.css
      home.css
  templates/
    add_author.html
    add_book.html
    author_detail.html
    book_detail.html
    edit_book.html
    home.html
  test_app.py
```

## Run

```powershell
.\.venv\Scripts\python.exe app.py
```

If the app is run from an IDE, use `app.py` as the Flask entry file.

## Important Routes

- `/` — library home page.
- `/add_author` — add an author.
- `/add_book` — add a book.
- `/book/<book_id>` — book detail page.
- `/book/<book_id>/edit` — edit a book.
- `/book/<book_id>/delete` — delete a book with `POST`.
- `/author/<author_id>` — author detail page.
- `/author/<author_id>/delete` — delete an author and their books with `POST`.

## Tests

```powershell
.\.venv\Scripts\python.exe -m unittest -q
```

## Notes

- The local SQLite database is stored at `data/library.sqlite`.
- Runtime/cache files and local database files are ignored by Git.
- Book recommendation uses RapidAPI via the RAPIDAPI_KEY environment variable. Do not commit API keys.

## RapidAPI Recommendation

The recommendation page is available at `/recommendation`.

Set the key outside Git before generating recommendations:

```powershell
$env:RAPIDAPI_KEY = "your-key"
```

Alternatively, create an ignored `.env.local` file with `RAPIDAPI_KEY=...`.
