<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pemesanan Sederhana Kafe</title>
    
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f5f5dc; /* Warna krem seperti kopi */
            color: #4a2c2a;
            margin: 0;
            padding: 20px;
        }
        .container {
            max-width: 700px;
            margin: auto;
            background-color: #ffffff;
            padding: 25px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }
        header {
            text-align: center;
            border-bottom: 2px solid #eee;
            margin-bottom: 20px;
        }
        h1 {
            color: #6f4e37;
        }
        h2 {
            color: #8b6b61;
            border-bottom: 1px solid #f0f0f0;
            padding-bottom: 5px;
            margin-top: 30px; /* Jarak antar kategori */
        }
        .menu-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 15px;
        }
        .menu-item {
            border: 1px solid #ddd;
            border-radius: 8px;
            padding: 15px;
            text-align: center;
        }
        .menu-item h3 {
            margin-top: 0;
        }
        .menu-item .price {
            font-weight: bold;
            color: #6f4e37;
            margin: 10px 0;
        }
        .add-to-cart-btn {
            background-color: #8b6b61;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
            transition: background-color 0.3s;
        }
        .add-to-cart-btn:hover {
            background-color: #6f4e37;
        }
        #cart-section, #form-section {
            margin-top: 30px;
        }
        #cart-items {
            list-style: none;
            padding: 0;
        }
        #cart-items li {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 8px 0;
            border-bottom: 1px solid #eee;
        }
        .delete-btn {
            background-color: #e74c3c;
            color: white;
            border: none;
            border-radius: 50%;
            width: 22px;
            height: 22px;
            font-weight: bold;
            cursor: pointer;
            margin-left: 10px;
            line-height: 22px; /* Vertically center the 'x' */
        }
        .delete-btn:hover {
            background-color: #c0392b;
        }
        #cart-total {
            text-align: right;
            font-size: 1.2em;
            font-weight: bold;
            margin-top: 10px;
        }
        form input {
            width: calc(100% - 20px);
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        #submit-order {
            width: 100%;
            padding: 15px;
            font-size: 1.1em;
            background-color: #6f4e37;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .modal {
            display: none;
            position: fixed;
            z-index: 1000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.6);
            align-items: center;
            justify-content: center;
        }
        .modal-content {
            background-color: #fff;
            padding: 30px;
            border-radius: 10px;
            text-align: center;
            position: relative;
        }
        .close-button {
            position: absolute;
            top: 10px;
            right: 15px;
            font-size: 28px;
            font-weight: bold;
            cursor: pointer;
        }
    </style>
</head>
<body>

    <div class="container">
        <header>
            <h1>Kafe Sederhana</h1>
            <p>Pesan menu favoritmu di bawah ini.</p>
        </header>

        <section id="menu-section">

            <h2>Cemilan</h2>
            <div class="menu-grid">
                <div class="menu-item">
                    <h3>Roti Bakar</h3>
                    <p class="price">Rp 12.000</p>
                    <button class="add-to-cart-btn" data-name="Roti Bakar" data-price="12000">Tambah</button>
                </div>
                <div class="menu-item">
                    <h3>Seblak</h3>
                    <p class="price">Rp 15.000</p>
                    <button class="add-to-cart-btn" data-name="Seblak" data-price="15000">Tambah</button>
                </div>
                <div class="menu-item">
                    <h3>Martabak Lumpia</h3>
                    <p class="price">Rp 10.000</p>
                    <button class="add-to-cart-btn" data-name="Martabak Lumpia" data-price="10000">Tambah</button>
                </div>
                <div class="menu-item">
                    <h3>Bakso Aci</h3>
                    <p class="price">Rp 15.000</p>
                    <button class="add-to-cart-btn" data-name="Bakso Aci" data-price="15000">Tambah</button>
                </div>
                <div class="menu-item">
                    <h3>Es Pisang Ijo</h3>
                    <p class="price">Rp 13.000</p>
                    <button class="add-to-cart-btn" data-name="Es Pisang Ijo" data-price="13000">Tambah</button>
                </div>
                <div class="menu-item">
                    <h3>Es Kul Kul</h3>
                    <p class="price">Rp 5.000</p>
                    <button class="add-to-cart-btn" data-name="Es Kul Kul" data-price="5000">Tambah</button>
                </div>
                <div class="menu-item">
                    <h3>Fishcake</h3>
                    <p class="price">Rp 10.000</p>
                    <button class="add-to-cart-btn" data-name="Fishcake" data-price="10000">Tambah</button>
                </div>
            </div>

            <h2>Makanan Berat</h2>
            <div class="menu-grid">
                <div class="menu-item">
                    <h3>Ayam Karage/Pop</h3>
                    <p class="price">Rp 25.000</p>
                    <button class="add-to-cart-btn" data-name="Ayam Karage/Pop" data-price="25000">Tambah</button>
                </div>
                <div class="menu-item">
                    <h3>Nugget Geprek</h3>
                    <p class="price">Rp 20.000</p>
                    <button class="add-to-cart-btn" data-name="Nugget Geprek" data-price="20000">Tambah</button>
                </div>
                <div class="menu-item">
                    <h3>Bento</h3>
                    <p class="price">Rp 30.000</p>
                    <button class="add-to-cart-btn" data-name="Bento" data-price="30000">Tambah</button>
                </div>
            </div>

            <h2>Minuman</h2>
            <div class="menu-grid">
                <div class="menu-item">
                    <h3>Es Teh</h3>
                    <p class="price">Rp 5.000</p>
                    <button class="add-to-cart-btn" data-name="Es Teh" data-price="5000">Tambah</button>
                </div>
                <div class="menu-item">
                    <h3>Mojito</h3>
                    <p class="price">Rp 15.000</p>
                    <button class="add-to-cart-btn" data-name="Mojito" data-price="15000">Tambah</button>
                </div>
            </div>

        </section>

        <section id="cart-section">
            <h2>Keranjang Anda</h2>
            <ul id="cart-items">
                </ul>
            <p id="cart-total">Total: Rp 0</p>
        </section>

        <section id="form-section">
            <h2>2. Isi Data Anda</h2>
            <form id="order-form">
                <input type="text" id="customer-name" placeholder="Nama Anda" required>
                <input type="text" id="customer-address" placeholder="Diantar kemana / Nomor Meja" required>
                <button type="submit" id="submit-order">Bayar dengan QRIS</button>
            </form>
        </section>
    </div>

    <div id="qris-modal" class="modal">
        <div class="modal-content">
            <span class="close-button">&times;</span>
            <h2>Pembayaran QRIS</h2>
            <p>Scan QR code di bawah ini untuk membayar.</p>
            <img src="https://www.investree.id/blog/wp-content/uploads/2021/11/QRIS-3.png.webp" alt="QRIS Code" width="200">
            <h3 id="qris-total">Total: Rp 0</h3>
            <small style="color:red;">Ini hanya simulasi.</small>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {

            const menuSection = document.getElementById('menu-section');
            const cartItems = document.getElementById('cart-items');
            const cartTotal = document.getElementById('cart-total');
            const orderForm = document.getElementById('order-form');
            const qrisModal = document.getElementById('qris-modal');
            const qrisTotal = document.getElementById('qris-total');
            const closeButton = document.querySelector('.close-button');

            let cart = [];

            function formatRupiah(angka) {
                return new Intl.NumberFormat('id-ID', { style: 'currency', currency: 'IDR', minimumFractionDigits: 0 }).format(angka);
            }

            function updateCartDisplay() {
                cartItems.innerHTML = '';
                let total = 0;
                if (cart.length === 0) {
                    const li = document.createElement('li');
                    li.textContent = 'Keranjang masih kosong.';
                    cartItems.appendChild(li);
                } else {
                    cart.forEach((item, index) => {
                        const li = document.createElement('li');
                        li.innerHTML = `
                            <span>${item.name}</span>
                            <span>
                                ${formatRupiah(item.price)}
                                <button class="delete-btn" data-index="${index}">&times;</button>
                            </span>
                        `;
                        cartItems.appendChild(li);
                        total += item.price;
                    });
                }
                cartTotal.textContent = `Total: ${formatRupiah(total)}`;
            }

            menuSection.addEventListener('click', function(event) {
                if (event.target.classList.contains('add-to-cart-btn')) {
                    const name = event.target.dataset.name;
                    const price = parseInt(event.target.dataset.price);
                    cart.push({ name, price });
                    updateCartDisplay();
                }
            });

            cartItems.addEventListener('click', function(event) {
                if (event.target.classList.contains('delete-btn')) {
                    const indexToDelete = parseInt(event.target.dataset.index);
                    cart.splice(indexToDelete, 1);
                    updateCartDisplay();
                }
            });

            orderForm.addEventListener('submit', function(event) {
                event.preventDefault();
                const customerName = document.getElementById('customer-name').value;
                const customerAddress = document.getElementById('customer-address').value;
                if (cart.length === 0) {
                    alert('Keranjang Anda masih kosong!');
                    return;
                }
                if (customerName === '' || customerAddress === '') {
                    alert('Harap isi nama dan tujuan Anda!');
                    return;
                }
                const finalTotal = cart.reduce((sum, item) => sum + item.price, 0);
                qrisTotal.textContent = `Total: ${formatRupiah(finalTotal)}`;
                qrisModal.style.display = 'flex';
            });

            function closeModal() {
                qrisModal.style.display = 'none';
            }
            closeButton.addEventListener('click', closeModal);
            window.addEventListener('click', function(event) {
                if (event.target == qrisModal) {
                    closeModal();
                }
            });
            
            updateCartDisplay();
        });
    </script>
</body>

</html>
