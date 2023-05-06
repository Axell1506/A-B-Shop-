<!DOCTYPE html>
<html>
<head>
	<title>Catalogo de Ropa</title>
	<style>
		body {
			background-color: #f6a5c0;
			font-family: Arial, sans-serif;
			text-align: center;
		}

		h1 {
			color: #ffffff;
			font-size: 36px;
			margin-top: 50px;
		}

		h2 {
			color: #ffffff;
			font-size: 24px;
			margin-top: 30px;
		}

		.container {
			display: flex;
			flex-wrap: wrap;
			justify-content: center;
			margin-top: 50px;
		}

		.producto {
			width: 300px;
			margin: 20px;
			border: 2px solid #ffffff;
			padding: 20px;
			background-color: #ffffff;
			border-radius: 10px;
			box-shadow: 0 0 10px #000000;
		}

		.producto img {
			width: 100%;
			margin-bottom: 10px;
		}

		.producto h3 {
			font-size: 20px;
			margin-bottom: 10px;
		}

		.producto p {
			font-size: 16px;
			margin-bottom: 10px;
		}

		.precio {
			font-size: 24px;
			font-weight: bold;
			color: #ff0000;
		}

		.descuento {
			font-size: 24px;
			font-weight: bold;
			color: #00ff00;
		}
	</style>
</head>
<body>
	<h1>Catalogo de Ropa</h1>
	<h2>Ropa con precio alto</h2>
	<div class="container">
		<div class="producto">
			<img src="https://via.placeholder.com/300x300.png?text=Producto1">
			<h3>Producto 1</h3>
			<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed commodo euismod sapien, vel aliquet massa faucibus eget.</p>
			<p class="precio">$100.00</p>
		</div>
		<div class="producto">
			<img src="https://via.placeholder.com/300x300.png?text=Producto2">
			<h3>Producto 2</h3>
			<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed commodo euismod sapien, vel aliquet massa faucibus eget.</p>
			<p class="precio">$200.00</p>
		</div>
		<!-- Agregar más productos de precio alto aquí -->
	</div>

	<h2>Ropa con descuento</h2>
	<div class="container">
		<div class="producto">
			<img src="https://via.placeholder.com/300x300.png?text=Producto3">
			<h3>Producto 3</h3>
			<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed commodo euismod sapien, vel aliquet massa faucibus eget.</p>
			<p class="descuento">$80.00</p>
		</div>
		<div class="producto">
			<img src="https://via.placeholder.com/300x300.png?text=Producto4">
			<h3>Producto 4</h3>
			<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed commodo eu
