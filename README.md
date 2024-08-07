 # Payment Web
This project is a PayTM-like application that allows users to send money to each other given an initial dummy balance. The application uses a stack comprising Express for the backend, React for the frontend, and MongoDB for the database. 

## Table of Contents
1. [Features](#features)
2. [API Endpoints](#api-endpoints)
3. [Schemas](#schemas)
4. [Middlewares](#middlewares)
 
 

## Features

- User Authentication
  - Sign Up
  - Sign In
  - Update User Information
- User Balance Management
  - View Balance
  - Transfer Money

## API Endpoints

### User Authentication

- **Sign Up**
  - Method: `POST`
  - Route: `/api/v1/user/signup`
  - Body:
    ```json
    {
      "username": "name@gmail.com",
      "firstName": "name",
      "lastName": "name",
      "password": "123456"
    }
    ```
  - Response:
    ```json
    {
      "message": "User created successfully",
      "token": "jwt"
    }
    ```

- **Sign In**
  - Method: `POST`
  - Route: `/api/v1/user/signin`
  - Body:
    ```json
    {
      "username": "name@gmail.com",
      "password": "123456"
    }
    ```
  - Response:
    ```json
    {
      "token": "jwt"
    }
    ```

- **Update User Information**
  - Method: `PUT`
  - Route: `/api/v1/user`
  - Body:
    ```json
    {
      "password": "new_password",
      "firstName": "updated_first_name",
      "lastName": "updated_last_name"
    }
    ```
  - Response:
    ```json
    {
      "message": "Updated successfully"
    }
    ```

### User Balance Management

- **Get Balance**
  - Method: `GET`
  - Route: `/api/v1/account/balance`
  - Response:
    ```json
    {
      "balance": 100
    }
    ```

- **Transfer Money**
  - Method: `POST`
  - Route: `/api/v1/account/transfer`
  - Body:
    ```json
    {
      "to": "recipient_id",
      "amount": 100
    }
    ```
  - Response:
    ```json
    {
      "message": "Transfer successful"
    }
    ```
  - Errors:
    - Insufficient balance
    - Invalid account

## Schemas

### User Schema
- `username`: String, unique
- `firstName`: String
- `lastName`: String
- `password`: String

### Account Schema
- `userId`: ObjectId, reference to User
- `balance`: Number

## Middlewares

### Auth Middleware
- Checks for `Authorization` header with Bearer token.
- Verifies the token and adds `userId` to the request object if valid.

 
