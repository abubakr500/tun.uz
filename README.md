<!doctype html>
<html lang="uz">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>tun.uz</title>
  <meta name="description" content="Shok va breaking yangiliklar bilan to'la demo sayt. 140+ xabar, rasmli va interaktiv.">
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700;800&display=swap" rel="stylesheet">
  <style>
    /* ========================= RESET ========================= */
    *,*::before,*::after{box-sizing:border-box}
    html,body{height:100%}
    body{margin:0;font-family:Inter,system-ui,-apple-system,"Segoe UI",Roboto,'Helvetica Neue',Arial;background:#0f1724;color:#0b1220;line-height:1.45}
    img{max-width:100%;display:block}
    a{color:inherit;text-decoration:none}

    /* ========================= THEME ========================= */
    :root{
      --bg:#f8fafc;
      --card:#ffffff;
      --muted:#6b7280;
      --accent:#ff2d55;
      --accent-2:#ff6b6b;
      --glass:rgba(255,255,255,0.6);
      --radius:12px;
      --shadow:0 10px 30px rgba(2,6,23,0.08);
    }

    /* dark header */
    header{
      background:linear-gradient(90deg,#0b1220,#062033);
      color:#fff;
      padding:18px 20px;
      border-bottom:4px solid rgba(255,255,255,0.02);
      position:sticky;top:0;z-index:60;
    }

    .wrap{max-width:1260px;margin:0 auto;padding:14px}
    .topbar{display:flex;align-items:center;gap:16px}
    .logo{font-weight:800;font-size:20px;letter-spacing:0.4px}
    nav{margin-left:auto}
    nav ul{list-style:none;margin:0;padding:0;display:flex;gap:14px;align-items:center}
    nav li{padding:6px 10px;border-radius:8px}
    nav a{color:rgba(255,255,255,0.9);font-weight:600}
    .logo small{display:block;font-weight:400;font-size:12px;color:rgba(255,255,255,0.6)}

    /* ========================= HERO ========================= */
    .hero{display:grid;grid-template-columns:1fr 320px;gap:18px;align-items:start;margin-top:18px}
    .hero-card{background:linear-gradient(180deg,rgba(255,255,255,0.03),rgba(255,255,255,0.02));padding:20px;border-radius:12px;color:#fff;box-shadow:0 8px 30px rgba(2,6,23,0.35)}
    .hero h1{margin:0 0 8px 0;font-size:24px}
    .hero p{margin:0;color:rgba(255,255,255,0.85)}
    .search{display:flex;gap:8px;margin-top:14px}
    .search input{flex:1;padding:10px 12px;border-radius:10px;border:0;background:rgba(255,255,255,0.06);color:#fff;outline:none}
    .search button{padding:10px 14px;border-radius:10px;border:0;background:var(--accent);color:#fff;font-weight:700;cursor:pointer}

    /* ========================= LAYOUT ========================= */
    .main-grid{display:grid;grid-template-columns:1fr 320px;gap:20px;margin-top:20px}
    .articles{display:grid;grid-template-columns:repeat(auto-fill,minmax(260px,1fr));gap:18px}
    .card{background:var(--card);border-radius:12px;overflow:hidden;display:flex;flex-direction:column;min-height:260px;box-shadow:var(--shadow);border:1px solid rgba(2,6,23,0.04)}
    .card img{width:100%;height:160px;object-fit:cover;display:block;cursor:pointer}
    .c-body{padding:12px 14px;display:flex;flex-direction:column;flex:1}
    .kicker{font-size:12px;color:var(--muted);margin-bottom:6px}
    h3{margin:0;font-size:16px;color:#0b1220}
    .meta{font-size:13px;color:var(--muted);margin-top:6px}
    .excerpt{flex:1;margin-top:8px;color:#334155}
    .readmore{margin-top:12px;align-self:flex-start;padding:8px 10px;border-radius:8px;background:transparent;border:1px solid rgba(2,6,23,0.06);cursor:pointer}

    /* ========================= SIDEBAR ========================= */
    aside .widget{background:var(--card);padding:14px;border-radius:12px;margin-bottom:14px;box-shadow:0 6px 18px rgba(2,6,23,0.03)}
    .tag{display:inline-block;padding:6px 10px;border-radius:999px;background:rgba(255,45,85,0.06);color:var(--accent);font-weight:700;font-size:12px}

    /* ========================= PAGINATION ========================= */
    .pagination{display:flex;gap:8px;justify-content:center;margin-top:18px;flex-wrap:wrap}
    .pagination button{padding:8px 12px;border-radius:8px;border:1px solid rgba(2,6,23,0.06);background:#fff;cursor:pointer}
    .pagination button[disabled]{opacity:0.6;cursor:default}

    /* ========================= FOOTER ========================= */
    footer{margin-top:32px;padding:18px;background:#071020;color:#cfe9ff}

    /* ========================= MODAL ========================= */
    #modal{position:fixed;inset:0;display:none;align-items:center;justify-content:center;background:rgba(2,6,23,0.6);z-index:9999}
    .modal-box{background:#fff;border-radius:12px;max-width:920px;width:94%;max-height:90%;overflow:auto;padding:18px;position:relative}
    .modal-box img{width:100%;height:auto;border-radius:8px;margin-bottom:12px}
    .modal-close{position:absolute;right:12px;top:12px;border:0;background:transparent;font-size:20px;cursor:pointer}

    /* ========================= UTILITIES ========================= */
    .u-p-0{padding:0}.u-p-4{padding:4px}.u-p-8{padding:8px}.u-p-12{padding:12px}.u-p-16{padding:16px}
    .u-m-0{margin:0}.u-m-4{margin:4px}.u-m-8{margin:8px}.u-m-12{margin:12px}.u-m-16{margin:16px}
    .f-100{font-size:100%}.f-90{font-size:90%}.f-110{font-size:110%}
    .d-flex{display:flex}.d-block{display:block}.d-grid{display:grid}
    .col-center{display:flex;align-items:center;justify-content:center}
    .text-center{text-align:center}
    .rounded-sm{border-radius:6px}.rounded-md{border-radius:10px}.rounded-lg{border-radius:14px}
    .shadow-sm{box-shadow:0 6px 12px rgba(2,6,23,0.04)}.shadow-md{box-shadow:0 10px 30px rgba(2,6,23,0.06)}
    .accent{color:var(--accent)}.muted{color:var(--muted)}
    .g1{gap:4px}.g2{gap:8px}.g3{gap:12px}.g4{gap:16px}.g5{gap:20px}
    .b-1{border:1px solid rgba(2,6,23,0.04)}.b-2{border:2px solid rgba(2,6,23,0.04)}
    .hide{display:none}.show{display:block}
    @media (max-width:980px){
      .main-grid{grid-template-columns:1fr}
      .hero{grid-template-columns:1fr}
      nav ul{display:none}
    }
  </style>
</head>
<body>
  <header>
    <div class="wrap topbar">
      <div>
        <div class="logo">MUKAMMAL<span style="color:var(--accent)"> NEWS</span></div>
        <small style="color:rgba(255,255,255,0.6)">Shok & Breaking yangiliklar </small>
      </div>
      <nav>
        <ul>
          <li><a href="#">Bosh</a></li>
          <li><a href="#">So'nggi</a></li>
          <li><a href="#">Shok</a></li>
          <li><a href="#">Tahlil</a></li>
          <li><a href="#">Sport</a></li>
          <li><a href="#">Kontakt</a></li>
        </ul>
      </nav>
    </div>

    <div class="wrap hero">
      <div class="hero-card">
        <div class="kicker">Breaking / Shok</div>
        <h1>Shok yangiliklar — tezkor vizual reportajlar</h1>
        <p>Bu sahifada "shok" tasvirlari (favqulodda hodisa, fojiya, portlash, to'qnashuv, tartibsizlik va h.k.) tegishli kategoriyalar bilan ko'rsatiladi.</p>
        <div class="search">
          <input id="searchInput" placeholder="Sarlavha yoki izoh bo'yicha qidiruv..." />
          <button id="searchBtn">Qidir</button>
        </div>
        <div style="margin-top:10px">
          <span class="tag">SHOK</span>
          <span class="tag" style="background:rgba(0,119,255,0.06);color:#0077ff;margin-left:8px;">LIVE</span>
        </div>
      </div>

      <aside style="align-self:start">
        <div class="widget">
          <h4>Trend mavzular</h4>
          <ul style="padding-left:16px;margin:8px 0 0 0;color:var(--muted)">
            <li>Accident / Crash</li>
            <li>Fire / Explosion</li>
            <li>Protest / Riot</li>
            <li>Political</li>
            <li>Sport incidents</li>
          </ul>
        </div>

        <div class="widget">
          <h4>Kontakt</h4>
          <p style="color:var(--muted)">contact@mukammalnews.uz</p>
        </div>
      </aside>
    </div>
  </header>

  <main class="wrap main-grid" id="main">
    <section>
      <div style="display:flex;justify-content:space-between;align-items:center">
        <h2 style="margin:0;color:#07102a">So'nggi xabarlar</h2>
        <div id="countBadge" style="padding:6px 10px;border-radius:8px;background:var(--card);font-weight:700;color:var(--accent)">Yuklanmoqda...</div>
      </div>

      <div class="articles" id="articles">
        <!-- JS will inject 140 articles -->
      </div>

      <div class="pagination" id="pagination" aria-label="Pagination"></div>
    </section>

    <aside>
      <div class="widget">
        <h4>Filtrlar</h4>
        <div style="display:flex;flex-direction:column;gap:8px;margin-top:8px">
          <select id="filterCategory" style="padding:8px;border-radius:8px;border:1px solid rgba(2,6,23,0.06)">
            <option value="">Barcha kategoriyalar</option>
            <option>Shok</option>
            <option>Accident</option>
            <option>Fire</option>
            <option>Protest</option>
            <option>Sport</option>
            <option>Politics</option>
            <option>Economy</option>
            <option>Health</option>
          </select>
          <button id="filterBtn" style="padding:8px;border-radius:8px;border:0;background:var(--accent);color:#fff;cursor:pointer">Filtrlash</button>
          <button id="clearFilter" style="padding:8px;border-radius:8px;border:1px solid rgba(2,6,23,0.06);background:#fff;cursor:pointer">Tozalash</button>
        </div>
      </div>

      <div class="widget">
        <h4>So'nggi shoklar</h4>
        <ol style="padding-left:16px;margin:8px 0 0 0;color:var(--muted)">
          <li>Avtohalokat — hududiy yo'llar</li>
          <li>Yong'in — sanoat zonasi</li>
          <li>Namoyish — markaziy maydon</li>
        </ol>
      </div>
    </aside>
  </main>

  <footer>
    <div class="wrap">
      <strong style="color:#fff">Mukammal News — Shok</strong>
      <p style="margin:8px 0 0 0;color:var(--muted)">Demo sayt · 140+ rasmli yangilik · HTML + CSS + JS bir faylda</p>
    </div>
  </footer>

  <!-- Modal for detailed article -->
  <div id="modal" role="dialog" aria-modal="true" aria-labelledby="modalTitle">
    <div class="modal-box">
      <button class="modal-close" id="modalClose" aria-label="Close">✕</button>
      <img id="modalImg" src="" alt="">
      <h3 id="modalTitle"></h3>
      <p id="modalMeta" style="color:var(--muted)"></p>
      <p id="modalBody"></p>
    </div>
  </div>

  <script>
  (function(){
    // ------- CONFIG -------
    const articlesWrap = document.getElementById('articles');
    const countBadge = document.getElementById('countBadge');
    const paginationEl = document.getElementById('pagination');
    const searchInput = document.getElementById('searchInput');
    const searchBtn = document.getElementById('searchBtn');
    const filterCategory = document.getElementById('filterCategory');
    const filterBtn = document.getElementById('filterBtn');
    const clearFilter = document.getElementById('clearFilter');

    // 🔥 YANGI: HAR KATEGORIYA UCHUN MOS RASM TOPICLARI
    const categoryToTopic = {
      'Shok': ['accident,crash,car', 'fire,explosion,smoke', 'disaster,storm,flood', 'building,collapse,ruins', 'ambulance,emergency,waiting'],
      'Accident': ['car,accident,crash', 'motorcycle,crash,road', 'truck,rollover,highway', 'train,derailment,crash'],
      'Fire': ['fire,explosion,flames', 'building,on fire', 'forest,fire,smoke', 'gas,leak,firefighters'],
      'Protest': ['protest,riot,crowd', 'people,demonstration,signs', 'police,protester,clash', 'roadblock,protest,riot'],
      'Police': ['police,crime,investigation', 'handcuffs,arrest,officer', 'police,raid,suspect', 'crime,scene,evidence'],
      'Disaster': ['flood,city,water', 'earthquake,building,debris', 'hurricane,wind,roof', 'landslide,rock,house'],
      'Sport': ['soccer,match,chaos', 'stadium,riot,crowd', 'player,injured,medical', 'boxing,ring,brawl', 'tennis,argument,umpire'],
      'Politics': ['politician,speech,stage', 'parliament,debate,conflict', 'president,press,conference', 'election,ballot,vote'],
      'Economy': ['stock,market,fall', 'bank,close,empty', 'workers,strike,protest', 'business,collapse,sign', 'inflation,price,shop'],
      'Health': ['hospital,emergency,waiting', 'doctor,mask,patient', 'epidemic,mask,face', 'clinic,overcrowded,queue']
    };

    // Barcha topiclar ro'yxati (moslik uchun)
    const shokTopics = Object.values(categoryToTopic).flat();

    const TOTAL = 140;
    const perPage = 12;

    // Helper: build image URL
    function imgUrl(i, topic){
      return `https://source.unsplash.com/1200x800/?${encodeURIComponent(topic)}&sig=${i}`;
    }

    // Build sample data array with "shock" categories and titles
    const categories = ['Shok','Accident','Fire','Protest','Police','Disaster','Sport','Politics','Economy','Health'];
    const sampleNews = [];
    for(let i=1;i<=TOTAL;i++){
      const category = categories[(i-1) % categories.length];

      // 👇 Kategoriyaga mos rasm topicini tanlash
      const possibleTopics = categoryToTopic[category] || ['accident,crash,car'];
      const topic = possibleTopics[(i-1) % possibleTopics.length];

      const titleKey = {
        'Shok': ['Favqulodda hodisa', 'Kutilmagan voqea', 'Tezkor xabar'],
        'Accident': ['Yo‘l-transport hodisasi', 'Avtohalokat', 'Traktor va mashina to‘qnashuvi'],
        'Fire': ['Yong‘in', 'Portlash', 'Zaharli tutun'],
        'Protest': ['Namoyish', 'To‘qnashuv', 'Tartibsizlik'],
        'Police': ['Politsiya tergov', 'Qo‘lga olish', 'Jinoyat tafsilotlari'],
        'Disaster': ['Tabiiy ofat', 'Sel', 'Qattiq bo‘ron'],
        'Sport': ['Maydon to‘qnashuvi', 'Stadionda hodisa', 'Sportchi jarohati'],
        'Politics': ['Siyosiy voqea', 'Majlis yangiliklari', 'Vakolat muhokamasi'],
        'Economy': ['Iqtisodiy halokat', 'Bozor inqirozi', 'Investitsiya to‘siqlari'],
        'Health': ['Sog‘liq favqulodda', 'Epidemiya, ogohlantirish', 'Tibbiy holat']
      };
      const titles = titleKey[category] || ['Yangilik'];
      const title = `${i}. ${titles[i % titles.length]} — ${category} yangiligi`;
      const excerpt = `Bu ${category} kategoriyasiga oid shok xabar №${i}. Ilgari e'lon qilingan dalillar va holatlar tezkor tarzda yangilanadi.`;
      sampleNews.push({
        id: i,
        title,
        category,
        time: `${(i%23)+1} soat oldin`,
        author: (i%3===0)? 'Editor' : 'Reporter',
        comments: Math.floor(Math.random()*500),
        img: imgUrl(i, topic),
        excerpt,
        body: `${title}\n\nTo'liq ma'lumot: Bu namunaviy maqola №${i}. Ushbu bo'limda hodisa tafsilotlari, rasmiy manbalar, guvohlar va yangilanishlar ko'rsatiladi.`
      });
    }

    // Render functions
    function renderAll(){
      articlesWrap.innerHTML = '';
      sampleNews.forEach(item=>{
        const art = document.createElement('article');
        art.className = 'card';
        art.setAttribute('data-category', item.category);
        art.innerHTML = `
          <img src="${item.img}" alt="${escapeHtml(item.category)}: ${escapeHtml(item.excerpt.substring(0, 50))}..." data-id="${item.id}">
          <div class="c-body">
            <div class="kicker">${item.category} • ${item.time}</div>
            <h3>${escapeHtml(item.title)}</h3>
            <div class="meta">By ${item.author} • ${item.comments} ta izoh</div>
            <p class="excerpt">${escapeHtml(item.excerpt)}</p>
            <button class="readmore" data-id="${item.id}">Batafsil</button>
          </div>
        `;
        articlesWrap.appendChild(art);
      });
      countBadge.textContent = sampleNews.length + ' ta xabar';
      renderPagination();
    }

    function escapeHtml(s){
      return String(s).replace(/&/g,'&amp;').replace(/</g,'<').replace(/>/g,'>');
    }

    // SEARCH
    function doSearch(){
      const q = searchInput.value.trim().toLowerCase();
      const cards = Array.from(articlesWrap.querySelectorAll('.card'));
      if(!q){
        cards.forEach(c=>c.style.display='flex');
        renderPagination();
        return;
      }
      cards.forEach(c=>{
        const t = c.querySelector('h3')?.textContent?.toLowerCase()||'';
        const e = c.querySelector('.excerpt')?.textContent?.toLowerCase()||'';
        if(t.includes(q) || e.includes(q)) c.style.display='flex'; else c.style.display='none';
      });
      paginationEl.style.display = 'none';
    }

    // FILTER
    function applyFilter(){
      const v = filterCategory.value;
      const cards = Array.from(articlesWrap.querySelectorAll('.card'));
      if(!v){
        cards.forEach(c=>c.style.display='flex');
        renderPagination();
        return;
      }
      cards.forEach(c=>{
        if(c.getAttribute('data-category') === v) c.style.display='flex'; else c.style.display='none';
      });
      paginationEl.style.display = 'none';
    }

    clearFilter.addEventListener('click', ()=>{
      filterCategory.value = '';
      renderPagination();
      document.getElementById('pagination').style.display = 'flex';
    });

    filterBtn.addEventListener('click', applyFilter);
    searchBtn.addEventListener('click', doSearch);
    searchInput.addEventListener('keydown', e=>{ if(e.key === 'Enter') doSearch() });

    // PAGINATION
    function renderPagination(){
      const cards = Array.from(articlesWrap.querySelectorAll('.card'));
      const visible = cards.filter(c => c.style.display !== 'none');
      const total = visible.length || cards.length;
      const pages = Math.ceil(total / perPage);
      paginationEl.innerHTML = '';
      for(let p=1;p<=pages;p++){
        const btn = document.createElement('button');
        btn.textContent = p;
        btn.addEventListener('click', ()=> showPage(p));
        paginationEl.appendChild(btn);
      }
      if(pages>0) showPage(1);
      paginationEl.style.display = pages>1 ? 'flex' : 'none';
    }

    function showPage(page){
      const cards = Array.from(articlesWrap.querySelectorAll('.card'));
      const visible = cards.filter(c => c.style.display !== 'none');
      const list = visible.length ? visible : cards;
      list.forEach((c, idx)=>{
        const p = Math.floor(idx / perPage) + 1;
        c.style.display = (p === page) ? 'flex' : 'none';
      });
      const btns = Array.from(paginationEl.children);
      btns.forEach((b,i)=> b.disabled = (i+1) === page);
    }

    // MODAL
    const modal = document.getElementById('modal');
    const modalImg = document.getElementById('modalImg');
    const modalTitle = document.getElementById('modalTitle');
    const modalMeta = document.getElementById('modalMeta');
    const modalBody = document.getElementById('modalBody');
    const modalClose = document.getElementById('modalClose');

    function openModal(id){
      const item = sampleNews.find(s => s.id === Number(id));
      if(!item) return;
      modalImg.src = item.img;
      modalTitle.textContent = item.title;
      modalMeta.textContent = `${item.category} • ${item.time} • By ${item.author}`;
      modalBody.textContent = item.body;
      modal.style.display = 'flex';
      document.body.style.overflow = 'hidden';
    }
    function closeModal(){ modal.style.display = 'none'; document.body.style.overflow = '' }
    modalClose.addEventListener('click', closeModal);
    modal.addEventListener('click', e => { if(e.target === modal) closeModal(); });
    document.addEventListener('keydown', e => { if(e.key === 'Escape') closeModal(); });

    // Click delegation for readmore and image click
    document.body.addEventListener('click', e=>{
      if(e.target.classList.contains('readmore')){
        openModal(e.target.getAttribute('data-id'));
      }
      if(e.target.tagName === 'IMG' && e.target.closest('.card')){
        openModal(e.target.getAttribute('data-id'));
      }
    });

    // INITIALIZE
    renderAll();

    // Lazy-load images
    function lazyLoadImages(){
      const imgs = document.querySelectorAll('img[data-src], img[src]');
      if('IntersectionObserver' in window){
        const io = new IntersectionObserver((entries, obs) => {
          entries.forEach(entry=>{
            if(entry.isIntersecting){
              const img = entry.target;
              if(img.dataset.src){ img.src = img.dataset.src; }
              obs.unobserve(img);
            }
          });
        }, {rootMargin: '200px'});
        imgs.forEach(img => io.observe(img));
      }
    }
    lazyLoadImages();

  })();
  </script>
</body>
</html>
