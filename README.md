<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Drone + Rover Crop Scout</title>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:wght@400;600;800&display=swap">
<style>
:root{--bg:#f2f6ec;--ink:#1f2a17;--mute:#56634b;--card:#fff;--line:#d3ddc6;--leaf:#2f6b1f;--lime:#b5d334;--soil:#241c14;--onsoil:#f2f6ec;
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#141a10;--ink:#e8efdc;--mute:#9aa88b;--card:#1d2617;--line:#2f3b26;--leaf:#8cc65a;--soil:#0c0f08}}
:root[data-theme="dark"]{--bg:#141a10;--ink:#e8efdc;--mute:#9aa88b;--card:#1d2617;--line:#2f3b26;--leaf:#8cc65a;--soil:#0c0f08}
*{box-sizing:border-box}html{scroll-padding-top:env(safe-area-inset-top,0px)}
body{margin:0;background:var(--bg);color:var(--ink);font:17px/1.55 "Bricolage Grotesque",system-ui,sans-serif}
.wrap{max-width:1040px;margin:0 auto;padding:0 22px}
.hero{background:var(--soil);color:var(--onsoil);overflow:hidden}
.hero .wrap{padding-top:44px}
h1{font-size:clamp(38px,7.5vw,78px);line-height:1;letter-spacing:-.03em;font-weight:800;margin:0 0 18px;max-width:12em}
.hero p{max-width:36em;color:#c9d6b8;margin:0 0 8px}
.field{display:block;width:100%;height:auto;margin-top:30px}
.drone{animation:fly 9s ease-in-out infinite alternate}
@keyframes fly{to{transform:translateX(560px)}}
@media (prefers-reduced-motion:reduce){.drone{animation:none}}
section{padding:60px 0}
h2{font-size:clamp(27px,4.5vw,40px);letter-spacing:-.02em;line-height:1.1;margin:0 0 12px}
.lead{color:var(--mute);max-width:38em;margin:0 0 30px}
.flow{list-style:none;margin:0;padding:0;display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));gap:0;counter-reset:s}
.flow li{counter-increment:s;padding:16px 14px 16px 0;border-top:3px solid var(--leaf);font-weight:600}
.flow li::before{content:counter(s);display:block;color:var(--leaf);font-size:28px;font-weight:800;line-height:1.1}
.flow li span{display:block;font-weight:400;color:var(--mute);font-size:15px}
.band{background:var(--card);border-block:1px solid var(--line)}
.two{display:grid;grid-template-columns:1fr 1fr;gap:48px}
@media(max-width:820px){.two{grid-template-columns:1fr}}
h3{margin:0 0 4px;font-size:24px}
.tag{color:var(--mute);font-size:15px;margin:0 0 14px}
table{border-collapse:collapse;width:100%}
th{text-align:left;font-size:14px;color:var(--mute);font-weight:600;padding:6px 0;border-bottom:2px solid var(--leaf)}
td{padding:11px 12px 11px 0;border-bottom:1px solid var(--line);vertical-align:top;font-size:16px}
td:first-child{font-weight:600;white-space:nowrap;padding-right:16px}
@media(max-width:520px){td:first-child{white-space:normal}}
.safe{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:26px}
.safe div{border-left:3px solid var(--lime);padding-left:14px}
.safe b{display:block}
.safe span{color:var(--mute);font-size:15px}
footer{padding:40px 0;color:var(--mute);font-size:15px;border-top:1px solid var(--line)}

.live{display:grid;grid-template-columns:1fr 1fr;gap:40px}
@media(max-width:820px){.live{grid-template-columns:1fr}}
.box{background:var(--card);border:1px solid var(--line);border-radius:10px;padding:20px}
.box label{display:block;font-size:14px;color:var(--mute);margin:10px 0 4px}
.box input,.box textarea{width:100%;font:inherit;font-size:16px;padding:9px 11px;border:1px solid var(--line);border-radius:6px;background:var(--bg);color:var(--ink)}
.box button{margin-top:14px;background:var(--lime);color:#1b2410;font:inherit;font-weight:600;border:0;border-radius:999px;padding:11px 22px;cursor:pointer}
.box button:focus-visible,.box input:focus-visible,.box textarea:focus-visible{outline:3px solid var(--lime);outline-offset:2px}
.big{font-size:clamp(40px,7vw,60px);font-weight:800;color:var(--leaf);line-height:1;margin:10px 0 4px}
#ans{white-space:pre-wrap;margin-top:14px;font-size:16px}
.note{font-size:14px;color:var(--mute);margin-top:10px}
</style>
</head>
<body>
<div class="hero"><div class="wrap">
 <h1>A drone finds weak plants. A rover checks the soil.</h1>
 <p>A low-cost farm scouting system. The drone scans the crop from above and marks weak spots with GPS. The rover drives to each spot, measures the soil, and waters it.</p>
 <svg class="field" viewBox="0 0 1040 190" aria-hidden="true" preserveAspectRatio="xMidYMax slice">
  <path d="M0 190H1040V140H0Z" fill="#2c3a1d"/><path d="M0 140H1040V110H0Z" fill="#3f6b2a"/>
  <path d="M0 110H1040V84H0Z" fill="#6f9a2f"/><path d="M0 84H1040V68H0Z" fill="#86ab38"/>
  <path d="M300 110H520L480 84H330Z" fill="#c9a62e"/><path d="M380 140H560L520 110H410Z" fill="#b5d334"/>
  <g class="drone" transform="translate(120 28)">
   <path d="M0 0L-24 56H24Z" fill="#b5d334" opacity=".18"/>
   <rect x="-16" y="-4" width="32" height="10" rx="5" fill="#f2f6ec"/>
   <path d="M-30 -8H-8M8 -8H30" stroke="#f2f6ec" stroke-width="3" stroke-linecap="round"/>
  </g>
 </svg>
</div></div>

<section><div class="wrap">
 <h2>How the mission runs</h2>
 <p class="lead">The drone and rover work as a team. Weak spots found in the air become the rover’s to-do list on the ground.</p>
 <ol class="flow">
  <li>Fly<span>Drone is flown manually over the field</span></li>
  <li>Scan<span>Camera scores plant greenness</span></li>
  <li>Mark<span>Weak images get a GPS position</span></li>
  <li>Send<span>Radio link passes spots to the rover</span></li>
  <li>Visit<span>Rover drives to the nearest cell first</span></li>
  <li>Measure<span>Moisture, pH, soil temperature</span></li>
  <li>Report<span>Field table on a web page</span></li>
 </ol>
</div></section>

<section class="band"><div class="wrap two">
 <div>
  <h3>Drone</h3><p class="tag">Scans the crop and marks weak spots</p>
  <table><tr><th>Feature</th><th>How it works</th></tr>
   <tr><td>Manual flight</td><td>APM 2.8 flown with the FlySky transmitter in Stabilize mode</td></tr>
   <tr><td>Plant health scan</td><td>ESP32-CAM looks down and scores greenness (2G − R − B) and plant cover</td></tr>
   <tr><td>Weak spot marking</td><td>Weak images are tagged WEAK with a GPS position from the NEO-6M</td></tr>
   <tr><td>SD card log</td><td>Every reading is saved as log.csv, as a backup</td></tr>
   <tr><td>Long-range data link</td><td>ESP8266 + nRF24L01+PA sends weak spots to the rover, several hundred metres in open ground</td></tr>
   <tr><td>Live while flying</td><td>The rover’s weak-spot count goes up during the flight</td></tr>
   <tr><td>Light and cheap</td><td>ESP32-CAM is about 10 g, so the 920 kV motors carry it easily</td></tr>
  </table>
 </div>
 <div>
  <h3>Rover</h3><p class="tag">Visits each weak spot and tests the soil</p>
  <table><tr><th>Feature</th><th>How it works</th></tr>
   <tr><td>Manual control by phone</td><td>WiFi hotspot and web page with drive buttons, speed slider, and a STOP button</td></tr>
   <tr><td>Automatic mission</td><td>Receives the weak spots, groups them into 5 m cells, and visits the nearest cell first</td></tr>
   <tr><td>GPS navigation</td><td>Drives in steps, works out its direction from the GPS course, and corrects with timed turns (no compass)</td></tr>
   <tr><td>Soil measurement</td><td>Moisture, pH, and soil temperature at each weak cell</td></tr>
   <tr><td>Pump</td><td>Waters a spot from the web page (auto-off after 10 seconds)</td></tr>
   <tr><td>Servo</td><td>Moves the probe or the pump nozzle</td></tr>
   <tr><td>Buzzer</td><td>Beeps on start, on arrival at each cell, and when the mission ends</td></tr>
   <tr><td>MANUAL / AUTO switch</td><td>Only one mode controls the motors, and STOP returns to manual at once</td></tr>
   <tr><td>Return home</td><td>Goes back to the saved start point after the mission</td></tr>
   <tr><td>Field report</td><td>A web page table with cell number, position, moisture, pH, and temperature</td></tr>
   <tr><td>Auto start</td><td>The program starts when the battery is switched on</td></tr>
  </table>
 </div>
</div></section>

<section><div class="wrap">
 <h2>Built to fail safely</h2>
 <p class="lead">The rover is designed to stop rather than guess.</p>
 <div class="safe">
  <div><b>Phone goes silent</b><span>The rover stops.</span></div>
  <div><b>Cell takes too long</b><span>It gives up after 5 minutes and moves on.</span></div>
  <div><b>Anything goes wrong</b><span>STOP returns to manual control at once.</span></div>
  <div><b>Main battery switch</b><span>Cuts all power.</span></div>
 </div>
</div></section>

<section class="band"><div class="wrap">
 <h2>Live weather and farm advice</h2>
 <p class="lead">Weather comes from OpenWeather. The AI advisor uses Gemini, the weather, and the rover’s soil readings to suggest what to do.</p>
 <div class="live">
  <div class="box" id="wx">
   <h3>Weather in <span id="cityName">Chennai, IN</span></h3>
   <div class="big" id="temp">--</div><div id="desc">Enter your OpenWeather key and press Get weather.</div>
   <div class="note" id="more"></div>
   <label for="owkey">OpenWeather API key</label><input id="owkey" type="password" autocomplete="off">
   <button id="getwx">Get weather</button>
  </div>
  <div class="box">
   <h3>Agri AI advisor</h3>
   <label for="moist">Soil moisture (%)</label><input id="moist" inputmode="decimal">
   <label for="ph">Soil pH</label><input id="ph" inputmode="decimal">
   <label for="st">Soil temperature (°C)</label><input id="st" inputmode="decimal">
   <label for="q">Question (optional)</label><textarea id="q" rows="2" placeholder="Should I water this weak spot today?"></textarea>
   <label for="gkey">Gemini API key (optional, built-in key is used if empty)</label><input id="gkey" type="password" autocomplete="off">
   <button id="ask">Ask AI</button>
   <div id="ans" aria-live="polite"></div>
  </div>
 </div>
 <p class="note">The Gemini key is built into this page. The OpenWeather key is typed here and kept only in this browser.</p>
</div></section>

<footer><div class="wrap">Drone and rover crop scouting project. Built with APM 2.8, ESP32-CAM, NEO-6M GPS, ESP8266 and nRF24L01+PA.</div></footer>

<script>
const CITY="Chennai",COUNTRY="IN",MODEL="gemini-3.8-flash";
const GEMINI_KEY="AQ.Ab8RN6LYUd9D8GgN6h7y_CbCuljUVgfW-IuAbK10tFPlg-NClA";
let wxText="Weather not loaded.";
const $=id=>document.getElementById(id);
for(const [id,k] of [["owkey","ow"],["gkey","gm"]]){try{$(id).value=localStorage.getItem(k)||""}catch(e){}}
function save(k,v){try{localStorage.setItem(k,v)}catch(e){}}

$("getwx").onclick=async()=>{
 const key=$("owkey").value.trim();if(!key){$("desc").textContent="Enter your OpenWeather key first.";return}
 save("ow",key);$("desc").textContent="Loading...";
 try{
  const r=await fetch(`https://api.openweathermap.org/data/2.5/weather?q=${CITY},${COUNTRY}&units=metric&appid=${encodeURIComponent(key)}`);
  const d=await r.json();if(!r.ok)throw new Error(d.message||r.status);
  $("temp").textContent=Math.round(d.main.temp)+"°C";
  $("desc").textContent=d.weather[0].description;
  $("more").textContent=`Humidity ${d.main.humidity}% · Wind ${d.wind.speed} m/s · Feels like ${Math.round(d.main.feels_like)}°C`;
  wxText=`${CITY}: ${d.main.temp}°C, ${d.weather[0].description}, humidity ${d.main.humidity}%, wind ${d.wind.speed} m/s.`;
 }catch(e){$("desc").textContent="Could not load weather: "+e.message}
};

$("ask").onclick=async()=>{
 const key=$("gkey").value.trim()||GEMINI_KEY;
 save("gm",$("gkey").value.trim());$("ans").textContent="Thinking...";
 const prompt=`You are an agriculture advisor for a small farm using a scouting drone and soil rover.
Weather: ${wxText}
Soil at a weak spot: moisture ${$("moist").value||"unknown"}%, pH ${$("ph").value||"unknown"}, temperature ${$("st").value||"unknown"}°C.
Question: ${$("q").value||"What should the farmer do for this weak spot?"}
Answer in under 120 words with 3 short, practical steps.`;
 const url=`https://generativelanguage.googleapis.com/v1beta/models/${MODEL}:generateContent`;
 const opts={method:"POST",headers:{"Content-Type":"application/json","x-goog-api-key":key},body:JSON.stringify({contents:[{parts:[{text:prompt}]}]})};
 let err="";
 for(let i=1;i<=4;i++){
  try{
   const r=await fetch(url,opts);const d=await r.json();
   if(r.ok){$("ans").textContent=d.candidates[0].content.parts.map(p=>p.text).join("");return}
   err=d.error?.message||r.status;
   if(![429,500,503,504].includes(r.status))break;
  }catch(e){err=e.message}
  $("ans").textContent=`AI is busy. Retrying (${i}/3)...`;
  await new Promise(t=>setTimeout(t,i*2500));
 }
 $("ans").textContent="AI request failed: "+err+"\nWait a minute and press Ask AI again.";
};
</script>
</body>
</html>
