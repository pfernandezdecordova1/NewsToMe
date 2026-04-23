# PROPOSAL.md — miBooks

## What I'm building
A book search app called miBooks that lets users search for books by title or keyword, filter results by publish year, and save their favorites to come back to later.

## Which API I'm using
Open Library Search API
https://openlibrary.org/developers/api

I opened the API in the browser before writing any code. A search for "harry potter" returns a JSON object with a `docs` array where each book has fields like `title`, `author_name`, `first_publish_year`, `subject`, and `cover_i` (used to build the cover image URL).

## Why I chose this
I wanted something I could actually use. I read a lot and I never have a good place to quickly look up a book and save it for later. Open Library also has no API key requirement which means it works on GitHub Pages without any setup, and the JSON response was easy enough to understand just by looking at it in the browser.

## Core features
1. Search for books by title, author, or keyword using `fetch()`
2. Display results dynamically as cards with cover image, author, year, and subject
3. Filter results by publish year (all, before 2000, 2000 and later)
4. Save favorite books to a personal reading list using `localStorage`
5. Responsive card grid that works on mobile and desktop

## What I don't know yet
- How `async` and `await` actually work under the hood — I've seen it before but never written it myself from scratch
- How to read a `fetch()` response and pull out the right fields from the JSON
- What to do if the API takes too long or returns an empty result
- How to keep JavaScript organized when the code starts getting longer