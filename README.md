# index.html
<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora</title>
</head>
<body>
    <h1>Somar Números</h1>
    <input type="number" id="num1" placeholder="Digite o primeiro número">
    <input type="number" id="num2" placeholder="Digite o segundo número">
    <button onclick="calcular()">Somar</button>
    <p id="resultado"></p>

    <script>
        function calcular() {
            let a = document.getElementById('num1').value;
            let b = document.getElementById('num2').value;

            fetch('http://localhost:5000/soma', {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ a: Number(a), b: Number(b) })
            })
            .then(response => response.json())
            .then(data => {
                document.getElementById('resultado').innerText = 'Resultado: ' + data.resultado;
            });
        }
    </script>
</body>
</html>
