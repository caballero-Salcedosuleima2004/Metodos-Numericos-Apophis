# 🛰️ Simulador Orbital Interactivo

Este simulador permite modificar los parámetros orbitales del asteroide Apophis y observar cómo el método de Newton-Raphson corrige la órbita en tiempo real.

---

<div style="
display:flex;
gap:20px;
flex-wrap:wrap;
align-items:flex-start;
margin-top:25px;
">

<!-- PANEL IZQUIERDO -->
<div style="
flex:1;
min-width:280px;
background:rgba(10,15,30,0.75);
backdrop-filter:blur(10px);
padding:20px;
border-radius:18px;
border:1px solid rgba(0,229,255,0.15);
box-shadow:0 0 20px rgba(0,229,255,0.08);
">

<h3 style="margin-top:0;color:#67e8f9;">
⚙️ Parámetros Orbitales
</h3>

<div style="margin-bottom:16px;">

<label>Excentricidad Orbital (e)</label>

<input type="range"
id="slider-e"
min="0.05"
max="0.5"
step="0.0001"
value="0.19116634"
style="width:100%;">

<div id="val-e" style="margin-top:5px;color:#4ade80;">
0.19116634
</div>

</div>

<div style="margin-bottom:16px;">

<label>Semieje Mayor (a)</label>

<input type="range"
id="slider-a"
min="0.5"
max="2.0"
step="0.0001"
value="0.92238032"
style="width:100%;">

<div id="val-a" style="margin-top:5px;color:#4ade80;">
0.92238032 UA
</div>

</div>

<div style="margin-bottom:16px;">

<label>Anomalía Media (M)</label>

<input type="range"
id="slider-M"
min="0.1"
max="6.2"
step="0.0001"
value="5.4595"
style="width:100%;">

<div id="val-M" style="margin-top:5px;color:#4ade80;">
5.4595 rad
</div>

</div>

<hr style="border-color:rgba(255,255,255,0.08);margin:20px 0;">

<h3 style="color:#67e8f9;">
📊 Resultados Numéricos
</h3>

<table style="
width:100%;
border-collapse:collapse;
font-size:0.95rem;
">

<tr>
<td style="padding:10px;">Anomalía Excéntrica</td>
<td>
<span id="res-E"
style="color:#4ade80;font-family:monospace;">
-
</span>
</td>
</tr>

<tr>
<td style="padding:10px;">Radio Orbital</td>
<td>
<span id="res-r"
style="color:#4ade80;font-family:monospace;">
-
</span>
</td>
</tr>

<tr>
<td style="padding:10px;">Iteraciones</td>
<td>
<span id="res-iter"
style="color:#facc15;font-family:monospace;">
-
</span>
</td>
</tr>

<tr>
<td style="padding:10px;">Estado</td>
<td id="estadoMetodo"
style="color:#4ade80;">
● Convergencia Exitosa
</td>
</tr>

</table>

</div>

<!-- PANEL DERECHO -->
<div style="
flex:1.4;
min-width:340px;
background:rgba(10,15,30,0.75);
backdrop-filter:blur(10px);
padding:20px;
border-radius:18px;
border:1px solid rgba(0,229,255,0.15);
box-shadow:0 0 20px rgba(0,229,255,0.08);
">

<h3 style="margin-top:0;color:#67e8f9;">
🌌 Simulación Orbital
</h3>

<canvas id="orbitaCanvas"
width="700"
height="400"
style="
width:100%;
background:black;
border-radius:14px;
border:1px solid rgba(0,229,255,0.2);
">
</canvas>

<hr style="margin:20px 0;border-color:rgba(255,255,255,0.08);">

<h3 style="color:#67e8f9;">
📉 Convergencia del Error
</h3>

<div class="chart-container">
<canvas id="graficaError"></canvas>
</div>

</div>

</div>

---

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<script>

let grafica;

function simularNewtonRaphson(){

    let e = parseFloat(document.getElementById('slider-e').value);

    let a = parseFloat(document.getElementById('slider-a').value);

    let M = parseFloat(document.getElementById('slider-M').value);

    document.getElementById('val-e').innerText = e.toFixed(8);

    document.getElementById('val-a').innerText = a.toFixed(8) + " UA";

    document.getElementById('val-M').innerText = M.toFixed(4) + " rad";

    /* =========================================
       VALORES INICIALES
       ========================================= */

    let E = 5.4;

    let r = 0.80;

    let tolerancia = 1e-6;

    let error = 1.0;

    let iteracion = 0;

    let maxIter = 100;

    let errores = [];

    let iteraciones = [];

    /* =========================================
       METODO NEWTON-RAPHSON
       ========================================= */

    while(error > tolerancia && iteracion < maxIter){

        let f1 = E - e * Math.sin(E) - M;

        let f2 = r - a * (1 - e * Math.cos(E));

        let J11 = 1 - e * Math.cos(E);

        let J12 = 0;

        let J21 = -a * e * Math.sin(E);

        let J22 = 1;

        let det = (J11 * J22) - (J12 * J21);

        let inv11 = J22 / det;

        let inv12 = -J12 / det;

        let inv21 = -J21 / det;

        let inv22 = J11 / det;

        let deltaE = inv11 * f1 + inv12 * f2;

        let deltar = inv21 * f1 + inv22 * f2;

        E = E - deltaE;

        r = r - deltar;

        error = Math.sqrt((f1*f1)+(f2*f2));

        errores.push(error);

        iteraciones.push(iteracion + 1);

        iteracion++;
    }

    /* =========================================
       RESULTADOS
       ========================================= */

    document.getElementById('res-E').innerText = E.toFixed(10);

    document.getElementById('res-r').innerText = r.toFixed(10);

    document.getElementById('res-iter').innerText = iteracion;

    actualizarGrafica(iteraciones, errores);

    dibujarOrbita(a,e,E,r);
}

function actualizarGrafica(iteraciones, errores){

    const ctx = document.getElementById('graficaError').getContext('2d');

    if(grafica){
        grafica.destroy();
    }

    grafica = new Chart(ctx, {

        type:'line',

        data:{

            labels:iteraciones,

            datasets:[{

                label:'Error Numérico',

                data:errores,

                borderColor:'#00e5ff',

                backgroundColor:'rgba(0,229,255,0.15)',

                borderWidth:3,

                tension:0.25,

                fill:true,

                pointRadius:4
            }]
        },

        options:{

            responsive:true,

            plugins:{
                legend:{
                    labels:{
                        color:'#ffffff'
                    }
                }
            },

            scales:{

                x:{
                    title:{
                        display:true,
                        text:'Iteración',
                        color:'#ffffff'
                    },

                    ticks:{
                        color:'#ffffff'
                    }
                },

                y:{
                    title:{
                        display:true,
                        text:'Error',
                        color:'#ffffff'
                    },

                    ticks:{
                        color:'#ffffff'
                    }
                }
            }
        }
    });
}

function dibujarOrbita(a,e,E,r){

    const canvas = document.getElementById("orbitaCanvas");

    const ctx = canvas.getContext("2d");

    ctx.clearRect(0,0,canvas.width,canvas.height);

    const cx = canvas.width/2;

    const cy = canvas.height/2;

    const escala = 140;

    const b = a * Math.sqrt(1 - e*e);

    /* =========================================
       FONDO ESTRELLAS
       ========================================= */

    for(let i=0;i<70;i++){

        ctx.fillStyle = "white";

        ctx.globalAlpha = Math.random();

        ctx.fillRect(
            Math.random()*canvas.width,
            Math.random()*canvas.height,
            1.5,
            1.5
        );
    }

    ctx.globalAlpha = 1;

    /* =========================================
       ORBITA
       ========================================= */

    ctx.strokeStyle = "#00e5ff";

    ctx.lineWidth = 2;

    ctx.beginPath();

    for(let t=0;t<2*Math.PI;t+=0.01){

        let x = a*Math.cos(t);

        let y = b*Math.sin(t);

        x *= escala;

        y *= escala;

        if(t===0)
            ctx.moveTo(cx+x, cy+y);
        else
            ctx.lineTo(cx+x, cy+y);
    }

    ctx.stroke();

    /* =========================================
       SOL
       ========================================= */

    let solX = cx - a*e*escala;

    let solY = cy;

    const gradienteSol = ctx.createRadialGradient(
        solX,solY,2,
        solX,solY,20
    );

    gradienteSol.addColorStop(0,"#fff7ae");
    gradienteSol.addColorStop(1,"#facc15");

    ctx.fillStyle = gradienteSol;

    ctx.beginPath();

    ctx.arc(solX, solY, 12, 0, 2*Math.PI);

    ctx.fill();

    /* =========================================
       ASTEROIDE
       ========================================= */

    let xAst = a*(Math.cos(E)-e);

    let yAst = b*Math.sin(E);

    xAst *= escala;

    yAst *= escala;

    ctx.fillStyle = "#ef4444";

    ctx.beginPath();

    ctx.arc(cx+xAst, cy+yAst, 7, 0, 2*Math.PI);

    ctx.fill();

    /* =========================================
       LINEA RADIO VECTOR
       ========================================= */

    ctx.strokeStyle = "rgba(255,255,255,0.35)";

    ctx.lineWidth = 1.5;

    ctx.beginPath();

    ctx.moveTo(solX, solY);

    ctx.lineTo(cx+xAst, cy+yAst);

    ctx.stroke();

    /* =========================================
       TEXTO
       ========================================= */

    ctx.fillStyle = "#67e8f9";

    ctx.font = "14px monospace";

    ctx.fillText("Apophis", cx+xAst+10, cy+yAst);

    ctx.fillStyle = "#facc15";

    ctx.fillText("Sol", solX+14, solY);
}

document.getElementById('slider-e')
.addEventListener('input', simularNewtonRaphson);

document.getElementById('slider-a')
.addEventListener('input', simularNewtonRaphson);

document.getElementById('slider-M')
.addEventListener('input', simularNewtonRaphson);

simularNewtonRaphson();

</script>