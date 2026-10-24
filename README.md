<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>纯单机小游戏合集</title>
<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:"Microsoft Yahei","PingFang SC",sans-serif}
:root{--accent:#00f0c0;--accent2:#7b5cff}
body{background:#07071a;color:#fff;min-height:100vh;overflow-x:hidden}
#bg{position:fixed;inset:0;z-index:-1;
  background:radial-gradient(circle at 20% 20%,#1a0b3d 0,transparent 40%),
             radial-gradient(circle at 80% 70%,#06283d 0,transparent 45%),#07071a;}
.page-title{text-align:center;font-size:38px;margin:34px 16px 8px;
  background:linear-gradient(90deg,var(--accent),var(--accent2));-webkit-background-clip:text;background-clip:text;color:transparent;
  animation:textGlow 2.4s ease-in-out infinite alternate;}
@keyframes textGlow{from{filter:brightness(1)}to{filter:brightness(1.35)}}
.subtitle{text-align:center;color:#8a8fc0;font-size:14px;margin-bottom:24px}
.tag-bar{text-align:center;margin-bottom:26px;font-size:13px;color:#5fe0c8}
.tag-bar span{display:inline-block;background:rgba(0,240,192,.12);border:1px solid rgba(0,240,192,.35);
  border-radius:20px;padding:5px 14px;margin:4px}
.wrap{max-width:1080px;margin:0 auto;padding:0 18px 60px}
.section-title{color:#ffe877;font-size:22px;margin:34px 0 16px;border-left:5px solid var(--accent2);padding-left:12px}
.grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(210px,1fr));gap:16px}
.card{background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.14);border-radius:16px;padding:16px;cursor:pointer;
  transition:.35s;backdrop-filter:blur(6px);animation:fade .7s backwards}
@keyframes fade{from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:none}}
.card:hover{transform:translateY(-6px) scale(1.03);box-shadow:0 10px 28px rgba(0,240,192,.25);background:rgba(255,255,255,.1)}
.card h3{font-size:18px;margin-bottom:6px}
.card p{font-size:13px;color:#9ea3d0;line-height:1.5}
.badge{display:inline-block;font-size:11px;color:#0ff;border:1px solid #0ff;border-radius:6px;padding:1px 7px;margin-top:8px}
/* 弹窗 */
.modal{position:fixed;inset:0;background:rgba(3,3,15,.85);display:none;align-items:center;justify-content:center;z-index:50;padding:16px}
.modal.open{display:flex}
.modal-box{background:#0d0d28;border:1px solid rgba(0,240,192,.3);border-radius:18px;max-width:560px;width:100%;max-height:90vh;overflow:auto;padding:22px}
.modal-head{display:flex;justify-content:space-between;align-items:center;margin-bottom:14px}
.modal-head h2{font-size:22px}
.close{background:none;border:none;color:#fff;font-size:26px;cursor:pointer}
canvas{background:#000;border-radius:12px;display:block;margin:0 auto;max-width:100%;touch-action:none}
.btn{background:linear-gradient(90deg,var(--accent),var(--accent2));color:#07071a;border:none;border-radius:10px;padding:10px 20px;font-size:15px;font-weight:700;cursor:pointer;margin:6px 6px 0 0}
.btn.ghost{background:transparent;color:#fff;border:1px solid rgba(255,255,255,.3)}
.ctrl{text-align:center;color:#8a8fc0;font-size:13px;margin-top:10px;line-height:1.7}
.hint{color:#9ea3d0;font-size:14px;line-height:1.7;margin-bottom:12px}
.score{text-align:center;color:var(--accent);font-size:16px;margin-bottom:8px}
#snakeGrid{display:grid;grid-template-columns:repeat(4,1fr);gap:8px;max-width:340px;margin:0 auto}
#snakeGrid button{aspect-ratio:1/1;font-size:20px;border-radius:10px;border:1px solid rgba(255,255,255,.2);background:rgba(255,255,255,.06);color:#fff}
#snakeGrid button.on{background:linear-gradient(135deg,var(--accent),var(--accent2));color:#07071a}
</style>
</head>
<body>
<div id="bg"></div>

<div class="page-title">🎮 纯单机小游戏合集</div>
<div class="subtitle">无需联网 · 无需登录 · 不收集任何个人信息 · 存档仅存在本机浏览器</div>
<div class="tag-bar">
  <span>📴 断网可玩</span><span>🔒 免登录</span><span>💾 本地存档</span><span>📱 手机可玩</span>
</div>

<div class="wrap">

  <div class="section-title">🕹️ 内置单文件小游戏（双击即玩）</div>
  <div class="grid">
    <div class="card" onclick="openGame('snake')"><h3>🐍 贪吃蛇</h3><p>方向键 / 滑动控制，吃豆变长，撞墙或撞自己结束。</p><span class="badge">纯单机</span></div>
    <div class="card" onclick="openGame('tetris')"><h3>🧱 俄罗斯方块</h3><p>经典方块，←→移动、↑旋转、↓加速、空格直落。</p><span class="badge">纯单机</span></div>
    <div class="card" onclick="openGame('2048')"><h3>🔢 2048</h3><p>方向键 / 滑动合并相同数字，冲上 2048。</p><span class="badge">纯单机</span></div>
    <div class="card" onclick="openGame('mines')"><h3>💣 扫雷</h3><p>左键揭格、右键插旗，避开所有雷。</p><span class="badge">纯单机</span></div>
    <div class="card" onclick="openGame('memory')"><h3>🎴 翻牌记忆</h3><p>找出全部配对，用最少步数通关。</p><span class="badge">纯单机</span></div>
    <div class="card" onclick="openGame('rps')"><h3>✊ 石头剪刀布</h3><p>纯本地对战，随机电脑出手。</p><span class="badge">纯单机</span></div>
    <div class="card" onclick="openGame('dino')"><h3>🦕 恐龙跳跳</h3><p>空格 / 点屏起跳，躲避障碍刷高分。</p><span class="badge">纯单机</span></div>
    <div class="card" onclick="openGame('lights')"><h3>💡 关灯游戏</h3><p>点击翻转周围灯，把棋盘全变黑。</p><span class="badge">纯单机</sp
