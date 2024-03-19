## Movies API

**Movies** is a simple API (Application Programming Interface) designed 
for IT students who want to get familiar with using APIs in web applications.

### How to use

You can use ```fetch``` (learn [here](https://github.com/mrspecht/fetch-api)) to 
access the list of movies provided by the API. The list - an array of objects - 
is in the ```response``` object.

```javascript
const URL = 'https://api.andrespecht.dev/movies';

const options = {
  method: 'GET',
  mode: 'cors'
};

async function getMovies() {
  try {
    const response = await fetch(URL, options);
    if (!response.ok) {
      throw new Error(`${response.statusText} (${response.status})`);
    }
    // Parsing the reponse as JSON
    const data = await response.json();
    // The 'response' object contains an array of movies
    console.table(data.response);
  } catch(error) {
    console.log(error);
  }
};

getMovies();
```

### Fetching a specific movie

```javascript
const options = {
  method: 'GET',
  mode: 'cors'
};

async function getMovie(movie) {
  const URL = `https://api.andrespecht.dev/movie/${movie}`;

  try {
    const response = await fetch(URL, options);
    if (!response.ok) {
      throw new Error(`${response.statusText} (${response.status})`);
    }
    // Parsing the reponse as JSON
    const data = await response.json();
    // The 'response' object contains one movie object
    console.log(data.response);
  } catch(error) {
    console.log(error);
  }
};

getMovie('jurassic-park');

// The resulting object
{
  "title": "Jurassic Park",
  "year": 1993,
  "runningTime": "2h 7m",
  "genre": ["Adventure", "Action", "Sci-Fi"],
  "img": "https://raw.githubusercontent.com/mrspecht/media/main/img/jurassic-park.jpg"
}
```