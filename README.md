# Mastering PWA Fundamentals

## Learning Objectives

- Understand API documentation and integration
- Implement TypeScript interfaces for API responses
- Create reusable React components
- Build a responsive layout with Tailwind CSS
- Manage application state for filtering and pagination
- Implement proper error handling and loading states
- Set up Next.js API routes for server-side data fetching
- Manage environment variables for API keys

---

## Project Description

**CineSeek** is a modern movie discovery web application built with **Next.js**, **TypeScript**, and **Tailwind CSS**.  
Users can:
- Browse movies from the **MoviesDatabase API**
- View detailed movie information
- Filter and search by year or genre

The project emphasizes clean architecture, strong API integration, and responsive design.

---

## API Overview

The **MoviesDatabase API** offers data on:
- **9+ million** titles (movies, series, episodes)
- **11+ million** actors, cast, and crew
- YouTube trailers, awards, bios, and more

---

## Version

- **v1 (Current)**

---

## Available Endpoints

### Titles

- `GET /titles`  
  Returns an array of titles using filters/sorting

- `POST /x/titles-by-ids`  
  Returns titles matching an array of provided IDs

- `GET /titles/{id}`  
  Returns details of a specific title

- `GET /titles/{id}/ratings`  
  Returns rating and vote count

- `GET /titles/series/{id}`  
  Lists episodes of a series

- `GET /titles/seasons/{id}`  
  Returns number of seasons

- `GET /titles/series/{id}/{season}`  
  Returns episodes of a given season

- `GET /titles/episode/{id}`  
  Returns details of a specific episode

- `GET /titles/x/upcoming`  
  Lists upcoming titles

---

### Search

- `GET /titles/search/keyword/{keyword}`
  Returns array of titles according to filters / sorting query parameters provided and the keyword provided in path
  
- `GET /titles/search/title/{title}`
  Returns array of titles according to filters / sorting query parameters provided and the title provided in path
  
- `GET /titles/search/akas/{aka}`
  Returns array of titles according to filters / sorting query parameters provided and the aka provided in path, work only for exact matches

---

### Actors

- `GET /actors`
  Returns array of actors according to filters provided
  
- `GET /actors/{id}`
   Returns actor details
  

---

###  Utils

- `GET /title/utils/titleType`
  Returns array of title types
  
- `GET /title/utils/genres`
  Returns array of genres

- `GET /title/utils/lists`
   Returns array of lists (for 'list' query parameter)

---

## Request and Response Format

### Headers

```http
x-rapidapi-host: moviesdatabase.p.rapidapi.com
x-rapidapi-key: YOUR_API_KEY
```

#### Example Request
```bash
GET https://moviesdatabase.p.rapidapi.com/titles
```

#### Example Response
```json
{
  "results": [
    {
      "id": "tt1234567",
      "titleText": { "text": "Example Movie" },
      "releaseYear": { "year": 2023 },
      "ratingsSummary": {
        "aggregateRating": 7.6,
        "voteCount": 15230
      }
    }
  ]
}
```

## Authentication
To access the API, you need an API key from RapidAPI.

Steps:
Sign up or log in to RapidAPI

Subscribe to the MoviesDatabase API

Copy your API Key

Add it to the request headers:

```h
x-rapidapi-key: YOUR_API_KEY
x-rapidapi-host: moviesdatabase.p.rapidapi.com
```
In a Next.js project, store it in your .env.local file:

```env
NEXT_PUBLIC_RAPID_API_KEY=your_api_key_here
Access it via process.env.NEXT_PUBLIC_RAPID_API_KEY.
```

## Error Handling
Common Errors:
401 Unauthorized – Missing or invalid API key

429 Too Many Requests – Rate limit exceeded

404 Not Found – Invalid path or resource ID

500 Internal Server Error – API server error


## Usage Limits and Best Practices
Rate Limits:
Free tier usually includes 100–500 requests/month

Surpassing the limit returns a 429 status

Recommendations:
Cache results to avoid duplicate requests

Debounce search input

Use pagination for large data sets

Never hard-code your API key in the frontend

Write TypeScript interfaces to handle responses safely

---

## References
[MoviesDatabase API on RapidAPI](https://rapidapi.com/SAdrian/api/moviesdatabase)
