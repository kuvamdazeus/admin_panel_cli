# OaktreeApps Admin CLI

## About

This is a simple CLI application to quickly setup MERN stack admin project with Express backend & React frontend.

The CLI allows you to create resources at the frontend and corresponding routes & models at the backend with one command.

Everything is controlled in the `kitconfig` folder.

## Installation

To install the CLI application, run the following command:

```bash
npm i -g <npm-package>
```

Or the package can be run directly via npx:

```bash
npx <npm-package> [commands...]
```

## Commands

### `scaffold [...options] project-name`

Creates a new admin project containing the following folders:

1. **kitconfig** - folder containing the `.cjs` files for configuring the project (also comes with sample files `resources/products.cjs` & `resources/students.cjs`).

2. **webapp** - React.js project containing the UI.

3. **server** - Express.js (TypeScript) project hooked up to MongoDB database.

#### Usage

```bash
npx <npm-package> scaffold admin-panel
```

```bash
npx <npm-package> scaffold --only-webapp admin-panel
```

```bash
npx <npm-package> scaffold --only-server admin-panel
```

### `add resource`

Creates UI & corresponding backend (models, routes & controllers).

#### Usage

For example, let's say we need to create backend & UI for our "posts" model.

we'll first go into the `kitconfig/resources` folder, create a file named `posts.cjs` and define properties & fields this resource needs. (refer types autocomplete & sample files for defining new fields & other properties),

And then, while we're in the admin directory, we can run the following command:

```bash
npx <npm-package> add posts
```

### `remove resource`

Removes the previously created resource in UI & corresponding backend (models, routes & controllers).

> Only removes the resource from codebase, won't remove the config file.

#### Usage

```bash
npx <npm-package> remove posts
```

### `sync`

_Adds_ all the resources defined in `kitconfig/resources` folder, without overriding any of the existing resources.

#### Usage

```bash
npx <npm-package> sync
```

## .env files

### Frontend

The `.env` file in the frontend folder expects only 1 variable i.e base url of the corresponding backend server.

```python
VITE_BASE_URL = "http://localhost:3005/api"
```

### Backend

The `.env` file in the backend folder expects various variables, here's a sample `.env` file that goes with the server.

```python
REST_API_PORT=3005 #REQUIRED
MONGO_CONNECTION_URL=mongodb+srv://<username>:<password>@cluster.mongodb.net/?retryWrites=true&w=majority #REQUIRED


AUTH_PRIVATE_BASE64= #REQUIRED
AUTH_PUBLIC_BASE64= #REQUIRED

SMTP_HOST=
SMTP_PORT=
SMTP_USER=
SMTP_PASSWORD=
SMTP_FROM_EMAIL=
SMTP_FROM_NAME=

S3_REGION=
S3_ACCESS_KEY=
S3_ACCESS_ID=
S3_BUCKET_NAME=

STATIC_S3_REGION=
STATIC_S3_BUCKET_NAME=
```

## Kit Config

### Folder Structure

```
  |-kitconfig
    |-index.json
    |-resources
      |-<screen-name>.json
      |-<screen-name>.json
      ...

  |-webapp
  |-backend
```
