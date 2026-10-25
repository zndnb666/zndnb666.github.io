<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">
<title>尊者 · 高级游戏厅</title>
<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:"Microsoft Yahei",system-ui,sans-serif}
html,body{min-height:100vh;overflow-x:hidden}
body{
  background:
    radial-gradient(ellipse at 15% 15%, rgba(255,225,245,0.65) 0%, transparent 55%),
    radial-gradient(ellipse at 85% 20%, rgba(215,235,255,0.6) 0%, transparent 50%),
    radial-gradient(ellipse at 45% 75%, rgba(230,220,255,0.5) 0%, transparent 55%),
    radial-gradient(ellipse at 5% 85%, rgba(220,248,255,0.55) 0%, transparent 50%),
    radial-gradient(ellipse at 95% 65%, rgba(255,240,225,0.5) 0%, transparent 50%),
    #fafbff;
  background-attachment:fixed;
  position:relative;
}
#snowLayer{position:fixed;inset:0;z-index:10000;pointer-events:none;overflow:hidden}
.flake{
  position:absolute;top:-12px;border-radius:50%;
  background:radial-gradient(circle at 35% 35%, #4a1a6b, #12061f);
  box-shadow:0 0 7px rgba(70,15,110,0.55);
  animation:flakeFall linear infinite;will-change:transform;
}
@keyframes flakeFall{
  0%{transform:translateY(-10vh) translateX(0) rotate(0deg);opacity:0.9}
  100%{transform:translateY(112vh) translateX(55px) rotate(220deg);opacity:0.25}
}
#gamePage{position:relative;z-index:1;padding:36px 22px 90px;max-width:1180px;margin:0 auto}
.hero{text-align:center;margin-bottom:36px}
.welcome{display:block;font-size:42px;font-weight:600;color:#000;letter-spacing:4px;line-height:1.1;margin-bottom:2px}
.title-row{display:flex;align-items:baseline;justify-content:center;gap:10px}
.page-title{font-size:56px;font-weight:900;color:#000;letter-spacing:8px;line-height:1.1;margin:0}
.site-label{font-size:28px;font-weight:700;color:#000;letter-spacing:4px}
.slogan{display:block;margin-top:12px;font-size:clamp(10px,2.6vw,16px);color:#000;font-weight:500;letter-spacing:1px;white-space:nowrap;line-height:1.4}.section-title{
  width:100%;display:flex;align-items:center;gap:12px;
  margin:46px 0 20px;padding:11px 20px;
  font-size:21px;font-weight:800;color:#12061f;
  border-left:6px solid #4a1a6b;
  background:rgba(255,255,255,0.6);
  backdrop-filter:blur(12px);
  border-radius:0 16px 16px 0;
  box-shadow:0 3px 16px rgba(70,15,110,0.06);
}
.section-title .sub{margin-left:auto;font-size:12px;font-weight:400;color:#6a5a8a}
.game-wrap{display:grid;grid-template-columns:repeat(2,1fr);gap:20px;width:100%}
.game-item{
  background:linear-gradient(150deg,rgba(255,255,255,0.94),rgba(246,242,255,0.9));
  border:2.5px solid #0a0a12;border-radius:18px;
  cursor:pointer;text-decoration:none;color:inherit;
  display:flex;flex-direction:column;min-height:138px;
  position:relative;overflow:hidden;
  transition:transform 0.3s cubic-bezier(0.25,0.46,0.45,0.94),box-shadow 0.3s,border-color 0.3s;
  box-shadow:0 4px 22px rgba(25,8,45,0.1),inset 0 0 0 1px rgba(255,255,255,0.65);
  backdrop-filter:blur(14px);
}
.game-item::after{
  content:'';position:absolute;inset:0;pointer-events:none;
  background:radial-gradient(circle at 15% 0%,rgba(170,130,255,0.12),transparent 55%);
}
.game-item:hover{
  transform:translateY(-5px) scale(1.012);
  border-color:#4a1a6b;
  box-shadow:0 16px 42px rgba(50,15,90,0.2),0 0 0 1px rgba(70,25,110,0.25),inset 0 0 0 1px rgba(255,255,255,0.85);
}
.game-item .inner{padding:17px 17px 14px;display:flex;flex-direction:column;height:100%;position:relative;z-index:1}
.game-icon{font-size:32px;line-height:1;margin-bottom:7px;display:flex;align-items:center;gap:8px}
.icon-badge{font-size:10px;font-weight:700;padding:2px 8px;border-radius:6px;background:#0a0a12;color:#ddd0ff;letter-spacing:0.4px}
.game-name{font-size:16.5px;font-weight:800;color:#0a0a12;margin-bottom:4px;letter-spacing:0.3px}
.game-desc{font-size:12px;color:#54446e;line-height:1.5;flex:1}.tags{display:flex;flex-wrap:wrap;gap:5px;margin-top:9px}
.tag{font-size:10px;padding:2px 8px;border-radius:20px;border:1px solid #0a0a12;color:#0a0a12;font-weight:600;background:rgba(255,255,255,0.45)}
.tag.hot{background:#0a0a12;color:#fff}
.tag.green{border-color:#1a6b3a;color:#1a6b3a}
.tag.purple{border-color:#4a1a6b;color:#4a1a6b}
.game-modal{display:none;position:fixed;inset:0;z-index:9998;background:rgba(8,4,18,0.85);backdrop-filter:blur(8px);align-items:center;justify-content:center;padding:18px}
.game-modal.open{display:flex}
.board{background:linear-gradient(160deg,#110d1d,#1a1028);border:2px solid rgba(130,90,210,0.38);border-radius:20px;padding:22px;max-width:580px;width:100%;max-height:92vh;overflow:auto;text-align:center;position:relative;box-shadow:0 0 65px rgba(70,25,150,0.3)}
.close-btn{position:absolute;top:9px;right:15px;font-size:29px;color:#bfaee0;cursor:pointer;background:none;border:none;line-height:1;transition:0.2s}
.close-btn:hover{color:#ff78f0;transform:rotate(90deg)}
.board h2{color:#e2d2ff;font-size:21px;margin-bottom:11px}
.board canvas{background:#0a0618;border-radius:12px;display:block;margin:0 auto 11px;max-width:100%;height:auto;border:1px solid rgba(110,70,190,0.28)}
.info{color:#a294c8;font-size:13.5px;margin:5px 0}
.restart-btn{background:linear-gradient(135deg,#4a1a6b,#8a4aff);color:#fff;border:none;padding:10px 23px;border-radius:10px;font-size:14.5px;cursor:pointer;margin:6px 3px;transition:0.2s;font-weight:600}
.restart-btn:hover{filter:brightness(1.18);transform:translateY(-1px)}
.restart-btn:active{transform:scale(0.97)}
</style>
</head>
<body>
<div id="snowLayer"></div>
<div id="gamePage">
  <div class="hero">
    <span class="welcome">welcome to</span>
    <div class="title-row">
      <h1 class="page-title">尊者</h1>
      <span class="site-label">的网站</span>
    </div>
    <p class="slogan">让网页不再是单一的内容，而是让每个享受到丰富的乐趣。</p>
  </div><div class="section-title">🎮 内置游戏 <span class="sub">纯前端 · 断网可玩 · 9 款</span></div>
<div class="game-wrap">
  <div class="game-item" data-game="snake">
    <div class="inner">
      <div class="game-icon">🐍 <span class="icon-badge">经典</span></div>
      <span class="game-name">贪吃蛇</span>
      <div class="game-desc">方向键 / WASD / 滑动操控，吃食物变长，别撞墙。</div>
      <div class="tags"><span class="tag hot">内置</span><span class="tag">键盘/触屏</span></div>
    </div>
  </div>
  <div class="game-item" data-game="tetris">
    <div class="inner">
      <div class="game-icon">🧱 <span class="icon-badge">消除</span></div>
      <span class="game-name">俄罗斯方块</span>
      <div class="game-desc">←→移动，↑旋转，↓加速。堆满一行即可消除。</div>
      <div class="tags"><span class="tag hot">内置</span><span class="tag">键盘</span></div>
    </div>
  </div>
  <div class="game-item" data-game="g2048">
    <div class="inner">
      <div class="game-icon">🔢 <span class="icon-badge">数字</span></div>
      <span class="game-name">2048</span>
      <div class="game-desc">滑动合并相同数字，挑战合成 2048 方块。</div>
      <div class="tags"><span class="tag hot">内置</span><span class="tag">键盘/触屏</span></div>
    </div>
  </div>
  <div class="game-item" data-game="minesweeper">
    <div class="inner">
      <div class="game-icon">💣 <span class="icon-badge">益智</span></div>
      <span class="game-name">扫雷</span>
      <div class="game-desc">左键翻开，右键插旗。避开所有地雷即可获胜。</div>
      <div class="tags"><span class="tag hot">内置</span><span class="tag">鼠标</span></div>
    </div>
  </div><div class="game-item" data-game="memory">
    <div class="inner">
      <div class="game-icon">🃏 <span class="icon-badge">记忆</span></div>
      <span class="game-name">记忆翻牌</span>
      <div class="game-desc">翻开卡片记住图案位置，配对全部相同图案。</div>
      <div class="tags"><span class="tag hot">内置</span><span class="tag">鼠标/触屏</span></div>
    </div>
  </div>
  <div class="game-item" data-game="rps">
    <div class="inner">
      <div class="game-icon">✊ <span class="icon-badge">对战</span></div>
      <span class="game-name">石头剪刀布</span>
      <div class="game-desc">和电脑猜拳，简单解压，连赢有惊喜。</div>
      <div class="tags"><span class="tag hot">内置</span><span class="tag">点击</span></div>
    </div>
  </div>
  <div class="game-item" data-game="breakout">
    <div class="inner">
      <div class="game-icon">🏓 <span class="icon-badge">街机</span></div>
      <span class="game-name">打砖块</span>
      <div class="game-desc">移动挡板反弹小球，击碎所有砖块过关。</div>
      <div class="tags"><span class="tag hot">内置</span><span class="tag">键盘</span></div>
    </div>
  </div>
  <div class="game-item" data-game="flappy">
    <div class="inner">
      <div class="game-icon">🐦 <span class="icon-badge">反应</span></div>
      <span class="game-name">Flappy Bird</span>
      <div class="game-desc">点击 / 空格扇动翅膀，穿过管道缝隙。</div>
      <div class="tags"><span class="tag hot">内置</span><span class="tag">点击/空格</span></div>
    </div>
  </div>
  <div class="game-item" data-game="gomoku">
    <div class="inner">
      <div class="game-icon">⚫ <span class="icon-badge">棋类</span></div>
      <span class="game-name">五子棋（人机）</span>
      <div class="game-desc">15×15 棋盘，你先落黑子，五连即胜。</div>
      <div class="tags"><span class="tag hot">内置</span><span class="tag">鼠标/触屏</span></div>
    </div>
  </div>
</div><div class="section-title">🕹️ 经典外链 <span class="sub">免登录 · 新标签打开</span></div>
<div class="game-wrap">
  <a class="game-item" href="https://52tool.net/tools/game/snake" target="_blank" rel="noopener">
    <div class="inner">
      <div class="game-icon">🐍 <span class="icon-badge">经典</span></div>
      <span class="game-name">贪吃蛇·外链</span>
      <div class="game-desc">52tool 在线贪吃蛇，方向键 / WASD 控制。</div>
      <div class="tags"><span class="tag">免登录</span><span class="tag green">新标签</span></div>
    </div>
  </a>
  <a class="game-item" href="https://game.ur1.fun/tetris/" target="_blank" rel="noopener">
    <div class="inner">
      <div class="game-icon">🧱 <span class="icon-badge">消除</span></div>
      <span class="game-name">俄罗斯方块·外链</span>
      <div class="game-desc">轻量化在线俄罗斯方块，完整经典玩法。</div>
      <div class="tags"><span class="tag">免登录</span><span class="tag green">新标签</span></div>
    </div>
  </a>
  <a class="game-item" href="https://hi8.com/g/2048" target="_blank" rel="noopener">
    <div class="inner">
      <div class="game-icon">🔢 <span class="icon-badge">数字</span></div>
      <span class="game-name">2048·外链</span>
      <div class="game-desc">打开即玩，支持撤销、多种棋盘尺寸。</div>
      <div class="tags"><span class="tag">免登录</span><span class="tag green">新标签</span></div>
    </div>
  </a>
  <a class="game-item" href="https://www.saolei123.com/" target="_blank" rel="noopener">
    <div class="inner">
      <div class="game-icon">💣 <span class="icon-badge">益智</span></div>
      <span class="game-name">扫雷·外链</span>
      <div class="game-desc">经典扫雷网页版，首次点击安全，多难度。</div>
      <div class="tags"><span class="tag">免登录</span><span class="tag green">新标签</span></div>
    </div>
  </a><a class="game-item" href="https://www.ud5.com/tool/emoji-memory-game" target="_blank" rel="noopener">
    <div class="inner">
      <div class="game-icon">🃏 <span class="icon-badge">记忆</span></div>
      <span class="game-name">记忆翻牌·外链</span>
      <div class="game-desc">Emoji 记忆配对，三档难度，实时统计。</div>
      <div class="tags"><span class="tag">免登录</span><span class="tag green">新标签</span></div>
    </div>
  </a>
  <a class="game-item" href="https://ybboom.com/2026/10/19/original-fun-rock-paper-scissors-v100/" target="_blank" rel="noopener">
    <div class="inner">
      <div class="game-icon">✊ <span class="icon-badge">对战</span></div>
      <span class="game-name">石头剪刀布·外链</span>
      <div class="game-desc">与电脑随机猜拳，一局定胜负，零门槛。</div>
      <div class="tags"><span class="tag">免登录</span><span class="tag green">新标签</span></div>
    </div>
  </a>
  <a class="game-item" href="https://simplegames.io/breakout/" target="_blank" rel="noopener">
    <div class="inner">
      <div class="game-icon">🏓 <span class="icon-badge">街机</span></div>
      <span class="game-name">打砖块·外链</span>
      <div class="game-desc">Simplegames.io 经典 Breakout，无需注册。</div>
      <div class="tags"><span class="tag">免登录</span><span class="tag green">新标签</span></div>
    </div>
  </a>
  <a class="game-item" href="https://www.ud5.com/tool/flappy-bird-clone" target="_blank" rel="noopener">
    <div class="inner">
      <div class="game-icon">🐦 <span class="icon-badge">反应</span></div>
      <span class="game-name">Flappy·外链</span>
      <div class="game-desc">飞扬的小鸟网页版，点击或空格扇翅。</div>
      <div class="tags"><span class="tag">免登录</span><span class="tag green">新标签</span></div>
    </div>
  </a>
  <a class="game-item" href="https://hi8.com/g/gomoku" target="_blank" rel="noopener">
    <div class="inner">
      <div class="game-icon">⚫ <span class="icon-badge">棋类</span></div>
      <span class="game-name">五子棋·外链</span>
      <div class="game-desc">15×15 标准棋盘，五档 AI 难度。</div>
      <div class="tags"><span class="tag">免登录</span><span class="tag green">新标签</span></div>
    </div>
  </a>
</div><div class="section-title">🌐 免登录外链 <span class="sub">需联网 · 新标签打开</span></div>
<div class="game-wrap">
  <a class="game-item" href="https://pvz.wan1234.com/" target="_blank" rel="noopener">
    <div class="inner">
      <div class="game-icon">🌻 <span class="icon-badge">塔防</span></div>
      <span class="game-name">植物大战僵尸</span>
      <div class="game-desc">49 种植物 vs 26 类僵尸，经典塔防网页版。</div>
      <div class="tags"><span class="tag">免登录</span><span class="tag green">需联网</span></div>
    </div>
  </a>
  <a class="game-item" href="https://pvz.heheda.top/" target="_blank" rel="noopener">
    <div class="inner">
      <div class="game-icon">🧟 <span class="icon-badge">备用</span></div>
      <span class="game-name">PVZ 备用镜像</span>
      <div class="game-desc">植物大战僵尸备用地址，主站拥挤时使用。</div>
      <div class="tags"><span class="tag">免登录</span><span class="tag green">需联网</span></div>
    </div>
  </a>
  <a class="game-item" href="https://poki.com/zh" target="_blank" rel="noopener">
    <div class="inner">
      <div class="game-icon">🎮 <span class="icon-badge">海量</span></div>
      <span class="game-name">Poki 宝玩</span>
      <div class="game-desc">塔防、射击、休闲、双人，数千款免登录 H5。</div>
      <div class="tags"><span class="tag">免登录</span><span class="tag green">需联网</span></div>
    </div>
  </a>
  <a class="game-item" href="https://www.crazygames.com" target="_blank" rel="noopener">
    <div class="inner">
      <div class="game-icon">🕹️ <span class="icon-badge">4500+</span></div>
      <span class="game-name">CrazyGames</span>
      <div class="game-desc">io 对战、解谜、像素风，打开即玩。</div>
      <div class="tags"><span class="tag">免登录</span><span class="tag green">需联网</span></div>
    </div>
  </a>
  <a class="game-item" href="https://fc.wan1234.com" target="_blank" rel="noopener">
    <div class="inner">
      <div class="game-icon">👾 <span class="icon-badge">怀旧</span></div>
      <span class="game-name">红白机网页合集</span>
      <div class="game-desc">魂斗罗、马里奥、冒险岛，经典 FC 即点即玩。</div>
      <div class="tags"><span class="tag">免登录</span><span class="tag green">需联网</span></div>
    </div>
  </a>
  <a class="game-item" href="https://mcjs.cc/" target="_blank" rel="noopener">
    <div class="inner">
      <div class="game-icon">⛏️ <span class="icon-badge">沙盒</span></div>
      <span class="game-name">我的世界网页版</span>
      <div class="game-desc">纯免费 MC，支持单机与联机，打开即玩。</div>
      <div class="tags"><span class="tag">免登录</span><span class="tag green">需联网</span></div>
    </div>
  </a>
  </div><div class="section-title">🏆 大牌游戏 · 免登录直玩 <span class="sub">网页版 / 云游戏 · 点开即玩</span></div>
  <div class="game-wrap">
    <a class="game-item" href="https://ys.mihoyo.com/cloud/" target="_blank" rel="noopener">
      <div class="inner">
        <div class="game-icon">⛩️ <span class="icon-badge">开放世界</span></div>
        <span class="game-name">云·原神</span>
        <div class="game-desc">米哈游官方云游戏，浏览器秒玩提瓦特，无需下载 30G 客户端。</div>
        <div class="tags"><span class="tag">免登录</span><span class="tag purple">大牌IP</span></div>
      </div>
    </a>
    <a class="game-item" href="https://sr.mihoyo.com/cloud/" target="_blank" rel="noopener">
      <div class="inner">
        <div class="game-icon">🚂 <span class="icon-badge">回合制</span></div>
        <span class="game-name">云·崩坏：星穹铁道</span>
        <div class="game-desc">米哈游官方云版，网页直接上车，低配设备也能流畅跑图。</div>
        <div class="tags"><span class="tag">免登录</span><span class="tag purple">大牌IP</span></div>
      </div>
    </a>
    <a class="game-item" href="https://mc.kurogames.com/cloud/" target="_blank" rel="noopener">
      <div class="inner">
        <div class="game-icon">🌊 <span class="icon-badge">动作</span></div>
        <span class="game-name">云·鸣潮</span>
        <div class="game-desc">库洛官方云游戏，网页秒开，体验高速战斗。</div>
        <div class="tags"><span class="tag">免登录</span><span class="tag purple">大牌IP</span></div>
      </div>
    </a>
    <a class="game-item" href="https://dos.zone" target="_blank" rel="noopener">
      <div class="inner">
        <div class="game-icon">💾 <span class="icon-badge">怀旧神作</span></div>
        <span class="game-name">DOS.Zone</span>
        <div class="game-desc">上千款 90 年代大牌 PC 游戏在线玩：极品飞车、帝国时代、暴力摩托……</div>
        <div class="tags"><span class="tag">免登录</span><span class="tag">千款经典</span></div>
      </div>
    </a>
    <a class="game-item" href="https://cn.pigame.cc/" target="_blank" rel="noopener">
      <div class="inner">
        <div class="game-icon">🐷 <span class="icon-badge">云3A</span></div>
        <span class="game-name">小猪秒玩</span>
        <div class="game-desc">浏览器直接渲染 3A 大作与热门网游，3 秒启动。</div>
        <div class="tags"><span class="tag">免登录</span><span class="tag purple">3A/网游</span></div>
      </div>
    </a>
    <a class="game-item" href="https://www.suileyoo.com" target="_blank" rel="noopener">
      <div class="inner">
        <div class="game-icon">🖥️ <span class="icon-badge">网页版3A</span></div>
        <span class="game-name">随乐游云游戏</span>
        <div class="game-desc">网页秒开免下载，部分 3A 大作免账号试玩。</div>
        <div class="tags"><span class="tag">免登录</span><span class="tag purple">3A大作</span></div>
      </div>
    </a>
  </div>
</div>
<div class="game-modal" id="gameModal">
  <div class="board">
    <button class="close-btn" id="closeBtn">×</button>
    <div id="gameContent"></div>
  </div>
  </div><script>
(function(){
  var layer=document.getElementById('snowLayer');
  if(!layer)return;
  var N=160;
  for(var i=0;i<N;i++){
    var f=document.createElement('div');
    f.className='flake';
    var s=Math.random()*2.6+1.1;
    f.style.width=s+'px';f.style.height=s+'px';
    f.style.left=Math.random()*100+'vw';
    f.style.animationDuration=(Math.random()*13+9)+'s';
    f.style.animationDelay=(Math.random()*16)+'s';
    f.style.opacity=Math.random()*0.45+0.4;
    layer.appendChild(f);
  }
})();
var games={};
games.snake=function(){
  var wrap=document.getElementById('gameContent');
  wrap.innerHTML='<h2>🐍 贪吃蛇</h2><div class="info" id="snScore">得分：0　最高：0</div><canvas id="snCv" width="400" height="400"></canvas><div class="info">方向键 / WASD / 滑动</div><button type="button" class="restart-btn" onclick="games.snake()">重新开始</button>';
  var cv=document.getElementById('snCv'),ctx=cv.getContext('2d');
  var S=20,C=20,R=20;
  var snake,dir,food,score,timer,alive,best=+localStorage.getItem('snBest')||0;
  function reset(){
    snake=[{x:10,y:10},{x:9,y:10},{x:8,y:10}];dir={x:1,y:0};score=0;alive=true;
    document.getElementById('snScore').textContent='得分：0　最高：'+best;
    placeFood();draw();
    clearInterval(timer);timer=setInterval(loop,105);
  }function placeFood(){
  while(true){food={x:~~(Math.random()*C),y:~~(Math.random()*R)};
    if(!snake.some(function(s){return s.x===food.x&&s.y===food.y;}))break;}
}
function loop(){
  if(!alive)return;
  var h={x:snake[0].x+dir.x,y:snake[0].y+dir.y};
  if(h.x<0||h.y<0||h.x>=C||h.y>=R||snake.some(function(s){return s.x===h.x&&s.y===h.y;})){die();return;}
  snake.unshift(h);
  if(h.x===food.x&&h.y===food.y){
    score++;if(score>best){best=score;localStorage.setItem('snBest',best);}
    document.getElementById('snScore').textContent='得分：'+score+'　最高：'+best;placeFood();
  }else snake.pop();
  draw();
}
function die(){
  alive=false;clearInterval(timer);
  ctx.fillStyle='rgba(0,0,0,0.62)';ctx.fillRect(0,0,400,400);
  ctx.fillStyle='#fff';ctx.font='32px sans-serif';ctx.textAlign='center';
  ctx.fillText('Game Over',200,190);
  ctx.font='17px sans-serif';ctx.fillStyle='#ffe877';ctx.fillText('得分：'+score,200,228);
}
function draw(){
  ctx.fillStyle='#0a0620';ctx.fillRect(0,0,400,400);
  snake.forEach(function(s,i){ctx.globalAlpha=i===0?1:0.72;ctx.fillStyle='#ff78f0';ctx.fillRect(s.x*S,s.y*S,S-1,S-1);});
  ctx.globalAlpha=1;ctx.fillStyle='#5cff9d';ctx.fillRect(food.x*S,food.y*S,S-1,S-1);
    }var key=function(e){
    var k=e.key;
    if((k==='ArrowUp'||k==='w'||k==='W')&&dir.y!==1)dir={x:0,y:-1};
    else if((k==='ArrowDown'||k==='s'||k==='S')&&dir.y!==-1)dir={x:0,y:1};
    else if((k==='ArrowLeft'||k==='a'||k==='A')&&dir.x!==1)dir={x:-1,y:0};
    else if((k==='ArrowRight'||k==='d'||k==='D')&&dir.x!==-1)dir={x:1,y:0};
  };
  document.addEventListener('keydown',key);
  reset();
  return function(){clearInterval(timer);document.removeEventListener('keydown',key);};
};
games.tetris=function(){
  var wrap=document.getElementById('gameContent');
  wrap.innerHTML='<h2>🧱 俄罗斯方块</h2><div class="info" id="tetScore">得分：0　行数：0</div><canvas id="tetCv" width="240" height="480"></canvas><div class="info">←→移动 ↑旋转 ↓加速</div><button type="button" class="restart-btn" onclick="games.tetris()">重新开始</button>';
  var cv=document.getElementById('tetCv'),ctx=cv.getContext('2d');
  var COLS=12,ROWS=20,S=20;
  var SHAPES=[[[1,1,1,1]],[[1,1],[1,1]],[[0,1,0],[1,1,1]],[[1,0,0],[1,1,1]],[[0,0,1],[1,1,1]],[[0,1,1],[1,1,0]],[[1,1,0],[0,1,1]]];
  var board,piece,px,py,score,lines,timer,over,speed=600;
  function reset(){
    board=Array.from({length:ROWS},function(){return Array(COLS).fill(0);});
    score=0;lines=0;over=false;speed=600;
    document.getElementById('tetScore').textContent='得分：0　行数：0';
    newPiece();draw();
    clearInterval(timer);timer=setInterval(tick,speed);
  }function newPiece(){
  var t=~~(Math.random()*SHAPES.length);
  piece=SHAPES[t].map(function(r){return r.slice();});px=4;py=0;
  if(collide(px,py,piece)){over=true;gameOver();}
}
function collide(x,y,sh){
  for(var r=0;r<sh.length;r++)for(var c=0;c<sh[r].length;c++)if(sh[r][c]){
    var nx=x+c,ny=y+r;
    if(nx<0||nx>=COLS||ny>=ROWS)return true;
    if(ny>=0&&board[ny][nx])return true;
  }
  return false;
}
function merge(){piece.forEach(function(row,r){row.forEach(function(v,c){if(v)board[py+r][px+c]=1;});});}
function clearLines(){
  var cleared=0;
  for(var r=ROWS-1;r>=0;r--){
    if(board[r].every(function(v){return v;})){board.splice(r,1);board.unshift(Array(COLS).fill(0));cleared++;r++;}
  }
  if(cleared){
    lines+=cleared;score+=[0,100,300,500,800][cleared]||1000;
    document.getElementById('tetScore').textContent='得分：'+score+'　行数：'+lines;
    speed=Math.max(120,600-lines*30);clearInterval(timer);timer=setInterval(tick,speed);
  }
}
function tick(){
  if(over)return;
  if(!collide(px,py+1,piece)){py++;draw();return;}
  merge();clearLines();newPiece();draw();
}
function draw(){
  ctx.fillStyle='#0a0620';ctx.fillRect(0,0,240,480);
  for(var r=0;r<ROWS;r++)for(var c=0;c<COLS;c++)if(board[r][c]){
    ctx.fillStyle='#8a4aff';ctx.fillRect(c*S,r*S,S-1,S-1);
    ctx.fillStyle='rgba(255,255,255,0.14)';ctx.fillRect(c*S,r*S,S-1,4);
  }
  piece.forEach(function(row,r){row.forEach(function(v,c){if(v){
    ctx.fillStyle='#ff78f0';ctx.fillRect((px+c)*S,(py+r)*S,S-1,S-1);
    ctx.fillStyle='rgba(255,255,255,0.2)';ctx.fillRect((px+c)*S,(py+r)*S,S-1,4);
  }});});
    }
