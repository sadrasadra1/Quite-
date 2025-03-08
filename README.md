/dorr-shop
│
├── index.html
├── style.css
├── script.js
└── payment.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dorr Shop</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>Welcome to Dorr Shop</h1>
        <nav>
            <ul>
                <li><a href="index.html">Home</a></li>
                <li><a href="payment.html">Buy Dorr</a></li>
            </ul>
        </nav>
    </header>
    <main>
        <section>
            <h2>About Us</h2>
            <p>We sell the best Dorr in the world. Buy now using cryptocurrency!</p>
        </section>
    </main>
    <footer>
        <p>&copy; 2023 Dorr Shop. All rights reserved.</p>
    </footer>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f4f4f4;
}

header {
    background-color: #333;
    color: #fff;
    padding: 10px 0;
    text-align: center;
}

nav ul {
    list-style: none;
    padding: 0;
}

nav ul li {
    display: inline;
    margin: 0 15px;
}

nav ul li a {
    color: #fff;
    text-decoration: none;
}

main {
    padding: 20px;
    text-align: center;
}

footer {
    background-color: #333;
    color: #fff;
    text-align: center;
    padding: 10px 0;
    position: fixed;
    width: 100%;
    bottom: 0;
}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Buy Dorr</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>Buy Dorr</h1>
        <nav>
            <ul>
                <li><a href="index.html">Home</a></li>
                <li><a href="payment.html">Buy Dorr</a></li>
            </ul>
        </nav>
    </header>
    <main>
        <section>
            <h2>Purchase Dorr</h2>
            <form id="paymentForm">
                <label for="amount">Amount of Dorr:</label>
                <input type="number" id="amount" name="amount" min="1" required>
                <br>
                <label for="crypto">Select Cryptocurrency:</label>
                <select id="crypto" name="crypto">
                    <option value="bitcoin">Bitcoin (BTC)</option>
                    <option value="ethereum">Ethereum (ETH)</option>
                    <option value="litecoin">Litecoin (LTC)</option>
                </select>
                <br>
                <button type="submit">Proceed to Payment</button>
            </form>
            <div id="paymentDetails" style="display: none;">
                <h3>Payment Details</h3>
                <p>Please send <span id="cryptoAmount"></span> <span id="selectedCrypto"></span> to the following address:</p>
                <p><strong id="walletAddress"></strong></p>
                <p>After payment, your Dorr will be delivered automatically.</p>
            </div>
        </section>
    </main>
    <footer>
        <p>&copy; 2023 Dorr Shop. All rights reserved.</p>
    </footer>
    <script src="script.js"></script>
</body>
</html>
document.getElementById('paymentForm').addEventListener('submit', function(event) {
    event.preventDefault();

    const crypto = document.getElementById('crypto').value;

    // Course price in USD
    const coursePriceUSD = 15;

    // Bitcoin to USD exchange rate (this value should be fetched from an API)
    const bitcoinPriceUSD = 50000; // Example: Bitcoin price is $50,000

    // Calculate the equivalent amount in Bitcoin
    const amountInBTC = (coursePriceUSD / bitcoinPriceUSD).toFixed(8); // Bitcoin amount with 8 decimal places

    // Seller's wallet address
    const walletAddress = 'bc1qgkaaaeehlt0y7c7m3ck7wlt5kgg03yxaqz6cge'; // Seller's Bitcoin address

    // Display payment details
    document.getElementById('cryptoAmount').textContent = amountInBTC;
    document.getElementById('selectedCrypto').textContent = crypto.toUpperCase();
    document.getElementById('walletAddress').textContent = walletAddress;

    document.getElementById('paymentDetails').style.display = 'block';
});
