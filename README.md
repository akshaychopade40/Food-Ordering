<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Food Ordering System</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <h1>Food Ordering System</h1>
    
    <div id="menu">
        <h2>Menu</h2>
        <ul>
            <li>
                <span>Pizza</span>
                <span>$10</span>
                <button onclick="addToCart('Pizza', 10)">Add to Cart</button>
            </li>
            <li>
                <span>Burger</span>
                <span>$8</span>
                <button onclick="addToCart('Burger', 8)">Add to Cart</button>
            </li>
            <li>
                <span>Pasta</span>
                <span>$12</span>
                <button onclick="addToCart('Pasta', 12)">Add to Cart</button>
            </li>
            <li>
                <span>Coke</span>
                <span>$2</span>
                <button onclick="addToCart('Coke', 2)">Add to Cart</button>
            </li>
        </ul>
    </div>

    <div id="cart">
        <h2>Cart</h2>
        <ul id="cartItems"></ul>
        <p>Total: $<span id="totalAmount">0</span></p>
        <button onclick="checkout()">Checkout</button>
    </div>

    <script src="script.js"></script>
</body>
</html>
