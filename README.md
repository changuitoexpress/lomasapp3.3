<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Changuito Express - Delivery Rápido en Lomas y La Vista</title>

    <link rel="manifest" href="/manifest.json">

    <script src="https://cdn.tailwindcss.com"></script>

    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" integrity="sha512-9usAa10IRO0HhonpyAIVpjrylPvoDwiPUiKdWk5t3PyolY1cOd4DSE0Ga+ri4AuTroPR5aQvXU9xC6qOPnzFeg==" crossorigin="anonymous" referrerpolicy="no-referrer" />

    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">

    <link rel="stylesheet" href="css/style.css">

    <link rel="apple-touch-icon" href="/img/icons/icon-192x192.png">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black">
    <meta name="apple-mobile-web-app-title" content="Changuito App">
    <meta name="theme-color" content="#1a202c"> </head>
<body>

    <div id="loading-overlay" class="loading-overlay hidden">
        <div class="spinner"></div>
        <p>Cargando...</p>
    </div>

    <button id="theme-toggle" class="theme-toggle">
        <i class="fas fa-sun"></i> </button>

    <div class="container mx-auto px-4 py-8">

        <header class="landing-header">
             <div class="header-content">
                 <h1>Changuito Express</h1>
                 <p>
                     ¡Tus antojos y todo lo que necesites! 🚀 Pide fácil y rápido de tus locales favoritos en
                     <span class="font-semibold text-neon-yellow">Lomas de Angelópolis y La Vista</span>.
                     Explora, ordena y disfruta sin salir de casa.
                     <br>
                     <span class="text-sm block mt-2 opacity-80">Horario: Lunes a Domingo de 9:00 AM a 11:00 PM</span>
                 </p>
                 <div class="search-input-container">
                     <input type="text" id="search-input" placeholder="Busca restaurantes, tiendas, platillos...">
                 </div>
             </div>
        </header>

        <section id="recommended-section" class="horizontal-section">
             <h2>Nuestras Recomendaciones <i class="fas fa-star text-neon-yellow text-xl ml-1"></i></h2>
             <div id="recommendations-container" class="horizontal-container">
                 <p class="text-gray-400 italic p-4">Cargando...</p>
             </div>
        </section>

         <section id="same-cost-section" class="horizontal-section">
              <h2>CONTENEDOR (Todo por el Mismo Costo de Envío) <i class="fas fa-shipping-fast text-neon-purple text-xl ml-1"></i></h2>
              <div id="same-cost-container" class="horizontal-container">
                   <p class="text-gray-400 italic p-4">Cargando...</p>
              </div>
         </section>


        <div id="business-directory">
            </div>

        <section id="custom-order-section">
            <h2>¿No encuentras lo que buscas?</h2>
             <p>Pide lo que quieras de cualquier tienda o restaurante y nosotros te lo llevamos.</p>
            <div class="space-y-4">
                <input type="text" id="custom-business-name" class="custom-order-input" placeholder="Nombre del Negocio / Lugar">
                <textarea id="custom-order-details" class="custom-order-input" rows="4" placeholder="Describe tu pedido detallado..."></textarea>
                <input type="text" id="custom-delivery-address" class="custom-order-input" placeholder="Tu dirección de entrega completa">
                <button id="send-custom-order-btn">
                    <i class="fab fa-whatsapp"></i> Enviar Pedido Personalizado
                </button>
            </div>
        </section>

        <div class="social-media-links">
            <a href="https://www.facebook.com/share/16BujSyXXt/" target="_blank" class="facebook" aria-label="Facebook"><i class="fab fa-facebook-f"></i></a>
            <a href="https://www.instagram.com/changuitos_express?igsh=aHJscnNtZTJ4and2" target="_blank" class="instagram" aria-label="Instagram"><i class="fab fa-instagram"></i></a>
            <a href="https://tiktok.com/@changuito_express" target="_blank" class="tiktok" aria-label="TikTok"><i class="fab fa-tiktok"></i></a>
        </div>


    </div> <div id="menu-modal" class="modal">
        <div class="modal-content">
            <span class="close-button" onclick="closeModal()">&times;</span>
            <h2 id="modal-business-name" class="text-3xl font-semibold mb-4 text-center"></h2>
            <div id="modal-menu-content" class="mb-4">
                </div>
            <div id="modal-direct-order" class="modal-section hidden">
                 <h3>Productos Disponibles</h3>
                 <ul id="product-list">
                    </ul>
            </div>
            <div id="modal-manual-order" class="modal-section hidden">
                 <h3>Realiza tu pedido aquí:</h3>
                 <p class="text-gray-400 text-sm mb-2">Describe detalladamente lo que deseas pedir de este negocio.</p>
                 <textarea id="manual-order-text" placeholder="Escribe los detalles..."></textarea>
                 <button class="add-manual-order-btn">
                     <i class="fas fa-cart-plus"></i> Añadir Pedido Manual al Carrito
                 </button>
                 <p class="manual-order-note text-sm text-gray-400 mt-2 italic">El total de pedidos manuales se confirmará directamente con el negocio o repartidor.</p>
            </div>
        </div>
    </div>

    <div id="cart-icon-container" class="cart-icon-container">
        <i id="cart-icon" class="fas fa-shopping-cart"></i>
        <span id="cart-count" class="hidden">0</span>
    </div>

    <div id="cart-details">
        <h3><i class="fas fa-cart-arrow-down"></i>Tu Carrito</h3>
        <ul id="cart-items">
            </ul>
        <p id="empty-cart-message">El carrito está vacío.</p>
        <div id="cart-summary" class="hidden"> <p class="text-right text-lg font-bold mt-2">Subtotal (Productos Directos): $<span id="cart-subtotal">0.00</span></p>
             <p id="manual-order-summary-note" class="text-right text-sm text-gray-400 mt-1 italic hidden">El total de pedidos manuales se confirmará con el negocio/repartidor.</p>
        </div>
        <div id="cart-actions" class="space-y-3 hidden"> <label for="cart-delivery-address" class="block text-sm font-medium text-gray-300 mb-1">Dirección de Entrega:</label>
             <input type="text" id="cart-delivery-address" name="cart-delivery-address" placeholder="Escribe tu dirección completa aquí..." class="w-full">
             <button id="whatsapp-order-button" class="cart-action-button whatsapp-btn">
                 <i class="fab fa-whatsapp"></i> Enviar Pedido por WhatsApp
             </button>
        </div>
    </div>

    <div id="toast-container"></div>

    <script src="js/main.js" defer></script>

</body>
</html>

