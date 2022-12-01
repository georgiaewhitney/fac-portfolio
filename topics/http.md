# http portfolio

## 1. Write code that executes asynchronously

Asynchronous code has real value in providing a seamless experience for the user by moving the order of the single-threaded loop by which JavaScript runs so the user is not left waiting.  

```html!
function showMovies(url){
    fetch(url).then(res=>res.json())
    .then(function(data)
```

## 2. Use callbacks to access values that aren’t available synchronously

One common example of asynchronicity in JavaScript is the use of asynchronous callbacks. This is a type of callback function that executes after a specific condition is met and runs concurrently to any other code currently running???

## 3. Use promises to access values that aren’t available synchronously

Promises are objects that represent the eventual outcome of an asynchronous operation.

## 4. Use the fetch method to make HTTP requests and receive responses

```html!
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

## 5. Configure the options argument of the fetch method to make GET and POST requests

## 6. Use the map array method to create a new array containing new values

## 7. Use the filter array method to create a new array with certain values removed

## 8. Access DOM nodes using a variety of selectors

## 9. Add and remove DOM nodes to change the content on the page

## 10. Toggle the classes applied to DOM nodes to change their CSS properties

## 11. Use consistent layout and spacing

## 12. Follow a spacing guideline to give our app a consistent feel

## 13. Debug client side JS in our web browser

## 14. Use console.log() to help us debug our code
