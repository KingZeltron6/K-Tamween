# K-Tamween
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tamween Digital System</title>
    <style>
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background: #f4f7f6; margin: 0; display: flex; flex-direction: column; align-items: center; }
        .card { background: white; padding: 20px; border-radius: 15px; box-shadow: 0 10px 25px rgba(0,0,0,0.1); width: 90%; max-width: 400px; margin-top: 50px; text-align: center; }
        h1 { color: #2c3e50; }
        .balance { font-size: 2.5rem; color: #27ae60; font-weight: bold; margin: 20px 0; }
        button { background: #3498db; color: white; border: none; padding: 10px 20px; border-radius: 5px; cursor: pointer; font-size: 1rem; transition: 0.3s; }
        button:hover { background: #2980b9; }
        .items { margin-top: 20px; text-align: left; }
        .item-row { display: flex; justify-content: space-between; padding: 10px 0; border-bottom: 1px solid #eee; }
    </style>
</head>
<body>

    <div class="card">
        <h1>Tamween Card</h1>
        <p>Current Balance (Points)</p>
        <div class="balance" id="balanceDisplay">50.00</div>
        
        <div class="items">
            <h3>Available Items</h3>
            <div class="item-row">
                <span>Rice (5kg) - 10 pts</span>
                <button onclick="buyItem(10)">Buy</button>
            </div>
            <div class="item-row">
                <span>Sugar (2kg) - 5 pts</span>
                <button onclick="buyItem(5)">Buy</button>
            </div>
            <div class="item-row">
                <span>Oil (1L) - 8 pts</span>
                <button onclick="buyItem(8)">Buy</button>
            </div>
        </div>
        <br>
        <button style="background: #e74c3c;" onclick="resetBalance()">Reset Card</button>
    </div>

    <script>
        // Logic to make it "Work"
        let balance = localStorage.getItem('tamweenBalance') ? parseFloat(localStorage.getItem('tamweenBalance')) : 50.00;
        document.getElementById('balanceDisplay').innerText = balance.toFixed(2);

        function buyItem(cost) {
            if (balance >= cost) {
                balance -= cost;
                updateDisplay();
                alert("Purchase Successful!");
            } else {
                alert("Insufficient Balance!");
            }
        }

        function resetBalance() {
            balance = 50.00;
            updateDisplay();
        }

        function updateDisplay() {
            document.getElementById('balanceDisplay').innerText = balance.toFixed(2);
            localStorage.setItem('tamweenBalance', balance);
        }
    </script>
</body>
