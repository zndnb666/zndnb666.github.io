<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>丆.&牛逼</title>
<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:"Microsoft Yahei",sans-serif}

/* 粒子背景 */
#particles{
  position:fixed;top:0;left:0;width:100vw;height:100vh;
  background:linear-gradient(-45deg,#050520,#1b0e42,#082b46,#240b36);
  background-size:400% 400%;
  animation:bgFlow 12s ease infinite;
  z-index:-1;
}
@keyframes bgFlow{
  0%{background-position:0% 50%}
  50%{background-position:100% 50%}
  100%{background-position:0% 50%}
}
.particle{
  position:absolute;border-radius:500px;background:rgba(255,255,255,0.15);
  animation:float 15s linear infinite;
}
@keyframes float{
  0%{transform:translateY(110vh) rotate(0deg);opacity:0}
  10%{opacity:1}
  90%{opacity:1}
  100%{transform:translateY(-10vh) rotate(720deg);opacity:0}
}

/* 游戏主页 */
#gamePage{
  padding:40px 20px;min-height:100vh;
}
.page-title{
  text-align:center;font-size:42px;color:#fff;margin-bottom:14px;
  text-shadow:0 0 15px #ff78f0,0 0 30px #844bff;
  animation:textGlow 2.2s ease-in-out infinite alternate;
}
@keyframes textGlow{
  from{filter:brightness(1)}
  to{filter:brightness(1.4)}
}
.tip{
  text-align:center;color:#9fe9ff;font-size:14px;margin-bottom:30px;
  opacity:.85;
}
/* 板块标题样式 */
.section-title{
  width:100%;
  color:#ffe877;
  font-size:26px;
  margin:40px 0 20px;
  border-left:5px solid #844bff;
  padding-left:12px;
}
.game-wrap{
  max-width:1100px;margin:0 auto;display:grid;
  grid-template-columns:repeat(auto-fill,minmax(160px,1fr));
  gap:22px;
}
.game-item{
  background:rgba(255,255,255,0.08);border:1px solid rgba(255,255,255,0.18);
  border-radius:16px;padding:20px;text-align:center;cursor:pointer;
  transition:0.4s;backdrop-filter:blur(4px);
  animation:itemFade 0.8s backwards;
}
@keyframes itemFade{
  from{opacity:0;transform:translateY(25px)}
  to{opacity:1;transform:translateY(0)}
}
.game-item:hover{
  transform:translateY(-8px) scale(1.04);
  box-shadow:0 0 24px rgba(180,110,255,0.45);
  background:rgba(255,255,255,0.13);
}
.game-item a{
  color:#fff;text-decoration:none;font-size:17px;display:block;
}
.no-login-tag{
  display:inline-block;font-size:12px;color:#0ff;
  border:1px solid #0ff;border-radius:8px;padding:1px 6px;margin-top:8px;
}
.item-desc{
  font-size:12px;color:#b9c4ff;margin-top:6px;line-height:1.5;
}
</style>
</head>
<body>
<div id="particles"></div>

<!-- 小游戏页面 -->
<div id="gamePage">
  <h1 class="page-title">丆.&牛逼</h1>
  <div class="tip">内置小游戏断网可玩 · 云游戏需扫码登录 · 外链游戏点开即玩免登录</div>

  <div class="game-wrap">

    <!-- 板块1：内置纯单机小游戏（断网可玩） -->
    <div class="section-title">📱 内置纯单机小游戏（断网可玩·不登录）</div>
    <div class="game-item">
      <a href="javascript:void(0)" onclick="alert('贪吃蛇 - 方向键控制\n（内置版需单独引入JS模块）')">🐍 贪吃蛇</a>
      <span class="no-login-tag">离线</span>
    </div>
    <div class="game-item">
      <a href="javascript:void(0)" onclick="alert('俄罗斯方块\n（内置版需单独引入JS模块）')">🧱 俄罗斯方块</a>
      <span class="no-login-tag">离线</span>
    </div>
    <div class="game-item">
      <a href="javascript:void(0)" onclick="alert('2048\n（内置版需单独引入JS模块）')">🔢 2048</a>
      <span class="no-login-tag">离线</span>
    </div>
    <div class="game-item">
      <a href="javascript:void(0)" onclick="alert('扫雷\n（内置版需单独引入JS模块）')">💣 扫雷</a>
      <span class="no-login-tag">离线</span>
    </div>
    <div class="game-item">
      <a href="javascript:void(0)" onclick="alert('翻牌记忆\n（内置版需单独引入JS模块）')">🃏 翻牌记忆</a>
      <span class="no-login-tag">离线</span>
    </div>
    <div class="game-item">
      <a href="javascript:void(0)" onclick="alert('石头剪刀布\n（内置版需单独引入JS模块）')">✊ 石头剪刀布</a>
      <span class="no-login-tag">离线</span>
    </div>
    <div class="game-item">
      <a href="javascript:void(0)" onclick="alert('恐龙跳跳\n（内置版需单独引入JS模块）')">🦕 恐龙跳跳</a>
      <span class="no-login-tag">离线</span>
    </div>
    <div class="game-item">
      <a href="javascript:void(0)" onclick="alert('关灯游戏\n（内置版需单独引入JS模块）')">💡 关灯游戏</a>
      <span class="no-login-tag">离线</span>
    </div>

    <!-- 板块2：免登录 H5 网页游戏 -->
    <div class="section-title">🎲 免登录 H5 网页游戏（点开即玩）</div>
    <div class="game-item">
      <a target="_blank" rel="noopener" href="https://suika-game.io/">🍉 合成大西瓜</a>
      <span class="no-login-tag">免登录</span>
    </div>
    <div class="game-item">
      <a target="_blank" rel="noopener" href="https://slowroads.io/">🛣️ Slow Roads 佛系自驾</a>
      <span class="no-login-tag">免登录</span>
    </div>
    <div class="game-item">
      <a target="_blank" rel="noopener" href="https://papergames.io/zh">♟️ 象棋/五子棋/海战棋</a>
      <span class="no-login-tag">免登录</span>
    </div>
    <div class="game-item">
      <a target="_blank" rel="noopener" href="https://neal.fun/">🧠 Neal.Fun 脑洞合集</a>
      <span class="no-login-tag">免登录</span>
    </div>
    <div class="game-item">
      <a target="_blank" rel="noopener" href="https://poki.com/zh">🎮 Poki 小游戏合集</a>
      <span class="no-login-tag">免登录</span
