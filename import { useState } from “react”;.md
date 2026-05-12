import { useState } from “react”;  
  
const DAYS = [  
{  
id:1,dateLabel:“24 mai”,dayNum:“24”,month:“MAI”,weekday:“Samedi 24 mai”,location:“Albufeira”,color:”#ff6b35”,  
budget:{total:“51”,lines:[{l:“Taxi arrivée”,a:“6 €”},{l:“Courses”,a:“25 €”},{l:“Soirée bars”,a:“20 €”}]},  
stops:[  
{lat:37.0892,lng:-8.2506,name:“Appartement / Arrivée”,emoji:“🏠”},  
{lat:37.0860,lng:-8.2490,name:“Albufeira Old Town”,emoji:“🏘️”},  
{lat:37.0848,lng:-8.2513,name:“Praia dos Pescadores”,emoji:“🌊”},  
{lat:37.0858,lng:-8.2497,name:“Rua Cândido dos Reis”,emoji:“🍹”},  
],  
acts:[  
{i:“✈️”,n:“Départ 18h00 — arrivée 19h15”,d:“Taxi depuis l’aéroport”,p:“6 €/pers”,c:”#0088bb”},  
{i:“🏠”,n:“Installation à l’appart”,d:null,p:null,c:”#90a4ae”},  
{i:“🛒”,n:“Courses rapides”,d:“Supermarché”,p:“25 €/pers”,c:”#00b388”},  
{i:“🚶”,n:“Balade dans Albufeira Old Town”,d:null,p:null,c:”#f4a435”},  
{i:“🌊”,n:“Praia dos Pescadores de nuit”,d:“La plage centrale d’Albufeira”,p:null,c:”#0088bb”},  
{i:“🍳”,n:“Repas à l’appart”,d:null,p:null,c:”#90a4ae”},  
{i:“🍹”,n:“Soirée bars Old Town”,d:null,p:“20 €/pers”,c:”#e040fb”},  
],  
tip:“👉 Petite rue sympa : Rua Cândido dos Reis — plein de bars !”  
},  
{  
id:2,dateLabel:“25 mai”,dayNum:“25”,month:“MAI”,weekday:“Dimanche 25 mai”,location:“Albufeira”,color:”#00b388”,  
budget:{total:“44”,lines:[{l:“Bus São Rafael A/R”,a:“4 €”},{l:“Soirée The Strip”,a:“20 €”},{l:“Divers”,a:“20 €”}]},  
stops:[  
{lat:37.0892,lng:-8.2506,name:“Appartement”,emoji:“🏠”},  
{lat:37.0792,lng:-8.2772,name:“Marina de Albufeira”,emoji:“⛵”},  
{lat:37.0733,lng:-8.2968,name:“Praia de São Rafael”,emoji:“🏖️”},  
{lat:37.0718,lng:-8.3015,name:“Praia da Coelha”,emoji:“🏖️”},  
{lat:37.0895,lng:-8.2360,name:“The Strip Albufeira”,emoji:“🎉”},  
],  
acts:[  
{i:“🏊”,n:“Piscine chill”,d:null,p:null,c:”#0088bb”},  
{i:“⛵”,n:“Marina de Albufeira”,d:“Port coloré, photos sympas”,p:null,c:”#f4a435”},  
{i:“🍳”,n:“Repas à l’appart”,d:null,p:null,c:”#90a4ae”},  
{i:“🚌”,n:“Praia de São Rafael”,d:“Bus aller-retour”,p:“4 €/pers”,c:”#0088bb”},  
{i:“🏖️”,n:“Praia da Coelha”,d:“Dans la foulée”,p:null,c:”#f4a435”},  
{i:“🍳”,n:“Repas à l’appart”,d:null,p:null,c:”#90a4ae”},  
{i:“🎉”,n:“Soirée sur The Strip”,d:null,p:“20 €/pers”,c:”#e040fb”},  
],  
tip:null  
},  
{  
id:3,dateLabel:“26 mai”,dayNum:“26”,month:“MAI”,weekday:“Lundi 26 mai”,location:“Albufeira”,color:”#0088bb”,  
budget:{total:“117”,lines:[{l:“Kayak + transport”,a:“41 €”},{l:“Praia da Falésia”,a:“6 €”},{l:“Water sport”,a:“15 €”},{l:“Fast food”,a:“10 €”},{l:“Boat party sunset”,a:“45 €”}]},  
stops:[  
{lat:37.0855,lng:-8.2520,name:“Kayak — Albufeira”,emoji:“🚣”},  
{lat:37.0972,lng:-8.1898,name:“Praia da Falésia”,emoji:“🏖️”},  
{lat:37.0820,lng:-8.2630,name:“Water Sport Center”,emoji:“🌊”},  
{lat:37.0792,lng:-8.2772,name:“Marina (Boat Party)”,emoji:“🛥️”},  
],  
acts:[  
{i:“🚣”,n:“Activité Kayak”,d:”+ 6 € A/R”,p:“35 €/pers”,c:”#0088bb”},  
{i:“🧺”,n:“Pique-nique”,d:null,p:null,c:”#00b388”},  
{i:“🏖️”,n:“Praia da Falésia”,d:“Falaises rouges & sable blanc”,p:“6 €/pers”,c:”#f4a435”},  
{i:“🌊”,n:“Water Sport Center”,d:“Bouées tractées”,p:“15 €/pers”,c:”#0088bb”},  
{i:“🍔”,n:“Fast food”,d:null,p:“10 €/pers”,c:”#00b388”},  
{i:“🛥️”,n:“Boat Party Sunset 🌅”,d:null,p:“45 €/pers”,c:”#ff6b35”},  
],  
tip:null  
},  
{  
id:4,dateLabel:“27 mai”,dayNum:“27”,month:“MAI”,weekday:“Mardi 27 mai”,location:“Albufeira”,color:”#9c4dcc”,  
budget:{total:“54”,lines:[{l:“Bus Ninho de Andorinha A/R”,a:“4 €”},{l:“Restaurant”,a:“30 €”},{l:“Soirée”,a:“20 €”}]},  
stops:[  
{lat:37.0892,lng:-8.2506,name:“Appartement”,emoji:“🏠”},  
{lat:37.1137,lng:-8.3012,name:“Praia do Ninho de Andorinha”,emoji:“🏖️”},  
{lat:37.1040,lng:-8.3060,name:“Miradouro do Pau da Bandeira”,emoji:“🌅”},  
{lat:37.0860,lng:-8.2490,name:“Old Town / The Strip”,emoji:“🎉”},  
],  
acts:[  
{i:“🏊”,n:“Piscine le matin”,d:null,p:null,c:”#0088bb”},  
{i:“🚌”,n:“Praia do Ninho de Andorinha”,d:“Crique cachée”,p:“4 €/pers A/R”,c:”#0088bb”},  
{i:“🧺”,n:“Pique-nique”,d:null,p:null,c:”#00b388”},  
{i:“🌅”,n:“Coucher de soleil”,d:“Miradouro do Pau da Bandeira”,p:null,c:”#ff6b35”},  
{i:“🍽️”,n:“Restaurant”,d:null,p:“30 €/pers”,c:”#00b388”},  
{i:“🎉”,n:“Bars Old Town / The Strip”,d:null,p:“20 €/pers”,c:”#e040fb”},  
],  
tip:null  
},  
{  
id:5,dateLabel:“28 mai”,dayNum:“28”,month:“MAI”,weekday:“Mercredi 28 mai”,location:“Albufeira → Vilamoura”,color:”#f4a435”,  
budget:{total:“27”,lines:[{l:“Bus Vilamoura A/R”,a:“4 €”},{l:“Croisière catamaran sunset”,a:“23 €”}]},  
stops:[  
{lat:37.0892,lng:-8.2506,name:“Appartement”,emoji:“🏠”},  
{lat:37.0711,lng:-8.1191,name:“Marina de Vilamoura”,emoji:“⛵”},  
],  
acts:[  
{i:“🌴”,n:“Brunch / Piscine / Plage chill”,d:null,p:null,c:”#f4a435”},  
{i:“🍳”,n:“Repas à l’appart”,d:null,p:null,c:”#90a4ae”},  
{i:“🚌”,n:“Bus pour Vilamoura”,d:null,p:“4 €/pers A/R”,c:”#0088bb”},  
{i:“⛵”,n:“Croisière catamaran sunset 🌅”,d:“Depuis Vilamoura”,p:“23 €/pers”,c:”#0088bb”},  
{i:“🍳”,n:“Repas à l’appart”,d:null,p:null,c:”#90a4ae”},  
{i:“🛋️”,n:“Soirée chill à l’appart”,d:null,p:null,c:”#90a4ae”},  
],  
tip:null  
},  
{  
id:6,dateLabel:“29 mai”,dayNum:“29”,month:“MAI”,weekday:“Jeudi 29 mai”,location:“Albufeira + Algarve”,color:”#ff6b35”,  
budget:{total:“69”,lines:[{l:“Bus Prainha A/R”,a:“4 €”},{l:“Quad / Buggy”,a:“45 €”},{l:“Bars”,a:“20 €”}]},  
stops:[  
{lat:37.0805,lng:-8.3155,name:“Praia da Prainha”,emoji:“🏖️”},  
{lat:37.1200,lng:-8.2800,name:“Arrière-pays — Quad”,emoji:“🚙”},  
{lat:37.0985,lng:-8.4020,name:“Praia da Marinha”,emoji:“🌅”},  
],  
acts:[  
{i:“🚌”,n:“Praia da Prainha”,d:“Bus aller-retour”,p:“4 €/pers”,c:”#0088bb”},  
{i:“🧺”,n:“Pique-nique”,d:null,p:null,c:”#00b388”},  
{i:“🚙”,n:“Quad / Buggy arrière-pays Algarve”,d:null,p:“45 €/pers”,c:”#ff6b35”},  
{i:“🍳”,n:“Repas à l’appart”,d:null,p:null,c:”#90a4ae”},  
{i:“🌅”,n:“Coucher de soleil à Praia da Marinha”,d:“Plage mythique”,p:null,c:”#ff6b35”},  
{i:“🍹”,n:“Bars”,d:null,p:“20 €/pers”,c:”#e040fb”},  
],  
tip:null  
},  
{  
id:7,dateLabel:“30 mai”,dayNum:“30”,month:“MAI”,weekday:“Vendredi 30 mai”,location:“Albufeira → Lagos”,color:”#00b388”,  
budget:{total:“64–109”,lines:[{l:“Excursion dauphins (optionnel)”,a:“40 €”},{l:“Bus Praia do Camilo A/R”,a:“4 €”},{l:“Soirée The Strip”,a:“20 €”}]},  
stops:[  
{lat:37.0892,lng:-8.2506,name:“Appartement”,emoji:“🏠”},  
{lat:37.0844,lng:-8.6656,name:“Praia do Camilo — Lagos”,emoji:“🌅”},  
{lat:37.0895,lng:-8.2360,name:“The Strip Albufeira”,emoji:“🎉”},  
],  
acts:[  
{i:“🐬”,n:“Excursion dauphins (optionnel)”,d:“ou piscine chill”,p:“40 €/pers”,c:”#0088bb”},  
{i:“🍳”,n:“Repas à l’appart”,d:null,p:null,c:”#90a4ae”},  
{i:“🚌”,n:“Praia do Camilo — coucher de soleil”,d:“Plage mythique, Lagos”,p:“4 €/pers A/R”,c:”#0088bb”},  
{i:“🧺”,n:“Pique-nique”,d:null,p:null,c:”#00b388”},  
{i:“🎉”,n:“Dernière grosse soirée au Strip 🔥”,d:null,p:“20 €/pers”,c:”#e040fb”},  
],  
tip:null  
},  
{  
id:8,dateLabel:“31 mai”,dayNum:“31”,month:“MAI”,weekday:“Samedi 31 mai”,location:“Albufeira — Retour”,color:”#78909c”,  
budget:{total:“31”,lines:[{l:“Repas extérieur ×2”,a:“20 €”},{l:“Transport retour aéroport”,a:“11 €”}]},  
stops:[  
{lat:37.0892,lng:-8.2506,name:“Appartement”,emoji:“🏠”},  
{lat:37.0860,lng:-8.2490,name:“Old Town — Shopping”,emoji:“🛍️”},  
],  
acts:[  
{i:“🌊”,n:“Chill plage / Piscine”,d:null,p:null,c:”#0088bb”},  
{i:“🍽️”,n:“Repas à l’extérieur”,d:null,p:“10 €/pers”,c:”#00b388”},  
{i:“🛍️”,n:“Shopping souvenirs”,d:null,p:null,c:”#f4a435”},  
{i:“🚶”,n:“Balade dans la ville”,d:null,p:null,c:”#f4a435”},  
{i:“🍽️”,n:“Repas à l’extérieur”,d:null,p:“10 €/pers”,c:”#00b388”},  
{i:“✈️”,n:“Départ 19h55 — arrivée 23h10”,d:null,p:“11 €/pers”,c:”#0088bb”},  
],  
tip:null  
},  
];  
  
// ── Map projection ───────────────────────────────────────────────────────────  
const VW = 400, VH = 280;  
const allLats = DAYS.flatMap(d => d.stops.map(s => s.lat));  
const allLngs = DAYS.flatMap(d => d.stops.map(s => s.lng));  
const minLat = Math.min(…allLats) - 0.03;  
const maxLat = Math.max(…allLats) + 0.03;  
const minLng = Math.min(…allLngs) - 0.08;  
const maxLng = Math.max(…allLngs) + 0.08;  
  
function proj(lat, lng) {  
return {  
x: ((lng - minLng) / (maxLng - minLng)) * VW,  
y: VH - ((lat - minLat) / (maxLat - minLat)) * VH,  
};  
}  
  
// Pre-number all stops  
let _sn = 0;  
const STOPS_FLAT = DAYS.flatMap(day =>  
day.stops.map(stop => ({ …stop, num: ++_sn, dayId: day.id, color: day.color, weekday: day.weekday }))  
);  
  
// ── OSM-style SVG Map ────────────────────────────────────────────────────────  
function MapSVG({ activeDay }) {  
const [tip, setTip] = useState(null);  
  
// Algarve south coastline  
const coast = [  
{lat:36.98,lng:minLng+0.02},{lat:37.005,lng:-8.655},{lat:36.995,lng:-8.595},  
{lat:36.975,lng:-8.535},{lat:36.965,lng:-8.475},{lat:36.962,lng:-8.415},  
{lat:36.968,lng:-8.375},{lat:36.990,lng:-8.335},{lat:37.018,lng:-8.285},  
{lat:37.028,lng:-8.235},{lat:37.028,lng:-8.175},{lat:37.012,lng:-8.115},  
{lat:36.975,lng:-8.075},{lat:36.962,lng:maxLng-0.02},  
].map(p => proj(p.lat, p.lng));  
  
const landPts = [  
{x:0,y:0},{x:VW,y:0},{x:VW,y:coast[coast.length-1].y},  
…coast.slice().reverse(),  
{x:0,y:coast[0].y}  
].map(p=>`${(+p.x).toFixed(1)},${(+p.y).toFixed(1)}`).join(’ ’);  
  
const coastD = ‘M’+coast.map(p=>`${p.x.toFixed(1)},${p.y.toFixed(1)}`).join(‘L’);  
  
// A22 motorway  
const a22pts = Array.from({length:10},(_,i)=>{  
const lng = minLng+(maxLng-minLng)*i/9;  
return proj(37.116, lng);  
});  
const a22D = ‘M’+a22pts.map(p=>`${p.x.toFixed(1)},${p.y.toFixed(1)}`).join(‘L’);  
  
// EN125  
const en125pts = Array.from({length:10},(_,i)=>{  
const t=i/9, lng=minLng+(maxLng-minLng)*t;  
return proj(37.088+Math.sin(t*Math.PI*0.9)*0.005, lng);  
});  
const en125D = ‘M’+en125pts.map(p=>`${p.x.toFixed(1)},${p.y.toFixed(1)}`).join(‘L’);  
  
// Cities  
const cities = [  
{name:‘Albufeira’,lat:37.099,lng:-8.243},  
{name:‘Vilamoura’,lat:37.082,lng:-8.104},  
{name:‘Lagos’,    lat:37.102,lng:-8.667},  
{name:‘Portimão’, lat:37.140,lng:-8.536},  
{name:‘Loulé’,    lat:37.148,lng:-8.018},  
{name:‘Silves’,   lat:37.196,lng:-8.435},  
];  
  
const mid125 = en125pts[5];  
const midA22 = a22pts[4];  
  
return (  
<div style={{position:‘relative’,background:’#a8d4f0’,borderBottom:‘2px solid #b8ccd8’}}  
onClick={()=>setTip(null)}>  
<svg viewBox={`0 0 ${VW} ${VH}`} style={{display:‘block’,width:‘100%’}}>  
  
```  
    {/* Sea background */}  
    <rect x={0} y={0} width={VW} height={VH} fill="#a8d4f0"/>  
    {/* Sea texture */}  
    {[40,90,140,190,240].map(y=>(  
      <path key={y} d={`M0,${y} Q${VW*0.25},${y-3} ${VW*0.5},${y} Q${VW*0.75},${y+3} ${VW},${y}`}  
        fill="none" stroke="rgba(255,255,255,0.25)" strokeWidth="0.8"/>  
    ))}  
  
    {/* Land */}  
    <polygon points={landPts} fill="#f2efe9"/>  
  
    {/* Green zones */}  
    {[[0.28,0.28,52,18],[0.58,0.22,44,15],[0.14,0.38,38,13],[0.72,0.32,36,13],[0.44,0.16,30,11],[0.86,0.24,28,10]].map(([cx,cy,rx,ry],i)=>(  
      <ellipse key={i} cx={cx*VW} cy={cy*VH} rx={rx} ry={ry} fill="#d4e8c4" opacity="0.65"/>  
    ))}  
  
    {/* A22 */}  
    <path d={a22D} fill="none" stroke="#f0c040" strokeWidth="3.5" opacity="0.85"/>  
    <path d={a22D} fill="none" stroke="white" strokeWidth="1" strokeDasharray="5 4" opacity="0.6"/>  
    <rect x={midA22.x-10} y={midA22.y-8} width={20} height={11} rx={2} fill="#f0c040" opacity="0.9"/>  
    <text x={midA22.x} y={midA22.y} fontSize="7" fontWeight="800" fill="#7a5500" textAnchor="middle" dominantBaseline="middle" style={{fontFamily:'sans-serif'}}>A 22</text>  
  
    {/* EN125 */}  
    <path d={en125D} fill="none" stroke="#f8d880" strokeWidth="2.5" opacity="0.9"/>  
    <text x={mid125.x} y={mid125.y+9} fontSize="6.5" fontWeight="600" fill="#8a6a00" textAnchor="middle" opacity="0.9" style={{fontFamily:'sans-serif'}}>EN 125</text>  
  
    {/* Coastline */}  
    <path d={coastD} fill="none" stroke="#88b8d8" strokeWidth="1.8"/>  
  
    {/* City dots + labels */}  
    {cities.map(c=>{  
      const p = proj(c.lat,c.lng);  
      return (  
        <g key={c.name}>  
          <circle cx={p.x} cy={p.y} r="3" fill="#bbb" stroke="white" strokeWidth="1"/>  
          <text x={p.x+5} y={p.y+1} fontSize="8" fill="#444" fontWeight="500"  
            style={{fontFamily:'sans-serif'}}>{c.name}</text>  
        </g>  
      );  
    })}  
  
    {/* Day polylines */}  
    {DAYS.map(day=>{  
      const pts = day.stops.map(s=>proj(s.lat,s.lng));  
      if (pts.length<2) return null;  
      const active = activeDay==='all' || activeDay===day.id;  
      return (  
        <polyline key={day.id}  
          points={pts.map(p=>`${p.x.toFixed(1)},${p.y.toFixed(1)}`).join(' ')}  
          fill="none" stroke={day.color} strokeWidth="3" strokeLinecap="round"  
          opacity={active?0.95:0.07} style={{transition:'opacity 0.25s'}}/>  
      );  
    })}  
  
    {/* Numbered markers */}  
    {STOPS_FLAT.map(stop=>{  
      const p = proj(stop.lat,stop.lng);  
      const active = activeDay==='all' || activeDay===stop.dayId;  
      return (  
        <g key={stop.num} onClick={e=>{e.stopPropagation();setTip(stop);}}  
           style={{cursor:'pointer',opacity:active?1:0.08,transition:'opacity 0.25s'}}>  
          <circle cx={p.x} cy={p.y+1.5} r={13} fill="rgba(0,0,0,0.2)"/>  
          <circle cx={p.x} cy={p.y} r={13} fill={stop.color} stroke="white" strokeWidth="2.5"/>  
          <text x={p.x} y={p.y} textAnchor="middle" dominantBaseline="central"  
            fontSize="10" fontWeight="800" fill="white"  
            style={{fontFamily:'sans-serif',pointerEvents:'none'}}>  
            {stop.num}  
          </text>  
        </g>  
      );  
    })}  
  
    {/* Attribution */}  
    <text x={VW-3} y={VH-3} fontSize="6.5" fill="#666" textAnchor="end"  
      style={{fontFamily:'sans-serif'}}>Leaflet | © OpenStreetMap</text>  
  </svg>  
  
  {/* Popup tooltip */}  
  {tip && (  
    <div onClick={e=>e.stopPropagation()} style={{  
      position:'absolute', bottom:12, left:'50%', transform:'translateX(-50%)',  
      background:'white', borderRadius:12, padding:'10px 16px',  
      boxShadow:'0 6px 24px rgba(0,0,0,0.18)', border:'1px solid #dde',  
      minWidth:170, zIndex:10, fontFamily:'-apple-system,sans-serif',  
    }}>  
      <span style={{fontSize:16}}>{tip.emoji}</span>  
      <div style={{fontWeight:700,fontSize:13.5,color:'#1a3a4a',margin:'4px 0 2px'}}>{tip.name}</div>  
      <div style={{fontSize:11.5,color:'#88aabb'}}>{tip.weekday}</div>  
      <div onClick={()=>setTip(null)} style={{  
        position:'absolute',top:7,right:10,cursor:'pointer',color:'#bbb',fontSize:16,lineHeight:1  
      }}>×</div>  
    </div>  
  )}  
</div>  
```  
  
);  
}  
  
// ── App ──────────────────────────────────────────────────────────────────────  
export default function App() {  
const [view, setView] = useState(‘ov’);  
const activeDay = view===‘ov’ ? ‘all’ : Number(view);  
const currentDay = view!==‘ov’ ? DAYS.find(d=>d.id===Number(view)) : null;  
  
return (  
<div style={{fontFamily:’-apple-system,BlinkMacSystemFont,sans-serif’,background:’#f0f7fb’,minHeight:‘100vh’,color:’#1a3a4a’}}>  
  
```  
  {/* HERO */}  
  <div style={{background:'linear-gradient(160deg,#005f8a 0%,#0088bb 45%,#00aed4 100%)',padding:'40px 24px 0',textAlign:'center',position:'relative',overflow:'hidden'}}>  
    <div style={{position:'absolute',top:12,right:20,fontSize:28,opacity:0.6}}>☀️</div>  
    <div style={{position:'absolute',top:10,left:16,fontSize:26,opacity:0.5}}>🌴</div>  
    <div style={{fontSize:32,marginBottom:8}}>🇵🇹</div>  
    <div style={{fontSize:36,fontWeight:800,color:'#fff',textTransform:'uppercase',letterSpacing:'0.04em',lineHeight:1.1,textShadow:'0 2px 14px rgba(0,50,90,0.35)'}}>Voyage à<br/>Albufeira</div>  
    <div style={{color:'rgba(255,255,255,0.9)',fontSize:15,marginTop:10}}>Les filles 🌊</div>  
    <div style={{color:'#ffe066',fontSize:14,fontWeight:600,marginTop:4,marginBottom:22}}>24 mai — 31 mai 2026</div>  
    <svg viewBox="0 0 400 32" style={{display:'block',width:'100%'}}>  
      <path d="M0,18 C60,32 120,4 180,18 C240,32 300,4 360,16 C380,22 392,26 400,20 L400,32 L0,32 Z" fill="#f0f7fb"/>  
    </svg>  
  </div>  
  
  {/* MAP */}  
  <MapSVG activeDay={activeDay}/>  
  
  {/* TABS */}  
  <div style={{background:'#e4f3fb',padding:'10px 14px',overflowX:'auto',whiteSpace:'nowrap',borderBottom:'2px solid #b0d8f0',position:'sticky',top:0,zIndex:100,WebkitOverflowScrolling:'touch'}}>  
    {[{id:'ov',label:"🗺️ Vue d'ensemble"},...DAYS.map(d=>({id:String(d.id),label:d.dateLabel}))].map(tab=>(  
      <button key={tab.id} onClick={()=>setView(tab.id)} style={{  
        display:'inline-block',padding:'7px 16px',borderRadius:50,  
        border:view===tab.id?'none':'1.5px solid #88c8e8',  
        background:view===tab.id?'#0088bb':'transparent',  
        color:view===tab.id?'#fff':'#2a7a9a',  
        fontSize:13,fontWeight:600,cursor:'pointer',marginRight:8,  
        fontFamily:'inherit',boxShadow:view===tab.id?'0 2px 10px rgba(0,136,187,0.35)':'none',  
        transition:'all 0.2s',whiteSpace:'nowrap'  
      }}>{tab.label}</button>  
    ))}  
  </div>  
  
  {/* CONTENT */}  
  <div style={{padding:'0 15px 80px'}}>  
  
    {/* OVERVIEW */}  
    {view==='ov' && (  
      <div>  
        <div style={{fontSize:11,fontWeight:700,letterSpacing:'0.12em',textTransform:'uppercase',color:'#5a9ab5',margin:'20px 0 11px',display:'flex',alignItems:'center',gap:6}}>  
          📅 PROGRAMME JOUR PAR JOUR  
        </div>  
        {DAYS.map(day=>(  
          <div key={day.id} onClick={()=>setView(String(day.id))} style={{  
            background:'#fff',borderRadius:14,padding:'13px 15px',marginBottom:9,  
            display:'flex',alignItems:'center',gap:13,cursor:'pointer',  
            boxShadow:'0 1px 6px rgba(0,100,150,0.1)',border:'1px solid rgba(0,150,200,0.08)',  
          }}>  
            <div style={{width:4,height:36,borderRadius:4,background:day.color,flexShrink:0}}/>  
            <div style={{fontSize:14,fontWeight:700,minWidth:52,color:day.color}}>{day.dateLabel}</div>  
            <div style={{flex:1,fontSize:14,fontWeight:500}}>{day.location}</div>  
            <div style={{background:'#e6f7ff',color:'#0077aa',borderRadius:20,padding:'4px 12px',fontSize:13,fontWeight:700,whiteSpace:'nowrap'}}>{day.budget.total} €</div>  
          </div>  
        ))}  
      </div>  
    )}  
  
    {/* DAY VIEW */}  
    {currentDay && (  
      <div>  
        <div style={{display:'flex',alignItems:'center',gap:13,margin:'18px 0 14px'}}>  
          <div style={{width:52,height:52,borderRadius:14,background:currentDay.color,display:'flex',flexDirection:'column',alignItems:'center',justifyContent:'center',color:'#fff',fontWeight:700,lineHeight:1.1,flexShrink:0,boxShadow:'0 3px 12px rgba(0,0,0,0.18)'}}>  
            <span style={{fontSize:22}}>{currentDay.dayNum}</span>  
            <span style={{fontSize:9.5,textTransform:'uppercase',letterSpacing:'0.05em',opacity:0.85}}>{currentDay.month}</span>  
          </div>  
          <div>  
            <div style={{fontSize:18,fontWeight:700,color:'#1a3a4a'}}>{currentDay.weekday}</div>  
            <div style={{fontSize:12.5,color:'#5a9ab5',marginTop:2}}>📍 {currentDay.location}</div>  
          </div>  
        </div>  
  
        {currentDay.acts.map((a,i)=>(  
          <div key={i} style={{background:'#fff',borderRadius:14,padding:'13px 14px 13px 18px',marginBottom:9,display:'flex',alignItems:'center',gap:12,boxShadow:'0 1px 5px rgba(0,100,150,0.08)',border:'1px solid rgba(0,150,200,0.07)',position:'relative',overflow:'hidden'}}>  
            <div style={{position:'absolute',left:0,top:0,bottom:0,width:4,background:a.c,borderRadius:'2px 0 0 2px'}}/>  
            <div style={{fontSize:22,width:34,textAlign:'center',flexShrink:0}}>{a.i}</div>  
            <div style={{flex:1,minWidth:0}}>  
              <div style={{fontSize:14,fontWeight:600,color:'#1a3a4a',lineHeight:1.3}}>{a.n}</div>  
              {a.d&&<div style={{fontSize:12,color:'#7aacbe',marginTop:2}}>{a.d}</div>}  
            </div>  
            {a.p&&<div style={{background:'#e6f7ff',color:'#0077aa',borderRadius:20,padding:'4px 10px',fontSize:12,fontWeight:700,whiteSpace:'nowrap',flexShrink:0}}>{a.p}</div>}  
          </div>  
        ))}  
  
        {currentDay.tip&&(  
          <div style={{background:'#fffbea',border:'1.5px solid #ffe066',borderRadius:12,padding:'10px 13px',marginBottom:9,fontSize:13,color:'#7a5e00',display:'flex',alignItems:'flex-start',gap:8}}>  
            <span style={{flexShrink:0}}>💡</span><span>{currentDay.tip}</span>  
          </div>  
        )}  
  
        <div style={{background:'linear-gradient(135deg,#003d5c,#005f8a)',borderRadius:16,padding:'16px 17px 13px',marginTop:14,color:'#fff',boxShadow:'0 4px 18px rgba(0,70,120,0.28)'}}>  
          <div style={{fontSize:11,fontWeight:700,letterSpacing:'0.14em',textTransform:'uppercase',color:'#55ddff',marginBottom:13}}>💸 DÉPENSES DU JOUR</div>  
          {currentDay.budget.lines.map((l,i)=>(  
            <div key={i} style={{display:'flex',justifyContent:'space-between',fontSize:14,color:'rgba(255,255,255,0.72)',marginBottom:7}}>  
              <span>{l.l}</span><span>{l.a}</span>  
            </div>  
          ))}  
          <div style={{display:'flex',justifyContent:'space-between',fontSize:15,fontWeight:700,color:'#ffe066',borderTop:'1px solid rgba(255,255,255,0.15)',marginTop:9,paddingTop:9}}>  
            <span>Total estimé / pers</span><span>{currentDay.budget.total} €</span>  
          </div>  
        </div>  
      </div>  
    )}  
  </div>  
</div>  
```  
  
);  
}  
