## Movies API

[![Netlify Status](https://api.netlify.com/api/v1/badges/7334fbdc-4909-4ab6-b5b9-14ec037326b2/deploy-status)](https://app.netlify.com/sites/andre-specht-dev/deploys)


**Movies** is a simple static API (Application Programming Interface) designed 
for IT students who want to get familiar with using APIs in web applications.

### How to use

You can use ```fetch``` (learn [here](https://github.com/mrspecht/fetch-api)) to 
access the list of movies provided by the API. The list - an array of objects -  
is in the ```results``` object.

```javascript
const url = 'https://movies.andrespecht.dev';

const options = {
  method: 'GET',
  mode: 'cors'
};

async function getMovies() {
  try {
    const response = await fetch(url, options);
    if (!response.ok) {
      throw new Error(`${response.statusText} (${response.status})`);
    }
    // Parsing the reponse as JSON
    const data = await response.json();
    // Printing the movies
    console.table(data.results);
  } catch(error) {
    console.log(error);
  }
};

getMovies();
```