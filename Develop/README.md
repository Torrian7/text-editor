# Text Editor Starter Code
# Text Editor Application

![License Badge](https://img.shields.io/badge/License-MIT-blue)  
[Deployed Application](https://editmytext.herokuapp.com/)  
[GitHub Repository](https://github.com/torrian7/text-editor)

## Usage Instructions
- Navigate to the deployed application: https://editmytext.herokuapp.com/  
- Use the text editor in the browser or click the install button to download the application

## Table of Contents

- [Text Editor Starter Code](#text-editor-starter-code)
- [Text Editor Application](#text-editor-application)
  - [Usage Instructions](#usage-instructions)
  - [Table of Contents](#table-of-contents)
  - [Description](#description)
  - [Screenshot](#screenshot)
  - [Code Examples](#code-examples)
  - [Core Technologies Used](#core-technologies-used)
  - [License](#license)

## Description

The purpose of this project was to build a single-page text editor application that runs in the browser and is also installable as a PWA (Progressive Web Application). This application uses an IndexedDB database to get and store data. specifically, methods from the `idb` package were used to implement data persistence.

## Screenshot

![Screen Shot 2022-05-25 at 9 13 44 PM](https://user-images.githubusercontent.com/99947655/170415655-04e1212d-d1d4-4145-ba93-cc7bebc7e5b3.png)

## Code Examples

This example displays the use of the `idb` package methods to store data on the IndexedDB database.

```js
export const putDb = async (id, content) => {
  console.log("PUT request to the database");
  const jateDb = await openDB("jate", 1);
  const tx = jateDb.transaction("jate", "readwrite");
  const store = tx.objectStore("jate");
  const request = store.put({ id: id, content: content });
  const result = await request;
  console.log("data saved to the database", result);
};
```

This example displays how asset caching was implemented in the code.

```js
registerRoute(
  ({ request }) => ["style", "script", "worker"].includes(request.destination),
  new StaleWhileRevalidate({
    cacheName: "asset-cache",
    plugins: [
      new CacheableResponsePlugin({
        statuses: [0, 200],
      }),
    ],
  })
);
```

## Core Technologies Used

![JavaScript Badge](https://img.shields.io/badge/Language-JavaScript-yellow)
![CSS Badge](https://img.shields.io/badge/Language-CSS-blue)
![Node.js Badge](https://img.shields.io/badge/Environment-Node.js-green)
![IndexedDB Badge](https://img.shields.io/badge/Database-IndexedDB-informational)
![idb Badge](https://img.shields.io/badge/NPM-idb-red)
![Express Badge](https://img.shields.io/badge/NPM-Express.js-yellowgreen)
![heroku Badge](https://img.shields.io/badge/Deployment-heroku-blueviolet)


## License

MIT License

Copyright (c) 2023 Torrian Spells

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.