<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Núcleo Aurora | Acceso Institucional</title>

<style>
/* =========================
   SISTEMA DE DISEÑO
========================= */
:root{
  --bg:#060a14;
  --card:rgba(255,255,255,0.06);
  --primary:#00eaff;
  --secondary:#7b61ff;
  --success:#00ffb3;
  --danger:#ff4d6d;
  --text:#eaf6ff;
}

*{box-sizing:border-box;margin:0;padding:0;font-family:Segoe UI,Roboto,Arial}

body{
  background:
    radial-gradient(circle at 20% 20%, #0d1830, transparent 40%),
    radial-gradient(circle at 80% 0%, #120a2a, transparent 40%),
    var(--bg);
  color:var(--text);
  min-height:100vh;
}

/* =========================
   LAYOUT
========================= */
.wrapper{
  min-height:100vh;
  display:flex;
  align-items:center;
  justify-content:center;
  padding:20px;
}

.card{
  width:100%;
  max-width:420px;
  background:var(--card);
  backdrop-filter:blur(18px);
  border:1px solid rgba(255,255,255,.08);
  border-radius:18px;
  padding:32px;
  box-shadow:0 20px 60px rgba(0,0,0,.45);
}

/* =========================
   TABS
========================= */
.tabs{
  display:flex;
  gap:8px;
  margin-bottom:22px;
}

.tab{
  flex:1;
  text-align:center;
  padding:10px;
  border-radius:10px;
  cursor:pointer;
  font-size:14px;
  border:1px solid rgba(255,255,255,.15);
  transition:.25s;
}

.tab.active{
  background:linear-gradient(90deg,var(--primary),var(--secondary));
  color:#001018;
  font-weight:600;
}

/* =========================
   FORM
========================= */
.field{margin-bottom:14px}

label{
  font-size:12px;
  opacity:.8;
}

input{
  width:100%;
  padding:12px;
  margin-top:6px;
  border-radius:10px;
  border:1px solid rgba(255,255,255,.15);
  background:rgba(0,0,0,.35);
  color:#fff;
  outline:none;
}

input:focus{
  border-color:var(--primary);
  box-shadow:0 0 0 2px rgba(0,234,255,.15);
}

/* strength */
.strength{
  height:6px;
  border-radius:6px;
  margin-top:6px;
  background:rgba(255,255,255,.1);
  overflow:hidden;
}

.strength span{
  display:block;
  height:100%;
  width:0%;
  transition:.35s cubic-bezier(.4,0,.2,1);
}

/* buttons */
.btn{
  width:100%;
  padding:12px;
  border:none;
  border-radius:12px;
  font-weight:600;
  cursor:pointer;
  background:linear-gradient(90deg,var(--primary),var(--secondary));
  color:#001018;
  margin-top:6px;
  transition:.25s;
}

.btn:hover{
  transform:translateY(-1px);
  box-shadow:0 10px 25px rgba(0,234,255,.35);
}

.btn-ghost{
  background:transparent;
  color:var(--text);
  border:1px solid rgba(255,255,255,.2);
}

/* message */
.msg{
  margin-top:12px;
  font-size:13px;
  text-align:center;
  min-height:18px;
}

/* =========================
   DASHBOARD
========================= */
#app{display:none;padding:40px}

.grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
  gap:20px;
}

.metric{
  background:var(--card);
  border-radius:14px;
  padding:20px;
  border:1px solid rgba(255,255,255,.08);
}

.bar{
  height:12px;
  background:rgba(255,255,255,.12);
  border-radius:20px;
  overflow:hidden;
  margin-top:10px;
}

.bar-fill{
  height:100%;
  width:0%;
  background:linear-gradient(90deg,var(--primary),var(--success));
  transition:1.2s cubic-bezier(.2,.8,.2,1);
}

footer{
  text-align:center;
  margin-top:40px;
  opacity:.7;
  font-size:13px;
}
</style>
</head>
<body>

<div class="wrapper">
  <div class="card">

    <div class="tabs">
      <div id="tabLogin" class="tab active">Ingresar</div>
      <div id="tabRegister" class="tab">Crear cuenta</div>
    </div>

    <!-- LOGIN -->
    <div id="loginForm">
      <div class="field">
        <label>Gmail</label>
        <input id="loginEmail" type="email" placeholder="usuario@gmail.com">
      </div>

      <div class="field">
        <label>Contraseña</label>
        <input id="loginPass" type="password" placeholder="••••••••">
      </div>

      <button class="btn" id="loginBtn">Acceder al Núcleo</button>
      <div id="loginMsg" class="msg"></div>
    </div>

    <!-- REGISTER -->
    <div id="registerForm" style="display:none">
      <div class="field">
        <label>Nombre</label>
        <input id="regName" type="text">
      </div>

      <div class="field">
        <label>Gmail</label>
        <input id="regEmail" type="email" placeholder="nombre@gmail.com">
      </div>

      <div class="field">
        <label>Contraseña segura</label>
        <input id="regPass" type="password">
        <div class="strength"><span id="strengthBar"></span></div>
      </div>

      <div class="field">
        <label>Confirmar contraseña</label>
        <input id="regPass2" type="password">
      </div>

      <button class="btn" id="registerBtn">Crear cuenta Aurora</button>
      <div id="regMsg" class="msg"></div>
    </div>

  </div>
</div>

<!-- ================= DASHBOARD ================= -->
<div id="app">
  <h1>Núcleo Aurora — Centro de Calibración</h1>

  <div class="grid">
    <div class="metric">
      Armonía Global
      <div class="bar"><div id="bar1" class="bar-fill"></div></div>
    </div>
    <div class="metric">
      Estabilidad Climática
      <div class="bar"><div id="bar2" class="bar-fill"></div></div>
    </div>
    <div class="metric">
      Frecuencia Colectiva
      <div class="bar"><div id="bar3" class="bar-fill"></div></div>
    </div>
  </div>

  <footer>Sistema Aurora © 2045</footer>
</div>

<script>
/* ===============================
   TAB SWITCH
=============================== */
const tabLogin=document.getElementById("tabLogin");
const tabRegister=document.getElementById("tabRegister");
const loginForm=document.getElementById("loginForm");
const registerForm=document.getElementById("registerForm");

tabLogin.onclick=()=>{
  tabLogin.classList.add("active");
  tabRegister.classList.remove("active");
  loginForm.style.display="block";
  registerForm.style.display="none";
};

tabRegister.onclick=()=>{
  tabRegister.classList.add("active");
  tabLogin.classList.remove("active");
  loginForm.style.display="none";
  registerForm.style.display="block";
};

/* ===============================
   PASSWORD STRENGTH
=============================== */
const passInput=document.getElementById("regPass");
const strengthBar=document.getElementById("strengthBar");

passInput.addEventListener("input",()=>{
  const v=passInput.value;
  let s=0;
  if(v.length>=8)s++;
  if(/[A-Z]/.test(v))s++;
  if(/[0-9]/.test(v))s++;
  if(/[^A-Za-z0-9]/.test(v))s++;

  const colors=["#ff4d6d","#ffb84d","#ffee55","#00ffb3"];
  strengthBar.style.width=(s*25)+"%";
  strengthBar.style.background=colors[s-1]||"transparent";
});

/* ===============================
   SHA-256
=============================== */
async function sha256(str){
  const buf=new TextEncoder().encode(str);
  const hash=await crypto.subtle.digest("SHA-256",buf);
  return [...new Uint8Array(hash)]
    .map(b=>b.toString(16).padStart(2,"0"))
    .join("");
}

/* ===============================
   REGISTER
=============================== */
document.getElementById("registerBtn").onclick=async()=>{
  const name=regName.value.trim();
  const email=regEmail.value.trim();
  const pass=regPass.value;
  const pass2=regPass2.value;
  const msg=document.getElementById("regMsg");

  const gmail=/^[\\w.+-]+@gmail\\.com$/;

  if(!gmail.test(email)){
    msg.style.color="var(--danger)";
    msg.textContent="Ingrese un Gmail válido.";
    return;
  }

  if(pass!==pass2){
    msg.style.color="var(--danger)";
    msg.textContent="Las contraseñas no coinciden.";
    return;
  }

  const hash=await sha256(pass);
  localStorage.setItem("auroraUser",JSON.stringify({name,email,hash}));

  msg.style.color="var(--success)";
  msg.textContent="Cuenta creada correctamente.";
};

/* ===============================
   LOGIN
=============================== */
document.getElementById("loginBtn").onclick=async()=>{
  const email=loginEmail.value.trim();
  const pass=loginPass.value;
  const msg=document.getElementById("loginMsg");
  const saved=JSON.parse(localStorage.getItem("auroraUser")||"null");

  if(!saved){
    msg.style.color="var(--danger)";
    msg.textContent="No existe usuario registrado.";
    return;
  }

  const hash=await sha256(pass);

  if(saved.email===email && saved.hash===hash){
    document.querySelector(".wrapper").style.display="none";
    document.getElementById("app").style.display="block";

    requestAnimationFrame(()=>{
      bar1.style.width="93%";
      bar2.style.width="88%";
      bar3.style.width="96%";
    });
  }else{
    msg.style.color="var(--danger)";
    msg.textContent="Credenciales incorrectas.";
  }
};
</script>

</body>
</html>
   
