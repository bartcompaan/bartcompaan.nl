[script.js](https://github.com/user-attachments/files/25695046/script.js)
// ===== SPLASH SCREEN =====
document.addEventListener('DOMContentLoaded', function() {
    // Hide splash screen after 2.5 seconds
    setTimeout(function() {
        const splashScreen = document.getElementById('splashScreen');
        splashScreen.classList.add('hidden');
    }, 2500);

    // Form handling
    handleQuoteForm();
    handleAppointmentForm();
    handleSmoothScroll();
});

// ===== QUOTE FORM HANDLING =====
function handleQuoteForm() {
    const form = document.getElementById('quoteForm');
    if (form) {
        form.addEventListener('submit', function(e) {
            e.preventDefault();
            
            const formData = {
                naam: document.getElementById('naam').value,
                email: document.getElementById('email').value,
                telefoon: document.getElementById('telefoon').value,
                datum: document.getElementById('datum').value,
                eventtype: document.getElementById('eventtype').value,
                bericht: document.getElementById('bericht').value
            };

            // Log data (in production: send to server)
            console.log('Offerte aanvraag:', formData);
            
            // Show success message
            showNotification('Bedankt! Je offerte aanvraag is ontvangen. Ik neem snel contact op.');
            form.reset();
        });
    }
}

// ===== APPOINTMENT FORM HANDLING =====
function handleAppointmentForm() {
    const form = document.getElementById('appointmentForm');
    if (form) {
        form.addEventListener('submit', function(e) {
            e.preventDefault();
            
            const formData = {
                naam: document.getElementById('naam2').value,
                email: document.getElementById('email2').value,
                telefoon: document.getElementById('telefoon2').value,
                datum: document.getElementById('datum2').value,
                opmerking: document.getElementById('opmerking').value
            };

            // Log data (in production: send to server)
            console.log('Afspraak aanvraag:', formData);
            
            // Show success message
            showNotification('Afspraak aangevraagd! Ik zal je snel een bevestiging sturen.');
            form.reset();
        });
    }
}

// ===== NOTIFICATION SYSTEM =====
function showNotification(message) {
    // Create notification element
    const notification = document.createElement('div');
    notification.className = 'notification success';
    notification.textContent = message;
    
    // Add styles if not in CSS
    notification.style.cssText = `
        position: fixed;
        top: 20px;
        right: 20px;
        background-color: #ff6b00;
        color: #0a0a0a;
        padding: 15px 25px;
        border-radius: 5px;
        font-weight: 600;
        z-index: 10000;
        animation: slideIn 0.3s ease;
        box-shadow: 0 4px 15px rgba(255, 107, 0, 0.4);
    `;
    
    document.body.appendChild(notification);
    
    // Remove after 5 seconds
    setTimeout(() => {
        notification.style.animation = 'slideOut 0.3s ease';
        setTimeout(() => {
            document.body.removeChild(notification);
        }, 300);
    }, 5000);
}

// ===== SMOOTH SCROLL HANDLING =====
function handleSmoothScroll() {
    // Already handled by HTML scroll-behavior: smooth
    // This function can be expanded for more complex scroll behaviors
}

// ===== ADD ANIMATIONS TO CSS =====
const style = document.createElement('style');
style.textContent = `
    @keyframes slideIn {
        from {
            transform: translateX(400px);
            opacity: 0;
        }
        to {
            transform: translateX(0);
            opacity: 1;
        }
    }

    @keyframes slideOut {
        from {
            transform: translateX(0);
            opacity: 1;
        }
        to {
            transform: translateX(400px);
            opacity: 0;
        }
    }
`;
docum[index.html](https://github.com/user-attachments/files/25695076/index.html)
ent.head.appendChild(style);
<!DOCTYPE html>
<html lang="nl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bart Compaan - DJ Portfolio</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <!-- Splash Screen met Loading Animation -->
    <div id="splashScreen" class="splash-screen">
        <div class="turntable-container">
            <svg class="turntable" viewBox="0 0 200 200">
                <!-- Buitenring -->
                <circle cx="100" cy="100" r="95" fill="#1a1a1a" stroke="#ff6b00" stroke-width="2"/>
                
                <!-- Plaat -->
                <circle cx="100" cy="100" r="85" fill="#0a0a0a" stroke="#333" stroke-width="1"/>
                
                <!-- Vinyl grooves -->
                <circle cx="100" cy="100" r="80" fill="none" stroke="#222" stroke-width="0.5" opacity="0.5"/>
                <circle cx="100" cy="100" r="70" fill="none" stroke="#222" stroke-width="0.5" opacity="0.5"/>
                <circle cx="100" cy="100" r="60" fill="none" stroke="#222" stroke-width="0.5" opacity="0.5"/>
                <circle cx="100" cy="100" r="50" fill="none" stroke="#222" stroke-width="0.5" opacity="0.5"/>
                
                <!-- Center label -->
                <circle cx="100" cy="100" r="25" fill="#ff6b00"/>
                <circle cx="100" cy="100" r="20" fill="#0a0a0a"/>
                <circle cx="100" cy="100" r="5" fill="#ff6b00"/>
            </svg>
        </div>
        <p class="loading-text">Laden...</p>
    </div>

    <!-- Main Navigation -->
    <nav class="navbar">
        <div class="nav-container">
            <div class="logo">
                <span class="logo-icon">🎧</span>
                <span class="logo-text">Bart Compaan</span>
            </div>
            <ul class="nav-links">
                <li><a href="#over">Wie ben ik</a></li>
                <li><a href="#fotos">Fotos</a></li>
                <li><a href="#offerte">Offerte aanvragen</a></li>
                <li><a href="#afspraak">Afspraak maken</a></li>
            </ul>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="hero">
        <div class="hero-content">
            <h1>Bart Compaan</h1>
            <p class="tagline">Professionele DJ voor je Eventje</p>
            <div class="cta-buttons">
                <a href="#offerte" class="btn btn-primary">Offerte aanvragen</a>
                <a href="#afspraak" class="btn btn-secondary">Afspraak maken</a>
            </div>
        </div>
        <div class="hero-bg-pattern"></div>
    </section>

    <!-- Wie ben ik Section -->
    <section id="over" class="section about">
        <div class="container">
            <h2>Wie ben ik</h2>
            <div class="about-content">
                <div class="about-text">
                    <p>Hallo, ik ben Bart Compaan, een passionele DJ met jaren ervaring in het creëren van onvergetelijke muzikale ervaringen. Of het nu gaat om bruiloften, feestjes, bedrijfsevents of club nights, ik zorg ervoor dat de muziek perfect aansluit bij jouw event.</p>
                    <p>Met mijn professionele uitrusting en uitgebreide muziekverzameling creëer ik een sfeer waar iedereen van geniet. Mijn specialiteiten zijn:</p>
                    <ul class="features-list">
                        <li>🎵 Bruiloften en Private Events</li>
                        <li>🎉 Verjaarsdagen en Feestjes</li>
                        <li>💼 Bedrijfsevents en Conferenties</li>
                        <li>🎪 Festivals en Club Nights</li>
                        <li>🎧 Professionele Geluidstechniek</li>
                    </ul>
                </div>
                <div class="about-image">
                    <div class="placeholder-image">
                        <span class="placeholder-icon">🎧</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Fotos Section -->
    <section id="fotos" class="section gallery">
        <div class="container">
            <h2>Fotos</h2>
            <p class="section-subtitle">Bekijk enkele impressies van recente events</p>
            <div class="gallery-grid">
                <div class="gallery-item">
                    <div class="gallery-placeholder">
                        <span class="placeholder-icon">📸</span>
                    </div>
                </div>
                <div class="gallery-item">
                    <div class="gallery-placeholder">
                        <span class="placeholder-icon">🎸</span>
                    </div>
                </div>
                <div class="gallery-item">
                    <div class="gallery-placeholder">
                        <span class="placeholder-icon">🎤</span>
                    </div>
                </div>
                <div class="gallery-item">
                    <div class="gallery-placeholder">
                        <span class="placeholder-icon">🎵</span>
                    </div>
                </div>
                <div class="gallery-item">
                    <div class="gallery-placeholder">
                        <span class="placeholder-icon">🎶</span>
                    </div>
                </div>
                <div class="gallery-item">
                    <div class="gallery-placeholder">
                        <span class="placeholder-icon">🎼</span>
                    </div>
                </div>
            </div>
            <p class="gallery-note">Foto's kunnen hier eenvoudig worden toegevoegd</p>
        </div>
    </section>

    <!-- Offerte Aanvragen Section -->
    <section id="offerte" class="section quote-request">
        <div class="container">
            <h2>Offerte aanvragen</h2>
            <p class="section-subtitle">Vul het formulier in en ik neem snel contact met je op</p>
            <form class="form" id="quoteForm">
                <div class="form-group">
                    <input type="text" id="naam" name="naam" placeholder="Je naam" required>
                </div>
                <div class="form-group">
                    <input type="email" id="email" name="email" placeholder="Je e-mailadres" required>
                </div>
                <div class="form-group">
                    <input type="tel" id="telefoon" name="telefoon" placeholder="Je telefoonnummer" required>
                </div>
                <div class="form-group">
                    <input type="date" id="datum" name="datum" required>
                </div>
                <div class="form-group">
                    <select id="eventtype" name="eventtype" required>
                        <option value="">Kies het type event...</option>
                        <option value="bruiloft">Bruiloft</option>
                        <option value="verjaardag">Verjaardag</option>
                        <option value="bedrijf">Bedrijfsevent</option>
                        <option value="festival">Festival</option>
                        <option value="anders">Anders</option>
                    </select>
                </div>
                <div class="form-group">
                    <textarea id="bericht" name="bericht" placeholder="Vertel meer over je event..." rows="5" required></textarea>
                </div>
                <button type="submit" class="btn btn-primary">Offerte aanvragen</button>
            </form>
        </div>
    </section>

    <!-- Afspraak Maken Section -->
    <section id="afspraak" class="section appointment">
        <div class="container">
            <h2>Afspraak maken</h2>
            <p class="section-subtitle">Reserveer een moment voor een persoonlijk gesprek</p>
            <form class="form" id="appointmentForm">
                <div class="form-group">
                    <input type="text" id="naam2" name="naam" placeholder="Je naam" required>
                </div>
                <div class="form-group">
                    <input type="email" id="email2" name="email" placeholder="Je e-mailadres" required>
                </div>
                <div class="form-group">
                    <input type="tel" id="telefoon2" name="telefoon" placeholder="Je telefoonnummer" required>
                </div>
                <div class="form-group">
                    <label for="datum2">Kies een moment:</label>
                    <input type="datetime-local" id="datum2" name="datum" required>
                </div>
                <div class="form-group">
                    <textarea id="opmerking" name="opmerking" placeholder="Opmerkingen of vragen?" rows="4"></textarea>
                </div>
                <button type="submit" class="btn btn-primary">Afspraak bevestigen</button>
            </form>
        </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
        <div class="footer-content">
            <div class="footer-section">
                <h3>Contact</h3>
                <p>Email: <a href="mailto:info@bartcompaan.nl">info@bartcompaan.nl</a></p>
                <p>Telefoon: <a href="tel:+31612345678">+31 (0)6 12345678</a></p>
            </div>
            <div class="footer-section">
                <h3>Volg mij</h3>
                <div class="social-links">
                    <a href="#" class="social-link">Facebook</a>
                    <a href="#" class="social-link">Instagram</a>
                    <a href="#" class="social-link">YouTube</a>
                </div>
            </div>
            <div class="footer-section">
                <h3>&copy; 2026 Bart Compaan</h3>
                <p>Alle rechten voorbehouden</p>
            </div>
        </div>
    </footer>

    <script src="script.js"></script>
</body>
</html>
[styles.css](https://github.com/user-attachments/files/25695095/styles.css)
/* Reset en Base Styles */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

:root {
    --primary-color: #ff6b00;
    --dark-bg: #0a0a0a;
    --dark-bg-2: #1a1a1a;
    --dark-bg-3: #2a2a2a;
    --text-light: #e0e0e0;
    --text-muted: #a0a0a0;
    --accent-color: #ff6b00;
    --transition: all 0.3s ease;
}

html {
    scroll-behavior: smooth;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: var(--dark-bg);
    color: var(--text-light);
    line-height: 1.6;
    overflow-x: hidden;
}

/* ===== SPLASH SCREEN ===== */
.splash-screen {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(135deg, var(--dark-bg) 0%, var(--dark-bg-2) 100%);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    z-index: 9999;
    opacity: 1;
    transition: opacity 0.5s ease 0.5s;
}

.splash-screen.hidden {
    opacity: 0;
    pointer-events: none;
}

.turntable-container {
    width: 150px;
    height: 150px;
    margin-bottom: 30px;
}

.turntable {
    width: 100%;
    height: 100%;
    animation: spin 3s linear infinite;
    filter: drop-shadow(0 0 20px rgba(255, 107, 0, 0.3));
}

@keyframes spin {
    from {
        transform: rotate(0deg);
    }
    to {
        transform: rotate(360deg);
    }
}

.loading-text {
    font-size: 18px;
    color: var(--accent-color);
    letter-spacing: 2px;
    animation: pulse 1.5s ease-in-out infinite;
}

@keyframes pulse {
    0%, 100% {
        opacity: 0.6;
    }
    50% {
        opacity: 1;
    }
}

/* ===== NAVIGATION ===== */
.navbar {
    background-color: var(--dark-bg-2);
    border-bottom: 2px solid var(--accent-color);
    position: sticky;
    top: 0;
    z-index: 1000;
    box-shadow: 0 2px 15px rgba(0, 0, 0, 0.5);
}

.nav-container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 1rem 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo {
    display: flex;
    align-items: center;
    gap: 10px;
    font-size: 24px;
    font-weight: bold;
    color: var(--accent-color);
}

.logo-icon {
    font-size: 28px;
}

.nav-links {
    display: flex;
    list-style: none;
    gap: 2rem;
}

.nav-links a {
    color: var(--text-light);
    text-decoration: none;
    transition: var(--transition);
    font-weight: 500;
    position: relative;
}

.nav-links a::after {
    content: '';
    position: absolute;
    bottom: -5px;
    left: 0;
    width: 0;
    height: 2px;
    background-color: var(--accent-color);
    transition: width 0.3s ease;
}

.nav-links a:hover {
    color: var(--accent-color);
}

.nav-links a:hover::after {
    width: 100%;
}

/* ===== HERO SECTION ===== */
.hero {
    position: relative;
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    background: linear-gradient(135deg, var(--dark-bg) 0%, var(--dark-bg-2) 50%, var(--dark-bg-3) 100%);
}

.hero::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: 
        radial-gradient(circle at 20% 50%, rgba(255, 107, 0, 0.1) 0%, transparent 50%),
        radial-gradient(circle at 80% 80%, rgba(255, 107, 0, 0.05) 0%, transparent 50%);
    pointer-events: none;
}

.hero-content {
    position: relative;
    z-index: 2;
    text-align: center;
    animation: fadeInUp 1s ease;
}

.hero h1 {
    font-size: clamp(3rem, 8vw, 5rem);
    margin-bottom: 1rem;
    color: var(--accent-color);
    text-shadow: 0 0 20px rgba(255, 107, 0, 0.3);
}

.tagline {
    font-size: 1.5rem;
    color: var(--text-light);
    margin-bottom: 2rem;
    text-shadow: 0 2px 10px rgba(0, 0, 0, 0.5);
}

.cta-buttons {
    display: flex;
    gap: 2rem;
    justify-content: center;
    flex-wrap: wrap;
}

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

/* ===== BUTTONS ===== */
.btn {
    padding: 12px 30px;
    border: none;
    border-radius: 5px;
    font-size: 1rem;
    font-weight: 600;
    cursor: pointer;
    transition: var(--transition);
    text-decoration: none;
    display: inline-block;
    text-align: center;
}

.btn-primary {
    background-color: var(--accent-color);
    color: var(--dark-bg);
    box-shadow: 0 4px 15px rgba(255, 107, 0, 0.3);
}

.btn-primary:hover {
    background-color: #ff8a2a;
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(255, 107, 0, 0.5);
}

.btn-secondary {
    background-color: transparent;
    color: var(--accent-color);
    border: 2px solid var(--accent-color);
}

.btn-secondary:hover {
    background-color: var(--accent-color);
    color: var(--dark-bg);
    transform: translateY(-2px);
}

/* ===== SECTIONS ===== */
.section {
    padding: 5rem 2rem;
    max-width: 1200px;
    margin: 0 auto;
}

.section h2 {
    font-size: clamp(2rem, 5vw, 3.5rem);
    margin-bottom: 1rem;
    color: var(--accent-color);
    text-align: center;
    position: relative;
    padding-bottom: 1rem;
}

.section h2::after {
    content: '';
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
    width: 100px;
    height: 3px;
    background-color: var(--accent-color);
}

.section-subtitle {
    text-align: center;
    color: var(--text-muted);
    margin-bottom: 3rem;
    font-size: 1.1rem;
}

.container {
    width: 100%;
}

/* ===== ABOUT SECTION ===== */
.about {
    background: linear-gradient(135deg, var(--dark-bg-2) 0%, var(--dark-bg) 100%);
}

.about-content {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    align-items: center;
    margin-top: 2rem;
}

.about-text p {
    margin-bottom: 1.5rem;
    color: var(--text-light);
    font-size: 1.05rem;
    line-height: 1.8;
}

.features-list {
    list-style: none;
    margin-top: 2rem;
}

.features-list li {
    padding: 0.8rem 0;
    padding-left: 2rem;
    position: relative;
    color: var(--text-light);
    font-size: 1rem;
}

.features-list li::before {
    content: '';
    position: absolute;
    left: 0;
    top: 50%;
    transform: translateY(-50%);
    width: 8px;
    height: 8px;
    background-color: var(--accent-color);
    border-radius: 50%;
}

.about-image {
    display: flex;
    justify-content: center;
}

.placeholder-image {
    width: 300px;
    height: 300px;
    background: linear-gradient(135deg, var(--dark-bg-3) 0%, var(--dark-bg-2) 100%);
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 80px;
    border: 2px solid var(--accent-color);
    box-shadow: 0 0 30px rgba(255, 107, 0, 0.2);
}

/* ===== GALLERY SECTION ===== */
.gallery {
    background: linear-gradient(135deg, var(--dark-bg) 0%, var(--dark-bg-2) 100%);
}

.gallery-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    margin: 3rem 0;
}

.gallery-item {
    overflow: hidden;
    border-radius: 10px;
    cursor: pointer;
}

.gallery-placeholder {
    width: 100%;
    aspect-ratio: 1;
    background: linear-gradient(135deg, var(--dark-bg-3) 0%, var(--dark-bg-2) 100%);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 60px;
    border: 2px solid var(--accent-color);
    transition: var(--transition);
    border-radius: 10px;
}

.gallery-item:hover .gallery-placeholder {
    transform: scale(1.05);
    box-shadow: 0 0 30px rgba(255, 107, 0, 0.3);
}

.gallery-note {
    text-align: center;
    color: var(--text-muted);
    font-style: italic;
    margin-top: 2rem;
}

/* ===== FORMS ===== */
.form {
    background-color: var(--dark-bg-2);
    padding: 3rem;
    border-radius: 10px;
    border: 1px solid var(--dark-bg-3);
    max-width: 700px;
    margin: 0 auto;
    box-shadow: 0 5px 20px rgba(0, 0, 0, 0.3);
}

.form-group {
    margin-bottom: 1.5rem;
    display: flex;
    flex-direction: column;
}

.form-group label {
    margin-bottom: 0.5rem;
    color: var(--text-light);
    font-weight: 500;
}

.form-group input,
.form-group select,
.form-group textarea {
    padding: 12px 15px;
    background-color: var(--dark-bg);
    color: var(--text-light);
    border: 1px solid var(--dark-bg-3);
    border-radius: 5px;
    font-size: 1rem;
    font-family: inherit;
    transition: var(--transition);
}

.form-group input:focus,
.form-group select:focus,
.form-group textarea:focus {
    outline: none;
    border-color: var(--accent-color);
    box-shadow: 0 0 10px rgba(255, 107, 0, 0.2);
}

.form-group textarea {
    resize: vertical;
}

.form button {
    width: 100%;
    margin-top: 1rem;
}

/* ===== QUOTE REQUEST SECTION ===== */
.quote-request {
    background: linear-gradient(135deg, var(--dark-bg-2) 0%, var(--dark-bg) 100%);
}

/* ===== APPOINTMENT SECTION ===== */
.appointment {
    background: linear-gradient(135deg, var(--dark-bg) 0%, var(--dark-bg-2) 100%);
}

/* ===== FOOTER ===== */
.footer {
    background-color: var(--dark-bg-2);
    border-top: 2px solid var(--accent-color);
    padding: 3rem 2rem;
    margin-top: 5rem;
}

.footer-content {
    max-width: 1200px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 2rem;
}

.footer-section h3 {
    color: var(--accent-color);
    margin-bottom: 1rem;
}

.footer-section p {
    color: var(--text-muted);
    margin-bottom: 0.5rem;
}

.footer-section a {
    color: var(--accent-color);
    text-decoration: none;
    transition: var(--transition);
}

.footer-section a:hover {
    text-decoration: underline;
}

.social-links {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
}

.social-link {
    width: fit-content;
}

/* ===== RESPONSIVE ===== */
@media (max-width: 768px) {
    .nav-links {
        gap: 1rem;
        font-size: 0.9rem;
    }

    .about-content {
        grid-template-columns: 1fr;
        gap: 2rem;
    }

    .placeholder-image {
        width: 250px;
        height: 250px;
        font-size: 60px;
    }

    .gallery-grid {
        grid-template-columns: 1fr;
    }

    .cta-buttons {
        flex-direction: column;
        gap: 1rem;
    }

    .form {
        padding: 2rem;
    }

    .section {
        padding: 3rem 1rem;
    }

    .footer-content {
        grid-template-columns: 1fr;
        text-align: center;
    }

    .tagline {
        font-size: 1.2rem;
    }
}

@media (max-width: 480px) {
    .hero h1 {
        font-size: 2.5rem;
    }

    .tagline {
        font-size: 1rem;
    }

    .nav-container {
        padding: 0.75rem 1rem;
    }

    .nav-links {
        gap: 0.75rem;
        font-size: 0.8rem;
    }

    .logo-text {
        display: none;
    }

    .section h2 {
        font-size: 1.8rem;
    }
}
