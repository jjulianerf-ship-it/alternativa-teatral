<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calendario y Gestor de Trabajos</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f0f2f5;
            color: #333;
            transition: background-color 0.3s, color 0.3s;
        }
        .container {
            max-width: 1200px;
            margin: auto;
            padding: 20px;
        }
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px 20px;
            background-color: #007bff;
            color: #fff;
            border-radius: 5px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        header h1 {
            margin: 0;
            font-size: 24px;
        }
        button {
            background-color: #007bff;
            color: #fff;
            border: none;
            padding: 10px 15px;
            cursor: pointer;
            border-radius: 5px;
            font-size: 16px;
            transition: background-color 0.3s ease;
        }
        button:hover {
            background-color: #0056b3;
        }
        .dark-mode body {
            background-color: #333;
            color: #f4f4f4;
        }
        .dark-mode header {
            background-color: #444;
        }
        .dark-mode button {
            background-color: #555;
            color: #f4f4f4;
        }
        .dark-mode button:hover {
            background-color: #666;
        }
        .trabajos, .calendario, .form-section, .links {
            margin-bottom: 20px;
            background-color: #fff;
            border-radius: 5px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            padding: 15px;
        }
        .trabajo, .link {
            background-color: #f9f9f9;
            border: 1px solid #ddd;
            border-radius: 5px;
            padding: 10px;
            margin-bottom: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: background-color 0.3s ease;
        }
        .trabajo.completed {
            background-color: #d4edda;
            border-color: #c3e6cb;
        }
        .edit-buttons button {
            margin-right: 5px;
        }
        .edit-task {
            margin-top: 10px;
        }
        .calendario table, .horarios-table {
            width: 100%;
            border-collapse: collapse;
        }
        .calendario th, .calendario td, .horarios-table th, .horarios-table td {
            border: 1px solid #ddd;
            padding: 10px;
            text-align: center;
        }
        .calendario th, .horarios-table th {
            background-color: #007bff;
            color: #fff;
        }
        .calendario td.today {
            background-color: #e7f0ff;
            font-weight: bold;
        }
        .remove-link-button {
            background-color: #dc3545;
            border: none;
            color: #fff;
            padding: 5px;
            cursor: pointer;
            border-radius: 3px;
        }
        .remove-link-button:hover {
            background-color: #c82333;
        }
        .horarios-table th {
            background-color: #007bff;
            color: #fff;
        }
        .horarios-table td {
            background-color: #f9f9f9;
        }
        .horarios-table .yellow {
            background-color: #ffeb3b;
            color: #000000;
        }
        .horarios-table .blue {
            background-color: #2196f3;
            color: #000000;
        }
        .horarios-table .green {
            background-color: #4caf50;
            color: #000000;
        }
        select, input[type="text"], input[type="date"] {
            width: 100%;
            padding: 8px;
            margin: 5px 0;
            border-radius: 5px;
            border: 1px solid #ddd;
        }
        .fixed-links {
            background-color: #f0f2f5;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            margin-top: 20px;
        }
        .message {
            background-color: #ffecb3;
            padding: 10px;
            border: 1px solid #ffd54f;
            border-radius: 5px;
            color: #333;
            font-weight: bold;
            text-align: center;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Calendario version 1.0.3 </h1>
            <button onclick="toggleDarkMode()">Modo Oscuro</button>
        </header>

        <div class="horarios">
            <h2>Tabla de Horarios </h2>
            <table class="horarios-table">
                <thead>
                    <tr>
                        <th>Inicio</th>
                        <th>Lunes</th>
                        <th>Martes</th>
                        <th>Miércoles</th>
                        <th>Jueves</th>
                        <th>Viernes</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>13:00</td>
                        <td class="yellow">ORGANIZACIÓN INDUSTRIAL<br>(Viale)</td>
                        <td class="yellow">PROFESIONALIZANTE I:<br>ORGANIZACIÓN DE LA PRODUCCIÓN<br>(Daneri)<br>PRÁCTICA</td>
                        <td class="blue">ECONOMÍA<br>(Ventañú)</td>
                        <td class="green">ESTADÍSTICAS y<br>DISEÑO DE EXPERIMENTOS<br>(Ortiz)</td>
                        <td class="yellow">ORGANIZACIÓN INDUSTRIAL<br>(Viale)</td>
                    </tr>
                    <tr>
                        <td>14:00</td>
                        <td class="yellow">ORGANIZACIÓN INDUSTRIAL<br>(Viale)</td>
                        <td class="yellow">PROFESIONALIZANTE I:<br>ORGANIZACIÓN DE LA PRODUCCIÓN<br>(Daneri)<br>PRÁCTICA</td>
                        <td class="blue">ECONOMÍA<br>(Ventañú)</td>
                        <td class="green">ESTADÍSTICAS y<br>DISEÑO DE EXPERIMENTOS<br>(Ortiz)</td>
                        <td class="yellow">ORGANIZACIÓN INDUSTRIAL<br>(Viale)</td>
                    </tr>
                    <tr>
                        <td>15:10</td>
                        <td class="green">ESTADÍSTICAS y<br>DISEÑO DE EXPERIMENTOS<br>(Ortiz)</td>
                        <td class="yellow">PROFESIONALIZANTE I:<br>ORGANIZACIÓN DE LA PRODUCCIÓN<br>(Daneri)<br>PRÁCTICA</td>
                        <td class="blue">ECONOMÍA<br>(Ventañú)</td>
                        <td class="yellow">ORGANIZACIÓN INDUSTRIAL<br>(Viale)</td>
                        <td class="yellow">ORGANIZACIÓN INDUSTRIAL<br>(Viale)</td>
                    </tr>
                    <tr>
                        <td>16:10</td>
                        <td class="green">ESTADÍSTICAS y<br>DISEÑO DE EXPERIMENTOS<br>(Ortiz)</td>
                        <td class="yellow">PROFESIONALIZANTE I:<br>ORGANIZACIÓN DE LA PRODUCCIÓN<br>(Daneri)<br>PRÁCTICA</td>
                        <td class="blue">ECONOMÍA<br>(Ventañú)</td>
                        <td class="yellow">ORGANIZACIÓN INDUSTRIAL<br>(Viale)</td>
                        <td class="yellow">ORGANIZACIÓN INDUSTRIAL<br>(Viale)</td>
                    </tr>
                </tbody>
            </table>
        </div>

        <div class="calendario">
            <h2>Calendario</h2>
            <div>
                <button onclick="cambiarMes(-1)">Mes Anterior</button>
                <button onclick="cambiarMes(1)">Mes Siguiente</button>
            </div>
            <table id="calendario">
                <thead id="calendario-header"></thead>
                <tbody id="calendario-body"></tbody>
            </table>
        </div>

        <div class="form-section">
            <h3>Agregar Trabajo</h3>
            <label for="materia">Materia:</label>
            <select id="materia">
                <option value="">Selecciona una materia</option>
                <!-- Las materias se insertarán aquí -->
                    <option value="Estadísticas y Diseño de Experimentos">Estadísticas y Diseño de Experimentos</option>
                    <option value="Economía">Economía</option>
                    <option value="Organización Industrial">Organización Industrial</option>
                    <option value="Práctica Profesionalizante I: Organización de la Producción">Práctica Profesionalizante I: Organización de la Producción</option>
            </select>
            <label for="descripcion">Descripción:</label>
            <input type="text" id="descripcion">
            <label for="fecha">Fecha de Entrega:</label>
            <input type="date" id="fecha">
            <button onclick="agregarTrabajo()">Agregar Trabajo</button>
        </div>
        <div class="form-section">
            <h3>Trabajos</h3>
            <div>
                <button onclick="mostrarTrabajos('todos')">Todos</button>
                <button onclick="mostrarTrabajos('completado')">Completados</button>
                <button onclick="mostrarTrabajos('incompleto')">Incompletos</button>
            </div>
            <div id="trabajos"></div>
        </div>

        <div class="form-section">
            <h3>Links</h3>
            <div id="links-container"></div>
        </div>

        <div class="form-section">
            <h3>Agregar Link</h3>
            <label for="link-url">URL:</label>
            <input type="text" id="link-url" placeholder="Ingrese la URL">
            <label for="link-descripcion">Descripción:</label>
            <input type="text" id="link-descripcion" placeholder="Descripción del link">
            <button onclick="agregarLink()">Agregar Link</button>
        </div>

        <div class="fixed-links">
            <h3>Enlaces Útiles</h3>
            <ul>
        <li><a href="https://www.youtube.com/watch?v=NATSpYWERIE">Enlace 1 futura carpeta</a></li>
        <li><a href="https://drive.google.com/drive/folders/1g4Py5_k3Ue6GW9o9TM00k2C_gWQ9ShsZ?usp=sharing">Enlace 2 trabajos</a></li>
        <li><a href="https://floorplanner.com/projects/160842477/editor">Enlace 3 planos</a></li>
        <li><a href="https://app.diagrams.net/">Enlace 4 diagramas</a></li>
        <li><a href="https://es.wps.com/download/">Enlace 5 WPS</a></li>
        <li><a href="https://www.youtube.com/watch?v=wO1cIvij6PA" target="_blank">importante NO tocar</a></li>
            </ul>
        </div>

        <div class="message">
             No olvides revisar los trabajos y tareas pendientes :)

        </div>
    </div>

    <script>
        const trabajos = JSON.parse(localStorage.getItem('trabajos')) || [];
        const links = JSON.parse(localStorage.getItem('links')) || [];
        const fixedLinks = [
            { url: 'https://www.ejemplo.com', descripcion: 'Ejemplo' },
            { url: 'https://www.ejemplo2.com', descripcion: 'Ejemplo 2' }
        ];
        let darkMode = JSON.parse(localStorage.getItem('darkMode')) || false;

        function toggleDarkMode() {
            darkMode = !darkMode;
            document.body.classList.toggle('dark-mode', darkMode);
            localStorage.setItem('darkMode', JSON.stringify(darkMode));
        }

        function agregarTrabajo() {
            const materia = document.getElementById('materia').value;
            const descripcion = document.getElementById('descripcion').value;
            const fecha = document.getElementById('fecha').value;

            if (!materia || !descripcion || !fecha) {
                alert('Por favor, complete todos los campos.');
                return;
            }

            const trabajo = {
                materia,
                descripcion,
                fecha,
                completado: false
            };

            trabajos.push(trabajo);
            localStorage.setItem('trabajos', JSON.stringify(trabajos));
            mostrarTrabajos();
            notificar(`Nuevo trabajo agregado: ${materia}`);
        }

        function mostrarTrabajos(filtrado = 'todos') {
            const trabajosContainer = document.getElementById('trabajos');
            trabajosContainer.innerHTML = '';

            const trabajosFiltrados = trabajos.filter(trabajo => {
                if (filtrado === 'todos') return true;
                if (filtrado === 'completado') return trabajo.completado;
                if (filtrado === 'incompleto') return !trabajo.completado;
            });

            trabajosFiltrados.forEach((trabajo, index) => {
                const trabajoDiv = document.createElement('div');
                trabajoDiv.className = `trabajo ${trabajo.completado ? 'completed' : ''}`;
                trabajoDiv.innerHTML = `
                    <div>
                        <strong>Materia:</strong> ${trabajo.materia} <br>
                        <strong>Descripción:</strong> ${trabajo.descripcion} <br>
                        <strong>Fecha:</strong> ${trabajo.fecha}
                    </div>
                    <div class="edit-buttons">
                        <button onclick="marcarCompletado(${index})">${trabajo.completado ? 'Marcar Incompleto' : 'Marcar Completado'}</button>
                        <button onclick="eliminarTrabajo(${index})">Eliminar</button>
                    </div>
                `;
                trabajosContainer.appendChild(trabajoDiv);
            });
        }

        function marcarCompletado(index) {
            trabajos[index].completado = !trabajos[index].completado;
            localStorage.setItem('trabajos', JSON.stringify(trabajos));
            mostrarTrabajos();
            notificar(`Trabajo ${trabajos[index].materia} ${trabajos[index].completado ? 'completado' : 'marcado incompleto'}`);
        }

        function eliminarTrabajo(index) {
            trabajos.splice(index, 1);
            localStorage.setItem('trabajos', JSON.stringify(trabajos));
            mostrarTrabajos();
            notificar(`Trabajo eliminado`);
        }

        function agregarLink() {
            const url = document.getElementById('link-url').value;
            const descripcion = document.getElementById('link-descripcion').value;

            if (!url || !descripcion) {
                alert('Por favor, complete todos los campos.');
                return;
            }

            const link = {
                url,
                descripcion
            };

            links.push(link);
            localStorage.setItem('links', JSON.stringify(links));
            mostrarLinks();
            notificar(`Nuevo link agregado: ${descripcion}`);
        }

        function mostrarLinks() {
            const linksContainer = document.getElementById('links-container');
            linksContainer.innerHTML = '';

            links.forEach((link, index) => {
                const linkDiv = document.createElement('div');
                linkDiv.className = 'link';
                linkDiv.innerHTML = `
                    <div>
                        <a href="${link.url}" target="_blank">${link.descripcion}</a>
                        <button class="remove-link-button" onclick="eliminarLink(${index})">Eliminar</button>
                    </div>
                `;
                linksContainer.appendChild(linkDiv);
            });
        }

        function eliminarLink(index) {
            links.splice(index, 1);
            localStorage.setItem('links', JSON.stringify(links));
            mostrarLinks();
            notificar(`Link eliminado`);
        }

        function cambiarMes(direccion) {
            const calendario = document.getElementById('calendario');
            const fechaActual = new Date();
            fechaActual.setMonth(fechaActual.getMonth() + direccion);

            const mes = fechaActual.getMonth();
            const anio = fechaActual.getFullYear();

            const primerDia = new Date(anio, mes, 1);
            const ultimoDia = new Date(anio, mes + 1, 0);
            const diasDeLaSemana = ['Dom', 'Lun', 'Mar', 'Mié', 'Jue', 'Vie', 'Sáb'];

            let html = '<tr>';
            diasDeLaSemana.forEach(dia => html += `<th>${dia}</th>`);
            html += '</tr><tr>';

            for (let i = 0; i < primerDia.getDay(); i++) {
                html += '<td></td>';
            }

            for (let dia = 1; dia <= ultimoDia.getDate(); dia++) {
                const fecha = new Date(anio, mes, dia);
                const esHoy = fecha.toDateString() === new Date().toDateString();
                const trabajosEnFecha = trabajos.filter(trabajo => new Date(trabajo.fecha).toDateString() === fecha.toDateString());
                const actividades = trabajosEnFecha.map(trabajo => `<li>${trabajo.materia}: ${trabajo.descripcion}</li>`).join('');
                html += `
                    <td class="${esHoy ? 'today' : ''}" data-fecha="${fecha.toISOString().split('T')[0]}">
                        ${dia}
                        ${actividades ? `<ul>${actividades}</ul>` : ''}
                    </td>
                `;
                if ((dia + primerDia.getDay()) % 7 === 0) {
                    html += '</tr><tr>';
                }
            }

            if ((ultimoDia.getDate() + primerDia.getDay()) % 7 !== 0) {
                html += '</tr>';
            }

            calendario.querySelector('#calendario-header').innerHTML = `<tr><th colspan="7">${fechaActual.toLocaleString('es-ES', { month: 'long', year: 'numeric' })}</th></tr>`;
            calendario.querySelector('#calendario-body').innerHTML = html;
        }

        function notificar(mensaje) {
            if (Notification.permission === 'granted') {
                new Notification('Recordatorio', { body: mensaje });
            } else if (Notification.permission !== 'denied') {
                Notification.requestPermission().then(permission => {
                    if (permission === 'granted') {
                        new Notification('Recordatorio', { body: mensaje });
                    }
                });
            }
        }

        cambiarMes(0);
        mostrarTrabajos();
        mostrarLinks();

        document.addEventListener('DOMContentLoaded', () => {
            if (Notification.permission === 'default') {
                Notification.requestPermission();
            }
        });
    </script>
</body>
</html>
