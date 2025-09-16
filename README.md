<!doctype html>
<html lang="id">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Quiz: Recount Texts (Home Alone & My Roblox Conversation)</title>
  <style>
    :root{--bg:#0f172a;--card:#0b1220;--accent:#06b6d4;--muted:#94a3b8;--white:#eef2ff}
    body{font-family:Inter,ui-sans-serif,system-ui,Segoe UI,Roboto,"Helvetica Neue",Arial;background:linear-gradient(180deg,#031025 0%, #06233a 100%);color:var(--white);padding:24px}
    .container{max-width:900px;margin:0 auto}
    header{display:flex;align-items:center;gap:16px;margin-bottom:18px}
    h1{margin:0;font-size:20px}
    .card{background:rgba(255,255,255,0.03);border-radius:12px;padding:18px;box-shadow:0 6px 18px rgba(2,6,23,0.6)}
    .text-block{background:rgba(255,255,255,0.02);padding:12px;border-radius:8px;margin-bottom:12px;color:var(--muted);line-height:1.6}
    .question{margin:14px 0;padding:12px;border-radius:8px;background:rgba(255,255,255,0.01)}
    .options{display:flex;flex-direction:column;gap:8px;margin-top:8px}
    label.option{background:rgba(255,255,255,0.02);padding:10px;border-radius:8px;cursor:pointer;display:flex;align-items:center;gap:10px}
    input[type="radio"]{accent-color:var(--accent)}
    .controls{display:flex;gap:8px;align-items:center;justify-content:space-between;margin-top:12px}
    button{background:var(--accent);border:none;padding:10px 12px;border-radius:8px;color:#021124;cursor:pointer;font-weight:600}
    button.ghost{background:transparent;border:1px solid rgba(255,255,255,0.06);color:var(--white)}
    .progress{height:10px;background:rgba(255,255,255,0.04);border-radius:999px;overflow:hidden}
    .progress > i{display:block;height:100%;background:linear-gradient(90deg,var(--accent),#60a5fa)}
    .result{text-align:center;padding:18px}
    .meta{display:flex;gap:8px;align-items:center}
    .small{font-size:13px;color:var(--muted)}
    .review{margin-top:12px;text-align:left}
    .send{margin-top:10px;display:flex;gap:8px}
    input[type="text"]{padding:8px;border-radius:8px;border:1px solid rgba(255,255,255,0.04);background:transparent;color:var(--white);width:240px}
    footer{margin-top:18px;color:var(--muted);font-size:13px}
    @media(max-width:600px){.meta{flex-direction:column;align-items:flex-start}}
  </style>
</head>
<body>
  <div class="container">
    <header>
      <div>
        <h1>Quiz Interaktif: Recount Texts — <span class="small">(Home Alone & My Roblox Conversation)</span></h1>
        <div class="small">20 soal — otomatis hitung skor. Masukkan nama sebelum mulai.</div>
      </div>
    </header>

    <div class="card">
      <div style="display:flex;gap:8px;align-items:center;margin-bottom:12px">
        <input id="studentName" type="text" placeholder="Nama siswa (contoh: Aira)" />
        <button id="startBtn">Mulai Quiz</button>
        <button id="restartBtn" class="ghost">Reset</button>
      </div>

      <div id="quizArea" style="display:none">
        <div class="meta">
          <div class="small">Soal <span id="qNumber">1</span> / <span id="qTotal">20</span></div>
          <div style="flex:1" class="progress" aria-hidden><i id="progBar" style="width:0%"></i></div>
          <div class="small">Skor: <span id="liveScore">0</span></div>
        </div>

        <div id="contentArea" style="margin-top:12px"></div>

        <div class="controls">
          <div>
            <button id="prevBtn" class="ghost">Sebelumnya</button>
            <button id="nextBtn">Selanjutnya</button>
          </div>
          <div class="small">Pilih satu jawaban lalu tekan "Selanjutnya"</div>
        </div>
      </div>

      <div id="resultArea" style="display:none">
        <div class="result card">
          <h2 id="finalMsg">Quiz Selesai! 🎉</h2>
          <p class="small">Nama: <strong id="resName"></strong></p>
          <p style="font-size:18px">Skor kamu: <strong id="resScore"></strong> / <span id="resTotal"></span></p>
          <div class="send">
            <input id="sheetUrl" type="text" placeholder="(opsional) URL Web App Google Scripts" />
            <button id="sendBtn">Kirim ke Google Sheet</button>
          </div>
          <div id="sendMsg" class="small" style="margin-top:8px;color:#9fe6ff"></div>

          <div class="review" id="reviewArea"></div>
        </div>
      </div>

    </div>

    <footer>Tips: Jika mau rekap otomatis, deploy Google Apps Script sebagai Web App dan paste URL-nya di kolom "URL Web App" lalu tekan "Kirim ke Google Sheet".</footer>
  </div>

  <script>
    // Texts
    const homeAlone = `Last month, I had an unforgettable experience. My parents went to my grandmother's house for the weekend, and I had to stay home alone because I had extra classes at school. At first, I was very excited because I felt free to do anything I wanted.\n\nOn the first night, I cooked instant noodles for dinner and watched my favorite movie. Everything felt fun until I heard strange noises from the kitchen. My heart beat so fast! I grabbed a broomstick and carefully walked to the kitchen. Luckily, it was only the cat knocking down a glass. I laughed at myself for being so scared.\n\nThe next morning, I cleaned the house, washed the dishes, and even did my homework earlier than usual. In the evening, I talked to my parents on the phone and told them about my “adventure.”\n\nStaying home alone taught me something important: being independent is not easy, but it can make me stronger and more responsible.`;

    const roblox = `Last week, I had a funny and unforgettable experience when I played Roblox with my friends. We joined a roleplay game where everyone had to talk and act like real characters. At first, I just typed normal sentences, but then one of my friends started joking around and the chat turned into a very random conversation.\n\nWe laughed so hard because someone pretended to be a teacher, while another acted as a lost student who couldn't find the classroom. I joined the joke by becoming the “janitor” who gave directions in a dramatic way. The whole chat was full of laughter and silly emojis.\n\nAt the end, we realized that even though it was just a game, the conversation made us feel closer as friends. It was a simple but fun experience, and I learned that online games can also create real moments of joy and connection.`;

    // Questions (from user)
    const questions = [
      // Home Alone (1-10)
      { q: "Why did the writer feel both excited and scared during the weekend?", opts: [
          "Because he was free and also faced unexpected situations",
          "Because his parents told him to be careful",
          "Because the cat attacked him at night",
          "Because he was not allowed to watch TV"
        ], a:0 },
      { q: "If the glass had broken and hurt the cat, what should the writer have done first?", opts: [
          "Call his parents immediately",
          "Clean the kitchen and ignore the cat",
          "Give first aid to the cat and keep it safe",
          "Leave the house and go to the neighbor’s"
        ], a:2 },
      { q: "What lesson can students apply from the writer’s experience in their daily lives?", opts:[
          "Watching movies late at night is fun",
          "Being independent means doing chores and managing yourself",
          "Cooking instant noodles is the easiest way to survive",
          "Staying at home alone is always scary"
        ], a:1 },
      { q: "How would the story change if the writer had invited a friend to stay over?", opts:[
          "The story would be about friendship, not independence",
          "The cat would not make any noise",
          "The parents would punish him for inviting friends",
          "The writer would not cook noodles at all"
        ], a:0 },
      { q: "What does the text suggest about facing fears when alone?", opts:[
          "Fears should always be avoided",
          "Fears can help us learn responsibility and bravery",
          "Fears only make us weak",
          "Fears disappear if parents are at home"
        ], a:1 },
      { q: "If the writer had not been brave enough to check the kitchen, what might have happened?", opts:[
          "He would stay scared all night",
          "The parents would come home earlier",
          "The cat would clean the glass by itself",
          "He would forget to eat his noodles"
        ], a:0 },
      { q: "Which part of the story shows the writer’s growth in responsibility?", opts:[
          "Cooking noodles for dinner",
          "Cleaning the house and doing homework earlier",
          "Watching his favorite movie",
          "Talking on the phone with his parents"
        ], a:1 },
      { q: "What could be the impact if the writer always depends on his parents instead of being independent?", opts:[
          "He will become more creative",
          "He may lack problem-solving skills",
          "He will always be confident",
          "He will never feel scared"
        ], a:1 },
      { q: "How does the writer’s experience relate to students’ real life?", opts:[
          "Students also learn independence when they do their own tasks",
          "Students should never stay home alone",
          "Students should always call their parents for every problem",
          "Students only learn responsibility at school"
        ], a:0 },
      { q: "If you were the writer, what would you do differently in that situation?", opts:[
          "Sleep without worrying about the noises",
          "Call a friend to play games together",
          "Use the situation to practice more independence and bravery",
          "Leave the house until the parents come back"
        ], a:2 },

      // Roblox (11-20)
      { q: "Why did the writer describe the Roblox chat as unforgettable?", opts:[
          "Because they played seriously without laughing",
          "Because the conversation turned funny and random",
          "Because the game ended too quickly",
          "Because nobody wanted to join the roleplay"
        ], a:1 },
      { q: "What lesson can we learn from the writer’s experience?", opts:[
          "Online games are only for wasting time",
          "Conversations in games can build friendship and joy",
          "Playing Roblox is better than studying",
          "Joking online is always dangerous"
        ], a:1 },
      { q: "If the writer had not joined the joke as a janitor, how might the story have been different?", opts:[
          "The conversation would be less fun and creative",
          "The players would stop playing Roblox",
          "The friends would get angry at him",
          "The teacher character would leave the game"
        ], a:0 },
      { q: "How does the story relate to students’ real life?", opts:[
          "Students can learn teamwork and humor even in online spaces",
          "Students should never chat while playing games",
          "Students only laugh when they are offline",
          "Students must roleplay as teachers in real life"
        ], a:0 },
      { q: "If you were in the same game, what role would you choose to make the conversation more fun?", opts:[
          "A robot giving strict rules",
          "A friendly shopkeeper selling funny items",
          "A silent player who never types anything",
          "A referee who ends the game early"
        ], a:1 },
      { q: "Why did the writer mention silly emojis in the chat?", opts:[
          "To show how serious the roleplay was",
          "To highlight the fun and playful atmosphere",
          "To explain that emojis are necessary in every chat",
          "To show that they couldn’t type words"
        ], a:1 },
      { q: "If one of the friends had refused to roleplay, what might have happened?", opts:[
          "The game would still be funny",
          "The interaction might not be as engaging",
          "The chat would continue without humor",
          "Everyone would leave Roblox immediately"
        ], a:1 },
      { q: "What is the deeper message behind the writer’s experience?", opts:[
          "Games are only fun when they are random",
          "Friendship can grow through shared laughter and creativity",
          "Roblox is the best game in the world",
          "Roleplaying is more important than studying"
        ], a:1 },
      { q: "How would the story be different if the writer played alone?", opts:[
          "The story would focus on the game itself, not the conversation",
          "The writer would still laugh with emojis",
          "The janitor role would be even funnier",
          "The teacher character would still appear"
        ], a:0 },
      { q: "What skill did the writer unintentionally practice through the roleplay?", opts:[
          "Speaking formally in English",
          "Creative communication and collaboration",
          "Memorizing school lessons",
          "Avoiding responsibilities"
        ], a:1 }
    ];

    // State
    let idx = 0;
    const total = questions.length;
    const answers = new Array(total).fill(null);
    const startBtn = document.getElementById('startBtn');
    const restartBtn = document.getElementById('restartBtn');
    const quizArea = document.getElementById('quizArea');
    const contentArea = document.getElementById('contentArea');
    const qNumber = document.getElementById('qNumber');
    const qTotal = document.getElementById('qTotal');
    const progBar = document.getElementById('progBar');
    const liveScore = document.getElementById('liveScore');
    const prevBtn = document.getElementById('prevBtn');
    const nextBtn = document.getElementById('nextBtn');
    const resultArea = document.getElementById('resultArea');
    const resName = document.getElementById('resName');
    const resScore = document.getElementById('resScore');
    const resTotal = document.getElementById('resTotal');
    const reviewArea = document.getElementById('reviewArea');
    const sendBtn = document.getElementById('sendBtn');
    const sendMsg = document.getElementById('sendMsg');

    document.getElementById('qTotal').textContent = total;

    function renderQuestion(i){
      const item = questions[i];
      let html = '';
      // If first two questions show text orientation? We'll show the related text above first question block
      if(i === 0){ html += `<div class="text-block"><strong>Home Alone</strong><br>${homeAlone.replace(/\n/g,'<br>')}</div>`; }
      if(i === 10){ html += `<div class="text-block"><strong>My Roblox Conversation</strong><br>${roblox.replace(/\n/g,'<br>')}</div>`; }

      html += `<div class="question"><div><strong>Q${i+1}.</strong> ${item.q}</div><div class="options">`;
      item.opts.forEach((op, j)=>{
        const id = `opt_${i}_${j}`;
        const checked = answers[i] === j ? 'checked' : '';
        html += `<label class="option"><input type="radio" name="q${i}" id="${id}" value="${j}" ${checked}> <span>${String.fromCharCode(65+j)}. ${op}</span></label>`;
      });
      html += `</div></div>`;
      contentArea.innerHTML = html;
      qNumber.textContent = i+1;
      progBar.style.width = Math.round(((i)/total)*100) + '%';

      // attach listeners
      item.opts.forEach((op, j)=>{
        const el = document.getElementById(`opt_${i}_${j}`);
        el.addEventListener('change', ()=>{
          answers[i] = j;
          updateLiveScore();
        });
      });
    }

    function updateLiveScore(){
      let s = 0;
      for(let i=0;i<total;i++){
        if(answers[i] !== null && answers[i] === questions[i].a) s++;
      }
      liveScore.textContent = s;
    }

    nextBtn.addEventListener('click', ()=>{
      // ensure answered
      if(answers[idx] === null){ if(!confirm('Belum jawab soal ini. Lanjut tanpa jawaban?')) return; }
      if(idx < total-1){ idx++; renderQuestion(idx);} else { finishQuiz(); }
    });

    prevBtn.addEventListener('click', ()=>{
      if(idx>0){ idx--; renderQuestion(idx);} });

    startBtn.addEventListener('click', ()=>{
      const name = document.getElementById('studentName').value.trim();
      if(!name){ if(!confirm('Nama kosong. Lanjut tanpa nama?')) return; }
      document.querySelector('#quizArea').style.display = 'block';
      startBtn.disabled = true;
      document.getElementById('studentName').disabled = true;
      renderQuestion(0);
    });

    restartBtn.addEventListener('click', ()=>{
      if(!confirm('Reset quiz? Semua jawaban akan hilang.')) return;
      idx = 0; answers.fill(null); updateLiveScore(); renderQuestion(0);
      startBtn.disabled = false; document.getElementById('studentName').disabled = false;
      document.querySelector('#quizArea').style.display = 'none'; resultArea.style.display = 'none'; sendMsg.textContent = '';
    });

    function finishQuiz(){
      // calculate score
      let s = 0; for(let i=0;i<total;i++){ if(answers[i] !== null && answers[i] === questions[i].a) s++; }
      document.getElementById('quizArea').style.display = 'none';
      resultArea.style.display = 'block';
      resName.textContent = document.getElementById('studentName').value || '(Tidak diisi)';
      resScore.textContent = s;
      resTotal.textContent = total;
      // review
      let rev = '<h3 class="small">Review Jawaban</h3>';
      questions.forEach((it, i)=>{
        const user = answers[i];
        const correct = it.a;
        const isOk = user === correct;
        rev += `<div style="margin-bottom:10px;padding:8px;border-radius:8px;background:rgba(255,255,255,0.01)"><strong>Q${i+1}.</strong> ${it.q}<br><em class="small">Jawaban kamu: </em> ${user===null?'<span style="color:var(--muted)">(kosong)</span>':String.fromCharCode(65+user)+'. '+it.opts[user]}<br><em class="small">Jawaban benar: </em><strong>${String.fromCharCode(65+correct)+'. '+it.opts[correct]}</strong><div style="margin-top:6px;color:' + (isOk? '#9fe6ff' : '#ffb3b3') + '"><strong>'+(isOk? 'Benar ✅':'Salah ❌')+'</strong></div></div>`;
      });
      reviewArea.innerHTML = rev;

      // attach send
    }

    sendBtn.addEventListener('click', async ()=>{
      const url = document.getElementById('sheetUrl').value.trim();
      if(!url){ alert('Masukkan URL Web App Google Script untuk mengirim nilai.'); return; }
      // calculate final
      let s = 0; for(let i=0;i<total;i++){ if(answers[i] !== null && answers[i] === questions[i].a) s++; }
      const payload = {
        name: document.getElementById('studentName').value || '(Tidak diisi)',
        score: s,
        total: total,
        timestamp: new Date().toISOString()
      };
      try{
        sendMsg.textContent = 'Mengirim...';
        const res = await fetch(url, { method:'POST', headers:{'Content-Type':'application/json'}, body:JSON.stringify(payload)});
        const json = await res.json();
        sendMsg.textContent = json.status? (json.status + ' — ' + (json.message||'')) : 'Terkirim.';
      }catch(err){ sendMsg.textContent = 'Gagal kirim: '+err.message; }
    });

    // initial render hidden
    const resultAreaEl = document.getElementById('resultArea');
    // Expose finish for direct call from Next on last
    const resultArea = resultAreaEl;
  </script>
</body>
</html>
