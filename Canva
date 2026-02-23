<!DOCTYPE html><html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Bombonera Futurista — Núcleo Aurora</title><style>
*{box-sizing:border-box;margin:0;padding:0;font-family:Segoe UI,Roboto,Arial,sans-serif}
body{background:radial-gradient(circle at 20% 20%, #0a0f2a, #02040f 60%);color:#e6f0ff;overflow-x:hidden}
section{padding:80px 20px;position:relative}
h2{font-size:2.2rem;margin-bottom:20px}

.glass{background:rgba(255,255,255,0.06);backdrop-filter:blur(14px);border:1px solid rgba(255,255,255,0.12);border-radius:18px;box-shadow:0 10px 40px rgba(0,0,0,0.45)}

/* ================= LOGIN ================= */
#login{min-height:100vh;display:flex;align-items:center;justify-content:center}
.login-box{width:100%;max-width:420px;padding:40px;text-align:center}
.login-box p{opacity:.8;margin-bottom:25px}

.input-group{margin-bottom:18px;text-align:left}
.input-group input{width:100%;padding:12px;margin-top:6px;border-radius:10px;border:1px solid rgba(255,255,255,.15);background:rgba(0,0,0,.35);color:#fff}

.btn{width:100%;padding:12px;border:none;border-radius:12px;background:linear-gradient(90deg,#00e0ff,#7b61ff);color:#001018;font-weight:bold;cursor:pointer;transition:.3s}
.btn:hover{transform:translateY(-2px);box-shadow:0 0 25px rgba(0,224,255,.6)}

/* HERO */
#hero{min-height:90vh;display:flex;align-items:center;justify-content:center;text-align:center}
.hero-content{max-width:900px}
.cta{margin-top:25px;padding:14px 28px;border-radius:14px;border:none;font-weight:bold;background:linear-gradient(90deg,#00f0ff,#8a5cff);color:#001018;cursor:pointer}

.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:20px}
.card{padding:20px}

.energy-bar{height:14px;background:rgba(255,255,255,.12);border-radius:20px;overflow:hidden;margin:10px 0}
.energy-fill{height:100%;background:linear-gradient(90deg,#00ffd5,#7b61ff);width:0%;transition:1s}

.status-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:16px;margin-top:20px}
.status-box{padding:16px;border-radius:14px;background:rgba(0,0,0,.35);border:1px solid rgba(255,255,255,.08)}

footer{text-align:center;padding:40px 20px;opacity:.7}
canvas{position:absolute;inset:0;z-index:-1}
.hidden{display:none}
</style></head>
<body><!-- =====================================================
     INICIO DE SESIÓN CON GMAIL (SIMULADO)
===================================================== --><section id="login">
  <div class="login-box glass">
    <h1>Acceso Seguro al Núcleo Aurora</h1>
    <p>Inicio de sesión con cuenta Gmail (simulación local)</p><div class="input-group">
  <label>Correo Gmail</label>
  <input id="email" type="email" placeholder="usuario@gmail.com">
</div>

<div class="input-group">
  <label>Contraseña</label>
  <input id="password" type="password" placeholder="••••••••">
</div>

<button class="btn" onclick="login()">Iniciar sesión</button>
<p id="loginMsg" style="margin-top:12px;font-size:.9rem"></p>

  </div>
</section><div id="app" class="hidden"><section id="hero">
  <canvas id="bg"></canvas>
  <div class="hero-content">
    <h2>Centro de Planificación de la Humanidad</h2>
    <p>El resplandor de la inteligencia galáctica aplicado al equilibrio terrestre.</p>
    <button class="cta">Explorar Núcleo</button>
  </div>
</section><section>
  <h2>🌠 Misión Aurora — Calibración Galáctica</h2>
  <div class="glass card">
    El Algoritmo de Convergencia Energética Humana (ACEH) interpreta la capacidad
    humana como un resplandor galáctico. Cada individuo actúa como nodo energético
    dentro de una matriz planetaria que optimiza el equilibrio climático.
  </div>
</section><section>
  <h2>🔋 Centro de Calibración Energética</h2>
  <div class="glass card">
    <strong>Energía Global</strong>
    <div class="energy-bar"><div id="energyFill" class="energy-fill"></div></div><div class="status-grid">
  <div class="status-box">Nivel de armonía: <b id="harm">87%</b></div>
  <div class="status-box">Estabilidad climática: <b>Alta</b></div>
  <div class="status-box">Frecuencia colectiva: <b>Sincronizada</b></div>
  <div class="status-box">Protocolo Aurora: <b style="color:#00ffd5">Activo</b></div>
</div>

<canvas id="wave" height="160" style="margin-top:30px"></canvas>

  </div>
</section><footer>Bombonera Futurista — Núcleo Aurora</footer>
</div><script>
/* =====================================================
   LOGIN GMAIL SIMULADO (FRONTEND ONLY)
===================================================== */
function login(){
  const email=document.getElementById('email').value.trim();
  const pass=document.getElementById('password').value.trim();
  const msg=document.getElementById('loginMsg');

  // validar formato Gmail
  if(!email.endsWith('@gmail.com')){
    msg.textContent='Debe ingresar un correo Gmail válido';
    msg.style.color='#ff6b6b';
    return;
  }

  if(pass.length<4){
    msg.textContent='Contraseña demasiado corta';
    msg.style.color='#ff6b6b';
    return;
  }

  msg.textContent='Autenticación aceptada…';
  msg.style.color='#00ffcc';

  setTimeout(()=>{
    document.getElementById('login').style.display='none';
    document.getElementById('app').classList.remove('hidden');
    animateEnergy();
  },800);
}

/* HERO PARTICLES */
const canvas=document.getElementById('bg');
const ctx=canvas.getContext('2d');
let particles=[];
function resize(){canvas.width=innerWidth;canvas.height=innerHeight}
resize();addEventListener('resize',resize);
for(let i=0;i<60;i++){particles.push({x:Math.random()*canvas.width,y:Math.random()*canvas.height,vx:(Math.random()-.5)*0.6,vy:(Math.random()-.5)*0.6,r:Math.random()*2+1})}
function animate(){ctx.clearRect(0,0,canvas.width,canvas.height);particles.forEach(p=>{p.x+=p.vx;p.y+=p.vy;if(p.x<0||p.x>canvas.width)p.vx*=-1;if(p.y<0||p.y>canvas.height)p.vy*=-1;ctx.beginPath();ctx.arc(p.x,p.y,p.r,0,Math.PI*2);ctx.fillStyle='rgba(0,224,255,.7)';ctx.fill()});requestAnimationFrame(animate)}
animate();

/* ENERGY BAR */
function animateEnergy(){
  let val=0;const fill=document.getElementById('energyFill');const harm=document.getElementById('harm');const target=87;
  const int=setInterval(()=>{val++;fill.style.width=val+'%';harm.textContent=val+'%';if(val>=target)clearInterval(int)},20);
}
</script></body>
</html>
