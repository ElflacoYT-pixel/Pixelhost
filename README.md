<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>PixelHost | Hosting Gamer Premium</title>
<style>
/* ==== ESTILOS GLOBALES ==== */
*{margin:0;padding:0;box-sizing:border-box;font-family:'Poppins',sans-serif;}
body{background:#0a0a0a;color:#fff;overflow-x:hidden;}
header{background:linear-gradient(90deg,#000,#111,#f00);padding:15px 25px;display:flex;justify-content:space-between;align-items:center;position:sticky;top:0;z-index:10;box-shadow:0 0 25px #f00;}
header h1{color:#ff3333;text-shadow:0 0 15px #f00;font-size:1.6rem;}
nav a{color:white;text-decoration:none;margin:0 10px;font-weight:bold;transition:.3s;}
nav a:hover{color:#f00;text-shadow:0 0 10px red;}
section{display:none;padding:60px 20px;min-height:80vh;text-align:center;animation:fade .5s ease;}
section.active{display:block;}
@keyframes fade{from{opacity:0;transform:translateY(15px);}to{opacity:1;transform:translateY(0);}}
h2.section-title{color:#ff3333;text-shadow:0 0 15px #f00;margin-bottom:25px;font-size:2rem;}
/* ==== TARJETAS ==== */
.card-container{display:flex;flex-wrap:wrap;justify-content:center;gap:25px;}
.card{background:#111;border:1px solid #f00;padding:20px;border-radius:12px;min-width:230px;max-width:300px;transition:.3s;box-shadow:0 0 15px #f00a;}
.card:hover{transform:scale(1.05);box-shadow:0 0 25px #f00;}
.card h3{color:#ff3333;margin-bottom:10px;}
.card p{margin-bottom:15px;color:#ccc;}
button{background:#f00;border:none;padding:10px 20px;color:white;border-radius:8px;cursor:pointer;transition:0.3s;}
button:hover{box-shadow:0 0 15px #f00;}
footer{background:#111;text-align:center;padding:15px;color:#888;border-top:1px solid #333;}
/* ==== CARRITO ==== */
.cart-item{background:#111;padding:10px;margin:10px;border:1px solid #444;border-radius:8px;}
.total{font-size:1.3rem;color:#ff3333;text-shadow:0 0 10px #f00;margin-top:15px;}
@media(max-width:700px){.card-container{flex-direction:column;align-items:center;}header{flex-direction:column;}}
/* ==== ANIMACIÓN FONDO ==== */
.bg-rgb{
  position:fixed;top:0;left:0;width:100%;height:100%;
  background:radial-gradient(circle at 20% 30%,#f00 0%,transparent 40%),
             radial-gradient(circle at 80% 70%,#ff0000aa 0%,transparent 40%);
  filter:blur(100px);z-index:-1;animation:rgbMove 6s infinite alternate;
}
@keyframes rgbMove{
  from{transform:translate(0,0);}
  to{transform:translate(30px,-30px);}
}
</style>
</head>
<body>

<div class="bg-rgb"></div>

<header>
  <h1>PixelHost</h1>
  <nav>
    <a href="#" onclick="show('inicio')">Inicio</a>
    <a href="#" onclick="show('premium')">Webs Premium</a>
    <a href="#" onclick="show('discord')">Servers Discord</a>
    <a href="#" onclick="show('carrito')">Carrito</a>
    <a href="#" onclick="show('contacto')">Contacto</a>
    <a href="#" onclick="show('nosotros')">Nosotros</a>
  </nav>
</header>

<!-- ====== INICIO ====== -->
<section id="inicio" class="active">
  <h2 class="section-title">🏠 Bienvenido a PixelHost</h2>
  <p>Tu destino para <b>páginas web y servidores de Discord</b> con estilo gamer premium.</p><br>
  <button onclick="show('premium')">Ver Planes Web</button>
</section>

<!-- ====== PLANES WEB PREMIUM ====== -->
<section id="premium">
  <h2 class="section-title">💎 Webs Premium</h2>
  <div class="card-container">
    <div class="card">
      <h3>Web Básica</h3>
      <p>Ideal para proyectos pequeños o personales.</p>
      <p><b>$15</b></p>
      <button onclick="addToCart('Web Básica',15)">Agregar</button>
    </div>
    <div class="card">
      <h3>Web Avanzada</h3>
      <p>Diseño profesional, dominio incluido y hosting.</p>
      <p><b>$30</b></p>
      <button onclick="addToCart('Web Avanzada',30)">Agregar</button>
    </div>
    <div class="card">
      <h3>Web Premium</h3>
      <p>Diseño personalizado, hosting + SEO + soporte.</p>
      <p><b>$50</b></p>
      <button onclick="addToCart('Web Premium',50)">Agregar</button>
    </div>
  </div>
</section>

<!-- ====== SERVIDORES DISCORD ====== -->
<section id="discord">
  <h2 class="section-title">🌐 Servidores Discord</h2>
  <div class="card-container">
    <div class="card">
      <h3>Servidor Community</h3>
      <p>Configuración básica + roles automáticos.</p>
      <p><b>$10</b></p>
      <button onclick="addToCart('Servidor Community',10)">Agregar</button>
    </div>
    <div class="card">
      <h3>Servidor Premium</h3>
      <p>Diseño, bots avanzados y seguridad mejorada.</p>
      <p><b>$25</b></p>
      <button onclick="addToCart('Servidor Premium',25)">Agregar</button>
    </div>
    <div class="card">
      <h3>Servidor Ultimate</h3>
      <p>Setup completo, branding y soporte 24/7.</p>
      <p><b>$40</b></p>
      <button onclick="addToCart('Servidor Ultimate',40)">Agregar</button>
    </div>
  </div>
</section>

<!-- ====== CARRITO ====== -->
<section id="carrito">
  <h2 class="section-title">🛒 Tu Carrito</h2>
  <div id="cart-container"></div>
  <p class="total" id="cart-total"></p>
  <button onclick="clearCart()">Vaciar Carrito</button>
</section>

<!-- ====== CONTACTO ====== -->
<section id="contacto">
  <h2 class="section-title">📞 Contacto</h2>
  <p>¿Tienes dudas o quieres un plan personalizado?</p><br>
  <p>📧 contacto@pixelhost.com</p>
  <p>🌐 Discord: discord.gg/pixelhost</p>
</section>

<!-- ====== NOSOTROS ====== -->
<section id="nosotros">
  <h2 class="section-title">👥 Sobre Nosotros</h2>
  <p>En PixelHost combinamos <b>tecnología, diseño y comunidad</b> para ofrecer experiencias únicas.</p><br>
  <p>Nos especializamos en crear <b>páginas web y servidores de Discord</b> que brillan con estilo gamer.</p>
</section>

<footer>
  © 2025 PixelHost. Todos los derechos reservados.
</footer>

<script>
// ====== FUNCIONALIDAD SPA ======
function show(id){
  document.querySelectorAll("section").forEach(s=>s.classList.remove("active"));
  document.getElementById(id).classList.add("active");
  if(id==='carrito') renderCart();
}

// ====== CARRITO FUNCIONAL ======
let cart = JSON.parse(localStorage.getItem('cart')) || [];

function addToCart(name, price){
  cart.push({name,price});
  localStorage.setItem('cart', JSON.stringify(cart));
  alert(name+" agregado al carrito ✅");
}

function renderCart(){
  const container=document.getElementById('cart-container');
  container.innerHTML='';
  if(cart.length===0){container.innerHTML='<p>Tu carrito está vacío 🛍️</p>';document.getElementById('cart-total').textContent='';return;}
  let total=0;
  cart.forEach((item,i)=>{
    const div=document.createElement('div');
    div.className='cart-item';
    div.innerHTML=`${item.name} - $${item.price} <button onclick="removeItem(${i})">❌</button>`;
    container.appendChild(div);
    total+=item.price;
  });
  document.getElementById('cart-total').textContent='Total: $'+total;
}

function removeItem(index){
  cart.splice(index,1);
  localStorage.setItem('cart',JSON.stringify(cart));
  renderCart();
}

function clearCart(){
  if(confirm('¿Vaciar carrito completo?')){
    cart=[];
    localStorage.removeItem('cart');
    renderCart();
  }
}
</script>
</body>
</html>
