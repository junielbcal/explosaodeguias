<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Explosão de Prompts — O Arsenal Secreto do ChatGPT</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
*,*::before,*::after{margin:0;padding:0;box-sizing:border-box}

:root{
  --azul:#00c8e0;
  --azul-dim:#0099aa;
  --preto:#070709;
  --c1:#0e0e10;
  --c2:#161618;
  --c3:#222226;
  --c4:#2e2e34;
  --branco:#f0f0f0;
  --cinza:#888;
  --vermelho:#e63946;
  --verde-check:#22c55e;
}

html{scroll-behavior:smooth}
body{
  background:var(--preto);
  color:var(--branco);
  font-family:'DM Sans',sans-serif;
  font-size:16px;
  line-height:1.6;
  overflow-x:hidden;
}

/* ── UTIL ── */
.azul{color:var(--azul)}
.bold{font-weight:600}
.upper{text-transform:uppercase;letter-spacing:.08em}
.center{text-align:center}

/* ── BTN PRINCIPAL ── */
.btn-cta{
  display:block;
  width:100%;
  max-width:520px;
  margin:0 auto;
  background:linear-gradient(135deg,#0099c8,var(--azul));
  color:#000;
  font-family:'DM Sans',sans-serif;
  font-size:1rem;
  font-weight:700;
  letter-spacing:.06em;
  text-transform:uppercase;
  padding:20px 32px;
  border-radius:10px;
  text-decoration:none;
  text-align:center;
  border:none;
  cursor:pointer;
  box-shadow:0 0 40px rgba(0,200,224,.25);
  transition:box-shadow .2s,transform .15s;
}
.btn-cta:hover{box-shadow:0 0 60px rgba(0,200,224,.4);transform:translateY(-2px)}

/* ── SECTION WRAPPER ── */
.sec{padding:72px 24px}
.sec-inner{max-width:640px;margin:0 auto}
.sec-inner-wide{max-width:780px;margin:0 auto}

/* ════════════════════════════
   HERO
════════════════════════════ */
.hero{
  min-height:100vh;
  display:flex;
  flex-direction:column;
  align-items:center;
  justify-content:flex-end;
  padding:0 24px 56px;
  position:relative;
  overflow:hidden;
  background:radial-gradient(ellipse at 50% 20%, #0a1a2e 0%, var(--preto) 65%);
}

/* grade digital de fundo */
.hero::before{
  content:'';
  position:absolute;inset:0;
  background-image:
    linear-gradient(rgba(0,200,224,.06) 1px, transparent 1px),
    linear-gradient(90deg, rgba(0,200,224,.06) 1px, transparent 1px);
  background-size:48px 48px;
  pointer-events:none;
}

/* glow central */
.hero::after{
  content:'';
  position:absolute;
  top:5%;left:50%;transform:translateX(-50%);
  width:500px;height:500px;
  background:radial-gradient(circle,rgba(0,200,224,.12) 0%,transparent 70%);
  border-radius:50%;
  pointer-events:none;
}

.hero-logo{
  position:relative;z-index:2;
  font-family:'Bebas Neue',sans-serif;
  font-size:1.1rem;
  letter-spacing:.3em;
  color:var(--azul);
  margin-bottom:48px;
  display:flex;align-items:center;gap:10px;
  margin-top:40px;
}
.hero-logo::before,.hero-logo::after{content:'';flex:1;height:1px;background:rgba(0,200,224,.3)}

/* avatar / personagem */
.hero-avatar{
  position:relative;z-index:2;
  width:220px;height:220px;
  border-radius:50%;
  border:2px solid rgba(0,200,224,.4);
  box-shadow:0 0 60px rgba(0,200,224,.2);
  background:linear-gradient(160deg,#0a1825,#050507);
  display:flex;align-items:center;justify-content:center;
  font-size:80px;
  margin:0 auto 40px;
  overflow:hidden;
}

/* ícones laterais do herói */
.hero-icons{
  position:absolute;left:8%;top:50%;transform:translateY(-50%);
  display:flex;flex-direction:column;gap:12px;
  z-index:2;
}
@media(max-width:600px){.hero-icons{display:none}}
.hero-icon-box{
  width:52px;height:52px;
  background:rgba(255,255,255,.06);
  border:1px solid rgba(255,255,255,.1);
  border-radius:12px;
  display:flex;align-items:center;justify-content:center;
  font-size:22px;
}

.hero-content{
  position:relative;z-index:2;
  text-align:center;
  max-width:600px;
  margin:0 auto;
}

.hero-badge{
  display:inline-block;
  background:rgba(0,200,224,.1);
  border:1px solid rgba(0,200,224,.3);
  color:var(--azul);
  font-size:11px;font-weight:700;
  letter-spacing:.14em;text-transform:uppercase;
  padding:6px 16px;border-radius:100px;
  margin-bottom:20px;
}

.hero-h1{
  font-family:'Bebas Neue',sans-serif;
  font-size:clamp(2.2rem,8vw,4rem);
  letter-spacing:.05em;
  line-height:1.05;
  margin-bottom:8px;
}
.hero-h1 .azul{color:var(--azul)}

.hero-sub{
  font-size:15px;color:#999;
  max-width:480px;margin:12px auto 32px;
  line-height:1.7;
}

/* ════════════════════════════
   MAQUINA DE VENDAS
════════════════════════════ */
.maquina{
  background:var(--c1);
  border-top:1px solid var(--c3);
  border-bottom:1px solid var(--c3);
  padding:80px 24px;
  text-align:center;
}
.maquina h2{
  font-family:'Bebas Neue',sans-serif;
  font-size:clamp(1.8rem,5vw,3rem);
  letter-spacing:.04em;
  line-height:1.15;
  margin-bottom:8px;
}
.maquina-sub{
  font-size:13px;color:#666;
  letter-spacing:.06em;text-transform:uppercase;
  margin-bottom:48px;
}

/* mockup produto */
.produto-mockup{
  background:var(--c2);
  border:1px solid var(--c3);
  border-radius:16px;
  padding:28px;
  max-width:560px;
  margin:0 auto 32px;
  text-align:left;
}
.mockup-logo{
  font-family:'Bebas Neue',sans-serif;
  font-size:1.4rem;
  letter-spacing:.2em;
  color:var(--azul);
  margin-bottom:20px;
  display:flex;align-items:center;gap:8px;
}
.mockup-logo .dot{
  width:16px;height:16px;
  background:var(--azul);
  clip-path:polygon(50% 0%,100% 50%,50% 100%,0% 50%);
}
.cat-grid{
  display:grid;grid-template-columns:1fr 1fr;
  gap:8px;margin-top:16px;
}
.cat-item{
  background:var(--c3);
  border-radius:8px;padding:10px 14px;
  display:flex;align-items:center;gap:10px;
  font-size:13px;font-weight:600;color:var(--branco);
}
.cat-item .cat-icon{
  width:28px;height:28px;
  background:var(--c4);border-radius:6px;
  display:flex;align-items:center;justify-content:center;
  font-size:14px;flex-shrink:0;
}

/* ════════════════════════════
   1H → 1 MINUTO
════════════════════════════ */
.tempo{
  padding:80px 24px;
  text-align:center;
  background:var(--preto);
}
.tempo h2{
  font-family:'Bebas Neue',sans-serif;
  font-size:clamp(1.8rem,5vw,2.8rem);
  letter-spacing:.04em;
  line-height:1.2;
  margin-bottom:8px;
}
.tempo-sub{
  color:var(--azul);font-size:15px;font-weight:600;
  margin-bottom:8px;
}
.tempo-desc{color:#666;font-size:14px;max-width:480px;margin:0 auto 48px;line-height:1.7}

.funcoes-list{
  display:flex;flex-direction:column;gap:12px;
  max-width:500px;margin:0 auto;
}
.funcao-item{
  background:var(--c2);
  border:1px solid var(--c3);
  border-radius:10px;
  padding:18px 20px;
  display:flex;align-items:flex-start;gap:16px;
  text-align:left;
}
.funcao-icon-box{
  width:44px;height:44px;
  background:var(--c3);border-radius:10px;
  display:flex;align-items:center;justify-content:center;
  font-size:20px;flex-shrink:0;
}
.funcao-titulo{
  font-weight:700;font-size:15px;
  text-transform:uppercase;letter-spacing:.06em;
  margin-bottom:4px;color:var(--branco);
}
.funcao-desc{font-size:13px;color:#777;line-height:1.5}

/* ════════════════════════════
   COMO FUNCIONA
════════════════════════════ */
.como{
  background:var(--c1);
  border-top:1px solid var(--c3);
  padding:80px 24px;
  text-align:center;
}
.ctrlc{
  display:inline-flex;flex-direction:column;gap:16px;
  margin:32px auto;
}
.ctrl-row{
  display:flex;align-items:center;gap:10px;justify-content:center;
}
.ctrl-key{
  display:flex;align-items:center;justify-content:center;
  width:64px;height:64px;
  background:var(--c2);
  border:2px solid var(--c4);
  border-radius:10px;
  font-family:'Bebas Neue',sans-serif;
  font-size:1.5rem;letter-spacing:.08em;
  color:var(--branco);
  box-shadow:0 4px 0 var(--c4);
}
.ctrl-key.azul-key{
  border-color:var(--azul);
  color:var(--azul);
  box-shadow:0 4px 0 var(--azul-dim);
}
.plus-sign{font-size:1.5rem;color:#444}

.como-titulo{
  font-family:'Bebas Neue',sans-serif;
  font-size:clamp(1.8rem,5vw,2.6rem);
  letter-spacing:.04em;
  margin-bottom:12px;
}
.como-sub{color:#666;font-size:15px;max-width:480px;margin:0 auto 8px}
.como-azul{color:var(--azul);font-weight:700;font-size:15px;margin-bottom:40px}

/* ════════════════════════════
   DEPOIMENTOS
════════════════════════════ */
.depos{
  padding:80px 24px;
  background:var(--preto);
}
.depos-label{
  text-align:center;
  background:var(--c2);
  border:1px solid var(--c3);
  border-radius:8px;
  padding:12px 24px;
  display:flex;align-items:center;justify-content:center;gap:10px;
  max-width:340px;margin:0 auto 48px;
  font-weight:700;font-size:14px;
  color:var(--azul);
}

.depos-grid{
  display:flex;flex-direction:column;gap:16px;
  max-width:560px;margin:0 auto;
}
.depo-card{
  background:var(--c2);
  border:1px solid var(--c3);
  border-radius:14px;
  padding:20px;
}
.depo-msg{
  font-size:14px;color:#ccc;line-height:1.7;
  background:#1a1a1e;
  border-radius:10px;
  padding:14px 16px;
  margin-bottom:8px;
}
.depo-meta{font-size:11px;color:#555;text-align:right;margin-top:4px}
.depo-stat{
  background:var(--c3);
  border-radius:10px;
  padding:14px 16px;
  margin-bottom:8px;
  text-align:center;
}
.depo-stat-num{
  font-family:'Bebas Neue',sans-serif;
  font-size:2rem;color:var(--azul);letter-spacing:.04em;
}
.depo-stat-label{font-size:12px;color:#888}
.depo-stat-growth{font-size:11px;color:var(--verde-check);margin-top:2px}

/* ════════════════════════════
   POR DENTRO DO PRODUTO
════════════════════════════ */
.dentro{
  background:var(--c1);
  border-top:1px solid var(--c3);
  padding:80px 24px;
  text-align:center;
}
.dentro-label{
  background:var(--c2);
  border:1px solid var(--c3);
  border-radius:8px;
  padding:12px 24px;
  display:inline-flex;align-items:center;gap:10px;
  font-weight:700;font-size:14px;
  margin-bottom:32px;
}
.dentro h2{
  font-family:'Bebas Neue',sans-serif;
  font-size:clamp(1.6rem,4vw,2.4rem);
  letter-spacing:.04em;
  margin-bottom:8px;
}
.dentro-sub{color:var(--azul);font-size:14px;font-weight:600;margin-bottom:40px}

/* grade de prompts nomes */
.prompts-names{
  display:grid;
  grid-template-columns:repeat(auto-fill,minmax(200px,1fr));
  gap:8px;
  max-width:700px;margin:0 auto 40px;
  text-align:left;
}
.prompt-name-item{
  background:var(--c2);
  border:1px solid var(--c3);
  border-radius:8px;
  padding:10px 14px;
  font-size:13px;color:#aaa;
  display:flex;align-items:center;gap:8px;
}
.prompt-name-item::before{content:'→';color:var(--azul);font-weight:700;flex-shrink:0}

/* prompts detalhados */
.prompts-detail{
  display:flex;flex-direction:column;gap:12px;
  max-width:560px;margin:0 auto;text-align:left;
}
.prompt-detail-card{
  background:var(--c2);
  border:1px solid var(--c3);
  border-radius:12px;
  padding:20px;
}
.pd-titulo{
  font-weight:700;font-size:15px;color:var(--branco);
  margin-bottom:6px;
}
.pd-titulo span{color:var(--azul)}
.pd-sep{height:1px;background:var(--c3);margin:10px 0}
.pd-desc{font-size:13px;color:#777;line-height:1.6}

/* ════════════════════════════
   PARA QUEM É
════════════════════════════ */
.paraquem{
  padding:80px 24px;
  background:var(--preto);
  text-align:center;
}
.paraquem h2{
  font-family:'Bebas Neue',sans-serif;
  font-size:clamp(1.6rem,4vw,2.4rem);
  letter-spacing:.04em;
  margin-bottom:40px;
}

.paraquem-list{
  display:flex;flex-direction:column;gap:12px;
  max-width:520px;margin:0 auto;text-align:left;
}
.pq-item{
  background:var(--c2);
  border:1px solid var(--c3);
  border-radius:12px;
  padding:20px;
  display:flex;align-items:flex-start;gap:16px;
}
.pq-num{
  font-family:'Bebas Neue',sans-serif;
  font-size:1.8rem;color:var(--azul);
  line-height:1;flex-shrink:0;width:28px;
}
.pq-titulo{font-weight:700;font-size:15px;text-transform:uppercase;letter-spacing:.06em;color:var(--branco);margin-bottom:6px}
.pq-desc{font-size:13px;color:#777;line-height:1.6}
.pq-desc span{color:var(--azul);font-weight:600}

/* ════════════════════════════
   SEM / COM
════════════════════════════ */
.semcom{
  background:var(--c1);
  border-top:1px solid var(--c3);
  padding:80px 24px;
}
.semcom-inner{max-width:520px;margin:0 auto}

.sc-titulo{
  font-family:'Bebas Neue',sans-serif;
  font-size:clamp(1.6rem,4vw,2.4rem);
  letter-spacing:.04em;
  margin-bottom:24px;
}
.sc-titulo.sem{color:var(--vermelho)}
.sc-titulo.com{color:var(--verde-check);margin-top:48px}

.sc-list{list-style:none;display:flex;flex-direction:column;gap:0}
.sc-item{
  display:flex;align-items:center;gap:16px;
  padding:14px 0;
  border-bottom:1px solid var(--c3);
  font-size:14px;color:#888;
}
.sc-item:last-child{border-bottom:none}
.sc-box{
  width:28px;height:28px;border-radius:6px;
  display:flex;align-items:center;justify-content:center;
  flex-shrink:0;font-size:14px;
}
.sc-box.x{background:rgba(230,57,70,.12);border:1px solid rgba(230,57,70,.3);color:var(--vermelho)}
.sc-box.ok{background:rgba(34,197,94,.12);border:1px solid rgba(34,197,94,.3);color:var(--verde-check)}
.sc-item.ok-item{color:#ccc}

/* ════════════════════════════
   OFERTA
════════════════════════════ */
.oferta{
  padding:80px 24px;
  background:var(--preto);
  text-align:center;
}
.oferta-badge{
  display:inline-flex;align-items:center;gap:8px;
  background:rgba(0,200,224,.08);
  border:1px solid rgba(0,200,224,.25);
  border-radius:8px;
  padding:12px 24px;
  font-weight:700;font-size:13px;
  color:var(--azul);
  letter-spacing:.06em;text-transform:uppercase;
  margin-bottom:40px;
}
.oferta-box{
  background:var(--c2);
  border:1px solid var(--c3);
  border-radius:20px;
  padding:36px 28px;
  max-width:520px;margin:0 auto;
}
.oferta-produto-logo{
  font-family:'Bebas Neue',sans-serif;
  font-size:1.8rem;letter-spacing:.2em;
  color:var(--azul);
  display:flex;align-items:center;justify-content:center;gap:10px;
  margin-bottom:24px;
}

.oferta-mockup-cats{
  display:flex;flex-direction:column;gap:8px;
  margin-bottom:28px;
}
.ocat{
  background:var(--c3);
  border-radius:8px;padding:10px 16px;
  display:flex;align-items:center;justify-content:space-between;
  font-size:13px;font-weight:700;
  text-transform:uppercase;letter-spacing:.07em;
}
.ocat .ocico{font-size:16px}

.preco-de{
  font-size:18px;color:#555;
  text-decoration:line-through;
  margin-bottom:4px;
}
.preco-por{
  font-family:'Bebas Neue',sans-serif;
  font-size:4rem;letter-spacing:.04em;
  color:var(--branco);line-height:1;
  margin-bottom:6px;
}
.preco-label{font-size:12px;color:#555;margin-bottom:28px;letter-spacing:.06em;text-transform:uppercase}

/* ════════════════════════════
   GARANTIA
════════════════════════════ */
.garantia{
  background:var(--c1);
  border-top:1px solid var(--c3);
  padding:80px 24px;
  text-align:center;
}
.garantia-badge{
  display:inline-block;
  background:rgba(34,197,94,.1);
  border:1px solid rgba(34,197,94,.3);
  color:var(--verde-check);
  font-size:11px;font-weight:700;
  letter-spacing:.14em;text-transform:uppercase;
  padding:6px 18px;border-radius:100px;
  margin-bottom:28px;
}
.garantia-shield{
  width:120px;height:120px;
  background:linear-gradient(160deg,#0e2040,#0a0a12);
  border:2px solid var(--azul);
  border-radius:50%;
  display:flex;align-items:center;justify-content:center;
  margin:0 auto 28px;
  box-shadow:0 0 40px rgba(0,200,224,.2);
  flex-direction:column;gap:0;
}
.shield-num{
  font-family:'Bebas Neue',sans-serif;
  font-size:2.4rem;letter-spacing:.04em;
  color:var(--azul);line-height:1;
}
.shield-label{font-size:10px;color:var(--azul);letter-spacing:.1em;text-transform:uppercase}

.garantia h2{
  font-family:'Bebas Neue',sans-serif;
  font-size:clamp(1.6rem,4vw,2.2rem);
  letter-spacing:.04em;
  margin-bottom:16px;
}
.garantia-desc{
  font-size:14px;color:#888;
  max-width:480px;margin:0 auto 32px;
  line-height:1.75;
}
.garantia-desc strong{color:var(--branco)}

.garantia-items{
  display:flex;flex-direction:column;gap:8px;
  max-width:400px;margin:0 auto 40px;text-align:left;
}
.garantia-item{
  display:flex;align-items:center;gap:12px;
  font-size:14px;font-weight:600;color:var(--branco);
}
.garantia-item::before{
  content:'▶';color:var(--verde-check);font-size:10px;flex-shrink:0;
}

/* ════════════════════════════
   FOOTER
════════════════════════════ */
footer{
  padding:32px 24px;
  border-top:1px solid var(--c3);
  text-align:center;
  font-size:12px;color:#444;
}
footer span{color:var(--azul)}

/* ════════════════════════════
   RESPONSIVE
════════════════════════════ */
@media(max-width:500px){
  .cat-grid{grid-template-columns:1fr}
  .prompts-names{grid-template-columns:1fr}
}
</style>
</head>
<body>

<!-- ══════════════════════════════════
     HERO
══════════════════════════════════ -->
<section class="hero">

  <!-- ícones laterais -->
  <div class="hero-icons">
    <div class="hero-icon-box">📈</div>
    <div class="hero-icon-box">🤖</div>
    <div class="hero-icon-box">📱</div>
  </div>

  <!-- logo topo -->
  <div class="hero-logo">EXPLOSÃO DE PROMPTS</div>

  <!-- avatar central -->
  <div class="hero-avatar">🕵️</div>

  <!-- headline -->
  <div class="hero-content">
    <div class="hero-badge">⚡ O Arsenal Secreto do ChatGPT</div>
    <h1 class="hero-h1">
      O IMPULSO PARA VOCÊ<br>
      <span class="azul">CRIAR CONTEÚDO E VIRALIZAR</span><br>
      NO INSTAGRAM COM IA
    </h1>
    <p class="hero-sub">
      Tenha acesso ao kit completo de prompts avançados para ChatGPT que vai fazer o papel de um Social Media e uma equipe de Marketing — por uma fração do preço.
    </p>
    <a href="https://pay.kiwify.com.br/SJVeFkp" class="btn-cta">
      QUERO IMPULSIONAR MEU INSTAGRAM
    </a>
  </div>
</section>


<!-- ══════════════════════════════════
     MÁQUINA DE VENDAS
══════════════════════════════════ -->
<section class="maquina">
  <div class="sec-inner">
    <h2>TRANSFORME SEU INSTAGRAM EM UMA<br><span class="azul">MÁQUINA DE VENDAS AUTOMÁTICA</span><br>COM CHATGPT</h2>
    <p class="maquina-sub">[Sem precisar virar expert em marketing]</p>

    <div class="produto-mockup">
      <div class="mockup-logo">
        <div class="dot"></div>
        EXPLOSÃO DE PROMPTS
      </div>
      <p style="font-size:13px;color:#666;margin-bottom:16px">Kit completo de prompts para impulsionar seu Instagram</p>
      <div class="cat-grid">
        <div class="cat-item"><div class="cat-icon">✍️</div>Criação de Conteúdo</div>
        <div class="cat-item"><div class="cat-icon">📊</div>Estratégia e Alcance</div>
        <div class="cat-item"><div class="cat-icon">💰</div>Vendas e Conversão</div>
        <div class="cat-item"><div class="cat-icon">⚡</div>Gestão e Produtividade</div>
      </div>
    </div>

    <a href="https://pay.kiwify.com.br/SJVeFkp" class="btn-cta">IMPULSIONAR MEU INSTAGRAM</a>
  </div>
</section>


<!-- ══════════════════════════════════
     1H → 1 MINUTO
══════════════════════════════════ -->
<section class="tempo">
  <div class="sec-inner">
    <h2>SE ANTES VOCÊ LEVAVA 1H PARA<br>ESCREVER UM POST,<br><span class="azul">AGORA VOCÊ PRECISA DE APENAS 1 MINUTO!</span></h2>
    <p class="tempo-sub">Só precisa copiar, colar e ver seu perfil crescer.</p>
    <p class="tempo-desc">Chega de perder horas criando conteúdo. Agora você tem uma equipe completa de social media e marketing em um único kit. Com o Explosão de Prompts você:</p>

    <div class="funcoes-list">
      <div class="funcao-item">
        <div class="funcao-icon-box">▶️</div>
        <div>
          <div class="funcao-titulo">Cria Reels</div>
          <div class="funcao-desc">Roteiros de vídeos curtos que viralizam, desde dicas valiosas adaptadas ao seu nicho.</div>
        </div>
      </div>
      <div class="funcao-item">
        <div class="funcao-icon-box">🗂️</div>
        <div>
          <div class="funcao-titulo">Cria Carrosséis</div>
          <div class="funcao-desc">Educativos até vendedores: transforme qualquer ideia em slides que seu público vai salvar e compartilhar.</div>
        </div>
      </div>
      <div class="funcao-item">
        <div class="funcao-icon-box">➕</div>
        <div>
          <div class="funcao-titulo">Cria Stories</div>
          <div class="funcao-desc">Stories que prendem a atenção nos primeiros segundos e mantém seu público assistindo até o final.</div>
        </div>
      </div>
      <div class="funcao-item">
        <div class="funcao-icon-box">💲</div>
        <div>
          <div class="funcao-titulo">Cria Ofertas</div>
          <div class="funcao-desc">Textos de venda irresistíveis que transformam seguidores em clientes, com gatilhos mentais.</div>
        </div>
      </div>
      <div class="funcao-item">
        <div class="funcao-icon-box">📖</div>
        <div>
          <div class="funcao-titulo">Cria E-books</div>
          <div class="funcao-desc">E-books profissionais para usar como isca digital ou produto com estrutura que agrega valor real.</div>
        </div>
      </div>
      <div class="funcao-item">
        <div class="funcao-icon-box">📝</div>
        <div>
          <div class="funcao-titulo">Cria Legendas</div>
          <div class="funcao-desc">Textos envolventes que fazem seu público parar, ler até o final e interagir com seu conteúdo.</div>
        </div>
      </div>
      <div class="funcao-item">
        <div class="funcao-icon-box">👤</div>
        <div>
          <div class="funcao-titulo">Cria Bio Otimizada</div>
          <div class="funcao-desc">Bio que converte visitantes em seguidores e seguidores em clientes em segundos.</div>
        </div>
      </div>
    </div>
  </div>
</section>


<!-- ══════════════════════════════════
     COMO FUNCIONA
══════════════════════════════════ -->
<section class="como">
  <div class="sec-inner">
    <div class="como-titulo">COMO FUNCIONA?</div>
    <div class="ctrlc">
      <div class="ctrl-row">
        <div class="ctrl-key">CTRL</div>
        <span class="plus-sign">+</span>
        <div class="ctrl-key azul-key">C</div>
      </div>
      <div class="ctrl-row">
        <div class="ctrl-key">CTRL</div>
        <span class="plus-sign">+</span>
        <div class="ctrl-key azul-key">V</div>
      </div>
    </div>
    <p class="como-sub">Copie e cole todo meu arsenal de prompts que me faz</p>
    <p class="como-azul">viralizar e vender no Instagram!</p>
    <p style="font-size:14px;color:#666;max-width:400px;margin:0 auto">Cada prompt foi desenvolvido para uma tarefa específica. Você copia, personaliza com seu nicho e usa. Simples assim.</p>
  </div>
</section>


<!-- ══════════════════════════════════
     RESULTADOS / DEPOIMENTOS
══════════════════════════════════ -->
<section class="depos">
  <div class="sec-inner">
    <div class="depos-label">
      💬 RESULTADOS DOS PRIMEIROS USUÁRIOS
    </div>

    <div class="depos-grid">

      <div class="depo-card">
        <div class="depo-msg">
          "Cara, não tem noção do que esse prompt da bio fez pelo meu perfil. Tô ganhando seguidor por minuto. Como que um simples prompt do ChatGPT faz isso??? 🤯"
        </div>
        <div class="depo-meta">01:47</div>
        <div class="depo-msg" style="margin-top:8px">
          "Faz 3 dias só e aquele prompt de sequência de stories com venda já tá dando resultado. Fechei 2 contratos. Muito obrigado!"
        </div>
        <div class="depo-meta">11:02</div>
      </div>

      <div class="depo-card">
        <div class="depo-stat">
          <div class="depo-stat-num">765</div>
          <div class="depo-stat-label">Seguidores novos</div>
          <div class="depo-stat-growth">+2.150% em 10 dias</div>
        </div>
        <div class="depo-msg">
          "Criei um perfil do zero faz 8 dias e já ganhei isso de seguidor. Usando os prompts pra ter ideia de conteúdo e automatizar tudo. Já fiz 5 vendas do meu ebook só em 8 dias! 🚀"
        </div>
        <div class="depo-meta">15:45</div>
      </div>

      <div class="depo-card">
        <div class="depo-msg">
          "Adorei os prompts! É perfeito pra quem não sabe por onde começar. Ficou fácil de criar conteúdo de valor."
        </div>
        <div class="depo-msg" style="margin-top:8px">
          "Os prompts são práticos e personalizáveis pro meu nicho. Vou usar muito e vender muito com certeza kkkk"
        </div>
        <div class="depo-msg" style="margin-top:8px">
          "Cara, você não tem noção do que isso já fez por mim e como o ChatGPT ficou configurado e me entrega tudo que preciso. Muito obrigado!"
        </div>
      </div>

    </div>

    <div style="margin-top:36px">
      <a href="https://pay.kiwify.com.br/SJVeFkp" class="btn-cta">QUERO TER RESULTADOS</a>
    </div>
  </div>
</section>


<!-- ══════════════════════════════════
     POR DENTRO DO PRODUTO
══════════════════════════════════ -->
<section class="dentro">
  <div class="sec-inner-wide">
    <div class="dentro-label">
      <span class="dot" style="width:12px;height:12px;background:var(--azul);clip-path:polygon(50% 0%,100% 50%,50% 100%,0% 50%);display:inline-block"></span>
      POR DENTRO DO EXPLOSÃO DE PROMPTS
    </div>

    <h2>ISSO É SÓ <span class="azul">10% DOS PROMPTS</span><br>QUE VOCÊ VAI RECEBER NO KIT</h2>
    <p class="dentro-sub">↓ PROMPTS HIPER-ESPECÍFICOS PARA CRIAÇÃO DE CONTEÚDO ↓</p>

    <!-- grade de nomes -->
    <div class="prompts-names">
      <div class="prompt-name-item">Máquina de Conteúdo Semanal</div>
      <div class="prompt-name-item">Analista de Engajamento 360°</div>
      <div class="prompt-name-item">Bio que Vende em 3 Segundos</div>
      <div class="prompt-name-item">Otimizador de SEO Visual</div>
      <div class="prompt-name-item">Fábrica de Ideias com IA</div>
      <div class="prompt-name-item">Guerrilha de SEO para Reels</div>
      <div class="prompt-name-item">Carrossel de Lançamento</div>
      <div class="prompt-name-item">Reels Otimizados para Alcance</div>
      <div class="prompt-name-item">Método de Afiliação Premium</div>
      <div class="prompt-name-item">Arquiteto de Cursos Digitais</div>
      <div class="prompt-name-item">Criador de Conteúdo Atemporal</div>
      <div class="prompt-name-item">Necromante de Posts Antigos</div>
      <div class="prompt-name-item">DNA Visual da Marca</div>
      <div class="prompt-name-item">Série de Stories em 5 Atos</div>
      <div class="prompt-name-item">Desafio de Afiliados em 7 Dias</div>
      <div class="prompt-name-item">Quebra-Cabeça de Conteúdo Viral</div>
      <div class="prompt-name-item">Neurocopywriter que Engaja</div>
      <div class="prompt-name-item">Fluxo de DM que Parece Humano</div>
      <div class="prompt-name-item">Estratégia de Parceiras Virais</div>
      <div class="prompt-name-item">Dominador do Algoritmo do IG</div>
    </div>

    <!-- prompts detalhados -->
    <div class="prompts-detail">

      <div class="prompt-detail-card">
        <div class="pd-titulo">Prompt para o ChatGPT <span>analisar seu perfil no Instagram</span> por completo.</div>
        <div class="pd-sep"></div>
        <div class="pd-desc">Descubra exatamente o que está impedindo seu perfil de bombar e corrija em minutos — sem precisar de consultoria cara.</div>
      </div>

      <div class="prompt-detail-card">
        <div class="pd-titulo">Prompt que transforma ideias cruas em <span>carrosséis virais</span></div>
        <div class="pd-sep"></div>
        <div class="pd-desc">Converta qualquer ideia simples em um carrossel profissional que seu público vai querer salvar e compartilhar.</div>
      </div>

      <div class="prompt-detail-card">
        <div class="pd-titulo">Prompt para seus stories terem <span>5x mais alcance</span></div>
        <div class="pd-sep"></div>
        <div class="pd-desc">Dê um upgrade nos seus stories e faça mais pessoas assistirem até o fim — e clicarem no seu link.</div>
      </div>

      <div class="prompt-detail-card">
        <div class="pd-titulo">Prompt do ChatGPT para nunca mais se preocupar com <span>ideias de conteúdo</span></div>
        <div class="pd-sep"></div>
        <div class="pd-desc">Transforme 1 única ideia em 30 posts diferentes e mantenha seu feed sempre atualizado sem esgotar sua criatividade.</div>
      </div>

      <div class="prompt-detail-card">
        <div class="pd-titulo">Prompt para <span>100 ideias</span> para converter visualizações em vendas</div>
        <div class="pd-sep"></div>
        <div class="pd-desc">Desbloqueie 100 formatos de posts que fazem seu público passar de seguidor para comprador — no ritmo que você definir.</div>
      </div>

      <div class="prompt-detail-card">
        <div class="pd-titulo">Prompt do ChatGPT para gerar <span>ganchos virais ilimitados</span> no seu nicho</div>
        <div class="pd-sep"></div>
        <div class="pd-desc">Crie aberturas irresistíveis que fazem seu público parar de rolar o feed e prestar atenção em você — em qualquer formato.</div>
      </div>

      <div class="prompt-detail-card">
        <div class="pd-titulo">Prompt que cria <span>sequência de stories para vender</span></div>
        <div class="pd-sep"></div>
        <div class="pd-desc">Monte stories que guiam naturalmente seu público do 'olá' até o 'comprar agora' sem parecer forçado ou chato.</div>
      </div>

    </div>

    <div style="margin-top:40px">
      <a href="https://pay.kiwify.com.br/SJVeFkp" class="btn-cta">QUERO ACESSO AOS PROMPTS</a>
    </div>
  </div>
</section>


<!-- ══════════════════════════════════
     CADA PROMPT ESPECIALIZADO
══════════════════════════════════ -->
<section style="padding:60px 24px;background:var(--preto);text-align:center">
  <div class="sec-inner">
    <h2 style="font-family:'Bebas Neue',sans-serif;font-size:clamp(1.4rem,4vw,2rem);letter-spacing:.04em;margin-bottom:8px">CADA PROMPT ESPECIALIZADO EM<br><span class="azul">FAZER UMA TAREFA ÚNICA</span></h2>
    <p style="font-size:13px;color:#666;margin-bottom:0">Não são prompts genéricos. São comandos cirúrgicos, cada um projetado para um resultado específico e mensurável.</p>
  </div>
</section>


<!-- ══════════════════════════════════
     PARA QUEM É
══════════════════════════════════ -->
<section class="paraquem">
  <div class="sec-inner">
    <h2>PRA QUEM É O<br><span class="azul">EXPLOSÃO DE PROMPTS?</span></h2>

    <div class="paraquem-list">
      <div class="pq-item">
        <div class="pq-num">1</div>
        <div>
          <div class="pq-titulo">Criadores de Conteúdo</div>
          <div class="pq-desc">Você vai ter em mãos um arsenal completo para <span>otimizar a criação do seu Instagram</span>, aumentando seu engajamento, crescimento e vendas — sem gastar horas do seu dia.</div>
        </div>
      </div>
      <div class="pq-item">
        <div class="pq-num">2</div>
        <div>
          <div class="pq-titulo">Infoprodutores</div>
          <div class="pq-desc">Automatize a criação de conteúdo e deixe o ChatGPT ser seu Social Media enquanto você foca em <span>criar produtos e fechar vendas</span>.</div>
        </div>
      </div>
      <div class="pq-item">
        <div class="pq-num">3</div>
        <div>
          <div class="pq-titulo">Prestadores de Serviço</div>
          <div class="pq-desc">Construa uma <span>presença profissional no Instagram</span> e aumente seu engajamento com conteúdo estratégico que atrai novos clientes todos os dias.</div>
        </div>
      </div>
      <div class="pq-item">
        <div class="pq-num">4</div>
        <div>
          <div class="pq-titulo">Mentores e Coaches</div>
          <div class="pq-desc">Se posicione no Instagram através de conteúdos que geram <span>engajamento, crescimento, vendas</span> e fidelização de clientes — no piloto automático.</div>
        </div>
      </div>
      <div class="pq-item">
        <div class="pq-num">5</div>
        <div>
          <div class="pq-titulo">Consultores</div>
          <div class="pq-desc">Ao ter acesso aos prompts você vai conseguir <span>lotar sua agenda</span>, criando sequências de stories que atraem clientes em 24h ou menos.</div>
        </div>
      </div>
    </div>

    <div style="margin-top:32px">
      <a href="https://pay.kiwify.com.br/SJVeFkp" class="btn-cta">SIM, É PRA MIM!</a>
    </div>
  </div>
</section>


<!-- ══════════════════════════════════
     SEM / COM
══════════════════════════════════ -->
<section class="semcom">
  <div class="semcom-inner">

    <div class="sc-titulo sem">SEM O PROMPT<br>CLANDESTINO...</div>
    <ul class="sc-list">
      <li class="sc-item"><span class="sc-box x">✕</span>2-3 horas por dia pensando "o que postar hoje?"</li>
      <li class="sc-item"><span class="sc-box x">✕</span>Posts ruins que ninguém salva ou compartilha</li>
      <li class="sc-item"><span class="sc-box x">✕</span>Stories que ninguém assiste até o final</li>
      <li class="sc-item"><span class="sc-box x">✕</span>Bio que não converte visitantes em seguidores</li>
      <li class="sc-item"><span class="sc-box x">✕</span>Dias sem postar por falta de ideias</li>
      <li class="sc-item"><span class="sc-box x">✕</span>Crescimento lento e orgânico quase zero</li>
    </ul>

    <div class="sc-titulo com">COM O PROMPT<br>CLANDESTINO...</div>
    <ul class="sc-list">
      <li class="sc-item ok-item"><span class="sc-box ok">✓</span>30 dias de conteúdo planejado em 2 horas</li>
      <li class="sc-item ok-item"><span class="sc-box ok">✓</span>Carrosséis profissionais que viralizam</li>
      <li class="sc-item ok-item"><span class="sc-box ok">✓</span>Stories com 80% mais visualizações</li>
      <li class="sc-item ok-item"><span class="sc-box ok">✓</span>Bio otimizada que converte visitantes</li>
      <li class="sc-item ok-item"><span class="sc-box ok">✓</span>Ideias infinitas de conteúdo relevante</li>
      <li class="sc-item ok-item"><span class="sc-box ok">✓</span>Sistema de vendas automático no perfil</li>
    </ul>

  </div>
</section>


<!-- ══════════════════════════════════
     OFERTA
══════════════════════════════════ -->
<section class="oferta">
  <div class="sec-inner">
    <div class="oferta-badge">🔥 OFERTA ESPECIAL POR TEMPO LIMITADO</div>

    <div class="oferta-box">
      <div style="font-size:12px;color:#555;letter-spacing:.1em;text-transform:uppercase;margin-bottom:16px">ACESSE IMEDIATAMENTE</div>

      <div class="oferta-produto-logo">
        <div class="dot" style="width:18px;height:18px;background:var(--azul);clip-path:polygon(50% 0%,100% 50%,50% 100%,0% 50%)"></div>
        EXPLOSÃO DE PROMPTS
      </div>

      <div class="oferta-mockup-cats">
        <div class="ocat" style="color:#4ade80"><span class="ocico">✍️</span> CRIAÇÃO DE CONTEÚDO</div>
        <div class="ocat" style="color:#facc15"><span class="ocico">📊</span> ESTRATÉGIA E ALCANCE</div>
        <div class="ocat" style="color:var(--azul)"><span class="ocico">💰</span> VENDAS E CONVERSÃO</div>
        <div class="ocat" style="color:#f97316"><span class="ocico">⚡</span> GESTÃO E PRODUTIVIDADE</div>
      </div>

      <div class="preco-de">De R$ 97</div>
      <div class="preco-por">R$ <span class="azul">37</span></div>
      <div class="preco-label">Preço promocional por tempo limitado</div>

      <a href="https://pay.kiwify.com.br/SJVeFkp" class="btn-cta">
        ABRIR O EXPLOSÃO DE PROMPTS
      </a>
    </div>
  </div>
</section>


<!-- ══════════════════════════════════
     GARANTIA
══════════════════════════════════ -->
<section class="garantia">
  <div class="sec-inner">
    <div class="garantia-badge">GARANTIA INCONDICIONAL</div>

    <div class="garantia-shield">
      <div class="shield-num">7</div>
      <div class="shield-label">DIAS</div>
    </div>

    <h2>Sua satisfação ou seu<br><strong>dinheiro de volta.</strong></h2>

    <p class="garantia-desc">
      Tenho absoluta certeza de que o <strong>Explosão de Prompts</strong> vai revolucionar a forma como você cria conteúdo no Instagram usando IA. Por isso ofereço uma <strong>garantia incondicional de 7 dias.</strong> Teste os prompts, explore cada comando e veja na prática:
    </p>

    <div class="garantia-items">
      <div class="garantia-item">Gerar conteúdos 10x mais rápido</div>
      <div class="garantia-item">Aumentar seu engajamento com técnicas comprovadas</div>
      <div class="garantia-item">Economizar horas de trabalho toda semana</div>
    </div>

    <p style="font-size:13px;color:#666;max-width:420px;margin:0 auto 36px;line-height:1.7">
      Se por qualquer motivo você não sentir que o Explosão de Prompts entrega <strong style="color:var(--branco)">MUITO MAIS</strong> do que pagou, basta enviar um e-mail dentro de 7 dias pedindo o reembolso. <strong style="color:var(--branco)">Sem perguntas. Sem burocracia.</strong>
    </p>

    <a href="https://pay.kiwify.com.br/SJVeFkp" class="btn-cta">QUERO ACESSO AGORA COM GARANTIA</a>
  </div>
</section>


<!-- FOOTER -->
<footer>
  <p>© 2026 <span>Explosão de Prompts</span> · Todos os direitos reservados</p>
  <p style="margin-top:6px">@explosaodeprompts · Produto disponível na <span>Hotmart</span> · Garantia de 7 dias</p>
</footer>

</body>
</html>
