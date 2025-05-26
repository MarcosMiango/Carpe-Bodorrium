# Carpe-Bodorrium
Página Web de nuestra boda
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nuestra Boda - [Nombres]</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Georgia', serif;
            line-height: 1.6;
            color: #333;
            background: linear-gradient(135deg, #ffeef7 0%, #fff5f5 100%);
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header */
        .header {
            background: linear-gradient(rgba(0,0,0,0.3), rgba(0,0,0,0.3)), 
                        url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 600"><rect width="1200" height="600" fill="%23f8c8dc"/><circle cx="200" cy="150" r="80" fill="%23ffffff" opacity="0.1"/><circle cx="800" cy="400" r="120" fill="%23ffffff" opacity="0.1"/><circle cx="1000" cy="200" r="60" fill="%23ffffff" opacity="0.1"/></svg>');
            background-size: cover;
            background-position: center;
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            color: white;
            position: relative;
        }

        .header::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, rgba(219, 112, 147, 0.7), rgba(255, 182, 193, 0.7));
        }

        .header-content {
            position: relative;
            z-index: 2;
        }

        .header h1 {
            font-size: 4rem;
            margin-bottom: 1rem;
            font-weight: 300;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
            animation: fadeInUp 1s ease-out;
        }

        .header .date {
            font-size: 1.5rem;
            margin-bottom: 2rem;
            opacity: 0.9;
            animation: fadeInUp 1s ease-out 0.5s both;
        }

        .scroll-indicator {
            position: absolute;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%);
            animation: bounce 2s infinite;
        }

        .scroll-indicator::after {
            content: '↓';
            font-size: 2rem;
            color: white;
        }

        /* Navigation */
        .nav {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            position: sticky;
            top: 0;
            z-index: 100;
            padding: 1rem 0;
            box-shadow: 0 2px 20px rgba(0,0,0,0.1);
        }

        .nav ul {
            list-style: none;
            display: flex;
            justify-content: center;
            gap: 2rem;
        }

        .nav a {
            text-decoration: none;
            color: #333;
            font-weight: 500;
            padding: 0.5rem 1rem;
            border-radius: 25px;
            transition: all 0.3s ease;
        }

        .nav a:hover {
            background: linear-gradient(45deg, #db7093, #ffb6c1);
            color: white;
            transform: translateY(-2px);
        }

        /* Sections */
        .section {
            padding: 4rem 0;
            margin: 2rem 0;
        }

        .section-title {
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 3rem;
            color: #db7093;
            position: relative;
        }

        .section-title::after {
            content: '';
            display: block;
            width: 80px;
            height: 3px;
            background: linear-gradient(45deg, #db7093, #ffb6c1);
            margin: 1rem auto;
            border-radius: 2px;
        }

        /* About Section */
        .about {
            background: white;
            border-radius: 20px;
            padding: 3rem;
            margin: 2rem 0;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }

        .couple-info {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 3rem;
            margin-top: 2rem;
        }

        .bride, .groom {
            text-align: center;
            padding: 2rem;
            background: linear-gradient(135deg, #ffeef7, #fff5f5);
            border-radius: 15px;
            transition: transform 0.3s ease;
        }

        .bride:hover, .groom:hover {
            transform: translateY(-5px);
        }

        .couple-photo {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            background: linear-gradient(45deg, #db7093, #ffb6c1);
            margin: 0 auto 1rem;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            color: white;
        }

        /* Event Details */
        .event-details {
            background: white;
            border-radius: 20px;
            padding: 3rem;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }

        .event-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .event-card {
            background: linear-gradient(135deg, #ffeef7, #fff5f5);
            padding: 2rem;
            border-radius: 15px;
            text-align: center;
            transition: transform 0.3s ease;
        }

        .event-card:hover {
            transform: translateY(-5px);
        }

        .event-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
        }

        /* RSVP Form */
        .rsvp {
            background: white;
            border-radius: 20px;
            padding: 3rem;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 500;
            color: #333;
        }

        .form-group input,
        .form-group select,
        .form-group textarea {
            width: 100%;
            padding: 1rem;
            border: 2px solid #f0f0f0;
            border-radius: 10px;
            font-size: 1rem;
            transition: border-color 0.3s ease;
        }

        .form-group input:focus,
        .form-group select:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: #db7093;
        }

        .form-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1rem;
        }

        .btn {
            background: linear-gradient(45deg, #db7093, #ffb6c1);
            color: white;
            padding: 1rem 2rem;
            border: none;
            border-radius: 25px;
            font-size: 1.1rem;
            cursor: pointer;
            transition: all 0.3s ease;
            display: inline-block;
            text-decoration: none;
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(219, 112, 147, 0.4);
        }

        /* Photo Gallery */
        .photo-gallery {
            background: white;
            border-radius: 20px;
            padding: 3rem;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }

        .upload-area {
            border: 3px dashed #db7093;
            border-radius: 15px;
            padding: 3rem;
            text-align: center;
            margin-bottom: 2rem;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .upload-area:hover {
            background: #ffeef7;
            border-color: #ffb6c1;
        }

        .upload-area.dragover {
            background: #ffeef7;
            transform: scale(1.02);
        }

        .photo-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 1rem;
            margin-top: 2rem;
        }

        .photo-item {
            aspect-ratio: 1;
            background: #f0f0f0;
            border-radius: 10px;
            overflow: hidden;
            position: relative;
            transition: transform 0.3s ease;
        }

        .photo-item:hover {
            transform: scale(1.05);
        }

        .photo-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        /* Footer */
        .footer {
            background: linear-gradient(45deg, #db7093, #ffb6c1);
            color: white;
            text-align: center;
            padding: 3rem 0;
            margin-top: 4rem;
        }

        .footer h3 {
            margin-bottom: 1rem;
            font-size: 2rem;
        }

        .countdown {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin: 2rem 0;
        }

        .countdown-item {
            text-align: center;
            background: rgba(255,255,255,0.2);
            padding: 1rem;
            border-radius: 10px;
        }

        .countdown-number {
            font-size: 2rem;
            font-weight: bold;
            display: block;
        }

        /* Animations */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {
                transform: translateX(-50%) translateY(0);
            }
            40% {
                transform: translateX(-50%) translateY(-10px);
            }
            60% {
                transform: translateX(-50%) translateY(-5px);
            }
        }

        /* Responsive */
        @media (max-width: 768px) {
            .header h1 {
                font-size: 2.5rem;
            }
            
            .nav ul {
                flex-wrap: wrap;
                gap: 1rem;
            }
            
            .couple-info {
                grid-template-columns: 1fr;
            }
            
            .form-row {
                grid-template-columns: 1fr;
            }
            
            .countdown {
                flex-wrap: wrap;
                gap: 1rem;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header class="header">
        <div class="header-content">
            <h1>María & Carlos</h1>
            <p class="date">15 de Junio, 2024</p>
            <p>¡Nos casamos y queremos celebrarlo contigo!</p>
        </div>
        <div class="scroll-indicator"></div>
    </header>

    <!-- Navigation -->
    <nav class="nav">
        <ul>
            <li><a href="#inicio">Inicio</a></li>
            <li><a href="#nosotros">Nosotros</a></li>
            <li><a href="#evento">El Evento</a></li>
            <li><a href="#confirmacion">Confirmación</a></li>
            <li><a href="#fotos">Fotos</a></li>
        </ul>
    </nav>

    <div class="container">
        <!-- About Section -->
        <section id="nosotros" class="section">
            <div class="about">
                <h2 class="section-title">Nuestra Historia</h2>
                <p style="text-align: center; font-size: 1.2rem; margin-bottom: 2rem; color: #666;">
                    Después de 5 años juntos, hemos decidido dar el gran paso. Queremos compartir este momento especial 
                    con las personas más importantes de nuestras vidas.
                </p>
                
                <div class="couple-info">
                    <div class="bride">
                        <div class="couple-photo">👰</div>
                        <h3>María</h3>
                        <p>Profesora de arte, amante de los libros y los gatos. Su sonrisa ilumina cualquier habitación y su corazón es tan grande como su amor por la repostería.</p>
                    </div>
                    <div class="groom">
                        <div class="couple-photo">🤵</div>
                        <h3>Carlos</h3>
                        <p>Ingeniero de software, músico aficionado y chef de fin de semana. Su humor y paciencia infinita lo convierten en el compañero perfecto para cualquier aventura.</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Event Details -->
        <section id="evento" class="section">
            <div class="event-details">
                <h2 class="section-title">Detalles del Evento</h2>
                
                <div class="event-grid">
                    <div class="event-card">
                        <div class="event-icon">⛪</div>
                        <h3>Ceremonia</h3>
                        <p><strong>Hora:</strong> 17:00</p>
                        <p><strong>Lugar:</strong> Iglesia de San Miguel</p>
                        <p><strong>Dirección:</strong> Calle Principal 123, Centro</p>
                    </div>
                    
                    <div class="event-card">
                        <div class="event-icon">🎉</div>
                        <h3>Recepción</h3>
                        <p><strong>Hora:</strong> 19:00</p>
                        <p><strong>Lugar:</strong> Salón de Eventos "El Jardín"</p>
                        <p><strong>Dirección:</strong> Av. de las Flores 456</p>
                    </div>
                    
                    <div class="event-card">
                        <div class="event-icon">🍽️</div>
                        <h3>Banquete</h3>
                        <p><strong>Hora:</strong> 20:30</p>
                        <p><strong>Menú:</strong> Cena de tres tiempos</p>
                        <p><strong>Incluye:</strong> Barra libre y pastel</p>
                    </div>
                    
                    <div class="event-card">
                        <div class="event-icon">💃</div>
                        <h3>Fiesta</h3>
                        <p><strong>Hora:</strong> 22:00 - 03:00</p>
                        <p><strong>Música:</strong> DJ + Banda en vivo</p>
                        <p><strong>Dress Code:</strong> Formal/Elegante</p>
                    </div>
                </div>
                
                <div style="margin-top: 3rem; text-align: center; padding: 2rem; background: #ffeef7; border-radius: 15px;">
                    <h3 style="color: #db7093; margin-bottom: 1rem;">Información Importante</h3>
                    <p>• La ceremonia será al aire libre, recomendamos traer una chaqueta ligera</p>
                    <p>• Habrá servicio de guardería para los niños durante la recepción</p>
                    <p>• El lugar cuenta con estacionamiento gratuito</p>
                    <p>• Por favor, confirma tu asistencia antes del 1 de junio</p>
                </div>
            </div>
        </section>

        <!-- RSVP Section -->
        <section id="confirmacion" class="section">
            <div class="rsvp">
                <h2 class="section-title">Confirma tu Asistencia</h2>
                
                <form id="rsvpForm">
                    <div class="form-row">
                        <div class="form-group">
                            <label for="nombre">Nombre Completo *</label>
                            <input type="text" id="nombre" name="nombre" required>
                        </div>
                        <div class="form-group">
                            <label for="email">Email *</label>
                            <input type="email" id="email" name="email" required>
                        </div>
                    </div>
                    
                    <div class="form-row">
                        <div class="form-group">
                            <label for="telefono">Teléfono</label>
                            <input type="tel" id="telefono" name="telefono">
                        </div>
                        <div class="form-group">
                            <label for="acompanantes">Número de Acompañantes</label>
                            <select id="acompanantes" name="acompanantes">
                                <option value="0">Solo yo</option>
                                <option value="1">1 acompañante</option>
                                <option value="2">2 acompañantes</option>
                                <option value="3">3 acompañantes</option>
                                <option value="4">4+ acompañantes</option>
                            </select>
                        </div>
                    </div>
                    
                    <div class="form-group">
                        <label for="nombres_acompanantes">Nombres de Acompañantes</label>
                        <input type="text" id="nombres_acompanantes" name="nombres_acompanantes" placeholder="Nombres completos separados por comas">
                    </div>
                    
                    <div class="form-group">
                        <label for="restricciones">Restricciones Alimentarias</label>
                        <textarea id="restricciones" name="restricciones" rows="3" placeholder="Por favor especifica cualquier alergia o restricción alimentaria..."></textarea>
                    </div>
                    
                    <div class="form-group">
                        <label for="mensaje">Mensaje para los Novios</label>
                        <textarea id="mensaje" name="mensaje" rows="4" placeholder="Déjanos un mensaje especial..."></textarea>
                    </div>
                    
                    <div style="text-align: center; margin-top: 2rem;">
                        <button type="submit" class="btn">Confirmar Asistencia</button>
                    </div>
                </form>
                
                <div id="confirmationMessage" style="display: none; text-align: center; margin-top: 2rem; padding: 1rem; background: #d4edda; border-radius: 10px; color: #155724;">
                    ¡Gracias por confirmar tu asistencia! Nos emociona celebrar contigo.
                </div>
            </div>
        </section>

        <!-- Photo Gallery -->
        <section id="fotos" class="section">
            <div class="photo-gallery">
                <h2 class="section-title">Galería de Fotos</h2>
                <p style="text-align: center; margin-bottom: 2rem; color: #666;">
                    ¡Comparte tus fotos del gran día! Sube las mejores imágenes de la celebración.
                </p>
                
                <div class="upload-area" id="uploadArea">
                    <div style="font-size: 3rem; margin-bottom: 1rem;">📸</div>
                    <h3>Arrastra tus fotos aquí o haz clic para seleccionar</h3>
                    <p style="margin-top: 1rem; color: #666;">Formatos aceptados: JPG, PNG, GIF (máx. 5MB por foto)</p>
                    <input type="file" id="photoUpload" multiple accept="image/*" style="display: none;">
                </div>
                
                <div class="photo-grid" id="photoGrid">
                    <!-- Las fotos aparecerán aquí -->
                </div>
            </div>
        </section>
    </div>

    <!-- Footer -->
    <footer class="footer">
        <div class="container">
            <h3>¡Faltan muy pocos días!</h3>
            <div class="countdown" id="countdown">
                <div class="countdown-item">
                    <span class="countdown-number" id="days">00</span>
                    <span>Días</span>
                </div>
                <div class="countdown-item">
                    <span class="countdown-number" id="hours">00</span>
                    <span>Horas</span>
                </div>
                <div class="countdown-item">
                    <span class="countdown-number" id="minutes">00</span>
                    <span>Minutos</span>
                </div>
                <div class="countdown-item">
                    <span class="countdown-number" id="seconds">00</span>
                    <span>Segundos</span>
                </div>
            </div>
            <p style="margin-top: 2rem;">Con amor, María & Carlos ❤️</p>
        </div>
    </footer>

    <script>
        // Datos de confirmaciones (simulando base de datos)
        let confirmaciones = [];

        // Smooth scrolling para navegación
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // Formulario RSVP
        document.getElementById('rsvpForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const formData = new FormData(this);
            const data = {};
            for (let [key, value] of formData.entries()) {
                data[key] = value;
            }
            
            // Agregar timestamp
            data.fecha_confirmacion = new Date().toISOString();
            
            // Simular guardado (aquí conectarías con tu backend/Excel)
            confirmaciones.push(data);
            
            // Mostrar mensaje de confirmación
            document.getElementById('confirmationMessage').style.display = 'block';
            this.style.display = 'none';
            
            // Log para desarrollo (puedes ver los datos en la consola del navegador)
            console.log('Nueva confirmación:', data);
            console.log('Todas las confirmaciones:', confirmaciones);
        });

        // Upload de fotos
        const uploadArea = document.getElementById('uploadArea');
        const photoUpload = document.getElementById('photoUpload');
        const photoGrid = document.getElementById('photoGrid');
        let uploadedPhotos = [];

        uploadArea.addEventListener('click', () => photoUpload.click());

        uploadArea.addEventListener('dragover', (e) => {
            e.preventDefault();
            uploadArea.classList.add('dragover');
        });

        uploadArea.addEventListener('dragleave', () => {
            uploadArea.classList.remove('dragover');
        });

        uploadArea.addEventListener('drop', (e) => {
            e.preventDefault();
            uploadArea.classList.remove('dragover');
            handleFiles(e.dataTransfer.files);
        });

        photoUpload.addEventListener('change', (e) => {
            handleFiles(e.target.files);
        });

        function handleFiles(files) {
            Array.from(files).forEach(file => {
                if (file.type.startsWith('image/') && file.size <= 5 * 1024 * 1024) {
                    const reader = new FileReader();
                    reader.onload = (e) => {
                        const photoData = {
                            id: Date.now() + Math.random(),
                            src: e.target.result,
                            name: file.name,
                            uploadedAt: new Date().toISOString()
                        };
                        uploadedPhotos.push(photoData);
                        displayPhoto(photoData);
                    };
                    reader.readAsDataURL(file);
                }
            });
        }

        function displayPhoto(photoData) {
            const photoItem = document.createElement('div');
            photoItem.className = 'photo-item';
            photoItem.innerHTML = `<img src="${photoData.src}" alt="${photoData.name}">`;
            photoGrid.appendChild(photoItem);
        }

        // Countdown timer
        function updateCountdown() {
            const weddingDate = new Date('2024-06-15T17:00:00');
            const now = new Date();
            const difference = weddingDate.getTime() - now.getTime();

            if (difference > 0) {
                const days = Math.floor(difference / (1000 * 60 * 60 * 24));
                const hours = Math.floor((difference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                const minutes = Math.floor((difference % (1000 * 60 * 60)) / (1000 * 60));
                const seconds = Math.floor((difference % (1000 * 60)) / 1000);

                document.getElementById('days').textContent = days.toString().padStart(2, '0');
                document.getElementById('hours').textContent = hours.toString().padStart(2, '0');
                document.getElementById('minutes').textContent = minutes.toString().padStart(2, '0');
                document.getElementById('seconds').textContent = seconds.toString().padStart(2, '0');
            } else {
                document.getElementById('countdown').innerHTML = '<h2>¡Es hoy! ❤️</h2>';
            }
        }

        // Actualizar countdown cada segundo
        setInterval(updateCountdown, 1000);
        updateCountdown();

        // Función para exportar confirmaciones (para desarrollo)
        function exportarConfirmaciones() {
            const dataStr = JSON.stringify(confirmaciones, null, 2);
            const dataBlob = new Blob([dataStr], {type: 'application/json'});
            const url = URL.createObjectURL(dataBlob);
            const link = document.createElement('a');
            link.href = url;
            link.download = 'confirmaciones_boda.json';
            link.click();
        }

        // Hacer la función disponible globalmente para testing
        window.exportarConfirmaciones = exportarConfirmaciones;
    </script>
</body>
</html>
