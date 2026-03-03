<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Amor Flotante</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background: radial-gradient(circle at center, #ff7e5f, #feb47b); /* Fondo más cálido y radial */
            height: 100vh;
            font-family: 'Arial', sans-serif;
        }

        .element {
            position: absolute;
            font-size: clamp(12px, 2vw, 18px);
            text-shadow: 0 0 8px rgba(0,0,0,0.2);
            animation: float 8s linear infinite;
            opacity: 0;
            white-space: nowrap;
        }

        /* Tipos de elementos con más colores */
        .love-text { color: #ffffff; }
        .heart { color: #ff4757; content: "♥"; }
        .star { color: #ffd700; content: "★"; }
        .sparkle { color: #1dd1a1; }
        .warm-text { color: #ffeaa7; }

        /* Animación con movimiento aleatorio y profundidad */
        @keyframes float {
            0% { 
                transform: translate(0, 0) scale(0.8); 
                opacity: 0; 
            }
            15% { opacity: 1; }
            85% { opacity: 1; }
            100% { 
                transform: translate(calc(-50px + var(--x-offset)), -300px) scale(1.2); 
                opacity: 0; 
            }
        }

        /* Círculo central opcional como en la imagen original */
        .center-circle {
            position: absolute;
            width: 80px;
            height: 80px;
            border-radius: 50%;
            background: rgba(0,0,0,0.3);
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            font-size: 16px;
            text-align: center;
        }
    </style>
</head>
<body>
    <div class="center-circle">Amor<br>Infinito</div>
    <script>
        const elementTypes = [
            { text: "Amor Eterno", class: "love-text" },
            { text: "Corazón", class: "heart" },
            { text: "Estrella", class: "star" },
            { text: "Felicidad", class: "warm-text" },
            { text: "Brillo", class: "sparkle" },
            { text: "Te Adoro", class: "love-text" },
            { text: "Mi Vida", class: "warm-text" },
            { text: "Siempre", class: "love-text" },
            { text: "Cariño", class: "heart" },
            { text: "Unión", class: "warm-text" },
            { text: "Paz", class: "sparkle" },
            { text: "Ilusión", class: "love-text" },
            { text: "Eres mi Sol", class: "warm-text" },
            { text: "Mi Sueño", class: "love-text" },
            { text: "Para Siempre", class: "warm-text" },
            { text: "♥", class: "heart" },
            { text: "★", class: "star" },
            { text: "Esperanza", class: "sparkle" },
            { text: "Amanecer", class: "warm-text" },
            { text: "Mi Universo", class: "love-text" }
        ];

        function createFloatingElement() {
            const elemData = elementTypes[Math.floor(Math.random() * elementTypes.length)];
            const elem = document.createElement('div');
            elem.className = `element ${elemData.class}`;
            elem.textContent = elemData.text;
            
            // Posición inicial aleatoria
            elem.style.left = `${Math.random() * 100}%`;
            elem.style.top = `${Math.random() * 100}%`;
            
            // Desplazamiento horizontal aleatorio
            elem.style.setProperty('--x-offset', `${Math.random() * 100 - 50}px`);
            
            // Retraso y duración variables para mayor naturalidad
            elem.style.animationDelay = `${-Math.random() * 8}s`;
            elem.style.animationDuration = `${6 + Math.random() * 6}s`;

            document.body.appendChild(elem);

            // Eliminar elemento al finalizar la animación
            elem.addEventListener('animationend', () => elem.remove());
        }

        // Crear elementos cada poco tiempo
        setInterval(createFloatingElement, 200);
    </script>
</body>
</html>
