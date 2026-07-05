# Dummy JSON ECom API Endpoints Testing

> ECom API Testing project using [DummyJSON](https://dummyjson.com) — a free public fake REST API for e-commerce prototyping and QA testing.

---

Here is the Postman documentation for this project(collection with env) -- https://documenter.getpostman.com/view/39290336/2sBXwyG7Kp

## Overview

This collection covers end-to-end API testing for a simulated e-commerce platform powered by the **DummyJSON** public API. It includes authentication flows, product management, shopping cart operations, and user management — all organized into logical folders with reusable environment variables.

**Base URL:** `{{BaseUrl}}`  
**Environment:** `Ecom API Testing Env`  
**Auth:** Bearer token via `{{AccessToken}}`

---

## Environment Variables

| Variable | Description |
|---|---|
| `BaseUrl` | Base URL of the DummyJSON API (e.g. `https://dummyjson.com`) |
| `AccessToken` | JWT access token obtained after login |
| `RefreshToken` | JWT refresh token for session renewal |
| `UserId` | ID of the authenticated or target user |
| `ProductId` | ID of the target product for single-resource operations |

---

## Collection Structure

### 1. Introduction
Basic utility/diagnostic endpoints to verify connectivity and environment setup.

| Method | Endpoint | Name |
|---|---|---|
| GET | `{{BaseUrl}}/test` | Test Route |
| GET | `{{BaseUrl}}/ip` | IP Address |

---

### 2. Mock HTTP
Endpoints for simulating specific HTTP response codes — useful for testing error-handling logic.

| Method | Endpoint | Name |
|---|---|---|
| GET | `{{BaseUrl}}/http/500` | Mock HTTP Response |
| GET | `{{BaseUrl}}/http/404/Hello_Deb` | Custom HTTP Response |

---

### 3. Auth Flow
Handles user authentication, session management, and token refresh.

> Credentials can be sourced from [dummyjson.com/users](https://dummyjson.com/users).

| Method | Endpoint | Name |
|---|---|---|
| POST | `{{BaseUrl}}/auth/login` | Login User |
| GET | `{{BaseUrl}}/auth/me` | Get Current Auth User |
| POST | `{{BaseUrl}}/auth/refresh` | Refresh Auth Session |

**Flow:**
1. Call **Login User** → stores `AccessToken`, `RefreshToken`, and `UserId` in environment.
2. Call **Get Current Auth User** to validate the token.
3. Call **Refresh Auth Session** when the access token expires.

---

### 4. Products
Full CRUD operations on the products catalog, plus search, filter, sort, and pagination.

| Method | Endpoint | Name |
|---|---|---|
| GET | `{{BaseUrl}}/products` | Get All Products |
| GET | `{{BaseUrl}}/products/{{ProductId}}` | Get Single Product |
| GET | `{{BaseUrl}}/products/search?q=lipstick` | Search Products |
| GET | `{{BaseUrl}}/products/?limit=8&skip=10&select=title,price` | Limit & Skip Products |
| GET | `{{BaseUrl}}/products/?sortBy=title&order=desc` | Sort Products |
| GET | `{{BaseUrl}}/products/categories` | Get All Products Categories |
| GET | `{{BaseUrl}}/products/category-list` | Get Products Categories List |
| GET | `{{BaseUrl}}/products/category/laptops` | Get Products by a Category |
| POST | `{{BaseUrl}}/products/add` | Add a New Product |
| PUT | `{{BaseUrl}}/products/3` | Update an Existing Product |
| DELETE | `{{BaseUrl}}/products/{{ProductId}}` | Delete a Product |

---

### 5. Carts
Shopping cart management — create, read, update, and delete carts.

| Method | Endpoint | Name |
|---|---|---|
| GET | `{{BaseUrl}}/carts` | Get All Carts |
| GET | `{{BaseUrl}}/carts/1` | Get a Single Cart |
| GET | `{{BaseUrl}}/carts/{{UserId}}` | Get Carts by a User |
| POST | `{{BaseUrl}}/carts/add` | Add a New Cart |
| PUT | `{{BaseUrl}}/carts/1` | Update an Existing Cart |
| DELETE | `{{BaseUrl}}/carts/1` | Delete an Existing Cart |

---

### 6. Users
User management including CRUD, search, filtering, sorting, and fetching related resources.

| Method | Endpoint | Name |
|---|---|---|
| GET | `{{BaseUrl}}/users` | Get All Users |
| GET | `{{BaseUrl}}/users/{{UserId}}` | Get a Single User |
| GET | `{{BaseUrl}}/users/search?q=John` | Search Users |
| GET | `{{BaseUrl}}/users/filter?key=hair.color&value=Brown` | Filter Users |
| GET | `{{BaseUrl}}/users?sortBy=firstName&order=desc` | Sort & Order Users |
| GET | `{{BaseUrl}}/users/{{UserId}}/carts` | Get User's Carts by User ID |
| GET | `{{BaseUrl}}/users/{{UserId}}/posts` | Get User's Posts by User ID |
| POST | `{{BaseUrl}}/users/add` | Add a New User |
| PUT | `{{BaseUrl}}/users/3` | Update an Existing User |
| DELETE | `{{BaseUrl}}/users/201` | Delete an Existing User |

---

## Getting Started

1. **Import the collection** into your Postman workspace.
2. **Select the environment** `Ecom API Testing Env` from the environment dropdown.
3. **Set `BaseUrl`** to `https://dummyjson.com` in the environment.
4. **Run the Auth Flow** — execute the `Login User` request first. The post-response script will automatically populate `AccessToken`, `RefreshToken`, and `UserId`.
5. **Explore the folders** — each folder is self-contained and can be run independently after authentication.

---

## Running the Collection

You can run the entire collection or individual folders using the **Collection Runner**:

- Go to the collection → click **Run**
- Select the `Ecom API Testing Env` environment
- Optionally set iteration count and data files for data-driven runs
- Review pass/fail results per request in the runner output

---

## Notes

- DummyJSON is a **mock/fake API** — write/delete operations (POST, PUT, DELETE) simulate responses but do not persist data.
- Token expiry is short; use the **Refresh Auth Session** request to renew without re-logging in.
- The `{{ProductId}}` and `{{UserId}}` variables should be set in the environment before running single-resource requests.

---

## References

- [DummyJSON Official Docs](https://dummyjson.com/docs)
- [DummyJSON Users](https://dummyjson.com/users)
- [Postman Collection Runner Docs](https://learning.postman.com/docs/running-collections/intro-to-collection-runs/)