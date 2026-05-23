[index.html](https://github.com/user-attachments/files/28168594/index.html)
<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>閉店チェック｜銀座店</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@300;400;500;700&family=DM+Mono:wght@400;500&display=swap');
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:'Noto Sans JP',sans-serif;background:#f5f4f0;min-height:100vh}
#app{max-width:480px;margin:0 auto}
header{background:#1a1a18;padding:0 16px;position:sticky;top:0;z-index:10}
.h-inner{display:flex;justify-content:space-between;align-items:center;height:60px}
.h-title{font-family:'DM Mono',monospace;color:#fff;font-size:15px;font-weight:500;letter-spacing:.12em}
.h-sub{color:#6b7280;font-size:10px;letter-spacing:.08em;margin-top:2px}
.h-btn{background:transparent;border:1px solid #3f3f3c;color:#9ca3af;font-size:12px;padding:6px 12px;border-radius:20px;cursor:pointer;font-family:inherit}
main{padding:16px 16px 48px}
.card{background:#fff;border-radius:16px;padding:24px;box-shadow:0 1px 4px rgba(0,0,0,.06);margin-bottom:12px}
.lbl{font-size:13px;color:#6b7280;margin-bottom:16px;letter-spacing:.04em}
.name-input{width:100%;font-size:20px;font-weight:500;border:none;border-bottom:2px solid #1a1a18;padding:8px 0;background:transparent;font-family:'Noto Sans JP',sans-serif;color:#1a1a18;margin-bottom:32px;display:block}
.name-input:focus{outline:none}
.btn{width:100%;background:#1a1a18;color:#fff;border:none;border-radius:12px;padding:16px;font-size:15px;font-weight:500;cursor:pointer;font-family:inherit;letter-spacing:.04em}
.btn:disabled{opacity:.35}
.btn:active{transform:scale(.97)}
.prog-card{background:#fff;border-radius:16px;padding:16px 20px;margin-bottom:16px;box-shadow:0 1px 4px rgba(0,0,0,.06)}
.prog-top{display:flex;justify-content:space-between;align-items:center;margin-bottom:10px}
.prog-name{font-size:14px;font-weight:500;color:#1a1a18}
.prog-num{font-family:'DM Mono',monospace;font-size:22px;font-weight:500;color:#0d9488}
.prog-tot{font-family:'DM Mono',monospace;font-size:13px;color:#9ca3af}
.bar{height:6px;background:#f0f0ee;border-radius:4px;overflow:hidden}
.bar-fill{height:100%;border-radius:4px;background:#0d9488;transition:width .3s ease,background .5s ease}
.cat-hd{font-size:11px;font-weight:700;letter-spacing:.1em;display:flex;align-items:center;gap:6px;margin-bottom:8px;padding-left:4px}
.cat-dot{width:6px;height:6px;border-radius:50%;flex-shrink:0}
.check-item{width:100%;display:flex;align-items:center;gap:12px;padding:13px 16px;border:1.5px solid #e5e5e0;border-radius:12px;margin-bottom:8px;cursor:pointer;text-align:left;background:#fff;font-family:inherit;transition:background .15s,border-color .15s}
.check-item:active{transform:scale(.98)}
.check-item.done{background:#f0fdf9;border-color:#0d9488}
.check-item.highlight{background:#fffef5;border-color:#fcd34d}
.check-item.highlight.done{background:#fffbeb;border-color:#f59e0b}
.checkbox{width:22px;height:22px;border-radius:6px;border:1.5px solid #ccc;flex-shrink:0;display:flex;align-items:center;justify-content:center;transition:all .15s}
.checkbox.checked{background:#0d9488;border-color:#0d9488}
.checkbox.checked-hl{background:#f59e0b;border-color:#f59e0b}
.item-label{font-size:14px;line-height:1.45;color:#1a1a1a;flex:1}
.item-label.done{color:#9ca3af;text-decoration:line-through}
.on-badge{font-size:10px;font-weight:700;background:#f59e0b;color:#fff;border-radius:6px;padding:3px 8px;flex-shrink:0}
.on-badge.done{background:#d97706}
.hl-row{display:flex;align-items:center;gap:8px;flex:1}
.fin-btn{width:100%;color:#fff;border:none;border-radius:14px;padding:18px;font-size:16px;font-weight:700;cursor:pointer;font-family:inherit;letter-spacing:.05em;margin-top:8px;background:#9ca3af;opacity:.3;pointer-events:none}
.fin-btn.active{background:#059669;opacity:1;pointer-events:auto}
.fin-btn:active{transform:scale(.97)}
.cancel-btn{width:100%;background:transparent;border:none;color:#9ca3af;font-size:13px;padding:12px;cursor:pointer;font-family:inherit;margin-top:4px}
textarea{width:100%;border:1.5px solid #e5e5e0;border-radius:12px;padding:12px 14px;font-size:14px;font-family:'Noto Sans JP',sans-serif;color:#1a1a18;background:#fafaf8;line-height:1.7;margin-bottom:16px;resize:none}
textarea:focus{outline:none}
.stamp-wrap{display:flex;justify-content:center;margin-bottom:24px}
.stamp{width:120px;height:120px;border-radius:50%;border:4px solid #059669;display:flex;align-items:center;justify-content:center;animation:stmp .55s cubic-bezier(.175,.885,.32,1.275) both}
@keyframes stmp{0%{transform:scale(2.2) rotate(-15deg);opacity:0}65%{transform:scale(.88) rotate(3deg);opacity:1}100%{transform:scale(1) rotate(-2deg);opacity:1}}
.stamp-txt{font-size:28px;font-weight:700;color:#059669;letter-spacing:.1em}
.done-title{font-size:18px;font-weight:700;color:#1a1a18;margin-bottom:24px;letter-spacing:.04em;text-align:center}
.row{display:flex;justify-content:space-between;align-items:flex-start;padding:4px 0}
.rk{font-size:12px;color:#9ca3af;letter-spacing:.06em;flex-shrink:0}
.rv{font-size:15px;font-weight:600;color:#1a1a18;text-align:right}
.divider{height:1px;background:#f0f0ee;margin:12px 0}
.memo-preview{font-size:14px;color:#374151;line-height:1.7;margin-top:6px;white-space:pre-wrap;word-break:break-all;background:#fffbeb;border-radius:8px;padding:10px 12px}
.reset-btn{display:block;margin:0 auto;background:transparent;border:1.5px solid #1a1a18;color:#1a1a18;border-radius:12px;padding:14px 32px;font-size:14px;cursor:pointer;font-family:inherit;letter-spacing:.06em}
.banner{background:#fffbeb;border:1.5px solid #fcd34d;border-radius:14px;padding:14px 16px;margin-bottom:12px}
.banner-top{display:flex;align-items:center;gap:6px;margin-bottom:8px;flex-wrap:wrap}
.banner-label{font-size:12px;font-weight:700;color:#92400e;letter-spacing:.06em}
.banner-meta{font-size:11px;color:#b45309;margin-left:auto}
.banner-text{font-size:14px;color:#1a1a18;line-height:1.65;white-space:pre-wrap;word-break:break-all}
.overlay{position:fixed;inset:0;background:rgba(0,0,0,.55);z-index:100;display:flex;align-items:center;justify-content:center;padding:24px}
.pin-card{background:#fff;border-radius:20px;padding:32px 28px;width:100%;max-width:320px;text-align:center}
.pin-title{font-size:18px;font-weight:700;color:#1a1a18;margin-bottom:6px}
.pin-sub{font-size:12px;color:#9ca3af;margin-bottom:24px}
.pin-input{width:100%;font-size:28px;font-weight:700;text-align:center;border:none;border-bottom:2px solid #1a1a18;padding:8px 0;background:transparent;font-family:'DM Mono',monospace;letter-spacing:.3em;margin-bottom:8px}
.pin-input:focus{outline:none}
.pin-error{font-size:12px;color:#ef4444;margin-bottom:12px;display:none}
.admin-hd{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:12px}
.admin-title{font-size:15px;font-weight:700;color:#1a1a18}
.admin-sub{font-size:11px;color:#9ca3af;margin-top:2px}
.ot-badge{background:#fef2f2;color:#dc2626;font-size:12px;font-weight:700;padding:6px 12px;border-radius:20px;border:1.5px solid #fca5a5}
.legend{display:flex;gap:16px;margin-bottom:12px;padding-left:2px}
.legend-item{display:flex;align-items:center;gap:6px;font-size:11px;color:#6b7280}
.legend-dot{width:10px;height:10px;border-radius:3px;display:inline-block}
.log-row{border-radius:12px;padding:14px 16px;margin-bottom:8px;box-shadow:0 1px 3px rgba(0,0,0,.05);border-left:4px solid #0d9488;background:#fff}
.log-row.over{border-left-color:#ef4444;background:#fef2f2}
.log-top{display:flex;align-items:center;gap:8px;flex-wrap:wrap}
.log-date{font-family:'DM Mono',monospace;font-size:13px;color:#1a1a18;font-weight:500}
.log-day{font-size:11px;color:#9ca3af}
.log-name{font-size:13px;font-weight:600;color:#1a1a18;margin-left:auto}
.log-badge{background:#f0fdf9;color:#059669;font-size:10px;font-weight:700;padding:2px 8px;border-radius:20px}
.log-badge.over{background:#fef2f2;color:#dc2626}
.ot-note{font-size:11px;color:#dc2626;margin-top:6px;font-family:'DM Mono',monospace}
.log-memo{display:flex;gap:6px;align-items:flex-start;margin-top:10px;background:#fffbeb;border-radius:8px;padding:8px 10px}
.log-memo-text{font-size:13px;color:#374151;line-height:1.65;white-space:pre-wrap;word-break:break-all}
.empty{text-align:center;padding:48px 0;color:#9ca3af;font-size:14px}
.fade-in{animation:fi .35s ease both}
@keyframes fi{from{opacity:0;transform:translateY(8px)}to{opacity:1;transform:translateY(0)}}
.memo-hd{display:flex;align-items:flex-start;gap:12px;margin-bottom:16px}
.memo-icon{font-size:24px;line-height:1}
.memo-title{font-size:16px;font-weight:700;color:#1a1a18}
.memo-subtitle{font-size:12px;color:#9ca3af;margin-top:2px}
.sync-bar{background:#d1fae5;color:#065f46;font-size:11px;text-align:center;padding:4px;display:none}
.sync-bar.error{background:#fee2e2;color:#991b1b}
</style>
</head>
<body>
<div id="app">
  <header>
    <div class="h-inner">
      <div>
        <div class="h-title">CLOSING CHECK</div>
        <div class="h-sub">銀座店　閉店作業チェックリスト</div>
      </div>
      <button class="h-btn" id="histBtn" onclick="toggleHistory()">履歴</button>
    </div>
  </header>
  <div class="sync-bar" id="syncBar"></div>
  <main id="main"></main>
</div>

<script>
const DB_URL = "https://basiapp-default-rtdb.asia-southeast1.firebasedatabase.app/logs/ginza";
const ADMIN_PIN = "8484";
const DAYS = ["日","月","火","水","木","金","土"];
const ITEMS = [
  {id:1,cat:"清掃",label:"トイレ清掃/キッチン清掃"},
  {id:2,cat:"清掃",label:"玄関前クリーナー"},
  {id:3,cat:"清掃",label:"更衣室清掃"},
  {id:4,cat:"確認",label:"マシン・器具片付け"},
  {id:5,cat:"確認",label:"ゴミの確認"},
  {id:6,cat:"設備",label:"エアコン２カ所OFF（換気扇は常時ON）"},
  {id:7,cat:"設備",label:"ストレージ・更衣室電気OFF"},
  {id:8,cat:"設備",label:"PC / iPad / モニター・マイクOFF、マイク充電"},
  {id:9,cat:"設備",label:"外看板BASIライトON",hl:true},
  {id:10,cat:"設備",label:"入り口扉奥施錠・セキュリティセット"},
];
const CAT_COLORS = {設備:"#0d9488",清掃:"#7c3aed",確認:"#d97706"};

function fmt(iso){
  const d=new Date(iso);
  return d.getFullYear()+"/"+String(d.getMonth()+1).padStart(2,"0")+"/"+String(d.getDate()).padStart(2,"0")+" "+String(d.getHours()).padStart(2,"0")+":"+String(d.getMinutes()).padStart(2,"0");
}
function dayOf(iso){return DAYS[new Date(iso).getDay()];}
function closingMin(iso){const d=new Date(iso);return(d.getDay()===0||d.getDay()===6)?18*60+30:22*60;}
function isOver(iso){const d=new Date(iso);return d.getHours()*60+d.getMinutes()>closingMin(iso);}
function closingLbl(iso){const m=closingMin(iso);return String(Math.floor(m/60)).padStart(2,"0")+":"+String(m%60).padStart(2,"0");}
function esc(s){return String(s||"").replace(/&/g,"&amp;").replace(/</g,"&lt;").replace(/>/g,"&gt;").replace(/"/g,"&quot;");}

function showSync(msg, isError){
  const bar = document.getElementById("syncBar");
  bar.textContent = msg;
  bar.className = "sync-bar" + (isError ? " error" : "");
  bar.style.display = "block";
  if (!isError) setTimeout(()=>bar.style.display="none", 3000);
}

async function loadLogs(){
  try {
    const res = await fetch(DB_URL+".json?orderBy=%22completedAt%22&limitToLast=50");
    if (!res.ok) throw new Error("HTTP "+res.status);
    const data = await res.json();
    return data ? Object.values(data).sort((a,b)=>b.completedAt.localeCompare(a.completedAt)) : [];
  } catch(e) {
    showSync("データ取得エラー: "+e.message, true);
    return [];
  }
}

async function saveLog(entry){
  const res = await fetch(DB_URL+".json", {
    method:"POST",
    headers:{"Content-Type":"application/json"},
    body:JSON.stringify(entry)
  });
  if (!res.ok) throw new Error("HTTP "+res.status);
  return res.json();
}

let state = {screen:"name",name:"",checked:{},memo:"",logs:[],doneAt:null,adminMode:false,busy:false};

async function init(){
  state.logs = await loadLogs();
  render();
}

function render(){
  const m = document.getElementById("main");
  m.innerHTML = "";
  document.getElementById("histBtn").textContent = state.screen==="history" ? "← 戻る" : (state.adminMode?"👤 履歴":"履歴");
  if(state.screen==="name") renderName(m);
  else if(state.screen==="check") renderCheck(m);
  else if(state.screen==="memo") renderMemo(m);
  else if(state.screen==="done") renderDone(m);
  else if(state.screen==="history") renderHistory(m);
}

function renderName(m){
  const latestMemo = state.logs.find(l=>l.memo&&l.memo.trim());
  if(latestMemo){
    const b=document.createElement("div");
    b.className="banner fade-in";
    b.innerHTML='<div class="banner-top"><span>📋</span><span class="banner-label">直近の申し送り</span><span class="banner-meta">'+fmt(latestMemo.completedAt)+"　"+esc(latestMemo.name)+'</span></div><div class="banner-text">'+esc(latestMemo.memo)+"</div>";
    m.appendChild(b);
  }
  const d=document.createElement("div");
  d.className="card fade-in";
  d.innerHTML='<p class="lbl">担当者名を入力してください</p><input class="name-input" id="nameInput" placeholder="例：馬司 銀次郎" value="'+esc(state.name)+'"><button class="btn" id="startBtn" onclick="startCheck()"'+(state.name.trim()?'':' disabled')+'>チェックを開始する →</button>';
  m.appendChild(d);
  const inp=document.getElementById("nameInput");
  inp.addEventListener("input",e=>{state.name=e.target.value;document.getElementById("startBtn").disabled=!state.name.trim();});
  inp.addEventListener("keydown",e=>{if(e.key==="Enter")startCheck();});
  inp.focus();
}

function renderCheck(m){
  const count=Object.values(state.checked).filter(Boolean).length;
  const total=ITEMS.length;
  const done=count===total;
  const prog=document.createElement("div");
  prog.className="prog-card fade-in";
  prog.innerHTML='<div class="prog-top"><span class="prog-name">'+esc(state.name)+'</span><span><span class="prog-num" style="color:'+(done?"#059669":"#0d9488")+'">'+count+'</span><span class="prog-tot"> / '+total+'</span></span></div><div class="bar"><div class="bar-fill" style="width:'+(count/total*100)+'%;background:'+(done?"#059669":"#0d9488")+'"></div></div>';
  m.appendChild(prog);
  ["清掃","確認","設備"].forEach(cat=>{
    const block=document.createElement("div");
    block.style.marginBottom="12px";
    block.innerHTML='<div class="cat-hd" style="color:'+CAT_COLORS[cat]+'"><span class="cat-dot" style="background:'+CAT_COLORS[cat]+'"></span>'+cat+'</div>';
    ITEMS.filter(i=>i.cat===cat).forEach(item=>{
      const isChecked=!!state.checked[item.id];
      const btn=document.createElement("button");
      btn.className="check-item"+(isChecked?" done":"")+(item.hl?" highlight":"");
      btn.innerHTML='<span class="checkbox '+(isChecked?(item.hl?"checked-hl":"checked"):"")+'">'+
        (isChecked?'<svg width="12" height="9" viewBox="0 0 12 9" fill="none"><path d="M1 4.5L4.5 8L11 1" stroke="white" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"/></svg>':"")+
        '</span>'+
        (item.hl?'<span class="hl-row"><span class="item-label'+(isChecked?" done":"")+'">'+esc(item.label)+'</span><span class="on-badge'+(isChecked?" done":"")+'">ON にする</span></span>':
        '<span class="item-label'+(isChecked?" done":"")+'">'+esc(item.label)+'</span>');
      btn.onclick=()=>{state.checked[item.id]=!state.checked[item.id];render();};
      block.appendChild(btn);
    });
    m.appendChild(block);
  });
  const finBtn=document.createElement("button");
  finBtn.className="fin-btn"+(done?" active":"");
  finBtn.textContent=done?"次へ：申し送りを入力 →":"残り "+(total-count)+" 項目";
  finBtn.onclick=()=>{if(done){state.memo="";state.screen="memo";render();}};
  m.appendChild(finBtn);
}

function renderMemo(m){
  const d=document.createElement("div");
  d.className="card fade-in";
  d.innerHTML='<div class="memo-hd"><span class="memo-icon">📋</span><div><div class="memo-title">申し送り・メモ</div><div class="memo-subtitle">翌日の担当者へのメッセージ（任意）</div></div></div>'+
    '<textarea id="memoInput" rows="7" placeholder="例：\n・明日10時に業者来訪あり\n・更衣室の電球が切れかけています">'+esc(state.memo)+'</textarea>'+
    '<button class="fin-btn active" id="finishBtn" style="margin-top:0" onclick="finishCheck()">'+(state.memo.trim()?"✓ メモを添えて完了する":"✓ メモなしで完了する")+'</button>'+
    '<button class="cancel-btn" onclick="goBack()">← チェックリストに戻る</button>';
  m.appendChild(d);
  document.getElementById("memoInput").addEventListener("input",e=>{
    state.memo=e.target.value;
    document.getElementById("finishBtn").textContent=state.memo.trim()?"✓ メモを添えて完了する":"✓ メモなしで完了する";
  });
}

function renderDone(m){
  const d=document.createElement("div");
  d.className="fade-in";
  d.style.textAlign="center";
  d.style.paddingTop="20px";
  const iso=state.doneAt.toISOString();
  d.innerHTML='<div class="stamp-wrap"><div class="stamp"><div class="stamp-txt">完了</div></div></div>'+
    '<div class="done-title">閉店作業が完了しました</div>'+
    '<div class="card">'+
    '<div class="row"><span class="rk">担当者</span><span class="rv">'+esc(state.name)+'</span></div>'+
    '<div class="divider"></div>'+
    '<div class="row"><span class="rk">退勤時刻</span><span class="rv">'+fmt(iso)+'　<span style="font-size:12px;color:#9ca3af">（'+dayOf(iso)+'曜日）</span></span></div>'+
    (state.memo.trim()?'<div class="divider"></div><div class="row"><span class="rk">申し送り</span></div><div class="memo-preview">'+esc(state.memo)+'</div>':'')+
    '</div>'+
    '<button class="reset-btn" onclick="resetApp()">最初に戻る</button>';
  m.appendChild(d);
}

function renderHistory(m){
  const overCount=state.logs.filter(l=>isOver(l.completedAt)).length;
  const d=document.createElement("div");
  d.className="fade-in";
  d.innerHTML='<div class="admin-hd"><div><div class="admin-title">👤 管理者ビュー</div><div class="admin-sub">銀座店 · 閉店記録</div></div>'+
    (overCount>0?'<div class="ot-badge">⚠️ 要確認 '+overCount+'件</div>':'')+
    '</div>'+
    '<div class="legend">'+
    '<span class="legend-item"><span class="legend-dot" style="background:#f0fdf9;border:1.5px solid #0d9488"></span> 通常</span>'+
    '<span class="legend-item"><span class="legend-dot" style="background:#fef2f2;border:1.5px solid #ef4444"></span> 閉店時間超過</span>'+
    '</div>';
  if(state.logs.length===0){
    d.innerHTML+='<div class="empty">記録がまだありません</div>';
  } else {
    state.logs.forEach(log=>{
      const over=isOver(log.completedAt);
      d.innerHTML+='<div class="log-row'+(over?" over":"")+'">'+
        '<div class="log-top">'+
        '<span class="log-date">'+fmt(log.completedAt)+'</span>'+
        '<span class="log-day">'+dayOf(log.completedAt)+'曜日</span>'+
        '<span class="log-name">'+esc(log.name)+'</span>'+
        '<span class="log-badge'+(over?" over":"")+'">+'+(over?"⚠️ 超過":"完了")+'</span>'+
        '</div>'+
        (over?'<div class="ot-note">閉店予定 '+closingLbl(log.completedAt)+' → 完了 '+fmt(log.completedAt).slice(11)+'</div>':'')+
        (log.memo?'<div class="log-memo"><span>📋</span><span class="log-memo-text">'+esc(log.memo)+'</span></div>':'')+
        '</div>';
    });
  }
  d.innerHTML+='<button class="cancel-btn" style="margin-top:16px" onclick="exitAdmin()">管理者モードを終了</button>';
  m.appendChild(d);
}

window.startCheck=()=>{if(state.name.trim()){state.checked={};state.screen="check";render();}};
window.goBack=()=>{state.screen="check";render();};
window.resetApp=async()=>{state.name="";state.checked={};state.memo="";state.doneAt=null;state.screen="name";state.logs=await loadLogs();render();};
window.exitAdmin=()=>{state.adminMode=false;state.screen="name";render();};

window.finishCheck=async()=>{
  if(state.busy)return;
  state.busy=true;
  document.getElementById("finishBtn").textContent="保存中...";
  const now=new Date();
  try{
    await saveLog({name:state.name,completedAt:now.toISOString(),memo:state.memo.trim()});
    state.doneAt=now;
    state.logs=await loadLogs();
    showSync("✓ 保存しました");
    state.busy=false;
    state.screen="done";
    render();
  }catch(e){
    state.busy=false;
    showSync("保存エラー: "+e.message, true);
    document.getElementById("finishBtn").textContent="✓ もう一度試す";
  }
};

window.toggleHistory=async()=>{
  if(state.screen==="history"){
    state.screen=state.name?"check":"name";
    render();
    return;
  }
  if(state.adminMode){state.screen="history";state.logs=await loadLogs();render();return;}
  const overlay=document.createElement("div");
  overlay.className="overlay";
  overlay.innerHTML='<div class="pin-card">'+
    '<div class="pin-title">管理者PIN</div>'+
    '<div class="pin-sub">管理者のみ履歴を閲覧できます</div>'+
    '<input class="pin-input" type="password" inputmode="numeric" maxlength="6" id="pinInp" placeholder="••••">'+
    '<div class="pin-error" id="pinErr">PINが正しくありません</div>'+
    '<button class="btn" style="margin-bottom:8px" onclick="checkPin()">確認</button>'+
    '<button class="cancel-btn" onclick="this.closest(\'.overlay\').remove()">キャンセル</button>'+
    '</div>';
  document.body.appendChild(overlay);
  document.getElementById("pinInp").addEventListener("keydown",e=>{if(e.key==="Enter")window.checkPin();});
  setTimeout(()=>document.getElementById("pinInp").focus(),50);
};

window.checkPin=async()=>{
  const val=document.getElementById("pinInp").value;
  if(val===ADMIN_PIN){
    document.querySelector(".overlay").remove();
    state.adminMode=true;
    state.screen="history";
    state.logs=await loadLogs();
    render();
  }else{
    document.getElementById("pinErr").style.display="block";
    document.getElementById("pinInp").value="";
  }
};

init();
</script>
</body>
</html>
