# Chalinee.github.io
<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Cha Liris — 3D Portfolio</title>
  <meta name="description" content="Cha Liris — Digital Art, 3D Modeling, Game Design portfolio." />

  <!-- Three.js: โหลดจาก CDN เพื่อให้ไฟล์นี้เป็น index.html ไฟล์เดียว -->
  <script type="importmap">
  {
    "imports": {
      "three": "https://cdn.jsdelivr.net/npm/three@0.180.0/build/three.module.js",
      "three/addons/": "https://cdn.jsdelivr.net/npm/three@0.180.0/examples/jsm/"
    }
  }
  </script>

  <style>
    @import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700&family=Playfair+Display:wght@500;600;700&family=Noto+Sans+Thai:wght@400;500;600;700&display=swap');

    :root{
      --cream:#efe2ca;
      --cream-light:#f7f1e7;
      --milk:#fffaf2;
      --brown:#8a6946;
      --brown-dark:#624a34;
      --beige:#cfbba2;
      --blue:#a9c9d3;
      --blue-soft:#dcecf0;
      --yellow:#f6d387;
      --yellow-soft:#f9e8b6;
      --ink:#473a2e;
      --muted:#806f5c;
      --white:#fffdf8;
      --shadow: 0 24px 70px rgba(88,65,39,.15);
      --radius:32px;
    }

    *{box-sizing:border-box}
    html{scroll-behavior:smooth}
    body{
      margin:0;
      color:var(--ink);
      background:
        radial-gradient(circle at 15% 15%, rgba(246,211,135,.30), transparent 24%),
        radial-gradient(circle at 88% 35%, rgba(169,201,211,.34), transparent 28%),
        linear-gradient(135deg,#f7f1e7 0%,#efe2ca 52%,#f8f3ea 100%);
      font-family:"DM Sans","Noto Sans Thai",sans-serif;
      overflow-x:hidden;
    }

    body:before{
      content:"";
      position:fixed;
      inset:0;
      pointer-events:none;
      opacity:.28;
      background-image:
        radial-gradient(rgba(98,74,52,.18) .6px, transparent .7px);
      background-size:7px 7px;
      mix-blend-mode:multiply;
      z-index:100;
    }

    a{color:inherit;text-decoration:none}
    button{font:inherit}

    .nav{
      position:fixed;
      z-index:90;
      top:18px;
      left:50%;
      transform:translateX(-50%);
      width:min(1160px, calc(100% - 32px));
      display:flex;
      align-items:center;
      justify-content:space-between;
      padding:12px 16px 12px 20px;
      background:rgba(255,253,248,.72);
      backdrop-filter:blur(18px);
      border:1px solid rgba(138,105,70,.18);
      border-radius:999px;
      box-shadow:0 12px 40px rgba(88,65,39,.08);
    }

    .brand{
      display:flex;
      align-items:center;
      gap:10px;
      font-weight:700;
      letter-spacing:.04em;
    }
    .brand-dot{
      width:34px;height:34px;border-radius:50%;
      background:linear-gradient(145deg,var(--yellow),var(--blue));
      box-shadow:inset 0 2px 5px rgba(255,255,255,.7);
    }
    .nav-links{display:flex;gap:5px;align-items:center}
    .nav-links a{
      padding:9px 13px;
      border-radius:999px;
      color:var(--muted);
      font-size:.88rem;
      transition:.25s ease;
    }
    .nav-links a:hover,.nav-links a.active{
      color:var(--ink);
      background:rgba(207,187,162,.35);
    }
    .nav-contact{
      padding:10px 15px;
      border-radius:999px;
      background:var(--brown);
      color:white;
      font-size:.84rem;
      font-weight:700;
      box-shadow:0 8px 22px rgba(98,74,52,.18);
    }

    .page{
      min-height:100svh;
      position:relative;
      padding:110px max(24px,5vw) 70px;
      scroll-margin-top:30px;
    }

    .hero{
      min-height:100svh;
      display:grid;
      grid-template-columns:minmax(360px,.9fr) minmax(480px,1.35fr);
      align-items:center;
      gap:2vw;
      padding-top:100px;
    }

    .hero-copy{position:relative;z-index:3;max-width:650px}
    .eyebrow{
      display:inline-flex;align-items:center;gap:9px;
      padding:8px 13px;
      border-radius:999px;
      background:rgba(169,201,211,.35);
      border:1px solid rgba(98,74,52,.10);
      color:var(--brown-dark);
      font-size:.78rem;
      font-weight:700;
      letter-spacing:.12em;
      text-transform:uppercase;
    }
    .eyebrow span{
      width:7px;height:7px;border-radius:50%;background:var(--yellow);
    }

    h1{
      margin:22px 0 15px;
      font-family:"Playfair Display",serif;
      font-size:clamp(4rem,8.5vw,8.8rem);
      line-height:.83;
      font-weight:600;
      letter-spacing:-.055em;
      color:var(--brown-dark);
    }
    h1 em{
      display:block;
      color:var(--brown);
      font-size:.52em;
      letter-spacing:-.02em;
      margin-left:.08em;
      margin-top:.2em;
    }

    .hero-desc{
      max-width:570px;
      font-size:clamp(1rem,1.5vw,1.2rem);
      line-height:1.8;
      color:var(--muted);
    }

    .roles{
      display:flex;flex-wrap:wrap;gap:9px;
      margin:25px 0 30px;
    }
    .role{
      padding:10px 14px;
      border:1px solid rgba(98,74,52,.16);
      border-radius:999px;
      background:rgba(255,253,248,.54);
      font-size:.86rem;
      font-weight:600;
    }
    .role:nth-child(2){background:rgba(169,201,211,.34)}
    .role:nth-child(3){background:rgba(246,211,135,.38)}

    .scroll-hint{
      display:flex;align-items:center;gap:12px;
      color:var(--muted);font-size:.78rem;letter-spacing:.12em;
      text-transform:uppercase;
    }
    .scroll-line{width:55px;height:1px;background:var(--brown)}

    .scene-wrap{
      height:min(720px,72svh);
      min-height:510px;
      position:relative;
      border-radius:48px;
      overflow:hidden;
      background:
        radial-gradient(circle at 60% 38%, rgba(255,253,248,.95), transparent 25%),
        radial-gradient(circle at 18% 78%, rgba(246,211,135,.34), transparent 25%),
        linear-gradient(145deg, #e6f1f2 0%, #f4eadb 45%, #cfbba2 100%);
      box-shadow:var(--shadow);
      border:1px solid rgba(255,255,255,.7);
    }
    #three-canvas{width:100%;height:100%;display:block}
    .scene-label{
      position:absolute;left:24px;bottom:22px;
      padding:10px 13px;border-radius:14px;
      background:rgba(255,253,248,.72);
      backdrop-filter:blur(12px);
      font-size:.74rem;color:var(--muted);
      border:1px solid rgba(98,74,52,.1);
    }
    .scene-tip{
      position:absolute;right:24px;top:22px;
      padding:10px 13px;border-radius:14px;
      background:rgba(255,253,248,.58);
      backdrop-filter:blur(12px);
      font-size:.72rem;color:var(--brown-dark);
    }

    .orb{
      position:absolute;border-radius:50%;filter:blur(.2px);pointer-events:none;
    }
    .orb.one{width:130px;height:130px;background:rgba(246,211,135,.35);left:-45px;top:22%}
    .orb.two{width:90px;height:90px;background:rgba(169,201,211,.35);right:6%;bottom:14%}

    .section-title{
      max-width:760px;margin-bottom:46px;
    }
    .section-kicker{
      color:var(--brown);font-weight:700;letter-spacing:.12em;text-transform:uppercase;font-size:.75rem;
    }
    h2{
      font-family:"Playfair Display",serif;
      font-size:clamp(2.8rem,6vw,5.6rem);
      line-height:.95;margin:12px 0 15px;
      color:var(--brown-dark);letter-spacing:-.045em;
    }
    .section-title p{color:var(--muted);line-height:1.8;max-width:680px}

    .about{
      display:grid;grid-template-columns:1fr 1.25fr;gap:7vw;align-items:center;
      background:rgba(255,253,248,.30);
    }

    .portrait-card{
      position:relative;min-height:590px;
      border-radius:44px;
      overflow:hidden;
      background:linear-gradient(145deg,var(--blue-soft),var(--cream));
      box-shadow:var(--shadow);
      border:1px solid rgba(255,255,255,.7);
    }
    .portrait-card:after{
      content:"";
      position:absolute;inset:10% 12% auto auto;
      width:210px;height:210px;border-radius:50%;
      background:rgba(246,211,135,.46);
      filter:blur(1px);
    }
    .portrait-art{
      position:absolute;inset:0;
      display:flex;align-items:flex-end;justify-content:center;
      padding:55px 30px 0;
    }
    .abstract-person{
      width:78%;height:82%;
      border-radius:52% 48% 15% 15% / 42% 44% 14% 14%;
      background:
        radial-gradient(circle at 42% 20%, #f6e3cc 0 10%, transparent 10.5%),
        linear-gradient(135deg,#a9c9d3 0 47%,#8a6946 47% 75%,#f6d387 75%);
      transform:rotate(-4deg);
      box-shadow:inset 16px 0 30px rgba(255,255,255,.18), 0 30px 45px rgba(98,74,52,.14);
    }
    .portrait-caption{
      position:absolute;z-index:2;left:25px;right:25px;bottom:24px;
      display:flex;justify-content:space-between;align-items:end;
      color:white;
    }
    .portrait-caption strong{font-family:"Playfair Display",serif;font-size:1.8rem}
    .portrait-caption small{opacity:.8}

    .bio-grid{
      display:grid;grid-template-columns:repeat(2,1fr);gap:16px;margin-top:28px;
    }
    .info-card{
      padding:23px;border-radius:25px;
      background:rgba(255,253,248,.62);
      border:1px solid rgba(98,74,52,.10);
      box-shadow:0 12px 35px rgba(88,65,39,.06);
    }
    .info-card.full{grid-column:1/-1}
    .info-card .label{
      color:var(--muted);font-size:.72rem;letter-spacing:.09em;text-transform:uppercase;
      margin-bottom:7px;
    }
    .info-card .value{font-weight:600;line-height:1.65}
    .contact-row{display:flex;flex-wrap:wrap;gap:10px;margin-top:25px}
    .contact-pill{
      padding:12px 15px;border-radius:15px;background:var(--white);
      border:1px solid rgba(98,74,52,.11);font-size:.88rem;
    }

    .work-section{background:rgba(169,201,211,.13)}
    .work-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:16px}
    .work-card{
      min-height:330px;border-radius:30px;padding:24px;position:relative;overflow:hidden;
      display:flex;flex-direction:column;justify-content:flex-end;
      background:rgba(255,253,248,.66);
      border:1px solid rgba(98,74,52,.10);
      transition:transform .35s ease, box-shadow .35s ease;
    }
    .work-card:hover{transform:translateY(-8px);box-shadow:var(--shadow)}
    .work-card:before{
      content:"";position:absolute;width:190px;height:190px;border-radius:50%;
      right:-60px;top:-55px;background:var(--yellow-soft);
    }
    .work-card:nth-child(2):before{background:var(--blue-soft)}
    .work-card:nth-child(3):before{background:#e9dccb}
    .work-card:nth-child(4):before{background:#f8df9d}
    .number{position:absolute;top:20px;left:22px;color:var(--brown);font-weight:700;font-size:.78rem}
    .work-icon{
      position:absolute;top:75px;left:25px;
      width:72px;height:72px;border-radius:22px;
      background:rgba(255,253,248,.72);
      display:grid;place-items:center;font-size:2rem;
      border:1px solid rgba(98,74,52,.09);
    }
    .work-card h3{
      margin:0 0 8px;font-family:"Playfair Display",serif;font-size:1.65rem;
      position:relative;z-index:1;
    }
    .work-card p{margin:0;color:var(--muted);font-size:.84rem;line-height:1.65;position:relative;z-index:1}
    .coming{margin-top:16px;font-size:.7rem;letter-spacing:.1em;text-transform:uppercase;color:var(--brown);font-weight:700}

    footer{
      padding:34px max(24px,5vw);
      display:flex;justify-content:space-between;gap:20px;flex-wrap:wrap;
      color:var(--muted);font-size:.8rem;
      border-top:1px solid rgba(98,74,52,.10);
    }

    .fade-up{opacity:0;transform:translateY(22px);transition:opacity .8s ease,transform .8s ease}
    .fade-up.visible{opacity:1;transform:none}

    @media (max-width:980px){
      .hero{grid-template-columns:1fr;gap:28px;padding-top:120px}
      .scene-wrap{height:62svh;min-height:450px}
      .about{grid-template-columns:1fr}
      .portrait-card{min-height:450px}
      .work-grid{grid-template-columns:repeat(2,1fr)}
      .nav-links a:nth-child(n+3){display:none}
    }
    @media (max-width:620px){
      .nav{top:10px;width:calc(100% - 18px)}
      .brand span{display:none}
      .nav-contact{display:none}
      .page{padding-left:18px;padding-right:18px}
      .hero{padding-top:95px}
      h1{font-size:4.3rem}
      .scene-wrap{height:60svh;min-height:390px;border-radius:30px}
      .bio-grid{grid-template-columns:1fr}
      .info-card.full{grid-column:auto}
      .work-grid{grid-template-columns:1fr}
      .work-card{min-height:260px}
    }

    /* ลด motion สำหรับผู้ใช้ที่ตั้งค่าระบบไว้ */
    @media (prefers-reduced-motion:reduce){
      html{scroll-behavior:auto}
      *,*:before,*:after{animation-duration:.01ms!important;animation-iteration-count:1!important;transition-duration:.01ms!important}
    }
  </style>
</head>

<body>
  <nav class="nav">
    <a class="brand" href="#home" aria-label="Cha Liris home">
      <span class="brand-dot"></span><span>CHA LIRIS</span>
    </a>
    <div class="nav-links">
      <a href="#home" class="active">Home</a>
      <a href="#about">About</a>
      <a href="#works">Works</a>
    </div>
    <a class="nav-contact" href="#about">Contact</a>
  </nav>

  <main>
    <!-- PAGE 01 -->
    <section id="home" class="page hero">
      <div class="hero-copy fade-up">
        <div class="eyebrow"><span></span> 3D PORTFOLIO · 2026</div>
        <h1>Cha<em>Liris</em></h1>
        <p class="hero-desc">
          Digital Artist &amp; 3D / Game Design student.
          ชอบสร้างโลกเล็ก ๆ ผ่านภาพ ตัวละคร แอนิเมชัน และงานเกม
          โดยผสมความอบอุ่นแบบ handmade เข้ากับงานดิจิทัลร่วมสมัย
        </p>

        <div class="roles" aria-label="Specialties">
          <div class="role">Digital Art</div>
          <div class="role">3D Modeling</div>
          <div class="role">Game Design</div>
        </div>

        <div class="scroll-hint"><span class="scroll-line"></span> Scroll to explore</div>
      </div>

      <div class="scene-wrap fade-up">
        <canvas id="three-canvas" aria-label="3D animated tea pouring into a cup"></canvas>
        <div class="scene-tip">drag · orbit · scroll</div>
        <div class="scene-label">3D STUDY · TEA TIME</div>
        <div class="orb one"></div>
        <div class="orb two"></div>
      </div>
    </section>

    <!-- PAGE 02 -->
    <section id="about" class="page about">
      <div class="portrait-card fade-up">
        <div class="portrait-art"><div class="abstract-person"></div></div>
        <div class="portrait-caption">
          <div><strong>Cha Liris</strong><br><small>Digital Art · Game · Animation</small></div>
          <div>02 / 06</div>
        </div>
      </div>

      <div class="fade-up">
        <div class="section-title">
          <div class="section-kicker">02 — About Me</div>
          <h2>Nice to meet<br>you.</h2>
          <p>
            นักศึกษามหาวิทยาลัยชั้นปีที่ 4 ที่สนใจการเล่าเรื่องด้วยภาพ
            การออกแบบตัวละคร การสร้าง 3D และการออกแบบเกม
            กำลังมองหาโอกาสฝึกงานในสาย <strong>2D Artist / 3D / Game &amp; Animation</strong>
          </p>
        </div>

        <div class="bio-grid">
          <div class="info-card">
            <div class="label">Name</div>
            <div class="value">นางสาวชาลินี รักทอง</div>
          </div>
          <div class="info-card">
            <div class="label">Pen Name</div>
            <div class="value">Cha Liris</div>
          </div>
          <div class="info-card full">
            <div class="label">Education</div>
            <div class="value">
              นักศึกษามหาวิทยาลัยชั้นปีที่ 4<br>
              มหาวิทยาลัยราชมงคลรัตนโกสินทร์ · คณะสถาปัตยกรรมศาสตร์และการออกแบบ<br>
              สาขาวิชาการออกแบบสื่อดิจิทัล · เอกการออกแบบเกมและแอนิเมชัน
            </div>
          </div>
        </div>

        <div class="contact-row">
          <a class="contact-pill" href="tel:0992591114">📞 099 259 1114</a>
          <a class="contact-pill" href="mailto:chalinee.fon1114@gmail.com">📬 chalinee.fon1114@gmail.com</a>
        </div>
      </div>
    </section>

    <!-- FUTURE WORKS -->
    <section id="works" class="page work-section">
      <div class="section-title fade-up">
        <div class="section-kicker">03 — Selected Areas</div>
        <h2>Works to come.</h2>
        <p>พื้นที่สำหรับเพิ่มผลงานในหน้าถัดไปภายหลัง — โครงสร้างเตรียมไว้ให้แล้ว</p>
      </div>

      <div class="work-grid">
        <article class="work-card fade-up">
          <span class="number">01</span><div class="work-icon">✦</div>
          <h3>Digital Art</h3>
          <p>Illustration, visual development และงานภาพดิจิทัล</p>
          <span class="coming">Add projects later →</span>
        </article>
        <article class="work-card fade-up">
          <span class="number">02</span><div class="work-icon">◌</div>
          <h3>Character Design</h3>
          <p>Character concept, expression, costume และ visual identity</p>
          <span class="coming">Add projects later →</span>
        </article>
        <article class="work-card fade-up">
          <span class="number">03</span><div class="work-icon">◇</div>
          <h3>3D Modeling / Animation</h3>
          <p>Modeling, materials, lighting และ animation studies</p>
          <span class="coming">Add projects later →</span>
        </article>
        <article class="work-card fade-up">
          <span class="number">04</span><div class="work-icon">⌁</div>
          <h3>Game Design</h3>
          <p>Game concept, mechanics, visual direction และ prototype</p>
          <span class="coming">Add projects later →</span>
        </article>
      </div>
    </section>
  </main>

  <footer>
    <span>© 2026 Cha Liris</span>
    <span>Digital Art · 3D Modeling · Game Design</span>
  </footer>

  <script type="module">
    import * as THREE from 'three';
    import { OrbitControls } from 'three/addons/controls/OrbitControls.js';

    const canvas = document.querySelector('#three-canvas');
    const container = canvas.parentElement;

    const scene = new THREE.Scene();
    scene.background = new THREE.Color(0xe9ded0);

    const camera = new THREE.PerspectiveCamera(34, 1, 0.1, 100);
    camera.position.set(6.8, 5.1, 8.4);

    const renderer = new THREE.WebGLRenderer({
      canvas,
      antialias: true,
      alpha: true,
      powerPreference: 'high-performance'
    });
    renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
    renderer.shadowMap.enabled = true;
    renderer.shadowMap.type = THREE.PCFSoftShadowMap;
    renderer.outputColorSpace = THREE.SRGBColorSpace;
    renderer.toneMapping = THREE.ACESFilmicToneMapping;
    renderer.toneMappingExposure = 1.15;

    const controls = new OrbitControls(camera, canvas);
    controls.enableDamping = true;
    controls.dampingFactor = 0.06;
    controls.enablePan = false;
    controls.minDistance = 6;
    controls.maxDistance = 13;
    controls.minPolarAngle = Math.PI * .28;
    controls.maxPolarAngle = Math.PI * .62;
    controls.target.set(0, 1.15, 0);

    // ---------- Materials ----------
    const porcelain = new THREE.MeshPhysicalMaterial({
      color: 0xfffbf3,
      roughness: .28,
      metalness: 0,
      clearcoat: .55,
      clearcoatRoughness: .22
    });

    const gold = new THREE.MeshStandardMaterial({
      color: 0xc79c5c,
      roughness: .24,
      metalness: .78
    });

    const teaMat = new THREE.MeshPhysicalMaterial({
      color: 0x8a6946,
      roughness: .22,
      metalness: .02,
      transmission: .08,
      clearcoat: .4
    });

    const teaFoamMat = new THREE.MeshStandardMaterial({
      color: 0xc9a27a,
      roughness: .45
    });

    const tableMat = new THREE.MeshStandardMaterial({
      color: 0xcdbda8,
      roughness: .82
    });

    const clothMat = new THREE.MeshStandardMaterial({
      color: 0xece3d4,
      roughness: .96
    });

    // ---------- Lighting ----------
    scene.add(new THREE.HemisphereLight(0xfff8ea, 0x8a6946, 2.1));

    const key = new THREE.DirectionalLight(0xfff5df, 4.1);
    key.position.set(4, 9, 5);
    key.castShadow = true;
    key.shadow.mapSize.set(1536,1536);
    key.shadow.camera.left = -6;
    key.shadow.camera.right = 6;
    key.shadow.camera.top = 6;
    key.shadow.camera.bottom = -6;
    scene.add(key);

    const fill = new THREE.PointLight(0xb7d8df, 5, 18);
    fill.position.set(-5, 4, 2);
    scene.add(fill);

    const warm = new THREE.PointLight(0xf6d387, 3.8, 12);
    warm.position.set(3, 1, -4);
    scene.add(warm);

    // ---------- Helpers ----------
    function makeLathe(points, material, segments=64) {
      const geo = new THREE.LatheGeometry(points.map(p => new THREE.Vector2(p[0],p[1])), segments);
      const mesh = new THREE.Mesh(geo, material);
      mesh.castShadow = true;
      mesh.receiveShadow = true;
      return mesh;
    }

    // ---------- Table / cloth ----------
    const table = new THREE.Mesh(new THREE.CylinderGeometry(6.5,6.5,.32,96), tableMat);
    table.position.y = -1.1;
    table.receiveShadow = true;
    scene.add(table);

    const cloth = new THREE.Mesh(
      new THREE.CylinderGeometry(5.55,5.55,.05,96),
      clothMat
    );
    cloth.position.y = -.92;
    cloth.scale.set(1.04,.35,1.04);
    cloth.rotation.z = -.07;
    cloth.receiveShadow = true;
    scene.add(cloth);

    // subtle cloth stripes
    for(let i=-5;i<=5;i++){
      const stripe = new THREE.Mesh(
        new THREE.BoxGeometry(.12,.025,10.4),
        new THREE.MeshStandardMaterial({color:0xd7c5ac,roughness:1})
      );
      stripe.position.set(i*.72,-.88,0);
      stripe.rotation.y = -.38;
      stripe.rotation.z = -.015;
      scene.add(stripe);
    }

    // ---------- Saucer ----------
    const saucer = makeLathe([
      [0,-.03],[1.45,-.02],[1.72,.03],[2.0,.13],[2.12,.24],[2.0,.30],[1.45,.26],[.25,.12],[0,.08]
    ], porcelain, 96);
    saucer.scale.y = .58;
    saucer.position.y = -.72;
    scene.add(saucer);

    // gold rim
    const rim = new THREE.Mesh(
      new THREE.TorusGeometry(2.02,.035,12,96),
      gold
    );
    rim.scale.y=.58;
    rim.position.y=-.54;
    scene.add(rim);

    // ---------- Cup ----------
    const cup = new THREE.Group();
    cup.position.y = -.38;
    scene.add(cup);

    const cupBody = makeLathe([
      [0,-.02],[.52,-.02],[.92,.05],[1.16,.34],[1.22,.95],[1.18,1.36],[1.05,1.55],[.85,1.63],[.32,1.66],[0,1.66]
    ], porcelain, 96);
    cupBody.scale.y = 1;
    cup.add(cupBody);

    const innerTea = new THREE.Mesh(
      new THREE.CylinderGeometry(1.05,1.05,.055,96),
      teaMat
    );
    innerTea.position.y = 1.46;
    cup.add(innerTea);

    const innerRim = new THREE.Mesh(
      new THREE.TorusGeometry(1.12,.038,12,96),
      gold
    );
    innerRim.position.y = 1.58;
    cup.add(innerRim);

    // Decorative gold band
    const band = new THREE.Mesh(
      new THREE.TorusGeometry(1.18,.025,10,96),
      gold
    );
    band.position.y=.30;
    cup.add(band);

    // Cup handle
    const handle = new THREE.Mesh(
      new THREE.TorusGeometry(.55,.115,18,64,Math.PI*1.55),
      porcelain
    );
    handle.rotation.z = Math.PI/2;
    handle.rotation.y = Math.PI/2;
    handle.position.set(1.32,.95,0);
    handle.castShadow=true;
    cup.add(handle);

    const handleGold = new THREE.Mesh(
      new THREE.TorusGeometry(.55,.018,10,64,Math.PI*1.55),
      gold
    );
    handleGold.rotation.z = Math.PI/2;
    handleGold.rotation.y = Math.PI/2;
    handleGold.position.set(1.325,.95,0);
    cup.add(handleGold);

    // tiny embossed flower-like dots around cup
    for(let i=0;i<12;i++){
      const a = i/12*Math.PI*2;
      const d = 1.205;
      const dot = new THREE.Mesh(new THREE.SphereGeometry(.035,12,8), gold);
      dot.position.set(Math.cos(a)*d,.83,Math.sin(a)*d);
      cup.add(dot);
    }

    // ---------- Teapot / milk pot ----------
    const pot = new THREE.Group();
    pot.position.set(-2.55,2.15,-.45);
    pot.rotation.z = -.14;
    scene.add(pot);

    const potBody = makeLathe([
      [0,-.7],[.55,-.66],[.98,-.46],[1.12,-.02],[1.03,.42],[.72,.68],[.30,.76],[0,.78]
    ], porcelain, 80);
    potBody.scale.set(1.05,.9,1);
    pot.add(potBody);

    // pot neck / lip
    const potLip = new THREE.Mesh(new THREE.TorusGeometry(.40,.075,16,48), gold);
    potLip.position.y=.72;
    pot.add(potLip);

    // handle behind pot
    const potHandle = new THREE.Mesh(
      new THREE.TorusGeometry(.63,.09,16,64,Math.PI*1.45),
      porcelain
    );
    potHandle.rotation.z=Math.PI/2;
    potHandle.position.set(-.73,.15,0);
    pot.add(potHandle);

    // spout
    const spout = new THREE.Mesh(
      new THREE.ConeGeometry(.26,1.15,32),
      porcelain
    );
    spout.rotation.z=-Math.PI*.58;
    spout.position.set(.92,.20,.02);
    spout.scale.set(.72,1,.72);
    pot.add(spout);

    // gold pot decoration
    const potBand = new THREE.Mesh(new THREE.TorusGeometry(.94,.028,10,64),gold);
    potBand.position.y=.23;
    pot.add(potBand);

    // ---------- Pouring stream ----------
    const streamGroup = new THREE.Group();
    scene.add(streamGroup);

    const streamMat = new THREE.MeshPhysicalMaterial({
      color:0x9a704d,
      roughness:.15,
      metalness:0,
      transmission:.18,
      transparent:true,
      opacity:.96
    });

    const stream = new THREE.Mesh(
      new THREE.CylinderGeometry(.075,.095,3.25,32),
      streamMat
    );
    stream.position.set(-1.64,2.02,.02);
    stream.rotation.z=.05;
    stream.castShadow=true;
    streamGroup.add(stream);

    // splash / ripples
    const ripples = [];
    for(let i=0;i<4;i++){
      const ring = new THREE.Mesh(
        new THREE.TorusGeometry(.10+i*.13,.018,10,64),
        teaFoamMat
      );
      ring.rotation.x=Math.PI/2;
      ring.position.set(0,.0,.0);
      ring.scale.set(.7,.7,.7);
      ring.visible=false;
      cup.add(ring);
      ripples.push(ring);
    }

    // foam bubbles
    const bubbles=[];
    for(let i=0;i<42;i++){
      const r=.012+Math.random()*.045;
      const bubble=new THREE.Mesh(new THREE.SphereGeometry(r,10,8),teaFoamMat);
      const a=Math.random()*Math.PI*2;
      const rad=Math.sqrt(Math.random())*.92;
      bubble.position.set(Math.cos(a)*rad,1.49+Math.random()*.025,Math.sin(a)*rad);
      bubble.scale.y=.42;
      bubble.visible=false;
      cup.add(bubble);
      bubbles.push({mesh:bubble,delay:Math.random()*2.5});
    }

    // ---------- A few floating decorative particles ----------
    const particleMat = new THREE.MeshBasicMaterial({
      color:0xf6d387,
      transparent:true,
      opacity:.72
    });
    const particles=[];
    for(let i=0;i<22;i++){
      const p=new THREE.Mesh(new THREE.SphereGeometry(.025+Math.random()*.035,8,8),particleMat);
      p.position.set((Math.random()-.5)*5.2,Math.random()*3.8-.2,(Math.random()-.5)*2.8);
      scene.add(p);
      particles.push({mesh:p,phase:Math.random()*Math.PI*2});
    }

    // ---------- Resize ----------
    function resize(){
      const w=container.clientWidth;
      const h=container.clientHeight;
      camera.aspect=w/h;
      camera.updateProjectionMatrix();
      renderer.setSize(w,h,false);
    }
    window.addEventListener('resize',resize);
    resize();

    // ---------- Animation ----------
    const clock=new THREE.Clock();

    function animate(){
      requestAnimationFrame(animate);
      const t=clock.getElapsedTime();

      // gentle camera/scene life
      pot.rotation.z=-.14 + Math.sin(t*.8)*.008;
      pot.position.y=2.15 + Math.sin(t*1.1)*.018;

      // tea stream pulses very subtly
      const streamPulse=1 + Math.sin(t*7)*.045;
      stream.scale.x=streamPulse;
      stream.scale.z=streamPulse;

      // ripple cycles
      ripples.forEach((ring,i)=>{
        const cycle=(t*.75+i*.35)%2.6;
        if(cycle<1.8){
          ring.visible=true;
          const s=.25+cycle*1.15;
          ring.scale.set(s,s,s);
          ring.material.opacity=Math.max(0, .55-cycle*.30);
        }else{
          ring.visible=false;
        }
      });

      // bubbles rise / appear in waves
      bubbles.forEach((b,i)=>{
        const cycle=(t*0.55+b.delay)%3.0;
        const visible=cycle>1.15;
        b.mesh.visible=visible;
        if(visible){
          b.mesh.position.y=1.49+(cycle-1.15)*.025;
          const s=1+(Math.sin(t*4+i)*.12);
          b.mesh.scale.set(s,s*.42,s);
        }
      });

      particles.forEach((p)=>{
        p.mesh.position.y += Math.sin(t*.35+p.phase)*.0015;
        p.mesh.position.x += Math.cos(t*.25+p.phase)*.0008;
      });

      controls.update();
      renderer.render(scene,camera);
    }
    animate();

    // ---------- Active nav + reveal ----------
    const sections=[...document.querySelectorAll('main section')];
    const navLinks=[...document.querySelectorAll('.nav-links a')];
    const observer=new IntersectionObserver((entries)=>{
      entries.forEach(entry=>{
        if(entry.isIntersecting){
          const id=entry.target.id;
          navLinks.forEach(a=>a.classList.toggle('active',a.getAttribute('href')==='#'+id));
        }
      });
    },{threshold:.45});
    sections.forEach(s=>observer.observe(s));

    const reveal=new IntersectionObserver((entries)=>{
      entries.forEach(e=>{
        if(e.isIntersecting)e.target.classList.add('visible');
      });
    },{threshold:.12});
    document.querySelectorAll('.fade-up').forEach(el=>reveal.observe(el));

    // เริ่มหน้าแรกให้แสดงทันที
    document.querySelectorAll('#home .fade-up').forEach(el=>el.classList.add('visible'));
  </script>
</body>
</html>
