/Quite 
│
├── index.html
├── style.css
├── script.js
└── contract.js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dorr Shop - Online Courses</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <!-- منوی اصلی -->
    <header>
        <nav>
            <ul>
                <li><a href="#home">Home</a></li>
                <li><a href="#courses">Courses</a></li>
                <li><a href="#about">About Us</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </nav>
    </header>

    <!-- صفحه اصلی با متن‌های انگیزشی -->
    <section id="home">
        <h1>Welcome to Dorr Shop</h1>
        <p>Learn the best skills with our online courses. Pay with cryptocurrency and get instant access!</p>
        <div class="motivational">
            <p>"The future belongs to those who believe in the beauty of their dreams." – Eleanor Roosevelt</p>
            <p>"Success is not final, failure is not fatal: It is the courage to continue that counts." – Winston Churchill</p>
            <p>"Your time is limited, don't waste it living someone else's life." – Steve Jobs</p>
        </div>
    </section>

    <!-- صفحه دوره‌ها -->
    <section id="courses">
        <h2>Our Courses</h2>
        <div class="course">
            <h3>Course 1: Advanced Programming</h3>
            <p>Price: $15 (Pay with Bitcoin)</p>
            <button onclick="showPaymentDetails('bitcoin')">Buy Now</button>
        </div>
        <div class="course">
            <h3>Course 2: Web Development</h3>
            <p>Price: $20 (Pay with Ethereum)</p>
            <button onclick="showPaymentDetails('ethereum')">Buy Now</button>
        </div>
    </section>

    <!-- بخش پرداخت -->
    <section id="paymentDetails" style="display: none;">
        <h3>Payment Details</h3>
        <p>Please send <span id="cryptoAmount"></span> <span id="selectedCrypto"></span> to the following address:</p>
        <p><strong id="walletAddress"></strong></p>
        <p>After payment, your course will be delivered automatically.</p>
    </section>

    <!-- قرارداد هوشمند -->
    <section id="smartContract">
        <h2>Smart Contract</h2>
        <p>Our smart contract ensures secure and automatic delivery of courses after payment. Here's the code:</p>
        <pre id="contractCode"></pre>
    </section>

    <!-- اسکریپت‌ها -->
    <script src="script.js"></script>
    <script src="contract.js"></script>
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

section {
    padding: 20px;
    margin: 20px;
    background-color: #fff;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.course {
    margin-bottom: 20px;
}

button {
    background-color: #28a745;
    color: #fff;
    border: none;
    padding: 10px 20px;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #218838;
}

#paymentDetails {
    display: none;
    background-color: #e9ecef;
    padding: 20px;
    border-radius: 8px;
}

#smartContract {
    background-color: #f8f9fa;
    padding: 20px;
    border-radius: 8px;
}

pre {
    background-color: #e9ecef;
    padding: 10px;
    border-radius: 5px;
    overflow-x: auto;
}

.motivational {
    font-style: italic;
    color: #555;
    margin-top: 20px;
}

.motivational p {
    margin: 10px 0;
}
function showPaymentDetails(crypto) {
    const coursePriceUSD = 15; // قیمت دوره به دلار
    const bitcoinPriceUSD = 50000; // نرخ تبدیل بیت‌کوین به دلار (مثال)
    const ethereumPriceUSD = 3000; // نرخ تبدیل اتریوم به دلار (مثال)

    let amountInCrypto;
    if (crypto === 'bitcoin') {
        amountInCrypto = (coursePriceUSD / bitcoinPriceUSD).toFixed(8);
    } else if (crypto === 'ethereum') {
        amountInCrypto = (coursePriceUSD / ethereumPriceUSD).toFixed(8);
    }

    const walletAddress = crypto === 'bitcoin' ? 'bc1qgkaaaeehlt0y7c7m3ck7wlt5kgg03yxaqz6cge' : '0xYourEthereumAddress';

    document.getElementById('cryptoAmount').textContent = amountInCrypto;
    document.getElementById('selectedCrypto').textContent = crypto.toUpperCase();
    document.getElementById('walletAddress').textContent = walletAddress;

    document.getElementById('paymentDetails').style.display = 'block';
}
