<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JL Store | Relojes Exclusivos</title>
    <meta name="description" content="JL Store, tu destino para relojes de lujo. Estilo minimalista y moderno.">
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;700&display=swap" rel="stylesheet">
    
    <style>
        /* --- Variables y Reseteo Minimalista --- */
        :root {
            --bg-color: #f7f7f7;
            --text-color: #1a1a1a;
            --accent-color: #000000;
            --border-color: #dddddd;
            --shadow-light: 0 4px 12px rgba(0, 0, 0, 0.05);
            font-family: 'Roboto', sans-serif;
        }
        
        * { box-sizing: border-box; margin: 0; padding: 0; }
        
        body {
            background-color: var(--bg-color);
            color: var(--text-color);
            line-height: 1.6;
            padding-top: 60px; /* Espacio para el header fijo */
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* --- Header Minimalista y Fijo --- */
        header {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            background: rgba(255, 255, 255, 0.95);
            border-bottom: 1px solid var(--border-color);
            z-index: 1000;
            backdrop-filter: blur(5px);
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px 20px;
        }

        .logo {
            font-size: 24px;
            font-weight: 700;
            text-decoration: none;
            color: var(--accent-color);
            letter-spacing: 1px;
        }

        nav a {
            margin-left: 20px;
            text-decoration: none;
            color: var(--text-color);
            font-weight: 400;
            transition: color 0.3s;
        }

        nav a:hover {
            color: var(--accent-color);
        }

        .cart-btn {
            background: none;
            border: none;
            cursor: pointer;
            font-size: 16px;
            font-weight: 700;
            color: var(--text-color);
            padding: 5px 10px;
        }

        /* --- Hero Section --- */
        .hero {
            text-align: center;
            padding: 80px 0 60px;
        }

        .hero h1 {
            font-size: 48px;
            font-weight: 300;
            margin-bottom: 10px;
        }

        .hero p {
            color: #666;
            margin-bottom: 30px;
        }

        .btn {
            display: inline-block;
            background-color: var(--accent-color);
            color: #fff;
            padding: 12px 30px;
            text-decoration: none;
            font-weight: 700;
            border-radius: 3px;
            transition: opacity 0.3s;
        }

        .btn:hover {
            opacity: 0.9;
        }

        /* --- Product Grid --- */
        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 30px;
            padding-bottom: 50px;
        }

        .product-card {
            background-color: #fff;
            border: 1px solid var(--border-color);
            border-radius: 5px;
            padding: 20px;
            text-align: center;
            display: flex;
            flex-direction: column;
            transition: box-shadow 0.3s;
        }

        .product-card:hover {
            box-shadow: var(--shadow-light);
        }

        .product-image {
            width: 100%;
            height: 200px;
            object-fit: contain;
            margin-bottom: 15px;
            border-bottom: 1px solid #f0f0f0;
        }

        .product-title {
            font-size: 16px;
            font-weight: 700;
            margin-bottom: 5px;
            flex-grow: 1; /* Para que todos tengan el mismo tamaño */
        }

        .product-ref {
            font-size: 13px;
            color: #999;
            margin-bottom: 15px;
        }

        .product-price-info {
            font-weight: 700;
            color: #c0c0c0;
            margin-bottom: 15px;
        }

        .actions {
            display: flex;
            gap: 10px;
            margin-top: auto;
        }

        .actions button {
            flex: 1;
            padding: 8px;
            border: 1px solid var(--accent-color);
            background: var(--accent-color);
            color: #fff;
            border-radius: 3px;
            cursor: pointer;
            font-weight: 400;
            transition: background 0.3s;
        }

        .actions .view-btn {
            background: #fff;
            color: var(--accent-color);
        }

        .actions button:hover {
            opacity: 0.8;
        }

        /* --- Secciones Adicionales --- */
        section {
            padding: 40px 0;
            border-top: 1px solid var(--border-color);
        }

        section h2 {
            font-weight: 300;
            font-size: 32px;
            margin-bottom: 20px;
            text-align: center;
        }

        #contacto p {
            text-align: center;
            color: #666;
        }

        /* --- Footer --- */
        footer {
            text-align: center;
            padding: 20px 0;
            font-size: 12px;
            color: #999;
        }

        /* --- Cart Drawer y Modal (Para evitar duplicar código) --- */
        .drawer, .modal {
            position: fixed;
            transition: transform 0.3s ease-in-out, opacity 0.3s ease-in-out;
            z-index: 2000;
        }
        /* Ocultar Drawer */
        .drawer {
            top: 0;
            right: 0;
            width: 350px;
            height: 100%;
            background: #fff;
            box-shadow: -4px 0 15px rgba(0, 0, 0, 0.1);
            transform: translateX(100%);
        }
        .drawer.open {
            transform: translateX(0);
        }

        .drawer-header {
            padding: 15px 20px;
            border-bottom: 1px solid var(--border-color);
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-weight: 700;
        }

        .drawer-close {
            background: none;
            border: none;
            cursor: pointer;
            font-size: 20px;
        }

        .drawer-body {
            max-height: calc(100% - 130px);
            overflow-y: auto;
            padding: 20px;
        }

        .cart-item {
            display: flex;
            gap: 15px;
            margin-bottom: 15px;
            align-items: center;
        }

        .cart-item img {
            width: 60px;
            height: 60px;
            object-fit: contain;
            border: 1px solid var(--border-color);
            border-radius: 3px;
        }

        .item-details { flex-grow: 1; }
        .item-details strong { display: block; font-size: 14px; }
        .item-details span { font-size: 12px; color: #666; }

        .item-controls button {
            background: #eee;
            border: 1px solid #ddd;
            padding: 3px 8px;
            cursor: pointer;
            border-radius: 3px;
            margin-left: 5px;
        }
        .item-controls .remove-btn { color: #ff3333; border: none; background: none; font-size: 12px; }

        .drawer-footer {
            padding: 15px 20px;
            border-top: 1px solid var(--border-color);
            text-align: center;
        }

        .whatsapp-btn {
            display: block;
            background: #25d366;
            color: #fff;
            padding: 10px;
            text-decoration: none;
            font-weight: 700;
            border-radius: 3px;
        }

        /* --- Modal (Ventana emergente) --- */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.6);
            place-items: center;
        }
        .modal.open { display: grid; }
        
        .modal-content {
            background: #fff;
            padding: 30px;
            max-width: 800px;
            width: 90%;
            border-radius: 5px;
            display: flex;
            gap: 30px;
            position: relative;
        }

        .modal-left img {
            width: 250px;
            height: 250px;
            object-fit: contain;
            border: 1px solid var(--border-color);
            border-radius: 3px;
        }

        .modal-right h3 { font-weight: 700; font-size: 24px; margin-bottom: 10px; }
        .modal-right p { font-size: 14px; color: #666; margin-bottom: 15px; }

        .spec-list { list-style: none; margin-bottom: 20px; font-size: 14px; }
        .spec-list li strong { font-weight: 700; color: var(--text-color); }
        
        .modal-close-btn {
            position: absolute;
            top: 10px;
            right: 10px;
            background: none;
            border: none;
            font-size: 20px;
            cursor: pointer;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .hero h1 { font-size: 36px; }
            .header-content { flex-direction: column; gap: 10px; }
            header { padding-bottom: 10px; }
            body { padding-top: 110px; }
            .drawer { width: 100%; }
            .modal-content { flex-direction: column; text-align: center; }
            .modal-left, .modal-right { width: 100%; }
        }
    </style>
</head>
<body>

        <header>
        <div class="header-content container">
            <a href="#" class="logo">JL Store</a>
            <nav>
                <a href="#catalogo">Catálogo</a>
                <a href="#contacto">Contacto</a>
                <button id="open-cart-btn" class="cart-btn">🛒 Lista (<span id="cart-count">0</span>)</button>
            </nav>
        </div>
    </header>

    <main class="container">
        
                <section class="hero">
            <h1>Colección Exclusiva de Relojes</h1>
            <p>Precisión y elegancia en diseños minimalistas. Envíos garantizados a toda Colombia.</p>
            <a href="#catalogo" class="btn">Ver Modelos Ahora</a>
        </section>

        <hr>

                <section id="catalogo">
            <h2>Nuestros Productos</h2>
            <div id="product-grid" class="product-grid">
                            </div>
        </section>

        <hr>

                <section id="contacto">
            <h2>Contáctanos</h2>
            <p>Para consultar precios, disponibilidad y cotizaciones de pedidos:</p>
            <p style="font-size:18px; font-weight:700; margin-top:10px;">
                WhatsApp: <a href="https://wa.me/573000000000" target="_blank" style="color:var(--accent-color); text-decoration:none;">+57 300 000 0000</a>
            </p>
            <p style="margin-top:5px;">
                Correo: contacto@jlstore.com
            </p>
        </section>
    </main>

    <footer>
        © 2025 JL Store. Todos los derechos reservados.
    </footer>

        <div id="cart-drawer" class="drawer">
        <div class="drawer-header">
            Lista de Pedido
            <button id="close-cart-btn" class="drawer-close">✕</button>
        </div>
        <div id="cart-list" class="drawer-body">
                    </div>
        <div class="drawer-footer">
            <a href="https://wa.me/573000000000" target="_blank" class="whatsapp-btn">Enviar Lista por WhatsApp</a>
        </div>
    </div>

        <div id="product-modal" class="modal">
        <div class="modal-content">
            <button id="close-modal-btn" class="modal-close-btn">✕</button>
            <div class="modal-left">
                <img id="modal-image" src="" alt="Reloj en detalle">
            </div>
            <div class="modal-right">
                <h3 id="modal-title"></h3>
                <p style="font-style: italic; color: #999;">Ref: <span id="modal-ref"></span></p>
                
                <ul id="modal-specs" class="spec-list">
                                    </ul>

                <p style="font-weight: 700;">Stock: Disponible (Consulte vía WhatsApp)</p>

                <div style="display: flex; gap: 10px; align-items: center; margin-top: 20px;">
                    <label for="modal-qty">Cantidad:</label>
                    <input type="number" id="modal-qty" value="1" min="1" style="width: 60px; padding: 5px; border: 1px solid #ccc; border-radius: 3px;">
                    <button id="modal-add-btn" class="btn" style="flex-grow: 1;">Agregar a la Lista</button>
                </div>
            </div>
        </div>
    </div>


        <script>
        // Función para generar placeholders de SVG (Corregido y optimizado para fondo blanco)
        const createSvgPlaceholder = (text, color) => {
            return "data:image/svg+xml;utf8," + encodeURIComponent(`
                <svg xmlns='http://www.w3.org/2000/svg' width='400' height='400' viewBox='0 0 400 400'>
                    <rect width='100%' height='100%' fill='#fff'/>
                    <g transform='translate(40,40)'>
                        <rect width='320' height='320' rx='20' fill='${color}' opacity='0.5' stroke='#ccc' stroke-width='2'/>
                        <text x='160' y='170' font-size='18' font-family='Roboto, sans-serif' text-anchor='middle' fill='#333'>${text}</text>
                        <text x='160' y='200' font-size='12' font-family='Roboto, sans-serif' text-anchor='middle' fill='#666'>(Placeholder de Imagen)</text>
                    </g>
                </svg>
            `);
        };

        // Productos (Datos tomados de tus imágenes)
        const products = [
            { id: "rlx-date-trenzado-plateado-rojo", title: "Rlx Date Trenzado Plateado Tablero Negro Bisel Negro Rojo", img: createSvgPlaceholder("Plateado Bicolor", "#d9e2ea"), visual: { tablero: "Negro", bisel: "Pepsi (Rojo/Negro)", correa: "Jubilee" }, referencia: "Datejust/Unisex", tecnico: "Automático, Zafiro, 100m" },
            { id: "rlx-date-dorado-tablero-negro", title: "Rlx Date Dorado Tablero Negro Bisel Negro", img: createSvgPlaceholder("Dorado con Negro", "#ffbf00"), visual: { tablero: "Negro", bisel: "Negro", correa: "Oyster" }, referencia: "Date/Unisex", tecnico: "Automático, Zafiro, 100m" },
            { id: "rlx-diamond-roman-dorado-plateado", title: "Rlx Diamond Roman Dorado Tablero Plateado", img: createSvgPlaceholder("Roman Plateado", "#eeeeee"), visual: { tablero: "Plateado", bisel: "Diamond", correa: "President" }, referencia: "Day-Date/Unisex", tecnico: "Automático, Zafiro, 100m" },
            { id: "rlx-mujer-dayjust-diamond-bicolor-plateado", title: "Rlx Mujer Dayjust Diamond Bicolor Dorado Tablero Plateado", img: createSvgPlaceholder("Lady Bicolor", "#ffffee"), visual: { tablero: "Plateado", bisel: "Diamond", correa: "Jubilee" }, referencia: "Lady-Datejust (28mm)", tecnico: "Automático, Zafiro, 100m" },
            { id: "rlx-cubano-roman-dorado", title: "Rlx Cubano Roman Dorado Tablero Dorado", img: createSvgPlaceholder("Cubano Dorado", "#f0e68c"), visual: { tablero: "Dorado", bisel: "Roman", correa: "President" }, referencia: "Day-Date", tecnico: "Automático, Zafiro, 100m" },
            { id: "rlx-date-trenzado-dorado-verde", title: "Rlx Date Trenzado Dorado Tablero Negro Bisel Negro Verde", img: createSvgPlaceholder("Dorado con Bisel Verde", "#38761d"), visual: { tablero: "Negro", bisel: "Negro/Verde", correa: "Jubilee" }, referencia: "Datejust/Unisex", tecnico: "Automático, Zafiro, 100m" },
            { id: "rlx-mujer-dayjust-diamond-dorado", title: "Rlx Mujer Dayjust Diamond Dorado Tablero Dorado", img: createSvgPlaceholder("Lady Dorado", "#ffd700"), visual: { tablero: "Dorado", bisel: "Diamond", correa: "Jubilee" }, referencia: "Lady-Datejust (28mm)", tecnico: "Automático, Zafiro, 100m" },
            { id: "qyq-pu-bicolor-dorado", title: "QYQ PU Bicolor Dorado Tablero Dorado Bisel Negro", img: createSvgPlaceholder("QYQ Bicolor", "#ffefd5"), visual: { tablero: "Dorado", bisel: "Negro", correa: "Oyster" }, referencia: "QYQ/Unisex", tecnico: "Quartz, Hermeticidad básica" },
            { id: "rlx-datejust-diamond-dorado", title: "Rlx Datejust Diamond Dorado Tablero Plateado", img: createSvgPlaceholder("Datejust Diamond", "#f5f5f5"), visual: { tablero: "Plateado", bisel: "Diamond", correa: "Jubilee" }, referencia: "Datejust/Unisex", tecnico: "Automático, Zafiro, 100m" },
            { id: "rlx-dt-plateado", title: "Rlx Dt Plateado Tablero Blanco Bisel Negro Gris", img: createSvgPlaceholder("DT Plateado", "#e0e0e0"), visual: { tablero: "Blanco", bisel: "Negro/Gris", correa: "Oyster" }, referencia: "Date/Unisex", tecnico: "Automático, Zafiro, 100m" },
            { id: "caja-presentacion-generica", title: "Caja de Presentación Genérica", img: createSvgPlaceholder("Caja", "#cccccc"), visual: { tablero: "N/A", bisel: "N/A", correa: "N/A" }, referencia: "Accesorio", tecnico: "Caja para reloj de lujo (x1)" }
        ];

        // Referencias a elementos DOM
        const productGrid = document.getElementById('product-grid');
        const cartCount = document.getElementById('cart-count');
        const cartList = document.getElementById('cart-list');
        const cartDrawer = document.getElementById('cart-drawer');

        // Referencias del Modal
        const productModal = document.getElementById('product-modal');
        const modalImage = document.getElementById('modal-image');
        const modalTitle = document.getElementById('modal-title');
        const modalRef = document.getElementById('modal-ref');
        const modalSpecs = document.getElementById('modal-specs');
        const modalQty = document.getElementById('modal-qty');
        const modalAddBtn = document.getElementById('modal-add-btn');
        
        let cart = JSON.parse(localStorage.getItem('jl_cart') || '[]');

        // --- Funciones del Carrito ---
        const saveCart = () => {
            localStorage.setItem('jl_cart', JSON.stringify(cart));
            renderCart();
        };

        const addToCart = (productId, qty = 1) => {
            const prod = products.find(x => x.id === productId);
            if (!prod) return;

            const existing = cart.find(i => i.id === productId);
            
            if (existing) {
                existing.qty += qty;
            } else {
                // Sólo guardamos la info esencial, sin precio real.
                cart.push({ 
                    id: prod.id, 
                    title: prod.title, 
                    img: prod.img, 
                    qty 
                });
            }
            saveCart();
            openCart();
        };

        const renderCart = () => {
            cartCount.textContent = cart.reduce((s, i) => s + i.qty, 0);
            cartList.innerHTML = '';

            if (cart.length === 0) {
                cartList.innerHTML = `<p style="text-align:center; color:#999; padding-top:20px;">Tu lista de pedido está vacía.</p>`;
                return;
            }

            cart.forEach(item => {
                const div = document.createElement('div');
                div.className = 'cart-item';
                div.innerHTML = `
                    <img src="${item.img}" alt="${item.title}">
                    <div class="item-details">
                        <strong>${item.title}</strong>
                        <span>Cant: ${item.qty}</span>
                    </div>
                    <div class="item-controls">
                        <button onclick="removeOne('${item.id}')">—</button>
                        <button onclick="addOne('${item.id}')">+</button>
                        <button class="remove-btn" onclick="deleteItem('${item.id}')">Eliminar</button>
                    </div>
                `;
                cartList.appendChild(div);
            });
        };
        
        const addOne = (id) => { 
            const it = cart.find(x => x.id === id); 
            if (it) { 
                it.qty++; 
                saveCart(); 
            } 
        };
        const removeOne = (id) => { 
            let it = cart.find(x => x.id === id); 
            if (it) { 
                it.qty--; 
                if (it.qty <= 0) {
                    cart = cart.filter(x => x.id !== id);
                }
                saveCart(); 
            } 
        };
        const deleteItem = (id) => { 
            cart = cart.filter(x => x.id !== id); 
            saveCart(); 
        };

        // Exponer funciones al ámbito global (para los botones del carrito)
        window.addOne = addOne;
        window.removeOne = removeOne;
        window.deleteItem = deleteItem;


        // --- Renderizado de Productos ---
        const renderProducts = () => {
            productGrid.innerHTML = '';
            products.forEach(p => {
                const card = document.createElement('article');
                card.className = 'product-card';
                card.innerHTML = `
                    <img src="${p.img}" alt="${p.title}" class="product-image">
                    <div class="product-title">${p.title}</div>
                    <div class="product-ref">${p.referencia}</div>
                    <div class="product-price-info">CONSULTAR PRECIO (WhatsApp)</div>
                    <div class="actions">
                        <button class="view-btn" data-id="${p.id}">Detalles</button>
                        <button class="add-btn" data-id="${p.id}">Agregar a Lista</button>
                    </div>
                `;
                productGrid.appendChild(card);
            });
        };


        // --- Lógica del Modal (Ventana Emergente) ---
        let activeProductId = null;

        const openModal = (id) => {
            const p = products.find(x => x.id === id);
            if (!p) return;

            activeProductId = id;
            modalImage.src = p.img;
            modalImage.alt = p.title;
            modalTitle.textContent = p.title;
            modalRef.textContent = p.referencia;
            modalQty.value = 1;

            // Rellenar Especificaciones
            modalSpecs.innerHTML = `
                <li><strong>Tablero:</strong> ${p.visual.tablero}</li>
                <li><strong>Bisel:</strong> ${p.visual.bisel}</li>
                <li><strong>Correa:</strong> ${p.visual.correa}</li>
                <li><strong>Técnico:</strong> ${p.tecnico}</li>
            `;

            productModal.classList.add('open');
        };

        const closeModal = () => {
            productModal.classList.remove('open');
        };


        // --- Lógica del Drawer del Carrito ---
        const openCart = () => { cartDrawer.classList.add('open'); };
        const closeCart = () => { cartDrawer.classList.remove('open'); };


        // --- Event Listeners (Control de Clicks) ---

        // Clicks en el Grid de Productos (usa delegación)
        productGrid.addEventListener('click', (e) => {
            const id = e.target.dataset.id;
            if (!id) return;

            if (e.target.classList.contains('view-btn')) {
                openModal(id);
            } else if (e.target.classList.contains('add-btn')) {
                addToCart(id, 1);
            }
        });

        // Botones del Carrito
        document.getElementById('open-cart-btn').addEventListener('click', openCart);
        document.getElementById('close-cart-btn').addEventListener('click', closeCart);

        // Botones del Modal
        document.getElementById('close-modal-btn').addEventListener('click', closeModal);
        productModal.addEventListener('click', (e) => { 
            if (e.target === productModal) closeModal(); 
        });
        
        // Agregar desde Modal
        modalAddBtn.addEventListener('click', () => {
            const qty = parseInt(modalQty.value);
            if (activeProductId && qty > 0) {
                addToCart(activeProductId, qty);
                closeModal();
            }
        });


        // --- Inicialización ---
        renderProducts();
        renderCart();
    </script>

</body>
</html>
