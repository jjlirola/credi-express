<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Calculadora de Préstamo</title>
  <style>
    body {
      background-color: #ffffff;
      font-family: Arial, sans-serif;
      padding: 20px;
      color: #003366;
    }
    .calculadora {
      max-width: 400px;
      margin: auto;
      background: #fff;
      padding: 24px;
      border-radius: 12px;
      box-shadow: 0 0 12px rgba(0, 0, 0, 0.1);
    }
    h2 {
      text-align: center;
      color: #003366;
    }
    label {
      font-weight: bold;
      margin-top: 10px;
      display: block;
    }
    input[type="range"] {
      width: 100%;
    }
    .valores {
      display: flex;
      justify-content: space-between;
      font-size: 14px;
      margin-bottom: 4px;
    }
    .resultado p {
      margin: 6px 0;
    }
  </style>
</head>
<body>
  <div class="calculadora">
    <h2>Calcula tu crédito online</h2>

    <label for="monto">¿Cuánto dinero necesitas?</label>
    <div class="valores"><span>50€</span><span>300€</span></div>
    <input type="range" id="monto" min="50" max="300" step="10" value="100" oninput="update()">
    <p><strong>Importe seleccionado:</strong> <span id="montoDisplay">100</span> €</p>

    <label for="plazo">¿En cuántos días quieres devolverlo?</label>
    <div class="valores"><span>7</span><span>30 días</span></div>
    <input type="range" id="plazo" min="7" max="30" step="1" value="15" oninput="update()">
    <p><strong>Plazo seleccionado:</strong> <span id="plazoDisplay">15</span> días</p>

    <hr/>

    <div class="resultado">
      <p><strong>Importe solicitado:</strong> <span id="importe">100</span> €</p>
      <p><strong>Intereses estimados:</strong> <span id="intereses">15</span> €</p>
      <p><strong>Total a devolver:</strong> <span id="total">115</span> €</p>
      <p><strong>Fecha estimada de devolución:</strong> <span id="fecha"></span></p>
    </div>
  </div>

  <script>
    function update() {
      const monto = parseInt(document.getElementById("monto").value);
      const plazo = parseInt(document.getElementById("plazo").value);
      const interesDiario = 0.01;
      const intereses = Math.round(monto * interesDiario * plazo);
      const total = monto + intereses;

      const hoy = new Date();
      hoy.setDate(hoy.getDate() + plazo);
      const fechaDevolucion = hoy.toLocaleDateString('es-ES');

      document.getElementById("montoDisplay").textContent = monto;
      document.getElementById("plazoDisplay").textContent = plazo;
      document.getElementById("importe").textContent = monto;
      document.getElementById("intereses").textContent = intereses;
      document.getElementById("total").textContent = total;
      document.getElementById("fecha").textContent = fechaDevolucion;
    }

    update();
  </script>
</body>
</html>
