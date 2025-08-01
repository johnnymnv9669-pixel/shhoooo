<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>ร้านค้าของคุณ</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      background-color: #304674;
      color: white;
      font-family: sans-serif;
      margin: 0;
      padding: 1rem;
    }

    .products {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
      gap: 1rem;
      justify-content: center;
    }

    .product {
      background: #3d5a80;
      border-radius: 8px;
      padding: 1rem;
      text-align: center;
    }

    .product img {
      width: 100%;
      height: auto;
      border-radius: 6px;
    }

    .product h3 {
      font-size: 1rem;
      margin: 0.5rem 0 0.25rem;
    }

    .product p {
      font-size: 0.9rem;
      margin: 0.25rem 0;
    }

    .product button {
      margin-top: 0.5rem;
      padding: 0.5rem 1rem;
      background-color: #98c1d9;
      border: none;
      border-radius: 4px;
      color: #000;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <h1 style="text-align:center;">ร้านค้าของคุณ</h1>
  <div class="products" id="product-list"></div>

  <script>
    const API_URL = "https://script.google.com/macros/s/AKfycby8lXAg6TiZkOLzS9c8NnOMAp4yTRGle8gkq0NNHWKlFu1E5DqUCgXKHKQGc4aI-W2VCg/exec";

    fetch(API_URL)
      .then((res) => res.json())
      .then((data) => {
        const productList = document.getElementById("product-list");
        productList.innerHTML = data
          .map(
            (item) => `
            <div class="product">
              <img src="${item.Pictures}" alt="${item.Name}" />
              <h3>${item.Name}</h3>
              <p>${item.Price} Kip</p>
              <button onclick="window.location.href='#'">สั่งซื้อ</button>
            </div>
          `
          )
          .join("");
      });
  </script>
</body>
</html>
