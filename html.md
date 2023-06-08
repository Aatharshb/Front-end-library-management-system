# Front-end-library-management-system
<!DOCTYPE html>
<html>
<head>
  <title>Library Management System</title>
  <style>
    /* Add your custom CSS styles here */
  </style>
</head>
<body>
  <h1>Library Management System</h1>

  <div>
    <label for="book-title">Title:</label>
    <input type="text" id="book-title" />

    <label for="book-author">Author:</label>
    <input type="text" id="book-author" />

    <button onclick="addBook()">Add Book</button>
  </div>

  <table id="book-table">
    <tr>
      <th>Title</th>
      <th>Author</th>
      <th>Action</th>
    </tr>
  </table>

  <script>
    // Array to store book objects
    var books = [];

    function addBook() {
      var title = document.getElementById('book-title').value;
      var author = document.getElementById('book-author').value;

      // Create a book object
      var book = {
        title: title,
        author: author
      };

      // Add book to the array
      books.push(book);

      // Update the book table
      updateBookTable();

      // Clear the input fields
      document.getElementById('book-title').value = '';
      document.getElementById('book-author').value = '';
    }

    function removeBook(index) {
      // Remove the book from the array
      books.splice(index, 1);

      // Update the book table
      updateBookTable();
    }

    function updateBookTable() {
      var table = document.getElementById('book-table');

      // Clear existing rows
      while (table.rows.length > 1) {
        table.deleteRow(1);
      }

      // Add new rows
      for (var i = 0; i < books.length; i++) {
        var row = table.insertRow(-1);
        var titleCell = row.insertCell(0);
        var authorCell = row.insertCell(1);
        var actionCell = row.insertCell(2);

        titleCell.innerHTML = books[i].title;
        authorCell.innerHTML = books[i].author;
        actionCell.innerHTML = '<button onclick="removeBook(' + i + ')">Remove</button>';
      }
    }
  </script>
</body>
</html>
