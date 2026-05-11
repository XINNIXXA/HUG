
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Lynna 🐼💗</title>
<link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700;800&family=Quicksand:wght@500;600;700&display=swap" rel="stylesheet">
<style>
:root {
  --rose: #ff6b9d;
  --magenta: #c44dff;
  --peach: #ffb3d1;
  --deep: #1a0a2e;
  --mid: #2d1155;
  --glow: rgba(255,107,157,0.6);
  --glow2: rgba(196,77,255,0.5);
}

*, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }

html, body {
  width: 100%; height: 100%;
  overflow: hidden;
  background: var(--deep);
  font-family: 'Quicksand', sans-serif;
  cursor: none;
}

#cursor {
  position: fixed;
  width: 18px; height: 18px;
  background: radial-gradient(circle, #fff 0%, var(--rose) 60%, transparent 100%);
  border-radius: 50%;
  pointer-events: none;
  z-index: 9999;
  transform: translate(-50%,-50%);
  mix-blend-mode: screen;
  transition: transform 0.08s, width 0.2s, height 0.2s;
  box-shadow: 0 0 12px 4px var(--glow);
}

#canvas {
  position: fixed;
  inset: 0;
  z-index: 0;
  pointer-events: none;
}

.bg-mesh {
  position: fixed;
  inset: 0;
  z-index: 0;
  background:
    radial-gradient(ellipse 80% 60% at 20% 20%, rgba(196,77,255,0.18) 0%, transparent 60%),
    radial-gradient(ellipse 60% 80% at 80% 80%, rgba(255,107,157,0.22) 0%, transparent 60%),
    radial-gradient(ellipse 50% 50% at 50% 50%, rgba(45,17,85,0.8) 0%, var(--deep) 100%);
  animation: meshDrift 12s ease-in-out infinite alternate;
}
@keyframes meshDrift {
  from { filter: hue-rotate(0deg); }
  to   { filter: hue-rotate(25deg); }
}

.stage {
  position: relative; z-index: 10;
  width: 100%; height: 100vh;
  display: flex; flex-direction: column;
  align-items: center; justify-content: center;
  gap: 0;
}

.title-block {
  text-align: center;
  animation: slideDown 1s cubic-bezier(0.22,1,0.36,1) both;
  margin-bottom: 2px;
}
@keyframes slideDown {
  from { opacity:0; transform: translateY(-40px) scale(0.9); }
  to   { opacity:1; transform: translateY(0) scale(1); }
}

.title-for {
  font-family: 'Quicksand', sans-serif;
  font-size: clamp(0.75rem, 2vw, 0.95rem);
  color: var(--peach);
  letter-spacing: 5px;
  text-transform: uppercase;
  opacity: 0.75;
  margin-bottom: 4px;
}

.title-name {
  font-family: 'Dancing Script', cursive;
  font-size: clamp(3.2rem, 10vw, 6.5rem);
  font-weight: 800;
  line-height: 1;
  background: linear-gradient(135deg, #fff 0%, var(--peach) 35%, var(--rose) 65%, var(--magenta) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  filter: drop-shadow(0 0 30px rgba(255,107,157,0.7));
  animation: shimmer 4s ease-in-out infinite alternate;
}
@keyframes shimmer {
  from { filter: drop-shadow(0 0 20px rgba(255,107,157,0.5)) drop-shadow(0 0 60px rgba(196,77,255,0.2)); }
  to   { filter: drop-shadow(0 0 40px rgba(255,107,157,0.9)) drop-shadow(0 0 80px rgba(196,77,255,0.5)); }
}

.love-line {
  font-family: 'Dancing Script', cursive;
  font-size: clamp(1.1rem, 3.5vw, 1.6rem);
  color: var(--peach);
  animation: slideDown 1s 0.25s cubic-bezier(0.22,1,0.36,1) both;
  margin-bottom: 18px;
  display: flex; align-items: center; gap: 8px;
}
.love-heart {
  display: inline-block;
  animation: throb 1.2s ease-in-out infinite;
  color: var(--rose);
}
@keyframes throb {
  0%,100% { transform: scale(1); }
  40%      { transform: scale(1.4); }
  70%      { transform: scale(1.15); }
}

.card {
  position: relative;
  background: rgba(255,255,255,0.04);
  backdrop-filter: blur(18px);
  border: 1px solid rgba(255,180,220,0.18);
  border-radius: 36px;
  padding: 28px 32px 20px;
  display: flex; flex-direction: column; align-items: center;
  box-shadow:
    0 0 0 1px rgba(255,107,157,0.08),
    0 8px 40px rgba(0,0,0,0.4),
    0 0 80px rgba(255,107,157,0.08) inset;
  animation: slideDown 1s 0.1s cubic-bezier(0.22,1,0.36,1) both;
  transition: box-shadow 0.5s;
}
.card.hugging {
  box-shadow:
    0 0 0 2px rgba(255,107,157,0.4),
    0 8px 60px rgba(0,0,0,0.5),
    0 0 120px rgba(255,107,157,0.25) inset;
}

.card::before, .card::after {
  content: '✦';
  position: absolute;
  font-size: 1rem;
  color: rgba(255,180,220,0.35);
  animation: spinStar 8s linear infinite;
}
.card::before { top: 14px; left: 18px; }
.card::after  { bottom: 14px; right: 18px; animation-direction: reverse; }
@keyframes spinStar { to { transform: rotate(360deg); } }

.panda-outer {
  position: relative;
  cursor: pointer;
  user-select: none;
}

.panda-wrap {
  position: relative;
  width: 200px; height: 240px;
  transition: transform 0.2s;
  animation: floatIdle 3s ease-in-out infinite;
}
.panda-outer:active .panda-wrap { transform: scale(0.95); }

.panda-svg {
  width: 100%; height: 100%;
  filter: drop-shadow(0 0 18px rgba(255,107,157,0.4)) drop-shadow(0 12px 24px rgba(0,0,0,0.5));
  transition: filter 0.5s;
}
.hugging .panda-svg {
  filter: drop-shadow(0 0 40px rgba(255,107,157,0.9)) drop-shadow(0 0 80px rgba(196,77,255,0.5)) drop-shadow(0 12px 24px rgba(0,0,0,0.5));
}

.hugging .panda-wrap { animation: hugBounce 0.5s ease-out; }
@keyframes floatIdle {
  0%,100% { transform: translateY(0) rotate(0deg); }
  50%      { transform: translateY(-12px) rotate(1deg); }
}
@keyframes hugBounce {
  0%   { transform: scale(1); }
  30%  { transform: scale(1.1) rotate(-3deg); }
  60%  { transform: scale(0.97) rotate(2deg); }
  100% { transform: scale(1) rotate(0deg); }
}

#arm-l { transform-origin: 68px 158px; transition: transform 0.5s cubic-bezier(0.34,1.56,0.64,1); }
#arm-r { transform-origin: 152px 158px; transition: transform 0.5s cubic-bezier(0.34,1.56,0.64,1); }
.hugging #arm-l { transform: rotate(-55deg) translateY(-20px); }
.hugging #arm-r { transform: rotate(55deg) translateY(-20px); }

#eye-ln, #eye-rn { transition: opacity 0.3s; }
#eye-lh, #eye-rh { opacity: 0; transition: opacity 0.3s; }
.hugging #eye-ln, .hugging #eye-rn { opacity: 0; }
.hugging #eye-lh, .hugging #eye-rh { opacity: 1; }

#blush-l, #blush-r { opacity: 0; transition: opacity 0.6s; }
.hugging #blush-l, .hugging #blush-r { opacity: 1; }

#mouth-n { transition: opacity 0.3s; }
#mouth-h { opacity: 0; transition: opacity 0.3s; }
.hugging #mouth-n { opacity: 0; }
.hugging #mouth-h { opacity: 1; }

.bubble {
  position: absolute;
  top: -62px; left: 50%;
  transform: translateX(-50%) scale(0) rotate(-4deg);
  background: linear-gradient(135deg, rgba(255,255,255,0.95), rgba(255,220,240,0.95));
  border: 2px solid rgba(255,107,157,0.6);
  border-radius: 20px;
  padding: 8px 20px;
  font-size: 0.95rem;
  font-weight: 700;
  color: #b0005a;
  white-space: nowrap;
  box-shadow: 0 4px 20px rgba(255,107,157,0.4), 0 0 30px rgba(255,107,157,0.2);
  transition: transform 0.5s cubic-bezier(0.34,1.56,0.64,1), opacity 0.4s;
  opacity: 0;
  pointer-events: none;
}
.bubble::after {
  content: '';
  position: absolute; bottom: -10px; left: 50%;
  transform: translateX(-50%);
  border: 7px solid transparent;
  border-top-color: rgba(255,107,157,0.6);
}
.hugging .bubble { transform: translateX(-50%) scale(1) rotate(0deg); opacity: 1; }

.hug-btn {
  margin-top: 22px;
  padding: 13px 48px;
  background: linear-gradient(135deg, #ff6b9d, #c44dff);
  border: none; border-radius: 100px;
  color: #fff;
  font-family: 'Quicksand', sans-serif;
  font-size: 1.05rem; font-weight: 700;
  letter-spacing: 1.5px;
  cursor: pointer;
  position: relative; overflow: hidden;
  box-shadow: 0 4px 30px rgba(255,107,157,0.5), 0 0 60px rgba(196,77,255,0.2);
  transition: transform 0.2s, box-shadow 0.3s;
}
.hug-btn::before {
  content: '';
  position: absolute; inset: 0;
  background: linear-gradient(135deg, rgba(255,255,255,0.2), transparent);
  border-radius: inherit;
}
.hug-btn::after {
  content: '';
  position: absolute;
  top: -50%; left: -60%;
  width: 60%; height: 200%;
  background: rgba(255,255,255,0.25);
  transform: skewX(-20deg);
  transition: left 0.5s;
}
.hug-btn:hover::after { left: 130%; }
.hug-btn:hover { transform: translateY(-3px) scale(1.03); box-shadow: 0 8px 40px rgba(255,107,157,0.7), 0 0 80px rgba(196,77,255,0.4); }
.hug-btn:active { transform: scale(0.97); }

.hint {
  margin-top: 8px;
  font-size: 0.78rem; color: rgba(255,179,209,0.55);
  letter-spacing: 1px;
}

.dev {
  position: fixed;
  bottom: 16px; right: 20px;
  z-index: 20;
  font-size: 0.72rem;
  font-weight: 700;
  color: rgba(255,179,209,0.45);
  letter-spacing: 2px;
  text-transform: uppercase;
}

.glow-ring {
  position: absolute;
  inset: -30px;
  border-radius: 50%;
  background: transparent;
  pointer-events: none;
  opacity: 0;
  transition: opacity 0.5s;
}
.hugging .glow-ring {
  opacity: 1;
  animation: ringPulse 1.5s ease-in-out infinite;
}
@keyframes ringPulse {
  0%,100% { box-shadow: 0 0 40px 10px rgba(255,107,157,0.3), 0 0 80px 20px rgba(196,77,255,0.15); }
  50%      { box-shadow: 0 0 60px 20px rgba(255,107,157,0.5), 0 0 120px 40px rgba(196,77,255,0.3); }
}

.star-deco {
  position: absolute;
  font-size: 0.7rem;
  color: rgba(255,200,230,0.4);
  animation: twinkle 3s ease-in-out infinite;
  pointer-events: none;
}
@keyframes twinkle {
  0%,100% { opacity: 0.3; transform: scale(1); }
  50%      { opacity: 1; transform: scale(1.4); }
}
</style>
</head>
<body>

<div id="cursor"></div>
<canvas id="canvas"></canvas>
<div class="bg-mesh"></div>

<div class="stage">

  <div class="title-block">
    <div class="title-for">A little love for</div>
    <div class="title-name">Lynna 🐼</div>
  </div>

  <div class="love-line">
    <span class="love-heart">♥</span>
    I love you so much
    <span class="love-heart" style="animation-delay:0.3s">♥</span>
  </div>

  <div class="card" id="card">

    <div class="star-deco" style="top:22px;right:50px;animation-delay:0s">✦</div>
    <div class="star-deco" style="top:50px;right:28px;animation-delay:1.2s">✧</div>
    <div class="star-deco" style="bottom:50px;left:30px;animation-delay:0.6s">✦</div>
    <div class="star-deco" style="bottom:22px;left:55px;animation-delay:1.8s">✧</div>

    <div class="panda-outer" id="pandaOuter" onclick="toggleHug()">
      <div class="glow-ring"></div>
      <div class="bubble">Lynna I got you!! 🐾💗</div>

      <div class="panda-wrap" id="pandaWrap">
        <svg class="panda-svg" viewBox="0 0 220 250" xmlns="http://www.w3.org/2000/svg">
          <defs>
            <radialGradient id="bodyGrad" cx="50%" cy="40%" r="60%">
              <stop offset="0%" stop-color="#ffffff"/>
              <stop offset="100%" stop-color="#f0eaf5"/>
            </radialGradient>
            <radialGradient id="darkGrad" cx="40%" cy="35%" r="65%">
              <stop offset="0%" stop-color="#3a2a4a"/>
              <stop offset="100%" stop-color="#1a0f2e"/>
            </radialGradient>
            <radialGradient id="bellyGrad" cx="50%" cy="40%" r="60%">
              <stop offset="0%" stop-color="#fdf5ff"/>
              <stop offset="100%" stop-color="#ede0f5"/>
            </radialGradient>
            <filter id="softGlow">
              <feGaussianBlur in="SourceGraphic" stdDeviation="2" result="blur"/>
              <feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge>
            </filter>
          </defs>

          <ellipse cx="110" cy="247" rx="52" ry="7" fill="rgba(0,0,0,0.25)"/>
          <ellipse cx="110" cy="178" rx="60" ry="62" fill="url(#bodyGrad)"/>
          <ellipse cx="110" cy="188" rx="30" ry="36" fill="url(#bellyGrad)" opacity="0.9"/>
          <ellipse cx="83"  cy="232" rx="22" ry="13" fill="url(#darkGrad)"/>
          <ellipse cx="137" cy="232" rx="22" ry="13" fill="url(#darkGrad)"/>
          <ellipse cx="78"  cy="227" rx="7" ry="3"  fill="rgba(255,255,255,0.12)"/>
          <ellipse cx="132" cy="227" rx="7" ry="3"  fill="rgba(255,255,255,0.12)"/>

          <g id="arm-l">
            <ellipse cx="62" cy="165" rx="24" ry="12" fill="url(#darkGrad)" transform="rotate(-25 62 165)"/>
            <circle  cx="49" cy="177" r="12" fill="#2a1d3d"/>
            <circle cx="44" cy="173" r="2.5" fill="rgba(255,180,220,0.5)"/>
            <circle cx="50" cy="170" r="2.5" fill="rgba(255,180,220,0.5)"/>
            <circle cx="55" cy="173" r="2.5" fill="rgba(255,180,220,0.5)"/>
          </g>

          <g id="arm-r">
            <ellipse cx="158" cy="165" rx="24" ry="12" fill="url(#darkGrad)" transform="rotate(25 158 165)"/>
            <circle  cx="171" cy="177" r="12" fill="#2a1d3d"/>
            <circle cx="166" cy="173" r="2.5" fill="rgba(255,180,220,0.5)"/>
            <circle cx="172" cy="170" r="2.5" fill="rgba(255,180,220,0.5)"/>
            <circle cx="177" cy="173" r="2.5" fill="rgba(255,180,220,0.5)"/>
          </g>

          <ellipse cx="90" cy="155" rx="18" ry="10" fill="rgba(255,255,255,0.35)" transform="rotate(-20 90 155)"/>
          <circle cx="110" cy="100" r="56" fill="url(#bodyGrad)"/>
          <ellipse cx="90" cy="75" rx="20" ry="12" fill="rgba(255,255,255,0.4)" transform="rotate(-20 90 75)"/>

          <circle cx="62"  cy="54" r="21" fill="url(#darkGrad)"/>
          <circle cx="158" cy="54" r="21" fill="url(#darkGrad)"/>
          <circle cx="62"  cy="54" r="11" fill="#3a2050"/>
          <circle cx="158" cy="54" r="11" fill="#3a2050"/>
          <circle cx="62"  cy="54" r="5.5" fill="rgba(255,130,180,0.5)"/>
          <circle cx="158" cy="54" r="5.5" fill="rgba(255,130,180,0.5)"/>

          <ellipse cx="86"  cy="97" rx="19" ry="18" fill="url(#darkGrad)"/>
          <ellipse cx="134" cy="97" rx="19" ry="18" fill="url(#darkGrad)"/>

          <g id="eye-ln">
            <circle cx="86"  cy="97" r="10" fill="white"/>
            <circle cx="88"  cy="95" r="6"  fill="#111"/>
            <circle cx="90"  cy="93" r="2.5" fill="white"/>
            <circle cx="86"  cy="99" r="1.2" fill="rgba(255,255,255,0.6)"/>
          </g>
          <g id="eye-rn">
            <circle cx="134" cy="97" r="10" fill="white"/>
            <circle cx="136" cy="95" r="6"  fill="#111"/>
            <circle cx="138" cy="93" r="2.5" fill="white"/>
            <circle cx="134" cy="99" r="1.2" fill="rgba(255,255,255,0.6)"/>
          </g>

          <g id="eye-lh" filter="url(#softGlow)">
            <text x="76" y="105" font-size="18" fill="#ff4d88">♥</text>
          </g>
          <g id="eye-rh" filter="url(#softGlow)">
            <text x="124" y="105" font-size="18" fill="#ff4d88">♥</text>
          </g>

          <ellipse id="blush-l" cx="68"  cy="113" rx="14" ry="8" fill="#ffb3d1" opacity="0"/>
          <ellipse id="blush-r" cx="152" cy="113" rx="14" ry="8" fill="#ffb3d1" opacity="0"/>

          <ellipse cx="110" cy="112" rx="7.5" ry="5.5" fill="#3a2050"/>
          <ellipse cx="109" cy="111" rx="3"   ry="2"   fill="rgba(255,255,255,0.25)"/>

          <g id="mouth-n">
            <path d="M 100 122 Q 110 131 120 122" stroke="#5a3a6a" stroke-width="2.5" fill="none" stroke-linecap="round"/>
          </g>
          <g id="mouth-h">
            <path d="M 97 121 Q 110 137 123 121" stroke="#ff6b9d" stroke-width="3" fill="rgba(255,107,157,0.1)" stroke-linecap="round"/>
            <circle cx="99"  cy="123" r="3" fill="#ff6b9d" opacity="0.5"/>
            <circle cx="121" cy="123" r="3" fill="#ff6b9d" opacity="0.5"/>
          </g>

          <text x="100" y="200" font-size="20" fill="rgba(255,130,180,0.6)" filter="url(#softGlow)">♥</text>
          <text x="148" y="68"  font-size="11" fill="rgba(255,200,230,0.8)">✦</text>
          <text x="54"  y="72"  font-size="9"  fill="rgba(255,200,230,0.6)">✧</text>
          <text x="155" y="88"  font-size="8"  fill="rgba(255,200,230,0.55)">✦</text>
        </svg>
      </div>
    </div>

    <button class="hug-btn" id="hugBtn" onclick="toggleHug()">🐼 Hug Me, Lynna!</button>
    <div class="hint" id="hintText">tap the panda ✦ tap the button</div>
  </div>

</div>

<div class="dev">Dev by Xinn ✦</div>

<script>
// ── CURSOR
const cur = document.getElementById('cursor');
document.addEventListener('mousemove', e => {
  cur.style.left = e.clientX + 'px';
  cur.style.top  = e.clientY + 'px';
});
document.addEventListener('mousedown', () => { cur.style.transform = 'translate(-50%,-50%) scale(1.8)'; });
document.addEventListener('mouseup',   () => { cur.style.transform = 'translate(-50%,-50%) scale(1)'; });

// ── CANVAS PARTICLES
const canvas = document.getElementById('canvas');
const ctx = canvas.getContext('2d');
canvas.width  = window.innerWidth;
canvas.height = window.innerHeight;
window.addEventListener('resize', () => {
  canvas.width  = window.innerWidth;
  canvas.height = window.innerHeight;
});

let hugging = false;
const particles = [];

const EMOJIS = ['💗','💕','💖','🩷','💓','✨','🌸','💫','⭐','💝','🌷','🎀'];

class Particle {
  constructor(x, y, burst) {
    this.x = (x != null) ? x : Math.random() * canvas.width;
    this.y = (y != null) ? y : canvas.height + 20;
    this.burst = !!burst;

    if (this.burst) {
      const angle = Math.random() * Math.PI * 2;
      const speed = 2 + Math.random() * 5;
      this.vx = Math.cos(angle) * speed;
      this.vy = Math.sin(angle) * speed - 3;
    } else {
      this.vx = (Math.random() - 0.5) * 1.2;
      this.vy = -(0.6 + Math.random() * 1.8);
    }

    this.size    = 8 + Math.random() * 18;
    this.opacity = 0;
    this.maxOp   = 0.6 + Math.random() * 0.4;
    this.life    = 0;
    this.maxLife = this.burst ? 80 + Math.random() * 60 : 140 + Math.random() * 100;
    this.wobble  = Math.random() * Math.PI * 2;
    this.wobbleSpeed = 0.02 + Math.random() * 0.04;
    this.useEmoji = Math.random() > 0.4;
    this.emoji   = EMOJIS[Math.floor(Math.random() * EMOJIS.length)];
    this.rotation = Math.random() * Math.PI * 2;
    this.rotSpeed = (Math.random() - 0.5) * 0.08;
    this.isHeart  = !this.useEmoji && Math.random() > 0.4;
    this.isStar   = !this.useEmoji && !this.isHeart;
    this.gravity  = this.burst ? 0.08 : 0;

    const palette = ['#ff6b9d','#ff8fb3','#ffb3d1','#c44dff','#e07dff','#ff4d88','#fff0f8','#ffd6ec','#a855f7'];
    this.color = palette[Math.floor(Math.random() * palette.length)];
  }

  update() {
    this.life++;
    this.wobble += this.wobbleSpeed;
    this.x += this.vx + Math.sin(this.wobble) * 0.6;
    this.y += this.vy;
    this.vy += this.gravity;
    this.rotation += this.rotSpeed;

    const prog = this.life / this.maxLife;
    if (prog < 0.15)      this.opacity = (prog / 0.15) * this.maxOp;
    else if (prog < 0.7)  this.opacity = this.maxOp;
    else                  this.opacity = this.maxOp * (1 - (prog - 0.7) / 0.3);

    return this.life < this.maxLife;
  }

  draw() {
    ctx.save();
    ctx.globalAlpha = this.opacity;
    ctx.translate(this.x, this.y);
    ctx.rotate(this.rotation);

    if (this.useEmoji) {
      ctx.font = this.size + 'px serif';
      ctx.textAlign = 'center';
      ctx.textBaseline = 'middle';
      ctx.fillText(this.emoji, 0, 0);
    } else {
      ctx.fillStyle = this.color;
      ctx.shadowColor = this.color;
      ctx.shadowBlur = 14;
      if (this.isHeart) {
        const r = this.size * 0.55;
        ctx.beginPath();
        ctx.moveTo(0, r * 0.3);
        ctx.bezierCurveTo(0, -r*0.5, -r*1.2, -r*0.5, -r*1.2, r*0.2);
        ctx.bezierCurveTo(-r*1.2, r*0.9, 0, r*1.4, 0, r*1.4);
        ctx.bezierCurveTo(0, r*1.4, r*1.2, r*0.9, r*1.2, r*0.2);
        ctx.bezierCurveTo(r*1.2, -r*0.5, 0, -r*0.5, 0, r*0.3);
        ctx.fill();
      } else {
        // star
        const r = this.size * 0.5;
        ctx.beginPath();
        for (let i = 0; i < 10; i++) {
          const ang = (i * Math.PI) / 5 - Math.PI / 2;
          const rad = i % 2 === 0 ? r : r * 0.45;
          i === 0 ? ctx.moveTo(Math.cos(ang)*rad, Math.sin(ang)*rad)
                  : ctx.lineTo(Math.cos(ang)*rad, Math.sin(ang)*rad);
        }
        ctx.closePath(); ctx.fill();
      }
    }
    ctx.restore();
  }
}

function spawnAmbient() {
  const limit = hugging ? 220 : 90;
  if (particles.length < limit) particles.push(new Particle());
}

function spawnBurst(cx, cy) {
  for (let i = 0; i < 70; i++) particles.push(new Particle(cx, cy, true));
}

let lastTrail = 0;
document.addEventListener('mousemove', e => {
  const now = Date.now();
  if (now - lastTrail > 55) {
    lastTrail = now;
    if (Math.random() > 0.35) particles.push(new Particle(e.clientX, e.clientY, true));
  }
});

// Touch trail support
document.addEventListener('touchmove', e => {
  const t = e.touches[0];
  if (Math.random() > 0.35) particles.push(new Particle(t.clientX, t.clientY, true));
}, { passive: true });

function loop() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  spawnAmbient();
  for (let i = particles.length - 1; i >= 0; i--) {
    if (!particles[i].update()) { particles.splice(i, 1); continue; }
    particles[i].draw();
  }
  requestAnimationFrame(loop);
}
loop();

// ── HUG TOGGLE
let isHugging = false;
function toggleHug() {
  isHugging = !isHugging;
  hugging   = isHugging;

  const outer = document.getElementById('pandaOuter');
  const card  = document.getElementById('card');
  const btn   = document.getElementById('hugBtn');
  const hint  = document.getElementById('hintText');
  const wrap  = document.getElementById('pandaWrap');

  if (isHugging) {
    outer.classList.add('hugging');
    card.classList.add('hugging');
    wrap.classList.add('hugging');
    btn.textContent = '🥺 Let go...';
    hint.textContent = 'tap again to let go ♥';

    const rect = wrap.getBoundingClientRect();
    spawnBurst(rect.left + rect.width/2, rect.top + rect.height/2);

    let s = 0;
    const shim = setInterval(() => {
      s++;
      document.body.style.transform = s%2===0 ? 'translate(4px,-2px)' : 'translate(-4px,2px)';
      if (s > 7) { clearInterval(shim); document.body.style.transform = ''; }
    }, 55);
  } else {
    outer.classList.remove('hugging');
    card.classList.remove('hugging');
    wrap.classList.remove('hugging');
    btn.textContent = '🐼 Hug Me, Lynna!';
    hint.textContent = 'tap the panda ✦ tap the button';
  }
}
</script>
</body>
</html>
