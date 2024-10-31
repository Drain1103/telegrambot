<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Create Work Account</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(to right, #e8f0fe, #f1f8e9);
            margin: 0;
            padding: 0;
        }
        header {
            background-color: #4a90e2;
            color: white;
            padding: 15px 20px;
            text-align: center;
            font-size: 1.5em;
        }
        .container {
            display: flex;
            justify-content: center;
            align-items: flex-start;
            padding: 20px;
            flex-wrap: wrap;
        }
        .form-container, .account-layout {
            background-color: #fff;
            border-radius: 12px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
            width: 100%;
            max-width: 400px;
            padding: 30px;
            margin: 20px;
        }
        h2, h3, h4 {
            text-align: center;
            color: #4a90e2;
        }
        .form-group, .cart-item, .review {
            margin-bottom: 15px;
        }
        .form-group label, .product-category label {
            display: block;
            margin-bottom: 5px;
            color: #555;
        }
        .form-group input, .form-group textarea {
            width: 100%;
            padding: 10px;
            border: 2px solid #e1e1e1;
            border-radius: 5px;
            font-size: 1em;
            transition: border-color 0.3s;
        }
        .form-group input:focus {
            border-color: #4a90e2;
            outline: none;
        }
        button {
            width: 100%;
            padding: 10px;
            background-color: #4a90e2;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #357ab8;
        }
        .product {
            background-color: #f9f9f9;
            border: 1px solid #e1e1e1;
            border-radius: 8px;
            padding: 15px;
            text-align: center;
            margin: 10px;
            flex: 1 1 calc(30% - 20px);
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
            transition: transform 0.2s;
        }
        .product:hover {
            transform: scale(1.03);
        }
        .product img {
            max-width: 100%;
            height: auto;
            border-radius: 5px;
        }
        .chat-support, .order-tracking, .cart {
            background-color: #f9f9f9;
            padding: 15px;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
            margin: 20px 0;
        }
        #chat-log {
            max-height: 200px;
            overflow-y: auto;
            margin-top: 10px;
            background-color: #fff;
            border: 1px solid #e1e1e1;
            border-radius: 5px;
            padding: 10px;
        }
        .modal {
            display: none;
            position: fixed;
            z-index: 1;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            overflow: auto;
            background-color: rgb(0,0,0);
            background-color: rgba(0,0,0,0.4);
            padding-top: 60px;
        }
        .modal-content {
            background-color: #fefefe;
            margin: 5% auto;
            padding: 20px;
            border: 1px solid #888;
            width: 80%;
            border-radius: 10px;
        }
        .close {
            color: #aaa;
            float: right;
            font-size: 28px;
            font-weight: bold;
        }
        .close:hover,
        .close:focus {
            color: black;
            text-decoration: none;
            cursor: pointer;
        }
    </style>
</head>
<body>

<header>
    🛍️ A-Nyar Shopping Platform 🛍️
</header>

<div class="container">
    <!-- Account Creation Form -->
    <div class="form-container" id="account-form-container">
        <h2>Create Your Account</h2>
        <form id="account-form" onsubmit="return createAccount(event);">
            <div class="form-group">
                <label for="name">Full Name</label>
                <input type="text" id="name" name="name" placeholder="Enter your full name" required>
            </div>
            <div class="form-group">
                <label for="phone">Phone Number</label>
                <input type="tel" id="phone" name="phone" placeholder="Enter your phone number" required>
            </div>
            <div class="form-group">
                <label for="password">Password</label>
                <input type="password" id="password" name="password" placeholder="Create a password" required>
            </div>
            <button type="submit">Create Work Account</button>
        </form>
    </div>

    <!-- Profile Mockup -->
    <div class="account-layout" id="profile-mockup" style="display: none;">
        <h2>Welcome, <span id="profile-name">John Doe</span>!</h2>
        <p id="profile-phone">Phone: 123-456-7890</p>

        <!-- Search Bar -->
        <div class="form-group">
            <input type="text" id="search" placeholder="Search products..." oninput="searchProducts()">
        </div>

        <h3>Product Categories</h3>
        <div class="product-category">
            <label>Category 1</label>
            <div class="product" onclick="openModal('Product 1 Details', 'Description of Product 1.')">
                <img src="https://img.ltwebstatic.com/images3_spmp/2023/07/27/169044806227147be7a5fca57929c075e58c9ed112_thumbnail_336x.jpg" alt="Product 1">
                <h4>Product 1</h4>
                <p>$10.00</p>
                <button onclick="addToCart('Product 1', 10)">Add to Cart</button>
            </div>
        </div>
        <div class="product-category">
            <label>Category 2</label>
            <div class="product" onclick="openModal('Product 2 Details', 'Description of Product 2.')">
                <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRnTvo6xNxvNh8ZARdTL5fRn30Z1RHwlFEfRg&s" alt="Product 2">
                <h4>Product 2</h4>
                <p>$15.00</p>
                <button onclick="addToCart('Product 2', 15)">Add to Cart</button>
            </div>
        </div>
        <div class="product-category">
            <label>Category 3</label>
            <div class="product" onclick="openModal('Product 3 Details', 'Description of Product 3.')">
                <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTdE29Ddw7Rc9SIv4MffPMknnYwCDIEKXRruQ&s" alt="Product 3">
                <h4>Product 3</h4>
                <p>$20.00</p>
                <button onclick="addToCart('Product 3', 20)">Add to Cart</button>
            </div>
        </div>

        <!-- Cart Section -->
        <div class="cart">
            <h3>Shopping Cart</h3>
            <div id="cart-items"></div>
            <button onclick="checkout()">Checkout</button>
        </div>

        <!-- Review Section -->
        <div class="product-reviews">
            <h3>Leave a Review</h3>
            <textarea id="review-text" placeholder="Write your review here..."></textarea>
            <button onclick="submitReview()">Submit Review</button>
            <h4>Reviews:</h4>
            <div id="reviews"></div>
        </div>

        <!-- Chat Support -->
        <div class="chat-support">
            <h3>Chat Support</h3>
            <div id="chat-log"></div>
            <input type="text" id="chat-input" placeholder="Type your message...">
            <button onclick="sendMessage()">Send</button>
        </div>

        <!-- Order Tracking -->
        <div class="order-tracking">
            <h3>Order Status</h3>
            <p>Your last order status: <strong>Shipped</strong></p>
        </div>

        <!-- Contact Button -->
        <div style="text-align: center; margin: 20px;">
            <a href="https://m.me/drai1102" target="_blank" style="padding: 10px 20px; background-color: #4a90e2; color: white; text-decoration: none; border-radius: 5px;">Contact Us on Messenger</a>
        </div>
    </div>

    <!-- Modal for Product Details -->
    <div id="product-modal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal()">&times;</span>
            <h2 id="modal-title"></h2>
            <p id="modal-description"></p>
        </div>
    </div>
</div>

<script>
    function createAccount(event) {
        event.preventDefault();
        const name = document.getElementById('name').value;
        const phone = document.getElementById('phone').value;
        document.getElementById('profile-name').textContent = name;
        document.getElementById('profile-phone').textContent = 'Phone: ' + phone;
        document.getElementById('account-form-container').style.display = 'none';
        document.getElementById('profile-mockup').style.display = 'block';
    }

    function openModal(title, description) {
        document.getElementById('modal-title').textContent = title;
        document.getElementById('modal-description').textContent = description;
        document.getElementById('product-modal').style.display = 'block';
    }

    function closeModal() {
        document.getElementById('product-modal').style.display = 'none';
    }

    function addToCart(productName, price) {
        const cartItems = document.getElementById('cart-items');
        const item = document.createElement('div');
        item.className = 'cart-item';
        item.textContent = `${productName} - $${price}`;
        cartItems.appendChild(item);
    }

    function checkout() {
        alert('Proceeding to checkout!');
    }

    function submitReview() {
        const reviewText = document.getElementById('review-text').value;
        if (reviewText) {
            const reviewsSection = document.getElementById('reviews');
            const review = document.createElement('div');
            review.className = 'review';
            review.innerHTML = `<p><strong>You:</strong> ⭐⭐⭐⭐ - "${reviewText}"</p>`;
            reviewsSection.appendChild(review);
            document.getElementById('review-text').value = ''; // Clear the input
        }
    }

    function sendMessage() {
        const chatInput = document.getElementById('chat-input').value;
        if (chatInput) {
            const chatLog = document.getElementById('chat-log');
            const message = document.createElement('div');
            message.textContent = `User: ${chatInput}`;
            chatLog.appendChild(message);
            document.getElementById('chat-input').value = ''; // Clear the input
        }
    }

    function searchProducts() {
        const query = document.getElementById('search').value.toLowerCase();
        const products = document.querySelectorAll('.product');
        products.forEach(product => {
            const name = product.querySelector('h4').textContent.toLowerCase();
            product.style.display = name.includes(query) ? 'block' : 'none';
        });
    }

    document.getElementById('account-form-container').style.display = 'block';
</script>

</body>
</html>
