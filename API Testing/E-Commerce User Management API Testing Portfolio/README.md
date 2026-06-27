# E-Commerce User Management API Testing Portfolio

> Production-grade automated test collection covering authentication, security,
> and user profile CRUD operations across two public API platforms —
> **DummyJSON** and **ReqRes**.

---

Here is the Postman API Documentation for this entire collection --- https://documenter.getpostman.com/view/39290336/2sBXwyG7Kt

## Table of Contents

- [Overview](#overview)
- [APIs Under Test](#apis-under-test)
- [Collection Structure](#collection-structure)
- [Endpoints & Test Coverage](#endpoints--test-coverage)
  - [API 1: DummyJSON Authentication & Users](#api-1-dummyjson-authentication--users)
  - [API 2: ReqRes Pagination & Mutation](#api-2-reqres-pagination--mutation)
- [Environment Variables](#environment-variables)
- [Running the Collection](#running-the-collection)
  - [Postman UI](#postman-ui)
  - [Newman (CLI)](#newman-cli)
- [Test Strategy](#test-strategy)
- [Prerequisites](#prerequisites)

---

## Overview

This Postman collection is part of a QA portfolio demonstrating end-to-end
automated API testing skills. It validates:

- **Functional correctness** — status codes, response bodies, and data shapes
- **Security posture** — SQL injection resistance and absence of data leakage
- **Performance baseline** — response time thresholds
- **Schema integrity** — JSON schema validation on paginated responses
- **Token lifecycle** — automatic extraction and environment injection of auth
  tokens

---

## APIs Under Test

| Platform | Base URL | Purpose |
|---|---|---|
| [DummyJSON](https://dummyjson.com) | `{{dummyjson_url}}` | Authentication & user directory |
| [ReqRes](https://reqres.in) | `{{reqres_url}}` | Paginated user listing & deletion |

---

## Collection Structure