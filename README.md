<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>WimoPay</title>
  <style>
    body {
      font-family: sans-serif;
      padding: 20px;
      max-width: 800px;
      margin: auto;
      background-color: #ffffff;
      color: #002c5f;
    }
    h1, h2 {
      text-align: center;
    }
    .survey-section {
      margin-bottom: 30px;
      border: 2px solid #f7d800;
      background-color: #fffbe6;
      padding: 20px;
      border-radius: 15px;
    }
    .menu-item {
      background-color: #e6f0ff;
      border: 1px solid #b3d1ff;
      padding: 10px;
      border-radius: 10px;
      margin-top: 20px;
    }
    .menu-item img {
      max-width: 100%;
      border-radius: 8px;
    }
    .menu-item p {
      margin-top: 10px;
    }
    input {
      width: 100%;
      margin-bottom: 10px;
      padding: 8px;
      border-radius: 5px;
      border: 1px solid #ccc;
    }
    button {
      background-color: #f7d800;
      color: #002c5f;
      font-weight: bold;
      padding: 10px 20px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
    }
    button:hover {
      background-color: #ffe135;
    }
  </style>
</head>
<body>

  <h1>Catalogo WimoPay</h1>

  <!-- Registro de visitante -->
  <div id="surveySection" class="survey-section">
    <h2>Antes de ver el menú</h2>
    <label for="nombre">Nombre completo:</label>
    <input type="text" id="nombre" placeholder="Ej. Juan Pérez">

    <label for="municipio">Municipio:</label>
    <input type="text" id="municipio" placeholder="Ej. Guadalajara">

    <label for="colonia">Colonia:</label>
    <input type="text" id="colonia" placeholder="Ej. Lomas Verdes">

    <label for="telefono">Teléfono (opcional):</label>
    <input type="tel" id="telefono" placeholder="Ej. 33 1234 5678">

    <button onclick="validarEncuesta()">Ver Menú</button>
  </div>

  <!-- Menú (solo visible después del registro) -->
  <div id="menuSection" style="display: none;">
    <h2>Menú Actual</h2>

    <!-- Puedes dejar los productos como ya los tienes aquí -->
    <!-- Aquí va tu lista de productos del 1 al 35 (omitidos por brevedad) -->

    <!-- Contacto con Asesor -->
    <div class="survey-section">
      <h2>¿Necesitas ayuda?</h2>
      <p>Haz clic abajo y uno de nuestros asesores te contactará por WhatsApp.</p>
      <button onclick="contactarAsesor()">Contactar Asesor</button>
    </div>
  </div>

  <script>
    function validarEncuesta() {
      const nombre = document.getElementById("nombre").value.trim();
      const municipio = document.getElementById("municipio").value.trim();
      const colonia = document.getElementById("colonia").value.trim();

      if (!nombre || !municipio || !colonia) {
        alert("Por favor, completa tu nombre, municipio y colonia.");
        return;
      }

      document.getElementById("surveySection").style.display = "none";
      document.getElementById("menuSection").style.display = "block";
    }

    function contactarAsesor() {
      const nombre = document.getElementById("nombre").value.trim();
      const municipio = document.getElementById("municipio").value.trim();
      const colonia = document.getElementById("colonia").value.trim();

      const asesores = [
        { nombre: "Jesica ", telefono: "5213312345678" },
        { nombre: "Jesus Copado", telefono: "5213323456789" },
        { nombre: "Manuel Olivares", telefono: "5213334567890" },
        { nombre: "Luis García", telefono: "5213345678901" }
      ];

      const asesor = asesores[Math.floor(Math.random() * asesores.length)];
      const mensaje = encodeURIComponent(
        `Hola ${asesor.nombre}, soy ${nombre} de ${colonia}, ${municipio}. Necesito ayuda con el menú de WimoPay.`
      );
      const enlace = `https://wa.me/${asesor.telefono}?text=${mensaje}`;

      window.open(enlace, '_blank');
    }
  </script>

</body>
</html>
