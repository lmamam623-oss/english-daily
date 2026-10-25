<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>كلمة إنجليزية كل يوم</title>
<style>
body{font-family:sans-serif;background:#f4f6fb;margin:0;padding:20px}
.card{background:#fff;padding:20px;border-radius:16px;max-width:500px;margin:auto;box-shadow:0 4px 14px rgba(0,0,0,.08)}
h1{font-size:22px}
.word{font-size:32px;font-weight:bold;color:#1a73e8}
button{padding:10px 16px;border:none;border-radius:10px;margin:6px;cursor:pointer}
.know{background:#16a34a;color:#fff}
.dont{background:#ef4444;color:#fff}
</style>
</head>
<body>
<div class="card">
<h1>كلمة اليوم</h1>
<div id="app">جارٍ التحميل...</div>
</div>

<script>
const words=[
{en:"improve",ar:"يُحسّن",example:"I want to improve my English."},
{en:"important",ar:"مهم",example:"Practice is important."},
{en:"remember",ar:"يتذكر",example:"I remember this word."},
{en:"practice",ar:"يتدرب",example:"I practice English every day."},
{en:"learn",ar:"يتعلم",example:"I learn five words daily."}
];

let i=0;
const app=document.getElementById("app");

function show(){
if(i>=words.length){app.innerHTML="<p>أحسنت! أنهيت كلمات اليوم 🎉</p>";return}
const w=words[i];
app.innerHTML=`<p class="word">${w.en}</p><p>${w.ar}</p><p><em>${w.example}</em></p>
<button class="know" onclick="answer(true)">أعرفها</button>
<button class="dont" onclick="answer(false)">لا أعرفها</button>`;
}

function answer(k){
const w=words[i];
const s=JSON.parse(localStorage.getItem("words")||"{}");
s[w.en]=k?"known":"review";
localStorage.setItem("words",JSON.stringify(s));
i++;show();
}

show();
</script>
</body>
</html>
