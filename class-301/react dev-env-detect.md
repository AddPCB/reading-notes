# How to detect if your client and server are running in dev environment.

## server

### server/server.js

this is the start of my server.js file

```JSX
require("dotenv").config();
const express = require("express");
const mongoose = require("mongoose");
const Book = require("./models/book");
const PORT = process.env.PORT || 8080;
const app = express();
// confirm our environment is set properly
console.log(`server env: ${process.env.NODE_DEV_ENV}`);
// Use ternary operator to conditionally enable CORS when in development mode
process.env.NODE_DEV_ENV === "development"
  ? app.use((req, res, next) => {
      res.header("Access-Control-Allow-Origin", "http://localhost:3000");
      res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
      next();
    })
  : null;
// if we start with an empty books collection then add the seed file.
  mongoose.connect(process.env.DATABASE_URL).then(async () => {
    const booksCount = await Book.countDocuments();
    booksCount === 0 ?
      await Book.insertMany(require('./seed')) && console.log('Database seeded successfully!') :
      console.log(`The 'books' collection already has ${booksCount} documents.`);
  }).catch((error) => console.log(error));
```

### server/package.json

this is my full server package.json file

```JSX
{
  "name": "can-book-back",
  "version": "1.0.5",
  "description": "",
  "main": "server.js",
  "scripts": {
    "start": "cross-env NODE_DEV_ENV=development nodemon server"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "cors": "^2.8.5",
    "cross-env": "^7.0.3",
    "dotenv": "^10.0.0",
    "express": "^4.18.2",
    "mongodb": "^5.1.0",
    "mongoose": "^7.0.1"
  }
}

```

## client

### client/src/BestBooks.js

This is the start of my BestBooks.js

```JSX
import React, { useState, useEffect } from "react";
import axios from "axios";
import { Carousel } from "react-bootstrap";

// confirm our environment is set properly
console.log(`client env: ${process.env.NODE_DEV_ENV}`);

function BestBooks() {
  const [books, setBooks] = useState([]);
// use development endpoint only if we are in development mode.
  useEffect(() => {
    async function fetchData() {
      try {
        const API = process.env.REACT_APP_DEV_ENV === "development" ? "http://localhost:8080/books" : "/books";
        const response = await axios.get(API);
        setBooks(response.data);
      } catch (error) {
        console.log(error);
      }
    }
    fetchData();
  }, []);
```

### client/package.json

The scripts section of my client package.json

```json
  "scripts": {
    "start": "cross-env REACT_APP_DEV_ENV=development react-scripts start",
    "build": "react-scripts build"
  },
```
