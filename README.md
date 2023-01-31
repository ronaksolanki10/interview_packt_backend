
# Packt Assessment (Backend)

A project is about to build a Backend for the bookstore where admin can add, edit, delete the books and customers can search for a book and see the whole details about the book

## Author

- [@ronaksolanki10](https://github.com/ronaksolanki10)


## Tech Stack

**Programming Language:** PHP

**Framework:** Laravel 9.19 (A PHP Framework for Web Artisan)

**Databse:** MySql


## Installation

Below is the steps to install the project

1. Clone the project
```bash
  git clone https://github.com/ronaksolanki10/interview_packt_backend.git
```
2. Install dependencies

```bash
  composer install
```
3. Copy ```.env.example``` to ```.env```

4. Set database credentials accordingly in ```.env``` file

4. Add database tables & pre configured records into database using below command

```bash
  php artisan migrate --seed
```
5. Generate the application key & clear the cache

```bash
  php artisan key:generate
  php artisan optimize:clear
```

6. Start laravel application if testing in local machine using below command and the URL will be used as ```Base URL``` for the APIs, if setupping on the server then use URL accordingly.

```
 php artisan serve

```


    
## API Reference

Note: Below headers are required to make successfull API request

```
  Content-Type: application/json
  Accept: application/json
```
## 1. Admin APIs

#### Login

```http
  GET /api/admin/login
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `email` | `string` | **Required**. |
| `password` | `string` | **Required**. |

We used ```Sanctum``` of Laravel (Bearer Token Authentication) to authorize Admin API requests hense pass below header to make successful request for the below all Admin APIs

```
   Authorization: Bearer <YOUR_TOKEN>
```
Replace ```<YOUR_TOKEN>``` with the token that your received from the ```/api/admin/login``` API response

#### List of books with filter

```http
  POST api/admin/books/list
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `page`      | `integer` | **Required**. Which page to return |
| `rowsPerPage`      | `integer` | **Required**. Records per page |
| `sortBy`      | `string` | **Required**. Order the records with selected column |
| `sortType`      | `string` | **Required**. Direction of the order |
| `search[title]`      | `string` | **Optional**. Filter records matching specified Title |
| `search[author]`      | `string` | **Optional**. Filter records matching specified Author |
| `search[published_on]`      | `date` | **Optional**. Filter records matching specified Published On Date|
| `search[isbn]`      | `integer` | **Optional**. Filter records matching specified ISBN |
| `search[genre]`      | `string` | **Optional**. Filter records matching specified Genre |

#### Add a new book

```http
  POST api/admin/books
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `title`      | `string` | **Required**. Title of the book |
| `author`      | `string` | **Required**. Author of the book |
| `published_on`      | `date` | **Required**.  Published On Date of the book|
| `publisher`      | `string` | **Required**.  Publisher of the book|
| `isbn`      | `integer` | **Required**. ISBN of the book |
| `genre`      | `string` | **Required**. Genre of the book |
| `description`      | `string` | **Required**. Description of the book |
| `image`      | `string` | **Required**. Image URL of the book |

#### Get a book details

```http
  GET /api/admin/books/{id}
```
```{id}``` - ID of the book

#### Update a book

```http
  POST api/admin/books/{id}
```
```{id}``` - ID of the book

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `_method`      | `string` | **Required**. Method of the API request and is fixed to : ```PUT``` |
| `title`      | `string` | **Required**. Title of the book |
| `author`      | `string` | **Required**. Author of the book |
| `published_on`      | `date` | **Required**.  Published On Date of the book|
| `publisher`      | `string` | **Required**.  Publisher of the book|
| `isbn`      | `integer` | **Required**. ISBN of the book |
| `genre`      | `string` | **Required**. Genre of the book |
| `description`      | `string` | **Required**. Description of the book |
| `image`      | `string` | **Required**. Image URL of the book |

#### Delete a book

```http
  DELETE /api/admin/books/{id}
```
```{id}``` - ID of the book

## 2. Frontend (Customer) APIs

#### List of books with filter

```http
  POST api/books/list
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `page`      | `integer` | **Required**. Which page to return |
| `rowsPerPage`      | `integer` | **Required**. Records per page |
| `sortBy`      | `string` | **Required**. Order the records with selected column |
| `sortType`      | `string` | **Required**. Direction of the order |
| `search[title]`      | `string` | **Optional**. Filter records matching specified Title |
| `search[author]`      | `string` | **Optional**. Filter records matching specified Author |
| `search[published_on]`      | `date` | **Optional**. Filter records matching specified Published On Date|
| `search[isbn]`      | `integer` | **Optional**. Filter records matching specified ISBN |
| `search[genre]`      | `string` | **Optional**. Filter records matching specified Genre |

#### Get a book details

```http
  GET /api/books/{id}
```
```{id}``` - ID of the book
## Feedback

If you have any feedback or query, please feel free to reach out to me at ronaksolanki1310@gmail.com

