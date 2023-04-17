# BookExchange
<!DOCTYPE html>
<html>
<head>
	<title>Book Exchange</title>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<link rel="stylesheet" href="style.css">
</head>
<body>
	<header>
		<h1>Book Exchange</h1>
		<nav>
			<ul>
				<li><a href="#">Home</a></li>
				<li><a href="#">Browse Books</a></li>
				<li><a href="#">Profile</a></li>
				<li><a href="#">Log Out</a></li>
			</ul>
		</nav>
	</header>

	<main>
		<section id="search-bar">
			<form>
				<input type="text" name="search" placeholder="Search for a book...">
				<button type="submit">Search</button>
			</form>
		</section>

		<section id="book-listings">
			<h2>Available Books</h2>
			<ul>
				<li>
					<img src="book-cover.jpg" alt="Book Cover">
					<h3>Title of Book</h3>
					<p>Author Name</p>
					<p>Description of Book</p>
					<button>Request Book</button>
					<button>Add to Wishlist</button>
				</li>
				<!-- Repeat for more books -->
			</ul>
		</section>
	</main>

	<footer>
		<p>&copy; 2021 Book Exchange. All rights reserved.</p>
	</footer>
</body>
</html>

body {
	margin: 0;
	padding: 0;
	font-family: Arial, sans-serif;
}

header {
	background-color: #333;
	color: #fff;
	padding: 1em;
	display: flex;
	justify-content: space-between;
	align-items: center;
}

nav ul {
	list-style: none;
	padding: 0;
	margin: 0;
	display: flex;
}

nav li {
	margin-left: 1em;
}

nav a {
	color: #fff;
	text-decoration: none;
}

main {
	max-width: 800px;
	margin: 0 auto;
	padding: 2em;
}

#search-bar {
	margin-bottom: 2em;
}

#search-bar input[type="text"] {
	padding: 0.5em;
	width: 50%;
	border: none;
	border-radius: 5px;
}

#search-bar button[type="submit"] {
	padding: 0.5em;
	background-color: #333;
	color: #fff;
	border: none;
	border-radius: 5px;
	margin-left: 1em;
	cursor: pointer;
}

#book-listings {
	margin-bottom: 2em;
}

#book-listings h2 {
	margin-bottom: 1em;
}

#book-listings ul {
	list-style: none;
	padding: 0;
	margin: 0;
}

#book-listings li {
	margin-bottom: 2em;
	display: flex;
	align-items: center;
}

#book-listings img {
	width: 100px;
	margin-right: 1em;
}

#book-listings h3 {
	margin-bottom: 0.5em;
}

#book-listings p {
	margin-bottom: 1em;
}

#book-listings button {
	padding: 0.5em;
	background-color: #333;
	color: #fff;
	border: none;
	border-radius: 5px;
	margin-right: 1em;
	cursor: pointer;
}

footer {
	background-color: #333;
	color: #fff;
	padding: 1em;
	text-align: center;
}

// Define variables
const searchForm = document.querySelector('form');
const searchInput = document.querySelector('input[name="search"]');
const bookListings = document.querySelector('#book-listings ul');

// Define function to display book listings
function displayBooks() {
	// Clear previous book listings
	bookListings.innerHTML = '';

	// Create new book listings
	for (let i = 0; i < books.length; i++) {
		const book = books[i];

		// Check if book matches search term
		if (book.title.toLowerCase().includes(searchInput.value.toLowerCase())) {
			// Create HTML elements for book listing
			const li = document.createElement('li');
			const img = document.createElement('img');
			const h3 = document.createElement('h3');
			const author = document.createElement('p');
			const description = document.createElement('p');
			const requestBtn = document.createElement('button');
			const wishlistBtn = document.createElement('button');

			// Add content to HTML elements
			img.src = book.cover;
			img.alt = book.title;
			h3.textContent = book.title;
			author.textContent = `by ${book.author}`;
			description.textContent = book.description;
			requestBtn.textContent = 'Request Book';
			wishlistBtn.textContent = 'Add to Wishlist';

			// Add event listeners to buttons
			requestBtn.addEventListener('click', () => {
				alert(`You have requested ${book.title}`);
			});
			wishlistBtn.addEventListener('click', () => {
				alert(`You have added ${book.title} to your wishlist`);
			});

			// Append HTML elements to book listing
			li.appendChild(img);
			li.appendChild(h3);
			li.appendChild(author);
			li.appendChild(description);
			li.appendChild(requestBtn);
			li.appendChild(wishlistBtn);

			// Append book listing to book listings
			bookListings.appendChild(li);
		}
	}
}

// Define function to handle search form submission
function handleSearch(event) {
	event.preventDefault();
	displayBooks();
}

// Add event listener to search form
searchForm.addEventListener('submit', handleSearch);

// Define sample book data
const books = [
	{
		title: 'To Kill a Mockingbird',
		author: 'Harper Lee',
		description: 'A young girl growing up in a small Southern town during the 1930s learns the importance of tolerance and justice.',
		cover: '<https://images-na.ssl-images-amazon.com/images/I/51aV9G3N4WL._SX331_BO1,204,203,200_.jpg>'
	},
	{
		title: 'The Great Gatsby',
		author: 'F. Scott Fitzgerald',
		description: 'A millionaire throws extravagant parties in hopes of impressing his former love, but the truth about his past and present threaten to ruin everything.',
		cover: '<https://images-na.ssl-images-amazon.com/images/I/41jEbEJ+L9L._SX331_BO1,204,203,200_.jpg>'
	},
	{
		title: 'Pride and Prejudice',
		author: 'Jane Austen',
		description: 'The five Bennet sisters must navigate the complexities of love, marriage, and social status in Regency England.',
		cover: '<https://images-na.ssl-images-amazon.com/images/I/51rT3T1yKDL._SX308_BO1,204,203,200_.jpg>'
	}
];

// Display initial book listings
displayBooks();
