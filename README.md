# HitchHikr: A Virtual Global Hackathon Submission

**HitchHikr** is a mobile app that provides a smooth carpooling experience, designed to help users efficiently commute while reducing traffic congestion and carbon emissions.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)

## Introduction

Traffic congestion is a pressing issue affecting both the workforce and the environment. HitchHikr addresses this problem by promoting carpooling as an eco-friendly and efficient commuting solution. The app allows users to find and join carpool routes offered by other users who are traveling in the same direction.

Key benefits of HitchHikr:
- Reduce traffic congestion and carbon emissions.
- Efficiently find carpools along your route.
- Easily manage carpooling experiences.

## Features

- **Route-Based Carpools:** Drivers create routes, and carpoolers can hitchhike onto those routes, joining and leaving at convenient points along the way.

- **Real-time Updates:** Users can track the real-time locations of carpoolers and drivers, enhancing the carpooling experience.

- **Suitable Carpools:** The app identifies suitable carpools based on user locations, destinations, and maximum walking distances.

- **User Profiles:** Users can customize their profiles with details like car model, driver description, and maximum walking distance.

- **Mobile Platform:** HitchHikr is built for mobile devices using React Native and Expo.

## Technologies Used

- **Front-end:** React Native, Expo
- **Back-end:** Python Flask
- **Database:** SQLite (migrating to MySQL for production)
- **Maps Integration:** Google Maps API
- **Encryption:** Cryptography (for user ID encryption)
- **WebSockets:** Socket.IO (for real-time communication)
- **Authentication:** Custom authentication system

## Usage

1. Register and log in to the HitchHikr app.
2. Customize your profile with car model, driver description, and maximum walking distance.
3. Search for suitable carpools based on your location, destination, and preferences.
4. Join carpool routes and enjoy an efficient and eco-friendly commute.

## API Endpoints

#### Get Carpool Route

- **Endpoint:** `/maps/get_carpool_route`
- **Method:** GET
- **Description:** Get a carpool route based on user location, destination, and polyline.
- **Parameters:**
  - `userLocation` (Type: String) - User's current location (e.g., `"(123.456,789.012)"`).
  - `userDestination` (Type: String) - User's destination location (e.g., `"(123.456,789.012)"`).
  - `polyline` (Type: String) - Polyline representation of the route.

#### Get Suitable Carpools

- **Endpoint:** `/maps/get_suitable_carpools`
- **Method:** GET
- **Description:** Get suitable carpools for a user based on their location, destination, and preferences.
- **Parameters:**
  - `userLocation` (Type: String) - User's current location (e.g., `"(123.456,789.012)"`).
  - `userDestination` (Type: String) - User's destination location (e.g., `"(123.456,789.012)"`).
  - `hash` (Type: String) - User identification token.

#### Get Route

- **Endpoint:** `/maps/get_route`
- **Method:** GET
- **Description:** Get a route between two locations.
- **Parameters:**
  - `origin` (Type: String) - Starting location (e.g., `"(123.456,789.012)"`).
  - `destination` (Type: String) - Destination location (e.g., `"(123.456,789.012)"`).

#### User Registration

- **Endpoint:** `/accounts/register`
- **Method:** POST
- **Description:** Register a new user.
- **Request Body (JSON):**
  - `email` (Type: String) - User's email address.
  - `password` (Type: String) - User's password.
  - `name` (Type: String) - User's name.

#### User Login

- **Endpoint:** `/accounts/login`
- **Method:** GET
- **Description:** Log in an existing user.
- **Parameters:**
  - `email` (Type: String) - User's email address.
  - `password` (Type: String) - User's password.

#### Get User Profile

- **Endpoint:** `/accounts/get`
- **Method:** GET
- **Description:** Get user profile information.
- **Parameters:**
  - `hash` (Type: String) - User identification token.

#### Edit User Profile

- **Endpoint:** `/accounts/edit`
- **Method:** POST
- **Description:** Edit user profile information.
- **Request Body (JSON):**
  - `user_id` (Type: String) - User identification token.
  - `name` (Type: String) - User's name.
  - `email` (Type: String) - User's email address.
  - `description` (Type: String) - User's description.
  - `car_model` (Type: String) - User's car model.
  - `walking_distance` (Type: Float) - Maximum walking distance (in miles).

#### Get Carpool by Type

- **Endpoint:** `/carpool/get`
- **Method:** GET
- **Description:** Get carpool listings by type (driver or carpooler).
- **Parameters:**
  - `hash` (Type: String) - User identification token.
  - `type` (Type: String) - User type ('driver' or 'carpooler').

#### Connect to a Carpool

- **Endpoint:** `/carpool/connect`
- **Method:** POST
- **Description:** Connect a user to a carpool.
- **Request Body (JSON):**
  - `user_id` (Type: String) - User identification token.
  - `carpool_id` (Type: Integer) - Carpool ID.
  - `stops` (Type: Array of Strings) - Array of stops (e.g., `["(123.456,789.012)"]`).
  - `location` (Type: String) - Current location (e.g., `"(123.456,789.012)"`).
  - `destination` (Type: String) - Destination location (e.g., `"(123.456,789.012)"`).

#### Get User by ID

- **Endpoint:** `/user/get`
- **Method:** GET
- **Description:** Get user information by user ID.
- **Parameters:**
  - `user_id` (Type: String) - User identification token.

#### Get Carpool by ID

- **Endpoint:** `/carpool/<carpool_id>`
- **Method:** GET
- **Description:** Get carpool information by carpool ID.

#### Create a Carpool

- **Endpoint:** `/carpool/create`
- **Method:** POST
- **Description:** Create a new carpool listing.
- **Request Body (JSON):**
  - `hash` (Type: String) - User identification token.
  - `start_address` (Type: String) - Carpool start address.
  - `end_address` (Type: String) - Carpool end address.
  - `polyline` (Type: String) - Polyline representation of the route.
  - `occupancy` (Type: Integer) - Maximum carpool occupancy.

#### Real-time Notifications

- **Socket.IO:** Real-time notifications for join requests and responses. (Not an HTTP endpoint)

Please note that the latitude and longitude values are stringified tuples enclosed in double quotes, e.g., `"(123.456,789.012)"`. Ensure that the data types mentioned match the actual data types used in your API implementation.
