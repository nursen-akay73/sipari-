const express = require('express');
const bodyParser = require('body-parser');
const cors = require('cors');

const app = express();
app.use(bodyParser.json());
app.use(cors());

let orders = []; // Sipariş listesi

// Sipariş Ekleme
app.post('/addOrder', (req, res) => {
  const { id, product, quantity } = req.body;
  const order = { id, product, quantity, date: new Date() };
  orders.push(order);
  res.status(201).json({ message: 'Sipariş başarıyla eklendi!', order });
});

// Sipariş Listeleme
app.get('/orders', (req, res) => {
  res.json(orders);
});

// Sunucu Başlatma
const PORT = 3000;
app.listen(PORT, () => {
  console.log(`Server running on http://localhost:${PORT}`);
});
