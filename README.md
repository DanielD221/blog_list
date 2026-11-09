# Blog List API

A small REST API for saving links to blog posts, built with Node.js, Express, and MongoDB as part of Full Stack Open coursework.

Each entry contains a title, author, URL, and like count. This repository contains the standalone backend; the later version with user accounts and a React interface lives in [fullstackopen](https://github.com/DanielD221/fullstackopen).

## Features

- List all blogs or retrieve one by ID.
- Create, update, and delete blog entries.
- Reject new entries without a title or URL.
- Store data with Mongoose and return clean JSON identifiers.
- Log requests and handle malformed IDs and unknown routes.

## Run locally

Use Node.js 24 and npm, with a running MongoDB instance or a MongoDB Atlas database.

```sh
npm ci
```

Create a `.env` file in the repository root:

```dotenv
PORT=3003
MONGODB_URI=mongodb://127.0.0.1:27017/blog_list
```

```sh
npm run dev
```

The API is available at `http://localhost:3003/api/blogs`. Use `npm start` to run without file watching.

## API

| Method | Path | Purpose |
| --- | --- | --- |
| GET | `/api/blogs` | List blogs |
| GET | `/api/blogs/:id` | Retrieve a blog |
| POST | `/api/blogs` | Create a blog |
| PUT | `/api/blogs/:id` | Update a blog |
| DELETE | `/api/blogs/:id` | Delete a blog |

Example request body for creating a blog:

```json
{
  "title": "A useful article",
  "author": "Example Author",
  "url": "https://example.com/article",
  "likes": 0
}
```

## Structure

- `app.js` — Express configuration and MongoDB connection.
- `index.js` — HTTP server entry point.
- `controllers/blogs.js` — API routes.
- `models/blog.js` — Mongoose model.
- `utils/` — configuration, logging, and middleware.

## Development status

Run `npm run lint` for ESLint. There is no automated test script in this standalone repository.

This is a coursework backend. It does not implement authentication or access control. The app can serve a `dist/` directory, but no frontend source or built frontend is included here.
