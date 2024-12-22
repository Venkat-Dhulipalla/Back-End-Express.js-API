# Todo App Backend

A RESTful API built with Express.js and Prisma ORM for the Todo application.

## Features

- RESTful API endpoints
- MySQL database with Prisma ORM
- Type-safe database operations
- CRUD operations for tasks
- Error handling middleware
- Environment variable configuration

## Tech Stack

- Express.js
- TypeScript
- Prisma ORM
- MySQL
- Node.js
- CORS middleware

## Getting Started

### Prerequisites

- Node.js (v18 or higher)
- MySQL (v8.0 or higher)
- npm or yarn

### Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd todo-backend
```

2. Install dependencies:
```bash
npm install
# or
yarn install
```

3. Create a `.env` file in the root directory:
```env
DATABASE_URL="mysql://user:password@localhost:3306/todo_db"
PORT=3001
```

4. Set up the database:
```bash
# Create and apply migrations
npx prisma migrate dev

# Generate Prisma Client
npx prisma generate
```

5. Start the development server:
```bash
npm run dev
# or
yarn dev
```

The API will be available at `http://localhost:3001`

## Project Structure

```
todo-backend/
├── src/
│   ├── controllers/      # Request handlers
│   ├── routes/          # API routes
│   ├── middleware/      # Custom middleware
│   ├── prisma/         # Prisma schema and migrations
│   └── types/          # TypeScript type definitions
├── prisma/
│   ├── schema.prisma   # Database schema
│   └── migrations/     # Database migrations
└── package.json       # Project dependencies
```

## Database Schema

```prisma
model Task {
  id        Int      @id @default(autoincrement())
  title     String
  completed Boolean  @default(false)
  color     String
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
}
```

## API Endpoints

### Tasks

- `GET /tasks`
  - Get all tasks
  - Response: `Task[]`

- `POST /tasks`
  - Create a new task
  - Body: `{ title: string, color: string }`
  - Response: `Task`

- `PUT /tasks/:id`
  - Update a task
  - Body: `{ title?: string, completed?: boolean, color?: string }`
  - Response: `Task`

- `DELETE /tasks/:id`
  - Delete a task
  - Response: `204 No Content`

## Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm start` - Start production server
- `npm run migrate` - Run database migrations
- `npm run generate` - Generate Prisma Client

## Error Handling

The API includes comprehensive error handling for:
- Invalid requests
- Database errors
- Not found resources
- Validation errors

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details
