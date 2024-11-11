*******************************XML**********************************************
<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet type="text/xsl" href="books.xsl"?>
<books>
    <book>
        <title>The Great Gatsby</title>
        <author>F. Scott Fitzgerald</author>
        <isbn>9780743273565</isbn>
        <publisher>Scribner</publisher>
        <edition>1st</edition>
        <price>10.99</price>
    </book>
    <book>
        <title>1984</title>
        <author>George Orwell</author>
        <isbn>9780451524935</isbn>
        <publisher>Signet Classics</publisher>
        <edition>1st</edition>
        <price>9.99</price>
    </book>
    <book>
        <title>Sapiens: A Brief History of Humankind</title>
        <author>Yuval Noah Harari</author>
        <isbn>9780062316097</isbn>
        <publisher>Harper</publisher>
        <edition>1st</edition>
        <price>14.99</price>
    </book>
    <book>
        <title>Educated</title>
        <author>Tara Westover</author>
        <isbn>9780399590504</isbn>
        <publisher>Random House</publisher>
        <edition>1st</edition>
        <price>12.99</price>
    </book>
</books>

//////////////////XSL File
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
    <xsl:output method="html" encoding="UTF-8" indent="yes"/>
    <xsl:template match="/">
        <html>
        <head>
            <title>Book Information</title>
            <link rel="stylesheet" type="text/css" href="styles.css"/>
        </head>
        <body>
            <h1>Book Information</h1>
            <table>
                <tr>
                    <th>Title</th>
                    <th class="author-header">Author</th>
                    <th>ISBN</th>
                    <th>Publisher</th>
                    <th>Edition</th>
                    <th>Price</th>
                </tr>
                <xsl:for-each select="books/book">
                    <tr>
                        <td class="title"><xsl:value-of select="title"/></td>
                        <td class="author"><xsl:value-of select="author"/></td>
                        <td class="isbn"><xsl:value-of select="isbn"/></td>
                        <td class="publisher"><xsl:value-of select="publisher"/></td>
                        <td class="edition"><xsl:value-of select="edition"/></td>
                        <td class="price"><xsl:value-of select="price"/></td>
                    </tr>
                </xsl:for-each>
            </table>
        </body>
        </html>
    </xsl:template>
</xsl:stylesheet>

//////////css
body {
    font-family: Arial, sans-serif;
}
h1 {
    text-align: center;
}
table {
    width: 100%;
    border-collapse: collapse;
    margin: 20px 0;
}
th {
    background-color: grey; /* Grey header background */
    color: white;
    padding: 10px;
}
td {
    padding: 10px;
    text-align: left;
}
.author {
    color: blue; /* Color for author names */
    font-weight: bold; /* Bold author names */
    text-transform: uppercase; /* Capitalize author names */
}
.title {
    color: darkgreen; /* Color for titles */
}
.isbn {
    color: darkorange; /* Color for ISBN numbers */
}
.publisher {
    color: darkviolet; /* Color for publishers */
}
.edition {
    color: darkred; /* Color for editions */
}
.price {
    color: purple; /* Color for prices */
}
td:nth-child(odd) {
    background-color: #f2f2f2; /* Light gray for odd rows */
}
td:nth-child(even) {
    background-color: #ffffff; /* White for even rows */
}

*******************MOUSE EVENT KEYBOARD EVENT************************************
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>HTML DOM Events</title>
        <style>
            body {
                font-family: Arial, sans-serif;
                margin: 20px;
                background-color: #f4f4f4;
            }
            h1 {
                color: #333;
            }
            h2 {
                font-size: 1.5em;
                color: #555;
            }
            #demo, #demo1, #demo2 {
                margin-top: 10px;
                font-size: 1.2em;
                color: #007BFF;
            }
            #myP {
                font-size: 1.2em;
                margin: 10px 0;
            }
            .droptarget {
                width: 100px; 
                height: 35px;
                padding: 10px;
                border: 1px solid black;
                margin: 10px 0;
                background-color: #e9ecef;
                text-align: center;
                line-height: 35px; /* Center text vertically */
            }
            img {
                transition: transform 0.2s;
            }
            img:hover {
                transform: scale(1.5); /* Increase size on hover */
            }
            input[type="text"], input[type="file"] {
                margin-top: 10px;
                padding: 5px;
                font-size: 1em;
                border: 1px solid #ccc;
                border-radius: 4px;
                width: calc(100% - 12px); /* Full width with padding */
            }
            button {
                padding: 10px 15px;
                font-size: 1em;
                color: white;
                background-color: #007BFF;
                border: none;
                border-radius: 4px;
                cursor: pointer;
            }
            button:hover {
                background-color: #0056b3; /* Darker blue on hover */
            }
        </style>
    </head>
    <body>
    <h1>HTML DOM Events</h1>
    <h2>The onclick Event</h2>
    <p>Click to trigger a function that will output "Hello World":</p>
    <button onclick="displayHello()">Click me</button>
    <p id="demo"></p>
    
    <script>
        function displayHello() {
            document.getElementById("demo").innerHTML = "Hello World";
        }
    </script>
    
    <h2>The ondblclick Event</h2>
    <p ondblclick="displayHelloAgain()">Double-click this paragraph to trigger a function.</p>
    <p id="demo1"></p>
    
    <script>
        function displayHelloAgain() {
            document.getElementById("demo1").innerHTML += "Hello World ";
        }
    </script>
    
    <h2>Mouse Events</h2>
    <p id="myP" onmousedown="mouseDown()" onmouseup="mouseUp()">
        The mouseDown() function sets the color of this text to red. 
        The mouseUp() function sets the color of this text to blue.
    </p>
    
    <script>
        function mouseDown() {
            document.getElementById("myP").style.color = "red";
        }
    
        function mouseUp() {
            document.getElementById("myP").style.color = "blue";
        }
    </script>
    
    <h2>The onmouseenter Event</h2>
    <p>Hover over the image:</p>
    <input type="file" id="imageInput" accept="image/*" onchange="loadImage(event)">
    <img id="dynamicImage" src="" alt="User Image" width="64" height="64" style="display:none;">
    
    <script>
        function loadImage(event) {
            const img = document.getElementById('dynamicImage');
            img.src = URL.createObjectURL(event.target.files[0]);
            img.style.display = "block";
        }
    </script>
    
    <h2>Keyboard Events</h2>
    <h2>The onkeydown Event</h2>
    <p>Press a key in the input field:</p>
    <input type="text" onkeydown="myFunction(this)">
    
    <script>
        function myFunction(element) {
            element.style.backgroundColor = "red"; // Change background color to red on key press
        }
    </script>
    
    <h2>The onkeypress Event</h2>
    <p>A function is triggered when the user is pressing a key in the input field:</p>
    <input type="text" id="keypressInput" onkeypress="alertKeyPress()">
    
    <script>
        function alertKeyPress() {
            alert("You pressed a key inside the input field");
        }
    </script>
    
    <h2>The onkeyup Event</h2>
    <p>A function is triggered when the user releases a key in the input field:</p>
    Enter your name: <input type="text" id="fname" onkeyup="transformInput()">
    
    <script>
        function transformInput() {
            let x = document.getElementById("fname");
            x.value = x.value.toUpperCase();
        }
    </script>
    
    <h2>The ondrag Event</h2>
    <p>Drag the text up and down between the two rectangles:</p>
    
    <div class="droptarget" ondrop="drop(event)" ondragover="allowDrop(event)">
        <p ondragstart="dragStart(event)" ondrag="dragging(event)" draggable="true" id="dragtarget">Drag me!</p>
    </div>
    
    <p id="demo"></p>
    
    <div class="droptarget" ondrop="drop(event)" ondragover="allowDrop(event)"></div>
    
    <script>
        function dragStart(event) {
            event.dataTransfer.setData("Text", event.target.id);
        }
    
        function dragging(event) {
            document.getElementById("demo").innerHTML = "The p element is being dragged";
        }
    
        function allowDrop(event) {
            event.preventDefault();
        }
    
        function drop(event) {
            event.preventDefault();
            const data = event.dataTransfer.getData("Text");
            event.target.appendChild(document.getElementById(data));
            document.getElementById("demo").innerHTML = "The p element was dropped";
        }
    </script>
    
    </body>
    </html>
    ************************HTML FILES***********************************************

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shopping Cart</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Your Shopping Cart</h1>
    </header>
    <main>
        <h2>Items in Cart</h2>
        <ul id="cartItems">
            <!-- Cart items will be populated here -->
        </ul>
        <a href="payment.html">Proceed to Payment</a>
        <button onclick="goBack()">Back</button>
    </main>
    <script src="script.js"></script>
</body>
</html>
//////////////////////////////////////////
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Books Catalog</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Books Catalog</h1>
    </header>
    <main>
        <div class="book-list">
            <div class="book-item">
                <h3>The Great Gatsby</h3>
                <p>Author: F. Scott Fitzgerald</p>
                <button onclick="addToCart('The Great Gatsby')">Add to Cart</button>
            </div>
            <div class="book-item">
                <h3>1984</h3>
                <p>Author: George Orwell</p>
                <button onclick="addToCart('1984')">Add to Cart</button>
            </div>
            <div class="book-item">
                <h3>Sapiens</h3>
                <p>Author: Yuval Noah Harari</p>
                <button onclick="addToCart('Sapiens')">Add to Cart</button>
            </div>
        </div>
        <a href="cart.html">View Shopping Cart</a>
        <button onclick="goBack()">Back</button>
    </main>
    <script src="script.js"></script>
</body>
</html>
//////////////////////////////////////////
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Order Confirmation</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Order Confirmation</h1>
    </header>
    <main>
        <h2>Thank you for your order, <span id="confirmedUserName"></span>!</h2>
        <p>Your order has been placed successfully.</p>
        <button onclick="goBack()">Back</button>
        <a href="index.html">Return to Home</a>
    </main>
    <script src="script.js"></script>
</body>
</html>
//////////////////////////////
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Online Bookstore</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Welcome to the Online Bookstore</h1>
        <nav>
            <a href="login.html">Login</a>
            <a href="registration.html">Register</a>
            <a href="catalog.html">Books Catalog</a>
            <a href="cart.html">Cart</a>
            <span id="userNav"></span>
        </nav>
    </header>
    <main>
        <h2>Featured Books</h2>
        <div class="book-categories">
            <div class="category">
                <h3>Fiction</h3>
                <ul>
                    <li>
                        <span>The Great Gatsby</span>
                        <button onclick="addToCart('The Great Gatsby')">Add to Cart</button>
                    </li>
                    <li>
                        <span>1984</span>
                        <button onclick="addToCart('1984')">Add to Cart</button>
                    </li>
                </ul>
            </div>
            <div class="category">
                <h3>Non-Fiction</h3>
                <ul>
                    <li>
                        <span>Sapiens: A Brief History of Humankind</span>
                        <button onclick="addToCart('Sapiens: A Brief History of Humankind')">Add to Cart</button>
                    </li>
                    <li>
                        <span>Educated</span>
                        <button onclick="addToCart('Educated')">Add to Cart</button>
                    </li>
                </ul>
            </div>
            <div class="category">
                <h3>Science Fiction</h3>
                <ul>
                    <li>
                        <span>Dune</span>
                        <button onclick="addToCart('Dune')">Add to Cart</button>
                    </li>
                    <li>
                        <span>Neuromancer</span>
                        <button onclick="addToCart('Neuromancer')">Add to Cart</button>
                    </li>
                </ul>
            </div>
        </div>
    </main>
    <footer>
        <p>&copy; 2023 Online Bookstore</p>
    </footer>
    <script src="script.js"></script>
</body>
</html>
////////////////////////////////
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>User Login</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>User Login</h1>
    </header>
    <main>
        <form id="loginForm" onsubmit="return handleLogin(event)">
            <label for="username">Username:</label>
            <input type="text" id="username" name="username" required>
            <label for="password">Password:</label>
            <input type="password" id="password" name="password" required>
            <button type="submit">Login</button>
        </form>
        <p>Don't have an account? <a href="register.html">Register here</a></p>
        <button onclick="goBack()">Back</button>
    </main>
    <script src="script.js"></script>
</body>
</html>
////////////////////////////////////////
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Payment</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Payment Information</h1>
    </header>
    <main>
        <h2>Select Payment Method</h2>
        <form id="paymentForm" onsubmit="return handlePayment(event)">
            <input type="radio" id="creditCard" name="paymentMethod" value="creditCard" checked>
            <label for="creditCard">Credit Card</label><br>
            <input type="radio" id="googlePay" name="paymentMethod" value="googlePay">
            <label for="googlePay">Google Pay</label><br>
            <input type="radio" id="phonePay" name="paymentMethod" value="phonePay">
            <label for="phonePay">Phone Pay</label><br>
            <button type="submit">Pay Now</button>
        </form>
        <button onclick="goBack()">Back</button>
    </main>
    <script src="script.js"></script>
</body>
</html>
///////////////////////////////
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>User Profile</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Your Profile</h1>
    </header>
    <main>
        <h2>Account Information</h2>
        <p>Username: <span id="userDisplayName"></span></p>
        <h3>Books Added to Your Profile:</h3>
        <ul id="addedBooksList">
            <!-- Books added will be populated here -->
        </ul>
        <button onclick="goBack()">Back</button>
        <a href="catalog.html">Continue Shopping</a>
    </main>
    <script src="script.js"></script>
</body>
</html>
//////////////////////////
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>User Registration</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>User Registration</h1>
    </header>
    <main>
        <form id="registrationForm" onsubmit="return handleRegistration(event)">
            <label for="registerUsername">Username:</label>
            <input type="text" id="registerUsername" name="username" required>
            <label for="registerPassword">Password:</label>
            <input type="password" id="registerPassword" name="password" required>
            <button type="submit">Register</button>
        </form>
        <p>Already have an account? <a href="login.html">Login here</a></p>
        <button onclick="goBack()">Back</button>
    </main>
    <script src="script.js"></script>
</body>
</html>
Script.js //////////////////////////////
let userName = localStorage.getItem("userName") || "";
let cartItems = JSON.parse(localStorage.getItem("cartItems")) || [];

function handleLogin(event) {
    event.preventDefault();
    const username = document.getElementById("username").value;
    localStorage.setItem("userName", username);
    window.location.href = "profile.html";
}

function handleRegistration(event) {
    event.preventDefault();
    const username = document.getElementById("registerUsername").value;
    localStorage.setItem("userName", username);
    window.location.href = "profile.html";
}

function handlePayment(event) {
    event.preventDefault();
    const paymentMethod = document.querySelector('input[name="paymentMethod"]:checked').value;
    alert(`Payment successful using ${paymentMethod}`);
    window.location.href = "confirmation.html";
}

function addToCart(book) {
    cartItems.push(book);
    localStorage.setItem("cartItems", JSON.stringify(cartItems));
    alert(`${book} added to cart!`);
}

function displayUserName() {
    document.getElementById("userDisplayName").innerText = userName;
    document.getElementById("confirmedUserName").innerText = userName;
}

function populateCart() {
    const cartList = document.getElementById("cartItems");
    if (cartItems.length === 0) {
        cartList.innerHTML = "<li>Your cart is empty.</li>";
    } else {
        cartItems.forEach(item => {
            const listItem = document.createElement("li");
            listItem.innerText = item;
            cartList.appendChild(listItem);
        });
    }
}

function populateProfileBooks() {
    const addedBooksList = document.getElementById("addedBooksList");
    if (cartItems.length === 0) {
        addedBooksList.innerHTML = "<li>No books added yet.</li>";
    } else {
        cartItems.forEach(item => {
            const listItem = document.createElement("li");
            listItem.innerText = item;
            addedBooksList.appendChild(listItem);
        });
    }
}

function updateNav() {
    const userNav = document.getElementById("userNav");
    if (userName) {
        userNav.innerHTML = `Welcome, ${userName} | <a href="profile.html">Profile</a>`;
    } else {
        userNav.innerHTML = "";
    }
}
function goBack() {
    window.history.back();
}
document.addEventListener("DOMContentLoaded", () => {
    displayUserName();
    populateCart();
    populateProfileBooks();
    updateNav();
});
Styles.css//////////////////////////////////////////////////////////////////////////////////////
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 20px;
    background-color: #f9f9f9;
}

header {
    background: #343a40;
    color: white;
    padding: 10px 0;
    text-align: center;
}

nav {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 10px;
}

nav a {
    margin: 0 15px;
    color: white;
    text-decoration: none;
}

nav span {
    color: white;
    margin-left: 10px;
}

.book-categories, .book-list {
    display: flex;
    justify-content: space-around;
}

.category, .book-item {
    background: #007bff;
    color: white;
    padding: 15px;
    border-radius: 8px;
    width: 30%;
    margin: 10px 0;
}

.category ul, .book-list {
    list-style-type: none;
    padding: 0;
}

footer {
    text-align: center;
    margin-top: 20px;
}

button {
    background-color: #28a745;
    color: white;
    border: none;
    padding: 10px 15px;
    border-radius: 5px;
    cursor: pointer;
    margin-top: 10px;
}

button:hover {
    background-color: #218838;
}

form {
    display: flex;
    flex-direction: column;
    align-items: center;
}

label, input {
    margin: 5px 0;
}
****************************calculator**********************************************
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <style>
            body {
                font-family: Arial, sans-serif;
                background-color: #f4f4f4;
                margin: 0;
                padding: 20px;
            }
    
            h1 {
                color: #333;
            }
    
            form {
                background-color: #fff;
                padding: 20px;
                border-radius: 8px;
                box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
                max-width: 400px;
                margin: auto;
            }
    
            label {
                font-weight: bold;
                display: block;
                margin-bottom: 5px;
            }
    
            input[type="text"] {
                width: calc(100% - 22px);
                padding: 10px;
                margin-bottom: 15px;
                border: 1px solid #ccc;
                border-radius: 4px;
            }
    
            input[type="button"] {
                background-color: #5cb85c;
                color: white;
                border: none;
                padding: 10px 15px;
                border-radius: 4px;
                cursor: pointer;
                margin: 5px 0;
                width: 48%;
            }
    
            input[type="button"]:hover {
                background-color: #4cae4c;
            }
    
            p {
                font-size: 18px;
                color: #333;
            }
    
            hr {
                margin: 20px 0;
            }
    
            .container {
                display: inline-block;
                margin: 5px 0;
            }
        </style>
    </head>
    <body>
        <form>
            <center>
                <h1>Simple Calculate</h1>
                <label>1st number:</label>
                <input type="text" id="firstnum" class="container"><br><br>
                <label>2nd number:</label>
                <input type="text" id="secondnum" class="container"><br><br>
                <label>Select operators:</label>
                <input type="button" onclick="add()" class="container" value="+">
                <input type="button" onclick="subtrction()" value="-" class="container">
                <input type="button" onclick="multipleBY()" value="*" class="container">
                <input type="button" onclick="divide()" value="/" class="container"><br><br>
                <label>Assignment operator:</label>
                <input type="button" onclick="assigment()" value="+=" class="container"><br><br>
                <label>Comparison operator:</label>
                <input type="button" onclick="comparison()" value="==" class="container"><br><br>
                <label>Relational operator:</label>
                <input type="button" onclick="relational()" value=">=" class="container"><br><br>
                <label>Logical operator:</label>
                <input type="button" onclick="logical()" value="||" class="container"><br><br>
                <hr>
                <p><strong>The Result is: <span id="result"></span></strong></p>
            </center>
        </form>
        <script>
            function add() {
                num1 = parseInt(document.getElementById("firstnum").value);
                num2 = parseInt(document.getElementById("secondnum").value);
                document.getElementById("result").innerHTML = num1 + num2;
            }
            
            function subtrction() {
                num1 = document.getElementById("firstnum").value;
                num2 = document.getElementById("secondnum").value;
                document.getElementById("result").innerHTML = num1 - num2;
            }
            
            function multipleBY() {
                num1 = document.getElementById("firstnum").value;
                num2 = document.getElementById("secondnum").value;
                document.getElementById("result").innerHTML = num1 * num2;
            }
            
            function divide() {
                num1 = document.getElementById("firstnum").value;
                num2 = document.getElementById("secondnum").value;
                document.getElementById("result").innerHTML = num1 / num2;
            }
            
            function assigment() {
                num1 = parseInt(document.getElementById("firstnum").value);
                num2 = parseInt(document.getElementById("secondnum").value);
                document.getElementById("result").innerHTML = num1 += num2;
            }
            
            function comparison() {
                num1 = document.getElementById("firstnum").value;
                num2 = document.getElementById("secondnum").value;
                document.getElementById("result").innerHTML = num1 != num2;
            }
            
            function relational() {
                num1 = document.getElementById("firstnum").value;
                num2 = document.getElementById("secondnum").value;
                document.getElementById("result").innerHTML = num1 >= num2;
            }
            
            function logical() {
                num1 = document.getElementById("firstnum").value;
                num2 = document.getElementById("secondnum").value;
                document.getElementById("result").innerHTML = num1 + num2 || num2 + num1;
            }
        </script>
    </body>
    </html>
*********************dom,rows,carousel,form,glyphicons********************************
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Combined Bootstrap Components with Form Validation</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css">
    <style>
        body {
            padding: 20px;
            background-color: #f4f4f4;
        }
        h1 {
            margin-bottom: 20px;
        }
        .container {
            margin-bottom: 40px;
            background: white;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }
        .table {
            margin-top: 20px;
        }
        .navbar {
            margin-bottom: 20px;
        }
        .search-input {
            width: 250px;
        }
        .image-preview {
            margin-top: 10px;
        }
        .img-thumbnail {
            margin-right: 10px;
            margin-bottom: 10px;
        }
    </style>
</head>
<body>

<nav class="navbar navbar-expand-lg navbar-light bg-light">
    <a class="navbar-brand" href="#">Navbar</a>
    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
            <li class="nav-item active">
                <a class="nav-link" href="#">Home</a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="#">Features</a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="#">Pricing</a>
            </li>
        </ul>
        <form class="form-inline ml-auto">
            <input class="form-control search-input" type="search" placeholder="Search" aria-label="Search">
            <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
        </form>
    </div>
</nav>

<div class="container">
    <h1>User Registration</h1>
    <form id="dataForm">
        <label for="txtname">Name</label>
        <input type="text" id="txtname" required placeholder="Enter Name" class="form-control">
        <br>
        <label for="num">Mobile Number</label>
        <input type="number" id="num" required placeholder="Enter mobile number" class="form-control">
        <br>
        <label for="pwd">Password</label>
        <input type="password" id="pwd" required placeholder="Enter Password" class="form-control">
        <br>
        <label for="cpwd">Confirm Password</label>
        <input type="password" id="cpwd" required placeholder="Re-type the password" class="form-control">
        <br>
        <input type="button" id="btn" value="Submit" class="btn btn-primary" onclick="fnDisplay()">
    </form>

    <table class="table table-striped" id="dataTable">
        <thead>
            <tr>
                <th>#</th>
                <th>Name</th>
                <th>Mobile Number</th>
            </tr>
        </thead>
        <tbody>
            <!-- Dynamic data will be inserted here -->
        </tbody>
    </table>
</div>

<div class="container">
    <h1>Upload Images</h1>
    <form id="imageForm">
        <div class="form-group">
            <label for="imageInput1">Select Image 1</label>
            <input type="file" class="form-control-file" id="imageInput1" accept="image/*" onchange="loadImage(event, 'imagePreview1')">
        </div>
        <div class="form-group">
            <label for="imageInput2">Select Image 2</label>
            <input type="file" class="form-control-file" id="imageInput2" accept="image/*" onchange="loadImage(event, 'imagePreview2')">
        </div>
        <div class="form-group">
            <label for="imageInput3">Select Image 3</label>
            <input type="file" class="form-control-file" id="imageInput3" accept="image/*" onchange="loadImage(event, 'imagePreview3')">
        </div>
    </form>
    <div class="image-preview">
        <h5>Image Previews:</h5>
        <img id="imagePreview1" class="img-thumbnail" style="display:none;" alt="Image Preview 1">
        <img id="imagePreview2" class="img-thumbnail" style="display:none;" alt="Image Preview 2">
        <img id="imagePreview3" class="img-thumbnail" style="display:none;" alt="Image Preview 3">
    </div>
</div>

<div class="container">
    <h1>Images with Icons</h1>
    <img src="https://via.placeholder.com/150" alt="Placeholder Image" class="img-thumbnail">
    <i class="fas fa-check-circle" aria-hidden="true" style="font-size: 1.5em; margin-right: 10px;"></i>
    <i class="fas fa-times-circle" aria-hidden="true" style="font-size: 1.5em; margin-right: 10px;"></i>
    <i class="fas fa-info-circle" aria-hidden="true" style="font-size: 1.5em; margin-right: 10px;"></i>
    <i class="fas fa-exclamation-circle" aria-hidden="true" style="font-size: 1.5em; margin-right: 10px;"></i>
    <i class="fas fa-question-circle" aria-hidden="true" style="font-size: 1.5em; margin-right: 10px;"></i>
    <i class="fas fa-spinner" aria-hidden="true" style="font-size: 1.5em; margin-right: 10px;"></i>
    <i class="fas fa-star" aria-hidden="true" style="font-size: 1.5em; margin-right: 10px;"></i>
    <i class="fas fa-heart" aria-hidden="true" style="font-size: 1.5em; margin-right: 10px;"></i>
</div>

<div class="container">
    <h1>Row and Container Classes</h1>
    <form id="rowForm">
        <div class="form-group">
            <label for="leftColumnText">Left Column Text</label>
            <input type="text" class="form-control" id="leftColumnText" placeholder="Enter text for left column" required>
        </div>
        <div class="form-group">
            <label for="rightColumnText">Right Column Text</label>
            <input type="text" class="form-control" id="rightColumnText" placeholder="Enter text for right column" required>
        </div>
        <button type="button" class="btn btn-primary" onclick="addToRow()">Add to Row</button>
    </form>
    <div class="row" id="dynamicRow">
        <div class="col-md-6">
            <div class="alert alert-primary" role="alert" id="leftColumn" style="display:none;">Left Column Content</div>
        </div>
        <div class="col-md-6">
            <div class="alert alert-secondary" role="alert" id="rightColumn" style="display:none;">Right Column Content</div>
        </div>
    </div>
</div>

<script>
    function fnDisplay() {
        var v1 = document.getElementById("txtname").value;
        var v2 = document.getElementById("num").value;
        var v3 = document.getElementById("pwd").value;
        var v4 = document.getElementById("cpwd").value;

        if (v1 == null || v1 == "") {
            alert("Please enter your name");
        } else if (v2.length < 10) {
            alert("Mobile number must be 10 digits");
        } else if (v3 === v4) {
            // Add data to the table
            const table = document.getElementById('dataTable').getElementsByTagName('tbody')[0];
            const newRow = table.insertRow(table.rows.length);
            newRow.insertCell(0).innerHTML = table.rows.length; // Row number
            newRow.insertCell(1).innerHTML = v1;
            newRow.insertCell(2).innerHTML = v2;

            // Clear the input fields
            document.getElementById('dataForm').reset();
        } else {
            alert("Passwords do not match");
        }
    }

    function loadImage(event, previewId) {
        const img = document.getElementById(previewId);
        img.src = URL.createObjectURL(event.target.files[0]);
        img.style.display = "block";
    }

    function addToRow() {
        const leftText = document.getElementById('leftColumnText').value;
        const rightText = document.getElementById('rightColumnText').value;

        if (leftText && rightText) {
            document.getElementById('leftColumn').innerText = leftText;
            document.getElementById('rightColumn').innerText = rightText;
            document.getElementById('leftColumn').style.display = 'block';
            document.getElementById('rightColumn').style.display = 'block';

            // Clear the input fields
            document.getElementById('rowForm').reset();
        } else {
            alert("Please fill in both fields.");
        }
    }
</script>

<script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.6/dist/umd/popper.min.js"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
</body>
</html>
************php*******************************************************************
Index.php////////
<?php
// Database connection
$servername = "localhost"; // Adjust if needed
$username = "root"; // Your database username
$password = ""; // Your database password
$dbname = "student_portal";

// Create connection
$conn = new mysqli($servername, $username, $password, $dbname);

// Check connection
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

// Insert data
if ($_SERVER['REQUEST_METHOD'] == 'POST' && isset($_POST['add_student'])) {
    $name = $_POST['name'];
    $course = $_POST['course'];
    $phone_number = $_POST['phone_number'];
    $email = $_POST['email'];

    $sql = "INSERT INTO students (name, course, phone_number, email) VALUES ('$name', '$course', '$phone_number', '$email')";
    $conn->query($sql);
}

// Delete data
if (isset($_GET['delete'])) {
    $id = $_GET['delete'];
    $conn->query("DELETE FROM students WHERE id=$id");
}

// Fetch data
$result = $conn->query("SELECT * FROM students");
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Student Portal</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
</head>
<body>
    <div class="container">
        <h1 class="mt-5">Welcome to Student Portal</h1>
        <h2>Student Add</h2>
        <form method="POST" class="mb-4">
            <div class="form-group">
                <label for="name">Name:</label>
                <input type="text" name="name" class="form-control" required>
            </div>
            <div class="form-group">
                <label for="course">Course:</label>
                <input type="text" name="course" class="form-control" required>
            </div>
            <div class="form-group">
                <label for="phone_number">Phone Number:</label>
                <input type="text" name="phone_number" class="form-control" required>
            </div>
            <div class="form-group">
                <label for="email">Email:</label>
                <input type="email" name="email" class="form-control" required>
            </div>
            <button type="submit" name="add_student" class="btn btn-primary">Add Student</button>
        </form>

        <h2>Student Details</h2>
        <table class="table">
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Name</th>
                    <th>Course</th>
                    <th>Phone Number</th>
                    <th>Email</th>
                    <th>Action</th>
                </tr>
            </thead>
            <tbody>
                <?php while($row = $result->fetch_assoc()): ?>
                <tr>
                    <td><?php echo $row['id']; ?></td>
                    <td><?php echo $row['name']; ?></td>
                    <td><?php echo $row['course']; ?></td>
                    <td><?php echo $row['phone_number']; ?></td>
                    <td><?php echo $row['email']; ?></td>
                    <td>
                        <a href="edit.php?id=<?php echo $row['id']; ?>" class="btn btn-warning btn-sm">Edit</a>
                        <a href="?delete=<?php echo $row['id']; ?>" class="btn btn-danger btn-sm">Delete</a>
                    </td>
                </tr>
                <?php endwhile; ?>
            </tbody>
        </table>
    </div>
</body>
</html>

<?php
$conn->close();
?>
////////////edit.php
<?php
// Database connection
$servername = "localhost"; // Adjust if needed
$username = "root"; // Your database username
$password = ""; // Your database password
$dbname = "student_portal";

$conn = new mysqli($servername, $username, $password, $dbname);

if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

// Fetch student data
$id = $_GET['id'];
$result = $conn->query("SELECT * FROM students WHERE id=$id");
$student = $result->fetch_assoc();

// Update data
if ($_SERVER['REQUEST_METHOD'] == 'POST' && isset($_POST['update_student'])) {
    $name = $_POST['name'];
    $course = $_POST['course'];
    $phone_number = $_POST['phone_number'];
    $email = $_POST['email'];

    $sql = "UPDATE students SET name='$name', course='$course', phone_number='$phone_number', email='$email' WHERE id=$id";
    $conn->query($sql);
    header("Location: index.php"); // Redirect after update
}
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Edit Student</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
</head>
<body>
    <div class="container">
        <h1 class="mt-5">Edit Student</h1>
        <form method="POST">
            <div class="form-group">
                <label for="name">Name:</label>
                <input type="text" name="name" class="form-control" value="<?php echo $student['name']; ?>" required>
            </div>
            <div class="form-group">
                <label for="course">Course:</label>
                <input type="text" name="course" class="form-control" value="<?php echo $student['course']; ?>" required>
            </div>
            <div class="form-group">
                <label for="phone_number">Phone Number:</label>
                <input type="text" name="phone_number" class="form-control" value="<?php echo $student['phone_number']; ?>" required>
            </div>
            <div class="form-group">
                <label for="email">Email:</label>
                <input type="email" name="email" class="form-control" value="<?php echo $student['email']; ?>" required>
            </div>
            <button type="submit" name="update_student" class="btn btn-primary">Update Student</button>
        </form>
        <a href="index.php" class="btn btn-secondary mt-3">Back to Student List</a>
    </div>
</body>
</html>

<?php
$conn->close();
?>
*********************
    

