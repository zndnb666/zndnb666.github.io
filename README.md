<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>丆.&牛逼</title>
<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:"Microsoft Yahei",sans-serif}
#particles{position:fixed;top:0;left:0;width:100vw;height:100vh;background:linear-gradient(-45deg,#050520,#1b0e42,#082b46,#240b36);background-size:400% 400%;animation:bgFlow 12s ease infinite;z-index:-1;}
@keyframes bgFlow{0%{background-position:0% 50%}50%{background-position:100% 50%}100%{background-position:0% 50%}}
.particle{position:absolute;border-radius:500px;background:rgba(255,255,255,0.15);animation:float 15s linear infinite;}
@keyframes float{0%{transform:translateY(110vh) rotate(0deg);opacity:0}10%{opacity:1}90%{opacity:1}100%{transform:translateY(-10vh) rotate(720deg);opacity:0}}
#gamePage{padding:40px 20px;min-height:100vh;}
.page-title{text-align:center;font-size:42px;color:#fff;margin-bottom:14px;text-shadow:0 0 15px #ff78f0,0 0 30px #844bff;animation:textGlow 2.2s ease-in-out infinite alternate;}
@keyframes textGlow{from{filter:brightness(1)}to{filter:brightness(1.4)}}
.tip{text-align:center;color:#9fe9ff;font-size:14px;margin-bottom:30px;opacity:.85;}
.section-title{width:100%;color:#ffe877;font-size:26px;margin:40px 0 20px;border-left:5px solid #844bff;padding-left:12px;}
.game-wrap{max-width:1100px;margin:0 auto;display:grid;grid-template-columns:repeat(auto-fill,minmax(160px,1fr));gap:22px;}
.game-item{background:rgba(255,255,255,0.08);border:1px solid rgba(255,255,255,0.18);border-radius:16px;padding:20px;text-align:center;cursor:pointer;transition:0.4s;backdrop-filter:blur(4px);animation:itemFade 0.8s backwards;}
@keyframes itemFade{from{opacity:0;transform:translateY(25px)}to{opacity:1;transform:translateY(0)}}
.game-item:hover{transform:translateY(-8px) scale(1.04);box-shadow:0 0 24px rgba(180,110,255,0.45);background:rgba(255,255,255,0.13);}
.game-item a{color:#fff;text-decoration:none;font-size:17px;display:block;}
.no-login-tag{display:inline-block;font-size:12px;color:#0ff;border:1px solid #0ff;border-radius:8px;padding:1px 6px;margin-top:8px;}
.item-desc{font-size:12px;color:#b9c4ff;margin-top:6px;line-height:1.5;}
.game-modal{display:none;position:fixed;inset:0;z-index:9999;background:rgba(0,0,0,0.85);align-items:center;justify-content:center;padding:20px;}
.game-modal.open{display:flex}
.game-modal .board{background:rgba(20,12,45,0.97);border:1px solid rgba(180,110,255,0.5);border-radius:18px;padding:24px;max-width:560px;width:100%;max-height:92vh;overflow:auto;text-align:center;position:relative;}
.game-modal .board h2{color:#ffe877;font-size:22px;margin-bottom:14px}
.game-modal .board canvas{background:#0a0620;border-radius:12px;display:block;margin:0 auto 14px;max-width:100%;height:auto;}
.game-modal .close-btn{position:absolute;top:12px;right:16px;font-size:26px;color:#fff;cursor:pointer;background:none;border:none;line-height:1;}
.game-modal .close-btn:hover{color:#ff78f0}
.game-modal .info{color:#9fe9ff;font-size:14px;margin:8px 0}
.game-modal .restart-btn{background:linear-gradient(135deg,#844bff,#ff78f0);color:#fff;border:none;padding:10px 24px;border-radius:10px;font-size:15px;cursor:pointer;margin:6px 4px;}
.game-modal .restart-btn:hover{filter:brightness(1.15)}
.memory-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:10px;max-width:400px;margin:0 auto}
.memory-card{aspect-ratio:1;background:linear-gradient(135deg,#844bff,#ff78f0);border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:32px;cursor:pointer;transition:transform .3s;transform-style:preserve-3d;transform:rotateY(180deg);}
.memory-card.flipped{transform:rotateY(0)}
.memory-card.matched{opacity:.4;cursor:default}
</style>
</head>
<body>
<div id="particles"></div>
<div id="gamePage">
  <h1 class="page-title">丆.&牛逼</h1>
  <div class="tip">内置小游戏断网可玩 · 云游戏需扫码登录 · 外链游戏点开即玩免登录</div>
  <div class="game-wrap">
    <div class="section-title">📱 内置纯单机小游戏（断网可玩·不登录·真实可玩）</div>
    <div class="game-item"><a href="javascript:void(0)" onclick="openGame('snake')">🐍 贪吃蛇</a><div class="item-desc">方向键/WASD/滑动控制，吃食物长身体，撞墙或自己就死</div><span class="no-login-tag">离线</span></div>
    <div class="game-item"><a href="javascript:void(0)" onclick="openGame('tetris')">🧱 俄罗斯方块</a><div class="item-desc">方向键移动/旋转/加速，消行得分，速度越来越快</div><span class="no-login-tag">离线</span></div>
    <div class="game-item"><a href="javascript:void(0)" onclick="openGame('g2048')">🔢 2048</a><div class="item-desc">方向键滑动合并相同数字，凑出 2048</div><span class="no-login-tag">离线</span></div>
    <div class="game-item"><a href="javascript:void(0)" onclick="openGame('minesweeper')">💣 扫雷</a><div class="item-desc">左键挖、右键标记，找出所有雷</div><span class="no-login-tag">离线</span></div>
    <div class="game-item"><a href="javascript:void(0)" onclick="openGame('memory')">🃏 翻牌记忆</a><div class="item-desc">翻两张牌，配对成功就消除，越少步数越好</div><span class="no-login-tag">离线</span></div>
    <div class="game-item"><a hre/* ===== 1. 贪吃蛇 ===== */
function startSnake(){
  const wrap=document.getElementById('gameContent');
  wrap.innerHTML='<h2>🐍 贪吃蛇</h2><div class="info" id="snakeScore">得分：0　最高：0</div><canvas id="snakeCv" width="400" height="400"></canvas><div class="info">方向键 / WASD / 滑动屏幕</div><button class="restart-btn" onclick="startSnake()">重新开始</button>';
  const cv=document.getElementById('snakeCv'),ctx=cv.getContext('2d');
  const S=20,C=20,R=20;
  let snake,dir,food,score,timer,alive,best=+localStorage.getItem('snakeBest')||0;
  function reset(){
    snake=[{x:10,y:10},{x:9,y:10},{x:8,y:10}];dir={x:1,y:0};score=0;alive=true;
    document.getElementById('snakeScore').textContent='得分：0　最高：'+best;
    placeFood();draw();
    if(timer)clearInterval(timer);
    timer=setInterval(loop,105);
  }
  function placeFood(){
    while(true){food={x:Math.floor(Math.random()*C),y:Math.floor(Math.random()*R)};if(!snake.some(function(s){return s.x===food.x&&s.y===food.y;}))break;}
  }
  function loop(){
    if(!alive)return;
    const h={x:snake[0].x+dir.x,y:snake[0].y+dir.y};
    if(h.x<0||h.y<0||h.x>=C||h.y>=R||snake.some(function(s){return s.x===h.x&&s.y===h.y;})){
      alive=false;clearInterval(timer);
      ctx.fillStyle='rgba(0,0,0,0.6)';ctx.fillRect(0,0,400,400);
      ctx.fillStyle='#fff';ctx.font='34px sans-serif';ctx.textAlign='center';
      ctx.fillText('Game Over',200,190);ctx.font='18px sans-serif';ctx.fillStyle='#ffe877';
      ctx.fillText('得分：'+score,200,230);return;
    }
    snake.unshift(h);
    if(h.x===food.x&&h.y===food.y){
      score++;
      if(score>best){best=score;localStorage.setItem('snakeBest',best);}
      document.getElementById('snakeScore').textContent='得分：'+score+'　最高：'+best;
      placeFood();
    } else snake.pop();
    draw();
  }
  function draw(){
    ctx.fillStyle='#0a0620';ctx.fillRect(0,0,400,400);
    ctx.fillStyle='#ff78f0';
    snake.forEach(function(s,i){ctx.globalAlpha=i===0?1:0.75;ctx.fillRect(s.x*S,s.y*S,S-1,S-1);});
    ctx.globalAlpha=1;ctx.fillStyle='#5cff9d';ctx.fillRect(food.x*S,food.y*S,S-1,S-1);
  }
  const handler=function(e){
    const k=e.key;
    if((k==='ArrowUp'||k==='w'||k==='W')&&dir.y!==1)dir={x:0,y:-1};
    else if((k==='ArrowDown'||k==='s'||k==='S')&&dir.y!==-1)dir={x:0,y:1};
    else if((k==='ArrowLeft'||k==='a'||k==='A')&&dir.x!==1)dir={x:-1,y:0};
    else if((k==='ArrowRight'||k==='d'||k==='D')&&dir.x!==-1)dir={x:1,y:0};
  };
  document.addEventListener('keydown',handler);
  let ts=null;
  cv.addEventListener('touchstart',function(e){ts={x:e.touches[0].clientX,y:e.touches[0].clientY};e.preventDefault();},{passive:false});
  cv.addEventListener('touchmove',function(e){
    if(!ts)return;
    const t=e.touches[0],dx=t.clientX-ts.x,dy=t.clientY-ts.y;
    if(Math.abs(dx)<20&&Math.abs(dy)<20)return;
    if(Math.abs(dx)>Math.abs(dy)){if(dx>0&&dir.x!==-1)dir={x:1,y:0};else if(dx<0&&dir.x!==1)dir={x:-1,y:0};}
    else{if(dy>0&&dir.y!==-1)dir={x:0,y:1};else if(dy<0&&dir.y!==1)dir={x:0,y:-1};}
    ts=null;e.preventDefault();
  },{passive:false});
  reset();
  return function(){clearInterval(timer);document.removeEventListener('keydown',handler);};
}

/* ===== 2. 俄罗斯方块 ===== */
function startTetris(){
  const wrap=document.getElementById('gameContent');
  wrap.innerHTML='<h2>🧱 俄罗斯方块</h2><div class="info" id="tetScore">得分：0　行数：0</div><canvas id="tetCv" width="240" height="480"></canvas><div class="info">←→ 移动　↑/空格 旋转　↓ 加速</div><button class="restart-btn" onclick="startTetris()">重新开始</button>';
  const cv=document.getElementById('tetCv'),ctx=cv.getContext('2d');
  const COLS=12,ROWS=20,S=20;
  const SHAPES=[[[1,1,1,1]],[[1,1],[1,1]],[[0,1,0],[1,1,1]],[[1,0,0],[1,1,1]],[[0,0,1],[1,1,1]],[[0,1,1],[1,1,0]],[[1,1,0],[0,1,1]]];
  let board,piece,px,py,score,lines,timer,over,speed=600;
  function reset(){
    board=Array.from({length:ROWS},function(){return Array(COLS).fill(0);});
    score=0;lines=0;over=false;speed=600;
    document.getElementById('tetScore').textContent='得分：0　行数：0';
    newPiece();draw();
    if(timer)clearInterval(timer);
    timer=setInterval(tick,speed);
  }
  function newPiece(){
    const t=Math.floor(Math.random()*SHAPES.length);
    piece=SHAPES[t].map(function(r){return r.slice();});
    px=4;py=0;
    if(collide(px,py,piece)){over=true;gameOver();}
  }
  function collide(x,y,shape){
    for(let r=0;r<shape.length;r++)
      for(let c=0;c<shape[r].length;c++)
        if(shape[r][c]){
          const nx=x+c,ny=y+r;
          if(nx<0||nx>=COLS||ny>=ROWS)return true;
          if(ny>=0&&board[ny][nx])return true;
        }
    return false;
  }
  function merge(){
    for(let r=0;r<piece.length;r++)
      for(let c=0;c<piece[r].length;c++)
        if(piece[r][c])board[py+r][px+c]=1;
  }
  function clearLines(){
    let cleared=0;
    for(let r=ROWS-1;r>=0;r--)
      if(board[r].every(function(v){return v;})){
        board.splice(r,1);
        board.unshift(Array(COLS).fill(0));
        cleared++;r++;
      }
    if(cleared){
      lines+=cleared;
     /* ===== 3. 2048 ===== */
function start2048(){
  const wrap=document.getElementById('gameContent');
  wrap.innerHTML='<h2>🔢 2048</h2><div class="info" id="g2Score">分数：0　最高：0</div><div id="g2Grid" style="display:grid;grid-template-columns:repeat(4,1fr);gap:8px;max-width:340px;margin:0 auto;background:rgba(0,0,0,0.3);padding:10px;border-radius:12px;"></div><div class="info">方向键 / WASD / 滑动</div><button class="restart-btn" onclick="start2048()">重新开始</button>';
  const grid=document.getElementById('g2Grid');
  let board,score,best=+localStorage.getItem('g2Best')||0;
  function reset(){
    board=Array.from({length:4},function(){return Array(4).fill(0);});
    score=0;addTile();addTile();render();
    document.getElementById('g2Score').textContent='分数：0　最高：'+best;
  }
  function addTile(){
    const empty=[];
    for(let r=0;r<4;r++)for(let c=0;c<4;c++)if(!board[r][c])empty.push([r,c]);
    if(!empty.length)return;
    const rc=empty[Math.floor(Math.random()*empty.length)];
    board[rc[0]][rc[1]]=Math.random()<0.9?2:4;
  }
  function render(){
    const colors={0:'rgba(255,255,255,0.05)',2:'#eee4da',4:'#ede0c8',8:'#f2b179',16:'#f59563',32:'#f67c5f',64:'#f65e3b',128:'#edcf72',256:'#edcc61',512:'#edc850',1024:'#edc53f',2048:'#edc22e'};
    grid.innerHTML='';
    for(let r=0;r<4;r++)
      for(let c=0;c<4;c++){
        const cell=document.createElement('div');
        const v=board[r][c];
        cell.style.cssText='aspect-ratio:1;display:flex;align-items:center;justify-content:center;border-radius:8px;font-size:28px;font-weight:bold;transition:.12s;';
        cell.style.background=colors[v]||'#3c3a32';
        cell.style.color=v>4?'#fff':'#776e65';
        cell.textContent=v||'';
        grid.appendChild(cell);
      }
  }
  function slide(row){
    let arr=row.filter(function(v){return v;}),zeros=Array(4-arr.length).fill(0);
    for(let i=0;i<arr.length-1;i++)
      if(arr[i]===arr[i+1]){arr[i]*=2;arr.splice(i+1,1);i--;}
    return arr.concat(zeros);
  }
  function move(dir){
    let moved=false,gained=0;
    for(let i=0;i<4;i++){
      let line=[];
      if(dir==='left')line=[0,1,2,3].map(function(c){return board[i][c];});
      if(dir==='right')line=[3,2,1,0].map(function(c){return board[i][c];});
      if(dir==='up')line=[0,1,2,3].map(function(r){return board[r][i];});
      if(dir==='down')line=[3,2,1,0].map(function(r){return board[r][i];});
      const slid=slide(line);
      gained+=slid.filter(function(v){return v>0&&!line.includes(v);}).reduce(function(a,b){return a+b;},0);
      for(let k=0;k<4;k++){
        const val=slid[k];
        if(dir==='left'&&board[i][k]!==val)moved=true;
        if(dir==='right'&&board[i][3-k]!==val)moved=true;
        if(dir==='up'&&board[k][i]!==val)moved=true;
        if(dir==='down'&&board[3-k][i]!==val)moved=true;
        if(dir==='left')board[i][k]=val;
        if(dir==='right')board[i][3-k]=val;
        if(dir==='up')board[k][i]=val;
        if(dir==='down')board[3-k][i]=val;
      }
    }
    if(moved){
      score+=gained;
      if(score>best){best=score;localStorage.setItem('g2Best',best);}
      addTile();render();
      document.getElementById('g2Score').textContent='分数：'+score+'　最高：'+best;
      let won=false;
      for(let r=0;r<4&&!won;r++)for(let c=0;c<4;c++)if(board[r][c]===2048)won=true;
      if(won)setTimeout(function(){alert('🎉 合成 2048！继续冲 4096？');},120);
      else{let can=false;for(let r=0;r<4&&!can;r++)for(let c=0;c<4;c++){if(!board[r][c])can=true;if(c<3&&board[r][c]===board[r][c+1])can=true;if(r<3&&board[r][c]===board[r+1][c])can=true;}if(!can)setTimeout(function(){alert('没地方走了，分数：'+score);},120);}
    }
  }
  const handler=function(e){
    const k=e.key;
    if(['ArrowUp','ArrowDown','ArrowLeft','ArrowRight',' '].includes(k))e.preventDefault();
    if(k==='ArrowLeft'||k==='a'||k==='A')move('left');
    else if(k==='ArrowRight'||k==='d'||k==='D')move('right');
    else if(k==='ArrowUp'||k==='w'||k==='W')move('up');
    else if(k==='ArrowDown'||k==='s'||k==='S')move('down');
  };
  document.addEventListener('keydown',handler);
  reset();
  return function(){document.removeEventListener('keydown',handler);};
}

/* ===== 4. 扫雷 ===== */
function startMinesweeper(){
  const wrap=document.getElementById('gameContent');
  wrap.innerHTML='<h2>💣 扫雷</h2><div class="info" id="msInfo">左键挖 · 右键标记</div><div id="msGrid" style="display:inline-block;"></div><div class="info"><button class="restart-btn" onclick="startMinesweeper()">重新开始</button></div>';
  const W=9,H=9,MINES=12;
  let grid,revealed,flagged,gameOver;
  function reset(){
    grid=Array.from({length:H},function(){return Array.from({length:W},function(){return {mine:false,adj:0};});});
    revealed=Array.from({length:H},function(){return Array(W).fill(false);});
    flagged=Array.from({length:H},function(){return Array(W).fill(false);});
    gameOver=false;
    let placed=0;
    while(placed<MINES){
      const r=Math.floor(Math.random()*H),c=Math.floor(Math.random()*W);
      if(!grid[r][c].mine){grid/* ===== 5. 翻牌记忆 ===== */
function startMemory(){
  const wrap=document.getElementById('gameContent');
  wrap.innerHTML='<h2>🃏 翻牌记忆</h2><div class="info" id="memInfo">步数：0</div><div class="memory-grid" id="memGrid"></div><button class="restart-btn" onclick="startMemory()">换一局</button>';
  const icons=['🐶','🐱','🦊','🐻','🐼','🦁','🐯','🐸'];
  let cards,first,second,lock,steps;
  function reset(){
    cards=[];
    icons.forEach(function(ic){cards.push(ic,ic);});
    for(let i=cards.length-1;i>0;i--){
      const j=Math.floor(Math.random()*(i+1));
      const tmp=cards[i];cards[i]=cards[j];cards[j]=tmp;
    }
    first=null;second=null;lock=false;steps=0;
    document.getElementById('memInfo').textContent='步数：0';
    render();
  }
  function render(){
    const g=document.getElementById('memGrid');
    g.innerHTML='';
    cards.forEach(function(ic,i){
      const card=document.createElement('div');
      card.className='memory-card';
      card.dataset.i=i;
      card.textContent=ic;
      g.appendChild(card);
    });
    document.querySelectorAll('.memory-card').forEach(function(card){
      card.addEventListener('click',function(){
        if(lock)return;
        const i=+card.dataset.i;
        if(card.classList.contains('flipped')||card.classList.contains('matched'))return;
        card.classList.add('flipped');
        if(first===null)first=i;
        else {
          second=i;steps++;
          document.getElementById('memInfo').textContent='步数：'+steps;
          if(cards[first]===cards[second]){
            const els=document.querySelectorAll('.memory-card');
            setTimeout(function(){els[first].classList.add('matched');els[second].classList.add('matched');first=null;second=null;const left=document.querySelectorAll('.memory-card:not(.matched)').length;if(left===0)document.getElementById('memInfo').textContent='🎉 完成！共 '+steps+' 步';},250);
          } else {
            lock=true;
            const els=document.querySelectorAll('.memory-card');
            setTimeout(function(){els[first].classList.remove('flipped');els[second].classList.remove('flipped');first=null;second=null;lock=false;},700);
          }
        }
      });
    });
  }
  reset();
  return function(){};
}

/* ===== 6. 石头剪刀布 ===== */
function startRPS(){
  const wrap=document.getElementById('gameContent');
  wrap.innerHTML='<h2>✊ 石头剪刀布</h2><div class="info" id="rpsScore">你 0 : 0 电脑　连胜 0</div><div id="rpsBoard" style="font-size:60px;margin:18px 0;min-height:80px;">👊 vs 👊</div><div id="rpsMsg" style="color:#ffe877;font-size:16px;margin-bottom:14px;">三局两胜，选一个：</div><div><button class="restart-btn" onclick="pickRPS(0)">✊ 石头</button><button class="restart-btn" onclick="pickRPS(1)">✌️ 剪刀</button><button class="restart-btn" onclick="pickRPS(2)">🖐 布</button></div><button class="restart-btn" onclick="startRPS()">重开</button>';
  let pw=0,cw=0,streak=0;
  function pickRPS(you){
    if(pw>=2||cw>=2){pw=0;cw=0;}
    const arr=['✊','✌️','🖐'];
    const comp=Math.floor(Math.random()*3);
    let res;
    if(you===comp)res='平局';
    else if((you===0&&comp===1)||(you===1&&comp===2)||(you===2&&comp===0)){res='你赢了这局！';pw++;streak++;}
    else {res='电脑赢了这局';cw++;streak=0;}
    document.getElementById('rpsBoard').textContent=arr[you]+' vs '+arr[comp];
    document.getElementById('rpsMsg').textContent=res;
    document.getElementById('rpsScore').textContent='你 '+pw+' : '+cw+' 电脑　连胜 '+streak;
    if(pw>=2)setTimeout(function(){document.getElementById('rpsMsg').textContent='🎉 你赢了整局！';pw=0;cw=0;},400);
    if(cw>=2)setTimeout(function(){document.getElementById('rpsMsg').textContent='😢 电脑赢了整局，再来！';pw=0;cw=0;},400);
  }
  window.pickRPS=pickRPS;
  return function(){};
}

/* ===== 7. 恐龙跳跳 ===== */
function startDino(){
  const wrap=document.getElementById('gameContent');
  wrap.innerHTML='<h2>🦕 恐龙跳跳</h2><div class="info" id="dinoScore">距离：0　最高：0</div><canvas id="dinoCv" width="480" height="160"></canvas><div class="info">空格 / 上键 / 点屏幕跳跃</div><button class="restart-btn" onclick="startDino()">重新开始</button>';
  const cv=document.getElementById('dinoCv'),ctx=cv.getContext('2d');
  let dino,y,vy,gravity,jumping,obstacles,speed,score,timer,over,best=+localStorage.getItem('dinoBest')||0;
  function reset(){
    dino={x:60,w:30,h:34};y=126;vy=0;gravity=0.9;jumping=false;
    obstacles=[];speed=5;score=0;over=false;
    document.getElementById('dinoScore').textContent='距离：0　最高：'+best;
    if(timer)clearInterval(timer);
    timer=setInterval(loop,20);
  }
  function loop(){
    if(over)return;
    score+=1;
    if(score%300===0)speed+=0.4;
    if(!jumping&&(Math.random()<0.02||(obstacles.length&&obstacles[obstacles.length-1].x<300&&Math.random()<0.03))){
      obstacles.push({x:480,w:16,h:30});
    }
    vy+=gravity;y+=vy;
    if(y>=126){y=126;jumping=false;}
    obstacles.forEach(function(o){o.x-=speed;});
    obstacles=obstacles.filter(function(o){return o.x>-20;});
    for(let i=0;i<obstacles.length;i++){
      const o=obstacles[i];
      if(dino.x<o./* ===== 弹窗控制 ===== */
const games={snake:startSnake,tetris:startTetris,g2048:start2048,minesweeper:startMinesweeper,memory:startMemory,rps:startRPS,dino:startDino,lights:startLights};
let currentCleanup=null;
function openGame(name){
  const modal=document.getElementById('gameModal');
  modal.classList.add('open');
  document.getElementById('gameContent').innerHTML='';
  if(currentCleanup)currentCleanup();
  currentCleanup=games[name]()||null;
}
function closeGame(){
  document.getElementById('gameModal').classList.remove('open');
  if(currentCleanup)currentCleanup();
  currentCleanup=null;
}
document.getElementById('gameModal').addEventListener('click',function(e){
  if(e.target.id==='gameModal')closeGame();
});
document.addEventListener('keydown',function(e){
  if(e.key==='Escape')closeGame();
});

/* ===== 粒子生成 ===== */
const box=document.getElementById('particles');
for(let i=0;i<40;i++){
  const p=document.createElement('div');
  p.className='particle';
  const s=Math.random()*6+2;
  p.style.width=s+'px';
  p.style.height=s+'px';
  p.style.left=Math.random()*100+'vw';
  p.style.animationDuration=(Math.random()*10+8)+'s';
  p.style.animationDelay=(Math.random()*10)+'s';
  box.appendChild(p);
}
</script>
</body>
</html>
