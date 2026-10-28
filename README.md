<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Canteen Business Tracker</title>
<style>
:root{--green:#176b52;--green2:#218565;--ink:#172b25;--muted:#6b7c76;--line:#e1e9e5;--bg:#f4f7f5;--white:#fff;--amber:#f5b942}
*{box-sizing:border-box}body{margin:0;font-family:Inter,Arial,sans-serif;background:var(--bg);color:var(--ink)}
button,input,select{font:inherit}button{cursor:pointer;border:0;border-radius:10px;padding:10px 14px;font-weight:650}
.app{display:grid;grid-template-columns:240px 1fr;min-height:100vh}.sidebar{background:#102e25;color:#eaf4ef;padding:24px 16px;display:flex;flex-direction:column;gap:24px}.brand{display:flex;gap:11px;align-items:center;font-size:17px;font-weight:800;letter-spacing:.2px}.logo{background:#d8f2e6;color:#14583f;border-radius:11px;padding:10px;font-weight:900}.nav{display:grid;gap:7px}.nav button{background:transparent;color:#c4d8ce;text-align:left;padding:13px 14px}.nav button.active,.nav button:hover{background:#245242;color:white}.side-note{margin-top:auto;color:#9eb9ac;font-size:12px;line-height:1.5}
main{min-width:0;padding:28px clamp(16px,3vw,40px)}.top{display:flex;justify-content:space-between;align-items:center;gap:16px;margin-bottom:25px}.eyebrow{font-size:12px;text-transform:uppercase;letter-spacing:1.5px;color:var(--green2);font-weight:800}.top h1{margin:6px 0 0;font-size:clamp(24px,3vw,34px)}.top p{margin:7px 0 0;color:var(--muted)}.primary{background:var(--green);color:white}.secondary{background:#e5f1eb;color:var(--green)}.danger{background:#ffeded;color:#a72b2b}.stats{display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:14px;margin-bottom:20px}.stat{background:white;border:1px solid var(--line);border-radius:16px;padding:18px}.stat-label{font-size:13px;color:var(--muted)}.stat-value{font-size:29px;font-weight:800;margin-top:8px}.stat-sub{font-size:12px;color:var(--muted);margin-top:5px}.panel{background:white;border:1px solid var(--line);border-radius:16px;overflow:hidden}.panel-head{padding:18px 20px;display:flex;justify-content:space-between;align-items:center;gap:14px;border-bottom:1px solid var(--line);flex-wrap:wrap}.panel-head h2{font-size:17px;margin:0}.tools{display:flex;gap:9px;flex-wrap:wrap}.tools input,.tools select,.field input,.field select{border:1px solid #d7e2dc;border-radius:9px;padding:10px 11px;background:white;min-width:0}.tools input{width:min(260px,60vw)}.table-wrap{overflow:auto}table{border-collapse:collapse;width:100%;min-width:1050px}th{background:#eaf3ee;color:#315e4d;text-align:left;font-size:12px;letter-spacing:.45px;text-transform:uppercase;padding:13px 14px;white-space:nowrap}td{padding:12px 14px;border-bottom:1px solid #edf1ee;font-size:13px;white-space:nowrap}tbody tr:nth-child(even){background:#fafcfb}tbody tr:hover{background:#f0f8f3}td input[type=checkbox]{width:17px;height:17px;accent-color:var(--green);vertical-align:middle}td input[type=text],td input[type=tel]{width:100%;min-width:130px;border:1px solid transparent;background:transparent;border-radius:6px;padding:7px;color:inherit}td input:focus{outline:2px solid #8fcbb0;background:white;border-color:#8fcbb0}.ratio{border:0;background:#e8eeeb;border-radius:20px;padding:7px 10px;color:#315e4d;min-width:105px}.tag{display:inline-flex;padding:5px 8px;border-radius:30px;background:#e5f5ec;color:#176b52;font-size:11px;font-weight:750}.empty{padding:35px;text-align:center;color:var(--muted)}.bottom{display:flex;justify-content:space-between;align-items:center;gap:10px;padding:15px 20px;color:var(--muted);font-size:12px}.section{display:none}.section.active{display:block}.form-grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:15px;padding:20px}.field{display:grid;gap:7px;font-size:13px;font-weight:700}.field input,.field select{width:100%}.form-actions{padding:0 20px 20px;display:flex;gap:10px;justify-content:flex-end}.hint{font-size:12px;color:var(--muted);padding:0 20px 18px;line-height:1.5}.toast{position:fixed;right:20px;bottom:20px;background:#123e2e;color:white;padding:13px 18px;border-radius:12px;box-shadow:0 8px 30px #0002;display:none}.small{font-size:12px;color:var(--muted)}
@media(max-width:850px){.app{grid-template-columns:1fr}.sidebar{padding:14px;gap:12px}.brand{padding:2px 5px}.nav{display:flex;overflow:auto}.nav button{white-space:nowrap}.side-note{display:none}main{padding:20px 13px}.stats{grid-template-columns:repeat(2,minmax(0,1fr))}.top{align-items:flex-start}.top .primary{white-space:nowrap}.form-grid{grid-template-columns:1fr}}
</style>
</head>
<body>
<div class="app">
<aside class="sidebar">
  <div class="brand"><span class="logo">CB</span><span>CANTEEN BUSINESS</span></div>
  <nav class="nav">
    <button class="active" data-page="dashboard">▦ &nbsp; Dashboard</button>
    <button data-page="hospitals">▤ &nbsp; Hospital Leads</button>
    <button data-page="gyms">♧ &nbsp; Gym Leads</button>
    <button data-page="add">＋ &nbsp; Add New Lead</button>
  </nav>
  <div class="side-note">CANTEEN BUSINESS TRACKER<br>Data is saved in this browser on this device.<br><br>Export a CSV backup regularly.</div>
</aside>
<main>
  <section class="section active" id="dashboard">
    <div class="top"><div><div class="eyebrow">Overview</div><h1>Business Dashboard</h1><p>Track hospital and gym outreach in one place.</p></div><button class="primary" onclick="showPage('add')">＋ Add lead</button></div>
    <div class="stats">
      <div class="stat"><div class="stat-label">Total leads</div><div class="stat-value" id="totalStat">0</div><div class="stat-sub">Hospitals + gyms</div></div>
      <div class="stat"><div class="stat-label">Interested</div><div class="stat-value" id="interestedStat">0</div><div class="stat-sub">Marked as interested</div></div>
      <div class="stat"><div class="stat-label">Finalized</div><div class="stat-value" id="finalStat">0</div><div class="stat-sub">Marked as final</div></div>
      <div class="stat"><div class="stat-label">Pending follow-up</div><div class="stat-value" id="pendingStat">0</div><div class="stat-sub">Not finalized yet</div></div>
    </div>
    <div class="panel">
      <div class="panel-head"><h2>Recent leads</h2><div class="tools"><button class="secondary" onclick="exportCSV('all')">Export all CSV</button></div></div>
      <div class="table-wrap"><table><thead><tr><th>Type</th><th>Name</th><th>Phone</th><th>Interested</th><th>Final</th><th>Ratio</th></tr></thead><tbody id="recentRows"></tbody></table></div>
    </div>
    <p class="small">Starter data is based on the names visible in your screenshots. Add or edit records to match your full spreadsheet.</p>
  </section>

  <section class="section" id="hospitals">
    <div class="top"><div><div class="eyebrow">Lead management</div><h1>Hospital Leads</h1><p>Manage hospital contacts and deal status.</p></div><button class="primary" onclick="openAdd('Hospital')">＋ Add hospital</button></div>
    <div class="stats">
      <div class="stat"><div class="stat-label">Hospitals</div><div class="stat-value" id="hospitalCount">0</div></div>
      <div class="stat"><div class="stat-label">Interested</div><div class="stat-value" id="hospitalInterested">0</div></div>
      <div class="stat"><div class="stat-label">Finalized</div><div class="stat-value" id="hospitalFinal">0</div></div>
      <div class="stat"><div class="stat-label">Not finalized</div><div class="stat-value" id="hospitalPending">0</div></div>
    </div>
    <div class="panel"><div class="panel-head"><h2>Hospital contact register</h2><div class="tools"><input id="hospitalSearch" placeholder="Search name or phone…" oninput="renderTable('Hospital')"><select id="hospitalFilter" onchange="renderTable('Hospital')"><option value="all">All statuses</option><option value="interested">Interested</option><option value="final">Final</option><option value="pending">Pending</option></select><button class="secondary" onclick="exportCSV('Hospital')">Export CSV</button></div></div><div class="table-wrap"><table><thead><tr><th>S.No</th><th>Hospital name</th><th>Phone number</th><th>Interested</th><th>Final</th><th>Ratio</th><th>Actions</th></tr></thead><tbody id="hospitalRows"></tbody></table></div><div class="bottom"><span id="hospitalFoot"></span><span>Changes save automatically</span></div></div>
  </section>

  <section class="section" id="gyms">
    <div class="top"><div><div class="eyebrow">Lead management</div><h1>Gym Leads</h1><p>Manage gym contacts and deal status.</p></div><button class="primary" onclick="openAdd('Gym')">＋ Add gym</button></div>
    <div class="stats">
      <div class="stat"><div class="stat-label">Gyms</div><div class="stat-value" id="gymCount">0</div></div>
      <div class="stat"><div class="stat-label">Interested</div><div class="stat-value" id="gymInterested">0</div></div>
      <div class="stat"><div class="stat-label">Finalized</div><div class="stat-value" id="gymFinal">0</div></div>
      <div class="stat"><div class="stat-label">Not finalized</div><div class="stat-value" id="gymPending">0</div></div>
    </div>
    <div class="panel"><div class="panel-head"><h2>Gym contact register</h2><div class="tools"><input id="gymSearch" placeholder="Search name or phone…" oninput="renderTable('Gym')"><select id="gymFilter" onchange="renderTable('Gym')"><option value="all">All statuses</option><option value="interested">Interested</option><option value="final">Final</option><option value="pending">Pending</option></select><button class="secondary" onclick="exportCSV('Gym')">Export CSV</button></div></div><div class="table-wrap"><table><thead><tr><th>S.No</th><th>Gym name</th><th>Phone number</th><th>Interested</th><th>Final</th><th>Ratio</th><th>Actions</th></tr></thead><tbody id="gymRows"></tbody></table></div><div class="bottom"><span id="gymFoot"></span><span>Changes save automatically</span></div></div>
  </section>

  <section class="section" id="add">
    <div class="top"><div><div class="eyebrow">Contact register</div><h1>Add a lead</h1><p>Enter a hospital or gym contact.</p></div></div>
    <div class="panel"><div class="panel-head"><h2>Lead details</h2></div>
      <form id="leadForm">
      <div class="form-grid">
        <label class="field">Lead type<select id="leadType"><option>Hospital</option><option>Gym</option></select></label>
        <label class="field">Name *<input id="leadName" required placeholder="Enter hospital or gym name"></label>
        <label class="field">Phone number<input id="leadPhone" type="tel" inputmode="numeric" placeholder="Contact number"></label>
        <label class="field">Ratio / deal stage<select id="leadRatio"><option value="">Not set</option><option>1:1</option><option>2:1</option><option>3:1</option><option>Negotiation</option><option>Follow-up</option><option>Not interested</option><option>Other</option></select></label>
        <label class="field">Interested<select id="leadInterested"><option value="false">No</option><option value="true">Yes</option></select></label>
        <label class="field">Finalized<select id="leadFinal"><option value="false">No</option><option value="true">Yes</option></select></label>
      </div>
      <div class="form-actions"><button type="reset" class="secondary">Clear</button><button class="primary" type="submit">Save lead</button></div>
      </form>
      <div class="hint">This starter app stores entries in your browser using local storage. It does not yet sync changes back to Google Sheets or other devices.</div>
    </div>
  </section>
</main>
</div>
<div class="toast" id="toast"></div>
<script>
const starter=[
 {type:'Hospital',name:'SHREE VYAS MULTI SPECIAL',phone:'',interested:false,final:false,ratio:''},
 {type:'Hospital',name:'VED NARAYAN HEALTH CARE',phone:'6207509494',interested:false,final:false,ratio:''},
 {type:'Hospital',name:'NIRMALA MULTI SPECIALITY',phone:'',interested:false,final:false,ratio:''},
 {type:'Hospital',name:'KK LIFE CARE',phone:'',interested:false,final:false,ratio:''},
 {type:'Hospital',name:'MATA KAMLA',phone:'6562451506',interested:false,final:false,ratio:''},
 {type:'Hospital',name:'LIFE LINE',phone:'9709769992',interested:false,final:false,ratio:''},
 {type:'Hospital',name:'SHRI NARAYAN',phone:'8809653288',interested:false,final:false,ratio:''},
 {type:'Hospital',name:'SRI MANGALAM',phone:'9123100631',interested:false,final:false,ratio:''},
 {type:'Gym',name:'BEING STRONG GYM',phone:'7004539342',interested:false,final:false,ratio:''},
 {type:'Gym',name:'RPLATINUM GYM',phone:'7903431693',interested:false,final:false,ratio:''},
 {type:'Gym',name:'THE SWEAT ARENA',phone:'9304506435',interested:false,final:false,ratio:''},
 {type:'Gym',name:'BD FITNESS',phone:'9661843337',interested:false,final:false,ratio:''},
 {type:'Gym',name:'LIFELINE FITNESS GYM',phone:'7488933930',interested:false,final:false,ratio:''},
 {type:'Gym',name:'M3 OXYGEN GYM',phone:'8434853535',interested:false,final:false,ratio:''},
 {type:'Gym',name:'BODY FITNESS CLUB',phone:'9204835550',interested:false,final:false,ratio:''},
 {type:'Gym',name:'MUSCLE FACTORY',phone:'6204610542',interested:false,final:false,ratio:''}
];
let leads=[];try{leads=JSON.parse(localStorage.getItem('canteenLeadsV1'))||starter.map((x,i)=>({...x,id:i+1}));}catch(e){leads=starter.map((x,i)=>({...x,id:i+1}));}
let nextId=Math.max(0,...leads.map(x=>x.id||0))+1;
function save(){localStorage.setItem('canteenLeadsV1',JSON.stringify(leads));renderAll();showToast('Saved on this device');}
function showToast(s){const t=document.getElementById('toast');t.textContent=s;t.style.display='block';clearTimeout(window.toastTimer);window.toastTimer=setTimeout(()=>t.style.display='none',2200)}
function showPage(page){document.querySelectorAll('.section').forEach(s=>s.classList.toggle('active',s.id===page));document.querySelectorAll('.nav button').forEach(b=>b.classList.toggle('active',b.dataset.page===page));if(page==='add'&&!document.getElementById('leadName').value)document.getElementById('leadType').value='Hospital';}
document.querySelectorAll('.nav button').forEach(b=>b.addEventListener('click',()=>showPage(b.dataset.page)));
function openAdd(type){document.getElementById('leadForm').reset();document.getElementById('leadType').value=type;showPage('add');document.getElementById('leadName').focus()}
function ratioOptions(value){return ['','1:1','2:1','3:1','Negotiation','Follow-up','Not interested','Other'].map(v=>`<option ${v===value?'selected':''} value="${v}">${v||'Not set'}</option>`).join('')}
function renderTable(type){
 const key=type.toLowerCase(),body=document.getElementById(key+'Rows'),search=(document.getElementById(key+'Search').value||'').toLowerCase(),filter=document.getElementById(key+'Filter').value;
 let list=leads.filter(l=>l.type===type&&(`${l.name} ${l.phone}`.toLowerCase().includes(search)));
 if(filter==='interested')list=list.filter(l=>l.interested);if(filter==='final')list=list.filter(l=>l.final);if(filter==='pending')list=list.filter(l=>!l.final);
 body.innerHTML=list.map((l,i)=>`<tr><td>${i+1}</td><td><input aria-label="Name" type="text" value="${esc(l.name)}" onchange="update(${l.id},'name',this.value)"></td><td><input aria-label="Phone" type="tel" value="${esc(l.phone||'')}" onchange="update(${l.id},'phone',this.value)"></td><td><input aria-label="Interested" type="checkbox" ${l.interested?'checked':''} onchange="update(${l.id},'interested',this.checked)"></td><td><input aria-label="Final" type="checkbox" ${l.final?'checked':''} onchange="update(${l.id},'final',this.checked)"></td><td><select class="ratio" aria-label="Ratio" onchange="update(${l.id},'ratio',this.value)">${ratioOptions(l.ratio||'')}</select></td><td><button class="danger" onclick="removeLead(${l.id})">Delete</button></td></tr>`).join('')||'<tr><td colspan="7" class="empty">No matching leads. Add a new lead to get started.</td></tr>';
 document.getElementById(key+'Foot').textContent=`Showing ${list.length} of ${leads.filter(l=>l.type===type).length} leads`;
}
function esc(v){return String(v??'').replace(/[&<>"']/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]))}
function update(id,field,value){const l=leads.find(x=>x.id===id);if(l){l[field]=value;localStorage.setItem('canteenLeadsV1',JSON.stringify(leads));renderAll();showToast('Change saved')}}
function removeLead(id){const l=leads.find(x=>x.id===id);if(!l)return;if(confirm(`Delete "${l.name}"? This cannot be undone.`)){leads=leads.filter(x=>x.id!==id);save();showToast('Lead deleted')}}
function renderStats(type,prefix){const list=type==='all'?leads:leads.filter(l=>l.type===type);const set=(id,n)=>document.getElementById(id).textContent=n; if(type==='all'){set('totalStat',list.length);set('interestedStat',list.filter(l=>l.interested).length);set('finalStat',list.filter(l=>l.final).length);set('pendingStat',list.filter(l=>!l.final).length)}else{set(prefix+'Count',list.length);set(prefix+'Interested',list.filter(l=>l.interested).length);set(prefix+'Final',list.filter(l=>l.final).length);set(prefix+'Pending',list.filter(l=>!l.final).length)}}
function renderRecent(){const list=[...leads].slice(-8).reverse();document.getElementById('recentRows').innerHTML=list.map(l=>`<tr><td><span class="tag">${l.type}</span></td><td>${esc(l.name)}</td><td>${esc(l.phone||'—')}</td><td>${l.interested?'Yes':'No'}</td><td>${l.final?'Yes':'No'}</td><td>${esc(l.ratio||'—')}</td></tr>`).join('')||'<tr><td colspan="6" class="empty">No leads yet.</td></tr>'}
function renderAll(){renderStats('all');renderStats('Hospital','hospital');renderStats('Gym','gym');renderTable('Hospital');renderTable('Gym');renderRecent()}
function exportCSV(type){const list=type==='all'?leads:leads.filter(l=>l.type===type);const rows=[['S.No','Type','Name','Phone Number','Interested','Final','Ratio'],...list.map((l,i)=>[i+1,l.type,l.name,l.phone||'',l.interested?'Yes':'No',l.final?'Yes':'No',l.ratio||''])];const csv=rows.map(r=>r.map(v=>'"'+String(v).replace(/"/g,'""')+'"').join(',')).join('\r\n');const blob=new Blob(['\ufeff'+csv],{type:'text/csv;charset=utf-8;'});const a=document.createElement('a');a.href=URL.createObjectURL(blob);a.download=`canteen-${type.toLowerCase()}-leads.csv`;a.click();URL.revokeObjectURL(a.href)}
document.getElementById('leadForm').addEventListener('submit',e=>{e.preventDefault();const name=document.getElementById('leadName').value.trim();if(!name)return;leads.push({id:nextId++,type:document.getElementById('leadType').value,name,phone:document.getElementById('leadPhone').value.trim(),ratio:document.getElementById('leadRatio').value,interested:document.getElementById('leadInterested').value==='true',final:document.getElementById('leadFinal').value==='true'});localStorage.setItem('canteenLeadsV1',JSON.stringify(leads));e.target.reset();renderAll();showPage('dashboard');showToast('Lead added successfully')});
renderAll();
</script>
</body>
</html>
