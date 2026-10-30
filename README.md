[PHARMA_FACTORY_Survival_Mantenimiento_Consecuencias.html](https://github.com/user-attachments/files/34199957/PHARMA_FACTORY_Survival_Mantenimiento_Consecuencias.html)
<!doctype html>
<html lang="es">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>PHARMA FACTORY · Survival de mantenimiento</title>
<style>
:root{--bg:#061522;--panel:#0d263b;--panel2:#102f47;--line:#315b75;--cyan:#62ddec;--green:#55d99d;--yellow:#ffd166;--red:#ff737d;--txt:#edf7ff;--muted:#aac2d3}
*{box-sizing:border-box}
body{margin:0;background:radial-gradient(circle at 50% 0,#172a35,#03090f 72%);color:var(--txt);font-family:system-ui,Segoe UI,Arial,sans-serif}
header{display:flex;align-items:center;justify-content:space-between;gap:12px;padding:12px 20px;background:#04111ddd;border-bottom:1px solid #31516a;position:sticky;top:0;z-index:3}
.brand{font-size:22px;font-weight:950;letter-spacing:1.4px}.brand span{color:var(--cyan)}.sub{font-size:11px;letter-spacing:1.2px;color:var(--muted)}
header .chip,.chip{border:1px solid #416780;background:#071a29;color:#e7f7ff;border-radius:24px;padding:7px 11px;font-size:12px;font-weight:800}
main{max-width:1460px;margin:auto;padding:16px}
.grid{display:grid;grid-template-columns:minmax(0,1fr) 310px;gap:14px}
.panel{background:linear-gradient(145deg,#15242e,#07131d);border:1px solid #3a505c;border-radius:16px;padding:14px;box-shadow:0 14px 34px #0008}
.gamehead{display:flex;justify-content:space-between;align-items:center;gap:10px;flex-wrap:wrap;margin-bottom:10px}
h1{font-size:clamp(22px,3vw,34px);margin:4px 0}h2{font-size:18px;margin:2px 0 10px}h3{font-size:14px;margin:4px 0}
p{color:#c8dce9;line-height:1.48}.muted{color:var(--muted);font-size:12px;line-height:1.45}
.view{position:relative;border:1px solid #52616a;border-radius:14px;overflow:hidden;background:#02070b;box-shadow:inset 0 0 70px #000}
canvas{display:block;width:100%;height:auto;aspect-ratio:960/560;touch-action:none}
.hud{position:absolute;left:12px;right:12px;top:12px;display:flex;gap:7px;flex-wrap:wrap;pointer-events:none}
.hud .chip{backdrop-filter:blur(5px);background:#061521dd}
.centerMark{position:absolute;left:50%;top:50%;width:17px;height:17px;transform:translate(-50%,-50%);pointer-events:none}
.centerMark:before,.centerMark:after{content:"";position:absolute;background:#eaffff;box-shadow:0 0 5px #0b1b24}
.centerMark:before{width:2px;height:17px;left:7px;top:0}.centerMark:after{height:2px;width:17px;top:7px;left:0}
.viewPrompt{position:absolute;bottom:12px;left:50%;transform:translateX(-50%);background:#03111deF;border:1px solid #4c819b;border-radius:12px;padding:9px 14px;font-size:13px;font-weight:850;text-align:center;max-width:90%;width:max-content}
.alertBanner{display:none;position:absolute;top:66px;left:50%;transform:translateX(-50%);background:#5b1019ed;border:1px solid #ff5362;color:white;border-radius:10px;padding:9px 14px;font-weight:950;letter-spacing:1px;animation:blink .55s infinite;box-shadow:0 0 28px #ff263655}
.alertBanner.show{display:block}@keyframes blink{50%{opacity:.48}}
.controls{display:flex;gap:8px;flex-wrap:wrap;align-items:center;margin-top:12px}
button{border:0;border-radius:10px;padding:10px 13px;background:var(--cyan);color:#052033;font-weight:900;font-size:13px;cursor:pointer;transition:filter .15s,transform .15s}
button:hover{filter:brightness(1.1);transform:translateY(-1px)}button:disabled{opacity:.4;cursor:not-allowed;transform:none}
button.secondary{background:#244a64;color:#f0f8ff;border:1px solid #4c7188}
button.danger{background:#7b303b;color:white;border:1px solid #b85a63}
.dpad{display:grid;grid-template-columns:repeat(3,58px);grid-template-rows:repeat(2,42px);gap:5px}
.dpad button{padding:5px;font-size:16px}
.dpad .up{grid-column:2}.dpad .left{grid-column:1;grid-row:2}.dpad .down{grid-column:2;grid-row:2}.dpad .right{grid-column:3;grid-row:2}
.ctrlrow{display:flex;justify-content:space-between;align-items:center;gap:12px;flex-wrap:wrap}
.notice{background:#0b1a24;border:1px solid #435864;border-radius:11px;padding:11px;margin-top:10px;font-size:13px;color:#d9edf8;min-height:52px}
.task{padding:9px 10px;border:1px solid #31546c;border-radius:10px;background:#091f31;margin:7px 0}
.stateBox{margin-top:12px;background:#07131d;border:1px solid #354c59;border-radius:11px;padding:11px}
.stateLabel{display:flex;justify-content:space-between;gap:8px;font-size:12px;color:#c6d6df}
.stateLabel b{color:#fff;font-variant-numeric:tabular-nums}
.meter{height:8px;background:#24343e;border-radius:8px;overflow:hidden;margin-top:5px}
.meter i{display:block;height:100%;width:28%;background:#e6b54e;transition:width .3s,background .3s}
.logBox{display:flex;flex-direction:column;gap:6px;max-height:170px;overflow:auto}
.logEntry{font-size:11px;line-height:1.4;padding:8px;border-radius:8px;background:#081822;border-left:3px solid #6b8490;color:#c9dbe4}
.logEntry.goodLog{border-left-color:#55d99d}.logEntry.badLog{border-left-color:#ff737d}
#riskChip{border-color:#b68d4b}#lotChip{border-color:#4d8d7e}
#alertBanner.show{box-shadow:0 0 35px #ff233b99}

.task.active{border-color:var(--cyan);box-shadow:0 0 0 1px #62ddec55 inset}
.task.done{background:#10372f;border-color:#33896c}
.task strong{display:block;font-size:12px}.task small{color:var(--muted);font-size:11px}
.kpis{display:grid;grid-template-columns:1fr 1fr;gap:7px}
.kpi{padding:9px;border-radius:10px;background:#081b2c;border:1px solid #294c64}
.dashboard-modal{width:min(980px,100%);max-height:92vh;overflow:auto}
.dash-explain{display:grid;grid-template-columns:1fr 1fr;gap:9px;margin-top:12px}\n.endingPanel{border:1px solid #4a6472;border-radius:12px;padding:13px;margin:12px 0;background:#0a1b26}\n.endingPanel strong{font-size:18px}\n.endingPanel p{font-size:13px;margin:6px 0}
.explain-card{background:#081b2c;border:1px solid #31566e;border-radius:12px;padding:12px}
.explain-card h3{font-size:14px;margin:0 0 7px;color:#e9f7ff}
.explain-card p{font-size:12px;line-height:1.5;margin:5px 0;color:#c8dce9}
.explain-card b{color:#fff}
.explain-card .meaning{color:#9fc3d6}
@media(max-width:640px){.dash-explain{grid-template-columns:1fr}.dashboard-modal{padding:13px}}

.kpi span{display:block;font-size:10px;color:var(--muted)}.kpi b{display:block;font-size:20px;margin:3px 0}
.good{color:var(--green)}.warn{color:var(--yellow)}.bad{color:var(--red)}
.pulse{color:#ff8e96}
.toast{position:fixed;right:18px;top:78px;z-index:15;max-width:360px;background:#10354a;border:1px solid var(--cyan);border-left:5px solid var(--cyan);padding:13px 15px;border-radius:12px;box-shadow:0 12px 35px #0009;display:none}
.toast.show{display:block;animation:pop .2s ease-out}.toast.danger{background:#4c202a;border-color:var(--red);border-left-color:var(--red)}
@keyframes pop{from{transform:translateX(20px);opacity:0}to{transform:none;opacity:1}}
.overlay{position:fixed;inset:0;background:#020910eF;display:flex;align-items:center;justify-content:center;padding:16px;z-index:20;overflow:auto}
.modal{width:min(680px,100%);background:linear-gradient(145deg,#12334b,#0a2032);border:1px solid #4b7b96;border-radius:19px;padding:22px;box-shadow:0 25px 80px #000b}
.modal h2{font-size:23px}.modal p{font-size:14px}
.hidden{display:none!important}
label{display:block;color:#cfe2ee;font-size:13px;margin:12px 0 6px}
select{width:100%;padding:12px;background:#061a29;color:white;border:1px solid #4b7088;border-radius:10px;font:inherit}
.choicebox{display:grid;gap:8px;margin-top:12px}
.choicebox button{text-align:left;line-height:1.4;background:#21465f;color:white;border:1px solid #52738a}
.choicebox button:hover{background:#2b5b76}
.smalltag{display:inline-block;padding:5px 8px;border-radius:8px;background:#0a2031;border:1px solid #365d75;color:var(--cyan);font-size:11px;font-weight:900}
.footer{text-align:center;padding:14px;color:#7897ad;font-size:11px}
@media(max-width:950px){.grid{grid-template-columns:1fr}.sidegrid{display:grid;grid-template-columns:1fr 1fr;gap:10px}.sidegrid .panel{margin:0}}
@media(max-width:610px){main{padding:8px}.sidegrid{display:block}.sidegrid .panel{margin-top:10px}.viewPrompt{font-size:11px}.hud .chip{font-size:10px;padding:5px 7px}.modal{padding:17px}header{padding:10px 12px}.brand{font-size:18px}}
</style>
</head>
<body>
<header>
 <div><div class="brand">PHARMA <span>FACTORY</span></div><div class="sub">ÁREA ASIGNADA: MANTENIMIENTO Y EQUIPOS · PRIMERA PERSONA</div></div>
 <div class="chip">TURNO 07:00 – 15:00</div>
</header>
<main>
 <div class="grid">
  <section class="panel">
   <div class="gamehead">
    <div><div class="sub">PLANTA FARMACÉUTICA · SÓLIDOS ORALES</div><h1>Mantenimiento y equipos: misión de planta</h1></div>
    <div class="chip" id="missionChip">MISIÓN 1 DE 5</div>
   </div>
   <div class="view">
    <canvas id="view" width="960" height="560" aria-label="Vista en primera persona de la planta farmacéutica"></canvas>
    <div class="hud">
     <span class="chip" id="clock">07:00</span>
     <span class="chip" id="location">VESTIER</span>
     <span class="chip" id="ppe">EPP: PENDIENTE</span>
     <span class="chip" id="toolName">HERRAMIENTA: GUANTES</span>
     <span class="chip" id="riskChip">RIESGO: 28%</span>
     <span class="chip" id="lotChip">LOTE: BAJO CONTROL</span>
    </div>
    <div class="centerMark"></div>
    <div class="alertBanner" id="alertBanner">🚨 ALERTA DE EQUIPO</div>
    <div class="viewPrompt" id="viewPrompt">Pulsa «Acercarse e interactuar» para comenzar.</div>
   </div>
   <div class="controls ctrlrow">
    <div class="dpad" aria-label="Controles de movimiento">
     <button class="up" id="forward" title="Avanzar">▲</button>
     <button class="left secondary" id="turnLeft" title="Girar a la izquierda">↶</button>
     <button class="down secondary" id="backward" title="Retroceder">▼</button>
     <button class="right secondary" id="turnRight" title="Girar a la derecha">↷</button>
    </div>
    <div class="controls" style="margin:0">
     <button id="approachBtn">Acercarse e interactuar</button>
     <button class="secondary" id="useBtn">Usar / acción (E)</button>
     <button class="secondary" id="dashboardBtn">Ver dashboard</button>
     <button class="secondary" id="soundBtn">🔊 Sonido activado</button>
    </div>
   </div>
   <p class="muted">Teclado: W / ↑ avanzar · S / ↓ retroceder · A / ← girar a la izquierda · D / → girar a la derecha · E o espacio: interactuar. También puedes usar los botones de movimiento. En cada tarea, «Acercarse e interactuar» te lleva hasta el punto de trabajo.</p>
   <div class="notice" id="message">Estás en el vestier. Antes de ingresar al área de producción, debes colocarte y verificar el equipo de protección personal.</div>
  </section>
  <aside class="sidegrid">
   <section class="panel"><h2>Orden de trabajo</h2><div class="muted">La planta está bajo presión. Cada decisión puede proteger al personal y los equipos o empeorar la situación.</div><div id="taskList"></div>
    <div class="stateBox"><div class="stateLabel"><span>Riesgo operativo</span><b id="riskValue">28%</b></div><div class="meter"><i id="riskMeter"></i></div>
    <div class="stateLabel" style="margin-top:9px"><span>Integridad del lote</span><b id="lotValue">100%</b></div><div class="meter"><i id="lotMeter"></i></div></div>
    <h3 style="margin-top:14px">Registro de consecuencias</h3><div id="consequenceLog" class="logBox"><p class="muted">Aún no has tomado decisiones.</p></div>
    <p class="muted" id="npcStatus">Técnico: apoyo de mantenimiento. Supervisora: exige trazabilidad y liberación segura.</p><button class="secondary" id="resetBtn" style="width:100%">Reiniciar turno</button></section>
   <section class="panel"><h2>Dashboard de mantenimiento</h2><div class="kpis" id="kpis"></div><p class="muted">Los datos y metas son simulados con fines académicos. Verde = meta; amarillo = seguimiento; rojo = requiere intervención.</p></section>
  </aside>
 </div>
</main>
<div class="footer">Simulación académica. No sustituye procedimientos normalizados, permisos de trabajo, bloqueo/etiquetado ni formación técnica.</div>
<div class="toast" id="toast"></div>

<div class="overlay" id="intro">
 <div class="modal">
  <div class="smalltag">SIMULACIÓN CINEMATOGRÁFICA · ACTIVIDAD 3</div>
  <h1 style="font-size:clamp(34px,6vw,54px);color:var(--cyan);margin-top:12px">PHARMA FACTORY</h1>
  <h2>Tema central: mantenimiento y equipos</h2>
  <p>Esta vez recorrerás la planta <b>desde los ojos del personaje</b>. No verás al muñeco caminando desde afuera: observarás el vestier, las máquinas, las herramientas y al personal como si tú estuvieras dentro de la planta.</p>
  <p><b>Integrantes</b></p>
  <p>Abraham Andrades · Valeria Bohorquez · Carolina Olivares · Maria Camila Vega</p>
  <div class="notice">Usa W/A/S/D o los controles de pantalla para desplazarte. Al llegar a una estación, pulsa E. También puedes usar «Acercarse e interactuar» para ir directamente al siguiente punto.</div>
  <p class="muted">Gestiona tu riesgo, protege la integridad del lote y decide cuándo detener, reportar o liberar un equipo. Tus decisiones cambian la historia y los KPI. La simulación no sustituye procedimientos reales ni autoriza intervenciones técnicas.</p>
  <button id="startBtn">Iniciar el turno</button>
 </div>
</div>

<div class="overlay hidden" id="taskModal">
 <div class="modal">
  <div class="smalltag" id="modalArea">ESTACIÓN</div>
  <h2 id="modalTitle">Actividad</h2>
  <p id="modalText"></p>
  <div id="toolNotice" class="notice"></div>
  <label for="decision" id="decisionLabel">Selecciona cómo actuar:</label>
  <select id="decision"></select>
  <div class="notice" id="decisionImpact">La decisión tendrá un efecto sobre el equipo, el lote y los indicadores.</div>
  <div class="controls">
   <button id="confirmTask">Confirmar actividad</button>
   <button class="secondary" id="closeTask">Volver a la planta</button>
  </div>
 </div>
</div>

<div class="overlay hidden" id="eventModal">
 <div class="modal">
  <div class="smalltag">EVENTO INESPERADO · DECISIÓN DE TURNO</div>
  <h2 id="eventTitle">Alerta detectada</h2>
  <p id="eventText"></p>
  <div class="choicebox" id="eventChoices"></div>
 </div>
</div>

<div class="overlay hidden" id="dashModal">
 <div class="modal dashboard-modal">
  <div class="smalltag">INFORME DE RESULTADOS · ÁREA DE MANTENIMIENTO Y EQUIPOS</div>
  <h2 id="dashTitle">Dashboard de mantenimiento</h2>
  <p id="dashSummary">Estado de los indicadores del turno.</p>
  <div class="kpis" id="dashKpis"></div>
  <div id="endingPanel" class="endingPanel"></div>
  <div id="dashExplain" class="dash-explain"></div>
  <div class="explain-card framework-card">
   <h3>¿Cómo se conecta con la gestión?</h3>
   <p><b>Factores críticos de éxito:</b> disponibilidad y continuidad operativa, confiabilidad de los equipos, respuesta oportuna ante averías y prevención de fallas.</p>
   <p><b>PHVA / PDCA:</b> el dashboard corresponde principalmente a CHECK porque mide y compara el desempeño. ACT ocurre cuando se decide y ejecuta una acción correctiva o preventiva ante un KPI amarillo o rojo.</p>
   <p><b>Balanced Scorecard:</b> la relación principal es con la perspectiva de procesos internos, porque mide la disponibilidad y confiabilidad de los equipos que sostienen la operación farmacéutica. La formación del personal también aporta a aprendizaje y crecimiento.</p>
  </div>
  <p class="muted">Uptime, MTBF y MTTR son los KPI principales del área. Cumplimiento del mantenimiento preventivo y paradas no programadas son indicadores complementarios. Los valores, metas y rangos son simulados para esta actividad académica; no son datos reales ni límites regulatorios.</p>
  <div class="controls"><button id="closeDash">Volver a la planta</button><button class="secondary" id="restartFromDash">Reiniciar turno</button></div>
 </div>
</div>

<script>
'use strict';
(() => {
const canvas=document.getElementById('view'), ctx=canvas.getContext('2d');
const W=canvas.width,H=canvas.height;
const FOV=Math.PI/3, MAX_DEPTH=18;
const map=[
"##############",
"#............#",
"#............#",
"#..##........#",
"#..##........#",
"#............#",
"#............#",
"#............#",
"#............#",
"#............#",
"#............#",
"#............#",
"#............#",
"##############"
];
const objects=[
 {id:'locker',kind:'locker',name:'Vestier y EPP',x:4.0,y:2.45,w:1.15,h:1.65},
 {id:'tablet',kind:'tablet',name:'Tableteadora',x:8.6,y:2.7,w:1.7,h:2.0},
 {id:'bench',kind:'bench',name:'Puesto de mantenimiento',x:10.3,y:5.4,w:1.25,h:1.25},
 {id:'label',kind:'label',name:'Etiquetadora',x:9.5,y:9.6,w:1.85,h:1.85},
 {id:'release',kind:'release',name:'Puesto de verificación',x:3.7,y:10.0,w:1.35,h:1.45},
 {id:'tech',kind:'tech',name:'Técnico de mantenimiento',x:9.7,y:3.8,w:1.02,h:1.8,npc:true},
 {id:'supervisor',kind:'supervisor',name:'Supervisora de planta',x:4.2,y:9.6,w:1.05,h:1.85,npc:true}
];
const tasks=[
 {name:'Verificar EPP',loc:'VESTIER',object:'locker',tool:'GUANTES Y EPP',title:'Preparación antes de ingresar',text:'La planta está en turno. Se ha reportado una desviación en la tableteadora y debes ingresar al área de forma segura. La supervisora espera que verifiques tu protección antes de entrar.',notice:'La selección afecta el riesgo de contaminación y la autorización de acceso.',choices:[
  ['ok','Colocar y revisar todo el EPP','Entrada autorizada. El riesgo de exposición y contaminación se mantiene controlado.'],
  ['mask','Entrar sin protección facial completa','Se registra incumplimiento de EPP; aumenta el riesgo para el trabajador y se bloquea el acceso hasta corregirlo.'],
  ['gloves','Usar guantes deteriorados','Se registra una condición insegura y aumenta el riesgo de contaminación del área.']
 ]},
 {name:'Inspeccionar tableteadora',loc:'PRODUCCIÓN',object:'tablet',tool:'LISTA DE CHEQUEO',title:'La tableteadora presenta vibración',text:'La máquina está detenida para inspección. Observas una vibración inusual y una luz ámbar en el panel. El técnico te pregunta si vas a documentar el hallazgo o continuar el turno.',notice:'La inspección es visual y documental. No retires guardas ni manipules componentes móviles.',choices:[
  ['safe','Inspeccionar, registrar la vibración y solicitar evaluación','El técnico recibe el hallazgo. Se reduce la incertidumbre y se programa la intervención antes de una falla mayor.'],
  ['partial','Registrar solo la inspección visual, sin escalar la vibración','El hallazgo queda incompleto. La causa puede persistir y el riesgo operativo aumenta moderadamente.'],
  ['bad','Ignorar la vibración para no retrasar la producción','El defecto progresa. Aumenta la probabilidad de falla, se deteriora el MTBF y puede ocurrir una parada imprevista.']
 ]},
 {name:'Ejecutar mantenimiento preventivo',loc:'MANTENIMIENTO',object:'bench',tool:'KIT DE MANTENIMIENTO',title:'Orden preventiva crítica',text:'El planificador dejó una orden preventiva pendiente. El técnico te entrega el kit de mantenimiento, pero recuerda que la intervención requiere autorización, aislamiento y registro por personal competente.',notice:'La simulación representa la gestión de la orden y la verificación segura. No muestra instrucciones para intervenir equipos energizados.',choices:[
  ['safe','Verificar autorización y estado seguro; ejecutar y documentar','Se completa la orden. Disminuye el riesgo de falla futura y mejora el cumplimiento preventivo.'],
  ['partial','Hacer una revisión parcial y dejar pendiente el cierre técnico','El riesgo baja poco; quedan tareas abiertas y puede ser necesario detener la línea para completarlas.'],
  ['bad','Cerrar la orden sin realizar el mantenimiento','El incumplimiento queda trazado. Se acumula mantenimiento pendiente y aumenta la posibilidad de avería.']
 ]},
 {name:'Atender alarma de etiquetadora',loc:'ENVASADO',object:'label',tool:'LINTERNA Y RADIO',title:'🚨 La etiquetadora se detiene',text:'Una alarma roja y un ruido repentino interrumpen el envasado. Una orden de lote está en curso. La supervisora pide que coordines la respuesta; el técnico autorizado está esperando tu decisión.',notice:'No intervengas con el equipo energizado. Tu decisión determina la seguridad del personal, el estado del lote y el tiempo de recuperación.',choices:[
  ['safe','Asegurar el área, reportar y escalar al técnico autorizado','La zona queda controlada. Se preserva el lote y el técnico inicia el diagnóstico con trazabilidad.'],
  ['partial','Pausar la operación y esperar instrucciones sin documentar','El riesgo inmediato se contiene, pero se pierde tiempo de diagnóstico y la parada se prolonga.'],
  ['bad','Anular la alarma y ordenar un reinicio para continuar','La protección queda comprometida. La falla puede agravarse, el lote entra en retención y el riesgo operativo sube de forma crítica.']
 ]},
 {name:'Verificar y liberar el equipo',loc:'CONTROL DE CALIDAD',object:'release',tool:'TABLETA Y REGISTROS',title:'Decisión final: ¿liberar o retener?',text:'El técnico indica que la intervención terminó. La supervisora necesita saber si autorizas el retorno del equipo y qué haces con el lote procesado durante la incidencia.',notice:'La liberación requiere prueba funcional satisfactoria, registros completos, autorización y evaluación del impacto sobre el lote.',choices:[
  ['safe','Revisar prueba, documentación y autorizar liberación; cerrar desviación','El equipo retorna de forma controlada. Se conserva la trazabilidad y el lote solo sigue su flujo tras las verificaciones requeridas.'],
  ['partial','Mantener el equipo fuera de servicio hasta completar una evidencia pendiente','El lote queda protegido y el equipo no se libera; aumenta el tiempo de parada, pero se evita una liberación incompleta.'],
  ['bad','Liberar el equipo y el lote sin verificar todos los registros','Se genera una desviación crítica de calidad. El equipo puede fallar de nuevo y el lote debe retenerse para evaluación.']
 ]}
];
let player={x:2.35,y:2.55,a:0};
let step=0,minutes=420,frame=0,modalOpen=false,muted=false,gameStarted=false,autowalking=false;
let stats={uptime:82,mtbf:20,mttr:5,preventive:75,stops:8};
let plantState={risk:28,lot:100,authorized:true,maintenanceBacklog:1,incident:false,lotHeld:false,log:[]};
let zbuffer=new Float32Array(W);
let audioCtx=null;

function cell(x,y){const mx=Math.floor(x),my=Math.floor(y);return map[my]?.[mx]||'#';}
function blocked(x,y){const r=.19;return cell(x-r,y-r)==='#'||cell(x+r,y-r)==='#'||cell(x-r,y+r)==='#'||cell(x+r,y+r)==='#';}
function moveForward(amount){
 const nx=player.x+Math.cos(player.a)*amount,ny=player.y+Math.sin(player.a)*amount;
 if(!blocked(nx,player.y))player.x=nx;
 if(!blocked(player.x,ny))player.y=ny;
 minutes+=Math.max(1,Math.round(Math.abs(amount)*2.4));
}
function rotate(amount){player.a=(player.a+amount+Math.PI*2)%(Math.PI*2);minutes+=1;}
function startAudio(){
 if(muted)return;
 try{if(!audioCtx)audioCtx=new (window.AudioContext||window.webkitAudioContext)();if(audioCtx.state==='suspended')audioCtx.resume();}catch(e){}
}
function tone(freq,duration=.2,type='sawtooth',gain=.06,delay=0){
 if(muted)return;
 startAudio();if(!audioCtx)return;
 const t=audioCtx.currentTime+delay,o=audioCtx.createOscillator(),g=audioCtx.createGain();
 o.type=type;o.frequency.setValueAtTime(freq,t);g.gain.setValueAtTime(gain,t);g.gain.exponentialRampToValueAtTime(.001,t+duration);
 o.connect(g);g.connect(audioCtx.destination);o.start(t);o.stop(t+duration);
}
function alarm(){tone(880,.24,'square',.07);tone(620,.26,'square',.07,.28);tone(880,.24,'square',.07,.58);}
function success(){tone(520,.13,'sine',.05);tone(660,.13,'sine',.05,.14);tone(790,.2,'sine',.05,.28);}
function toast(title,body,danger=false){
 const el=document.getElementById('toast');el.className='toast show'+(danger?' danger':'');
 el.innerHTML='<b>'+title+'</b><div style="font-size:13px;margin-top:4px">'+body+'</div>';
 clearTimeout(window._toastTimer);window._toastTimer=setTimeout(()=>el.classList.remove('show'),4500);
}
function currentTask(){return tasks[step]||null;}
function distance(o){return Math.hypot(o.x-player.x,o.y-player.y);}
function activeObject(){const t=currentTask();return t?objects.find(o=>o.id===t.object):null;}
function updateHud(){
 document.getElementById('clock').textContent=String(Math.floor(minutes/60)).padStart(2,'0')+':'+String(minutes%60).padStart(2,'0');
 const t=currentTask();document.getElementById('location').textContent=t?t.loc:'TURNO FINALIZADO';
 document.getElementById('ppe').textContent='EPP: '+(tasks[0].done?'COMPLETO':'PENDIENTE');
 document.getElementById('toolName').textContent='HERRAMIENTA: '+(t?t.tool:'GUARDADA');
 document.getElementById('riskChip').textContent='RIESGO: '+plantState.risk+'%';
 document.getElementById('riskChip').style.color=plantState.risk>=65?'#ff737d':plantState.risk>=35?'#ffd166':'#55d99d';
 document.getElementById('lotChip').textContent='LOTE: '+(plantState.lotHeld?'RETENIDO':plantState.lot<75?'EN RIESGO':'BAJO CONTROL');
 document.getElementById('riskValue').textContent=plantState.risk+'%';
 document.getElementById('riskMeter').style.width=plantState.risk+'%';
 document.getElementById('riskMeter').style.background=plantState.risk>=65?'#ff5968':plantState.risk>=35?'#efbd57':'#55d99d';
 document.getElementById('lotValue').textContent=plantState.lot+'%';
 document.getElementById('lotMeter').style.width=plantState.lot+'%';
 document.getElementById('lotMeter').style.background=plantState.lot<75?'#ff5968':plantState.lot<90?'#efbd57':'#55d99d';
 renderLog();
 document.getElementById('missionChip').textContent=t?`MISIÓN ${step+1} DE 5`:'TURNO COMPLETADO';
 const obj=activeObject();
 if(!t){document.getElementById('viewPrompt').textContent='Turno completado. Abre el dashboard para revisar los KPI.';document.getElementById('alertBanner').classList.remove('show');}
 else{
  const d=distance(obj);
  document.getElementById('viewPrompt').textContent=d<2.15?'Pulsa E o «Usar / acción» para interactuar.':'Objetivo: '+obj.name+' · '+d.toFixed(1)+' m · Usa «Acercarse e interactuar».';
  document.getElementById('alertBanner').classList.toggle('show',step===3);
 }
 renderTasks();renderKpis('kpis');
}
function renderTasks(){
 document.getElementById('taskList').innerHTML=tasks.map((t,i)=>`<div class="task ${t.done?'done':''} ${i===step?'active':''}"><strong>${t.done?'✓':i===step?'▶':'○'} ${t.name}</strong><small>${t.loc}</small></div>`).join('');
}
function level(v,good,mid,lower=false){return lower?(v<=good?'good':v<=mid?'warn':'bad'):(v>=good?'good':v>=mid?'warn':'bad');}
function renderKpis(target){
 const values=[
 ['Uptime',stats.uptime+'%','Meta ≥95% · Amarillo 90–94% · Rojo <90%',level(stats.uptime,95,90)],
 ['MTBF',stats.mtbf.toFixed(0)+' h','Meta ≥35 h · Amarillo 25–34 h · Rojo <25 h',level(stats.mtbf,35,25)],
 ['MTTR',stats.mttr.toFixed(1)+' h','Meta ≤3 h · Amarillo >3–4 h · Rojo >4 h',level(stats.mttr,3,4,true)],
 ['Preventivo',stats.preventive+'%','Meta ≥90% · Amarillo 80–89% · Rojo <80%',level(stats.preventive,90,80)],
 ['Paradas no programadas',stats.stops+'/mes','Meta ≤3 · Amarillo 4–5 · Rojo >5',level(stats.stops,3,5,true)]
 ];
 document.getElementById(target).innerHTML=values.map(v=>`<div class="kpi"><span>${v[0]}</span><b class="${v[3]}">${v[1]}</b><span>${v[2]}</span><span class="${v[3]}" style="font-weight:900;margin-top:4px">${v[3]==='good'?'● EN META':v[3]==='warn'?'● SEGUIMIENTO':'● PRIORIDAD'}</span></div>`).join('');
}
function openTask(){
 const t=currentTask();if(!t||modalOpen||autowalking)return;
 const obj=activeObject();
 if(distance(obj)>2.2){toast('ACÉRCATE AL EQUIPO','Usa «Acercarse e interactuar» para llegar al punto de trabajo.');return;}
 startAudio();modalOpen=true;
 document.getElementById('modalArea').textContent=t.loc;
 document.getElementById('modalTitle').textContent=t.title;
 document.getElementById('modalText').textContent=t.text;
 document.getElementById('toolNotice').textContent=t.notice;
 const sel=document.getElementById('decision');sel.innerHTML='';
 t.choices.forEach(c=>{const opt=document.createElement('option');opt.value=c[0];opt.textContent=c[1];opt.dataset.impact=c[2]||'';sel.appendChild(opt);});
 const preview=()=>{document.getElementById('decisionImpact').textContent=sel.selectedOptions[0]?.dataset.impact||'La decisión tendrá consecuencias sobre el proceso.';};
 sel.onchange=preview;preview();
 document.getElementById('decisionLabel').textContent='Elige una decisión; revisa su consecuencia antes de confirmar:';
 document.getElementById('taskModal').classList.remove('hidden');
}
function closeTask(){document.getElementById('taskModal').classList.add('hidden');modalOpen=false;}
function clampStats(){
 stats.uptime=Math.max(55,Math.min(100,stats.uptime));stats.mtbf=Math.max(8,Math.min(60,stats.mtbf));
 stats.mttr=Math.max(1,Math.min(9,stats.mttr));stats.preventive=Math.max(35,Math.min(100,stats.preventive));
 stats.stops=Math.max(0,Math.min(20,stats.stops));
}
function recordConsequence(title,detail,kind='good'){
 plantState.log.unshift({title,detail,kind,time:String(Math.floor(minutes/60)).padStart(2,'0')+':'+String(minutes%60).padStart(2,'0')});
 plantState.log=plantState.log.slice(0,8);
 document.getElementById('message').textContent=title+': '+detail;
 toast(title,detail,kind==='bad');
 renderLog();
}
function renderLog(){
 const box=document.getElementById('consequenceLog');
 if(!box)return;
 box.innerHTML=plantState.log.length?plantState.log.map(e=>`<div class="logEntry ${e.kind==='good'?'goodLog':e.kind==='bad'?'badLog':''}"><b>${e.time} · ${e.title}</b><br>${e.detail}</div>`).join(''):'<p class="muted">Aún no has tomado decisiones.</p>';
}
function setRisk(v){plantState.risk=Math.max(0,Math.min(100,plantState.risk+v));}
function applyTaskChoice(i,choice){
 let title='',detail='',kind='good';
 if(i===0){
  if(choice==='ok'){setRisk(-7);plantState.authorized=true;title='EPP completo';detail='Acceso autorizado. Se mantiene controlada la exposición del trabajador.';success();}
  else if(choice==='mask'){setRisk(22);plantState.authorized=false;plantState.lot-=8;minutes+=20;plantState.authorized=true;title='Acceso bloqueado y corregido';detail='La supervisora impide el ingreso. Debes completar el EPP antes de entrar; pierdes 20 minutos y queda registrado el incumplimiento.';kind='bad';alarm();}
  else{setRisk(15);plantState.authorized=false;plantState.lot-=5;minutes+=15;plantState.authorized=true;title='EPP reemplazado';detail='No se autoriza el ingreso con guantes deteriorados. Se reemplazan antes de entrar; pierdes 15 minutos y queda una observación de seguridad.';kind='bad';alarm();}
 }
 if(i===1){
  if(choice==='safe'){setRisk(-9);stats.uptime+=3;stats.mtbf+=4;title='Vibración reportada';detail='El técnico recibe el hallazgo y programa evaluación. Se reduce el riesgo de una falla mayor.';}
  else if(choice==='partial'){setRisk(12);stats.uptime-=2;stats.mtbf-=2;title='Inspección incompleta';detail='La vibración sigue sin diagnóstico. La posibilidad de avería aumenta y la supervisora solicita seguimiento.';kind='warn';}
  else{setRisk(24);stats.uptime-=6;stats.mtbf-=5;stats.stops+=2;plantState.maintenanceBacklog++;title='Hallazgo ignorado';detail='La vibración progresa. La tableteadora puede detenerse de forma inesperada y se acumula una intervención pendiente.';kind='bad';alarm();}
 }
 if(i===2){
  if(choice==='safe'){setRisk(-14);stats.preventive+=13;stats.mtbf+=6;stats.stops-=1;plantState.maintenanceBacklog=Math.max(0,plantState.maintenanceBacklog-1);title='Preventivo completado';detail='La orden se ejecutó bajo control y quedó documentada. Disminuye el riesgo de falla repetitiva.';}
  else if(choice==='partial'){setRisk(8);stats.preventive+=3;stats.mtbf+=1;title='Orden parcialmente ejecutada';detail='Quedan actividades pendientes. Se requiere reprogramar y el equipo conserva una condición de riesgo moderado.';kind='warn';}
  else{setRisk(24);stats.preventive-=13;stats.mtbf-=6;stats.stops+=2;plantState.maintenanceBacklog+=2;title='Mantenimiento omitido';detail='La orden cerrada sin ejecución crea una brecha documental y aumenta la probabilidad de falla.';kind='bad';alarm();}
 }
 if(i===3){
  if(choice==='safe'){setRisk(-16);stats.mttr-=1.5;stats.stops-=2;stats.uptime+=5;plantState.incident=false;title='Avería contenida';detail='Área asegurada y técnico autorizado notificado. Se preserva el lote y comienza el diagnóstico con trazabilidad.';}
  else if(choice==='partial'){setRisk(9);stats.mttr+=1;stats.stops+=1;stats.uptime-=3;title='Parada prolongada';detail='La línea permanece en espera. No hay intervención insegura, pero el diagnóstico tarda más y aumenta el MTTR.';kind='warn';}
  else{setRisk(38);stats.mttr+=2.5;stats.stops+=3;stats.uptime-=9;plantState.lot-=28;plantState.lotHeld=true;plantState.incident=true;title='Falla agravada';detail='La protección fue anulada. Se detiene la línea, el lote queda retenido para evaluación y se activa una investigación de desviación.';kind='bad';alarm();}
 }
 if(i===4){
  if(choice==='safe'&&plantState.risk<65&&!plantState.incident){
   setRisk(-8);stats.uptime+=9;stats.mtbf+=5;stats.mttr-=1;stats.preventive+=7;stats.stops-=2;title='Equipo liberado';detail='La prueba fue satisfactoria, los registros están completos y la supervisora autoriza el retorno a operación.';success();
  }else if(choice==='safe'){
   setRisk(-3);plantState.lotHeld=true;stats.uptime+=2;title='Equipo en verificación reforzada';detail='Aunque se completó la prueba, el historial de riesgo exige revisar la desviación antes de liberar el lote. El equipo no se entrega a producción todavía.';kind='warn';
  }else if(choice==='partial'){
   setRisk(-4);plantState.lotHeld=true;stats.mttr+=.8;stats.stops+=1;title='Equipo y lote retenidos';detail='Se evita liberar sin evidencia. El tiempo de parada aumenta, pero se protege la trazabilidad y la calidad del lote.';kind='warn';
  }else{
   setRisk(35);plantState.lot-=35;plantState.lotHeld=true;plantState.incident=true;stats.uptime-=8;stats.mtbf-=5;stats.mttr+=1.5;stats.stops+=3;title='Liberación no autorizada';detail='Se genera una desviación crítica. Se ordena retener el lote y sacar el equipo de servicio para evaluación.';kind='bad';alarm();
  }
 }
 clampStats();plantState.lot=Math.max(0,Math.min(100,plantState.lot));
 recordConsequence(title,detail,kind);renderKpis('kpis');updateHud();
}
function completeTask(){
 if(!modalOpen)return;
 const i=step,choice=document.getElementById('decision').value;
 applyTaskChoice(i,choice);closeTask();step++;updateHud();
 if(step===3){setTimeout(()=>triggerEvent(0),450);return;}
 if(step===4){setTimeout(()=>triggerEvent(1),450);return;}
 if(step>=tasks.length){document.getElementById('message').textContent='Turno finalizado. Revisa los resultados del dashboard.';showDashboard(true);success();return;}
 document.getElementById('message').textContent='Actividad completada. Continúa hacia: '+tasks[step].name+'.';
}
const events=[
 {title:'⚠ VIBRACIÓN ANORMAL EN LA TABLETEADORA',text:'El técnico detecta que la vibración aumentó después del último ciclo. La supervisora espera tu decisión: la falla puede afectar la continuidad de la producción.',options:[
  {label:'Detener de forma controlada, documentar y evaluar la causa',run:()=>{setRisk(-9);stats.uptime-=1;stats.mtbf+=3;stats.preventive+=2;return ['Desviación controlada','Se evita que el defecto avance. Se abre una acción de mantenimiento y análisis de causa.','good'];}},
  {label:'Ignorar el hallazgo para no retrasar el lote',run:()=>{setRisk(25);stats.uptime-=6;stats.mtbf-=4;stats.stops+=2;plantState.lot-=10;return ['Riesgo de falla elevado','La vibración continúa y puede provocar una parada inesperada. El lote pasa a evaluación.','bad'];}},
  {label:'Solicitar al técnico una inspección planificada',run:()=>{setRisk(-5);stats.mtbf+=2;stats.preventive+=4;return ['Intervención planificada','El equipo queda bajo seguimiento técnico con una orden documentada.','good'];}}
 ]},
 {title:'🚨 ALARMA DE TEMPERATURA EN ENVASADO',text:'La etiquetadora reporta una alarma de temperatura. El lote procesado durante la incidencia necesita una evaluación documentada. Debes decidir cómo responder.',options:[
  {label:'Asegurar el área, reportar y escalar la alarma',run:()=>{setRisk(-11);stats.mttr-=.6;stats.stops-=1;stats.uptime+=2;plantState.lotHeld=true;return ['Alarma escalada correctamente','La línea queda segura y el lote se mantiene retenido preventivamente hasta revisar el impacto.','good'];}},
  {label:'Anular la protección para continuar produciendo',run:()=>{setRisk(32);stats.uptime-=7;stats.stops+=3;stats.mttr+=1.2;plantState.lot-=25;plantState.lotHeld=true;plantState.incident=true;return ['Incidente crítico','La operación se detiene, el lote queda retenido y se debe abrir una investigación de desviación.','bad'];}},
  {label:'Poner el equipo en espera y consultar el historial de alarmas',run:()=>{setRisk(-4);stats.mttr-=.4;stats.preventive+=1;plantState.lotHeld=true;return ['Diagnóstico en espera controlada','Se conserva la seguridad, pero el tiempo de respuesta aumenta mientras se revisa el historial.','warn'];}}
 ]}
];
function triggerEvent(index){
 const ev=events[index];if(!ev)return;
 alarm();document.getElementById('eventTitle').textContent=ev.title;
 document.getElementById('eventText').textContent=ev.text;
 const box=document.getElementById('eventChoices');box.innerHTML='';
 ev.options.forEach(o=>{
  const b=document.createElement('button');b.textContent=o.label;
  b.addEventListener('click',()=>{
   const result=o.run();clampStats();plantState.lot=Math.max(0,Math.min(100,plantState.lot));
   document.getElementById('eventModal').classList.add('hidden');
   if(result)recordConsequence(result[0],result[1],result[2]);
   renderKpis('kpis');updateHud();
   if(step>=tasks.length){showDashboard(true);}
  });
  box.appendChild(b);
 });
 document.getElementById('eventModal').classList.remove('hidden');
}
function dashboardRows(){
 const rows=[
  {name:'Uptime / disponibilidad',value:stats.uptime+'%',target:'Meta: ≥95%',range:'Verde ≥95% · Amarillo 90–<95% · Rojo <90%',fce:'Disponibilidad y continuidad operativa',formula:'(Tiempo operativo / tiempo programado) × 100',source:'Registro de horas programadas y horas de operación del equipo',frequency:'Registro por turno y consolidación mensual',owner:'Supervisor de mantenimiento',meaning:'Indica qué porcentaje del tiempo programado el equipo estuvo disponible para operar.',interpret:stats.uptime>=95?'La disponibilidad alcanzó la meta: el equipo estuvo operativo durante casi todo el tiempo programado.':stats.uptime>=90?'La disponibilidad está cerca de la meta, pero todavía hubo tiempo de equipo detenido que debe investigarse.':'La disponibilidad está por debajo de la meta: las paradas están afectando la continuidad de la producción.',status:level(stats.uptime,95,90)},
  {name:'MTBF / tiempo medio entre fallas',value:stats.mtbf.toFixed(0)+' h',target:'Meta: ≥35 h',range:'Verde ≥35 h · Amarillo 25–<35 h · Rojo <25 h',fce:'Confiabilidad y prevención de fallas',formula:'Tiempo operativo / número de fallas',source:'Bitácora de fallas y órdenes de trabajo del equipo',frequency:'Consolidación mensual',owner:'Coordinador o ingeniero de mantenimiento',meaning:'Es el tiempo promedio de funcionamiento entre una falla y la siguiente. Cuanto mayor sea, más confiable es el equipo.',interpret:stats.mtbf>=35?'Se cumple la meta: en promedio, el equipo trabaja más tiempo antes de presentar otra falla.':stats.mtbf>=25?'El intervalo entre fallas requiere seguimiento para mejorar la confiabilidad.':'Las fallas ocurren con demasiada frecuencia frente a la meta; se debe revisar la causa raíz y el plan preventivo.',status:level(stats.mtbf,35,25)},
  {name:'MTTR / tiempo medio de reparación',value:stats.mttr.toFixed(1)+' h',target:'Meta: ≤3 h',range:'Verde ≤3 h · Amarillo >3–4 h · Rojo >4 h',fce:'Respuesta y recuperación ante averías',formula:'Tiempo total de reparación / número de reparaciones',source:'Hora de reporte de avería y hora de retorno autorizado a operación',frequency:'Consolidación mensual',owner:'Coordinador de mantenimiento',meaning:'Es el tiempo promedio que se necesita para reparar un equipo después de una avería. Cuanto menor sea, más rápida es la recuperación.',interpret:stats.mttr<=3?'Se cumple la meta: el tiempo promedio de reparación está controlado.':stats.mttr<=4?'La reparación toma más tiempo del objetivo; conviene revisar diagnóstico, repuestos y coordinación.':'El tiempo de reparación supera la meta y prolonga la indisponibilidad del equipo.',status:level(stats.mttr,3,4,true)},
  {name:'Cumplimiento del mantenimiento preventivo',value:stats.preventive+'%',target:'Meta: ≥90%',range:'Verde ≥90% · Amarillo 80–<90% · Rojo <80%',fce:'Ejecución del mantenimiento preventivo',formula:'(Mantenimientos realizados / programados) × 100',source:'Plan preventivo y órdenes de mantenimiento cerradas',frequency:'Seguimiento semanal y consolidación mensual',owner:'Planificador de mantenimiento',meaning:'Mide el porcentaje de actividades preventivas realizadas respecto de las que estaban programadas.',interpret:stats.preventive>=90?'El programa preventivo cumple la meta: se está ejecutando la mayoría de las actividades planificadas.':stats.preventive>=80?'Hay actividades preventivas pendientes que deben reprogramarse y cerrarse.':'El cumplimiento es bajo: aumenta el riesgo de fallas por mantenimiento no ejecutado.',status:level(stats.preventive,90,80)},
  {name:'Paradas no programadas',value:stats.stops+' / mes',target:'Meta: ≤3 por mes',range:'Verde ≤3 · Amarillo 4–5 · Rojo >5',fce:'Continuidad operativa y control de interrupciones',formula:'Conteo de paradas inesperadas en el periodo',source:'Registro de paradas de producción y bitácora de mantenimiento',frequency:'Registro diario y consolidación mensual',owner:'Supervisores de producción y mantenimiento',meaning:'Cuenta las interrupciones inesperadas del equipo durante un mes. Cuantas menos ocurran, mejor es la continuidad operativa.',interpret:stats.stops<=3?'Las paradas inesperadas están dentro de la meta.':stats.stops<=5?'Las paradas requieren seguimiento para evitar que aumenten.':'Hay demasiadas paradas inesperadas; es prioritario analizar las causas y prevenir recurrencias.',status:level(stats.stops,3,5,true)}
 ];
 return rows;
}
function renderDashboardExplanation(){
 const rows=dashboardRows();
 document.getElementById('dashExplain').innerHTML=rows.map((r,i)=>`
  <article class="explain-card">
   <h3>${i+1}. ${r.name}</h3>
   <p><b>Valor obtenido:</b> ${r.value} &nbsp; <b>Meta:</b> ${r.target}</p>
   <p><b>Rangos de gestión:</b> ${r.range}</p>
   <p><b>FCE relacionado:</b> ${r.fce}</p>
   <p><b>Fórmula:</b> ${r.formula}</p>
   <p><b>Fuente del dato:</b> ${r.source}</p>
   <p><b>Frecuencia:</b> ${r.frequency}</p>
   <p><b>Responsable propuesto:</b> ${r.owner}</p>
   <p class="meaning"><b>¿Qué significa?</b> ${r.meaning}</p>
   <p><b>Interpretación del resultado:</b> ${r.interpret}</p>
   <p><b>Estado:</b> <span class="${r.status}">${r.status==='good'?'EN META':r.status==='warn'?'SEGUIMIENTO':'REQUIERE INTERVENCIÓN'}</span></p>
  </article>`).join('');
}
function getEnding(){
 if(plantState.incident||plantState.risk>=70||plantState.lot<65)
  return {kind:'bad',title:'FINAL: CONTINGENCIA EN LA PLANTA',text:'Tus decisiones elevaron el riesgo o comprometieron el lote. La planta detiene la liberación, retiene el lote y abre una investigación. El equipo permanece fuera de servicio hasta demostrar condiciones seguras.'};
 if(plantState.risk>=40||plantState.lot<90||plantState.maintenanceBacklog>1)
  return {kind:'warn',title:'FINAL: TURNO CON DESVIACIONES',text:'La producción se sostuvo parcialmente, pero quedaron riesgos, registros o tareas pendientes. La supervisora solicita acciones correctivas y preventivas antes de normalizar el proceso.'};
 return {kind:'good',title:'FINAL: OPERACIÓN RECUPERADA',text:'Priorizaste la seguridad, el mantenimiento y la trazabilidad. Los equipos regresan a operación bajo control y el turno termina con el riesgo contenido.'};
}
function showDashboard(finalReport=false){
 renderKpis('dashKpis');renderDashboardExplanation();
 document.getElementById('dashTitle').textContent=finalReport?'Informe final · Consecuencias de tus decisiones':'Dashboard de mantenimiento y equipos';
 const ending=finalReport?getEnding():null;
 document.getElementById('endingPanel').innerHTML=finalReport?`<strong class="${ending.kind}">${ending.title}</strong><p>${ending.text}</p><p><b>Riesgo operativo:</b> ${plantState.risk}% · <b>Integridad del lote:</b> ${plantState.lot}% · <b>Órdenes pendientes:</b> ${plantState.maintenanceBacklog}</p><p><b>Estado del lote:</b> ${plantState.lotHeld?'RETENIDO PARA EVALUACIÓN':'SIN RETENCIÓN ADICIONAL'}</p>`:'';
 document.getElementById('dashSummary').textContent=finalReport
  ?'Terminaste el recorrido de mantenimiento. A continuación se muestran los valores finales de los cinco KPI y lo que significan para la disponibilidad, confiabilidad y conservación de los equipos.'
  :'Consulta el estado actual de los indicadores del área de mantenimiento y equipos.';
 document.getElementById('closeDash').textContent=finalReport?'Cerrar informe':'Volver a la planta';
 document.getElementById('dashModal').classList.remove('hidden');
}
function closeDashboard(){document.getElementById('dashModal').classList.add('hidden');}
function approach(){
 const obj=activeObject();if(!obj||modalOpen||autowalking)return;
 startAudio();autowalking=true;
 const dx=obj.x-player.x,dy=obj.y-player.y,len=Math.hypot(dx,dy)||1;
 const destX=obj.x-dx/len*1.28,destY=obj.y-dy/len*1.28;
 const start={x:player.x,y:player.y,a:player.a},endA=Math.atan2(dy,dx);
 let elapsed=0;const duration=650;
 function animate(){
  elapsed+=16;const t=Math.min(1,elapsed/duration),ease=t*t*(3-2*t);
  player.x=start.x+(destX-start.x)*ease;player.y=start.y+(destY-start.y)*ease;
  let diff=((endA-start.a+Math.PI*3)%(Math.PI*2))-Math.PI;player.a=start.a+diff*ease;
  draw();if(t<1){requestAnimationFrame(animate);}else{autowalking=false;minutes+=2;updateHud();openTask();}
 }
 requestAnimationFrame(animate);
}
function interact(){if(modalOpen||autowalking)return;const obj=activeObject();if(!obj)return;if(distance(obj)>2.2){toast('FUERA DE ALCANCE','Acércate a la estación o pulsa el botón «Acercarse e interactuar».');return;}openTask();}
function reset(){
 player={x:2.35,y:2.55,a:0};step=0;minutes=420;modalOpen=false;autowalking=false;
 stats={uptime:82,mtbf:20,mttr:5,preventive:75,stops:8};plantState={risk:28,lot:100,authorized:true,maintenanceBacklog:1,incident:false,lotHeld:false,log:[]};tasks.forEach(t=>t.done=false);
 ['taskModal','eventModal','dashModal'].forEach(id=>document.getElementById(id).classList.add('hidden'));
 document.getElementById('message').textContent='El turno vuelve a comenzar. La planta está bajo tensión: protege al personal, evita fallas y conserva la integridad del lote.';
 updateHud();draw();
}

function make3DWorker(kind){
 // Personaje de videojuego con apariencia 3D: volumen, luz ambiental, brillos y sombras.
 const c=document.createElement('canvas');c.width=220;c.height=420;
 const g=c.getContext('2d');
 const tech=kind==='tech';
 const coat=tech?'#edf4f6':'#e9f3f6';
 const trim=tech?'#24536b':'#16819a';
 const skin='#c58f72';

 const linear=(x1,y1,x2,y2,stops)=>{
  const gr=g.createLinearGradient(x1,y1,x2,y2);
  stops.forEach(s=>gr.addColorStop(s[0],s[1]));return gr;
 };
 const radial=(x,y,r,stops)=>{
  const gr=g.createRadialGradient(x-r*.28,y-r*.32,r*.04,x,y,r);
  stops.forEach(s=>gr.addColorStop(s[0],s[1]));return gr;
 };
 const path=(points,fill,stroke=null,line=1)=>{
  g.beginPath();g.moveTo(points[0][0],points[0][1]);
  for(let i=1;i<points.length;i++)g.lineTo(points[i][0],points[i][1]);
  g.closePath();g.fillStyle=fill;g.fill();
  if(stroke){g.strokeStyle=stroke;g.lineWidth=line;g.stroke();}
 };
 const rounded=(x,y,w,h,r,fill,stroke=null,line=1)=>{
  g.beginPath();g.roundRect(x,y,w,h,r);g.fillStyle=fill;g.fill();
  if(stroke){g.strokeStyle=stroke;g.lineWidth=line;g.stroke();}
 };
 const ellipse=(x,y,rx,ry,fill,stroke=null,line=1)=>{
  g.beginPath();g.ellipse(x,y,rx,ry,0,0,Math.PI*2);g.fillStyle=fill;g.fill();
  if(stroke){g.strokeStyle=stroke;g.lineWidth=line;g.stroke();}
 };
 const tube2d=(x1,y1,x2,y2,width,fill)=>{
  g.lineCap='round';g.lineJoin='round';g.strokeStyle=fill;g.lineWidth=width;
  g.beginPath();g.moveTo(x1,y1);g.lineTo(x2,y2);g.stroke();
 };

 // Sombra suave bajo los pies.
 ellipse(110,386,63,18,radial(110,386,64,[[0,'rgba(3,18,28,.35)'],[1,'rgba(3,18,28,0)']]));
 // Piernas y calzado: pantalón de uniforme con pliegues y volumen.
 path([[74,282],[108,282],[105,365],[91,374],[78,365]],linear(70,290,110,290,[[0,'#839ba7'],[.28,'#e8f0f3'],[.72,'#c5d5dc'],[1,'#718b99']]));
 path([[112,282],[147,282],[142,365],[128,374],[113,365]],linear(112,290,151,290,[[0,'#6e8795'],[.32,'#e6eef1'],[.78,'#bdcdd5'],[1,'#708a98']]));
 tube2d(92,300,91,352,3,'rgba(94,121,135,.42)');
 tube2d(130,300,128,352,3,'rgba(94,121,135,.42)');
 // Botas.
 path([[76,359],[95,359],[102,380],[99,390],[54,390],[53,383],[64,374]],linear(55,370,100,390,[[0,'#637b88'],[.35,'#2d4859'],[1,'#122b3b']]),'#193444',2);
 path([[121,359],[140,359],[158,380],[158,390],[114,390],[112,383]],linear(112,370,160,390,[[0,'#667e8a'],[.35,'#2c4759'],[1,'#102a3a']]),'#193444',2);
 tube2d(61,384,94,384,2,'#a4b9c2');tube2d(121,384,153,384,2,'#a4b9c2');

 // Bata/overol: silueta anatómica, hombros, cintura y sombreado de tela.
 path([[78,146],[92,132],[130,132],[148,147],[171,181],[158,222],[151,285],[67,285],[60,222],[49,181]],
      linear(48,140,177,170,[[0,'#879eaa'],[.18,'#dce8ed'],[.43,'#ffffff'],[.72,'#d7e5eb'],[1,'#829ba8']]),'#8da7b3',2);
 // Pliegues laterales de la bata.
 path([[65,178],[78,156],[85,276],[73,280],[69,226]],'rgba(103,132,146,.20)');
 path([[145,158],[163,183],[151,273],[140,278],[146,216]],'rgba(87,119,135,.22)');
 path([[94,150],[110,158],[108,280],[97,280]],'rgba(255,255,255,.44)');
 // Paneles de hombro y cuello.
 path([[79,145],[94,132],[111,148],[102,171],[77,164]],linear(75,135,107,170,[[0,trim],[1,'#8baab8']]));
 path([[130,132],[148,147],[143,165],[118,171],[111,148]],linear(111,135,151,170,[[0,trim],[1,'#6c96a8']]));
 path([[91,137],[110,154],[130,137],[121,176],[101,176]],linear(93,140,128,170,[[0,'#fdfefe'],[1,'#b9cbd4']]));
 // Costuras, botones y bolsillos.
 tube2d(110,164,110,280,2,'#8da5b1');
 [188,211,234,257].forEach(y=>ellipse(111,y,2.5,2.5,'#7e9aa8'));
 rounded(126,194,25,35,4,linear(126,194,151,220,[[0,'#eaf3f6'],[1,'#9db5c0']]),'#93aab5',1.5);
 tube2d(130,202,146,202,1.5,'#7895a3');

 // Brazos con volumen, mangas y puños.
 g.beginPath();g.moveTo(79,151);g.bezierCurveTo(61,155,48,176,43,210);g.lineTo(54,229);g.bezierCurveTo(69,217,81,190,94,174);g.closePath();
 g.fillStyle=linear(42,170,95,195,[[0,'#839ba7'],[.3,'#f9fcfd'],[.72,'#d2e1e7'],[1,'#8199a5']]);g.fill();g.strokeStyle='#91aab5';g.stroke();
 g.beginPath();g.moveTo(143,151);g.bezierCurveTo(161,155,174,176,179,210);g.lineTo(168,229);g.bezierCurveTo(153,217,141,190,128,174);g.closePath();
 g.fillStyle=linear(130,170,181,198,[[0,'#7e98a5'],[.3,'#ffffff'],[.72,'#cfdee5'],[1,'#7893a0']]);g.fill();g.strokeStyle='#91aab5';g.stroke();
 // Codos, guantes y dedos.
 ellipse(51,218,11,13,radial(51,218,14,[[0,'#ecf7fa'],[.6,'#9ab8c4'],[1,'#5f8292']]));
 ellipse(170,218,11,13,radial(170,218,14,[[0,'#ecf7fa'],[.6,'#9ab8c4'],[1,'#5f8292']]));
 path([[42,222],[57,224],[61,240],[51,252],[38,245]],linear(37,222,63,248,[[0,'#cce1e7'],[.45,'#77a7b7'],[1,'#315b70']]));
 path([[164,224],[179,222],[184,245],[171,252],[159,240]],linear(159,222,184,248,[[0,'#d5eaf0'],[.45,'#78a6b5'],[1,'#31576b']]));
 // Cuello y cabeza con sombreado suave.
 rounded(97,119,27,31,7,linear(96,120,125,148,[[0,'#8f6655'],[.5,skin],[1,'#805c50']]));
 ellipse(110,87,39,48,radial(110,88,48,[[0,'#f0c7a4'],[.55,skin],[.87,'#a97863'],[1,'#744e43']]),'#7c594e',1.5);
 // Orejas y perfil de la nariz.
 ellipse(72,91,7,12,linear(66,82,79,103,[[0,'#efc7a5'],[1,'#996c5a']]));
 ellipse(148,91,7,12,linear(143,82,152,103,[[0,'#efc7a5'],[1,'#996c5a']]));
 // Cofia sanitaria con malla, borde y pliegues.
 g.beginPath();g.moveTo(72,78);g.bezierCurveTo(68,39,84,23,111,22);g.bezierCurveTo(139,21,153,42,148,80);g.bezierCurveTo(129,68,93,68,72,78);g.closePath();
 g.fillStyle=linear(72,25,150,84,[[0,'#ffffff'],[.42,'#eef4f6'],[.8,'#c4d4dc'],[1,'#8ba5b1']]);g.fill();g.strokeStyle='#9db2bc';g.lineWidth=1.5;g.stroke();
 g.save();g.beginPath();g.ellipse(110,54,36,25,-.05,0,Math.PI*2);g.clip();
 g.strokeStyle='rgba(121,153,166,.38)';g.lineWidth=.8;
 for(let x=78;x<145;x+=7){g.beginPath();g.moveTo(x,30);g.lineTo(x+18,78);g.stroke();}
 for(let y=35;y<78;y+=7){g.beginPath();g.moveTo(75,y);g.lineTo(149,y+4);g.stroke();}
 g.restore();
 // Cejas, ojos y gafas protectoras.
 tube2d(88,86,101,85,2.5,'#59453c');tube2d(118,85,131,86,2.5,'#59453c');
 ellipse(95,94,4,4,'#263c4a');ellipse(124,94,4,4,'#263c4a');
 rounded(76,84,32,19,7,'rgba(143,208,224,.26)','#547f91',2);
 rounded(112,84,32,19,7,'rgba(143,208,224,.26)','#547f91',2);
 tube2d(108,92,112,92,3,'#547f91');
 // Mascarilla, pliegues y cintas.
 path([[79,106],[94,101],[127,101],[141,107],[135,132],[110,139],[85,131]],linear(80,104,138,136,[[0,'#ffffff'],[.5,'#dce9ed'],[1,'#9db6c1']]),'#91aab5',1.2);
 [113,120,127].forEach(y=>tube2d(91,y,131,y-1,1,'rgba(125,156,169,.38)'));
 tube2d(80,110,70,105,1.5,'#c5d9e0');tube2d(140,110,150,105,1.5,'#c5d9e0');

 // Accesorios diferentes para identificar cada rol.
 if(tech){
  // Cinturón de herramientas y llave de mantenimiento sostenida al costado.
  rounded(63,271,95,17,5,linear(63,271,159,287,[[0,'#35596d'],[.5,'#173e55'],[1,'#102e42']]));
  rounded(35,238,16,36,4,linear(35,238,51,274,[[0,'#aabac1'],[1,'#5e7784']]),'#526f7d');
  tube2d(39,245,48,245,2,'#e0e8eb');
  tube2d(179,236,190,283,7,linear(178,235,190,284,[[0,'#dce5e8'],[.5,'#7c929d'],[1,'#384f5c']]));
  tube2d(184,236,196,232,7,'#9aaeb8');
  rounded(85,294,50,12,4,'#27495e');
 }else{
  // Portapapeles en el brazo izquierdo de la supervisora.
  g.save();g.translate(44,222);g.rotate(-.12);
  rounded(-15,-4,34,62,5,linear(-15,-4,19,58,[[0,'#193f58'],[1,'#071f32']]),'#7896a4',2);
  rounded(-10,3,24,46,3,linear(-10,3,14,48,[[0,'#ffffff'],[1,'#d0e0e6']]));
  tube2d(-6,12,10,12,1.5,trim);tube2d(-6,21,10,21,1.5,'#8ba6b2');tube2d(-6,30,8,30,1.5,'#8ba6b2');
  g.restore();
  rounded(124,163,30,17,4,'#166d83');
 }
 // Brillo general y profundidad de luz lateral.
 const overlay=linear(48,45,180,380,[[0,'rgba(255,255,255,.16)'],[.4,'rgba(255,255,255,0)'],[1,'rgba(3,27,40,.13)']]);
 g.fillStyle=overlay;g.fillRect(0,0,c.width,c.height);
 return c;
}
function spriteCanvas(kind){
 if(kind==='tech'||kind==='supervisor')return make3DWorker(kind);
 const c=document.createElement('canvas');c.width=200;c.height=230;const g=c.getContext('2d');
 const round=(x,y,w,h,r,fill,stroke)=>{g.beginPath();g.roundRect(x,y,w,h,r);g.fillStyle=fill;g.fill();if(stroke){g.strokeStyle=stroke;g.lineWidth=3;g.stroke();}};
 if(kind==='locker'){
  round(22,30,156,175,8,'#8da9b7','#d7e6ec');g.fillStyle='#29495c';g.fillRect(32,40,136,155);
  for(let i=0;i<3;i++){g.fillStyle=['#48b9c6','#e7f1f3','#4a8c75'][i];g.fillRect(41+i*43,49,36,136);g.fillStyle='#17384a';g.fillRect(69+i*43,112,3,8);}
  g.fillStyle='#f4f8fa';g.font='bold 16px Arial';g.textAlign='center';g.fillText('EPP',100,22);
 }else if(kind==='tablet'||kind==='label'||kind==='bench'){
  round(13,76,174,105,13,'#8ea6b0','#e2eef2');round(28,52,144,48,9,kind==='label'?'#4c6f86':'#718e9c','#dce9ee');
  round(43,25,112,38,7,'#183e53','#78a2b6');
  g.fillStyle='#172d3a';g.fillRect(43,108,114,41);
  for(let i=0;i<5;i++){g.fillStyle=i===2&&kind==='label'?'#ff535d':'#54d3df';g.fillRect(52+i*19,116,10,10);}
  g.fillStyle='#eaf5f8';g.font='bold 13px Arial';g.textAlign='center';g.fillText(kind==='tablet'?'TABLETEADORA':kind==='label'?'ETIQUETADORA':'MANTENIMIENTO',100,203);
  g.fillStyle='#263f4c';g.fillRect(30,180,12,25);g.fillRect(158,180,12,25);
  if(kind==='label'){g.fillStyle='#ff424b';g.beginPath();g.arc(162,55,10,0,Math.PI*2);g.fill();}
 }else if(kind==='release'){
  round(18,95,164,87,10,'#567b91','#a8c8d8');round(30,50,140,55,8,'#0a2538','#62ddec');
  g.fillStyle='#59dc9c';g.fillRect(45,65,110,25);g.fillStyle='#fff';g.font='bold 13px Arial';g.textAlign='center';g.fillText('VERIFICACIÓN',100,82);
  g.fillStyle='#d6e8ef';g.fillRect(32,183,136,10);
 }else{
  // Personal de planta: bata, rostro, cofia y gafas.
  g.fillStyle='#d8e6ea';g.beginPath();g.moveTo(40,210);g.lineTo(52,105);g.quadraticCurveTo(100,75,148,105);g.lineTo(160,210);g.closePath();g.fill();g.strokeStyle='#6b8b9b';g.stroke();
  g.fillStyle='#c68d68';g.beginPath();g.arc(100,72,40,0,Math.PI*2);g.fill();
  g.fillStyle='#f3f7f8';g.beginPath();g.arc(100,44,43,Math.PI,Math.PI*2);g.fill();
  g.fillStyle='#173b53';g.fillRect(70,69,22,8);g.fillRect(108,69,22,8);
  g.fillStyle='#355d72';g.fillRect(96,105,8,88);
  g.fillStyle='#1a4258';g.font='bold 13px Arial';g.textAlign='center';g.fillText(kind==='tech'?'TÉCNICO':'SUPERVISORA',100,224);
  if(kind==='supervisor'){g.fillStyle='#62ddec';g.fillRect(130,120,24,42);}
 }
 return c;
}
const sprites=objects.map(o=>({...o,img:spriteCanvas(o.kind)}));
function castWalls(){
 const dirX=Math.cos(player.a),dirY=Math.sin(player.a),planeX=-dirY*Math.tan(FOV/2),planeY=dirX*Math.tan(FOV/2);
 const sky=ctx.createLinearGradient(0,0,0,H/2);sky.addColorStop(0,'#152f46');sky.addColorStop(1,'#8aa6b2');ctx.fillStyle=sky;ctx.fillRect(0,0,W,H/2);
 const floor=ctx.createLinearGradient(0,H/2,0,H);floor.addColorStop(0,'#667c83');floor.addColorStop(.35,'#314c58');floor.addColorStop(1,'#142c3b');ctx.fillStyle=floor;ctx.fillRect(0,H/2,W,H/2);
 // Perspectiva del piso: líneas que simulan baldosas de planta.
 ctx.strokeStyle='rgba(205,230,235,.11)';ctx.lineWidth=1;
 for(let y=H/2+18;y<H;y+=Math.max(7,(y-H/2)*.105)){ctx.beginPath();ctx.moveTo(0,y);ctx.lineTo(W,y);ctx.stroke();}
 for(let x=0;x<W;x+=95){ctx.beginPath();ctx.moveTo(W/2+(x-W/2)*.08,H/2);ctx.lineTo(x,H);ctx.stroke();}
 const stripe=1;
 for(let sx=0;sx<W;sx+=stripe){
  const cameraX=2*sx/W-1,rayX=dirX+planeX*cameraX,rayY=dirY+planeY*cameraX;
  let mapX=Math.floor(player.x),mapY=Math.floor(player.y);
  const deltaX=Math.abs(1/(rayX||.00001)),deltaY=Math.abs(1/(rayY||.00001));
  let stepX,stepY,sideX,sideY;
  if(rayX<0){stepX=-1;sideX=(player.x-mapX)*deltaX}else{stepX=1;sideX=(mapX+1-player.x)*deltaX}
  if(rayY<0){stepY=-1;sideY=(player.y-mapY)*deltaY}else{stepY=1;sideY=(mapY+1-player.y)*deltaY}
  let side=0,hit=false,guard=0;
  while(!hit&&guard++<40){
   if(sideX<sideY){sideX+=deltaX;mapX+=stepX;side=0}else{sideY+=deltaY;mapY+=stepY;side=1}
   if(map[mapY]?.[mapX]==='#'||!map[mapY]?.[mapX])hit=true;
  }
  let dist=side===0?sideX-deltaX:sideY-deltaY;dist=Math.max(.08,dist);zbuffer[sx]=dist;
  const lineH=Math.min(H*2,H/dist),start=Math.max(0,(H-lineH)/2),end=Math.min(H,(H+lineH)/2);
  let shade=Math.max(.24,1-dist/13)*(side===1?.78:1);
  const alternate=(Math.floor((side===0?player.y+rayY*dist:player.x+rayX*dist)*3)%2===0);
  const base=alternate?[110,144,157]:[91,126,141];
  const red=Math.floor(base[0]*shade),green=Math.floor(base[1]*shade),blue=Math.floor(base[2]*shade);
  ctx.fillStyle=`rgb(${red},${green},${blue})`;ctx.fillRect(sx,start,stripe+1,end-start);
  ctx.fillStyle=`rgba(225,245,250,${.09*shade})`;ctx.fillRect(sx,start,stripe+1,Math.max(2,lineH*.012));
  ctx.fillStyle=`rgba(5,22,34,${.14})`;ctx.fillRect(sx,end-2,stripe+1,2);
 }
}
function drawSprites(){
 const dirX=Math.cos(player.a),dirY=Math.sin(player.a),planeX=-dirY*Math.tan(FOV/2),planeY=dirX*Math.tan(FOV/2);
 const inv=1/(planeX*dirY-dirX*planeY);
 const list=sprites.map(s=>({...s,dist:Math.hypot(s.x-player.x,s.y-player.y)})).sort((a,b)=>b.dist-a.dist);
 for(const s of list){
  const dx=s.x-player.x,dy=s.y-player.y;
  const tx=inv*(dirY*dx-dirX*dy),ty=inv*(-planeY*dx+planeX*dy);
  if(ty<=.18||ty>MAX_DEPTH)continue;
  const screenX=W/2*(1+tx/ty);
  let height=Math.abs(H/ty)*s.h*.72;
  if(s.npc)height=Math.min(height,300); // evita que el personal ocupe toda la pantalla cuando está cerca
  const width=height*(s.w/s.h)*.88;
  const top=H/2-height*.66,left=screenX-width/2;
  const x0=Math.max(0,Math.floor(left)),x1=Math.min(W,Math.ceil(left+width));
  // Dibuja solo las columnas que no están tapadas por una pared.
  // Esto evita que los equipos y el personal desaparezcan por un z-buffer incompleto.
  const xa=Math.max(0,Math.floor(left)),xb=Math.min(W,Math.ceil(left+width));
  let visibleStart=-1;
  for(let px=xa;px<=xb;px++){
   const visible=px<xb && ty<zbuffer[px];
   if(visible && visibleStart<0)visibleStart=px;
   if(!visible && visibleStart>=0){
    const segmentWidth=px-visibleStart;
    const sourceX=Math.max(0,(visibleStart-left)/width*s.img.width);
    const sourceEnd=Math.min(s.img.width,(px-left)/width*s.img.width);
    const sourceWidth=Math.max(.1,sourceEnd-sourceX);
    ctx.drawImage(s.img,sourceX,0,sourceWidth,s.img.height,visibleStart,top,segmentWidth,height);
    visibleStart=-1;
   }
  }
  // Indicator name over the target when it is the next station.
  if(currentTask()&&s.id===currentTask().object&&s.dist<5){
   const alpha=Math.max(0,1-s.dist/5);ctx.fillStyle=`rgba(255,239,156,${alpha})`;ctx.font='bold 15px Arial';ctx.textAlign='center';
   ctx.fillText('▼ '+s.name,screenX,top-10);
  }
 }
}
function drawHands(){
 const t=currentTask(),tool=t?t.tool:'GUARDADA';
 ctx.save();
 // Mangas y guantes vistos desde los ojos del personaje.
 ctx.fillStyle='#d8e8ed';ctx.beginPath();ctx.moveTo(0,H);ctx.lineTo(0,H-18);ctx.lineTo(120,H-75);ctx.lineTo(240,H);ctx.closePath();ctx.fill();
 ctx.beginPath();ctx.moveTo(W,H);ctx.lineTo(W,H-18);ctx.lineTo(W-120,H-75);ctx.lineTo(W-240,H);ctx.closePath();ctx.fill();
 ctx.fillStyle='#28566a';ctx.beginPath();ctx.ellipse(190,H-36,66,31,-.15,0,Math.PI*2);ctx.fill();ctx.beginPath();ctx.ellipse(W-190,H-36,66,31,.15,0,Math.PI*2);ctx.fill();
 ctx.strokeStyle='#b8d2dc';ctx.lineWidth=4;ctx.beginPath();ctx.moveTo(240,H-32);ctx.lineTo(W-240,H-32);ctx.stroke();
 // Herramienta visible en primer plano, cambia con la tarea.
 if(step===2){ctx.save();ctx.translate(W/2+42,H-94);ctx.rotate(-.35);ctx.fillStyle='#9caeb7';ctx.fillRect(-8,-65,16,104);ctx.fillStyle='#dce8ec';ctx.fillRect(-34,-70,68,15);ctx.restore();}
 else if(step===3){ctx.fillStyle='#233c4c';ctx.fillRect(W/2+25,H-112,33,76);ctx.fillStyle='#f5e7a2';ctx.fillRect(W/2+30,H-122,23,12);ctx.fillStyle='#fff8c7';ctx.globalAlpha=.22;ctx.beginPath();ctx.moveTo(W/2+42,H-122);ctx.lineTo(W/2+170,H-210);ctx.lineTo(W/2+135,H-80);ctx.closePath();ctx.fill();ctx.globalAlpha=1;}
 else if(step===1||step===4){ctx.fillStyle='#1c3548';ctx.fillRect(W/2+25,H-114,66,80);ctx.fillStyle='#67ddeb';ctx.fillRect(W/2+34,H-104,48,52);ctx.fillStyle='#163245';ctx.fillRect(W/2+38,H-95,40,5);ctx.fillRect(W/2+38,H-83,32,4);}
 else{ctx.fillStyle='#b9ced6';ctx.beginPath();ctx.roundRect(W/2-18,H-90,36,55,7);ctx.fill();}
 ctx.restore();
}
function draw(){
 frame++;
 castWalls();drawSprites();
 // Haz de linterna desde la perspectiva del personaje: centro visible y periferia en sombra.
 const beam=ctx.createRadialGradient(W*.51,H*.48,24,W*.51,H*.48,W*.68);
 beam.addColorStop(0,'rgba(224,242,244,.14)');
 beam.addColorStop(.22,'rgba(177,213,221,.07)');
 beam.addColorStop(.62,'rgba(3,10,16,.10)');
 beam.addColorStop(1,'rgba(0,0,0,.58)');
 ctx.fillStyle=beam;ctx.fillRect(0,0,W,H);
 // Grano/scanline muy sutil para dar una sensación de cámara cinematográfica.
 if(frame%3===0){ctx.fillStyle='rgba(205,225,232,.018)';for(let y=0;y<H;y+=4)ctx.fillRect(0,y,W,1);}
 drawHands();
 const vignette=ctx.createRadialGradient(W/2,H/2,H*.16,W/2,H/2,H*.8);
 vignette.addColorStop(0,'rgba(0,0,0,0)');vignette.addColorStop(1,'rgba(0,0,0,.48)');
 ctx.fillStyle=vignette;ctx.fillRect(0,0,W,H);
 if(step===3||plantState.risk>=65||plantState.incident){
  ctx.fillStyle=`rgba(255,18,32,${.045+Math.abs(Math.sin(frame*.08))*.09})`;
  ctx.fillRect(0,0,W,H);
 }
}
function tick(){if(gameStarted){draw();}requestAnimationFrame(tick);}
function bindHold(id,fn){
 const el=document.getElementById(id);let timer=null;
 const run=()=>{if(!gameStarted||modalOpen||autowalking)return;fn();draw();updateHud();};
 el.addEventListener('click',run);
 el.addEventListener('touchstart',e=>{e.preventDefault();run();},{passive:false});
}
document.getElementById('startBtn').addEventListener('click',()=>{
 startAudio();gameStarted=true;document.getElementById('intro').classList.add('hidden');
 document.getElementById('message').textContent='Has entrado a la planta desde la perspectiva del personaje. Dirígete al vestier para verificar el EPP.';
 draw();updateHud();
});
document.getElementById('forward').addEventListener('click',()=>{if(!modalOpen&&!autowalking){moveForward(.42);draw();updateHud();}});
document.getElementById('backward').addEventListener('click',()=>{if(!modalOpen&&!autowalking){moveForward(-.36);draw();updateHud();}});
document.getElementById('turnLeft').addEventListener('click',()=>{if(!modalOpen&&!autowalking){rotate(-.22);draw();updateHud();}});
document.getElementById('turnRight').addEventListener('click',()=>{if(!modalOpen&&!autowalking){rotate(.22);draw();updateHud();}});
document.getElementById('approachBtn').addEventListener('click',approach);
document.getElementById('useBtn').addEventListener('click',interact);
document.getElementById('confirmTask').addEventListener('click',completeTask);
document.getElementById('closeTask').addEventListener('click',closeTask);
document.getElementById('dashboardBtn').addEventListener('click',showDashboard);
document.getElementById('closeDash').addEventListener('click',closeDashboard);
document.getElementById('restartFromDash').addEventListener('click',()=>{reset();});
document.getElementById('resetBtn').addEventListener('click',reset);
document.getElementById('soundBtn').addEventListener('click',()=>{
 muted=!muted;document.getElementById('soundBtn').textContent=muted?'🔇 Sonido desactivado':'🔊 Sonido activado';if(!muted)startAudio();
});
document.addEventListener('keydown',e=>{
 if(!gameStarted)return;
 if(['ArrowUp','ArrowDown','ArrowLeft','ArrowRight',' '].includes(e.key))e.preventDefault();
 if(modalOpen){if(e.key==='Escape')closeTask();return;}
 const k=e.key.toLowerCase();
 if(k==='w'||k==='arrowup')moveForward(.28);
 if(k==='s'||k==='arrowdown')moveForward(-.24);
 if(k==='a'||k==='arrowleft')rotate(-.12);
 if(k==='d'||k==='arrowright')rotate(.12);
 if(k==='e'||k===' '||k==='enter')interact();
 draw();updateHud();
});
renderTasks();renderKpis('kpis');updateHud();draw();requestAnimationFrame(tick);
})();
</script>
</body>
</html>
