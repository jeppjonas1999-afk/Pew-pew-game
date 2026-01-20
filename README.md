<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Sandbox Assault Shooter</title>
<style>
body {
   margin: 0;
   background: #111;
   color: white;
   font-family: Arial, sans-serif;
   text-align: center;
}

#ui {
   padding: 10px;
   background: #222;
   display: flex;
   justify-content: space-around;
   flex-wrap: wrap;
}

canvas {
   background: #000;
   display: block;
   margin: auto;
   border: 2px solid #444;
}

/* SHOP */
#shop {
   position: fixed;
   top: 0; left: 0;
   width: 100%; height: 100%;
   background: rgba(0,0,0,0.9);
   display: none;
   flex-direction: column;
   justify-content: center;
   align-items: center;
   z-index: 10;
}

.shop-btn {
   margin: 10px;
   padding: 12px 20px;
   background: #333;
   color: white;
   border: 1px solid #777;
   cursor: pointer;
}

.shop-btn:hover {
   background: #555;
}
</style>
</head>
<body>

<div id="ui">
   <div>Health: <span id="health">100</span></div>
   <div>Weapon: <span id="weapon">Pistol</span></div>
   <div>Score: <span id="score">0</span></div>
   <div>Wave: <span id="wave">0</span></div>
</div>

<div id="shop">
   <h1>SHOP</h1>
   <button class="shop-btn" onclick="buyWeapon('SMG')">
       Buy SMG (300) | Stacks: <span id="smgStacks">0</span>
   </button>
   <button class="shop-btn" onclick="buyWeapon('Shotgun')">
       Buy Shotgun (450) | Stacks: <span id="shotgunStacks">0</span>
   </button>
   <button class="shop-btn" onclick="closeShop()">Continue</button>
</div>

<canvas id="game" width="800" height="500"></canvas>

<script>
const canvas = document.getElementById("game");
const ctx = canvas.getContext("2d");

let health = 100;
let score = 0;
let wave = 0;
let shopOpen
