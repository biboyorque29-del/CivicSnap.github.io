<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>CivicSnap – Snap. Report. Improve.</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
:root{--pri:#2563EB;--sec:#10B981;--acc:#F59E0B;--bg:#F8FAFC;--tx:#1E293B;--card:#fff;--mut:#64748B;--bd:#E2E8F0;--red:#DC2626;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#0F172A;--tx:#E2E8F0;--card:#1E293B;--mut:#94A3B8;--bd:#334155}}
:root[data-theme="dark"]{--bg:#0F172A;--tx:#E2E8F0;--card:#1E293B;--mut:#94A3B8;--bd:#334155}
*{box-sizing:border-box}html{scroll-padding-top:env(safe-area-inset-top,0px)}
body{margin:0;background:var(--bg);color:var(--tx);font-family:Poppins,Inter,system-ui,sans-serif;line-height:1.55}
button,input,select,textarea{font:inherit;color:inherit}
:focus-visible{outline:2px solid var(--pri);outline-offset:2px}
header{position:sticky;top:env(safe-area-inset-top,0px);z-index:20;background:var(--card);border-bottom:1px solid var(--bd);display:flex;flex-wrap:wrap;align-items:center;gap:.5rem 1rem;padding:.6rem 1rem}
.logo{font-weight:700;font-size:1.2rem;color:var(--pri);background:none;border:0;cursor:pointer}
nav{display:flex;gap:.25rem;flex:1;flex-wrap:wrap}
nav button,.btn{border:1px solid transparent;background:none;border-radius:8px;padding:.45rem .8rem;cursor:pointer}
nav button.on{background:var(--pri);color:#fff}
.btn{background:var(--pri);color:#fff;font-weight:500}.btn.alt{background:none;color:var(--pri);border-color:var(--pri)}.btn.sm{padding:.25rem .6rem;font-size:.8rem}.btn.g{background:var(--sec)}
select,input,textarea{background:var(--card);border:1px solid var(--bd);border-radius:8px;padding:.5rem .7rem;width:100%}
.tools{display:flex;gap:.5rem;align-items:center}.tools select{width:auto}
main{max-width:1000px;margin:0 auto;padding:1rem}
.hero{background:linear-gradient(135deg,var(--pri),#1D4ED8);color:#fff;border-radius:16px;padding:2.5rem 1.5rem;margin-bottom:1.5rem}
.hero h1{font-size:clamp(2rem,6vw,3.2rem);margin:0}.hero .tag{font-size:1.2rem;color:#FDE68A;margin:.2rem 0 1rem}.hero p{max-width:60ch;margin:0 0 1.2rem}
.hero .btn{background:var(--acc);color:#1E293B}.hero .btn.alt{background:none;color:#fff;border-color:#fff}
.grid{display:grid;gap:1rem;grid-template-columns:repeat(auto-fit,minmax(200px,1fr))}
.card{background:var(--card);border:1px solid var(--bd);border-radius:12px;padding:1rem}
.card h3{margin:0 0 .3rem;font-size:1rem}.card p{margin:0;color:var(--mut);font-size:.9rem}
.num{font-size:1.9rem;font-weight:700;color:var(--pri)}
h2{margin:1.8rem 0 .8rem}
.badge{display:inline-block;padding:.1rem .6rem;border-radius:99px;font-size:.78rem;font-weight:600}
.Pending{background:#FEF3C7;color:#92400E}.In-Progress{background:#DBEAFE;color:#1E40AF}.Resolved{background:#D1FAE5;color:#065F46}.Rejected{background:#FEE2E2;color:#991B1B}
.pr{font-size:.8rem;color:var(--mut)}.pr.Critical{color:var(--red);font-weight:600}
label{display:block;font-weight:500;margin:.8rem 0 .25rem;font-size:.9rem}
.row{display:grid;gap:1rem;grid-template-columns:repeat(auto-fit,minmax(220px,1fr))}
.filters{display:grid;gap:.5rem;grid-template-columns:repeat(auto-fit,minmax(130px,1fr));margin-bottom:1rem}
.rep{display:flex;flex-direction:column;gap:.35rem;margin-bottom:.8rem}
.rep .top{display:flex;justify-content:space-between;gap:.5rem;align-items:start}
.rep .act{display:flex;gap:.4rem;flex-wrap:wrap;align-items:center}.rep .act select{width:auto;padding:.25rem .5rem;font-size:.8rem}
.thumbs{display:flex;gap:.4rem;flex-wrap:wrap}.thumbs img{width:64px;height:64px;object-fit:cover;border-radius:8px}
.bars{display:flex;align-items:end;gap:.5rem;height:150px;border-bottom:1px solid var(--bd)}
.bars div{flex:1;background:var(--pri);border-radius:6px 6px 0 0;position:relative;min-height:4px}
.bars span{position:absolute;top:-1.3rem;left:0;right:0;text-align:center;font-size:.75rem}
.bl{display:flex;gap:.5rem}.bl small{flex:1;text-align:center;color:var(--mut)}
.pie{width:150px;height:150px;border-radius:50%;flex:none}
.pw{display:flex;gap:1rem;align-items:center;flex-wrap:wrap}.lg{font-size:.82rem;list-style:none;margin:0;padding:0}.lg i{display:inline-block;width:10px;height:10px;border-radius:3px;margin-right:.4rem}
.bell{position:relative}.bell b{position:absolute;top:-2px;right:-2px;background:var(--red);color:#fff;border-radius:99px;font-size:.65rem;padding:0 .35rem}
#np{position:absolute;right:1rem;top:100%;width:min(320px,92vw);max-height:60vh;overflow:auto;display:none;box-shadow:0 8px 24px rgba(0,0,0,.18)}
#np .n{padding:.5rem 0;border-bottom:1px solid var(--bd);font-size:.85rem}#np .n.u{font-weight:600}
.toast{position:fixed;bottom:calc(1rem + env(safe-area-inset-bottom,0px));left:50%;transform:translateX(-50%);background:var(--tx);color:var(--bg);padding:.6rem 1rem;border-radius:8px;z-index:50}
.hide{display:none!important}
footer{text-align:center;color:var(--mut);font-size:.8rem;padding:2rem 1rem}
@media (prefers-reduced-motion:no-preference){.hero{animation:in .5s ease-out}@keyframes in{from{opacity:0;transform:translateY(8px)}}}
</style>
</head>
<body>
<header>
<button class="logo" onclick="go('home')">📸 CivicSnap</button>
<nav id="nav"></nav>
<div class="tools">
<select id="role" aria-label="Sign in as"><option>Student</option><option>Teacher</option><option>Administrator</option><option>Maintenance</option></select>
<button class="btn alt sm bell" id="bell" aria-label="Notifications">🔔<b id="bc">0</b></button>
<button class="btn alt sm" id="th" aria-label="Toggle dark mode">🌙</button>
</div>
<div id="np" class="card"></div>
</header>
<main id="app"></main>
<footer>CivicSnap for Ilaya Barangka Integrated School. Demo prototype: sign-in is simulated and data stays in this page.</footer>
<script>
const CATS=["Classroom Damage","Furniture Damage","Electrical Issues","Plumbing Problems","Sanitation Concerns","Safety Hazards","Other Concerns"];
const PRI=["Low","Medium","High","Critical"],ST=["Pending","In Progress","Resolved","Rejected"];
const COL=["#2563EB","#10B981","#F59E0B","#8B5CF6","#EC4899","#EF4444","#64748B"];
const STAFF=["Mang Ruel","Mang Tonio","Mr. Santos"];
let me={role:"Student",name:"Student"},view="home",nid=6,notes=[],imgs=[];
const d=(m,day)=>new Date(2026,m,day,9,30).toISOString();
let R=[
{id:1,title:"Broken armchair in Grade 8-Rizal",cat:CATS[1],desc:"Two armchairs have loose legs.",loc:"Room 204",pri:"Medium",st:"Pending",by:"Student",to:"",at:d(10,18),img:[]},
{id:2,title:"Flickering ceiling light",cat:CATS[2],desc:"Light flickers all day and gives students headaches.",loc:"Room 112",pri:"High",st:"In Progress",by:"Teacher",to:"Mang Ruel",at:d(10,12),img:[]},
{id:3,title:"Leaking faucet in comfort room",cat:CATS[3],desc:"Constant dripping, wet floor.",loc:"Ground floor CR",pri:"High",st:"Resolved",by:"Student",to:"Mang Tonio",at:d(9,28),img:[]},
{id:4,title:"Exposed wires near stage",cat:CATS[5],desc:"Wires hanging beside the stage outlet.",loc:"Covered court",pri:"Critical",st:"In Progress",by:"Teacher",to:"Mr. Santos",at:d(10,20),img:[]},
{id:5,title:"Overflowing trash bins",cat:CATS[4],desc:"Bins near the canteen are full by noon.",loc:"Canteen",pri:"Low",st:"Resolved",by:"Student",to:"Mang Tonio",at:d(8,30),img:[]},
{id:6,title:"Cracked windowpane",cat:CATS[0],desc:"Crack running across the lower pane.",loc:"Room 301",pri:"Medium",st:"Rejected",by:"Teacher",to:"",at:d(7,14),img:[]}];
const $=s=>document.querySelector(s),esc=s=>String(s).replace(/[&<>"]/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;"}[c]));
const fmt=i=>new Date(i).toLocaleString("en-PH",{dateStyle:"medium",timeStyle:"short"});
const cls=s=>s.replace(" ","-");
function toast(t){const e=document.createElement("div");e.className="toast";e.textContent=t;document.body.appendChild(e);setTimeout(()=>e.remove(),2200)}
function notify(m){notes.unshift({m,u:1,t:new Date().toISOString()});drawBell()}
function drawBell(){const u=notes.filter(n=>n.u).length;$("#bc").textContent=u;$("#bc").classList.toggle("hide",!u);
$("#np").innerHTML="<strong>Notifications</strong>"+(notes.length?notes.map(n=>`<div class="n ${n.u?"u":""}">${esc(n.m)}<br><small>${fmt(n.t)}</small></div>`).join(""):"<p>No notifications yet. You will see updates on your reports here.</p>")}
$("#bell").onclick=()=>{const p=$("#np");const o=p.style.display==="block";p.style.display=o?"none":"block";if(o){notes.forEach(n=>n.u=0);drawBell()}};
$("#role").onchange=e=>{me={role:e.target.value,name:e.target.value};const ok=allowed();if(!ok.includes(view))view=ok[0];notes=[];drawBell();render();toast("Signed in as "+me.role)};
function allowed(){const r=me.role;return r==="Administrator"?["dashboard","reports","users"]:r==="Maintenance"?["reports"]:["home","report","reports"]}
$("#th").onclick=()=>{const dk=getComputedStyle(document.body).backgroundColor==="rgb(15, 23, 42)";const t=dk?"light":"dark";document.documentElement.dataset.theme=t;$("#th").textContent=dk?"🌙":"☀️"};
function go(v){if(!allowed().includes(v)&&v!=="home"){return}view=v;render();window.scrollTo(0,0)}
function mine(){return me.role==="Administrator"?R:me.role==="Maintenance"?R.filter(r=>r.to===STAFF[0]):R.filter(r=>r.by===me.role)}
function badge(s){return `<span class="badge ${cls(s)}">${s}</span>`}
function render(){
const nav={home:"Home",report:"Report a concern",reports:me.role==="Administrator"?"All reports":me.role==="Maintenance"?"Assigned to me":"My reports",dashboard:"Dashboard",users:"Users"};
const list=me.role==="Administrator"||me.role==="Maintenance"?allowed():["home",...allowed().filter(x=>x!=="home")];
$("#nav").innerHTML=list.map(k=>`<button class="${view===k?"on":""}" onclick="go('${k}')">${nav[k]}</button>`).join("");
const v={home,report,reports,dashboard,users}[view];$("#app").innerHTML=v();if(view==="report")bindForm();if(view==="reports")bindFilters();}
function home(){const b=[["Faster reporting","Submit concerns anytime and anywhere."],["Transparency","Monitor the progress of every report."],["Better communication","Connect students, teachers, and administrators."],["Safer school environment","Help maintain a conducive learning atmosphere."]];
const s=[["500+","Reports submitted"],["90%","Resolution rate"],["1,200","Active users"],["24 hours","Average response time"]];
return `<section class="hero"><h1>CivicSnap</h1><div class="tag">Snap. Report. Improve.</div><p>CivicSnap is a digital reporting platform that empowers students, teachers, and school personnel to quickly report and monitor school facility concerns. By connecting issue reporting with efficient resolution, CivicSnap promotes transparency, accountability, and a safer learning environment for everyone.</p><button class="btn" onclick="go('report')">Report a concern</button> <button class="btn alt" onclick="document.getElementById('about').scrollIntoView({behavior:'smooth'})">Learn more</button></section>
<h2 id="about">About CivicSnap</h2><div class="card"><p>CivicSnap aims to solve the problem of delayed and inefficient reporting of school facility concerns. Traditional reporting methods often rely on verbal communication or written notes, resulting in delayed actions and unresolved issues.</p><p style="margin-top:.6rem">Through a centralized digital platform, users can document concerns with photographs, submit reports instantly, and track progress from submission to resolution.</p></div>
<h2>Benefits</h2><div class="grid">${b.map(x=>`<div class="card"><h3>${x[0]}</h3><p>${x[1]}</p></div>`).join("")}</div>
<h2>CivicSnap in numbers <small style="font-weight:400;color:var(--mut)">(sample data)</small></h2><div class="grid">${s.map(x=>`<div class="card"><div class="num">${x[0]}</div><p>${x[1]}</p></div>`).join("")}</div>`}
function report(){if(me.role==="Administrator"||me.role==="Maintenance")return `<div class="card"><h3>Reporting is for students and teachers</h3><p>Switch the sign-in role at the top to submit a report.</p></div>`;
return `<h2 style="margin-top:.5rem">Report a concern</h2><form id="f" class="card" onsubmit="return false"><label for="t">Concern title</label><input id="t" required maxlength="80" placeholder="e.g. Broken chair in Room 204">
<div class="row"><div><label for="c">Category</label><select id="c">${CATS.map(c=>`<option>${c}</option>`).join("")}</select></div><div><label for="p">Priority level</label><select id="p">${PRI.map(c=>`<option ${c==="Medium"?"selected":""}>${c}</option>`).join("")}</select></div></div>
<label for="l">Location</label><input id="l" required placeholder="Room, building, or area">
<label for="ds">Detailed description</label><textarea id="ds" rows="4" required placeholder="What is wrong, and since when?"></textarea>
<label for="im">Photo evidence (you can add several)</label><input id="im" type="file" accept="image/*" multiple><div class="thumbs" id="pv" style="margin-top:.5rem"></div>
<p class="pr" style="margin-top:.8rem">Date and time are recorded automatically when you submit.</p><button class="btn" style="margin-top:.5rem">Submit report</button></form>`}
function bindForm(){imgs=[];$("#im").onchange=e=>{imgs=[];$("#pv").innerHTML="";[...e.target.files].forEach(f=>{const u=URL.createObjectURL(f);imgs.push(u);$("#pv").innerHTML+=`<img src="${u}" alt="Preview of ${esc(f.name)}">`})};
$("#f").onsubmit=e=>{e.preventDefault();if(!$("#f").reportValidity())return;R.unshift({id:++nid,title:$("#t").value,cat:$("#c").value,desc:$("#ds").value,loc:$("#l").value,pri:$("#p").value,st:"Pending",by:me.role,to:"",at:new Date().toISOString(),img:imgs});notify(`Report submitted: ${$("#t").value}`);toast("Report submitted");view="reports";render()}}
function reports(){const loc=[...new Set(R.map(r=>r.loc))];
const o=(a,l)=>`<select id="${l}" aria-label="${l}"><option value="">All ${l}</option>${a.map(x=>`<option>${x}</option>`).join("")}</select>`;
return `<h2 style="margin-top:.5rem">${me.role==="Administrator"?"All reports":me.role==="Maintenance"?"Assigned to me":"My reports"}</h2><div class="filters"><input id="q" type="search" placeholder="Search reports" aria-label="Search reports">${o(ST,"status")}${o(CATS,"category")}${o(PRI,"priority")}${o(loc,"location")}<input id="dt" type="date" aria-label="Date"></div><div id="list"></div>`}
function bindFilters(){["q","status","category","priority","location","dt"].forEach(i=>$("#"+i).oninput=drawList);drawList()}
function drawList(){const q=$("#q").value.toLowerCase(),f=i=>$("#"+i).value;
const L=mine().filter(r=>(!q||(r.title+r.desc+r.loc).toLowerCase().includes(q))&&(!f("status")||r.st===f("status"))&&(!f("category")||r.cat===f("category"))&&(!f("priority")||r.pri===f("priority"))&&(!f("location")||r.loc===f("location"))&&(!f("dt")||r.at.slice(0,10)<=f("dt")&&new Date(r.at).toLocaleDateString("en-CA")===f("dt")));
$("#list").innerHTML=L.length?L.map(card).join(""):`<div class="card"><p>No reports match. Clear a filter or submit a new report.</p></div>`}
function card(r){const A=me.role==="Administrator",M=me.role==="Maintenance";
return `<div class="card rep"><div class="top"><strong>${esc(r.title)}</strong>${badge(r.st)}</div><p>${esc(r.desc)}</p><div class="pr ${r.pri}">${r.cat} · ${esc(r.loc)} · ${r.pri} priority</div><div class="pr">${fmt(r.at)} · by ${r.by}${r.to?" · assigned to "+r.to:""}</div>${r.img.length?`<div class="thumbs">${r.img.map(u=>`<img src="${u}" alt="Evidence">`).join("")}</div>`:""}
<div class="act">${A?`<select onchange="setSt(${r.id},this.value)" aria-label="Status">${ST.map(s=>`<option ${s===r.st?"selected":""}>${s}</option>`).join("")}</select><select onchange="assign(${r.id},this.value)" aria-label="Assign"><option value="">Assign to…</option>${STAFF.map(s=>`<option ${s===r.to?"selected":""}>${s}</option>`).join("")}</select>`:""}
${M&&r.st!=="Resolved"?`<button class="btn sm" onclick="setSt(${r.id},'In Progress')">Start repair</button><button class="btn sm g" onclick="setSt(${r.id},'Resolved')">Mark resolved</button>`:""}</div></div>`}
function setSt(id,s){const r=R.find(x=>x.id===id);r.st=s;notify(`Status updated: “${r.title}” is now ${s}`);if(s==="Resolved")notify(`Concern resolved: ${r.title}`);toast("Status updated");render()}
function assign(id,p){if(!p)return;const r=R.find(x=>x.id===id);r.to=p;if(r.st==="Pending")r.st="In Progress";notify(`Report assigned: “${r.title}” to ${p}`);toast("Report assigned");render()}
function dashboard(){const c=s=>R.filter(r=>r.st===s).length;
const cards=[["Total reports",R.length],["Pending",c("Pending")],["In progress",c("In Progress")],["Resolved",c("Resolved")]];
const mo=["Aug","Sep","Oct","Nov"],mi=[7,8,9,10],mc=mi.map(m=>R.filter(r=>new Date(r.at).getMonth()===m).length),mx=Math.max(...mc,1);
const cc=CATS.map(k=>R.filter(r=>r.cat===k).length),tot=R.length;let a=0;const seg=cc.map((n,i)=>{const s=a;a+=n/tot*100;return `${COL[i]} ${s}% ${a}%`}).join(",");
return `<h2 style="margin-top:.5rem">Dashboard</h2><div class="grid">${cards.map(x=>`<div class="card"><div class="num">${x[1]}</div><p>${x[0]}</p></div>`).join("")}</div>
<h2>Monthly trends</h2><div class="card"><div class="bars">${mc.map(n=>`<div style="height:${n/mx*100}%"><span>${n}</span></div>`).join("")}</div><div class="bl">${mo.map(m=>`<small>${m}</small>`).join("")}</div></div>
<h2>Most common concern categories</h2><div class="card pw"><div class="pie" role="img" aria-label="Pie chart of reports by category" style="background:conic-gradient(${seg})"></div><ul class="lg">${CATS.map((k,i)=>`<li><i style="background:${COL[i]}"></i>${k}: ${cc[i]}</li>`).join("")}</ul></div>
<h2>Export</h2><button class="btn alt" onclick="window.print()">Print or save reports as PDF</button>`}
function users(){const u=[["Student","Student"],["Teacher","Teacher"],["Administrator","Administrator"],...STAFF.map(s=>[s,"Maintenance"])];
return `<h2 style="margin-top:.5rem">Users</h2><div class="grid">${u.map(x=>`<div class="card"><h3>${x[0]}</h3><p>${x[1]}</p></div>`).join("")}</div>`}
drawBell();render();
</script>
</body>
</html>
