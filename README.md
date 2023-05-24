<!DOCTYPE html>
<html>
<head>
    <title>[A&B SHOP]</title>
    <style>
        body {
            background-color: pink;
            text-align: center;
        }

        h1 {
            animation: colorChange 10s infinite;
        }

        @keyframes colorChange {
            0% { color: red; }
            50% { color: blue; }
            100% { color: green; }
        }

        .product {
            display: inline-block;
            margin: 10px;
            padding: 10px;
            border: 1px solid black;
            background-color: white;
            position: relative;
        }

        .product img {
            width: 200px;
            height: 200px;
            display: block;
            margin: 0 auto;
            border: 5px solid red;
            animation: frameChange 2s infinite;
        }

        @keyframes frameChange {
            0% { border-color: red; }
            50% { border-color: blue; }
            100% { border-color: green; }
        }

        #cart {
            margin-top: 20px;
        }

        #ticket-container {
            margin-top: 20px;
        }

        #instructions {
            margin-top: 20px;
            padding: 20px;
            border: 2px solid black;
            background-color: #f9f9f9;
            text-align: center;
        }
    </style>
</head>
<body>
    <h1>[A&B SHOP]</h1>

    <div id="instructions">
        <h3>¡Bienvenido a nuestra tienda en línea!</h3>
        <p>Aquí encontrarás una amplia selección de productos de moda a precios increíbles.</p>
        <p>Para realizar una compra, sigue estos pasos:</p>
        <ol>
            <li>Explora nuestra sección de productos en venta.</li>
            <li>Selecciona los productos que deseas adquirir y agrégalos al carrito de compras.</li>
            <li>Haz clic en el botón "Realizar Pedido" para generar el ticket de pedido.</li>
            <li>Revisa el ticket de pedido y confirma los productos y el total a pagar.</li>
            <li>Haz clic en el botón "Enviar por WhatsApp" para enviar el ticket a nuestro número de WhatsApp.</li>
            <li>¡Listo! Tu pedido será procesado y te contactaremos para coordinar el envío y el pago.</li>
        </ol>
        <p>Aceptamos diferentes formas de pago, como tarjeta de crédito, transferencia bancaria y pago en efectivo.</p>
    </div>

    <h2>Productos en venta</h2>
    <div id="product-container"></div>

    <h2>Carrito de Compras</h2>
    <div id="cart"></div>
    <button onclick="generateTicket()">Realizar Pedido</button>

    <h2>Ticket de Pedido</h2>
    <div id="ticket-container"></div>
    <button onclick="sendTicket()">Enviar por WhatsApp</button>

    <button onclick="location.reload()">Realizar otro pedido</button>

    <script>
        var products = [
            { name: 'Camisa', price: 25.99, image: '001.jpg' },
            { name: 'Pantalón', price: 39.99, image: 'pants.jpg' },
            { name: 'Zapatos', price: 59.99, image: 'shoes.jpg' },
            { name: 'Vestido', price: 49.99, image: 'dress.jpg' },
            { name: 'Sombrero', price: 19.99, image: 'hat.jpg' },
            { name: 'Corbata', price: 14.99, image: 'tie.jpg' },
            // Agregar aquí los 30 productos adicionales
            { name: 'Blusa', price: 29.99, image: 'blouse.jpg' },
            { name: 'Shorts', price: 34.99, image: 'shorts.jpg' },
            { name: 'Chaqueta', price: 69.99, image: 'jacket.jpg' },
            { name: 'Falda', price: 39.99, image: 'skirt.jpg' },
            { name: 'Calcetines', price: 9.99, image: 'socks.jpg' },
            { name: 'Sudadera', price: 49.99, image: 'hoodie.jpg' },
            { name: 'Gorra', price: 19.99, image: 'cap.jpg' },
            { name: 'Pijama', price: 54.99, image: 'pajamas.jpg' },
            { name: 'Bolso', price: 39.99, image: 'bag.jpg' },
            { name: 'Reloj', price: 79.99, image: 'watch.jpg' },
            { name: 'Jersey', price: 44.99, image: 'sweater.jpg' },
            { name: 'Anillo', price: 29.99, image: 'ring.jpg' },
            { name: 'Blazer', price: 59.99, image: 'blazer.jpg' },
            { name: 'Gafas de sol', price: 24.99, image: 'sunglasses.jpg' },
            { name: 'Pantalones cortos', price: 34.99, image: 'shortpants.jpg' },
            { name: 'Cinturón', price: 14.99, image: 'belt.jpg' },
            { name: 'Bikini', price: 39.99, image: 'bikini.jpg' },
            { name: 'Bufanda', price: 19.99, image: 'scarf.jpg' },
            { name: 'Tacones', price: 59.99, image: 'heels.jpg' },
            { name: 'Sweatshirt', price: 44.99, image: 'sweatshirt.jpg' },
            { name: 'Pantalones de yoga', price: 29.99, image: 'yogapants.jpg' },
            { name: 'Vestido de noche', price: 69.99, image: 'eveningdress.jpg' },
            { name: 'Calcetines deportivos', price: 9.99, image: 'sportsocks.jpg' },
            { name: 'Gorro de invierno', price: 19.99, image: 'winterhat.jpg' },
            { name: 'Traje de baño', price: 39.99, image: 'swimsuit.jpg' },
        ];

        var cart = [];

        function displayProducts() {
            var productContainer = document.getElementById('product-container');

            for (var i = 0; i < products.length; i++) {
                var product = products[i];

                var productDiv = document.createElement('div');
                productDiv.className = 'product';

                var productName = document.createElement('h3');
                productName.textContent = product.name;

                var productImage = document.createElement('img');
                productImage.src = product.image;

                var productPrice = document.createElement('p');
                productPrice.textContent = '$' + product.price.toFixed(2);

                var addToCartButton = document.createElement('button');
                addToCartButton.textContent = 'Agregar al Carrito';
                addToCartButton.onclick = function (product) {
                    return function () {
                        addToCart(product);
                        this.disabled = true;
                    };
                }(product);

                productDiv.appendChild(productName);
                productDiv.appendChild(productImage);
                productDiv.appendChild(productPrice);
                productDiv.appendChild(addToCartButton);

                productContainer.appendChild(productDiv);
            }
        }

        function addToCart(product) {
            cart.push(product);
            updateCart();
        }

        function updateCart() {
            var cartDiv = document.getElementById('cart');
            cartDiv.innerHTML = '';

            var total = 0;

            for (var i = 0; i < cart.length; i++) {
                var cartItem = cart[i];

                var cartItemDiv = document.createElement('div');
                cartItemDiv.textContent = cartItem.name + ' - $' + cartItem.price.toFixed(2);

                cartDiv.appendChild(cartItemDiv);

                total += cartItem.price;
            }

            var totalDiv = document.createElement('div');
            totalDiv.textContent = 'Total: $' + total.toFixed(2);

            cartDiv.appendChild(totalDiv);
        }

        function generateTicket() {
            var ticketContainer = document.getElementById('ticket-container');
            ticketContainer.innerHTML = '';

            var ticketHeader = document.createElement('h3');
            ticketHeader.textContent = 'Ticket de Pedido';

            var ticketList = document.createElement('ul');

            for (var i = 0; i < cart.length; i++) {
                var ticketItem = document.createElement('li');
                ticketItem.textContent = cart[i].name + ' - $' + cart[i].price.toFixed(2);
                ticketList.appendChild(ticketItem);
            }

            var totalDiv = document.createElement('div');
            totalDiv.textContent = 'Total a pagar: $' + getTotal().toFixed(2);

            var thankYouMessage = document.createElement('p');
            thankYouMessage.textContent = 'Gracias por comprar con nosotros. Su pedido está siendo procesado. Por favor, envíe el siguiente mensaje a nuestro número de WhatsApp:';

            var whatsappMessage = document.createElement('p');
            whatsappMessage.textContent = 'Pedido: ' + getCartItemsString() + ', Total: $' + getTotal().toFixed(2) + ', Gracias por su compra.';

            ticketContainer.appendChild(ticketHeader);
            ticketContainer.appendChild(ticketList);
            ticketContainer.appendChild(totalDiv);
            ticketContainer.appendChild(thankYouMessage);
            ticketContainer.appendChild(whatsappMessage);
        }

       
        function sendTicket() {
    var ticketInfo = 'Gracias por comprar con nosotros. Su pedido está siendo procesado. Por favor, revise los detalles a continuación:\n\n';

    // Agregar los productos al mensaje con separaciones y marcos
    for (var i = 0; i < cart.length; i++) {
        var product = cart[i];
        ticketInfo += '━━━━━━━━━━━━━━━━━━━━━━━\n';
        ticketInfo += 'Producto: ' + product.name + '\n';
        ticketInfo += 'Precio: $' + product.price.toFixed(2) + '\n';
        ticketInfo += '━━━━━━━━━━━━━━━━━━━━━━━\n\n';
    }

    // Agregar el total a pagar
    ticketInfo += 'Total a pagar: $' + getTotal().toFixed(2) + '\n\n';

    // Agregar mensaje de agradecimiento
    ticketInfo += 'Gracias por su compra.\n';

    var whatsappUrl = 'https://wa.me/5620791336?text=' + encodeURIComponent(ticketInfo);

    window.open(whatsappUrl);
}

        function getTotal() {
            var total = 0;

            for (var i = 0; i < cart.length; i++) {
                total += cart[i].price;
            }

            return total;
        }

        function getCartItemsString() {
            var itemsString = '';

            for (var i = 0; i < cart.length; i++) {
                itemsString += cart[i].name + ', ';
            }

            itemsString = itemsString.slice(0, -2);

            return itemsString;
        }

        displayProducts();
    </script>
</body>
</html>
