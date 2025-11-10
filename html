<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1"/>
<title>Flappy City-Pop — Pixel Flappy with City-Pop Music</title>
<style>
  :root { font-family: Inter, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial; }
  html,body { height:100%; margin:0; background: linear-gradient(#6fb3ff,#d9f2ff 60%); }
  .container { max-width:980px; margin:18px auto; padding:12px; }
  header { display:flex; align-items:center; justify-content:space-between; gap:12px; margin-bottom:8px; }
  h1 { margin:0; font-size:18px; color:#04344a; letter-spacing:0.2px; }
  .controls { display:flex; gap:8px; align-items:center; }
  button, select { background:#0b5; color:#fff; border:0; padding:8px 10px; border-radius:8px; cursor:pointer; font-weight:700; }
  button.secondary { background:#fff; color:#04344a; border:1px solid rgba(0,0,0,0.06); }
  .card { background: linear-gradient(#e6f8ff,#f8ffff); padding:12px; border-radius:12px; box-shadow:0 8px 30px rgba(5,30,60,0.08); }
  .game-row { display:flex; gap:12px; align-items:flex-start; }
  #gameWrap { flex: 1 1 640px; min-width:300px; }
  canvas#game { width:100%; height:620px; image-rendering: pixelated; border-radius:8px; display:block; background: linear-gradient(#78c0ff, #bfefff 60%); touch-action:none; }
  .side { width:260px; min-width:200px; }
  .panel { background:#fff; padding:12px; border-radius:10px; box-shadow:0 6px 20px rgba(0,0,0,0.06); color:#04344a; }
  label { display:block; font-weight:700; margin-top:8px; font-size:13px; }
  input[type="range"] { width:100%; }
  .hud { display:flex; justify-content:space-between; align-items:center; margin-top:10px; font-weight:800; color:#04344a; }
  .muted { color:#547; font-weight:600; font-size:13px; margin-top:6px; }
  .overlay { position:fixed; inset:0; display:flex; align-items:center; justify-content:center; background:rgba(0,0,0,0.45); }
  .dialog { background:#fff; width:90%; max-width:420px; border-radius:12px; padding:18px; text-align:center; box-shadow:0 12px 40px rgba(5,30,60,0.2); }
  .small { font-size:13px; color:#446; margin-top:6px; }
  footer { margin-top:10px; text-align:center; font-size:13px; color:#04344a;}
  @media (max-width:900px){ .game-row{flex-direction:column-reverse;} .side{width:100%} canvas#game{height:460px} }
</style>
</head>
<body>
  <div class="container">
    <header>
      <h1>Flappy City-Pop — Pixel Mode + City-Pop Music</h1>
      <div class="controls">
        <button id="startBtn">Start</button>
        <button id="replayBtn" class="secondary">Replay</button>
        <button id="muteBtn" class="secondary">Mute</button>
      </div>
    </header>

    <div class="card game-row">
      <div id="gameWrap">
        <canvas id="game" aria-label="Flappy CityPop game"></canvas>
        <div class="hud">
          <div>Score: <span id="score">0</span></div>
          <div>Best: <span id="best">0</span></div>
          <div id="state">Press Space / Tap to play</div>
        </div>
      </div>

      <div class="side">
        <div class="panel">
          <label>Pixel Art Mode
            <select id="pixelToggle">
              <option value="1">On (pixel art)</option>
              <option value="0">Off (smooth)</option>
            </select>
          </label>

          <label>Difficulty
            <select id="difficulty">
              <option value="easy">Easy</option>
              <option value="medium" selected>Medium</option>
              <option value="hard">Hard</option>
            </select>
          </label>

          <label>Pipe Gap (px)
            <input type="range" id="gapRange" min="90" max="220" value="140"/>
            <div class="muted">Current gap: <span id="gapVal">140</span> px</div>
          </label>

          <label>Music Style
            <select id="musicStyle">
              <option value="citypop" selected>Japanese City-Pop (synth loop)</option>
              <option value="chill">Lo-fi Chill</option>
              <option value="none">None</option>
            </select>
          </label>

          <div style="margin-top:10px; display:flex; gap:8px;">
            <button id="applySettings" class="secondary">Apply</button>
            <button id="exportBtn" class="secondary">Export Best</button>
          </div>

          <div class="small">Controls: Space / Up = flap. Click/tap to flap. P = Pause.</div>
        </div>

        <div style="height:12px"></div>

        <div class="panel">
          <div style="font-weight:800">About</div>
          <div class="small">This build uses canvas pixel art and an internal WebAudio synth to create a short city-pop loop — no external files required. Toggle music or mute if browser blocks auto-play; interacting with the canvas will unlock audio.</div>
        </div>
      </div>
    </div>

    <footer>Built for you — press Start and enjoy the city-pop vibes ✨</footer>
  </div>

  <div id="overlay" class="overlay" style="display:none;">
    <div class="dialog" role="dialog" aria-modal="true">
      <h2 id="overlayTitle">Game Over</h2>
      <div id="overlayMsg" style="font-weight:900; font-size:20px; margin-top:8px;">Score: 0</div>
      <div class="small">Best: <span id="overlayBest">0</span></div>
      <div style="margin-top:12px;">
        <button id="overlayPlay">Play Again</button>
        <button id="overlayClose" class="secondary">Close</button>
      </div>
    </div>
  </div>

<script>
/* Flappy City-Pop — single file
   Pixel art + City-Pop synth loop + sfx + responsive + controls
*/

(() => {
  // Elements
  const canvas = document.getElementById('game');
  const ctx = canvas.getContext('2d');
  const startBtn = document.getElementById('startBtn');
  const replayBtn = document.getElementById('replayBtn');
  const muteBtn = document.getElementById('muteBtn');
  const scoreEl = document.getElementById('score');
  const bestEl = document.getElementById('best');
  const stateEl = document.getElementById('state');
  const overlay = document.getElementById('overlay');
  const overlayMsg = document.getElementById('overlayMsg');
  const overlayBest = document.getElementById('overlayBest');
  const overlayPlay = document.getElementById('overlayPlay');
  const overlayClose = document.getElementById('overlayClose');
  const pixelToggle = document.getElementById('pixelToggle');
  const difficultySelect = document.getElementById('difficulty');
  const gapRange = document.getElementById('gapRange');
  const gapVal = document.getElementById('gapVal');
  const applySettings = document.getElementById('applySettings');
  const musicStyle = document.getElementById('musicStyle');
  const exportBtn = document.getElementById('exportBtn');

  // Canvas sizing
  let baseW = 480, baseH = 640;
  function resizeCanvas() {
    const wrap = canvas.parentElement;
    const cssW = wrap.clientWidth;
    const cssH = Math.min(window.innerHeight - 160, 720);
    canvas.style.width = cssW + 'px';
    canvas.style.height = cssH + 'px';
    const ratio = window.devicePixelRatio || 1;
    const pixelMode = pixelToggle.value === '1';
    if (pixelMode) {
      const scale = Math.max(1, Math.floor(cssW / baseW));
      canvas.width = baseW * scale;
      canvas.height = Math.floor(baseH * (cssH / cssW) * scale);
      ctx.imageSmoothingEnabled = false;
    } else {
      canvas.width = Math.floor(cssW * ratio);
      canvas.height = Math.floor(cssH * ratio);
      ctx.imageSmoothingEnabled = true;
    }
  }
  window.addEventListener('resize', resizeCanvas);

  // Game config
  const CONFIG = {
    gravity: 1000,
    flapImpulse: -360,
    basePipeSpeed: 180,
    pipeWidth: 56,
    birdRadius: 12,
    groundHeight: 90,
    spawnSpacing: 220
  };

  gapVal.textContent = gapRange.value;
  gapRange.addEventListener('input', ()=> gapVal.textContent = gapRange.value );

  // State
  let running = false, gameOverFlag = false, lastTS = null;
  let bird = { x: 120, y: 240, vy: 0, rot: 0, radius: CONFIG.birdRadius };
  let pipes = [], spawnTimer = 0, score = 0, best = Number(localStorage.getItem('flappy_citypop_best') || 0), pipesPassed = 0;
  bestEl.textContent = best;
  scoreEl.textContent = 0;

  // Audio
  const AudioContext = window.AudioContext || window.webkitAudioContext;
  const audioCtx = AudioContext ? new AudioContext() : null;
  let audioOn = true;
  let musicPlaying = false;
  muteBtn.addEventListener('click', () => {
    audioOn = !audioOn;
    muteBtn.textContent = audioOn ? 'Mute' : 'Unmute';
    if (!audioOn) stopMusic();
  });

  // SFX
  function sfx(type) {
    if (!audioOn || !audioCtx) return;
    const t0 = audioCtx.currentTime;
    if (type === 'flap') {
      const o = audioCtx.createOscillator(), g = audioCtx.createGain();
      o.type = 'sine'; o.frequency.setValueAtTime(720, t0);
      g.gain.setValueAtTime(0.12, t0); g.gain.exponentialRampToValueAtTime(0.001, t0 + 0.12);
      o.connect(g); g.connect(audioCtx.destination); o.start(t0); o.stop(t0 + 0.12);
    } else if (type === 'score') {
      const o = audioCtx.createOscillator(), g = audioCtx.createGain();
      o.type = 'triangle'; o.frequency.setValueAtTime(880, t0); o.frequency.exponentialRampToValueAtTime(1320, t0 + 0.08);
      g.gain.setValueAtTime(0.12, t0); g.gain.exponentialRampToValueAtTime(0.001, t0 + 0.16);
      o.connect(g); g.connect(audioCtx.destination); o.start(t0); o.stop(t0 + 0.16);
    } else if (type === 'hit') {
      const o1 = audioCtx.createOscillator(), g = audioCtx.createGain();
      o1.type = 'sawtooth'; o1.frequency.setValueAtTime(240, t0);
      g.gain.setValueAtTime(0.2, t0); g.gain.exponentialRampToValueAtTime(0.001, t0 + 0.4);
      o1.connect(g); g.connect(audioCtx.destination); o1.start(t0); o1.stop(t0 + 0.38);
    }
  }

  // City-Pop style music engine
  let musicNodes = null;
  function startMusic(style='citypop') {
    if (!audioOn || !audioCtx || musicPlaying) return;
    if (audioCtx.state === 'suspended') audioCtx.resume();
    if (style === 'none') return;
    const t0 = audioCtx.currentTime + 0.05;
    const loopLength = 2.0;
    const master = audioCtx.createGain(); master.gain.value = 0.55; master.connect(audioCtx.destination);

    const pad = audioCtx.createOscillator(); const padGain = audioCtx.createGain();
    pad.type = 'sine'; pad.frequency.value = 200; padGain.gain.value = 0.08;
    pad.connect(padGain); padGain.connect(master); pad.start(t0);

    const eGain = audioCtx.createGain(); eGain.gain.value = 0.0; eGain.connect(master);
    const chordNotes = [
      [440, 554.37, 660],
      [392, 494, 622.25],
      [349.23, 440, 523.25],
      [392, 494, 622.25]
    ];
    let chordIndex = 0;
    function scheduleChords(start) {
      for (let i=0;i<4;i++){
        const when = start + i*loopLength;
        const notes = chordNotes[(chordIndex + i) % chordNotes.length];
        for (let n of notes) {
          const o = audioCtx.createOscillator();
          const g = audioCtx.createGain();
          o.type = 'sawtooth';
          o.frequency.setValueAtTime(n, when);
          g.gain.setValueAtTime(0.0, when);
          g.gain.linearRampToValueAtTime(0.09, when + 0.04);
          g.gain.linearRampToValueAtTime(0.02, when + loopLength - 0.12);
          g.gain.linearRampToValueAtTime(0.0, when + loopLength);
          o.connect(g); g.connect(eGain);
          o.start(when); o.stop(when + loopLength);
        }
      }
      chordIndex = (chordIndex + 4) % chordNotes.length;
    }

    const bassGain = audioCtx.createGain(); bassGain.gain.value = 0.0; bassGain.connect(master);
    function scheduleBass(start) {
      const pattern = [110, 0, 98, 0];
      for (let i=0;i<4;i++){
        const when = start + i*loopLength;
        const freq = pattern[i % pattern.length] || 0;
        if (freq > 0) {
          const o = audioCtx.createOscillator(); const g = audioCtx.createGain();
          o.type = 'triangle'; o.frequency.setValueAtTime(freq, when);
          g.gain.setValueAtTime(0.0, when); g.gain.linearRampToValueAtTime(0.16, when + 0.02);
          g.gain.exponentialRampToValueAtTime(0.01, when + loopLength - 0.05);
          o.connect(g); g.connect(bassGain); o.start(when); o.stop(when + loopLength);
        }
      }
    }

    const drumGain = audioCtx.createGain(); drumGain.gain.value = 0.9; drumGain.connect(master);
    function scheduleDrums(start) {
      const ko = audioCtx.createOscillator(), kg = audioCtx.createGain();
      ko.type = 'sine'; ko.frequency.setValueAtTime(100, start);
      kg.gain.setValueAtTime(0.4, start); kg.gain.exponentialRampToValueAtTime(0.001, start + 0.18);
      ko.connect(kg); kg.connect(drumGain); ko.start(start); ko.stop(start + 0.18);

      const bufferSize = audioCtx.sampleRate * 0.05;
      const noiseBuffer = audioCtx.createBuffer(1, bufferSize, audioCtx.sampleRate);
      const data = noiseBuffer.getChannelData(0);
      for (let i=0;i<data.length;i++) data[i] = (Math.random()*2 -1) * Math.exp(-i / (audioCtx.sampleRate * 0.02));
      const nb = audioCtx.createBufferSource(); nb.buffer = noiseBuffer;
      const ng = audioCtx.createGain(); ng.gain.setValueAtTime(0.12, start + 0.2); ng.gain.exponentialRampToValueAtTime(0.001, start + 0.3);
      nb.connect(ng); ng.connect(drumGain); nb.start(start + 0.2); nb.stop(start + 0.3);
    }

    let loopStart = audioCtx.currentTime + 0.05;
    scheduleChords(loopStart); scheduleBass(loopStart); scheduleDrums(loopStart);
    const interval = setInterval(() => {
      loopStart += 4 * loopLength;
      scheduleChords(loopStart); scheduleBass(loopStart); scheduleDrums(loopStart);
    }, 4 * loopLength * 1000 - 60);

    musicNodes = { pad, interval, eGain, bassGain, drumGain };
    musicPlaying = true;
  }

  function stopMusic() {
    if (!musicPlaying || !audioCtx) return;
    if (musicNodes) {
      try { musicNodes.pad.stop(); } catch(e){}
      clearInterval(musicNodes.interval);
    }
    musicNodes = null;
    musicPlaying = false;
  }

  // Game functions
  function resetGame() {
    bird = { x: 120, y: Math.max(120, canvas.height/3), vy: 0, rot: 0, radius: CONFIG.birdRadius };
    pipes = []; spawnTimer = 0; score = 0; pipesPassed = 0;
    scoreEl.textContent = '0';
    stateEl.textContent = 'Press Space / Tap to play';
    gameOverFlag = false; running = false; lastTS = null;
  }

  function setDifficulty(diff) {
    if (diff === 'easy') {
      CONFIG.basePipeSpeed = 150;
      gapRange.value = Math.max(120, Number(gapRange.value));
    } else if (diff === 'medium') {
      CONFIG.basePipeSpeed = 190;
    } else if (diff === 'hard') {
      CONFIG.basePipeSpeed = 230;
      gapRange.value = Math.max(110, Number(gapRange.value)-10);
    }
    gapVal.textContent = gapRange.value;
  }

  setDifficulty(difficultySelect.value);

  function startGame() {
    if (audioCtx && audioCtx.state === 'suspended') audioCtx.resume();
    if (musicStyle.value !== 'none') startMusic(musicStyle.value);
    resetGame();
    running = true;
    lastTS = performance.now();
    spawnPipe(canvas.width + 120);
    requestAnimationFrame(loop);
  }

  function spawnPipe(offset=0) {
    const gap = Number(gapRange.value);
    const minTop = 40;
    const maxTop = canvas.height - CONFIG.groundHeight - gap - 40;
    const gapY = Math.floor(Math.random() * (Math.max(0, maxTop - minTop + 1)) + minTop);
    const x = canvas.width + offset;
    pipes.push({ x, gapY, gap, width: CONFIG.pipeWidth, scored: false });
  }

  function flap() {
    if (!running) startGame();
    if (gameOverFlag) return;
    bird.vy = CONFIG.flapImpulse;
    bird.rot = -0.7;
    sfx('flap');
  }

  function circleRectCollision(cx, cy, r, rx, ry, rw, rh) {
    const closestX = Math.max(rx, Math.min(cx, rx + rw));
    const closestY = Math.max(ry, Math.min(cy, ry + rh));
    const dx = cx - closestX, dy = cy - closestY;
    return (dx*dx + dy*dy) <= r*r;
  }

  function checkCollision() {
    const groundY = canvas.height - CONFIG.groundHeight;
    if (bird.y + bird.radius > groundY) return true;
    if (bird.y - bird.radius < 0) return true;
    for (let p of pipes) {
      if (circleRectCollision(bird.x, bird.y, bird.radius, p.x, 0, p.width, p.gapY)) return true;
      if (circleRectCollision(bird.x, bird.y, bird.radius, p.x, p.gapY + p.gap, p.width, canvas.height - (p.gapY + p.gap))) return true;
    }
    return false;
  }

  function gameOver() {
    sfx('hit');
    gameOverFlag = true;
    running = false;
    if (score > best) { best = score; localStorage.setItem('flappy_citypop_best', String(best)); bestEl.textContent = best; }
    overlayMsg.textContent = 'Score: ' + score;
    overlayBest.textContent = best;
    overlay.style.display = 'flex';
    stateEl.textContent = 'Game Over';
    stopMusic();
  }

  function update(dt) {
    if (!running || gameOverFlag) return;
    bird.vy += CONFIG.gravity * dt;
    bird.y += bird.vy * dt;
    bird.rot = Math.max(-0.9, Math.min(1.3, bird.rot + bird.vy * 0.0015));

    spawnTimer += dt;
    const speed = CONFIG.basePipeSpeed + Math.floor(pipesPassed / 8) * 20;
    const spawnInterval = CONFIG.spawnSpacing / speed;
    if (spawnTimer > spawnInterval) { spawnTimer = 0; spawnPipe(); }

    for (let i = pipes.length - 1; i >= 0; i--) {
      pipes[i].x -= speed * dt;
      if (!pipes[i].scored && pipes[i].x + pipes[i].width < bird.x) {
        pipes[i].scored = true;
        score += 1; pipesPassed++;
        scoreEl.textContent = score;
        sfx('score');
        if (score % 12 === 0) gapRange.value = Math.max(90, Number(gapRange.value) - 6);
        gapVal.textContent = gapRange.value;
      }
      if (pipes[i].x + pipes[i].width < -60) pipes.splice(i,1);
    }
    if (checkCollision()) gameOver();
  }

  function draw() {
    resizeCanvas();
    const W = canvas.clientWidth, H = canvas.clientHeight;
    const skyGrad = ctx.createLinearGradient(0, 0, 0, H);
    skyGrad.addColorStop(0, '#78c0ff'); skyGrad.addColorStop(0.6, '#9fe6ff'); skyGrad.addColorStop(1, '#dff9ff');
    ctx.fillStyle = skyGrad;
    ctx.fillRect(0,0,W,H);

    drawCloudLayer();

    for (let p of pipes) {
      drawPipe(p);
    }

    const groundY = H - CONFIG.groundHeight;
    ctx.fillStyle = '#7bbf4a';
    ctx.fillRect(0, groundY, W, CONFIG.groundHeight);
    ctx.fillStyle = '#6db23f';
    for (let i=0;i<Math.ceil(W/40);i++){
      ctx.fillRect(i*40 + ((Date.now()/120) % 40), groundY + 10, 20, 6);
    }

    drawBird();

    ctx.fillStyle = 'rgba(2,30,45,0.9)';
    ctx.font = '700 34px Inter, Arial';
    ctx.textAlign = 'center';
    ctx.fillText(score, W/2, 58);

    if (!running && !gameOverFlag) {
      ctx.font = '600 16px Inter, Arial';
      ctx.fillStyle = 'rgba(2,30,45,0.75)';
      ctx.fillText('Press Space / Tap to flap', W/2, H/2 + 48);
    }
  }

  function drawPipe(p) {
    const x = p.x, w = p.width, gapY = p.gapY, gap = p.gap;
    ctx.fillStyle = '#1b9955';
    ctx.fillRect(x, 0, w, gapY);
    ctx.fillRect(x, gapY + gap, w, canvas.clientHeight - (gapY + gap) - CONFIG.groundHeight);
    ctx.fillStyle = '#148042';
    ctx.fillRect(x - 6, gapY - 6, w + 12, 12);
    ctx.fillRect(x - 6, gapY + gap - 6, w + 12, 12);
  }

  function drawCloudLayer() {
    const W = canvas.clientWidth, H = canvas.clientHeight;
    const t = Date.now()/1000;
    ctx.fillStyle = 'rgba(255,255,255,0.85)';
    for (let i=0;i<6;i++){
      const cx = (i*220 + (t*30) % (W+200)) - 100;
      const cy = 40 + (i%2)*30;
      drawCloud(cx, cy, 36 + (i%3)*10, 18 + (i%2)*6);
    }
  }
  function drawCloud(x,y,w,h) {
    ctx.beginPath();
    ctx.ellipse(x, y, w, h, 0, 0, Math.PI*2);
    ctx.ellipse(x + w*0.6, y-4, w*0.8, h*0.8, 0, 0, Math.PI*2);
    ctx.ellipse(x - w*0.6, y-6, w*0.6, h*0.7, 0, 0, Math.PI*2);
    ctx.fill();
  }

  function drawBird() {
    const pixelMode = pixelToggle.value === '1' && ctx.imageSmoothingEnabled === false;
    if (pixelMode) {
      const off = document.createElement('canvas');
      const ow = 64, oh = 64;
      off.width = ow; off.height = oh;
      const octx = off.getContext('2d');
      octx.clearRect(0,0,ow,oh);
      const bx = ow/2, by = oh/2;
      octx.fillStyle = '#ffd166'; octx.beginPath(); octx.arc(bx,by,12,0,Math.PI*2); octx.fill();
      octx.fillStyle = '#ffb347'; octx.beginPath(); octx.ellipse(bx-3, by+3, 6, 4, 0.2, 0, Math.PI*2); octx.fill();
      octx.fillStyle = '#222'; octx.beginPath(); octx.arc(bx+5, by-5, 2.5, 0, Math.PI*2); octx.fill();
      octx.fillStyle = '#ff7b00'; octx.beginPath(); octx.moveTo(bx+12,by); octx.lineTo(bx+20, by-6); octx.lineTo(bx+20, by+6); octx.closePath(); octx.fill();
      const destW = 48, destH = 48;
      ctx.save();
      ctx.translate(bird.x, bird.y);
      ctx.rotate(bird.rot);
      ctx.imageSmoothingEnabled = false;
      ctx.drawImage(off, -destW/2, -destH/2, destW, destH);
      ctx.restore();
    } else {
      ctx.save();
      ctx.translate(bird.x, bird.y);
      ctx.rotate(bird.rot);
      ctx.fillStyle = '#ffd166'; ctx.beginPath(); ctx.arc(0,0,18,0,Math.PI*2); ctx.fill();
      ctx.fillStyle = '#ffb347'; ctx.beginPath(); ctx.ellipse(-4,6,10,6,0.2,0,Math.PI*2); ctx.fill();
      ctx.fillStyle = '#222'; ctx.beginPath(); ctx.arc(6,-6,4,0,Math.PI*2); ctx.fill();
      ctx.fillStyle = '#ff7b00'; ctx.beginPath();
      ctx.moveTo(18,0); ctx.lineTo(28,-8); ctx.lineTo(28,8); ctx.closePath(); ctx.fill();
      ctx.restore();
    }
  }

  function loop(ts) {
    if (!lastTS) lastTS = ts;
    const dt = Math.min(0.033, (ts - lastTS) / 1000);
    lastTS = ts;
    update(dt);
    draw();
    if (!gameOverFlag) requestAnimationFrame(loop);
  }

  window.addEventListener('keydown', (e) => {
    if (e.code === 'Space' || e.code === 'ArrowUp') { e.preventDefault(); flap(); }
    if (e.code === 'KeyP') {
      if (!gameOverFlag) {
        running = !running;
        if (running) { lastTS = performance.now(); requestAnimationFrame(loop); stateEl.textContent = 'Resumed'; }
        else stateEl.textContent = 'Paused';
      }
    }
  });
  canvas.addEventListener('click', (e) => { flap(); });
  canvas.addEventListener('touchstart', (e) => { e.preventDefault(); flap(); }, { passive:false });

  startBtn.addEventListener('click', () => { startGame(); overlay.style.display = 'none'; });
  replayBtn.addEventListener('click', () => { startGame(); overlay.style.display = 'none'; });
  overlayPlay.addEventListener('click', () => { overlay.style.display = 'none'; startGame(); });
  overlayClose.addEventListener('click', () => { overlay.style.display = 'none'; });

  applySettings.addEventListener('click', () => {
    setDifficulty(difficultySelect.value);
    stopMusic();
    if (audioOn && musicStyle.value !== 'none') startMusic(musicStyle.value);
    stateEl.textContent = 'Settings applied';
    setTimeout(()=> stateEl.textContent = 'Press Space / Tap to play', 1200);
  });

  exportBtn.addEventListener('click', () => {
    const payload = { best, date: new Date().toISOString(), notes: 'Flappy CityPop best score export' };
    const blob = new Blob([JSON.stringify(payload, null, 2)], { type: 'application/json' });
    const url = URL.createObjectURL(blob);
    const a = document.createElement('a'); a.href = url; a.download = 'flappy-citypop-best.json'; a.click();
    URL.revokeObjectURL(url);
  });

  gapRange.addEventListener('change', () => { gapVal.textContent = gapRange.value; });

  resizeCanvas();
  resetGame();
  draw();

  function initPipesForDemo() {
    pipes = [];
    spawnPipe(80);
    spawnPipe(320);
  }
  initPipesForDemo();

  window.__flappyCitypop = { startGame, resetGame, flap };

})();
</script>
</body>
</html>