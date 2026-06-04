<!DOCTYPE html>
<html>
<head>
<title>Carrying Capacity Simulator</title>

<style>
body{
font-family:Arial;
margin:20px;
}

.slider{
width:300px;
}

.panel{
border:1px solid black;
padding:10px;
margin:10px;
}
</style>
</head>

<body>

<h1>Biome Carrying Capacity Simulator</h1>

<div class="panel">

Food:
<input type="range" id="food" min="0" max="100" value="80">

<br><br>

Water:
<input type="range" id="water" min="0" max="100" value="80">

<br><br>

Space:
<input type="range" id="space" min="0" max="100" value="80">

<br><br>

Weather:
<input type="range" id="weather" min="0" max="100" value="80">

<br><br>

Predators:
<input type="range" id="predators" min="0" max="100" value="20">

<br><br>

Disease:
<input type="range" id="disease" min="0" max="100" value="10">

</div>

<div class="panel">
Population:
<span id="population">50</span>

<br>

Carrying Capacity:
<span id="capacity">160</span>

</div>

<button onclick="runSimulation()">
Run One Year
</button>

<script>

let population = 50;

function runSimulation(){

let food =
Number(document.getElementById("food").value);

let water =
Number(document.getElementById("water").value);

let space =
Number(document.getElementById("space").value);

let weather =
Number(document.getElementById("weather").value);

let predators =
Number(document.getElementById("predators").value);

let disease =
Number(document.getElementById("disease").value);

let carryingCapacity =
((food + water + space + weather)/4)*2;

let birthRate =
10 - predators/20;

let deathRate =
5 + disease/10 + predators/20;

if(population < carryingCapacity){

population += birthRate;

}else{

population -= deathRate;

}

population =
Math.max(0,Math.round(population));

document.getElementById("population")
.innerText = population;

document.getElementById("capacity")
.innerText = Math.round(carryingCapacity);

}

</script>

</body>
</html>
