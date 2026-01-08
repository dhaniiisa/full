<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<title>Balok Tengah</title>

<style>
  body {
    margin: 0;
    height: 100vh;
    background: #c4fcff; position: relative;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    font-family: Arial, sans-serif;
  }

  /* Balok utama */
  .balok-utama {
    width: 450px;
    padding: 90px;
    background: #fff9fd;
    border-radius: 16px;
    text-align: center;
    box-shadow: 0 8px 20px rgba(0,0,0,0.1);
    margin-bottom: 25px;
  }

  .balok-utama h2 {
    margin:10 0 10px;
    color: #333;
  }

  .balok-utama p {
    margin: 10 0 10px;
    font-size: 14px;
    color: #666;
  }

  /* Balok tombol */
  .balok-next {
    width: 200px;
    height: 50px;
    background: #4caf50;
    color: white;
    border-radius: 10px;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    transition: 0.2s;
  }

  .balok-next:hover {
    background: #43a047;
    transform: scale(1.05);
  }
</style>
</head>
<body>

  <div class="balok-utama">
    <h2>HIIIII👋 Akhirnya kita ketemu lagi</h2>
    <p>Did anything feel a bit odd today?
       Feel free to share your story here. take ur time.
       </p>
  </div>

  <div class="balok-next" onclick="nextPage()">
    go there 
  </div>

<script>
  function nextPage() {
    window.location.href = "next.html";
  }
</script>

</body>
</html>
<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<title>Mood Tracker</title>

<style>
body {
    margin: 0;
    min-height: 100vh;
    font-family: Arial, sans-serif;
    background: linear-gradient(135deg, #c9bdff, #b9f3ff);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

/* BALOK UTAMA */
.container {
    background: #fdeeff;
    padding: 20px;
    border-radius: 18px;
    width: 500px;
    box-shadow: 0 10px 25px rgba(0,0,0,0.15);
    text-align: center;
}

h1 {
    margin-bottom: 10px;
}

.moods {
    display: flex;
    justify-content: space-between;
    margin: 20px 0;
}

.mood {
    font-size: 28px;
    cursor: pointer;
    transition: transform 0.2s;
}

.mood:hover {
    transform: scale(1.3);
}

button {
    margin-top: 10px;
    padding: 10px;
    width: 100%;
    border: none;
    border-radius: 10px;
    background: #4facfe;
    color: white;
    font-size: 14px;
    cursor: pointer;
}

button:hover {
    opacity: 0.9;
}

.history {
    margin-top: 20px;
    text-align: left;
}

.history ul {
    padding-left: 18px;
    max-height: 150px;
    overflow-y: auto;
}

/* TOMBOL NEXT PAGE (DI LUAR BALOK) */
.next-page {
    margin-top: 15px;
    width: 300px;
}

.next-page button {
    width: 100%;
    background: linear-gradient(135deg, #268bff, #89a7ff);
}
</style>
</head>

<body>

<div class="container">
    <h1>kalau kata malio,<br>kamu warna apa hari ini?</h1>
    <p>Choose your color today</p>

    <div class="moods">
        <span class="mood" onclick="selectMood('🟡 HAPPY')">🟡</span>
        <span class="mood" onclick="selectMood('🟢 NORMAL')">🟢</span>
        <span class="mood" onclick="selectMood('🔵 SAD')">🔵</span>
        <span class="mood" onclick="selectMood('🔴 MAD')">🔴</span>
        <span class="mood" onclick="selectMood('🟣 EXCITED')">🟣</span>
    </div>

    <p id="selectedMood">Haven't chosen a color yet</p>

    <button onclick="saveMood()">Save Mood</button>

    <div class="history">
        <h3>Mood History</h3>
        <ul id="moodList"></ul>
    </div>
</div>

<!-- TOMBOL DI BAWAH BALOK -->
<div class="next-page">
    <button onclick="nextPage()">Next</button>
</div>

<script>
let currentMood = "";

function selectMood(mood) {
    currentMood = mood;
    document.getElementById("selectedMood").innerText =
        "Mood hari ini: " + mood;
}

function saveMood() {
    if (!currentMood) {
        alert("Pilih mood dulu!");
        return;
    }

    const date = new Date().toLocaleDateString("id-ID");
    const moods = JSON.parse(localStorage.getItem("moods")) || [];

    moods.push({ date, mood: currentMood });
    localStorage.setItem("moods", JSON.stringify(moods));

    currentMood = "";
    document.getElementById("selectedMood").innerText =
        "Haven't chosen a color yet";
    loadMood();
}

function loadMood() {
    const moodList = document.getElementById("moodList");
    moodList.innerHTML = "";

    const moods = JSON.parse(localStorage.getItem("moods")) || [];
    moods.forEach(item => {
        const li = document.createElement("li");
        li.textContent = `${item.date} - ${item.mood}`;
        moodList.appendChild(li);
    });
}

function nextPage() {
    window.location.href = "page3.html";
}

loadMood();
</script>

</body>
</html>
<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Mood & Notes Calendar</title>

<style>
*{box-sizing:border-box;}
body{
    margin:0;
    font-family:"Poppins",sans-serif;
    background:linear-gradient(135deg,#e6ffca,#f7ffe1);
    min-height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
}
.app{
    background:#fff;
    width:100%;
    max-width:380px;
    padding:16px;
    border-radius:22px;
    box-shadow:0 15px 30px rgba(0,0,0,.2);
}

/* ===== INTRO / JUDUL ===== */
.intro{
    text-align:center;
    margin-bottom:14px;
}
.intro h1{
    font-size:18px;
    margin:0;
    font-weight:600;
}
.intro p{
    font-size:12px;
    margin-top:6px;
    color:#666;
    line-height:1.4;
}

/* ===== HEADER KALENDER ===== */
.header{
    display:flex;
    justify-content:space-between;
    align-items:center;
    margin-bottom:10px;
}
.header button{
    background:#a6c1ee;
    border:none;
    color:#fff;
    font-size:18px;
    padding:6px 12px;
    border-radius:10px;
}
.header h2{font-size:16px;}

/* ===== KALENDER ===== */
.days,.dates{
    display:grid;
    grid-template-columns:repeat(7,1fr);
    text-align:center;
}
.days div{
    font-size:11px;
    font-weight:600;
    color:#666;
}
.date{
    margin:4px;
    padding:10px 4px;
    border-radius:14px;
    background:#f1f1f1;
    font-size:13px;
    cursor:pointer;
    position:relative;
    transition:.2s;
}
.date:hover{transform:scale(1.05);}

/* WARNA MOOD */
.mood-happy{background:#b5ead7;}
.mood-normal{background:#fff1ac;}
.mood-sad{background:#81c8ef;}
.mood-angry{background:#ff9aa2;}
.mood-excited{background:#cdb4db;}

.note-preview{
    font-size:10px;
    opacity:.7;
    white-space:nowrap;
    overflow:hidden;
    text-overflow:ellipsis;
}
.mood-emoji{
    position:absolute;
    bottom:4px;
    right:6px;
    font-size:12px;
}

/* ===== MODAL ===== */
.modal{
    display:none;
    position:fixed;
    inset:0;
    background:rgba(0,0,0,.4);
    justify-content:center;
    align-items:center;
}
.modal-content{
    background:#fff;
    width:90%;
    max-width:320px;
    padding:16px;
    border-radius:18px;
}
.moods{
    display:flex;
    justify-content:space-between;
    font-size:26px;
    margin-bottom:8px;
}
.moods span{
    cursor:pointer;
    opacity:.4;
}
.moods span.active{
    opacity:1;
    transform:scale(1.2);
}
textarea{
    width:100%;
    height:90px;
    border-radius:12px;
    border:1px solid #ccc;
    padding:10px;
    resize:none;
}
.save-btn,.delete-btn{
    width:100%;
    margin-top:8px;
    padding:10px;
    border:none;
    border-radius:12px;
    color:#fff;
}
.save-btn{background:#a6c1ee;}
.delete-btn{background:#ff9aa2;font-size:13px;}
</style>
</head>

<body>

<div class="app">

    <!-- JUDUL & INSTRUKSI -->
    <div class="intro">
        <h1>Daily Mood & Notes</h1>
        <p>
            Klik tanggal untuk menulis catatan.<br>
             🌱
        </p>
    </div>

    <!-- HEADER KALENDER -->
    <div class="header">
        <button onclick="changeMonth(-1)">‹</button>
        <h2 id="monthYear"></h2>
        <button onclick="changeMonth(1)">›</button>
    </div>

    <!-- NAMA HARI -->
    <div class="days">
        <div>Min</div><div>Sen</div><div>Sel</div>
        <div>Rab</div><div>Kam</div><div>Jum</div><div>Sab</div>
    </div>

    <!-- TANGGAL -->
    <div class="dates" id="dates"></div>
</div>

<!-- MODAL -->
<div class="modal" id="modal">
    <div class="modal-content">
        <div class="moods">
            <span onclick="pickMood('😊','happy')">😊</span>
            <span onclick="pickMood('😐','normal')">😐</span>
            <span onclick="pickMood('😢','sad')">😢</span>
            <span onclick="pickMood('😡','angry')">😡</span>
            <span onclick="pickMood('🤩','excited')">🤩</span>
        </div>
        <textarea id="note" placeholder="Tulis catatan... (mood opsional)"></textarea>
        <button class="save-btn" onclick="saveData()">Simpan</button>
        <button class="delete-btn" onclick="deleteData()">Hapus</button>
    </div>
</div>

<script>
let current=new Date();
let selectedKey="";
let selectedMood={emoji:"",class:""};

function renderCalendar(){
    const dates=document.getElementById("dates");
    dates.innerHTML="";
    const y=current.getFullYear();
    const m=current.getMonth();
    document.getElementById("monthYear").innerText=
        current.toLocaleDateString("id-ID",{month:"long",year:"numeric"});

    const firstDay=new Date(y,m,1).getDay();
    const total=new Date(y,m+1,0).getDate();
    const data=JSON.parse(localStorage.getItem("moodNotes"))||{};

    for(let i=0;i<firstDay;i++) dates.innerHTML+="<div></div>";

    for(let d=1;d<=total;d++){
        const key=`${y}-${m}-${d}`;
        const div=document.createElement("div");
        div.className="date";

        const day=document.createElement("div");
        day.innerText=d;
        div.appendChild(day);

        if(data[key]){
            if(data[key].moodClass){
                div.classList.add("mood-"+data[key].moodClass);
            }
            if(data[key].note){
                const preview=document.createElement("div");
                preview.className="note-preview";
                preview.innerText=data[key].note;
                div.appendChild(preview);
            }
            if(data[key].mood){
                const emoji=document.createElement("div");
                emoji.className="mood-emoji";
                emoji.innerText=data[key].mood;
                div.appendChild(emoji);
            }
        }

        div.onclick=()=>openModal(key);
        dates.appendChild(div);
    }
}

function changeMonth(step){
    current.setMonth(current.getMonth()+step);
    renderCalendar();
}

function openModal(key){
    selectedKey=key;
    selectedMood={emoji:"",class:""};
    document.querySelectorAll(".moods span").forEach(s=>s.classList.remove("active"));

    const data=JSON.parse(localStorage.getItem("moodNotes"))||{};
    document.getElementById("note").value=data[key]?.note||"";

    if(data[key]?.mood){
        selectedMood.emoji=data[key].mood;
        selectedMood.class=data[key].moodClass;
        document.querySelectorAll(".moods span").forEach(s=>{
            if(s.innerText===selectedMood.emoji) s.classList.add("active");
        });
    }
    document.getElementById("modal").style.display="flex";
}

function pickMood(emoji,cls){
    selectedMood={emoji, class:cls};
    document.querySelectorAll(".moods span").forEach(s=>{
        s.classList.toggle("active",s.innerText===emoji);
    });
}

function saveData(){
    const note=document.getElementById("note").value.trim();
    if(!note && !selectedMood.emoji){
        document.getElementById("modal").style.display="none";
        return;
    }
    const data=JSON.parse(localStorage.getItem("moodNotes"))||{};
    data[selectedKey]={
        note,
        mood:selectedMood.emoji,
        moodClass:selectedMood.class
    };
    localStorage.setItem("moodNotes",JSON.stringify(data));
    document.getElementById("modal").style.display="none";
    renderCalendar();
}

function deleteData(){
    const data=JSON.parse(localStorage.getItem("moodNotes"))||{};
    delete data[selectedKey];
    localStorage.setItem("moodNotes",JSON.stringify(data));
    document.getElementById("modal").style.display="none";
    renderCalendar();
}

renderCalendar();
</script>

</body>
</html>
