# miBooks

miBooks is a book search app that pulls live data from the Open Library API. You can search for any book, filter results by publish year, and save books you want to read later — all stored in your browser.

## What the app does

- Search for books by title, author, or keyword
- Filter results by publish year (before 2000 or 2000 and later)
- Save books to a personal reading list that persists with `localStorage`
- Shows a loading state while the API is fetching and an error message if something goes wrong
- Responsive layout that works on mobile

## No API used

Open Library Search API — https://openlibrary.org/developers/api

No API key required. Data is fetched from `https://openlibrary.org/search.json?q=...`

## Live site

https://pfernandezdecordova1.github.io/miniproject3-miBooks/


## What I learned about working with APIs

This was my first time writing a real `fetch()` call from scratch. The trickiest part was understanding that `fetch()` returns a Promise and that you need `await` twice — once to get the response and once to parse the JSON. I also learned that real API data is messy: some books are missing cover images, some have no publish year, and you have to handle those cases so the page doesn't break.

Using `localStorage` to persist saved books across page reloads was simpler than I expected once I understood `JSON.stringify` and `JSON.parse`.

## Learning Logs

Iteration 1 — Fetch and Display

The Open Library response is a JSON object with a `docs` array. Each item in `docs` is a book with fields like `title`, `author_name` (an array), `first_publish_year`, `subject` (an array), and `cover_i` (a number used to build the cover image URL). I used `console.log(data)` to explore the structure before writing any rendering code.

The trickiest part was understanding `async/await`. I kept getting `[object Promise]` back until I realized I needed to `await response.json()` as a second step. Once that clicked, the rest made sense.

Iteration 2 — Interactivity and Design

I connected the search input to the API by grabbing the value from the text field and passing it into `encodeURIComponent()` before adding it to the URL. I added a year filter that runs on the already-fetched data so it doesn't need a new API call each time.

For layout I used CSS Grid with `auto-fill` and `minmax(220px, 1fr)` so the cards reflow automatically on smaller screens. I added a loading message that shows while `fetch()` is running and swaps out when results arrive.

Iteration 3 — Polish and Extend

I added `localStorage` so saved books stick around after you close the tab. The main edge cases I handled were books with no cover image (shows a placeholder instead), books with no publish year (displays "Year unknown"), and searches that return zero results (shows a friendly message instead of an empty grid).
