# http portfolio

## 1. Write code that executes asynchronously

Asynchronous code has real value in providing a seamless experience for the user when dealing with HTTP requests as they can take some time. Using asynchronous code here works by moving the order of the single-threaded loop by which JavaScript runs so the user is not left waiting for each response one-by-one.  

```js
function showMovies(url){
    fetch(url).then(res=>res.json())
    .then(function(data){
        if(data.results.length){
            data.results.forEach(element=>{
                if(element.poster_path){
                    const el = document.createElement('div');
                    const image = document.createElement('img');
                    const text = document.createElement('p');
```

## 2. Use callbacks to access values that aren’t available synchronously

Callback functions are passed into another function whereby the callback will be called upon at the appropriate time. 

As with the `showMovies()` function above

## 3. Use promises to access values that aren’t available synchronously

Promises are objects that represent the eventual outcome of an asynchronous operation.

As learnt in the [promises workshop](https://learn.foundersandcoders.com/workshops/promise-practice/) as part of this module:
> Promises make it easier to run code in sequence. A promise object’s .then method returns a new promise that resolves with whatever value you returned from the callback you passed in.



## 4. Use the fetch method to make HTTP requests and receive responses

The above `showMovies()` function makes an HTTP request by fetching the data and then displaying the results if the request is successful. 

Our group chose to work with the TMDB api, along with the Marvel Database api. 

```js!
const searchApi = `https://api.themoviedb.org/3/search/movie?&api_key=${myApi}&query=`

```

with the request handled here:

```js
function handleEvents(){
    if(window.navigator.onLine){
        resultsHub.style.display = "block";
        searchHub.style.display = "none";
        const title = search.value;
        if(title){
            searchTitle.innerText = `showing results for "${title}"`;
            showMovies(searchApi+title);
            search.value = ""
        }
```


## 5. Configure the options argument of the fetch method to make GET and POST requests

## 6. Use the map array method to create a new array containing new values

## 7. Use the filter array method to create a new array with certain values removed

## 8. Access DOM nodes using a variety of selectors

## 9. Add and remove DOM nodes to change the content on the page

I used the `.appendChild` and `.createElement` methods to append the DOM nodes of data results to be displayed to the user. 

```js
if(data.results.length){
            data.results.forEach(element=>{
                if(element.poster_path){
                    const el = document.createElement('div');
                    const image = document.createElement('img');
                    const text = document.createElement('p');

                    text.innerHTML = `${element.title}`;
                    image.src = filmImgs + element.poster_path;
                    el.appendChild(image);
                    el.appendChild(text);
                    el.onclick= ()=>showDetails(element);
                    results.appendChild(el)
                }
            });
```

## 10. Toggle the classes applied to DOM nodes to change their CSS properties

## 11. Use consistent layout and spacing

I used CSS to display and hide the results or lack of depending on the search submitted. When selected, films are displayed in the same rendered format in a pop-up panel box. The full results would are listed in an inline-block format. This works, but upon review, using CSS grid would work better here. 

The CSS is organised by its styled elements. Here is a snippet of the film info panels:

```css
#film-info-panel{
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background: rgba(128,128,128,0.71);
  display: none;
  justify-content: center;
  align-items: center;
}
#panel{
  width: 50rem;
  height: 50rem;
  position: relative;
  background: white;
  font-family: sans-serif;
}
```

Again, this ensures consistency in film display - with its unique content filled in by JavaScript functionality. 

```js
function showDetails(element){
    body.style.overflow ="hidden"
    filmInfoPanel.style.display ="flex";
    img.src = filmImgs + element.poster_path;
    title.innerHTML = `${element.title}`;
    panelName.innerHTML = `${element.title}`;
    date.innerHTML = `${element.release_date}`;
    rating.innerHTML = `${element.vote_average}`;
    description.innerHTML = `${element.overview}`;
    language.innerHTML = `${element.original_language}`
}

```

## 12. Follow a spacing guideline to give our app a consistent feel

## 13. Debug client side JS in our web browser

## 14. Use console.log() to help us debug our code

We faced an issue where our two APIs were not displaying a paired set of fetched results. To work out the issue, we used `console.log()` to ensure the data submitted was received. 

```js
console.log(title);
form.addEventListener('submit',(e)=>{
    e.preventDefault();
    handleEvents();
})
```
