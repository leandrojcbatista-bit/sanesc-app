[index.html](https://github.com/user-attachments/files/26867194/index.html)
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0"/>
<title>Sanesc</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@400;500;600&family=IBM+Plex+Mono:wght@400;500&display=swap');
:root{--blue-dark:#0D3B6E;--blue-main:#1565C0;--blue-light:#E3F2FD;--green:#2E7D32;--green-light:#E8F5E9;--orange:#E65100;--orange-light:#FFF3E0;--red:#B71C1C;--red-light:#FFEBEE;--gray-bg:#F5F7FA;--gray-border:#DDE3EC;--gray-text:#455A64;--gray-muted:#90A4AE;--text-primary:#1A2332;--radius:10px;--radius-sm:6px;}
*{box-sizing:border-box;margin:0;padding:0;}
body{font-family:'IBM Plex Sans',sans-serif;background:#fff;color:var(--text-primary);max-width:430px;margin:0 auto;min-height:100vh;display:flex;flex-direction:column;}
.header{background:var(--blue-dark);color:white;padding:16px 18px 12px;display:flex;align-items:center;gap:12px;}
.header-icon{width:38px;height:38px;background:rgba(255,255,255,0.15);border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:18px;flex-shrink:0;}
.header h1{font-size:15px;font-weight:600;}.header p{font-size:10px;opacity:.6;margin-top:2px;font-family:'IBM Plex Mono',monospace;}
.tabs{display:flex;background:white;border-bottom:1px solid var(--gray-border);position:sticky;top:0;z-index:10;}
.tab{flex:1;padding:9px 2px 8px;font-size:10px;font-weight:500;text-align:center;cursor:pointer;color:var(--gray-muted);border-bottom:2px solid transparent;transition:all .18s;}
.tab.active{color:var(--blue-main);border-bottom-color:var(--blue-main);}
.tab-icon{font-size:17px;display:block;margin-bottom:2px;}
.content{flex:1;overflow-y:auto;background:var(--gray-bg);}
.section{display:none;padding:16px;}.section.active{display:block;}
.geo-strip{display:flex;align-items:center;gap:10px;background:var(--green-light);border:1px solid #A5D6A7;border-radius:var(--radius-sm);padding:10px 12px;margin-bottom:14px;}
.geo-dot{width:9px;height:9px;border-radius:50%;background:var(--green);flex-shrink:0;animation:blink 1.6s infinite;}
@keyframes blink{0%,100%{opacity:1;}50%{opacity:.3;}}
.geo-strip strong{font-size:12px;font-weight:600;color:var(--green);display:block;}
.geo-strip span{font-size:11px;color:#388E3C;font-family:'IBM Plex Mono',monospace;}
.field-group{margin-bottom:13px;}
.field-group label{font-size:11px;font-weight:600;color:var(--gray-text);display:block;margin-bottom:4px;text-transform:uppercase;letter-spacing:.05em;}
.field-group input,.field-group select,.field-group textarea{width:100%;padding:10px 12px;border:1px solid var(--gray-border);border-radius:var(--radius-sm);font-size:14px;font-family:'IBM Plex Sans',sans-serif;background:white;color:var(--text-primary);outline:none;}
.field-group input:focus,.field-group select:focus,.field-group textarea:focus{border-color:var(--blue-main);box-shadow:0 0 0 3px rgba(21,101,192,.12);}
.field-group textarea{resize:vertical;min-height:68px;line-height:1.5;}
.row2{display:grid;grid-template-columns:1fr 1fr;gap:10px;}
.card{background:white;border:1px solid var(--gray-border);border-radius:var(--radius);padding:14px 16px;margin-bottom:14px;}
.card-title{font-size:11px;font-weight:600;color:var(--gray-text);text-transform:uppercase;letter-spacing:.05em;margin-bottom:10px;}
.stat-row{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-bottom:14px;}
.stat-box{background:white;border:1px solid var(--gray-border);border-radius:var(--radius-sm);padding:10px;text-align:center;}
.stat-box .val{font-size:17px;font-weight:600;font-family:'IBM Plex Mono',monospace;}
.stat-box .lbl{font-size:10px;color:var(--gray-muted);margin-top:2px;}
.nivel-bar{height:12px;background:var(--gray-bg);border-radius:20px;overflow:hidden;border:1px solid var(--gray-border);}
.nivel-fill{height:100%;border-radius:20px;transition:width .5s,background .5s;}
.nivel-label{display:flex;justify-content:space-between;font-size:11px;color:var(--gray-muted);margin-top:5px;}
.lucio-card{background:white;border:2px solid var(--blue-main);border-radius:var(--radius);padding:14px 16px;margin-bottom:14px;display:none;}
.lucio-card .card-title{color:var(--blue-main);}
.lucio-total{background:#E3F2FD;border-radius:8px;padding:10px 12px;margin-top:4px;}
.lucio-total-label{font-size:11px;font-weight:600;color:var(--blue-dark);text-transform:uppercase;letter-spacing:.05em;margin-bottom:4px;}
.lucio-total-val{font-size:22px;font-weight:600;color:var(--blue-main);font-family:'IBM Plex Mono',monospace;}
.photo-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-bottom:10px;}
.photo-slot{aspect-ratio:1;border-radius:var(--radius-sm);border:1.5px dashed var(--gray-border);display:flex;flex-direction:column;align-items:center;justify-content:center;font-size:10px;color:var(--gray-muted);cursor:pointer;background:white;position:relative;overflow:hidden;transition:all .15s;}
.photo-slot:active{transform:scale(.97);}
.photo-slot .slot-icon{font-size:20px;margin-bottom:3px;}
.photo-slot.filled{border-style:solid;border-color:#A5D6A7;}
.photo-slot img{width:100%;height:100%;object-fit:cover;}
.geo-badge{position:absolute;bottom:3px;left:3px;background:rgba(21,101,192,.85);color:white;font-size:8px;padding:2px 5px;border-radius:3px;font-family:'IBM Plex Mono',monospace;}
.foto-count{font-size:12px;color:var(--gray-text);margin-bottom:14px;}
.btn{display:block;width:100%;padding:12px;border:none;border-radius:var(--radius-sm);font-size:14px;font-weight:600;font-family:'IBM Plex Sans',sans-serif;text-align:center;cursor:pointer;transition:all .15s;}
.btn-primary{background:var(--blue-main);color:white;}
.btn-success{background:var(--green);color:white;}
.btn-success:disabled{background:#9E9E9E;cursor:not-allowed;}
.btn-outline{background:white;color:var(--text-primary);border:1px solid var(--gray-border);margin-bottom:12px;}
.check-item{display:flex;align-items:center;gap:10px;padding:6px 0;}
.check-item input[type=checkbox]{width:16px;height:16px;accent-color:var(--blue-main);}
.check-item span{font-size:13px;}
.oc-item{padding:11px 0;border-bottom:1px solid var(--gray-border);}
.oc-item:last-child{border-bottom:none;}
.oc-header{display:flex;align-items:center;gap:7px;margin-bottom:4px;flex-wrap:wrap;}
.badge{display:inline-block;font-size:11px;font-weight:600;padding:2px 8px;border-radius:20px;}
.badge-vazamento{background:var(--blue-light);color:var(--blue-dark);}
.badge-nivel{background:var(--orange-light);color:var(--orange);}
.badge-falha{background:#FCE4EC;color:#880E4F;}
.badge-outro{background:#F3E5F5;color:#4A148C;}
.badge-grav{font-size:10px;padding:2px 7px;background:var(--gray-bg);color:var(--gray-text);border:1px solid var(--gray-border);border-radius:20px;}
.oc-hora{font-size:11px;color:var(--gray-muted);font-family:'IBM Plex Mono',monospace;margin-left:auto;}
.oc-desc{font-size:12px;color:var(--gray-text);line-height:1.5;}
.send-status{border-radius:var(--radius-sm);padding:14px;text-align:center;font-size:13px;font-weight:500;margin-top:12px;display:none;line-height:1.5;}
.send-status.sending{background:var(--blue-light);color:var(--blue-dark);display:block;}
.send-status.success{background:var(--green-light);border:1px solid #A5D6A7;color:var(--green);display:block;}
.send-status.error{background:var(--red-light);border:1px solid #EF9A9A;color:var(--red);display:block;}
.divider{height:1px;background:var(--gray-border);margin:4px 0 14px;}
.section-label{font-size:11px;font-weight:600;color:var(--gray-muted);text-transform:uppercase;letter-spacing:.05em;margin-bottom:10px;}
</style>
</head>
<body>
<div class="header">
  <div class="header-icon">💧</div>
  <div><h1>Sanesc</h1><p>TELIMETRIASANESC — REGISTRO DE CAMPO</p></div>
</div>
<div class="tabs">
  <div class="tab active" onclick="showTab('identificacao')"><span class="tab-icon">🏭</span>ESTAÇÃO</div>
  <div class="tab" onclick="showTab('capacidade')"><span class="tab-icon">💧</span>CAPAC.</div>
  <div class="tab" onclick="showTab('fotos')"><span class="tab-icon">📷</span>FOTOS</div>
  <div class="tab" onclick="showTab('ocorrencias')"><span class="tab-icon">⚠️</span>OCORR.</div>
</div>
<div class="content">

<!-- ABA 1: ESTAÇÃO -->
<div class="section active" id="sec-identificacao">
  <div class="geo-strip"><div class="geo-dot"></div><div><strong id="geo-label">Obtendo localização...</strong><span id="geo-coords">Aguardando GPS</span></div></div>
  <div class="field-group"><label>Código da Estação</label><input type="text" id="cod-estacao" placeholder="Ex: EAR-042"/></div>
  <div class="field-group"><label>Nome / Localidade</label>
    <select id="nome-localidade" onchange="verificarLucioRosa()">
      <option value="">Selecione...</option>
      <optgroup label="Setor Lúcio Rosa">
        <option>Reservatório 1</option><option>Reservatório 2</option><option>Reservatório 3</option>
        <option>Reservatório 4</option><option>Reservatório 5</option><option>Uirapuru</option>
      </optgroup>
      <optgroup label="Setor Paraíso"><option>Paraíso 1</option><option>Paraíso 2</option></optgroup>
      <optgroup label="Setor Matinha/Oliveira">
        <option>Matinha Caixa Maior</option><option>Matinha Caixa Menor</option>
        <option>Matinha Taça</option><option>Oliveira</option>
      </optgroup>
      <optgroup label="Setor Buriti/Ecológico"><option>Buriti</option><option>Ecológico Araguaia</option></optgroup>
      <optgroup label="Setor Nova Goiânia/Morro">
        <option>Morro</option><option>Nova Goiânia</option><option>Concreto</option>
      </optgroup>
      <optgroup label="Engopa / Dois Irmãos / Sozinha">
        <option>Engopa</option>
        <option>Dois Irmãos</option>
        <option>Sozinha</option>
      </optgroup>
      <optgroup label="Outras Localidades">
        <option>Top do Parque</option><option>Capri</option><option>Jaepel</option>
        <option>Laranjeiras</option><option>Ravena</option><option>FGR</option>
        <option>Quebec</option><option>Valeria Perilo</option><option>Galvão</option>
        <option>Ingá</option><option>Trajano</option><option>10 Milhões</option>
      </optgroup>
    </select>
  </div>
  <div class="field-group"><label>Tipo de Reservatório</label>
    <select id="tipo-reservatorio">
      <option value="">Selecione...</option>
      <option>Cisterna subterrânea</option><option>Reservatório elevado</option>
      <option>Caixa d'água superficial</option><option>Reservatório de concreto</option><option>Outro</option>
    </select>
  </div>
  <div class="row2">
    <div class="field-group"><label>Responsável</label><input type="text" id="responsavel" placeholder="Nome do técnico"/></div>
    <div class="field-group"><label>Matrícula</label><input type="text" id="matricula" placeholder="Ex: 00842"/></div>
  </div>
  <div class="field-group"><label>Data da Vistoria</label><input type="date" id="data-vistoria"/></div>
  <div class="field-group"><label>Observações gerais</label><textarea id="observacoes" placeholder="Condições de acesso..."></textarea></div>
  <button class="btn btn-primary" onclick="showTab('capacidade')">Próximo: Capacidade →</button>
</div>

<!-- ABA 2: CAPACIDADE -->
<div class="section" id="sec-capacidade">
  <div class="stat-row">
    <div class="stat-box"><div class="val" id="stat-cap">—</div><div class="lbl">Total (m³)</div></div>
    <div class="stat-box"><div class="val" id="stat-vol">—</div><div class="lbl">Atual (m³)</div></div>
    <div class="stat-box"><div class="val" id="stat-pct">—</div><div class="lbl">Nível %</div></div>
  </div>
  <div class="card">
    <div class="card-title">Volume de armazenamento</div>
    <div class="row2" style="margin-bottom:12px;">
      <div class="field-group" style="margin:0;"><label>Capacidade total (m³)</label><input type="number" id="cap-total" placeholder="Ex: 500" oninput="atualizarStats()"/></div>
      <div class="field-group" style="margin:0;"><label>Volume atual (m³)</label><input type="number" id="vol-atual" placeholder="Ex: 350" oninput="atualizarStats()"/></div>
    </div>
    <div class="nivel-bar"><div class="nivel-fill" id="nivel-fill" style="width:0%;background:#4CAF50;"></div></div>
    <div class="nivel-label"><span id="nivel-desc">Informe os volumes acima</span><span id="nivel-pct-label"></span></div>
  </div>

  <!-- PAINEL LÚCIO ROSA -->
  <div class="lucio-card" id="painel-lucio">
    <div class="card-title">📊 Volumes — Estação Lúcio Rosa</div>
    <div class="field-group" style="margin-bottom:10px;">
      <label>Volume medido na estação Lúcio Rosa (m³)</label>
      <input type="number" id="vol-medido-lucio" placeholder="Ex: 320" oninput="calcularTotalLucio()"/>
    </div>
    <div class="field-group" style="margin-bottom:10px;">
      <label>Volume medido Engopa (m³)</label>
      <input type="number" id="vol-engopa" placeholder="Ex: 100" oninput="calcularTotalLucio()"/>
    </div>
    <div class="field-group" style="margin-bottom:10px;">
      <label>Volume medido Dois Irmãos (m³)</label>
      <input type="number" id="vol-dois-irmaos" placeholder="Ex: 80" oninput="calcularTotalLucio()"/>
    </div>
    <div class="lucio-total">
      <div class="lucio-total-label">Volume total medido (Lúcio Rosa + Engopa + Dois Irmãos)</div>
      <div class="lucio-total-val" id="vol-total-medido">— m³</div>
    </div>
  </div>

  <!-- PAINEL ENGOPA -->
  <div class="lucio-card" id="painel-engopa">
    <div class="card-title">📊 Volume — Estação Engopa</div>
    <div class="field-group" style="margin-bottom:10px;">
      <label>Volume medido Engopa (m³)</label>
      <input type="number" id="vol-engopa-solo" placeholder="Ex: 100" oninput="calcularEngopa()"/>
    </div>
    <div class="lucio-total">
      <div class="lucio-total-label">Volume registrado</div>
      <div class="lucio-total-val" id="vol-total-engopa">— m³</div>
    </div>
  </div>

  <!-- PAINEL DOIS IRMÃOS -->
  <div class="lucio-card" id="painel-dois-irmaos">
    <div class="card-title">📊 Volume — Estação Dois Irmãos</div>
    <div class="field-group" style="margin-bottom:10px;">
      <label>Volume medido Dois Irmãos (m³)</label>
      <input type="number" id="vol-dois-irmaos-solo" placeholder="Ex: 80" oninput="calcularDoisIrmaos()"/>
    </div>
    <div class="lucio-total">
      <div class="lucio-total-label">Volume registrado</div>
      <div class="lucio-total-val" id="vol-total-dois-irmaos">— m³</div>
    </div>
  </div>

  <!-- PAINEL SOZINHA -->
  <div class="lucio-card" id="painel-sozinha">
    <div class="card-title">📊 Volume — Estação Sozinha</div>
    <div class="field-group" style="margin-bottom:10px;">
      <label>Volume medido Sozinha (m³)</label>
      <input type="number" id="vol-sozinha-solo" placeholder="Ex: 60" oninput="calcularSozinha()"/>
    </div>
    <div class="lucio-total">
      <div class="lucio-total-label">Volume registrado</div>
      <div class="lucio-total-val" id="vol-total-sozinha">— m³</div>
    </div>
  </div>

  <div class="field-group"><label>Qualidade da água</label>
    <select id="qualidade-agua">
      <option value="">Selecione...</option>
      <option>Boa — dentro dos padrões</option><option>Regular — monitoramento necessário</option>
      <option>Ruim — análise laboratorial indicada</option><option>Crítica — interdição necessária</option>
    </select>
  </div>
  <div class="row2">
    <div class="field-group"><label>Pressão (mca)</label><input type="number" id="pressao" placeholder="Ex: 15"/></div>
    <div class="field-group"><label>Vazão (L/s)</label><input type="number" id="vazao" placeholder="Ex: 4.5"/></div>
  </div>
  <div class="row2">
    <div class="field-group"><label>Última manutenção</label><input type="date" id="ultima-manutencao"/></div>
    <div class="field-group"><label>Próxima manutenção</label><input type="date" id="prox-manutencao"/></div>
  </div>
  <button class="btn btn-primary" onclick="showTab('fotos')">Próximo: Fotos →</button>
</div>

<!-- ABA 3: FOTOS -->
<div class="section" id="sec-fotos">
  <div class="geo-strip"><div class="geo-dot"></div><div><strong>Fotos com geolocalização ativa</strong><span id="geo-foto-coords">Coordenadas serão anexadas</span></div></div>
  <div class="section-label">Toque para abrir a câmera</div>
  <input type="file" id="cam0" accept="image/*" capture="environment" style="display:none" onchange="carregarFoto(0,'Vista geral',this)"/>
  <input type="file" id="cam1" accept="image/*" capture="environment" style="display:none" onchange="carregarFoto(1,'Medidor',this)"/>
  <input type="file" id="cam2" accept="image/*" capture="environment" style="display:none" onchange="carregarFoto(2,'Tampa',this)"/>
  <input type="file" id="cam3" accept="image/*" capture="environment" style="display:none" onchange="carregarFoto(3,'Estrutura',this)"/>
  <input type="file" id="cam4" accept="image/*" capture="environment" style="display:none" onchange="carregarFoto(4,'Entorno',this)"/>
  <input type="file" id="cam5" accept="image/*" capture="environment" style="display:none" onchange="carregarFoto(5,'Adicional',this)"/>
  <div class="photo-grid" id="photo-grid">
    <div class="photo-slot" onclick="document.getElementById('cam0').click()"><span class="slot-icon">📷</span><span>Vista geral</span></div>
    <div class="photo-slot" onclick="document.getElementById('cam1').click()"><span class="slot-icon">📷</span><span>Medidor</span></div>
    <div class="photo-slot" onclick="document.getElementById('cam2').click()"><span class="slot-icon">📷</span><span>Tampa</span></div>
    <div class="photo-slot" onclick="document.getElementById('cam3').click()"><span class="slot-icon">📷</span><span>Estrutura</span></div>
    <div class="photo-slot" onclick="document.getElementById('cam4').click()"><span class="slot-icon">📷</span><span>Entorno</span></div>
    <div class="photo-slot" onclick="document.getElementById('cam5').click()"><span class="slot-icon">➕</span><span>Adicionar</span></div>
  </div>
  <div class="foto-count" id="fotos-status">0 fotos adicionadas</div>
  <button class="btn btn-primary" onclick="showTab('ocorrencias')">Próximo: Ocorrências →</button>
</div>

<!-- ABA 4: OCORRÊNCIAS -->
<div class="section" id="sec-ocorrencias">
  <div class="card">
    <div class="card-title">Nova ocorrência</div>
    <div class="field-group" style="margin-bottom:10px;"><label>Tipo</label>
      <select id="tipo-ocorrencia">
        <option value="">Selecione...</option>
        <option value="vazamento">Vazamento</option>
        <option value="nivel">Nível crítico de água</option>
        <option value="falha">Falha de equipamento</option>
        <option value="outro">Outro</option>
      </select>
    </div>
    <div class="field-group" style="margin-bottom:10px;"><label>Gravidade</label>
      <select id="gravidade">
        <option value="">Selecione...</option>
        <option>Baixa — monitorar</option><option>Média — manutenção programada</option>
        <option>Alta — ação imediata</option><option>Crítica — emergência</option>
      </select>
    </div>
    <div class="field-group" style="margin-bottom:10px;"><label>Descrição</label>
      <textarea id="desc-ocorrencia" placeholder="Descreva o problema..." style="min-height:60px;"></textarea>
    </div>
    <div class="card-title" style="margin-bottom:6px;">Ações necessárias</div>
    <label class="check-item"><input type="checkbox" id="acao1"/><span>Reparo emergencial</span></label>
    <label class="check-item"><input type="checkbox" id="acao2"/><span>Notificar supervisão</span></label>
    <label class="check-item"><input type="checkbox" id="acao3"/><span>Interdição parcial</span></label>
    <label class="check-item"><input type="checkbox" id="acao4"/><span>Coleta de amostras</span></label>
  </div>
  <button class="btn btn-outline" onclick="adicionarOcorrencia()">+ Registrar ocorrência</button>
  <div id="lista-ocorrencias"></div>
  <div class="divider"></div>
  <button class="btn btn-success" id="btn-salvar" onclick="enviarParaSheets()">☁️ Salvar e enviar ao Google Sheets</button>
  <div class="send-status" id="send-status"></div>
</div>

</div>
<script>
const SCRIPT_URL = "https://script.google.com/macros/s/AKfycbzaXrDRUsFvExPy7SETsABOnOQK3WTBZy6BveQDoPpLSlG1mXUvP8aRu9xStL2-z8CgeA/exec";
const geoData = {lat:"", lng:""};
const fotosAdicionadas = {};
const ocorrenciasLista = [];
let nivelPctVal = "";

document.getElementById("data-vistoria").value = new Date().toISOString().split("T")[0];

if (navigator.geolocation) {
  navigator.geolocation.getCurrentPosition(
    pos => {
      geoData.lat = pos.coords.latitude.toFixed(6);
      geoData.lng = pos.coords.longitude.toFixed(6);
      document.getElementById("geo-label").textContent = "Localização obtida ✓";
      document.getElementById("geo-coords").textContent = geoData.lat + ", " + geoData.lng;
      document.getElementById("geo-foto-coords").textContent = geoData.lat + ", " + geoData.lng;
    },
    err => {
      document.getElementById("geo-label").textContent = "GPS indisponível";
      document.getElementById("geo-coords").textContent = "Permissão negada";
    },
    {enableHighAccuracy:true, timeout:10000, maximumAge:0}
  );
}

const tabNames = ["identificacao","capacidade","fotos","ocorrencias"];
function showTab(name) {
  document.querySelectorAll(".tab").forEach((t,i) => t.classList.toggle("active", tabNames[i]===name));
  document.querySelectorAll(".section").forEach(s => s.classList.remove("active"));
  document.getElementById("sec-"+name).classList.add("active");
}

function verificarLucioRosa() {
  const setorLucio = ["Reservatório 1","Reservatório 2","Reservatório 3","Reservatório 4","Reservatório 5","Uirapuru"];
  const val = document.getElementById("nome-localidade").value;
  document.getElementById("painel-lucio").style.display = setorLucio.includes(val) ? "block" : "none";
  document.getElementById("painel-engopa").style.display = val === "Engopa" ? "block" : "none";
  document.getElementById("painel-dois-irmaos").style.display = val === "Dois Irmãos" ? "block" : "none";
  document.getElementById("painel-sozinha").style.display = val === "Sozinha" ? "block" : "none";
}

function calcularTotalLucio() {
  const lucio = parseFloat(document.getElementById("vol-medido-lucio").value) || 0;
  const engopa = parseFloat(document.getElementById("vol-engopa").value) || 0;
  const doisirmaos = parseFloat(document.getElementById("vol-dois-irmaos").value) || 0;
  const total = lucio + engopa + doisirmaos;
  document.getElementById("vol-total-medido").textContent = total > 0 ? total.toLocaleString("pt-BR") + " m³" : "— m³";
}

function calcularEngopa() {
  const v = parseFloat(document.getElementById("vol-engopa-solo").value) || 0;
  document.getElementById("vol-total-engopa").textContent = v > 0 ? v.toLocaleString("pt-BR") + " m³" : "— m³";
}

function calcularDoisIrmaos() {
  const v = parseFloat(document.getElementById("vol-dois-irmaos-solo").value) || 0;
  document.getElementById("vol-total-dois-irmaos").textContent = v > 0 ? v.toLocaleString("pt-BR") + " m³" : "— m³";
}

function calcularSozinha() {
  const v = parseFloat(document.getElementById("vol-sozinha-solo").value) || 0;
  document.getElementById("vol-total-sozinha").textContent = v > 0 ? v.toLocaleString("pt-BR") + " m³" : "— m³";
}

function atualizarStats() {
  const cap = parseFloat(document.getElementById("cap-total").value) || 0;
  const vol = parseFloat(document.getElementById("vol-atual").value) || 0;
  document.getElementById("stat-cap").textContent = cap ? cap.toLocaleString("pt-BR") : "—";
  document.getElementById("stat-vol").textContent = vol ? vol.toLocaleString("pt-BR") : "—";
  if (cap > 0) {
    const pct = Math.min(100, Math.round((vol/cap)*100));
    nivelPctVal = String(pct);
    document.getElementById("stat-pct").textContent = pct + "%";
    const fill = document.getElementById("nivel-fill");
    fill.style.width = pct + "%";
    fill.style.background = pct < 20 ? "#F44336" : pct < 50 ? "#FF9800" : "#4CAF50";
    document.getElementById("nivel-desc").textContent = pct < 20 ? "⚠ Nível crítico" : pct < 50 ? "Nível baixo" : "Nível adequado";
    document.getElementById("nivel-pct-label").textContent = pct + "%";
  }
}

function carregarFoto(idx, label, input) {
  const file = input.files[0];
  if (!file) return;
  const reader = new FileReader();
  reader.onload = function(e) {
    const slot = document.getElementById("photo-grid").children[idx];
    slot.innerHTML = '<img src="'+e.target.result+'" style="width:100%;height:100%;object-fit:cover;"/><div class="geo-badge">'+(geoData.lat||"--")+","+(geoData.lng||"--")+"</div>";
    slot.classList.add("filled");
    // Guardar base64, tipo e label para envio ao Drive
    fotosAdicionadas[idx] = {
      label: label,
      lat: geoData.lat,
      lng: geoData.lng,
      base64: e.target.result.split(",")[1],
      mimeType: file.type,
      nome: label.replace(/\s+/g,"-") + "-" + Date.now() + ".jpg"
    };
    document.getElementById("fotos-status").textContent = Object.keys(fotosAdicionadas).length + " foto(s) tirada(s) com localização";
  };
  reader.readAsDataURL(file);
}

function adicionarOcorrencia() {
  const tipo = document.getElementById("tipo-ocorrencia").value;
  const grav = document.getElementById("gravidade").value;
  const desc = document.getElementById("desc-ocorrencia").value.trim();
  if (!tipo) { alert("Selecione o tipo de ocorrência."); return; }
  const acoes = [];
  if (document.getElementById("acao1").checked) acoes.push("Reparo emergencial");
  if (document.getElementById("acao2").checked) acoes.push("Notificar supervisão");
  if (document.getElementById("acao3").checked) acoes.push("Interdição parcial");
  if (document.getElementById("acao4").checked) acoes.push("Coleta de amostras");
  const now = new Date();
  const hora = now.getHours().toString().padStart(2,"0")+":"+now.getMinutes().toString().padStart(2,"0");
  ocorrenciasLista.push({tipo,grav,desc,acoes,hora});
  const badgeMap = {vazamento:"badge-vazamento",nivel:"badge-nivel",falha:"badge-falha",outro:"badge-outro"};
  const labelMap = {vazamento:"Vazamento",nivel:"Nível crítico",falha:"Falha de equip.",outro:"Outro"};
  const div = document.createElement("div");
  div.className = "oc-item";
  div.innerHTML = '<div class="oc-header"><span class="badge '+badgeMap[tipo]+'">'+labelMap[tipo]+'</span>'+(grav?'<span class="badge-grav">'+grav.split("—")[0].trim()+'</span>':'')+'<span class="oc-hora">'+hora+'</span></div><div class="oc-desc">'+(desc||"Sem descrição.")+(acoes.length?'<br><em style="font-size:11px;color:#90A4AE;">Ações: '+acoes.join(", ")+"</em>":"")+"</div>";
  document.getElementById("lista-ocorrencias").appendChild(div);
  document.getElementById("tipo-ocorrencia").value = "";
  document.getElementById("gravidade").value = "";
  document.getElementById("desc-ocorrencia").value = "";
  ["acao1","acao2","acao3","acao4"].forEach(id => document.getElementById(id).checked = false);
}

function enviarParaSheets() {
  const btn = document.getElementById("btn-salvar");
  const status = document.getElementById("send-status");
  btn.disabled = true;
  status.className = "send-status sending";
  status.textContent = "⏳ Enviando dados...";

  const ocTexto = ocorrenciasLista.map(o => "["+o.hora+"] "+o.tipo.toUpperCase()+": "+(o.desc||"Sem desc.")).join(" | ");
  const lucio = parseFloat(document.getElementById("vol-medido-lucio").value) || 0;
  const engopa = parseFloat(document.getElementById("vol-engopa").value) || 0;
  const totalLucio = (lucio + engopa) > 0 ? String(lucio + engopa) : "";

  const params = new URLSearchParams({
    acao: "salvar",
    codEstacao:      document.getElementById("cod-estacao").value.trim(),
    nomeLocalidade:  document.getElementById("nome-localidade").value.trim(),
    tipoReservatorio:document.getElementById("tipo-reservatorio").value.trim(),
    responsavel:     document.getElementById("responsavel").value.trim(),
    matricula:       document.getElementById("matricula").value.trim(),
    dataVistoria:    document.getElementById("data-vistoria").value,
    latitude:        geoData.lat,
    longitude:       geoData.lng,
    capacidadeTotal: document.getElementById("cap-total").value || "",
    volumeAtual:     document.getElementById("vol-atual").value || "",
    nivelPct:        nivelPctVal ? nivelPctVal+"%" : "",
    qualidadeAgua:   document.getElementById("qualidade-agua").value,
    pressao:         document.getElementById("pressao").value || "",
    vazao:           document.getElementById("vazao").value || "",
    ultimaManutencao:document.getElementById("ultima-manutencao").value,
    proxManutencao:  document.getElementById("prox-manutencao").value,
    qtdFotos:        Object.keys(fotosAdicionadas).length,
    ocorrencias:     ocTexto,
    observacoes:     document.getElementById("observacoes").value.trim(),
    volMedidoLucio:  document.getElementById("vol-medido-lucio").value || "",
    volEngopaSolo:   document.getElementById("vol-engopa-solo").value || "",
    volDoisIrmaos:   document.getElementById("vol-dois-irmaos-solo").value || "",
    volSozinha:      document.getElementById("vol-sozinha-solo").value || "",
    volDoisIrmaosLucio: document.getElementById("vol-dois-irmaos").value || "",
    volEngopa:       document.getElementById("vol-engopa").value || "",
    volTotalMedido:  totalLucio
  });

  const qtdFotos = Object.keys(fotosAdicionadas).length;

  // Enviar dados via GET
  const url = SCRIPT_URL + "?" + params.toString();
  fetch(url, {method: "GET", mode: "no-cors"})
    .then(() => {
      status.className = "send-status success";
      status.innerHTML = "✅ Registro salvo na planilha!" + (qtdFotos > 0 ? "<br><span style=\"font-size:12px;font-weight:400;\">" + qtdFotos + " foto(s) registrada(s)</span>" : "");
      setTimeout(() => resetarApp(), 2500);
      btn.disabled = false;
    })
    .catch(err => {
      status.className = "send-status error";
      status.innerHTML = "❌ Erro: " + err.message;
      btn.disabled = false;
    });
}

function resetarApp() {
  ["cod-estacao","nome-localidade","tipo-reservatorio","responsavel","matricula","observacoes",
   "cap-total","vol-atual","qualidade-agua","pressao","vazao","ultima-manutencao","prox-manutencao",
   "tipo-ocorrencia","gravidade","desc-ocorrencia","vol-medido-lucio","vol-engopa","vol-dois-irmaos","vol-engopa-solo","vol-dois-irmaos-solo","vol-sozinha-solo"
  ].forEach(id => { const el=document.getElementById(id); if(el) el.value=""; });
  ["acao1","acao2","acao3","acao4"].forEach(id => { const el=document.getElementById(id); if(el) el.checked=false; });
  document.getElementById("stat-cap").textContent = "—";
  document.getElementById("stat-vol").textContent = "—";
  document.getElementById("stat-pct").textContent = "—";
  document.getElementById("nivel-fill").style.width = "0%";
  document.getElementById("nivel-desc").textContent = "Informe os volumes acima";
  document.getElementById("nivel-pct-label").textContent = "";
  document.getElementById("vol-total-medido").textContent = "— m³";
  document.getElementById("painel-lucio").style.display = "none";
  document.getElementById("painel-engopa").style.display = "none";
  document.getElementById("painel-dois-irmaos").style.display = "none";
  document.getElementById("vol-total-engopa").textContent = "— m³";
  document.getElementById("vol-total-dois-irmaos").textContent = "— m³";
  document.getElementById("painel-sozinha").style.display = "none";
  document.getElementById("vol-total-sozinha").textContent = "— m³";
  nivelPctVal = "";
  const slots = document.getElementById("photo-grid").children;
  const labels = ["Vista geral","Medidor","Tampa","Estrutura","Entorno","Adicionar"];
  const icons = ["📷","📷","📷","📷","📷","➕"];
  for (let i=0; i<slots.length; i++) {
    slots[i].innerHTML = '<span class="slot-icon">'+icons[i]+'</span><span>'+labels[i]+'</span>';
    slots[i].classList.remove("filled");
    const cam = document.getElementById("cam"+i);
    if (cam) cam.value = "";
  }
  Object.keys(fotosAdicionadas).forEach(k => delete fotosAdicionadas[k]);
  document.getElementById("fotos-status").textContent = "0 fotos adicionadas";
  ocorrenciasLista.length = 0;
  document.getElementById("lista-ocorrencias").innerHTML = "";
  document.getElementById("send-status").className = "send-status";
  document.getElementById("data-vistoria").value = new Date().toISOString().split("T")[0];
  showTab("identificacao");
}
</script>
</body>
</html>
