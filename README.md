## Movies API

**Movies** is a simple static API designed for IT students who want to get 
familiar with using APIs in web applications.

### How to use

You can use ```fetch``` (more [here](https://github.com/mrspecht/fetch-api)) to 
access the list of movies provided by the API. This list, an array of objects, 
is returned by ```results```.

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
    const data = await response.json();
    // Printing the movies
    console.table(data.results);
  } catch(error) {
    console.log(error);
  }
};

getMovies();
```