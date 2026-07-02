<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-slate-100 p-6">
    <div class="max-w-lg mx-auto bg-white p-8 rounded-xl shadow-md">
        <h1 class="text-2xl font-bold mb-6 text-center">Registro de Pedidos</h1>
        <form id="form" class="space-y-4">
            <input type="number" id="dni" placeholder="DNI" class="w-full p-2 border rounded" required>
            <input type="text" id="apellido" placeholder="APELLIDO" class="w-full p-2 border rounded uppercase" required>
            <input type="text" id="nombre" placeholder="NOMBRE" class="w-full p-2 border rounded uppercase" required>
            <select id="sede" class="w-full p-2 border rounded" required>
                <option value="">Selecciona sede</option>
                <option value="Central">Central</option>
                <option value="Las Heras">Las Heras</option>
                <option value="Uspallata">Uspallata</option>
            </select>
            <select id="carrera" class="w-full p-2 border rounded" required>
                <option value="">Selecciona carrera</option>
                <option value="Tecnicatura">Tecnicatura</option>
                <option value="Licenciatura">Licenciatura</option>
            </select>
            <button type="button" onclick="enviar()" class="w-full bg-blue-600 text-white py-2 rounded hover:bg-blue-700">Enviar Pedido</button>
        </form>
    </div>

    <script>
        function enviar() {
            const url = "PEGA_AQUÍ_TU_URL_DE_APPSCRIPT_QUE_TERMINA_EN_/exec";
            const datos = {
                dni: document.getElementById('dni').value,
                apellido: document.getElementById('apellido').value.toUpperCase(),
                nombre: document.getElementById('nombre').value.toUpperCase(),
                sede: document.getElementById('sede').value,
                carrera: document.getElementById('carrera').value
            };

            fetch(url, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify(datos)
            })
            .then(r => r.text())
            .then(res => alert("Respuesta: " + res))
            .catch(err => alert("Error: " + err));
        }
    </script>
</body>
</html>
