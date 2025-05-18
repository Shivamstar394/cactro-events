# cactro-events
# YouTube Mini-Dashboard

## Overview  
This is a Next.js application that connects with the YouTube API to allow users to manage one of their uploaded unlisted videos in detail. Features include viewing video details, commenting and replying on comments, updating video title and description, deleting comments, and maintaining searchable notes related to the video.

## Features  
- Display video details fetched via YouTube API  
- Add, reply to, and delete comments  
- Update video title and description  
- Notes section with tagging and search functionality (stored in MongoDB)  
- Event logging of user actions stored in MongoDB  
- Authentication via Google OAuth using NextAuth.js

## Technologies Used  
- Next.js (React framework)  
- NextAuth.js for authentication  
- YouTube Data API v3  
- MongoDB for storing comments, notes, and logs  
- Mongoose for MongoDB object modeling

## API Endpoints  

| Method | Endpoint              | Description                      |
|--------|-----------------------|--------------------------------|
| GET    | `/api/video`          | Fetch video details             |
| PUT    | `/api/video`          | Update video title & description|
| POST   | `/api/comments`       | Add a new comment               |
| POST   | `/api/comments/reply` | Reply to an existing comment    |
| DELETE | `/api/comments/:id`   | Delete a comment                |
| GET    | `/api/notes`          | Retrieve notes with optional search |
| POST   | `/api/notes`          | Create a new note              |
| PUT    | `/api/notes/:id`      | Update a note                   |
| DELETE | `/api/notes/:id`      | Delete a note                  |
| GET    | `/api/logs`           | Retrieve event logs             |

## Database Schema

- **Comments**  
  - `_id`: ObjectId  
  - `videoId`: string  
  - `userId`: string  
  - `text`: string  
  - `parentId`: ObjectId (nullable, for replies)  
  - `createdAt`: Date

- **Notes**  
  - `_id`: ObjectId  
  - `userId`: string  
  - `videoId`: string  
  - `text`: string  
  - `tags`: array of strings  
  - `createdAt`: Date  
  - `updatedAt`: Date

- **Logs**  
  - `_id`: ObjectId  
  - `userId`: string  
  - `action`: string  
  - `timestamp`: Date  
  - `metadata`: object (optional)

## Environment Variables

Create a `.env.local` file in the root of the project with the following variables:

NEXTAUTH_SECRET=your_nextauth_secret
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret
MONGODB_URI=your_mongodb_connection_string
NEXT_PUBLIC_YOUTUBE_API_KEY=your_youtube_api_key

markdown
Copy code

## Getting Started

1. Clone the repository  
2. Install dependencies: `npm install`  
3. Set up `.env.local` with your credentials  
4. Run the development server: `npm run dev`  
5. Open [http://localhost:3000](http://localhost:3000) to view the app

## Deployment

You can deploy this app to Vercel, Netlify, or other hosting platforms supporting Next.js. Make sure to configure the environment variables on the hosting platform.

## Acknowledgments

- [NextAuth.js](https://next-auth.js.org/) for authentication  
- [Google APIs](https://developers.google.com/youtube/v3) for video data  
- MongoDB for database storage

---

Feel free to customize or expand this as needed! Let me know if you want me t
