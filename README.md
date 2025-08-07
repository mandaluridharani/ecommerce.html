<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Awesome Shop</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* Custom styles for Inter font and general body styling */
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f8fafc; /* Light gray background */
            color: #334155; /* Dark slate gray text */
        }
        /* Hide scrollbar for Chrome, Safari and Opera */
        .no-scrollbar::-webkit-scrollbar {
            display: none;
        }
        /* Hide scrollbar for IE, Edge and Firefox */
        .no-scrollbar {
            -ms-overflow-style: none;  /* IE and Edge */
            scrollbar-width: none;  /* Firefox */
        }
    </style>
</head>
<body class="flex flex-col min-h-screen">
    <!-- Header Section -->
    <header class="bg-gradient-to-r from-blue-600 to-purple-600 text-white p-4 shadow-lg">
        <div class="container mx-auto flex justify-between items-center">
            <h1 class="text-3xl font-bold rounded-lg p-2 bg-white bg-opacity-20">My Awesome Shop</h1>
            <nav>
                <ul class="flex space-x-6">
                    <li><a href="#" class="hover:text-blue-200 transition duration-300">Home</a></li>
                    <li><a href="#products" class="hover:text-blue-200 transition duration-300">Products</a></li>
                    <li><a href="#cart" class="hover:text-blue-200 transition duration-300">Cart (<span id="cart-count">0</span>)</a></li>
                    <li><a href="#" class="hover:text-blue-200 transition duration-300">Contact</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <!-- Main Content Area -->
    <main class="container mx-auto my-8 p-4 flex-grow">
        <!-- Products Section -->
        <section id="products" class="mb-12">
            <h2 class="text-4xl font-extrabold text-center mb-8 text-gray-800">Our Products</h2>
            <div id="product-list" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-8">
                <!-- Product cards will be injected here by JavaScript -->
            </div>
        </section>

        <!-- Shopping Cart Section -->
        <section id="cart" class="bg-white p-6 rounded-xl shadow-lg border border-gray-200">
            <h2 class="text-4xl font-extrabold text-center mb-8 text-gray-800">Your Shopping Cart</h2>
            <div id="cart-items" class="space-y-4">
                <!-- Cart items will be injected here by JavaScript -->
                <p id="empty-cart-message" class="text-center text-gray-500 text-lg">Your cart is empty.</p>
            </div>
            <div class="mt-8 pt-6 border-t border-gray-200 flex justify-between items-center">
                <p class="text-2xl font-bold text-gray-800">Total: $<span id="cart-total">0.00</span></p>
                <button id="checkout-button" class="bg-green-500 hover:bg-green-600 text-white font-bold py-3 px-6 rounded-xl shadow-md transition duration-300 transform hover:scale-105 focus:outline-none focus:ring-2 focus:ring-green-500 focus:ring-opacity-50">
                    Checkout
                </button>
            </div>
        </section>
    </main>

    <!-- Footer Section -->
    <footer class="bg-gray-800 text-white p-6 mt-8 shadow-inner">
        <div class="container mx-auto text-center">
            <p>&copy; 2025 My Awesome Shop. All rights reserved.</p>
            <div class="flex justify-center space-x-4 mt-2">
                <a href="#" class="hover:text-blue-400 transition duration-300">Privacy Policy</a>
                <a href="#" class="hover:text-blue-400 transition duration-300">Terms of Service</a>
            </div>
        </div>
    </footer>

    <script>
        // --- Product Data ---
        const products = [
            {
                id: 1,
                name: "Wireless Headphones",
                price: 59.99,
                image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTo9R9IJDw_QjrCfSrkBlktHLsvhnSJkA_NEw&s",
                description: "Experience crystal-clear audio with these comfortable wireless headphones."
            },
            {
                id: 2,
                name: "Smartwatch Pro",
                price: 199.99,
                image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSwhZZnXfHUxP1dAmH1EFsqjNVAWj131p_J4Q&s",
                description: "Track your fitness and stay connected with the latest smartwatch."
            },
            {
                id: 3,
                name: "Portable Bluetooth Speaker",
                price: 34.50,
                image: "data:image/jpeg;base64,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",
                description: "Compact and powerful, perfect for music on the go."
            },
            {
                id: 4,
                name: "Gaming Mouse",
                price: 45.00,
                image: "data:image/jpeg;base64,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",
                description: "Precision and speed for the ultimate gaming experience."
            },
            {
                id: 5,
                name: "USB-C Hub",
                price: 29.99,
                image: "data:image/jpeg;base64,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",
                description: "Expand your laptop's connectivity with this versatile hub."
            },
            {
                id: 6,
                name: "Ergonomic Keyboard",
                price: 79.99,
                image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ_IyFrPBiyTmY154uAXZNHE2oq2p2rrkWkUg&s",
                description: "Type comfortably all day with this ergonomic design."
            },
            {
                id: 7,
                name: "External SSD 1TB",
                price: 120.00,
                image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRv3Z5ws428cVMvg_-QvtD8W8KMuluJUPytVw&s",
                description: "Fast and reliable storage for all your files."
            },
            {
                id: 8,
                name: "Webcam 1080p",
                price: 65.00,
                image: "data:image/jpeg;base64,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",
                description: "High-definition video calls for work or leisure."
            }
        ];

        // --- Global Cart State ---
        let cart = [];

        // --- DOM Elements ---
        const productListDiv = document.getElementById('product-list');
        const cartItemsDiv = document.getElementById('cart-items');
        const cartTotalSpan = document.getElementById('cart-total');
        const cartCountSpan = document.getElementById('cart-count');
        const emptyCartMessage = document.getElementById('empty-cart-message');
        const checkoutButton = document.getElementById('checkout-button');

        // --- Functions ---

        /**
         * Renders all products to the product list section.
         */
        function renderProducts() {
            productListDiv.innerHTML = ''; // Clear existing products
            products.forEach(product => {
                const productCard = document.createElement('div');
                productCard.className = 'bg-white rounded-xl shadow-lg overflow-hidden transform transition duration-300 hover:scale-105 border border-gray-200';
                productCard.innerHTML = `
                    <img src="${product.image}" alt="${product.name}" class="w-full h-48 object-cover object-center">
                    <div class="p-6">
                        <h3 class="text-xl font-semibold mb-2 text-gray-900">${product.name}</h3>
                        <p class="text-gray-600 text-sm mb-4">${product.description}</p>
                        <div class="flex justify-between items-center">
                            <span class="text-2xl font-bold text-blue-600">$${product.price.toFixed(2)}</span>
                            <button data-id="${product.id}" class="add-to-cart-btn bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded-lg shadow-md transition duration-300 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-opacity-50">
                                Add to Cart
                            </button>
                        </div>
                    </div>
                `;
                productListDiv.appendChild(productCard);
            });

            // Add event listeners to "Add to Cart" buttons
            document.querySelectorAll('.add-to-cart-btn').forEach(button => {
                button.addEventListener('click', (event) => {
                    const productId = parseInt(event.target.dataset.id);
                    addToCart(productId);
                });
            });
        }

        /**
         * Adds a product to the cart or increments its quantity if already present.
         * @param {number} productId - The ID of the product to add.
         */
        function addToCart(productId) {
            const product = products.find(p => p.id === productId);
            if (!product) return;

            const existingItem = cart.find(item => item.id === productId);

            if (existingItem) {
                existingItem.quantity++;
            } else {
                cart.push({ ...product, quantity: 1 });
            }
            updateCartDisplay();
        }

        /**
         * Removes a product from the cart.
         * @param {number} productId - The ID of the product to remove.
         */
        function removeFromCart(productId) {
            cart = cart.filter(item => item.id !== productId);
            updateCartDisplay();
        }

        /**
         * Updates the quantity of a product in the cart.
         * @param {number} productId - The ID of the product.
         * @param {number} newQuantity - The new quantity.
         */
        function updateCartQuantity(productId, newQuantity) {
            const item = cart.find(i => i.id === productId);
            if (item) {
                if (newQuantity <= 0) {
                    removeFromCart(productId);
                } else {
                    item.quantity = newQuantity;
                }
            }
            updateCartDisplay();
        }

        /**
         * Updates the shopping cart display, total, and item count.
         */
        function updateCartDisplay() {
            cartItemsDiv.innerHTML = ''; // Clear existing cart items
            let total = 0;
            let itemCount = 0;

            if (cart.length === 0) {
                emptyCartMessage.classList.remove('hidden');
            } else {
                emptyCartMessage.classList.add('hidden');
                cart.forEach(item => {
                    const itemTotal = item.price * item.quantity;
                    total += itemTotal;
                    itemCount += item.quantity;

                    const cartItemDiv = document.createElement('div');
                    cartItemDiv.className = 'flex items-center justify-between bg-gray-50 p-4 rounded-lg shadow-sm border border-gray-100';
                    cartItemDiv.innerHTML = `
                        <div class="flex items-center space-x-4">
                            <img src="${item.image}" alt="${item.name}" class="w-16 h-16 object-cover rounded-md shadow-sm">
                            <div>
                                <h4 class="font-semibold text-lg text-gray-800">${item.name}</h4>
                                <p class="text-gray-600">Price: $${item.price.toFixed(2)}</p>
                            </div>
                        </div>
                        <div class="flex items-center space-x-3">
                            <button data-id="${item.id}" data-action="decrease" class="quantity-btn bg-red-400 hover:bg-red-500 text-white font-bold py-1 px-3 rounded-full transition duration-300">-</button>
                            <span class="text-xl font-medium text-gray-700">${item.quantity}</span>
                            <button data-id="${item.id}" data-action="increase" class="quantity-btn bg-green-400 hover:bg-green-500 text-white font-bold py-1 px-3 rounded-full transition duration-300">+</button>
                            <button data-id="${item.id}" class="remove-from-cart-btn bg-red-600 hover:bg-red-700 text-white font-bold py-2 px-4 rounded-lg shadow-md transition duration-300">Remove</button>
                        </div>
                    `;
                    cartItemsDiv.appendChild(cartItemDiv);
                });
            }

            cartTotalSpan.textContent = total.toFixed(2);
            cartCountSpan.textContent = itemCount;

            // Add event listeners for quantity buttons and remove buttons
            document.querySelectorAll('.quantity-btn').forEach(button => {
                button.addEventListener('click', (event) => {
                    const productId = parseInt(event.target.dataset.id);
                    const action = event.target.dataset.action;
                    const item = cart.find(i => i.id === productId);
                    if (item) {
                        if (action === 'increase') {
                            updateCartQuantity(productId, item.quantity + 1);
                        } else if (action === 'decrease') {
                            updateCartQuantity(productId, item.quantity - 1);
                        }
                    }
                });
            });

            document.querySelectorAll('.remove-from-cart-btn').forEach(button => {
                button.addEventListener('click', (event) => {
                    const productId = parseInt(event.target.dataset.id);
                    removeFromCart(productId);
                });
            });
        }

        /**
         * Handles the checkout process (simple alert for now).
         */
        function handleCheckout() {
            if (cart.length === 0) {
                // Instead of alert, we'll show a simple message box or update UI.
                // For this example, we'll just log to console and update a temporary message.
                console.log("Your cart is empty. Add items before checking out!");
                const messageBox = document.createElement('div');
                messageBox.className = 'fixed top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 bg-yellow-100 border border-yellow-400 text-yellow-700 px-4 py-3 rounded-lg shadow-lg z-50';
                messageBox.innerHTML = `
                    <p class="font-bold">Cart Empty!</p>
                    <p>Please add items to your cart before checking out.</p>
                `;
                document.body.appendChild(messageBox);
                setTimeout(() => {
                    messageBox.remove();
                }, 3000); // Remove message after 3 seconds
                return;
            }

            const messageBox = document.createElement('div');
            messageBox.className = 'fixed top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 bg-green-100 border border-green-400 text-green-700 px-4 py-3 rounded-lg shadow-lg z-50';
            messageBox.innerHTML = `
                <p class="font-bold">Order Placed!</p>
                <p>Thank you for your purchase. Your total was $${cartTotalSpan.textContent}.</p>
            `;
            document.body.appendChild(messageBox);

            // Clear the cart after a short delay
            setTimeout(() => {
                messageBox.remove();
                cart = []; // Clear the cart
                updateCartDisplay(); // Update display to show empty cart
            }, 3000); // Display message for 3 seconds
        }

        // --- Event Listeners ---
        document.addEventListener('DOMContentLoaded', () => {
            renderProducts();
            updateCartDisplay(); // Initialize cart display
        });

        checkoutButton.addEventListener('click', handleCheckout);
    </script>
</body>
</html>
