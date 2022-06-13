#PROJECT NAME: BOOKSHELF PROJECT
##This project allows user to create, update, get,  and delete books from a bookshelf database.





#API DOCUMENTATION
##GETTING STARTED
#BASE URL
This API is still used in development mode, since it has not been hosted. Therefore, our url is still the local host. http://127.0.0.1:5000/

#Authentication
There is no authentication or API key currently for this API
##EROR HANDLING
Errors are returned in JSON form in the following format

{
    'success': False,
    'error': 405,
    'message': 'Method Not Allowed'
}

The error status code in this API currently are 404 and 422
1. 404: Resource not Found
2. 422: Could not process request
##ENDPOINT LIBRARY
#GET/books
        1. Returns a list of books from the database, with a success message and the total number of books.
        2. Books are paginated into groups of 8
    Sample: curl http://127.0.0.1:5000/books
    {
    "books": [
        {
        "author": "Stephen King",
        "id": 1,
        "rating": 5,
        "title": "The Outsider: A Novel"
        },
        {
        "author": "Lisa Halliday",
        "id": 2,
        "rating": 4,
        "title": "Asymmetry: A Novel"
        },
        {
        "author": "Kristin Hannah",
        "id": 3,
        "rating": 1,
        "title": "The Great Alone"
        },
        {
        "author": "Tara Westover",
        "id": 4,
        "rating": 5,
        "title": "Educated: A Memoir"
        },
        {
        "author": "Jojo Moyes",
        "id": 5,
        "rating": 5,
        "title": "Still Me: A Novel"
        },
        {
        "author": "Leila Slimani",
        "id": 6,
        "rating": 2,
        "title": "Lullaby"
        },
        {
        "author": "Gina Apostol",
        "id": 9,
        "rating": 5,
        "title": "Insurrecto: A Novel"
        },
        {
        "author": "Tayari Jones",
        "id": 10,
        "rating": 1,
        "title": "An American Marriage"
        }
    ],
    "success": true,
    "total_books": 17
    }


#PATCH/books/<int:book_id>
        1. Update the rating of a book whose id has been passed as a variable to the url decorator. It returns a success status and the id of the updated book8
    Sample: curl http://127.0.0.1:5000/books/9 -X PATCH -H "Content-Type: application/json" -d '{"rating":"1"}'
    {
    "id": 9,       
    "success": true
    }

#DELETE/books/<int:book_id>
        1. Delete a book whose id has been passed as a variable to the url decorator. It returns a success status, id of the deleted book, the list of current books in the database, and the total number of books in the database
        2. Books are paginated into groups of 8
    Sample: curl -X DELETE http://127.0.0.1:5000/books/10
{
  "Total_books": 15,
  "books": [
    {
      "author": "Stephen King",
      "id": 1,
      "rating": 5,
      "title": "The Outsider: A Novel"
    },
    {
      "author": "Lisa Halliday",
      "id": 2,
      "rating": 4,
      "title": "Asymmetry: A Novel"
    },
    {
      "author": "Kristin Hannah",
      "id": 3,
      "rating": 1,
      "title": "The Great Alone"
    },
    {
      "author": "Tara Westover",
      "id": 4,
      "rating": 5,
      "title": "Educated: A Memoir"
    },
    {
      "author": "Jojo Moyes",
      "id": 5,
      "rating": 5,
      "title": "Still Me: A Novel"
    },
    {
      "author": "Leila Slimani",
      "id": 6,
      "rating": 2,
      "title": "Lullaby"
    },
    {
      "author": "Gina Apostol",
      "id": 9,
      "rating": 1,
      "title": "Insurrecto: A Novel"
    },
    {
      "author": "Jordan B. Peterson",
      "id": 11,
      "rating": 5,
      "title": "12 Rules for Life: An Antidote to Chaos"
    }
  ],
  "deleted": 10,
  "success": true
}

#POST/books
        1. Post a new book into the database. It returns a success status, the id of the created book, the list of books currently in the database, and the the total number of books in the database
        2. Books are paginated into groups of 8
    Sample: 