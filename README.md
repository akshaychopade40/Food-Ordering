<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Food Ordering System</title>
    <style>
        body 
        {
            font-family: Arial, sans-serif;
        }
        .menu, .cart 
        {
            margin: 20px;
            padding: 20px;
            border: 1px solid #ccc;
        }
        .menu-item, .cart-item 
        {
            display: flex;
            justify-content: space-between;
            margin-bottom: 10px;
        }
        .cart-item input 
        {
            width: 50px;
        }
        .checkout 
        {
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="menu">
        <h2>Menu</h2>
        <div class="menu-item">
            <span>Pizza</span>
            <span>$10.00</span>
            <button onclick="addToCart('Pizza', 10.00)">Add to Cart</button>
        </div>
        <div class="menu-item">
            <span>Burger</span>
            <span>$5.00</span>
            <button onclick="addToCart('Burger', 5.00)">Add to Cart</button>
        </div>
        <div class="menu-item">
            <span>Fries</span>
            <span>$2.50</span>
            <button onclick="addToCart('Fries', 2.50)">Add to Cart</button>
        </div>
        <div class="menu-item">
            <span>Coke</span>
            <span>$1.50</span>
            <button onclick="addToCart('Coke', 1.50)">Add to Cart</button>
        </div>
    </div>

    <div class="cart">
        <h2>Cart</h2>
        <div id="cart-items"></div>
        <div class="checkout">
            <h3>Total: $<span id="total-amount">0.00</span></h3>
            <button onclick="checkout()">Checkout</button>
        </div>
    </div>

    <script>
        let cart = [];

        function addToCart(item, price) 
        {
            let cartItem = cart.find(i => i.name === item);
            if (cartItem) 
            {
                cartItem.quantity++;
            } else 
            {
                cart.push({ name: item, price: price, quantity: 1 });
            }
            updateCart();
        }

        function updateCart() 
        {
            let cartItemsDiv = document.getElementById('cart-items');
            cartItemsDiv.innerHTML = '';
            let total = 0;

            cart.forEach(item => {
                total += item.price * item.quantity;
                cartItemsDiv.innerHTML += `
                    <div class="cart-item">
                        <span>${item.name}</span>
                        <span>$${item.price.toFixed(2)}</span>
                        <input type="number" value="${item.quantity}" min="1" onchange="updateQuantity('${item.name}', this. Value)">
                        <button onclick="removeFromCart('${item.name}')">Remove</button>
                    </div>
                `;
            });

            document.getElementById('total-amount').innerText = total.toFixed(2);
        }

        function updateQuantity(name, quantity) 
        {
            let cartItem = cart.find(i => i.name === name);
            if (cartItem) 
            {
                cartItem.quantity = parseInt(quantity);
            }
            updateCart();
        }

        function removeFromCart(name) 
        {
            cart = cart.filter(item => item.name !== name);
            updateCart();
        }

        function checkout() 
        {
            alert(`Your total is $${document.getElementById('total-amount').innerText}. Thank you for your order!`);
            cart = [];
            updateCart();
        }
    </script>
</body>
</html>
