# Movie_Details
Get the details of the searched movie

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="style1.css">
</head>
<body>
    <div class="search">
        <input type="text" id="movieName" placeholder="Search any movie by its name...">
        <button class="btn" onclick="searchMovie()">Search movie</button>
    </div>
    <div class="container">
        <div>
            <h2 id="title"></h2>
            <p id="desc"></p>
            <p>Genre: <span id="genre"></span></p>
            <p>Actors: <span id="actors"></span></p>
            <p>Directors: <span id="directors"></span></p>
            <p>Writers: <span id="writers"></span></p>
            <p>Box Office Collection: <span id="collection"></span></p>
            <p>Awards: <span id="awards"></span></p>
            <p>IMDB Ratings: <span id="ratings"></span></p>
        </div>
        <img src="" id="poster" alt="">
    </div>
    <script src="app1.js"></script>
</body>
</html>

let api = 'https://www.omdbapi.com/?i=tt3896198&apikey=f23d97d6&t='
function searchMovie(){
    let query = document.getElementById('movieName').value;
    let search = api+query;
    fetch(search).then(function(data){
        return data.json()
    }).then(function(data){
        document.getElementById('title').innerText = data.Title;
        document.getElementById('desc').innerText = data.Plot;
        document.getElementById('genre').innerText = data.Genre;
        document.getElementById('actors').innerText = data.Actors;
        document.getElementById('directors').innerText = data.Director;
        document.getElementById('awards').innerText = data.Awards;
        document.getElementById('collection').innerText = data.BoxOffice;
        document.getElementById('ratings').innerText = data.imdbRating;
        document.getElementById('writers').innerText = data.Writer;
        document.getElementById('poster').src = data.Poster;
    })
}


