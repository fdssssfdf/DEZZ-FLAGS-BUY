<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Buy DEZZ FFlags</title>
  <script src="https://www.paypal.com/sdk/js?client-id=AWeXVSVsCKTijEFkPhkkaLP9f1LKm5tBtqLPSZ9Y41V_A8uSD4jfXSPmEhIjC25hJDcC9NQd3hT14yd6&currency=USD"></script>
  <style>
    body { font-family: Arial, sans-serif; text-align: center; margin-top: 100px; }
    .hidden { display: none; }
    button { padding: 10px 20px; font-size: 18px; cursor: pointer; }
    #paypal-button-container { margin-top: 20px; }
    a { font-size: 18px; color: blue; }
  </style>
</head>
<body>

  <!-- Page 1 -->
  <div id="page1">
    <h1>Buy DEZZ FFlags</h1>
    <button onclick="goToPurchase()">Buy</button>
  </div>

  <!-- Page 2 -->
  <div id="page2" class="hidden">
    <h1>Buy DEZZ FFlags For 5 USD</h1>
    <div id="paypal-button-container"></div>
  </div>

  <!-- Page 3 -->
  <div id="page3" class="hidden">
    <h1>Get DEZZ FFlags</h1>
    <p><a href="https://pastebin.com/N6Eg7Vy7" target="_blank" rel="noopener noreferrer">https://pastebin.com/N6Eg7Vy7</a></p>
  </div>

  <script>
    function goToPurchase() {
      document.getElementById('page1').classList.add('hidden');
      document.getElementById('page2').classList.remove('hidden');

      // Render PayPal button
      paypal.Buttons({
        createOrder: function(data, actions) {
          // Set up the transaction
          return actions.order.create({
            purchase_units: [{
              amount: {
                value: '5.00' // $5 payment
              }
            }]
          });
        },
        onApprove: function(data, actions) {
          // Capture the funds from the transaction
          return actions.order.capture().then(function(details) {
            // Show success page
            document.getElementById('page2').classList.add('hidden');
            document.getElementById('page3').classList.remove('hidden');
          });
        },
        onError: function(err) {
          alert('Payment could not be completed. Please try again.');
          console.error(err);
        }
      }).render('#paypal-button-container');
    }
  </script>

</body>
</html>
