# projeto-jogo-da-velha
criando um Jogo divertido e mais famoso do mundo, o jogo da velha!

/////////CÓDIGO HTML/////////

<!DOCTYPE html>
<html lang="pt-br">
<head>
   <title>
       Jogo da Velha
   </title>
   <meta charset="UTF-8">
   <link rel="stylesheet" href="estilo.css">
</head>

<body>
<h1>
     Jogo da Velha
</h1>
<div>
     <div id="1" class="quadrado" onclick="escolherquadrado(this.id)">-</div>
     <div id="2" class="quadrado" onclick="escolherquadrado(this.id)">-</div>
     <div id="3" class="quadrado" onclick="escolherquadrado(this.id)">-</div>
</div>

<div>
    <div id="4" class="quadrado" onclick="escolherquadrado(this.id)">-</div>
    <div id="5" class="quadrado" onclick="escolherquadrado(this.id)">-</div>
    <div id="6" class="quadrado" onclick="escolherquadrado(this.id)">-</div>
</div>

<div>
    <div id="7" class="quadrado" onclick="escolherquadrado(this.id)">-</div>
    <div id="8" class="quadrado" onclick="escolherquadrado(this.id)">-</div>
    <div id="9" class="quadrado" onclick="escolherquadrado(this.id)">-</div>
</div>

<div class="jogador">
    <label>
        Jogador:
    </label>
    <label id="jogadorselecionado">

    </label>
</div>

<div class="vencedor">
    <label>
        Vencedor:
    </label>
    <label id="jogadorvencedor">

    </label>
</div>

<div>
    <button onclick="reiniciar()">
        Reiniciar
    </button>
</div>
</body>
<script src="velha.js"></script>
</html>


////////Código CSS/////////

body{
    text-align: center;
}

.quadrado{
    text-align: center;
    width: 58px;
    background: #eee;
    display: inline-block;
    padding: 48px;
    font-size: 68px;
    margin: 5px;
    cursor: pointer;
    color: #eee;
}

.jogador, .vencedor{
    font-size: 30px;
    margin-top: 10px;
}

button{
    margin-top: 10px;
    width: 100px;
    height: 30px;
    background: #eee;
    cursor: pointer;
}

///////// Código Javascript/////

var jogador, vencedor = null;
var jogadorselecionado = document.getElementById('jogador-selecionado');
var jogadorvencedor = document.getElementById('jogador-vencedor');
var quadrados = document.getElementsByClassName('quadrado');

mudarjogador('x');


function escolherquadrado(id){
    if(vencedor !== null) {
        return;
    }

    var quadrado = document.getElementById(id);
    if(quadrado.innerHTML !== '-') {
        return;
    }

    quadrado.innerHTML = jogador;
    quadrado.style.color = '#000' ;
    
    if(jogador === 'x') {
        jogador = '0';

    }else{
        jogador = 'x';
    }
    mudarjogador(jogador);
    checavencedor();

}

function mudarjogador(valor) {
    jogador = valor;
    jogadorselecionado.innerHTML = jogador;
}

function checavencedor() {
    var quadrado1 = document.getElementById(1);
    var quadrado2 = document.getElementById(2);
    var quadrado3 = document.getElementById(3);
    var quadrado4 = document.getElementById(4);
    var quadrado5 = document.getElementById(5);
    var quadrado6 = document.getElementById(6);
    var quadrado7 = document.getElementById(7);
    var quadrado8 = document.getElementById(8);
    var quadrado9 = document.getElementById(9);

    if(checasequencia(quadrado1,quadrado2,quadrado3)) {
        mudacorquadrado(quadrado1, quadrado2, quadrado3);
        mudavencedor(quadrado1);
        return;
    }

    if(checasequencia(quadrado4,quadrado5,quadrado6)) {
        mudacorquadrado(quadrado4, quadrado5, quadrado6);
        mudavencedor(quadrado4);
        return;
    }

    if(checasequencia(quadrado7,quadrado8,quadrado9)) {
        mudacorquadrado(quadrado7,quadrado8,quadrado9);
        mudavencedor(quadrado7);
        return;

    }
    
    if(checasequencia(quadrado1,quadrado4,quadrado7)) {
        mudacorquadrado(quadrado1, quadrado4, quadrado7);
        mudavencedor(quadrado4);
        return;
    }

    if(checasequencia(quadrado2,quadrado5,quadrado8)) {
        mudacorquadrado(quadrado2,quadrado5,quadrado8);
        mudavencedor(quadrado2);
        return;
    }

    if(checasequencia(quadrado3,quadrado6,quadrado9)) {
        mudacorquadrado(quadrado3,quadrado6,quadrado9);
        mudavencedor(quadrado3);
        return;
    }

    if(checasequencia(quadrado1,quadrado5,quadrado9)) {
        mudacorquadrado(quadrado1,quadrado5,quadrado9);
        mudavencedor(quadrado1);
        return;
    }

    if(checasequencia(quadrado3,quadrado5,quadrado7)) {
        mudacorquadrado(quadrado3,quadrado5,quadrado7);
        mudavencedor(quadrado3);
        return;
    }  

}


function mudavencedor(quadrado) {
    vencedor = quadrado.innerHTML;
    jogadorselecionado.innerHTML = vencedor;


}

function mudacorquadrado(quadrado1, quadrado2, quadrado3) {
    quadrado1.style.background = '#0f0' ;
    quadrado2.style.background = '#0f0' ;
    quadrado3.style.background = '#0f0' ;
}

function checasequencia(quadrado1, quadrado2, quadrado3) {
    var eiqual = false;
    if(quadrado1.innerHTML !== '-' && quadrado1.innerHTML === quadrado2.innerHTML && quadrado2.innerHTML === quadrado3.innerHTML){
        eiqual = true;
    }
 return eiqual;
}

function reiniciar() {
    vencedor = null;
    vencedorselecionado.innerHTML =  '';

    for(var i = 1; i <= 9; i++) {
        var quadrado = document.getElementById(i);
        quadrado.style.background = '#eee';
        quadrado.style.color = '#eee';
        quadrado.innerHTML = '-';

    }
    mudarjogador('x');
}


///////////////////

