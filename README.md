# Intenfix-Reviews-intenfix.com
pip install Flask
from flask import Flask, jsonify

app = Flask(__name__)

# Sample stock data
stocks = [
    {"symbol": "AAPL", "name": "Apple Inc.", "price": 150.50},
    {"symbol": "GOOGL", "name": "Alphabet Inc.", "price": 2800.00},
    {"symbol": "MSFT", "name": "Microsoft Corporation", "price": 300.25}
]

@app.route('/api/stocks')
def get_stocks():
    return jsonify(stocks)

if __name__ == '__main__':
    app.run(debug=True)
python app.py
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Intenfix Trading App</title>
</head>
<body>
    <h1>Intenfix Trading App</h1>
    <h2>Available Stocks</h2>
    <ul id="stock-list"></ul>

    <script>
        // Fetch stock data from the backend server
        fetch('http://127.0.0.1:5000/api/stocks')
            .then(response => response.json())
            .then(stocks => {
                const stockList = document.getElementById('stock-list');
                stocks.forEach(stock => {
                    const li = document.createElement('li');
                    li.textContent = `${stock.symbol} - ${stock.name} - $${stock.price}`;
                    stockList.appendChild(li);
                });
            })
            .catch(error => console.error('Error fetching stock data:', error));
    </script>
</body>
</html>
