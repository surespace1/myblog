---
title: 音乐空间
date: 2025-12-11 08:12:59
layout: page
comments: false
---

<style>
  :root {
    --bg-color: #ffffff;
    --text-primary: #1d1d1f;
    --text-secondary: #86868b;
    --accent-gradient: linear-gradient(135deg, #007aff, #5856d6);
    --vinyl-size: 260px;
    --shadow-static: 0 10px 30px rgba(0,0,0,0.15);
    --shadow-active: 0 25px 50px rgba(88, 86, 214, 0.35); /* 播放时的彩色投影 */
  }

  /* --- 容器：纯白极简 --- */
  .music-page-container {
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 60px 20px;
    font-family: -apple-system, BlinkMacSystemFont, "SF Pro Display", "Segoe UI", Roboto, sans-serif;
    max-width: 600px;
    margin: 0 auto;
    background-color: var(--bg-color);
    /* 移除边框和背景色，融入页面 */
  }

  /* --- 1. 黑胶唱片 (超写实物理质感) --- */
  .vinyl-wrapper {
    position: relative;
    width: var(--vinyl-size);
    height: var(--vinyl-size);
    margin-bottom: 50px;
    cursor: pointer;
    z-index: 10;
    transition: transform 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
  }

  .vinyl-wrapper:active {
    transform: scale(0.97);
  }

  /* 唱片本体 */
  .vinyl-disc {
    width: 100%;
    height: 100%;
    border-radius: 50%;
    background: #111;
    /* 模拟黑胶的微细沟槽纹理 */
    background-image: repeating-radial-gradient(
      #111 0, 
      #111 2px, 
      #1a1a1a 3px, 
      #1a1a1a 4px
    );
    position: relative;
    /* 默认状态的投影：干净、深邃 */
    box-shadow: var(--shadow-static);
    transition: box-shadow 0.6s ease;
    animation: spin 8s linear infinite;
    animation-play-state: paused;
  }

  /* 唱片的高光反射 (物理光泽) - 关键点 */
  .vinyl-disc::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0; bottom: 0;
    border-radius: 50%;
    /* 使用锥形渐变模拟各向异性反光 */
    background: conic-gradient(
      from 45deg,
      rgba(255,255,255,0) 0%,
      rgba(255,255,255,0.15) 20%,
      rgba(255,255,255,0) 40%,
      rgba(255,255,255,0) 50%,
      rgba(255,255,255,0.1) 70%,
      rgba(255,255,255,0) 90%
    );
    pointer-events: none;
    z-index: 2;
  }

  /* 封面贴图区 */
  .vinyl-disc::after {
    content: '';
    position: absolute;
    top: 50%; left: 50%;
    transform: translate(-50%, -50%);
    width: 42%; height: 42%;
    background: url('/music/cover.jpg') no-repeat center center;
    background-size: cover;
    border-radius: 50%;
    /* 封面边缘的细节处理 */
    border: 6px solid #1a1a1a;
    box-shadow: inset 0 0 15px rgba(0,0,0,0.5); 
    z-index: 3;
  }

  /* 播放时的动态效果 */
  .vinyl-disc.playing {
    animation-play-state: running;
    /* 播放时：阴影变大，且带有一点高级的蓝紫色漫射光 */
    box-shadow: var(--shadow-active);
  }

  @keyframes spin {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
  }

  /* --- 2. 控制区与排版 --- */
  .controls-area {
    width: 100%;
    text-align: center;
    position: relative;
    z-index: 20;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  /* 动态可视化声波 */
  .visualizer {
    display: flex;
    align-items: flex-end;
    justify-content: center;
    height: 24px;
    gap: 5px;
    margin-bottom: 20px;
  }
  
  .bar {
    width: 5px;
    background: var(--text-secondary); /* 默认灰色 */
    border-radius: 10px;
    transition: all 0.3s;
    height: 4px; /* 默认静止 */
  }

  /* 播放时的声波动画 */
  .visualizer.active .bar {
    /* 激活时变成炫酷渐变色 */
    background: var(--accent-gradient);
    animation: bounce 1s infinite ease-in-out;
  }
  .bar:nth-child(1) { animation-delay: 0.0s; }
  .bar:nth-child(2) { animation-delay: 0.2s; }
  .bar:nth-child(3) { animation-delay: 0.4s; }
  .bar:nth-child(4) { animation-delay: 0.1s; }
  .bar:nth-child(5) { animation-delay: 0.3s; }

  @keyframes bounce {
    0%, 100% { height: 6px; }
    50% { height: 24px; }
  }

  /* 歌名设计 */
  .song-title {
    font-size: 2rem;
    font-weight: 700;
    color: var(--text-primary);
    margin: 0 0 8px 0;
    letter-spacing: -0.5px;
    /* 简单的入场动画 */
    transition: opacity 0.3s;
  }
  
  .status-text {
    font-size: 0.9rem;
    color: var(--text-secondary);
    margin-bottom: 40px;
    font-weight: 500;
    letter-spacing: 0.5px;
    text-transform: uppercase;
  }

  /* 按钮组 */
  .btn-group {
    display: flex;
    align-items: center;
    gap: 30px;
  }

  /* 通用按钮样式 */
  .btn {
    border: none;
    outline: none;
    cursor: pointer;
    transition: all 0.2s cubic-bezier(0.25, 0.46, 0.45, 0.94);
    display: flex;
    align-items: center;
    justify-content: center;
  }

  /* 播放按钮 (圆形极简) */
  .btn-play {
    width: 64px;
    height: 64px;
    border-radius: 50%;
    background: #f0f0f0;
    color: var(--text-primary);
    font-size: 1.2rem;
    box-shadow: 0 5px 15px rgba(0,0,0,0.05);
  }
  .btn-play:hover {
    background: #e5e5e5;
    transform: scale(1.05);
  }

  /* 切歌按钮 (胶囊型，主色调) */
  .btn-next {
    padding: 14px 32px;
    border-radius: 40px;
    background: var(--text-primary); /* 深黑背景 */
    color: #fff;
    font-size: 1rem;
    font-weight: 600;
    box-shadow: 0 10px 20px rgba(0,0,0,0.15);
  }
  .btn-next:hover {
    transform: translateY(-2px);
    box-shadow: 0 15px 30px rgba(0,0,0,0.25);
    /* 悬停时出现微妙的彩色光晕 */
    background: var(--accent-gradient);
  }
  .btn-next:active {
    transform: scale(0.95);
  }

</style>

<div class="music-page-container">

  <!-- 唱片 -->
  <div class="vinyl-wrapper" onclick="togglePlayState()">
    <div id="vinyl" class="vinyl-disc"></div>
  </div>

  <div class="controls-area">
    <!-- 极简声波 -->
    <div id="visualizer" class="visualizer">
      <div class="bar"></div><div class="bar"></div><div class="bar"></div>
      <div class="bar"></div><div class="bar"></div>
    </div>
    <!-- 信息 -->
    <div id="song-title" class="song-title">Music Space</div>
    <div id="status-text" class="status-text">Ready to play</div>
    <!-- 按钮 -->
    <div class="btn-group">
      <!-- 播放暂停 -->
      <button class="btn btn-play" onclick="togglePlayState()" title="播放/暂停">
        <span id="play-icon">▶</span>
      </button>
      <!-- 切歌 -->
      <button class="btn btn-next" onclick="nextRandomSong()">
        Random Track
      </button>
    </div>
  </div>

</div>

<script>
  // ================= 配置区域 =================
  var myPlaylist = [
    { title: "FallinFlower", url: "/music/FallinFlower.mp3" },
    { title: "遇见", url: "/music/遇见.mp3" },
    { title: "温柔", url: "/music/温柔.mp3" },
    { title: "我怀念的", url: "/music/我怀念的.mp3" },
  ];
  // ===========================================

  var audio = new Audio();
  var vinyl = document.getElementById('vinyl');
  var titleDom = document.getElementById('song-title');
  var statusDom = document.getElementById('status-text');
  var playIcon = document.getElementById('play-icon');
  var vizDom = document.getElementById('visualizer');
  
  var isPlaying = false;
  var currentIndex = -1;

  function nextRandomSong() {
    var randomIndex = Math.floor(Math.random() * myPlaylist.length);
    if (myPlaylist.length > 1 && randomIndex === currentIndex) {
      nextRandomSong();
      return;
    }
    currentIndex = randomIndex;
    var song = myPlaylist[currentIndex];

    // 简单的文字淡入淡出效果
    titleDom.style.opacity = 0;
    setTimeout(() => {
        titleDom.innerText = song.title;
        titleDom.style.opacity = 1;
    }, 200);

    audio.src = song.url;
    audio.load();
    statusDom.innerText = "Loading...";
    
    tryPlay();
  }

  function tryPlay() {
    var playPromise = audio.play();
    if (playPromise !== undefined) {
      playPromise.then(_ => { setPlayingUI(); })
      .catch(error => {
        console.warn("Autoplay blocked");
        setPausedUI();
        statusDom.innerText = "Click to Play";
      });
    }
  }

  function togglePlayState() {
    if (!audio.src) { nextRandomSong(); return; }
    if (isPlaying) { audio.pause(); setPausedUI(); } 
    else { tryPlay(); }
  }

  function setPlayingUI() {
    isPlaying = true;
    vinyl.classList.add('playing');
    vizDom.classList.add('active'); // 激活声波
    playIcon.innerText = "||";
    playIcon.style.marginLeft = "0"; // 修正暂停图标位置
    statusDom.innerText = "Now Playing";
    statusDom.style.color = "#007aff";
  }

  function setPausedUI() {
    isPlaying = false;
    vinyl.classList.remove('playing');
    vizDom.classList.remove('active'); // 停止声波
    playIcon.innerText = "▶";
    playIcon.style.marginLeft = "4px"; // 修正播放图标视觉中心
    statusDom.innerText = "Paused";
    statusDom.style.color = "#86868b";
  }

  audio.addEventListener('ended', function() { nextRandomSong(); });

  setTimeout(function() {
    if (myPlaylist.length > 0) nextRandomSong();
    else titleDom.innerText = "Playlist Empty";
  }, 200);
</script>
