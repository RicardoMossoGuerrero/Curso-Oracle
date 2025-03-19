<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sorteo Amigo Secreto</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 600px;
            margin: 2rem auto;
            padding: 0 1rem;
        }
        .container {
            background-color: #f5f5f5;
            padding: 2rem;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        .input-group {
            display: flex;
            gap: 1rem;
            margin-bottom: 1rem;
        }
        input {
            padding: 0.5rem;
            flex: 1;
        }
        button {
            padding: 0.5rem 1rem;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
        #sortearBtn {
            background-color: #2196F3;
        }
        #sortearBtn:hover {
            background-color: #1976D2;
        }
        #listaAmigos {
            list-style-type: none;
            padding: 0;
        }
        #listaAmigos li {
            background-color: white;
            padding: 0.5rem;
            margin: 0.5rem 0;
            border-radius: 4px;
        }
        #resultado {
            margin-top: 1rem;
            padding: 1rem;
            background-color: #E8F5E9;
            border-radius: 4px;
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Sorteo Amigo Secreto</h1>
        
        <div class="input-group">
            <input type="text" id="nombreAmigo" placeholder="Ingresa el nombre de un amigo">
            <button onclick="agregarAmigo()">Adicionar</button>
        </div>

        <ul id="listaAmigos"></ul>
        
        <button id="sortearBtn" onclick="sortearAmigo()">Sortear Amigo</button>
        
        <div id="resultado"></div>
    </div>

    <script>
        // Array para almacenar los nombres de los amigos
        let amigos = [];

        // Función para agregar un amigo a la lista
        function agregarAmigo() {
            const inputNombre = document.getElementById('nombreAmigo');
            const nombre = inputNombre.value.trim();

            // Validar que el campo no esté vacío
            if (nombre === '') {
                alert('Por favor, ingresa un nombre válido');
                return;
            }

            // Agregar el nombre al array
            amigos.push(nombre);

            // Actualizar la lista visual
            actualizarLista();

            // Limpiar el campo de entrada
            inputNombre.value = '';
        }

        // Función para actualizar la lista visual
        function actualizarLista() {
            const lista = document.getElementById('listaAmigos');
            lista.innerHTML = '';

            amigos.forEach(amigo => {
                const li = document.createElement('li');
                li.textContent = amigo;
                lista.appendChild(li);
            });
        }

        // Función para sortear un amigo aleatorio
        function sortearAmigo() {
            if (amigos.length === 0) {
                alert('Agrega al menos un amigo antes de sortear');
                return;
            }

            // Seleccionar un amigo aleatorio
            const indiceAleatorio = Math.floor(Math.random() * amigos.length);
            const amigoSeleccionado = amigos[indiceAleatorio];

            // Mostrar el resultado
            const resultado = document.getElementById('resultado');
            resultado.style.display = 'block';
            resultado.innerHTML = `<h3>¡El amigo seleccionado es:</h3><p>${amigoSeleccionado}</p>`;
        }
    </script>
</body>
</html>
