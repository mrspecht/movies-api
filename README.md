## Movies API

**Movies** is a simple API (Application Programming Interface) designed 
for IT students who want to get familiar with using APIs in web applications.

### How to use

You can use ```fetch``` (learn [here](https://github.com/mrspecht/fetch-api)) to 
access the list of movies provided by the API. The list - an array of objects - 
is in the ```results``` object.

```javascript
const url = 'https://api.andrespecht.dev/movies';

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

### Movie object

```javascript
{
  "title": "Jurassic Park",
  "year": 1993,
  "runningTime": "2h 7m",
  "genre": ["Adventure", "Action", "Sci-Fi"],
  "img": "https://raw.githubusercontent.com/mrspecht/media/main/img/jurassic-park.jpg"
}
```
