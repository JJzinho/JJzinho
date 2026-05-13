<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bug Hunter</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    overflow:hidden;
    background:#0f172a;
    font-family:Arial;
}

canvas{
    display:block;
}

#score{
    position:absolute;
    top:20px;
    left:20px;
    color:white;
    font-size:24px;
    z-index:10;
}

#title{
    position:absolute;
    top:20px;
    right:20px;
    color:#38bdf8;
    font-size:22px;
    font-weight:bold;
}
</style>
</head>
<body>

<div id="score">Score: 0</div>
<div id="title">🐞 Bug Hunter</div>

<canvas id="game"></canvas>

<script>
const canvas = document.getElementById("game");
const ctx = canvas.getContext("2d");

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let player = {
    x: canvas.width / 2 - 40,
    y: canvas.height - 80,
    width: 80,
    height: 20,
    speed: 8
};

let keys = {};
let bugs = [];
let score = 0;

document.addEventListener("keydown", e => {
    keys[e.key] = true;
});

document.addEventListener("keyup", e => {
    keys[e.key] = false;
});

function spawnBug(){
    bugs.push({
        x: Math.random() * (canvas.width - 40),
        y: -40,
        size: 40,
        speed: 2 + Math.random() * 4
    });
}

setInterval(spawnBug, 700);

function update(){

    if(keys["ArrowLeft"] || keys["a"]){
        player.x -= player.speed;
    }

    if(keys["ArrowRight"] || keys["d"]){
        player.x += player.speed;
    }

    if(player.x < 0) player.x = 0;
    if(player.x + player.width > canvas.width){
        player.x = canvas.width - player.width;
    }

    bugs.forEach((bug, index) => {
        bug.y += bug.speed;

        if(
            bug.y + bug.size > player.y &&
            bug.x < player.x + player.width &&
            bug.x + bug.size > player.x
        ){
            bugs.splice(index,1);
            score++;
            document.getElementById("score").innerText =
            "Score: " + score;
        }

        if(bug.y > canvas.height){
            bugs.splice(index,1);
        }
    });
}

function draw(){

    ctx.clearRect(0,0,canvas.width,canvas.height);

    ctx.fillStyle = "#38bdf8";
    ctx.fillRect(
        player.x,
        player.y,
        player.width,
        player.height
    );

    bugs.forEach(bug => {
        ctx.font = "35px Arial";
        ctx.fillText("🐞", bug.x, bug.y);
    });
}

function gameLoop(){
    update();
    draw();
    requestAnimationFrame(gameLoop);
}

gameLoop();
</script>

</body>
</html>

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:0f172a,100:2563eb&height=180&section=header&text=Joan%20Antônio&fontSize=42&fontColor=ffffff&animation=fadeIn&fontAlignY=35"/>

<div align="center">

# 👋 Olá, eu sou o Joan Antônio

### Desenvolvedor focado em RPA, Automação com IA e Sistemas Web

💻 Python | JavaScript | Node.js | React | SQL | FastAPI  
🤖 RPA | Selenium | Automações Empresariais | IA aplicada a processos  
🏢 Criando soluções para otimizar rotinas comerciais, financeiras e operacionais

</div>

---

## 🚀 Sobre mim

Sou desenvolvedor com foco em **automação de processos**, **RPA**, **sistemas internos** e **integrações com IA**.

Gosto de criar soluções que reduzem trabalho manual, organizam dados e ajudam empresas a ganhar produtividade.

Atualmente trabalho com projetos envolvendo:

- Robôs com Selenium
- Automação de planilhas Excel
- Integrações com APIs
- Sistemas com FastAPI
- Interfaces web com React
- Automações com Outlook e WhatsApp
- Organização financeira e documental
- Inteligência artificial aplicada a processos internos

---

## 🧠 Tecnologias que uso

<div align="center">

<img src="https://skillicons.dev/icons?i=python,java,javascript,nodejs,react,html,css,fastapi,mysql,postgres,git,github,vscode" />

</div>

---

## 🔥 Principais áreas

```txt
RPA
Automação com IA
Python
Selenium
FastAPI
React
Node.js
SQL
Excel Automation
APIs
Back-end
Sistemas internos
