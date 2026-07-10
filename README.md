# myShop

myShop is a full-stack shop builder and storefront application. It includes a Node.js/Express backend with PostgreSQL, Sequelize, Passport authentication, and a React/Vite frontend for managing a shop and publishing a public storefront.

## Project Structure

```text
myShop/
  backend/   Express API, authentication, Sequelize models, EJS views
  frontend/  React app built with Vite
```

## Features

- Email/password signup and login
- Google OAuth login
- Protected dashboard and account pages
- Create, update, and delete shop items
- Public storefront route by site name
- Contact form that sends email through Gmail SMTP

## Requirements

- Node.js 18 or newer
- npm
- PostgreSQL database access for local development or a production `DATABASE_URL`

## Setup

### 1. Install dependencies

Install backend dependencies:

```bash
cd backend
npm install
```

Install frontend dependencies:

```bash
cd ../frontend
npm install
```

### 2. Configure environment variables

Create a `.env` file in `backend/` with the values used by the server:

```bash
DATABASE_URL=
GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=
GMAIL_USER=
GMAIL_PASS=
PG_PASSWORD=
```

The backend also uses Sequelize config in `backend/config/config.json`. For local development, review those values and update them if your PostgreSQL setup is different.

### 3. Run database migrations

If you are using Sequelize CLI migrations, run them from `backend/` after setting up the database connection.

```bash
npx sequelize-cli db:migrate
```

## Running the app

Start the backend:

```bash
cd backend
npm run start
```

For production-style backend startup:

```bash
npm run start:prod
```

Start the frontend:

```bash
cd frontend
npm run dev
```

By default, the backend runs on port `3000` and Vite runs on its usual dev port.

## Backend Routes

Some of the main backend endpoints are:

- `POST /signup` - create a new account
- `POST /login` - log in with email and password
- `GET /logout` - log out the current session
- `GET /account` - fetch the logged-in user account
- `POST /account` - update account details
- `GET /items` - fetch items for the current user
- `POST /additem` - add a new item
- `POST /update` - update an item
- `DELETE /delete/:id` - delete an item
- `GET /myshop/:siteName` - fetch a public storefront by site name
- `POST /contact` - send a contact message

## Frontend Routes

The React app includes routes for:

- Home
- Signup
- Login
- Dashboard
- About
- Contact
- Account
- Update account
- Public shop template

## Notes

- The backend CORS configuration currently allows the deployed frontend origin in `backend/app.js`. If you are running the frontend locally, update that origin to match your local dev URL.
- The repository includes both EJS views and a React frontend. The React app is the main user-facing client in `frontend/`.
