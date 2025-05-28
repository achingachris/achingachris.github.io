---
author: ["Chris Achinga"]
title: "Beginners Guide to Using APIs in Python"
date: "2024-01-02"
description: "Simple API consumptions in Python"
tags: ["python", "api"]
ShowToc: true
---

Application Programming Interfaces (APIs) are crucial in the world of software development. They serve as the backbone for communication between different software applications. This article explores how to interact with a simple API using Python. We'll use a dummy server set up using JSON-Server, a package that allows you to create a fake API for testing and development purposes.

## Setting Up the Dummy Server

Before diving into Python code, let's set up our dummy server. JSON-Server provides a full fake REST API with zero coding in less than a minute(not literally). Here's how you can set it up:


### Requirements

1. [ ] Node.js
2. [ ] NPM (Node Package Manager)

Steps

1. Install JSON-Server: Run `npm install -g json-server`to install JSON-Server globally.
2. Create a `db.json` File: This file will be a database for your dummy API.

```json

 {
 "marvelstars": [
   {
       "id": 3,
       "rating": 10,
       "name": "Natasha Romanoff",
       "stagename": "Black Widow",
       "powers": "Expert martial artist, marksmanship, and hand-to-hand combat. Skilled spy and master of espionage."
     },
     {
       "id": 18,
       "rating": 9,
       "name": "Diana Prince",
       "stagename": "Wonder Woman",
       "powers": "Superhuman strength, agility, and durability. Wields the Lasso of Truth and indestructible bracelets."
     },
 ]
 }
```

3. Start the Server: Use the following script to start your JSON-Server.

```javascript

 const jsonServer = require('json-server')
 const cors = require('cors')
 const path = require('path')
 const server = jsonServer.create()
 const router = jsonServer.router(path.join(__dirname, 'db.json'))
 const middlewares = jsonServer.defaults()
 server.use(cors())
 server.use(jsonServer.bodyParser)
 server.use(middlewares)
 server.use(router)
 const PORT = 8000
 server.listen(PORT, () => {
   console.log(`JSON Server is running on http://localhost:${PORT}`)
 })
```

# Interacting with the API using Python

With its simplicity and readability, Python is an excellent choice for API interaction. We'll use the requests library, which is a simple HTTP library for Python.

## Installation

First, ensure you have the requests library installed:

`pip install requests`

### Performing CRUD Operations

Import requests on your script and set variables:

```python
import requests
api_url = "http://localhost:8000/marvelstars"
response = requests.get(api_url)
```

1. Read Operation (GET request)

```python
if response.status_code == 200:
    marvelstars = response.json()
    print("Fetched Marvel Stars:")
    for star in marvelstars:
        print(star)
else:
    print(f"Failed to fetch data. Status code: {response.status_code}")

```

2. Create Operation (POST request)

```python
# Add a new Marvel star (POST request)
new_star = {
    "id": 73,
    "rating": 1,
    "name": "Ngugu Wa Thiongo",
    "stagename": "Thanos",
    "powers": "Snaps and annoys people"
}
response = requests.post(api_url, json=new_star)
if response.status_code == 201:
    print("New Marvel Star added successfully.")
else:
    print(f"Failed to add new Marvel Star. Status code: {response.status_code}")
```

3. Update Operation (PUT request)

```pyhton
# Edit an existing Marvel star (PUT request)
updated_star = {
      "id": 3,
      "rating": 10,
      "name": "Natasha Romanoff",
      "stagename": "Black Widow",
      "powers": "Expert martial artist, marksmanship, and hand-to-hand combat. Skilled spy and master of espionage."
    }
response = requests.put(api_url + "/3", json=updated_star)
if response.status_code == 200:
    print("Marvel Star updated successfully.")
else:
    print(f"Failed to update Marvel Star. Status code: {response.status_code}")

```

4. Delete Operation (DELETE request)

```python
# Delete a Marvel star by ID (DELETE request)
star_id_to_delete = 23
response = requests.delete(f"{api_url}/{star_id_to_delete}")
if response.status_code == 200:
    print(f"Marvel Star with ID {star_id_to_delete} deleted successfully.")
else:
    print(f"Failed to delete Marvel Star by ID. Status code: {response.status_code}")
```

## Conclusion

Using Python to interact with APIs is straightforward and efficient. By following these steps, you can set up a dummy server with JSON-Server and use Python's requests library to perform various CRUD operations. This forms a foundational skill for any developer looking to integrate different software applications or services.

https://github.com/achingachris/fetch-and-get/blob/main/python/fetchandget.ipynb
