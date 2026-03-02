# Pet Shelter API

![Node.js](https://img.shields.io/badge/Node.js-20.x-green?logo=node.js) ![TypeScript](https://img.shields.io/badge/TypeScript-5.x-blue?logo=typescript) ![Express](https://img.shields.io/badge/Express-5.x-black?logo=express) ![License](https://img.shields.io/badge/license-MIT-brightgreen)

A RESTful API for managing a pet shelter's animal listings — supports filtering, querying by ID, and basic authentication middleware.

## Index

- [About](#about)
- [Usage](#usage)
- [Development](#development)
- [Contribution](#contribution)
- [License](#license)

---

## About

A back-end API built with Express and TypeScript to serve pet shelter data. The main goal was to learn how to:

- Structure an Express app using **routers, controllers, and middleware** in separate files
- Type **Request, Response, and query/route params** with TypeScript generics
- Write **query parameter filtering** (by species, adoption status, age range)
- Create and chain **custom middleware** (ID validation, password-based auth)
- Configure a **TypeScript project** with `tsconfig.json` and compile to `dist/`
- Handle **404 catch-all routes** in Express 5

---

## Usage

### Installation

1. Clone the repository:
   ```bash
   git clone <your-repo-url>
   cd <project-folder>
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Build and start the server:
   ```bash
   npm start
   ```
4. The API will be running at `http://localhost:8000`

### Commands

```bash
npm run build   # Compiles TypeScript to JavaScript in /dist
npm run start   # Builds and starts the server with Node
```

### Endpoints

| Method | Endpoint     | Description                        | Auth required |
|--------|--------------|------------------------------------|---------------|
| GET    | `/pets`      | Returns all pets (supports filters)| No            |
| GET    | `/pets/:id`  | Returns a single pet by ID         | Yes           |

**Query parameters for `GET /pets`:**

| Param     | Type              | Example              |
|-----------|-------------------|----------------------|
| `species` | string            | `?species=Dog`       |
| `adopted` | `true` \| `false` | `?adopted=false`     |
| `minAge`  | number            | `?minAge=2`          |
| `maxAge`  | number            | `?maxAge=5`          |

**Auth for `GET /pets/:id`:**  
Pass `?password=please` as a query parameter.

---

## Development

### Pre-Requisites

- Node.js 20+
- A text editor
- Basic knowledge of TypeScript and Express
- A REST client 

### File Structure

| No | File Name | What it does |
|----|-----------|--------------|
| 1 | `src/index.ts` | Entry point — sets up Express, registers middleware and routes |
| 2 | `src/routes/pets.routes.ts` | Defines the `/pets` route paths and attaches middleware/controllers |
| 3 | `src/controllers/pets.controllers.ts` | Handles request logic — filtering pets and fetching by ID |
| 4 | `src/middleware/pets.middleware.ts` | Validates numeric IDs and checks query-based auth |
| 5 | `src/data/pets.ts` | In-memory pet data and the `Pet` type definition |
| 6 | `tsconfig.json` | TypeScript config — compiles from `src/` to `dist/` |
| 7 | `package.json` | Project metadata, dependencies, and build scripts |

### Build

TypeScript source lives in `src/` and is compiled by `tsc` into `dist/`. When `npm start` runs, it first compiles the project then executes `dist/index.js` with Node. The app uses in-memory data (no database), so data resets on every restart.

---

## Contribution

1. Found a bug? Open an issue and I'll try to fix it.
2. Advice? If you have ideas for new filters, endpoints, or auth improvements, let me know!

---

## License

Feel free to use this for your own practice! **MIT** License.