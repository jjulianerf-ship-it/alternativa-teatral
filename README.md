<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tienda de Artículos Deportivos</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }
        header {
            background-color: #333;
            color: #fff;
            padding: 10px 0;
            text-align: center;
        }
        header h1 {
            margin: 0;
        }
        nav {
            background-color: #444;
            padding: 10px;
            text-align: center;
        }
        nav a {
            color: #fff;
            margin: 0 15px;
            text-decoration: none;
            font-weight: bold;
        }
        .container {
            width: 80%;
            margin: auto;
            overflow: hidden;
        }
        .main-content {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-around;
            margin: 20px 0;
        }
        .category {
            background-color: #fff;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            margin: 10px;
            padding: 15px;
            text-align: center;
            width: 30%;
        }
        .category img {
            max-width: 100%;
            border-radius: 8px;
        }
        .category h2 {
            margin: 15px 0;
            font-size: 1.5em;
            color: #333;
        }
        footer {
            background-color: #333;
            color: #fff;
            padding: 10px 0;
            text-align: center;
        }
    </style>
</head>
<body>
    <header>
        <h1>Tienda de Artículos Deportivos</h1>
    </header>

    <nav>
        <a href="#yoga">Yoga</a>
        <a href="#golf">Golf</a>
        <a href="#baloncesto">Baloncesto</a>
        <a href="#tenis">Tenis</a>
        <a href="#rafting">Rafting</a>
        <a href="#ciclismo">Ciclismo</a>
        <a href="#patinaje">Patinaje</a>
        <a href="#paracaidismo">Paracaidismo</a>
        <a href="#esqui">Esquí</a>
    </nav>

    <div class="container">
        <div class="main-content">
            <div class="category" id="yoga">
                <img src="https://example.com/yoga.jpg" alt="Yoga">
                <h2>Yoga</h2>
                <p>Encuentra los mejores equipos y accesorios para tus prácticas de yoga.</p>
            </div>
            <div class="category" id="golf">
                <img src="https://example.com/golf.jpg" alt="Golf">
                <h2>Golf</h2>
                <p>Todo lo necesario para mejorar tu juego de golf.</p>
            </div>
            <div class="category" id="baloncesto">
                <img src="https://example.com/baloncesto.jpg" alt="Baloncesto">
                <h2>Baloncesto</h2>
                <p>Compra balones, zapatillas y más para tus partidos de baloncesto.</p>
            </div>
            <div class="category" id="tenis">
                <img src="https://example.com/tenis.jpg" alt="Tenis">
                <h2>Tenis</h2>
                <p>Equipos y accesorios para tus partidos de tenis.</p>
            </div>
            <div class="category" id="rafting">
                <img src="https://example.com/rafting.jpg" alt="Rafting">
                <h2>Rafting</h2>
                <p>Todo lo necesario para tus aventuras en el rafting.</p>
            </div>
            <div class="category" id="ciclismo">
                <img src="https://example.com/ciclismo.jpg" alt="Ciclismo">
                <h2>Ciclismo</h2>
                <p>Encuentra bicicletas y accesorios para tus rutas.</p>
            </div>
            <div class="category" id="patinaje">
                <img src="https://example.com/patinaje.jpg" alt="Patinaje">
                <h2>Patinaje</h2>
                <p>Todo para disfrutar del patinaje, desde patines hasta accesorios.</p>
            </div>
            <div class="category" id="paracaidismo">
                <img src="https://example.com/paracaidismo.jpg" alt="Paracaidismo">
                <h2>Paracaidismo</h2>
                <p>Equipos para tus saltos en paracaídas.</p>
            </div>
            <div class="category" id="esqui">
                <img src="https://example.com/esqui.jpg" alt="Esquí">
                <h2>Esquí</h2>
                <p>Todo lo que necesitas para tus aventuras en la nieve.</p>
            </div>
        </div>
    </div>

    <footer>
        <p>&copy; 2024 Tienda de Artículos Deportivos. Todos los derechos reservados.</p>
    </footer>
</body>
</html>
