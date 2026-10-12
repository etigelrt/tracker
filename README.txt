<!DOCTYPE html><html lang="ru"><head><meta charset="utf-8"><title>Трекер привычек</title>
<link rel="manifest" href="manifest.webmanifest"><link rel="apple-touch-icon" href="icon-180.png"><meta name="theme-color" content="#0a0e1a"><meta name="apple-mobile-web-app-capable" content="yes"><meta name="mobile-web-app-capable" content="yes"><meta name="apple-mobile-web-app-title" content="Трекер">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<style>
:root{--bg:#f4f6fb;--cd:#fff;--tx:#18203a;--mu:#6b7490;--bd:#e0e5f0;--ac:#e89a1c;--ok:#1fa36b;--bad:#d9475f;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#0a0e1a;--cd:#131b30;--tx:#e8ecf5;--mu:#98a2bd;--bd:#26304f;--ac:#f5b942;--ok:#4ad4a0;--bad:#ff6b83}}
:root[data-theme="dark"]{--bg:#0a0e1a;--cd:#131b30;--tx:#e8ecf5;--mu:#98a2bd;--bd:#26304f;--ac:#f5b942;--ok:#4ad4a0;--bad:#ff6b83}
*{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent}
body{background:var(--bg);color:var(--tx);font:15px/1.4 -apple-system,system-ui,'Segoe UI',Roboto,sans-serif;padding:14px 14px calc(84px + env(safe-area-inset-bottom,0px));max-width:560px;margin:0 auto}
h1{font-size:20px}h2{font-size:13px;color:var(--ac);letter-spacing:.6px;text-transform:uppercase;margin:0 0 8px}
.card{background:var(--cd);border:1px solid var(--bd);border-radius:16px;padding:14px;margin-bottom:12px}
.top{display:flex;align-items:center;justify-content:space-between;margin-bottom:12px}
.top b{text-transform:capitalize}.nav button,.btn{background:var(--cd);border:1px solid var(--bd);color:var(--tx);border-radius:10px;padding:8px 13px;font-size:15px}
.btn.p{background:var(--ac);color:#111;border-color:var(--ac);font-weight:600}
.prog{display:flex;gap:14px;align-items:center}
.ring{width:84px;height:84px;border-radius:50%;display:grid;place-items:center;flex:none}
.ring i{font-style:normal;width:64px;height:64px;border-radius:50%;background:var(--cd);display:grid;place-items:center;font-weight:700;font-size:18px}
.mu{color:var(--mu);font-size:13px}
.row{display:flex;align-items:center;gap:11px;padding:9px 2px;border-top:1px solid var(--bd)}
.row:first-of-type{border-top:0}.row input[type=checkbox]{width:24px;height:24px;accent-color:var(--ok);flex:none}
.row span{flex:1}.row em{font-style:normal;font-size:12px;color:var(--ac)}
input[type=text],input[type=number],textarea{width:100%;background:var(--bg);border:1px solid var(--bd);color:var(--tx);border-radius:10px;padding:10px;font:inherit}
textarea{min-height:64px;resize:vertical}
.t3{display:flex;gap:8px;align-items:center;margin-bottom:8px}.t3 input[type=checkbox]{width:24px;height:24px;accent-color:var(--ok);flex:none}
.cups{display:flex;align-items:center;justify-content:space-between;gap:10px}.cups big{font-size:22px;font-weight:700}
.bar{height:9px;border-radius:5px;background:var(--bd);overflow:hidden;margin:6px 0}.bar i{display:block;height:100%;background:var(--ac)}
.chips{display:flex;gap:6px;margin:8px 0}.chip{flex:1;text-align:center;padding:6px;border-radius:9px;border:1px solid var(--bd);font-size:13px}.chip.on{background:var(--ok);color:#06150e;border-color:var(--ok);font-weight:700}
.cnt{display:flex;align-items:center;gap:8px;padding:9px 0;border-top:1px solid var(--bd)}.cnt span{flex:1;font-size:14px}.cnt b{min-width:56px;text-align:center}
.wk{display:grid;grid-template-columns:1fr repeat(7,22px) 38px;gap:4px;align-items:center;font-size:12px;padding:5px 0;border-top:1px solid var(--bd)}
.wk.h{border:0;color:var(--mu);text-align:center}.wk .l{overflow:hidden;white-space:nowrap;text-overflow:ellipsis;text-align:left;font-size:13px}
.dt{width:18px;height:18px;border-radius:50%;background:var(--bd);justify-self:center}.dt.on{background:var(--ok)}
.bars{display:flex;gap:6px;align-items:flex-end;height:80px;margin-bottom:6px}.bars div{flex:1;text-align:center;font-size:11px;color:var(--mu)}.bars i{display:block;background:var(--ac);border-radius:5px 5px 0 0;min-height:3px;margin-bottom:3px}
.st{font-size:12px;font-weight:600}.ok{color:var(--ok)}.bad{color:var(--bad)}
nav{position:fixed;left:0;right:0;bottom:0;display:flex;background:var(--cd);border-top:1px solid var(--bd);padding:6px 6px calc(6px + env(safe-area-inset-bottom,0px));max-width:560px;margin:0 auto}
nav button{flex:1;background:none;border:0;color:var(--mu);font-size:11px;padding:6px 0}nav button b{display:block;font-size:20px;font-weight:400}nav button.on{color:var(--ac);font-weight:700}
</style></head><body><div id="app"></div>
<nav id="nav"></nav>
<script>
var G=[{g:'🌅 Утро',i:[['wake','Подъём в 07:00'],['morn','Вода, движение, порядок']]},
{g:'🎯 Фокус и бизнес',i:[['deep','Глубокая работа 2 ч без телефона'],['proj','Проект / продукт'],['sales','Продажи / клиенты'],['top3','Топ-3 задачи выполнены (авто)']]},
{g:'📚 Развитие',i:[['eng','Английский 40 мин'],['read','Чтение 20–30 мин'],['skill','Навыки IT / практика']]},
{g:'💪 Здоровье',i:[['sport','Спорт / тренировка'],['food','Белок, овощи, мало сахара'],['water','Вода 2 л — 8 стаканов (авто)'],['stress','Дыхание / прогулка'],['sleep','Сон 7–8 ч, отбой до 23:00']]},
{g:'🚫 Не делаю',i:[['n1','Без соцсетей до обеда'],['n2','Без импульсных покупок'],['n3','Без ночных переписок'],['n4','Не сравнивал себя с другими'],['n5','Не откладывал на потом']]}];
var ALL=[];G.forEach(function(g){g.i.forEach(function(x){ALL.push({id:x[0],l:x[1]})})});
var CN=[{id:'clients',l:'Платящие клиенты (цель: 10 за 6 мес)',t:10,p:'all'},{id:'contacts',l:'Контакты по продажам за месяц',t:100,p:'m'},{id:'meet',l:'Встречи с клиентами за месяц',t:10,p:'m'},{id:'live',l:'Живая практика английского за неделю',t:1,p:'w'},{id:'trips',l:'Новые страны в этом году',t:1,p:'y'}];
var MR=[['m1','Отложил 20–30% дохода сразу'],['m2','Не брал ненужных кредитов'],['m3','Инвестировал, пусть даже немного'],['m4','Потратил меньше, чем заработал']];
var PR=[{id:'wk',l:'Обзор недели (30 мин, воскресенье)',n:7},{id:'qt',l:'Пересмотр целей (раз в квартал)',n:90},{id:'ck',l:'Чекап у врача (раз в год)',n:365}];
var ST=[1000,3000,10000],tab='today',rs=0;
function key(d){return d.getFullYear()+'-'+String(d.getMonth()+1).padStart(2,'0')+'-'+String(d.getDate()).padStart(2,'0')}
function parse(k){var a=k.split('-').map(Number);return new Date(a[0],a[1]-1,a[2])}
function add(k,n){var d=parse(k);d.setDate(d.getDate()+n);return key(d)}
var TODAY=key(new Date()),cur=TODAY;
function wkey(k){return add(k,-((parse(k).getDay()+6)%7))}
function esc(s){return String(s==null?'':s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/"/g,'&quot;')}
var S;try{S=JSON.parse(localStorage.getItem('trk2'))}catch(e){}
if(!S||!S.d)S={d:{},c:{},m:{},l:{},r:{},inc:'',fund:'',rate:''};
function save(){try{localStorage.setItem('trk2',JSON.stringify(S))}catch(e){}}
function dflt(){return{h:{},top:[{t:'',d:0},{t:'',d:0},{t:'',d:0}],w:0,s:''}}
function day(k){return S.d[k]||(S.d[k]=dflt())}
function done(k,id){var x=S.d[k];if(!x)return false;if(id==='water')return x.w>=8;if(id==='top3')return x.top.every(function(o){return o.t.trim()&&o.d});return !!x.h[id]}
function pct(k){var n=0;ALL.forEach(function(a){if(done(k,a.id))n++});return Math.round(n/ALL.length*100)}
function streak(id){var k=TODAY,n=0;if(!done(k,id))k=add(k,-1);while(n<400&&done(k,id)){n++;k=add(k,-1)}return n}
function pk(p,k){return p==='all'?'all':p==='m'?k.slice(0,7):p==='w'?wkey(k):k.slice(0,4)}
function cget(id,p){return S.c[id+'|'+pk(p,TODAY)]||0}
function vToday(){var x=S.d[cur]||dflt(),p=pct(cur),isT=cur===TODAY;
var dn=parse(cur).toLocaleDateString('ru-RU',{weekday:'long',day:'numeric',month:'long'});
var h='<div class="top"><div class="nav"><button data-b="prev">‹</button></div><div style="text-align:center"><b>'+dn+'</b>'+(isT?'':'<div><button class="btn" data-b="now" style="padding:3px 10px;font-size:12px;margin-top:4px">К сегодня</button></div>')+'</div><div class="nav"><button data-b="next">›</button></div></div>';
h+='<div class="card prog"><div class="ring" style="background:conic-gradient(var(--ac) '+p*3.6+'deg,var(--bd) 0)"><i>'+p+'%</i></div><div><b>Выполнено за день</b><div class="mu">Привычки, вода, топ-3. Главное — не пропускать два дня подряд.</div></div></div>';
h+='<div class="card"><h2>Топ-3 задачи дня</h2>';
for(var i=0;i<3;i++)h+='<div class="t3"><input type="checkbox" data-c="td" data-i="'+i+'"'+(x.top[i].d?' checked':'')+'><input type="text" data-f="tt" data-i="'+i+'" placeholder="Задача '+(i+1)+'" value="'+esc(x.top[i].t)+'"></div>';
h+='</div><div class="card"><h2>Вода</h2><div class="cups"><button class="btn" data-b="w-">−</button><div style="text-align:center"><big>'+x.w+' / 8</big><div class="mu">стаканов по 250 мл = '+(x.w*0.25)+' л</div></div><button class="btn p" data-b="w+">+</button></div></div>';
h+='<div class="card"><h2>Сон, часов</h2><input type="number" step="0.5" min="0" max="14" inputmode="decimal" data-f="sl" placeholder="Например 7.5" value="'+esc(x.s)+'"></div>';
G.forEach(function(g){h+='<div class="card"><h2>'+g.g+'</h2>';g.i.forEach(function(a){var id=a[0],auto=id==='water'||id==='top3',s=streak(id);
h+='<label class="row"><input type="checkbox" '+(auto?'disabled ':'data-c="h" data-id="'+id+'" ')+(done(cur,id)?'checked':'')+'><span>'+a[1]+'</span><em>'+(s>1?'🔥 '+s:'')+'</em></label>'});h+='</div>'});
return h}
function vWeek(){var ds=[];for(var i=6;i>=0;i--)ds.push(add(TODAY,-i));var wd=['вс','пн','вт','ср','чт','пт','сб'];
var h='<h1 style="margin-bottom:12px">Неделя</h1><div class="card"><h2>Выполнение по дням</h2><div class="bars">';
ds.forEach(function(k){var p=pct(k);h+='<div><i style="height:'+Math.max(3,p*0.6)+'px"></i>'+p+'%<br>'+wd[parse(k).getDay()]+'</div>'});
var avg=Math.round(ds.reduce(function(a,k){return a+pct(k)},0)/7);
h+='</div><div class="mu">Среднее за 7 дней: <b>'+avg+'%</b></div></div>';
G.forEach(function(g){h+='<div class="card"><h2>'+g.g+'</h2><div class="wk h"><span></span>'+ds.map(function(k){return'<span>'+wd[parse(k).getDay()]+'</span>'}).join('')+'<span>%</span></div>';
g.i.forEach(function(a){var n=0;h+='<div class="wk"><span class="l">'+a[1].replace(' (авто)','')+'</span>'+ds.map(function(k){var d=done(k,a[0]);if(d)n++;return'<i class="dt'+(d?' on':'')+'"></i>'}).join('')+'<b>'+Math.round(n/7*100)+'</b></div>'});h+='</div>'});
return h}
function vGoals(){var inc=parseFloat(S.inc)||0,nx=ST.filter(function(s){return s>inc})[0]||ST[2],pr=Math.min(100,Math.round(inc/nx*100));
var h='<h1 style="margin-bottom:12px">Цели</h1><div class="card"><h2>Доход в месяц, $</h2><div class="chips">'+ST.map(function(s){return'<div class="chip'+(inc>=s?' on':'')+'">'+s.toLocaleString('ru-RU')+'$</div>'}).join('')+'</div>';
h+='<input type="number" inputmode="decimal" data-f="inc" placeholder="Текущий доход в месяц" value="'+esc(S.inc)+'"><div class="bar"><i style="width:'+pr+'%"></i></div><div class="mu">'+(inc>=ST[2]?'Главная цель достигнута 🎉':'До '+nx+'$: ещё '+Math.max(0,nx-inc)+'$ ('+pr+'%)')+'</div></div>';
h+='<div class="card"><h2>Счётчики</h2>';CN.forEach(function(c){var v=cget(c.id,c.p),p=Math.min(100,Math.round(v/c.t*100));
h+='<div class="cnt"><span>'+c.l+'<div class="bar"><i style="width:'+p+'%"></i></div></span><button class="btn" data-b="c-" data-id="'+c.id+'" data-p="'+c.p+'">−</button><b>'+v+' / '+c.t+'</b><button class="btn p" data-b="c+" data-id="'+c.id+'" data-p="'+c.p+'">+</button></div>'});h+='</div>';
h+='<div class="card"><h2>Финансовая подушка</h2><div class="mu" style="margin-bottom:6px">Сколько месяцев расходов отложено (цель 3–6)</div><input type="number" step="0.5" inputmode="decimal" data-f="fund" value="'+esc(S.fund)+'"><div class="bar"><i style="width:'+Math.min(100,(parseFloat(S.fund)||0)/6*100)+'%"></i></div>';
h+='<div class="mu" style="margin:8px 0 6px">Доля дохода, которую откладываю, % (цель 20–30)</div><input type="number" inputmode="decimal" data-f="rate" value="'+esc(S.rate)+'"></div>';
var ym=TODAY.slice(0,7);h+='<div class="card"><h2>Правила денег, этот месяц</h2>';MR.forEach(function(m){h+='<label class="row"><input type="checkbox" data-c="m" data-id="'+m[0]+'"'+(S.m[ym+'|'+m[0]]?' checked':'')+'><span>'+m[1]+'</span></label>'});return h+'</div>'}
function vRev(){var wk=wkey(TODAY),r=S.r[wk]||{p:['','',''],w:'',f:''};
var h='<h1 style="margin-bottom:12px">Обзор</h1><div class="card"><h2>Периодические дела</h2>';
PR.forEach(function(p){var l=S.l[p.id],n=l?Math.round((parse(TODAY)-parse(l))/864e5):null,late=n===null||n>p.n;
h+='<div class="cnt"><span>'+p.l+'<div class="st '+(late?'bad':'ok')+'">'+(n===null?'ещё не отмечено':n===0?'сегодня ✓':n+' дн. назад'+(late?' — пора':''))+'</div></span><button class="btn p" data-b="pd" data-id="'+p.id+'">Сделал</button></div>'});
h+='</div><div class="card"><h2>Обзор недели (с '+parse(wk).toLocaleDateString('ru-RU',{day:'numeric',month:'long'})+')</h2><div class="mu" style="margin-bottom:6px">3 приоритета на следующую неделю</div>';
for(var i=0;i<3;i++)h+='<input type="text" style="margin-bottom:8px" data-f="rp" data-i="'+i+'" placeholder="Приоритет '+(i+1)+'" value="'+esc(r.p[i])+'">';
h+='<div class="mu" style="margin:4px 0 6px">Что получилось</div><textarea data-f="rw">'+esc(r.w)+'</textarea><div class="mu" style="margin:8px 0 6px">Что не вышло и почему</div><textarea data-f="rf">'+esc(r.f)+'</textarea></div>';
h+='<button class="btn" data-b="rst" style="width:100%;color:var(--bad)">'+(rs?'Нажми ещё раз: удалить все данные':'Сбросить все данные')+'</button>';return h}
function render(){var v={today:vToday,week:vWeek,goals:vGoals,rev:vRev};$('#app').innerHTML=v[tab]();
$('#nav').innerHTML=[['today','✅','Сегодня'],['week','📊','Неделя'],['goals','🎯','Цели'],['rev','📝','Обзор']].map(function(t){return'<button data-t="'+t[0]+'" class="'+(tab===t[0]?'on':'')+'"><b>'+t[1]+'</b>'+t[2]+'</button>'}).join('')}
function $(s){return document.querySelector(s)}
document.addEventListener('click',function(e){var t=e.target.closest('[data-t]');if(t){tab=t.dataset.t;rs=0;render();window.scrollTo(0,0);return}
var b=e.target.closest('[data-b]');if(!b)return;var a=b.dataset.b,id=b.dataset.id;
if(a==='prev')cur=add(cur,-1);else if(a==='next')cur=add(cur,1);else if(a==='now')cur=TODAY;
else if(a==='w+')day(cur).w=Math.min(20,day(cur).w+1);else if(a==='w-')day(cur).w=Math.max(0,day(cur).w-1);
else if(a==='c+'||a==='c-'){var k=id+'|'+pk(b.dataset.p,TODAY);S.c[k]=Math.max(0,(S.c[k]||0)+(a==='c+'?1:-1))}
else if(a==='pd')S.l[id]=TODAY;
else if(a==='rst'){if(!rs){rs=1;render();return}S={d:{},c:{},m:{},l:{},r:{},inc:'',fund:'',rate:''};rs=0}
save();render()});
document.addEventListener('change',function(e){var c=e.target.dataset.c;if(!c)return;var i=+e.target.dataset.i,id=e.target.dataset.id;
if(c==='h')day(cur).h[id]=e.target.checked;else if(c==='td')day(cur).top[i].d=e.target.checked?1:0;else if(c==='m')S.m[TODAY.slice(0,7)+'|'+id]=e.target.checked;
save();render()});
document.addEventListener('input',function(e){var f=e.target.dataset.f;if(!f)return;var v=e.target.value,i=+e.target.dataset.i,wk=wkey(TODAY);
function rv(){return S.r[wk]||(S.r[wk]={p:['','',''],w:'',f:''})}
if(f==='tt')day(cur).top[i].t=v;else if(f==='sl')day(cur).s=v;else if(f==='inc')S.inc=v;else if(f==='fund')S.fund=v;else if(f==='rate')S.rate=v;
else if(f==='rp')rv().p[i]=v;else if(f==='rw')rv().w=v;else if(f==='rf')rv().f=v;save()});
document.addEventListener('focusout',function(e){if(e.target.dataset&&(e.target.dataset.f==='inc'||e.target.dataset.f==='fund'))render()});
render();
if('serviceWorker' in navigator)navigator.serviceWorker.register('sw.js').catch(function(){});
</script></body></html>
