# Fftiurnament998
Tournament website 
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Vibrant Gaming</title>
<link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&family=Roboto:wght@400;700&display=swap" rel="stylesheet">
<link rel="icon" href="favicon.png" type="image/png">

<!-- Social Media Meta Tags -->
<meta property="og:title" content="Vibrant Gaming">
<meta property="og:description" content="Track points, join tournaments, and compete with friends!">
<meta property="og:image" content="banner.png">
<meta property="og:url" content="https://yourdomain.com">
<meta property="og:type" content="website">
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="Vibrant Gaming">
<meta name="twitter:description" content="Track points, join tournaments, and compete with friends!">
<meta name="twitter:image" content="banner.png">

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<style>
/* Basic Reset */
*{margin:0;padding:0;box-sizing:border-box;}
body{font-family:'Roboto',sans-serif;background:#0d0d0d;color:#fff;}
header{display:flex;justify-content:space-between;align-items:center;padding:20px;background:#111;position:sticky;top:0;z-index:100;}
header h1{font-family:'Press Start 2P',cursive;color:#00ffff;text-shadow:0 0 10px #00ffff;}
nav a{color:#fff;margin-left:20px;text-decoration:none;font-weight:bold;transition:0.3s;}
nav a:hover{color:#ff00ff;text-shadow:0 0 10px #ff00ff;}
section{padding:80px 20px;text-align:center;}
.btn{display:inline-block;padding:12px 25px;margin-top:20px;background:#00ffff;color:#000;font-weight:bold;border:none;cursor:pointer;transition:0.3s;border-radius:10px;text-transform:uppercase;}
.btn:hover{background:#ff00ff;color:#fff;box-shadow:0 0 15px #ff00ff;}
.games,.tournaments,.leaderboard{display:flex;justify-content:center;flex-wrap:wrap;gap:20px;}
.card{background:rgba(0,0,0,0.6);padding:20px;border-radius:15px;width:250px;margin:15px;transition:0.3s;box-shadow:0 0 15px #00ffff;position:relative;overflow:hidden;}
.card::before{content:"";position:absolute;top:0;left:0;width:100%;height:100%;background:linear-gradient(45deg,#ff00ff,#00ffff,#ffeb3b,#ff00ff);opacity:0.3;filter:blur(20px);transition:0.5s;z-index:-1;}
.card:hover{transform:scale(1.05);box-shadow:0 0 25px #ff00ff;}
table{width:80%;margin:20px auto;border-collapse:collapse;transition:0.5s;}
th,td{padding:12px;border-bottom:1px solid #444;text-align:center;cursor:pointer;}
th{color:#00ffff;text-shadow:0 0 5px #00ffff;}
tr:hover{background:rgba(255,0,255,0.1);}
.top1{background:#ff00ff; color:#fff; text-shadow:0 0 15px #ff00ff;}
.top2{background:#00ffff; color:#000; text-shadow:0 0 15px #00ffff;}
.top3{background:#ffeb3b; color:#000; text-shadow:0 0 15px #ffeb3b;}
input,textarea,select{padding:10px;margin:10px 0;width:100%;border-radius:10px;border:none;}
input:focus,textarea:focus,select:focus{outline:none;box-shadow:0 0 10px #00ffff;}
body::before{content:"";position:fixed;top:0;left:0;width:100%;height:100%;background:radial-gradient(circle,rgba(255,0,255,0.2)0%,transparent 70%),radial-gradient(circle,rgba(0,255,255,0.2)0%,transparent 70%);background-size:200px 200px;animation:moveBG 20s linear infinite;z-index:-1;}
@keyframes moveBG{0%{background-position:0 0,100px 100px;}100%{background-position:100px 100px,0 0;}}
.form-container{max-width:400px;margin:0 auto;text-align:left;}
.form-container label{display:block;margin-top:10px;color:#00ffff;}
#dashboard{margin:20px auto;width:80%;padding:15px;background:rgba(255,255,255,0.1);border-radius:10px;}
.fade-in{animation:fadeIn 0.5s;}
@keyframes fadeIn{0%{opacity:0; transform:translateY(-20px);}100%{opacity:1;transform:translateY(0);}}
.modal{display:none;position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.9);align-items:center;justify-content:center;z-index:200;}
.modal-content{background:#111;padding:20px;border-radius:15px;width:90%;max-width:500px;position:relative;}
.close-btn{position:absolute;top:10px;right:15px;font-size:20px;color:#ff00ff;cursor:pointer;}
canvas{background:#222;border-radius:10px;padding:10px;}
</style>
</head>
<body>

<header>
<h1>Vibrant Gaming</h1>
<nav>
<a href="#home">Home</a>
<a href="#games">Games</a>
<a href="#tournaments">Tournaments</a>
<a href="#leaderboard">Leaderboard</a>
<a href="#contact">Contact</a>
</nav>
</header>

<section id="home">
<h2>Welcome Back!</h2>
<p>Track points, join tournaments, and view player profiles!</p>
<div class="form-container">
<h3>Login</h3>
<form id="loginForm">
<label>Username:</label>
<input type="text" id="username" required>
<button type="submit" class="btn">Login</button>
</form>
</div>
<div id="dashboard" style="display:none;">
<h3>Player Dashboard</h3>
<p id="playerStats"></p>
</div>
</section>

<section id="games">
<h2>Games</h2>
<div class="games">
<div class="card"><h3>Battle Royale</h3></div>
<div class="card"><h3>Racing Fury</h3></div>
<div class="card"><h3>Fantasy Quest</h3></div>
</div>
</section>

<section id="tournaments">
<h2>Upcoming Tournaments</h2>
<div class="tournaments" id="tournamentList">
<div class="card"><h3>Fortnite Frenzy</h3><p>Date: 25th Aug | Prize: $200</p></div>
<div class="card"><h3>Speed Racer Cup</h3><p>Date: 30th Aug | Prize: $150</p></div>
<div class="card"><h3>Dragon Slayer League</h3><p>Date: 5th Sep | Prize: $300</p></div>
</div>
<div class="form-container">
<h3>Register for Tournament</h3>
<form id="tournamentForm">
<label>Name:</label>
<input type="text" id="playerName" required>
<label>Email:</label>
<input type="email" id="playerEmail" required>
<label>Game:</label>
<select id="playerGame" required>
<option value="Battle Royale">Battle Royale</option>
<option value="Racing Fury">Racing Fury</option>
<option value="Fantasy Quest">Fantasy Quest</option>
</select>
<button type="submit" class="btn">Register</button>
</form>
</div>
</section>

<section id="leaderboard">
<h2>Leaderboard</h2>
<table id="leaderboardTable">
<tr><th>Rank</th><th>Player</th><th>Game</th><th>Points</th></tr>
</table>
</section>

<!-- Player Profile Modal -->
<div id="profileModal" class="modal">
<div class="modal-content">
<span class="close-btn" id="closeModal">&times;</span>
<h2 id="modalName"></h2>
<p id="modalGame"></p>
<p id="modalPoints"></p>
<canvas id="pointsChart" width="400" height="200"></canvas>
</div>
</div>

<section id="contact">
<h2>Contact Us</h2>
<form onsubmit="alert('Message sent!'); return false;" class="form-container">
<input type="text" placeholder="Your Name" required>
<input type="email" placeholder="Your Email" required>
<textarea placeholder="Your Message" rows="5" required></textarea>
<button type="submit" class="btn">Send Message</button>
</form>
</section>

<footer>
&copy; 2025 Vibrant Gaming. All Rights Reserved.
</footer>

<script>
// Leaderboard and profiles
let leaderboardData = JSON.parse(localStorage.getItem('leaderboard')) || [
{player:'ShadowGamer',game:'Battle Royale',points:9800,history:[9000,9200,9500,9800]},
{player:'NeonRacer',game:'Racing Fury',points:8700,history:[8000,8300,8500,8700]},
{player:'DragonSlayer',game:'Fantasy Quest',points:8300,history:[7000,7500,8000,8300]}
];
const leaderboardTable = document.getElementById('leaderboardTable');
let currentUser = '';

function animatePoints(cell,newValue){
let current=parseInt(cell.innerText)||0;
const step=Math.ceil((newValue-current)/20);
let count=0;
const interval=setInterval(()=>{
current+=step;
count++;
if(count>=20){current=newValue;clearInterval(interval);}
cell.innerText=current;
},20);
}

function renderLeaderboard(){
leaderboardTable.innerHTML='<tr><th>Rank</th><th>Player</th><th>Game</th><th>Points</th></tr>';
leaderboardData.sort((a,b)=>b.points-a.points);
leaderboardData.forEach((item,index)=>{
const row=leaderboardTable.insertRow();
row.classList.add('fade-in');
row.insertCell(0).innerText=index+1;
const nameCell=row.insertCell(1);
nameCell.innerText=item.player;
nameCell.style.color='#00ffff';
nameCell.style.cursor='pointer';
nameCell.onclick=()=>openProfile(item);
row.insertCell(2).innerText=item.game;
const pointsCell=row.insertCell(3);
animatePoints(pointsCell,item.points);
if(index===0) row.classList.add('top1');
if(index===1) row.classList.add('top2');
if(index===2) row.classList.add('top3');
});
localStorage.setItem('leaderboard',JSON.stringify(leaderboardData));
updateDashboard();
}

function updateDashboard(){
if(!currentUser) return;
const user=leaderboardData.find(u=>u.player===currentUser);
if(user){
document.getElementById('dashboard').style.display='block';
document.getElementById('playerStats').innerText=`Player: ${user.player} | Game: ${user.game} | Points: ${user.points}`;
}
}

// Login
document.getElementById('loginForm').addEventListener('submit',function(e){
e.preventDefault();
currentUser=document.getElementById('username').value;
alert(`Welcome ${currentUser}! You can now register for tournaments.`);
document.getElementById('loginForm').reset();
updateDashboard();
});

// Tournament registration
document.getElementById('tournamentForm').addEventListener('submit',function(e){
e.preventDefault();
if(!currentUser){alert('Please login first!');return;}
const name=document.getElementById('playerName').value;
const game=document.getElementById('playerGame').value;
const points=Math.floor(Math.random()*5000)+500;
leaderboardData.push({player:name,game:game,points:points,history:[points]});
renderLeaderboard();
alert(`Thanks ${name}! You are registered for ${game} with ${points} points.`);
document.getElementById('tournamentForm').reset();
});

// Profile modal
const modal=document.getElementById('profileModal');
const closeModalBtn=document.getElementById('closeModal');
function openProfile(player){
document.getElementById('modalName').innerText=player.player;
document.getElementById('modalGame').innerText=`Game: ${player.game}`;
document.getElementById('modalPoints').innerText=`Points: ${player.points}`;
modal.style.display='flex';
const ctx=document.getElementById('pointsChart').getContext('2d');
if(window.playerChart) window.playerChart.destroy();
window.playerChart=new Chart(ctx,{
type:'line',
data:{
labels:player.history.map((_,i)=>`T${i+1}`),
datasets:[{label:'Points Over Time',data:player.history,borderColor:'#00ffff',backgroundColor:'rgba(0,255,255,0.2)',fill:true,tension:0.3}]
},
options:{responsive:true,plugins:{legend:{labels:{color:'#fff'}}},scales:{x:{ticks:{color:'#fff'}},y:{ticks:{color:'#fff'}}}}
});
}
closeModalBtn.onclick=()=>{modal.style.display='none';};
window.onclick=function(event){if(event.target==modal){modal.style.display='none';}};

renderLeaderboard();
</script>

</body>
</html>
