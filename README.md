# Crypto Tracker

A cryptocurrency tracker application that fetches and displays real-time cryptocurrency prices and market data using a crypto API.

## Features

- Fetches real-time cryptocurrency prices
- Displays market data for various cryptocurrencies
- Allows users to search for specific cryptocurrencies

## Technologies Used

- HTML
- CSS
- JavaScript
- Crypto API (e.g., CoinGecko)

## How to Use

1. Clone the repository:
   ```sh
   git clone https://github.com/your-username/crypto-tracker.git
cd crypto-tracker

### .gitignore:

### index.html:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Crypto Tracker</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>Crypto Tracker</h1>
        <input type="text" id="crypto-input" placeholder="Enter cryptocurrency name">
        <button id="search-button">Search</button>
        <div id="crypto-info"></div>
    </div>
    <script src="script.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    background-color: #f0f0f0;
    margin: 0;
    padding: 0;
}

.container {
    max-width: 600px;
    margin: 50px auto;
    padding: 20px;
    background-color: #fff;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    text-align: center;
}

#crypto-input {
    padding: 10px;
    margin-bottom: 10px;
    width: 80%;
}

#search-button {
    padding: 10px;
    cursor: pointer;
}

#crypto-info {
    margin-top: 20px;
}
document.getElementById('search-button').addEventListener('click', function() {
    const crypto = document.getElementById('crypto-input').value.toLowerCase();
    const apiUrl = `https://api.coingecko.com/api/v3/coins/${crypto}`;

    fetch(apiUrl)
        .then(response => response.json())
        .then(data => {
            const cryptoInfo = `
                <h2>${data.name} (${data.symbol.toUpperCase()})</h2>
                <p>Current Price: $${data.market_data.current_price.usd}</p>
                <p>Market Cap: $${data.market_data.market_cap.usd}</p>
                <p>24h High: $${data.market_data.high_24h.usd}</p>
                <p>24h Low: $${data.market_data.low_24h.usd}</p>
            `;
            document.getElementById('crypto-info').innerHTML = cryptoInfo;
        })
        .catch(error => console.error('Error fetching cryptocurrency data:', error));
});
