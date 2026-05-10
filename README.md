
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Lynna's Panda 🐼</title>
<link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Nunito:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #fff0f5;
    --pink: #ff85a2;
    --deep-pink: #e8476b;
    --soft: #ffd6e7;
    --black: #1a1a2e;
    --white: #ffffff;
    --heart: #ff4d77;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    font-family: 'Nunito', sans-serif;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    position: relative;
  }

  /* Floating hearts background */
  .hearts-bg {
    position: fixed;
    inset: 0;
    pointer-events: none;
    z-index: 0;
  }
  .heart-float {
    position: absolute;
    bottom: -60px;
    font-size: 1.5rem;
    opacity: 0;
    animation: floatUp linear infinite;
  }
  @keyframes floatUp {
    0%   { opacity: 0; transform: translateY(0) rotate(0deg); }
    10%  { opacity: 0.7; }
    90%  { opacity: 0.4; }
    100% { opacity: 0; transform: translateY(-110vh) rotate(30deg); }
  }

  /* Page title */
  .title-wrap {
    text-align: center;
    z-index: 2;
    position: relative;
    margin-bottom: 6px;
    animation: fadeDown 0.9s cubic-bezier(0.22, 1, 0.36, 1) both;
  }
  @keyframes fadeDown {
    from { opacity: 0; transform: translateY(-30px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  .title {
    font-family: 'Pacifico', cursive;
    font-size: clamp(2rem, 6vw, 3.8rem);
    color: var(--deep-pink);
    text-shadow: 3px 4px 0 #ffc0cb, 5px 7px 0 rgba(232,71,107,0.15);
    letter-spacing: 1px;
    line-height: 1.1;
  }
  .subtitle {
    font-size: clamp(1rem, 2.5vw, 1.3rem);
    color: var(--pink);
    font-weight: 700;
    margin-top: 6px;
    letter-spacing: 2px;
    text-transform: uppercase;
  }

  /* Love text */
  .love-text {
    font-family: 'Pacifico', cursive;
    font-size: clamp(1.1rem, 3vw, 1.7rem);
    color: var(--heart);
    z-index: 2;
    position: relative;
    margin-bottom: 18px;
    animation: fadeDown 1.1s 0.2s cubic-bezier(0.22, 1, 0.36, 1) both;
  }
  .love-text span {
    display: inline-block;
    animation: heartbeat 1.5s infinite;
  }
  @keyframes heartbeat {
    0%, 100% { transform: scale(1); }
    30%       { transform: scale(1.25); }
    60%       { transform: scale(1.1); }
  }

  /* Scene container */
  .scene {
    z-index: 2;
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    animation: fadeUp 0.9s 0.3s cubic-bezier(0.22, 1, 0.36, 1) both;
  }
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* Panda SVG wrapper */
  .panda-wrap {
    position: relative;
    width: 220px;
    height: 260px;
    cursor: pointer;
    transition: transform 0.2s;
    user-select: none;
  }
  .panda-wrap:active { transform: scale(0.96); }

  .panda-svg {
    width: 100%;
    height: 100%;
    transition: filter 0.3s;
    filter: drop-shadow(0 12px 30px rgba(255,133,162,0.35));
  }

  /* Hug state — panda's arms swing out & screen dims */
  .hug-mode .panda-svg {
    filter: drop-shadow(0 16px 40px rgba(255,77,119,0.55));
  }

  /* Arms animation (SVG elements) */
  #arm-left  { transform-origin: 75px 165px; transition: transform 0.45s cubic-bezier(0.34,1.56,0.64,1); }
  #arm-right { transform-origin: 145px 165px; transition: transform 0.45s cubic-bezier(0.34,1.56,0.64,1); }
  .hug-mode #arm-left  { transform: rotate(-50deg) translateY(-18px); }
  .hug-mode #arm-right { transform: rotate(50deg) translateY(-18px); }

  /* Eyes blink / heart eyes */
  #eye-left-normal, #eye-right-normal { transition: opacity 0.3s; }
  #eye-left-heart,  #eye-right-heart  { opacity: 0; transition: opacity 0.3s; }
  .hug-mode #eye-left-normal,
  .hug-mode #eye-right-normal { opacity: 0; }
  .hug-mode #eye-left-heart,
  .hug-mode #eye-right-heart  { opacity: 1; }

  /* Blush */
  #blush-left, #blush-right { opacity: 0; transition: opacity 0.5s; }
  .hug-mode #blush-left, .hug-mode #blush-right { opacity: 1; }

  /* Mouth */
  #mouth-normal { transition: opacity 0.3s; }
  #mouth-happy  { opacity: 0; transition: opacity 0.3s; }
  .hug-mode #mouth-normal { opacity: 0; }
  .hug-mode #mouth-happy  { opacity: 1; }

  /* Hug overlay text */
  .hug-label {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) scale(0);
    font-family: 'Pacifico', cursive;
    font-size: 2.5rem;
    color: var(--heart);
    white-space: nowrap;
    pointer-events: none;
    transition: transform 0.4s cubic-bezier(0.34,1.56,0.64,1);
    text-shadow: 0 2px 12px rgba(255,77,119,0.35);
  }
  .hug-mode .hug-label { transform: translate(-50%, -50%) scale(1); }

  /* Flying hearts on hug */
  .hug-heart {
    position: absolute;
    font-size: 1.6rem;
    pointer-events: none;
    opacity: 0;
    animation: none;
  }
  .hug-mode .hug-heart { animation: burstHeart 0.9s ease-out forwards; }
  .hug-heart:nth-child(1)  { top: 10px;  left: 30px;  animation-delay: 0s; }
  .hug-heart:nth-child(2)  { top: 0;     left: 100px; animation-delay: 0.08s; }
  .hug-heart:nth-child(3)  { top: 15px;  left: 175px; animation-delay: 0.16s; }
  .hug-heart:nth-child(4)  { top: 60px;  left: -10px; animation-delay: 0.05s; }
  .hug-heart:nth-child(5)  { top: 60px;  left: 210px; animation-delay: 0.12s; }
  @keyframes burstHeart {
    0%   { opacity: 1; transform: translateY(0) scale(0.5); }
    70%  { opacity: 1; }
    100% { opacity: 0; transform: translateY(-70px) scale(1.3); }
  }

  /* Bounce idle animation */
  .idle-bounce {
    animation: bounce 2.5s ease-in-out infinite;
  }
  .hug-mode .idle-bounce { animation: none; }
  @keyframes bounce {
    0%, 100% { transform: translateY(0); }
    50%       { transform: translateY(-10px); }
  }

  /* Button */
  .hug-btn {
    margin-top: 28px;
    padding: 14px 42px;
    background: linear-gradient(135deg, var(--pink), var(--deep-pink));
    color: #fff;
    font-family: 'Nunito', sans-serif;
    font-size: 1.15rem;
    font-weight: 800;
    border: none;
    border-radius: 50px;
    cursor: pointer;
    box-shadow: 0 6px 24px rgba(232,71,107,0.35), 0 2px 0 #c23060 inset;
    letter-spacing: 1px;
    transition: transform 0.15s, box-shadow 0.15s;
    position: relative;
    overflow: hidden;
  }
  .hug-btn::after {
    content: '';
    position: absolute;
    inset: 0;
    background: rgba(255,255,255,0.18);
    opacity: 0;
    transition: opacity 0.2s;
    border-radius: inherit;
  }
  .hug-btn:hover { transform: translateY(-3px); box-shadow: 0 10px 30px rgba(232,71,107,0.45), 0 2px 0 #c23060 inset; }
  .hug-btn:hover::after { opacity: 1; }
  .hug-btn:active { transform: translateY(0) scale(0.97); }

  /* Hint text */
  .hint {
    margin-top: 10px;
    font-size: 0.88rem;
    color: #e8b0c0;
    font-weight: 600;
    letter-spacing: 0.5px;
  }

  /* Dev credit */
  .dev {
    position: fixed;
    bottom: 16px;
    right: 20px;
    font-size: 0.78rem;
    color: #e8b0c0;
    font-weight: 700;
    letter-spacing: 1px;
    z-index: 10;
  }

  /* Bubble */
  .bubble {
    position: absolute;
    top: -54px;
    left: 50%;
    transform: translateX(-50%) scale(0);
    background: white;
    border: 2.5px solid var(--pink);
    border-radius: 18px;
    padding: 7px 18px;
    font-size: 1rem;
    font-weight: 800;
    color: var(--deep-pink);
    white-space: nowrap;
    box-shadow: 0 4px 14px rgba(255,133,162,0.3);
    transition: transform 0.4s cubic-bezier(0.34,1.56,0.64,1);
    pointer-events: none;
  }
  .bubble::after {
    content: '';
    position: absolute;
    bottom: -10px;
    left: 50%;
    transform: translateX(-50%);
    border: 6px solid transparent;
    border-top-color: var(--pink);
  }
  .hug-mode .bubble { transform: translateX(-50%) scale(1); }
</style>
</head>
<body>

<!-- Floating hearts background -->
<div class="hearts-bg" id="heartsContainer"></div>

<!-- Title -->
<div class="title-wrap">
  <div class="title">Lynna's Panda 🐼</div>
  <div class="subtitle">A hug just for you ✨</div>
</div>

<!-- Love text -->
<div class="love-text">
  I love you so much &nbsp;<span>💖</span>
</div>

<!-- Scene -->
<div class="scene" id="scene">
  <div class="panda-wrap idle-bounce" id="pandaWrap" onclick="toggleHug()">

    <!-- Hug bubble -->
    <div class="bubble">Huggg!! 🐼💕</div>

    <!-- Flying hearts -->
    <div class="hug-heart">💗</div>
    <div class="hug-heart">💕</div>
    <div class="hug-heart">💖</div>
    <div class="hug-heart">🩷</div>
    <div class="hug-heart">💓</div>

    <!-- PANDA SVG -->
    <svg class="panda-svg" viewBox="0 0 220 260" xmlns="http://www.w3.org/2000/svg">

      <!-- Shadow -->
      <ellipse cx="110" cy="253" rx="55" ry="8" fill="rgba(0,0,0,0.08)"/>

      <!-- Body -->
      <ellipse cx="110" cy="185" rx="62" ry="65" fill="white" stroke="#222" stroke-width="2.5"/>

      <!-- Belly spot -->
      <ellipse cx="110" cy="195" rx="32" ry="38" fill="#f0f0f0"/>

      <!-- Left arm (normal) -->
      <g id="arm-left">
        <ellipse cx="68" cy="172" rx="22" ry="13" fill="#222" transform="rotate(-30 68 172)"/>
        <circle cx="55" cy="182" r="10" fill="#333"/>
      </g>

      <!-- Right arm (normal) -->
      <g id="arm-right">
        <ellipse cx="152" cy="172" rx="22" ry="13" fill="#222" transform="rotate(30 152 172)"/>
        <circle cx="165" cy="182" r="10" fill="#333"/>
      </g>

      <!-- Left leg -->
      <ellipse cx="83" cy="238" rx="20" ry="14" fill="#222"/>
      <!-- Right leg -->
      <ellipse cx="137" cy="238" rx="20" ry="14" fill="#222"/>

      <!-- Head -->
      <circle cx="110" cy="108" r="58" fill="white" stroke="#222" stroke-width="2.5"/>

      <!-- Ear patches -->
      <circle cx="62"  cy="60" r="20" fill="#222"/>
      <circle cx="158" cy="60" r="20" fill="#222"/>
      <circle cx="62"  cy="60" r="10" fill="#444"/>
      <circle cx="158" cy="60" r="10" fill="#444"/>

      <!-- Eye patches -->
      <ellipse cx="88"  cy="103" rx="18" ry="17" fill="#222"/>
      <ellipse cx="132" cy="103" rx="18" ry="17" fill="#222"/>

      <!-- Normal eyes -->
      <g id="eye-left-normal">
        <circle cx="88"  cy="103" r="9" fill="white"/>
        <circle cx="90"  cy="101" r="5" fill="#111"/>
        <circle cx="92"  cy="100" r="2" fill="white"/>
      </g>
      <g id="eye-right-normal">
        <circle cx="132" cy="103" r="9" fill="white"/>
        <circle cx="134" cy="101" r="5" fill="#111"/>
        <circle cx="136" cy="100" r="2" fill="white"/>
      </g>

      <!-- Heart eyes (hidden by default) -->
      <g id="eye-left-heart">
        <text x="79" y="109" font-size="16" fill="#ff4d77">♥</text>
      </g>
      <g id="eye-right-heart">
        <text x="123" y="109" font-size="16" fill="#ff4d77">♥</text>
      </g>

      <!-- Blush -->
      <ellipse id="blush-left"  cx="72"  cy="120" rx="12" ry="7" fill="#ffb3c6" opacity="0.85"/>
      <ellipse id="blush-right" cx="148" cy="120" rx="12" ry="7" fill="#ffb3c6" opacity="0.85"/>

      <!-- Nose -->
      <ellipse cx="110" cy="117" rx="7" ry="5" fill="#555"/>

      <!-- Normal mouth -->
      <g id="mouth-normal">
        <path d="M 100 125 Q 110 133 120 125" stroke="#555" stroke-width="2.5" fill="none" stroke-linecap="round"/>
      </g>
      <!-- Happy mouth -->
      <g id="mouth-happy">
        <path d="M 97 124 Q 110 138 123 124" stroke="#ff6b8b" stroke-width="2.8" fill="none" stroke-linecap="round"/>
        <path d="M 97 124 Q 110 142 123 124" fill="rgba(255,107,139,0.15)"/>
      </g>

      <!-- Tiny heart on chest -->
      <text x="101" y="207" font-size="18" fill="#ffb3c6">♥</text>

    </svg>
  </div>

  <button class="hug-btn" onclick="toggleHug()">
    🐼 Hug Me, Lynna!
  </button>
  <div class="hint" id="hintText">Click the panda or the button ☝️</div>
</div>

<!-- Dev credit -->
<div class="dev">Dev by Xinn 🌸</div>

<script>
  let hugging = false;

  // Generate floating bg hearts
  const container = document.getElementById('heartsContainer');
  const emojis = ['💗','💕','💖','🩷','💞','💓','🌸','✨'];
  for (let i = 0; i < 22; i++) {
    const h = document.createElement('div');
    h.className = 'heart-float';
    h.textContent = emojis[Math.floor(Math.random() * emojis.length)];
    h.style.left = Math.random() * 100 + 'vw';
    h.style.animationDuration = (6 + Math.random() * 10) + 's';
    h.style.animationDelay = (Math.random() * 12) + 's';
    h.style.fontSize = (1 + Math.random() * 1.2) + 'rem';
    container.appendChild(h);
  }

  function toggleHug() {
    const wrap = document.getElementById('pandaWrap');
    const hint = document.getElementById('hintText');
    hugging = !hugging;

    if (hugging) {
      wrap.classList.add('hug-mode');
      document.getElementById('scene').classList.add('hug-mode');
      wrap.classList.remove('idle-bounce');
      hint.textContent = 'Click again to let go 🥺';
      // Shake camera gently
      document.body.style.transition = 'transform 0.1s';
      let s = 0;
      const shake = setInterval(() => {
        s++;
        document.body.style.transform = s % 2 === 0 ? 'translateX(3px)' : 'translateX(-3px)';
        if (s > 5) { clearInterval(shake); document.body.style.transform = ''; }
      }, 60);
    } else {
      wrap.classList.remove('hug-mode');
      document.getElementById('scene').classList.remove('hug-mode');
      setTimeout(() => wrap.classList.add('idle-bounce'), 100);
      hint.textContent = 'Click the panda or the button ☝️';
    }
  }
</script>
</body>
</html>
