# vegetable-selector
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Vegetable Selector (Telugu)</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: #f7f7f7;
      padding: 20px;
      max-width: 600px;
      margin: auto;
    }
    h2 {
      text-align: center;
      color: #333;
    }
    .item {
      background: #fff;
      padding: 12px;
      border-radius: 8px;
      margin-bottom: 12px;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    }
    label {
      font-weight: bold;
    }
    input, select {
      margin-top: 5px;
      padding: 6px;
      width: 100%;
      box-sizing: border-box;
    }
    button {
      width: 100%;
      padding: 12px;
      background-color: #28a745;
      color: white;
      border: none;
      border-radius: 8px;
      font-size: 16px;
      cursor: pointer;
    }
    button:hover {
      background-color: #218838;
    }
    pre {
      background: #eee;
      padding: 10px;
      border-radius: 8px;
    }
  </style>
</head>
<body>
  <h2>🛒 Vegetable Selector (కూరగాయల ఎంపిక)</h2>
  <div id="vegList"></div>

  <button onclick="showSummary()">Submit (సబ్మిట్)</button>

  <h3>📋 Your Selection (మీ ఎంపిక):</h3>
  <pre id="summary"></pre>

  <script>
    const vegetables = [
      { en: "Tomato", te: "టమోటా" },
      { en: "Potato", te: "బంగాళదుంప" },
      { en: "Onion", te: "ఉల్లిపాయ" },
      { en: "Carrot", te: "కారెట్" },
      { en: "Brinjal", te: "వంకాయ" },
      { en: "Lady Finger", te: "బెండకాయ" },
      { en: "Cabbage", te: "క్యాబేజి" },
      { en: "Cauliflower", te: "కాలీఫ్లవర్" },
      { en: "Beans", te: "బీన్స్" },
      { en: "Bottle Gourd", te: "సొరకాయ" },
      { en: "Ridge Gourd", te: "బీరకాయ" },
      { en: "Snake Gourd", te: "పొట్లకాయ" },
      { en: "Drumstick", te: "మునగకాయ" },
      { en: "Green Chilli", te: "పచ్చిమిర్చి" },
      { en: "Coriander", te: "కొత్తిమీర" },
      { en: "Mint", te: "పుదీనా" },
      { en: "Spinach", te: "పాలకూర" },
      { en: "Fenugreek Leaves", te: "మెంతికూర" },
      { en: "Cucumber", te: "దోసకాయ" },
      { en: "Raw Banana", te: "అరటికాయ" }
    ];

    const vegList = document.getElementById("vegList");

    vegetables.forEach((veg, i) => {
      const div = document.createElement("div");
      div.className = "item";
      div.innerHTML = `
        <label>${veg.en} (${veg.te})</label>
        <input type="number" id="qty${i}" placeholder="Quantity" min="0">
        <select id="unit${i}">
          <option value="kg">kg</option>
          <option value="g">grams</option>
        </select>
      `;
      vegList.appendChild(div);
    });

    function showSummary() {
      let result = "";
      vegetables.forEach((veg, i) => {
        const qty = document.getElementById("qty" + i).value;
        const unit = document.getElementById("unit" + i).value;
        if (qty && qty > 0) {
          result += `${veg.en} (${veg.te}): ${qty} ${unit}\n`;
        }
      });
      document.getElementById("summary").textContent = result || "No vegetables selected.";
    }
  </script>
</body>
</html>
