# Valentine
<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Valentine Blue</title>

<style>
body{
    margin:0;
    font-family: 'Segoe UI', sans-serif;
    background: linear-gradient(135deg,#cfe9ff,#a7d3ff,#dff3ff);
    overflow:hidden;
    text-align:center;
    color:#0b3d91;
}

.screen{
    position:absolute;
    width:100%;
    height:100%;
    display:flex;
    justify-content:center;
    align-items:center;
    flex-direction:column;
}

.hidden{ display:none; }

input{
    padding:12px;
    border-radius:20px;
    border:none;
    outline:none;
    width:220px;
    text-align:center;
    margin-top:10px;
}

button{
    margin-top:15px;
    padding:10px 20px;
    border:none;
    border-radius:20px;
    background:#0b3d91;
    color:white;
    cursor:pointer;
}

img{
    width:260px;
    border-radius:20px;
    margin-top:20px;
    box-shadow:0 10px 25px rgba(0,0,0,0.2);
}

/* Love animation */
.heart{
    position:absolute;
    font-size:20px;
    animation: float 5s linear infinite;
    color:#4da6ff;
}

@keyframes float{
    from{
        transform: translateY(100vh) scale(1);
        opacity:1;
    }
    to{
        transform: translateY(-10vh) scale(1.5);
        opacity:0;
    }
}
</style>
</head>

<body>

<!-- Musik -->
<audio id="music" autoplay loop>
  <source src="music.mp3" type="audio/mpeg">
</audio>
<audio id="lagu" loop>
  <source src="music.mp3" type="audio/mpeg">
</audio>

<button onclick="playMusic()">by ola</button>

<script>
function playMusic(){
  document.getElementById("lagu").play();
}
</script>


<!-- Input Nama -->
<div class="screen" id="start">
    <h2>Enter your name 💙</h2>
    <input type="text" id="nama" placeholder="Nama...">
    <button onclick="mulai()">join</button>
</div>

<!-- Halaman Utama -->
<div class="screen hidden" id="main">
    <h1 id="textNama"></h1>
    <p>if no one has told you yet, i am proud of you, i see you trying your best, even when things get really tough. i see you 🤍</p>

    <!-- FOTO -->
    <img src="https://i.pinimg.com/736x/ad/4d/b2/ad4db25b75448df9a0ccce938a885fa1.jpg" alt="valentine">
</div>

<script>
function mulai(){
    const nama = document.getElementById("nama").value;
    if(nama.trim() === "") return;

    document.getElementById("start").classList.add("hidden");
    document.getElementById("main").classList.remove("hidden");

    document.getElementById("textNama").innerText = "Happy Valentine, " + nama + " 💙";
}

/* Generate hearts */
function createHeart(){
    const heart = document.createElement("div");
    heart.classList.add("heart");
    heart.innerText = "💙";
    heart.style.left = Math.random() * window.innerWidth + "px";
    heart.style.fontSize = (Math.random()*20 + 15) + "px";
    heart.style.animationDuration = (Math.random()*3 + 3) + "s";

    document.body.appendChild(heart);

    setTimeout(()=>{ heart.remove(); },5000);
}

setInterval(createHeart,300);
</script>

</body>
</html>