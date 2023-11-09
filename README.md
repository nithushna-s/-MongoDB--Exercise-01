
**1. Create a Database called movies.**
use movies
 **2. Create a collection called moviedetails.**
 db.collections("moviedetails")
**3. Create above 5 movie documents into a moviedetails collection.**
db.moviedetails.insertMany([{ "Movie-Title": "Jurassic Park", "Genre/Type": "Adventure" , "Director": "Steven Spielberg" , "Release Year": 1993 },{ "Movie-Title": "Forrest Gump", "Genre/Type": "Drama" , "Director": "Robert Zemeckies" , "Release Year": 1994 }, { "Movie-Title": "Titanic", "Genre/Type": "Romance", "Director": "James Cameron", "Release Year": 1997 }, { "Movie-Title": "The Dark Knight", "Genre/Type": "Action", "Director": "Christopher Nolan", "Release Year": 2008 },{ "Movie-Title": "Avatar", "Genre/Type": "Science Fiction", "Director": "James Cameron", "Release Year": 2009 }])
**4. List all documents created.**
moviesDB> db.moviedetails.find()
[
  {
    _id: ObjectId("654c8abc924d9342ba84368c"),
    'Movie-Title': 'Jurassic Park',
    'Genre/Type': 'Adventure',
    Director: 'Steven Spielberg',
    'Release Year': 1993
  },
  {
    _id: ObjectId("654c8abc924d9342ba84368d"),
    'Movie-Title': 'Forrest Gump',
    'Genre/Type': 'Drama',
    Director: 'Robert Zemeckies',
    'Release Year': 1994
  },
  {
    _id: ObjectId("654c8abc924d9342ba84368e"),
    'Movie-Title': 'Titanic',
    'Genre/Type': 'Romance',
    Director: 'James Cameron',
    'Release Year': 1997
  },
  {
    _id: ObjectId("654c8abc924d9342ba84368f"),
    'Movie-Title': 'The Dark Knight',
    'Genre/Type': 'Action',
    Director: 'Christopher Nolan',
    'Release Year': 2008
  },
  {
    _id: ObjectId("654c8abc924d9342ba843690"),
    'Movie-Title': 'Avatar',
    'Genre/Type': 'Science Fiction',
    Director: 'James Cameron',
    'Release Year': 2009
  }
]

**5. List James Cameron’s movies.**
moviesDB> db.moviedetails.find({"Director": "James Cameron"})
[
  {
    _id: ObjectId("654c8abc924d9342ba84368e"),
    'Movie-Title': 'Titanic',
    'Genre/Type': 'Romance',
    Director: 'James Cameron',
    'Release Year': 1997
  },
  {
    _id: ObjectId("654c8abc924d9342ba843690"),
    'Movie-Title': 'Avatar',
    'Genre/Type': 'Science Fiction',
    Director: 'James Cameron',
    'Release Year': 2009
  }
]

**6. List  James Cameron’s movies released in 2009.**
moviesDB> db.moviedetails.find({"Director": "James Cameron" ,"Release Year": 2009})
[
  {
    _id: ObjectId("654c8abc924d9342ba843690"),
    'Movie-Title': 'Avatar',
    'Genre/Type': 'Science Fiction',
    Director: 'James Cameron',
    'Release Year': 2009
  }
]

**7. Delete the movie which you don’t like.**
moviesDB> db.moviedetails.remove({'Movie-Title': 'Avatar'})
DeprecationWarning: Collection.remove() is deprecated. Use deleteOne, deleteMany, findOneAndDelete, or bulkWrite.
{ acknowledged: true, deletedCount: 1 }
moviesDB>  db.moviedetails.find()
[
  {
    _id: ObjectId("654c8abc924d9342ba84368c"),
    'Movie-Title': 'Jurassic Park',
    'Genre/Type': 'Adventure',
    Director: 'Steven Spielberg',
    'Release Year': 1993
  },
  {
    _id: ObjectId("654c8abc924d9342ba84368d"),
    'Movie-Title': 'Forrest Gump',
    'Genre/Type': 'Drama',
    Director: 'Robert Zemeckies',
    'Release Year': 1994
  },
  {
    _id: ObjectId("654c8abc924d9342ba84368e"),
    'Movie-Title': 'Titanic',
    'Genre/Type': 'Romance',
    Director: 'James Cameron',
    'Release Year': 1997
  },
  {
    _id: ObjectId("654c8abc924d9342ba84368f"),
    'Movie-Title': 'The Dark Knight',
    'Genre/Type': 'Action',
    Director: 'Christopher Nolan',
    'Release Year': 2008
  }
]

**8. Add the movie which is your favourite.**
moviesDB> db.moviedetails.insertOne({"Movie-Title":"leo","Genre/Type":"Action","Director":"lk","Release Year":"2023"})
{
  acknowledged: true,
  insertedId: ObjectId("654ca2f61046f5637d01e43e")
}
moviesDB> show collections
moviedetails
moviesDB> db.moviedetails.find()
[
  {
    _id: ObjectId("654c8abc924d9342ba84368c"),
    'Movie-Title': 'Jurassic Park',
    'Genre/Type': 'Adventure',
    Director: 'Steven Spielberg',
    'Release Year': 1993
  },
  {
    _id: ObjectId("654c8abc924d9342ba84368d"),
    'Movie-Title': 'Forrest Gump',
    'Genre/Type': 'Drama',
    Director: 'Robert Zemeckies',
    'Release Year': 1994
  },
  {
    _id: ObjectId("654c8abc924d9342ba84368e"),
    'Movie-Title': 'Titanic',
    'Genre/Type': 'Romance',
    Director: 'James Cameron',
    'Release Year': 1997
  },
  {
    _id: ObjectId("654c8abc924d9342ba84368f"),
    'Movie-Title': 'The Dark Knight',
    'Genre/Type': 'Action',
    Director: 'Christopher Nolan',
    'Release Year': 2008
  },
  {
    _id: ObjectId("654ca2f61046f5637d01e43e"),
    'Movie-Title': 'leo',
    'Genre/Type': 'Action',
    Director: 'lk',
    'Release Year': '2023'
  }
]

**9.List movie Directed  by Christopher Nolan in 1994.**
moviesDB> db.moviedetails.find({"Movie-Title":"Christopher Nolan","Release Year": 1994})
**10.List out the Director’s Name in your document.**
moviesDB>  db.moviedetails.distinct("Director")
[
  'Christopher Nolan',
  'James Cameron',
  'Robert Zemeckies',
  'Steven Spielberg',
  'lk'
]

