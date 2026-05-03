# FreeAPI Authentication Frontend

This project is a simple authentication-based frontend application built with vanilla HTML and JavaScript. It uses the FreeAPI Authentication Module to implement a basic auth flow with register, login, route protection, and current-user fetching.

## Project Overview

The goal of this project is to understand how frontend authentication works with:

- API requests
- login and register flows
- token-based session handling
- protected pages
- current user state

This project is intentionally kept simple and focuses on the frontend flow using plain HTML pages and inline JavaScript.

## Features

- Register screen
- Login screen
- Protected home page
- Current logged-in user display
- Redirect to login when no token is present
- Token stored in `localStorage`

## Tech Stack

- HTML
- JavaScript
- FreeAPI Authentication Module

## API Endpoints Used

### Register User

`POST https://api.freeapi.app/api/v1/users/register`

Required body:

```json
{
  "email": "user.email@domain.com",
  "password": "test@123",
  "role": "ADMIN",
  "username": "doejohn"
}
```

### Login User

`POST https://api.freeapi.app/api/v1/users/login`

Required body:

```json
{
  "password": "test@123",
  "username": "doejohn"
}
```

### Logout User

`POST https://api.freeapi.app/api/v1/users/logout`

Use this endpoint to log the user out and clear the active session.

### Get Current User

`GET https://api.freeapi.app/api/v1/users/current-user`

Use this endpoint to fetch the currently logged-in user's details.

## Project Structure

```text
.
├── index.html
├── login.html
├── register.html
├── home.html
└── css/
```

## Current Flow

### `index.html`

- Checks if `accessToken` exists in `localStorage`
- Redirects to `login.html` if not logged in
- Redirects to `home.html` if already logged in

### `register.html`

- Collects `username`, `email`, `password`, and `role`
- Sends a registration request to FreeAPI
- Redirects the user to the login page after successful registration

### `login.html`

- Collects `username` and `password`
- Sends a login request to FreeAPI
- Stores the returned `accessToken` in `localStorage`
- Redirects the user to `home.html`

### `home.html`

- Reads the `accessToken` from `localStorage`
- Redirects to `login.html` if the token is missing
- Calls the current-user endpoint with the bearer token
- Shows the logged-in user's username on the page
- Removes the token and redirects to login if the request fails

## How To Run

Because this project uses plain HTML files, you can run it in any simple frontend setup:

1. Open the project folder in your editor.
2. Run it using a live server extension, or open the HTML files in the browser.
3. Start from `index.html`.

Using a local server is recommended so navigation between pages works more reliably.

## Expected Improvements

To fully match the assignment requirements, the following can still be added later:

- Logout button connected to the logout API
- Better success and error messages in the UI
- Loading states while requests are in progress
- Cleaner styling with CSS or Tailwind
- Better handling for API error responses
- Optional refresh token handling if needed

## Learning Goals

This project helps practice:

- sending `POST` and `GET` requests with `fetch`
- handling auth tokens on the frontend
- protecting routes/pages
- updating UI based on login state
- working with a third-party authentication API

## Submission

For final submission, include:

- Live hosted project link
- Public GitHub repository link

## Author

Built as a frontend authentication practice project using the FreeAPI Authentication Module.
