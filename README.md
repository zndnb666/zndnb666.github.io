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

/* ===== 联系板块 ===== */
.contact{
  width:100%;
  margin-top:56px;
  padding:26px 20px;
  text-align:center;
  background:linear-gradient(150deg,rgba(255,255,255,0.94),rgba(246,242,255,0.9));
  border:2.5px solid #0a0a12;
  border-radius:18px;
  backdrop-filter:blur(14px);
  box-shadow:0 4px 22px rgba(25,8,45,0.1),inset 0 0 0 1px rgba(255,255,255,0.65);
}
.contact-line2{
  font-size:clamp(10px,2.6vw,16px);
  color:#808080;
  font-weight:500;
  letter-spacing:0.3px;
  line-height:1.6;
}

/* ===== 公告页 ===== */
#noticeOverlay{
  position:fixed;
  top:0;left:0;right:0;bottom:0;
  z-index:10001;
  display:flex;align-items:center;justify-content:center;
}
#noticePanel{
  position:absolute;
  top:20px;left:20px;right:20px;bottom:20px;
  background:#fff;
  border-radius:16px;
  box-shadow:0 0 50px rgba(0,0,0,0.25);
  display:flex;flex-direction:column;align-items:center;
  padding:28px 24px;
  overflow-y:auto;
  animation:noticeIn 0.7s cubic-bezier(0.22,1,0.36,1) forwards;
}
@keyframes noticeIn{
  from{transform:scale(0);opacity:0}
  to{transform:scale(1);opacity:1}
}
#noticeOverlay.closing #noticePanel{
  animation:noticeOut 0.5s cubic-bezier(0.5,0,0.75,0) forwards;
}
@keyframes noticeOut{
  from{transform:scale(1);opacity:1}
  to{transform:scale(0);opacity:0}
}
.notice-title{
  display:inline-block;
  border:2px solid #000;
  border-radius:6px;
  padding:6px 22px;
  font-size:11px;
  font-weight:700;
  color:#000;
  letter-spacing:3px;
  margin-bottom:28px;
  white-space:nowrap;
  background:#f5f5f5;
}
.notice-content{
  width:100%;
  max-width:640px;
  text-align:left;
  color:#000;
  font-size:16px;
  line-height:1.9;
}
.notice-content p{margin-bottom:14px}
.notice-content strong{font-weight:700}
#closeNotice{
  margin-top:28px;
  padding:10px 36px;
  background:#000;
  color:#fff;
  border:none;
  border-radius:8px;
  font-size:15px;
  cursor:pointer;
  transition:0.2s;
}
#closeNotice:hover{background:#333}
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
  <a class="game-item" href="https://66970010-boop.github.io/frog-miner/" target="_blank" rel="noopener">
    <div class="inner">
      <div class="game-icon">🐸 <span class="icon-badge">放置</span></div>
      <span class="game-name">奶蛙工厂</span>
      <div class="game-desc">GitHub Pages 原创放置小游戏，点击奶蛙积累资源、解锁升级，越点越上瘾。</div>
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
  <a class="game-item" href="https://playcsonline.com" target="_blank" rel="noopener">
    <div class="inner">
      <div class="game-icon">🔫 <span class="icon-badge">射击</span></div>
      <span class="game-name">Cs go</span>
      <div class="game-desc">网页版 CS 反恐精英，免登录直接开战，经典射击玩法。</div>
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

  <!-- ===== 联系方式 ===== -->
  <div class="contact">
    <div class="contact-line2">联系方式:网易邮箱:zndnbnb@163.com</div>
  </div>
</div>

<!-- ===== 公告页 ===== -->
<div id="noticeOverlay">
  <div id="noticePanel">
    <div class="notice-title">通知</div>
    <div class="notice-content">
      <p><strong>更新内容:</strong><br>1.本站新增:Cs go和奶蛙工厂</p>
      <p><strong>本站说明:</strong><br>本站上方所有游戏都免登录！免注册！点击即玩！<br>下方云游戏大多可以密码、邮箱登录，少量借助软件请见量！</p>
      <p><strong>本站初衷:</strong><br>让网页不再是单一的内容，而是让每个享受到丰富的乐趣。</p>
    </div>
    <button id="closeNotice">我知道了</button>
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
                                                                                                }function gameOver(){
    clearInterval(timer);
    ctx.fillStyle='rgba(0,0,0,0.62)';ctx.fillRect(0,0,240,480);
    ctx.fillStyle='#fff';ctx.font='26px sans-serif';ctx.textAlign='center';
    ctx.fillText('Game Over',120,218);ctx.font='15px sans-serif';ctx.fillStyle='#ffe877';
    ctx.fillText('得分：'+score,120,256);
  }
  var key=function(e){
    if(over)return;
    var k=e.key;
    if(k==='ArrowLeft'&&!collide(px-1,py,piece))px--;
    else if(k==='ArrowRight'&&!collide(px+1,py,piece))px++;
    else if(k==='ArrowDown'&&!collide(px,py+1,piece))py++;
    else if(k==='ArrowUp'||k===' '){
      var rot=piece[0].map(function(_,i){return piece.map(function(r){return r[i];}).reverse();});
      if(!collide(px,py,rot))piece=rot;
    }
    draw();
  };
  document.addEventListener('keydown',key);
  reset();
  return function(){clearInterval(timer);document.removeEventListener('keydown',key);};
};
games.g2048=function(){
  var wrap=document.getElementById('gameContent');
  wrap.innerHTML='<h2>🔢 2048</h2><div class="info" id="g2Score">分数：0　最高：0</div><div id="g2Grid" style="display:grid;grid-template-columns:repeat(4,1fr);gap:8px;max-width:340px;margin:0 auto;background:rgba(0,0,0,0.3);padding:10px;border-radius:12px;"></div><div class="info">方向键 / WASD / 滑动</div><button type="button" class="restart-btn" onclick="games.g2048()">重新开始</button>';
  var grid=document.getElementById('g2Grid');
  var board,score,best=+localStorage.getItem('g2Best')||0;
  function reset(){
    board=Array.from({length:4},function(){return Array(4).fill(0);});score=0;
    addTile();addTile();render();
    document.getElementById('g2Score').textContent='分数：0　最高：'+best;
  }function addTile(){
  var empty=[];
  for(var r=0;r<4;r++)for(var c=0;c<4;c++)if(board[r][c]===0)empty.push([r,c]);
  if(!empty.length)return;
  var rc=empty[~~(Math.random()*empty.length)];
  board[rc[0]][rc[1]]=Math.random()<0.9?2:4;
}
function render(){
  var colors={0:'rgba(255,255,255,0.06)',2:'#eee4da',4:'#ede0c8',8:'#f2b179',16:'#f59563',32:'#f67c5f',64:'#f65e3b',128:'#edcf72',256:'#edcc61',512:'#edc850',1024:'#edc53f',2048:'#edc22e'};
  grid.innerHTML='';
  for(var r=0;r<4;r++)for(var c=0;c<4;c++){
    var v=board[r][c],cell=document.createElement('div');
    cell.style.cssText='aspect-ratio:1;display:flex;align-items:center;justify-content:center;border-radius:8px;font-size:25px;font-weight:800;';
    cell.style.background=colors[v]||'#3c3a32';
    cell.style.color=v>4?'#fff':'#776e65';
    cell.textContent=v||'';
    grid.appendChild(cell);
  }
}
function slide(row){
  var arr=row.filter(function(v){return v;}),zeros=4-arr.length;
  arr=arr.concat(Array(zeros).fill(0));
  var gained=0;
  for(var i=0;i<3;i++)if(arr[i]&&arr[i]===arr[i+1]){
    arr[i]*=2;gained+=arr[i];arr.splice(i+1,1);arr.push(0);
  }
  return {arr:arr,gained:gained};
}function move(dir){
    var moved=false,gained=0;
    for(var i=0;i<4;i++){
      var line;
      if(dir==='left')line=board[i].slice();
      else if(dir==='right')line=board[i].slice().reverse();
      else if(dir==='up')line=[0,1,2,3].map(function(r){return board[r][i];});
      else line=[3,2,1,0].map(function(r){return board[r][i];});
      var res=slide(line),slid=res.arr;gained+=res.gained;
      for(var k=0;k<4;k++){
        if(dir==='left'&&board[i][k]!==slid[k])moved=true;
        if(dir==='right'&&board[i][3-k]!==slid[k])moved=true;
        if(dir==='up'&&board[k][i]!==slid[k])moved=true;
        if(dir==='down'&&board[3-k][i]!==slid[k])moved=true;
      }
      for(var k2=0;k2<4;k2++){
        if(dir==='left')board[i][k2]=slid[k2];
        else if(dir==='right')board[i][3-k2]=slid[k2];
        else if(dir==='up')board[k2][i]=slid[k2];
        else board[3-k2][i]=slid[k2];
      }
    }
    if(moved){
      score+=gained;
      if(score>best){best=score;localStorage.setItem('g2Best',best);}
      addTile();render();
      document.getElementById('g2Score').textContent='分数：'+score+'　最高：'+best;
      var has2048=false;
      for(var ri=0;ri<4;ri++){for(var ci=0;ci<4;ci++){if(board[ri][ci]===2048){has2048=true;break;}}if(has2048)break;}
      if(has2048)setTimeout(function(){alert('🎉 合成 2048！');},100);
    }
  }
  var key=function(e){
    var k=e.key;
    if(k==='ArrowLeft'||k==='a'||k==='A')move('left');
    else if(k==='ArrowRight'||k==='d'||k==='D')move('right');
    else if(k==='ArrowUp'||k==='w'||k==='W')move('up');
    else if(k==='ArrowDown'||k==='s'||k==='S')move('down');
  };
  document.addEventListener('keydown',key);
  reset();
  return function(){document.removeEventListener('keydown',key);};
};games.minesweeper=function(){
  var wrap=document.getElementById('gameContent');
  wrap.innerHTML='<h2>💣 扫雷</h2><div class="info" id="msInfo">💣 12　✅ 0</div><div id="msGrid" style="display:inline-block;"></div><div class="info"><button type="button" class="restart-btn" onclick="games.minesweeper()">重新开始</button></div>';
  var W=9,H=9,MINES=12;
  var grid,revealed,flagged,over;
  function reset(){
    grid=Array.from({length:H},function(){return Array.from({length:W},function(){return {mine:false,adj:0};});});
    revealed=Array.from({length:H},function(){return Array(W).fill(false);});
    flagged=Array.from({length:H},function(){return Array(W).fill(false);});
    over=false;
    var placed=0;
    while(placed<MINES){
      var r=~~(Math.random()*H),c=~~(Math.random()*W);
      if(!grid[r][c].mine){grid[r][c].mine=true;placed++;}
    }
    for(var r2=0;r2<H;r2++)for(var c2=0;c2<W;c2++)if(!grid[r2][c2].mine){
      var n=0;
      for(var dr=-1;dr<=1;dr++)for(var dc=-1;dc<=1;dc++){
        var nr=r2+dr,nc=c2+dc;
        if(nr>=0&&nr<H&&nc>=0&&nc<W&&grid[nr][nc].mine)n++;
      }
      grid[r2][c2].adj=n;
    }
    document.getElementById('msInfo').textContent='💣 12　✅ 0';
    render();
  }
  function reveal(r,c){
    if(r<0||r>=H||c<0||c>=W||revealed[r][c]||flagged[r][c]||over)return;
    revealed[r][c]=true;
    if(grid[r][c].mine){lose();return;}
    if(grid[r][c].adj===0)for(var dr=-1;dr<=1;dr++)for(var dc=-1;dc<=1;dc++)if(dr||dc)reveal(r+dr,c+dc);
    checkWin();
}function toggleFlag(r,c){
    if(revealed[r][c]||over)return;
    flagged[r][c]=!flagged[r][c];
    var n=0;flagged.forEach(function(row){row.forEach(function(v){if(v)n++;});});
    document.getElementById('msInfo').textContent='💣 '+(MINES-n)+'　✅ '+n;
    render();
  }
  function lose(){
    over=true;
    for(var r=0;r<H;r++)for(var c=0;c<W;c++)revealed[r][c]=true;
    render();
    document.getElementById('msInfo').textContent='💥 踩雷了！';
  }
  function checkWin(){
    for(var r=0;r<H;r++)for(var c=0;c<W;c++)
      if(!grid[r][c].mine&&!revealed[r][c])return;
    over=true;
    document.getElementById('msInfo').textContent='🎉 扫雷成功！';
  }
  function render(){
    var g=document.getElementById('msGrid');
    g.innerHTML='';
    for(var r=0;r<H;r++)for(var c=0;c<W;c++){
      (function(r,c){
        var btn=document.createElement('button');
        btn.type='button';
        btn.style.cssText='width:34px;height:34px;font-size:14px;font-weight:700;border:1px solid #2a1a4a;cursor:pointer;border-radius:4px;margin:1px;';
        if(!revealed[r][c]){
          btn.style.background=flagged[r][c]?'#4a1a6b':'rgba(255,255,255,0.1)';
          btn.textContent=flagged[r][c]?'🚩':'';
        }else if(grid[r][c].mine){
          btn.style.background='#8a1a1a';btn.textContent='💣';
        }else{
          btn.style.background='rgba(200,190,230,0.2)';
          btn.style.color=grid[r][c].adj===1?'#4a9aff':grid[r][c].adj===2?'#2a8a2a':'#c0a0ff';
          btn.textContent=grid[r][c].adj||'';
        }
        btn.addEventListener('click',function(){reveal(r,c);});
        btn.addEventListener('contextmenu',function(e){e.preventDefault();toggleFlag(r,c);});
        g.appendChild(btn);
      })(r,c);
    }
  }
  reset();
  return function(){};
};
games.memory=function(){
  var wrap=document.getElementById('gameContent');
  var icons=['🍎','🍌','🍇','🍓','🍒','🥝','🍑','🍍'];
  var deck=icons.concat(icons).sort(function(){return Math.random()-0.5;});
  var flipped=[],matched=0,moves=0,lock=false;
  wrap.innerHTML='<h2>🃏 记忆翻牌</h2><div class="info" id="memInfo">步数：0　配对：0/8</div><div id="memGrid" style="display:grid;grid-template-columns:repeat(4,1fr);gap:10px;max-width:360px;margin:0 auto;"></div><button type="button" class="restart-btn" onclick="games.memory()">重新开始</button>';
  var grid=document.getElementById('memGrid');deck.forEach(function(icon,i){
    var card=document.createElement('div');
    card.style.cssText='aspect-ratio:1;background:linear-gradient(135deg,#4a1a6b,#8a4aff);border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:30px;cursor:pointer;transition:0.3s;user-select:none;color:transparent;';
    card.textContent=icon;card.dataset.icon=icon;card.dataset.i=i;
    card.addEventListener('click',function(){
      if(lock||card.dataset.done||flipped.indexOf(card)>=0)return;
      card.style.background='rgba(255,255,255,0.15)';card.style.color='#fff';
      flipped.push(card);
      if(flipped.length===2){
        moves++;
        document.getElementById('memInfo').textContent='步数：'+moves+'　配对：'+matched+'/8';
        if(flipped[0].dataset.icon===flipped[1].dataset.icon){
          flipped.forEach(function(c){c.dataset.done='1';c.style.opacity='0.35';c.style.cursor='default';});
          matched++;flipped=[];
          document.getElementById('memInfo').textContent='步数：'+moves+'　配对：'+matched+'/8';
          if(matched===8)setTimeout(function(){alert('🎉 全部配对成功！');},200);
        }else{
          lock=true;
          setTimeout(function(){
            flipped.forEach(function(c){c.style.background='linear-gradient(135deg,#4a1a6b,#8a4aff)';c.style.color='transparent';});
            flipped=[];lock=false;
          },500);
        }
      }
    });
    grid.appendChild(card);
  });
  return function(){};
};
games.rps=function(){
  var wrap=document.getElementById('gameContent');
  wrap.innerHTML='<h2>✊ 石头剪刀布</h2><div class="info" id="rpsScore">胜：0　负：0　平：0</div><div style="display:flex;justify-content:center;gap:16px;margin:20px 0;" id="rpsBtns"></div><div class="info" id="rpsResult" style="font-size:18px;font-weight:700;color:#e0d0ff;">选择你的出拳</div><button type="button" class="restart-btn" onclick="games.rps()">重置比分</button>';
  var win=0,lose=0,draw=0;
  var opts=['✊','✋','✌️'],names=['石头','布','剪刀'];
  var btns=document.getElementById('rpsBtns');
  opts.forEach(function(o,i){
    var b=document.createElement('button');
    b.type='button';
    b.className='restart-btn';b.textContent=o;b.style.fontSize='32px';b.style.padding='12px 24px';
    b.onclick=function(){
      var cpu=~~(Math.random()*3);
      var res=document.getElementById('rpsResult');
      if(i===cpu){draw++;res.textContent='平局！都是'+names[i];res.style.color='#ffe877';}
      else if((i===0&&cpu===2)||(i===1&&cpu===0)||(i===2&&cpu===1)){win++;res.textContent='你赢了！'+names[i]+' 胜 '+names[cpu];res.style.color='#5cff9d';}
      else{lose++;res.textContent='你输了！'+names[cpu]+' 胜 '+names[i];res.style.color='#ff6b6b';}
      document.getElementById('rpsScore').textContent='胜：'+win+'　负：'+lose+'　平：'+draw;
    };
    btns.appendChild(b);
  });
  return function(){};
};games.breakout=function(){
  var wrap=document.getElementById('gameContent');
  wrap.innerHTML='<h2>🏓 打砖块</h2><div class="info" id="brScore">得分：0</div><canvas id="brCv" width="480" height="360"></canvas><div class="info">←→ / A D 移动挡板</div><button type="button" class="restart-btn" onclick="games.breakout()">重新开始</button>';
  var cv=document.getElementById('brCv'),ctx=cv.getContext('2d');
  var paddle={x:190,w:100,h:12,y:340},ball={x:240,y:300,dx:3,dy:-3,r:7};
  var bricks=[],score=0,timer,over=false;
  var COLS=8,BW=52,BH=18,PAD=6,TOP=40;
  function reset(){
    paddle.x=190;ball={x:240,y:300,dx:3,dy:-3,r:7};score=0;over=false;
    bricks=[];
    for(var r=0;r<5;r++)for(var c=0;c<COLS;c++)
      bricks.push({x:PAD+c*(BW+PAD),y:TOP+r*(BH+PAD),w:BW,h:BH,alive:true});
    document.getElementById('brScore').textContent='得分：0';
    draw();clearInterval(timer);timer=setInterval(loop,16);
  }
  function loop(){
    if(over)return;
    ball.x+=ball.dx;ball.y+=ball.dy;
    if(ball.x-ball.r<0||ball.x+ball.r>480)ball.dx*=-1;
    if(ball.y-ball.r<0)ball.dy*=-1;
    if(ball.y+ball.r>360){over=true;clearInterval(timer);drawGameOver();return;}
    if(ball.y+ball.r>=paddle.y&&ball.x>=paddle.x&&ball.x<=paddle.x+paddle.w&&ball.dy>0){
      var hit=(ball.x-(paddle.x+paddle.w/2))/(paddle.w/2);
      ball.dx=hit*5;ball.dy=-Math.abs(ball.dy);
    }
    bricks.forEach(function(b){
      if(!b.alive)return;
      if(ball.x+b.r>b.x&&ball.x-b.r<b.x+b.w&&ball.y+b.r>b.y&&ball.y-b.r<b.y+b.h){
        b.alive=false;score+=10;ball.dy*=-1;
        document.getElementById('brScore').textContent='得分：'+score;
      }
    });
    if(bricks.every(function(b){return !b.alive;})){over=true;clearInterval(timer);drawWin();return;}
    draw();
    }function draw(){
    ctx.fillStyle='#0a0620';ctx.fillRect(0,0,480,360);
    ctx.fillStyle='#8a4aff';ctx.fillRect(paddle.x,paddle.y,paddle.w,paddle.h);
    ctx.beginPath();ctx.arc(ball.x,ball.y,ball.r,0,Math.PI*2);ctx.fillStyle='#ff78f0';ctx.fill();
    bricks.forEach(function(b){
      if(!b.alive)return;
      ctx.fillStyle=b.y<60?'#5cff9d':b.y<100?'#ffe877':'#ff6b9d';
      ctx.fillRect(b.x,b.y,b.w,b.h);
    });
  }
  function drawGameOver(){
    ctx.fillStyle='rgba(0,0,0,0.62)';ctx.fillRect(0,0,480,360);
    ctx.fillStyle='#fff';ctx.font='30px sans-serif';ctx.textAlign='center';
    ctx.fillText('Game Over',240,170);ctx.font='16px sans-serif';ctx.fillStyle='#ffe877';
    ctx.fillText('得分：'+score,240,208);
  }
  function drawWin(){
    ctx.fillStyle='rgba(0,0,0,0.62)';ctx.fillRect(0,0,480,360);
    ctx.fillStyle='#5cff9d';ctx.font='30px sans-serif';ctx.textAlign='center';
    ctx.fillText('🎉 通关！',240,170);ctx.fillStyle='#ffe877';ctx.font='16px sans-serif';
    ctx.fillText('得分：'+score,240,208);
  }
  var key=function(e){
    var k=e.key;
    if((k==='ArrowLeft'||k==='a'||k==='A')&&paddle.x>0)paddle.x-=28;
    if((k==='ArrowRight'||k==='d'||k==='D')&&paddle.x<380)paddle.x+=28;
  };
  document.addEventListener('keydown',key);
  reset();
  return function(){clearInterval(timer);document.removeEventListener('keydown',key);};
};games.flappy=function(){
  var wrap=document.getElementById('gameContent');
  wrap.innerHTML='<h2>🐦 Flappy Bird</h2><div class="info" id="flScore">得分：0</div><canvas id="flCv" width="320" height="440"></canvas><div class="info">点击 / 空格 扇翅膀</div><button type="button" class="restart-btn" onclick="games.flappy()">重新开始</button>';
  var cv=document.getElementById('flCv'),ctx=cv.getContext('2d');
  var bird={y:200,vy:0},pipes=[],score=0,timer,over=false,frame=0;
  var G=0.45,JUMP=-7.2,PIPE_W=52,GAP=130,SPEED=2.4;
  function reset(){
    bird={y:200,vy:0};pipes=[];score=0;over=false;frame=0;
    document.getElementById('flScore').textContent='得分：0';
    draw();clearInterval(timer);timer=setInterval(loop,16);
  }
  function loop(){
    if(over)return;
    frame++;
    bird.vy+=G;bird.y+=bird.vy;
    if(bird.y<0||bird.y>440){die();return;}
    if(frame%90===0)pipes.push({x:320,top:60+Math.random()*200});
    pipes.forEach(function(p){p.x-=SPEED;});
    pipes=pipes.filter(function(p){return p.x+PIPE_W>0;});
    for(var i=0;i<pipes.length;i++){
      var p=pipes[i];
      if(bird.y+12>p.top&&bird.y-12<p.top+GAP&&p.x<60&&p.x+PIPE_W>0){die();return;}
      if(!p.passed&&p.x+PIPE_W<60){p.passed=true;score++;document.getElementById('flScore').textContent='得分：'+score;}
    }
    draw();
                                                        }function die(){
    over=true;clearInterval(timer);
    ctx.fillStyle='rgba(0,0,0,0.6)';ctx.fillRect(0,0,320,440);
    ctx.fillStyle='#fff';ctx.font='28px sans-serif';ctx.textAlign='center';
    ctx.fillText('Game Over',160,200);ctx.fillStyle='#ffe877';ctx.font='16px sans-serif';
    ctx.fillText('得分：'+score,160,236);
  }
  function draw(){
    ctx.fillStyle='#0a0620';ctx.fillRect(0,0,320,440);
    ctx.fillStyle='#5cff9d';
    pipes.forEach(function(p){ctx.fillRect(p.x,0,PIPE_W,p.top);ctx.fillRect(p.x,p.top+GAP,PIPE_W,440-p.top-GAP);});
    ctx.beginPath();ctx.arc(60,bird.y,13,0,Math.PI*2);ctx.fillStyle='#ffe877';ctx.fill();
    ctx.fillStyle='#0a0620';ctx.beginPath();ctx.arc(64,bird.y-4,3,0,Math.PI*2);ctx.fill();
  }
  var jump=function(){if(over)return;bird.vy=JUMP;};
  cv.addEventListener('click',jump);
  var key=function(e){if(e.key===' ')jump();};
  document.addEventListener('keydown',key);
  reset();
  return function(){clearInterval(timer);cv.removeEventListener('click',jump);document.removeEventListener('keydown',key);};
};
games.gomoku=function(){
  var wrap=document.getElementById('gameContent');
  wrap.innerHTML='<h2>⚫ 五子棋（人机）</h2><div class="info" id="gmInfo">你先手（黑子）</div><canvas id="gmCv" width="420" height="420"></canvas><button type="button" class="restart-btn" onclick="games.gomoku()">重新开始</button>';
  var cv=document.getElementById('gmCv'),ctx=cv.getContext('2d');
  var N=15,S=28,OFF=14;
  var board,turn,over;
  function reset(){
    board=Array.from({length:N},function(){return Array(N).fill(0);});
    turn=1;over=false;
    document.getElementById('gmInfo').textContent='你先手（黑子）';
    draw();
        }function draw(){
  ctx.fillStyle='#d4a96a';ctx.fillRect(0,0,420,420);
  ctx.strokeStyle='#3a2a1a';ctx.lineWidth=1;
  for(var i=0;i<N;i++){
    ctx.beginPath();ctx.moveTo(OFF+i*S,OFF);ctx.lineTo(OFF+i*S,OFF+(N-1)*S);ctx.stroke();
    ctx.beginPath();ctx.moveTo(OFF,OFF+i*S);ctx.lineTo(OFF+(N-1)*S,OFF+i*S);ctx.stroke();
  }
  for(var r=0;r<N;r++)for(var c=0;c<N;c++){
    if(!board[r][c])continue;
    ctx.beginPath();ctx.arc(OFF+c*S,OFF+r*S,12,0,Math.PI*2);
    ctx.fillStyle=board[r][c]===1?'#0a0a12':'#f5f0ff';
    ctx.fill();ctx.strokeStyle='#0a0a12';ctx.stroke();
  }
}
function click(e){
  if(over||turn!==1)return;
  var rect=cv.getBoundingClientRect();
  var x=e.clientX-rect.left,y=e.clientY-rect.top;
  var c=Math.round((x-OFF)/S),r=Math.round((y-OFF)/S);
  if(r<0||r>=N||c<0||c>=N||board[r][c])return;
  board[r][c]=1;draw();
  if(check(r,c,1)){over=true;document.getElementById('gmInfo').textContent='🎉 你赢了！';return;}
  turn=2;document.getElementById('gmInfo').textContent='电脑思考中…';
  setTimeout(aiMove,200);
}
function aiMove(){
  if(over)return;
  var empties=[];
  for(var r=0;r<N;r++)for(var c=0;c<N;c++)if(!board[r][c])empties.push([r,c]);
  if(!empties.length){over=true;document.getElementById('gmInfo').textContent='平局';return;}
  var pick=empties[~~(Math.random()*empties.length)];
  outer:for(var i=0;i<empties.length;i++){
    var rr=empties[i][0],cc=empties[i][1];
    board[rr][cc]=2;
    if(check(rr,cc,2)){pick=[rr,cc];board[rr][cc]=0;break outer;}
    board[rr][cc]=0;
  }
  board[pick[0]][pick[1]]=2;draw();
  if(check(pick[0],pick[1],2)){over=true;document.getElementById('gmInfo').textContent='💻 电脑赢了';return;}
  turn=1;document.getElementById('gmInfo').textContent='轮到你了（黑子）';
}function check(r,c,p){
    var dirs=[[1,0],[0,1],[1,1],[1,-1]];
    for(var d=0;d<dirs.length;d++){
      var dr=dirs[d][0],dc=dirs[d][1],n=1;
      for(var s=1;s<5;s++){var nr=r+dr*s,nc=c+dc*s;if(nr<0||nr>=N||nc<0||nc>=N||board[nr][nc]!==p)break;n++;}
      for(var s2=1;s2<5;s2++){var nr2=r-dr*s2,nc2=c-dc*s2;if(nr2<0||nr2>=N||nc2<0||nc2>=N||board[nr2][nc2]!==p)break;n++;}
      if(n>=5)return true;
    }
    return false;
  }
  cv.addEventListener('click',click);
  reset();
  return function(){cv.removeEventListener('click',click);};
};
var cleanup=null;
function openGame(name){
  var modal=document.getElementById('gameModal');
  var content=document.getElementById('gameContent');
  if(!modal||!content)return;
  modal.classList.add('open');
  content.innerHTML='';
  if(cleanup){try{cleanup();}catch(e){}cleanup=null;}
  if(typeof games[name]==='function'){
    try{cleanup=games[name]()||null;}
    catch(err){
      content.innerHTML='<h2>加载失败</h2><div class="info">'+err.message+'</div>';
      if(window.console)console.error(err);
    }
  }else{
    content.innerHTML='<h2>游戏不存在</h2><div class="info">该游戏暂未实现</div>';
  }
}
function closeModal(){
  var modal=document.getElementById('gameModal');
  if(modal)modal.classList.remove('open');
  if(cleanup){try{cleanup();}catch(e){}cleanup=null;}
}
function bindGameItems(){
  var items=document.querySelectorAll('.game-item[data-game]');
  for(var i=0;i<items.length;i++){
    (function(item){
      item.addEventListener('click',function(e){
        e.preventDefault();
        openGame(item.getAttribute('data-game'));
      });
    })(items[i]);
  }
  var closeBtn=document.getElementById('closeBtn');
  if(closeBtn)closeBtn.addEventListener('click',closeModal);
  var modal=document.getElementById('gameModal');
  if(modal)modal.addEventListener('click',function(e){
    if(e.target===modal)closeModal();
  });
  document.addEventListener('keydown',function(e){
    if(e.key==='Escape')closeModal();
  });
}
if(document.readyState==='loading'){
  document.addEventListener('DOMContentLoaded',bindGameItems);
}else{
  bindGameItems();
}

/* ===== 公告页控制 ===== */
(function(){
  var overlay = document.getElementById('noticeOverlay');
  var closeBtn = document.getElementById('closeNotice');
  if(!overlay || !closeBtn) return;
  closeBtn.addEventListener('click', function(){
    overlay.classList.add('closing');
    setTimeout(function(){
      overlay.style.display = 'none';
    }, 500);
  });
})();
</script>
</body>
</html>
