[index.html](https://github.com/user-attachments/files/31874802/index.html)
<!doctype html>
<html lang="zh-Hant">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover">
<meta name="theme-color" content="#fff7f2">
<title>HW × ZONA｜共同開銷</title>
<style>
:root{--bg:#fff8f4;--card:#fff;--text:#302b29;--muted:#8b817b;--line:#eee4df;--accent:#d97757;--red:#c65d5d;--green:#4d8b6b;--orange:#b9772c}
*{box-sizing:border-box}body{margin:0;background:var(--bg);color:var(--text);font-family:-apple-system,BlinkMacSystemFont,"Noto Sans TC","PingFang TC",sans-serif}
.app{max-width:520px;margin:auto;padding:24px 18px 120px}.top{display:flex;justify-content:space-between;align-items:center;margin-bottom:18px}
h1{font-size:22px;margin:0}.month{font-size:14px;color:var(--muted);background:#fff;border:1px solid var(--line);padding:8px 10px;border-radius:12px}
.card{background:var(--card);border:1px solid var(--line);border-radius:22px;padding:20px;margin-bottom:14px;box-shadow:0 6px 20px #6b49330b}
.label{font-size:13px;color:var(--muted)}.balance{font-size:38px;font-weight:800;margin:5px 0 15px}.progress{height:10px;background:#f0e8e4;border-radius:99px;overflow:hidden}.bar{height:100%;background:var(--accent);width:0;border-radius:99px}
.stats{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-top:15px}.people{display:grid;grid-template-columns:repeat(3,1fr);gap:8px}.stat,.person{background:#fffaf7;border-radius:15px;padding:12px}.stat b,.person b{display:block;font-size:18px;margin-top:4px}.person{font-size:13px}.person b{font-size:16px}
.section-title{font-weight:750;margin:20px 3px 10px}.empty{text-align:center;color:var(--muted);padding:25px}
.item{padding:14px 0;border-bottom:1px solid var(--line)}.item:last-child{border-bottom:0}.item-head{display:flex;justify-content:space-between;gap:12px}.item small{color:var(--muted);line-height:1.55}.amount{font-weight:750}.expense{color:var(--red)}.income{color:var(--green)}
.meta{margin-top:5px}.badges{display:flex;gap:6px;flex-wrap:wrap;margin-top:7px}.badge{font-size:12px;padding:4px 8px;border-radius:99px;background:#f5efec;color:#6f625c}.badge.pending{background:#fff3df;color:var(--orange)}.badge.done{background:#edf8f1;color:var(--green)}
.item-actions{display:flex;justify-content:flex-end;gap:7px;margin-top:10px}.mini{padding:7px 10px;border-radius:10px;background:#f5efec;color:#635751;font-size:13px}.mini.done{background:#edf8f1;color:var(--green)}.mini.delete{background:#fff0f0;color:var(--red)}
button{border:0;font:inherit;cursor:pointer}.bottom-actions{position:fixed;left:50%;transform:translateX(-50%);bottom:18px;width:min(484px,calc(100% - 36px));display:grid;grid-template-columns:1fr 1.4fr;gap:9px}.fab{padding:15px 10px;border-radius:18px;font-weight:750;font-size:16px;box-shadow:0 10px 25px #6b493320}.fab.secondary{background:#fff;color:var(--accent);border:1px solid var(--line)}.fab.primary{background:var(--accent);color:white}
dialog{border:0;border-radius:22px;width:min(480px,calc(100% - 30px));padding:0;box-shadow:0 20px 60px #0003}dialog::backdrop{background:#2b211d66}.form{padding:22px}.form h2{margin:0 0 18px}.field{margin:12px 0}.field label{display:block;font-size:13px;color:var(--muted);margin-bottom:6px}input,select{width:100%;padding:13px;border:1px solid var(--line);border-radius:13px;background:#fff;font:inherit}.row{display:flex;gap:9px}.row>*{flex:1}.actions{display:flex;gap:9px;margin-top:18px}.actions button{flex:1;padding:13px;border-radius:13px}.cancel{background:#f4eeeb}.save{background:var(--accent);color:#fff}.note{font-size:12px;color:var(--muted);line-height:1.6}.topup-note{background:#f7fbf8;border:1px solid #e0eee5;border-radius:14px;padding:11px 12px;font-size:13px;color:#5f7567;margin-top:10px}
.reimburse-card{background:#fffaf4;border:1px solid #f3dfc4;border-radius:16px;padding:13px 14px;margin-bottom:14px}.reimburse-card b{display:block;font-size:18px;margin-top:3px}
</style>
</head>
<body>
<main class="app">
<div class="top"><div><h1>❤️ HW × ZONA</h1><div id="syncStatus" style="font-size:12px;color:var(--muted);margin-top:5px">☁️ 連線中…</div></div><div class="month" id="monthLabel"></div></div>
<section class="card">
<div class="label">本月共同開銷剩餘</div><div class="balance" id="balance">$6,000</div>
<div class="label" id="spentLabel">已支出 $0／可用 $6,000</div>
<div style="margin-top:9px" class="progress"><div class="bar" id="bar"></div></div>
<div class="stats"><div class="stat"><span class="label">本月可用</span><b id="budget">$6,000</b></div><div class="stat"><span class="label">已支出</span><b id="spent">$0</b></div></div>
<div class="topup-note" id="topupSummary">基本公基金 $6,000 ・ 本月儲值 $0</div>
</section>

<div class="section-title">🧾 待請款</div>
<div class="reimburse-card"><span class="label">目前尚未完成請款</span><b id="pendingTotal">$0</b><span class="label" id="pendingDetail">阿偉 $0 ・ 曉吟 $0</span></div>

<div class="section-title">👫 本月實際付款</div>
<section class="card people"><div class="person">👨 阿偉<b id="hao">$0</b></div><div class="person">👩 曉吟<b id="yin">$0</b></div><div class="person">💰 公基金<b id="fund">$0</b></div></section>
<div class="section-title">📖 最近紀錄</div><section class="card" id="list"></section>
<p class="note">付款人會保留「當下真正付錢的人」。若負擔對象不同，系統會標記為待請款；完成請款後只更新狀態，不會改掉原始付款人。</p>
</main>

<div class="bottom-actions"><button class="fab secondary" onclick="openTopupForm()">＋ 儲值</button><button class="fab primary" onclick="openExpenseForm()">＋ 記共同開銷</button></div>

<dialog id="expenseDlg"><form class="form" onsubmit="saveExpense(event)">
<h2 id="expenseFormTitle">＋ 新增共同開銷</h2>
<input id="editingId" type="hidden">
<div class="field"><label>項目</label><input id="expenseTitle" maxlength="40" placeholder="例如：晚餐、超市採買" required></div>
<div class="field"><label>金額</label><input id="expenseAmount" type="number" min="1" step="1" placeholder="例如 500" required></div>
<div class="row">
<div class="field"><label>實際付款人</label><select id="expensePayer"><option>阿偉</option><option>曉吟</option><option>公基金</option></select></div>
<div class="field"><label>最後負擔對象</label><select id="expenseBurden"><option>公基金</option><option>阿偉</option><option>曉吟</option></select></div>
</div>
<div class="row"><div class="field"><label>類別</label><select id="expenseCategory"><option>吃飯</option><option>交通</option><option>娛樂</option><option>日用品</option><option>生活</option><option>其他</option></select></div>
<div class="field"><label>日期</label><input id="expenseDate" type="date" required></div></div>
<div class="field"><label>備註</label><input id="expenseMemo" maxlength="80" placeholder="可留空"></div>
<div class="actions"><button type="button" class="cancel" onclick="expenseDlg.close()">取消</button><button class="save" type="submit">儲存</button></div>
</form></dialog>

<dialog id="topupDlg"><form class="form" onsubmit="saveTopup(event)">
<h2>＋ 儲值到公基金</h2>
<div class="field"><label>金額</label><input id="topupAmount" type="number" min="1" step="1" placeholder="例如 1000" required></div>
<div class="row"><div class="field"><label>儲值類型</label><select id="topupKind"><option>上期結餘</option><option>臨時加值</option><option>其他</option></select></div>
<div class="field"><label>來源</label><select id="topupSource"><option>公基金</option><option>阿偉</option><option>曉吟</option></select></div></div>
<div class="field"><label>日期</label><input id="topupDate" type="date" required></div>
<div class="field"><label>備註</label><input id="topupMemo" maxlength="80" placeholder="例如：8 月剩餘帶入"></div>
<div class="actions"><button type="button" class="cancel" onclick="topupDlg.close()">取消</button><button class="save" type="submit">儲值</button></div>
</form></dialog>

<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>
<script>
const SUPABASE_URL="https://covelofbpxltkyhjfkgn.supabase.co";
const SUPABASE_KEY="sb_publishable_IW1-d7fZqbZ0zYHE0BWW_A_cA5mP3jb";
const { createClient } = supabase;
const db=createClient(SUPABASE_URL,SUPABASE_KEY);
const BASE_BUDGET=6000;
const now=new Date(),ym=now.toISOString().slice(0,7);
document.querySelector("#monthLabel").textContent=now.getFullYear()+" 年 "+(now.getMonth()+1)+" 月";
let records=[];

function money(n){return "$"+Number(n||0).toLocaleString("zh-TW")}
function escapeHtml(v){return String(v??"").replace(/[&<>'"]/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;',"'":'&#39;','"':'&quot;'}[c]));}
function today(){return new Date().toISOString().slice(0,10)}
function isTopup(x){return String(x.title||"").startsWith("TOPUP|")}
function topupInfo(x){const p=String(x.title||"").split("|");return {kind:p[1]||"其他",source:p[2]||"公基金"}}
function expenseName(x){return isTopup(x)?"":x.title||x.category||"共同開銷"}

function render(){
 const current=records.filter(x=>x.expense_date?.slice(0,7)===ym);
 const expenses=current.filter(x=>!isTopup(x));
 const topups=current.filter(isTopup);
 const spent=expenses.reduce((s,x)=>s+Number(x.amount),0);
 const added=topups.reduce((s,x)=>s+Number(x.amount),0);
 const budget=BASE_BUDGET+added,balance=budget-spent;
 document.querySelector("#balance").textContent=money(balance);
 document.querySelector("#budget").textContent=money(budget);
 document.querySelector("#spent").textContent=money(spent);
 document.querySelector("#spentLabel").textContent=`已支出 ${money(spent)}／可用 ${money(budget)}`;
 document.querySelector("#topupSummary").textContent=`基本公基金 ${money(BASE_BUDGET)} ・ 本月儲值 ${money(added)}`;
 document.querySelector("#bar").style.width=(budget?Math.min(100,spent/budget*100):0)+"%";

 const payerTotal=p=>expenses.filter(x=>x.payer===p).reduce((s,x)=>s+Number(x.amount),0);
 document.querySelector("#hao").textContent=money(payerTotal("阿偉"));
 document.querySelector("#yin").textContent=money(payerTotal("曉吟"));
 document.querySelector("#fund").textContent=money(payerTotal("公基金"));

 const pending=expenses.filter(x=>x.reimbursement_status==="待請款");
 const pendingTotal=pending.reduce((s,x)=>s+Number(x.amount),0);
 const pendingBy=p=>pending.filter(x=>x.payer===p).reduce((s,x)=>s+Number(x.amount),0);
 document.querySelector("#pendingTotal").textContent=money(pendingTotal);
 document.querySelector("#pendingDetail").textContent=`阿偉 ${money(pendingBy("阿偉"))} ・ 曉吟 ${money(pendingBy("曉吟"))}`;

 current.sort((a,b)=>b.expense_date.localeCompare(a.expense_date)||String(b.created_at).localeCompare(String(a.created_at)));
 document.querySelector("#list").innerHTML=current.length?current.map(x=>{
   if(isTopup(x)){
     const t=topupInfo(x);
     return `<div class="item"><div class="item-head"><div><b>＋ ${escapeHtml(t.kind)}</b><div class="meta"><small>來源：${escapeHtml(t.source)} ・ ${escapeHtml(x.expense_date)}</small><br><small>${escapeHtml(x.memo||"")}</small></div></div><div class="amount income">+${money(x.amount)}</div></div><div class="item-actions"><button class="mini delete" onclick="removeRecord('${x.id}')">刪除</button></div></div>`;
   }
   const statusClass=x.reimbursement_status==="待請款"?"pending":x.reimbursement_status==="已請款"?"done":"";
   const action=x.reimbursement_status==="待請款"
     ? `<button class="mini done" onclick="toggleReimbursement('${x.id}')">✓ 完成請款</button>`
     : x.reimbursement_status==="已請款"
       ? `<button class="mini" onclick="toggleReimbursement('${x.id}')">↩ 改回待請款</button>`
       : "";
   return `<div class="item">
     <div class="item-head"><div><b>${escapeHtml(expenseName(x))}</b><div class="meta"><small>${escapeHtml(x.category)} ・ ${escapeHtml(x.expense_date)}</small><br><small>${escapeHtml(x.memo||"")}</small></div></div><div class="amount expense">-${money(x.amount)}</div></div>
     <div class="badges"><span class="badge">付款：${escapeHtml(x.payer)}</span><span class="badge">負擔：${escapeHtml(x.burden)}</span><span class="badge ${statusClass}">${escapeHtml(x.reimbursement_status)}</span></div>
     <div class="item-actions">${action}<button class="mini" onclick="editExpense('${x.id}')">✏️ 編輯</button><button class="mini delete" onclick="removeRecord('${x.id}')">刪除</button></div>
   </div>`;
 }).join(""):'<div class="empty">這個月還沒有紀錄<br>開始記第一筆共同開銷吧 ❤️</div>';
}

async function loadRecords(){
 const {data,error}=await db.from("shared_expenses").select("*").order("expense_date",{ascending:false}).order("created_at",{ascending:false});
 if(error){console.error(error);alert("雲端資料讀取失敗：\n"+error.message);return;}
 records=data||[];render();
}

function openExpenseForm(){
 document.querySelector("#expenseFormTitle").textContent="＋ 新增共同開銷";
 document.querySelector("#editingId").value="";
 document.querySelector("#expenseDlg form").reset();
 document.querySelector("#expenseDate").value=today();
 document.querySelector("#expenseBurden").value="公基金";
 document.querySelector("#expenseDlg").showModal();
}
function openTopupForm(){
 document.querySelector("#topupDlg form").reset();
 document.querySelector("#topupDate").value=today();
 document.querySelector("#topupDlg").showModal();
}
function editExpense(id){
 const x=records.find(r=>r.id===id);
 if(!x||isTopup(x))return;
 document.querySelector("#expenseFormTitle").textContent="✏️ 編輯共同開銷";
 document.querySelector("#editingId").value=x.id;
 document.querySelector("#expenseTitle").value=x.title||"";
 document.querySelector("#expenseAmount").value=x.amount;
 document.querySelector("#expensePayer").value=x.payer;
 document.querySelector("#expenseBurden").value=x.burden;
 document.querySelector("#expenseCategory").value=x.category;
 document.querySelector("#expenseDate").value=x.expense_date;
 document.querySelector("#expenseMemo").value=x.memo||"";
 document.querySelector("#expenseDlg").showModal();
}

async function saveExpense(e){
 e.preventDefault();
 const id=document.querySelector("#editingId").value;
 const payer=document.querySelector("#expensePayer").value;
 const burden=document.querySelector("#expenseBurden").value;
 let status=(payer===burden)?"不需請款":"待請款";
 if(id){
   const old=records.find(r=>r.id===id);
   if(old && old.reimbursement_status==="已請款" && old.payer===payer && old.burden===burden) status="已請款";
 }
 const payload={
   title:document.querySelector("#expenseTitle").value.trim(),
   amount:Number(document.querySelector("#expenseAmount").value),
   payer, burden,
   reimbursement_status:status,
   category:document.querySelector("#expenseCategory").value,
   expense_date:document.querySelector("#expenseDate").value,
   memo:document.querySelector("#expenseMemo").value.trim()||null,
   updated_at:new Date().toISOString()
 };
 const btn=e.submitter;btn.disabled=true;btn.textContent="儲存中…";
 const result=id
   ? await db.from("shared_expenses").update(payload).eq("id",id)
   : await db.from("shared_expenses").insert(payload);
 btn.disabled=false;btn.textContent="儲存";
 if(result.error){alert("儲存失敗："+result.error.message);return;}
 document.querySelector("#expenseDlg").close();await loadRecords();
}

async function saveTopup(e){
 e.preventDefault();
 const kind=document.querySelector("#topupKind").value,source=document.querySelector("#topupSource").value;
 const payload={
   title:`TOPUP|${kind}|${source}`,
   amount:Number(document.querySelector("#topupAmount").value),
   payer:source,
   burden:"公基金",
   reimbursement_status:"不需請款",
   category:"其他",
   expense_date:document.querySelector("#topupDate").value,
   memo:document.querySelector("#topupMemo").value.trim()||null,
   updated_at:new Date().toISOString()
 };
 const btn=e.submitter;btn.disabled=true;btn.textContent="儲值中…";
 const {error}=await db.from("shared_expenses").insert(payload);
 btn.disabled=false;btn.textContent="加入";
 if(error){alert("儲值失敗："+error.message);return;}
 document.querySelector("#topupDlg").close();await loadRecords();
}

async function toggleReimbursement(id){
 const x=records.find(r=>r.id===id);
 if(!x||!["待請款","已請款"].includes(x.reimbursement_status))return;

 const nextStatus=x.reimbursement_status==="待請款" ? "已請款" : "待請款";
 const message=nextStatus==="已請款"
   ? `確認「${expenseName(x)}」${money(x.amount)} 已完成請款？\n付款人 ${x.payer} 會保留不變。`
   : `要把「${expenseName(x)}」${money(x.amount)} 改回待請款嗎？\n付款人 ${x.payer} 會保留不變。`;

 if(!confirm(message))return;

 const {error}=await db.from("shared_expenses")
   .update({reimbursement_status:nextStatus,updated_at:new Date().toISOString()})
   .eq("id",id);

 if(error){alert("更新失敗："+error.message);return;}
 await loadRecords();
}

async function removeRecord(id){
 if(!confirm("確定要刪除這筆紀錄嗎？"))return;
 const {error}=await db.from("shared_expenses").delete().eq("id",id);
 if(error){alert("刪除失敗："+error.message);return;}
 await loadRecords();
}

db.channel("shared-expenses-live")
  .on("postgres_changes",{event:"*",schema:"public",table:"shared_expenses"},()=>loadRecords())
  .subscribe((status)=>{
    const el=document.querySelector("#syncStatus");
    if(status==="SUBSCRIBED") el.textContent="☁️ 已同步・兩邊共用";
    else if(status==="CHANNEL_ERROR"||status==="TIMED_OUT") el.textContent="⚠️ 同步連線異常";
    else el.textContent="☁️ 連線中…";
  });
loadRecords();
</script>
</body></html>
