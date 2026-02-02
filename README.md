# rpg
<!doctype html>
<html lang="vi">

<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>RPG_V11</title>
  <style>
    :root {
      --bg: #0f0f12;
      --panel: rgba(255, 255, 255, .07);
      --panel2: rgba(255, 255, 255, .10);
      --stroke: rgba(255, 255, 255, .14);
      --text: rgba(255, 255, 255, .92);
      --muted: rgba(255, 255, 255, .68);
      --shadow: 0 18px 54px rgba(0, 0, 0, .45);
      --radius: 18px;
      --good: rgba(120, 220, 160, .95);
      --bad: rgba(255, 92, 122, .95);
      --warn: rgba(255, 200, 80, .95);
      --accent: rgba(175, 180, 185, .95);
    }

    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Arial;
      color: var(--text);
      background:
        radial-gradient(1200px 900px at 20% 10%, rgba(124, 92, 255, .22), transparent 55%),
        radial-gradient(900px 700px at 80% 30%, rgba(43, 213, 118, .15), transparent 60%),
        radial-gradient(800px 600px at 50% 90%, rgba(255, 92, 122, .10), transparent 55%),
        var(--bg);
      min-height: 100vh;
    }

    .wrap {
      max-width: 1240px;
      margin: 0 auto;
      padding: 14px 12px 30px;
    }

    header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      margin-bottom: 12px;
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 12px;
      user-select: none;
      min-width: 0;
    }

    .logo {
      width: 38px;
      height: 38px;
      border-radius: 14px;
      background: linear-gradient(135deg, rgba(124, 92, 255, .9), rgba(43, 213, 118, .85));
      box-shadow: var(--shadow);
      flex: 0 0 auto;
    }

    .brandText {
      min-width: 0;
    }

    .brand h1 {
      font-size: 15px;
      margin: 0;
      letter-spacing: .2px;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
    }

    .brand p {
      margin: 0;
      font-size: 12px;
      color: var(--muted);
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
    }

    .grid {
      display: grid;
      grid-template-columns: 1.55fr .95fr;
      gap: 12px;
    }

    @media (max-width: 980px) {
      .grid {
        grid-template-columns: 1fr;
      }
    }

    .center-text {
      text-align: center;
      font-size: 16px;
      line-height: 1.6;
    }

    .card {
      background: var(--panel);
      border: 1px solid var(--stroke);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      backdrop-filter: blur(14px);
      overflow: hidden;
    }

    .cardHead {
      padding: 12px 12px 0;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
    }

    .sectionTitle {
      margin: 0;
      font-size: 12px;
      color: var(--muted);
      letter-spacing: .6px;
      text-transform: uppercase;
    }

    .pillRow {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      padding: 10px 12px 0;
    }

    .pill {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 8px 10px;
      border-radius: 999px;
      background: var(--panel2);
      border: 1px solid var(--stroke);
      font-size: 12px;
      color: var(--muted);
      white-space: nowrap;
    }

    .pill b {
      color: var(--text);
      font-weight: 600;
    }

    .pane {
      padding: 12px;
    }

    .story {
      white-space: pre-wrap;
      line-height: 1.6;
      color: var(--muted);
      font-size: 13px;
      min-height: 240px;
      max-height: 440px;
      overflow: auto;
      padding-right: 6px;
    }

    .help {
      color: rgba(255, 255, 255, .55);
      font-size: 12px;
      margin-top: 10px;
      line-height: 1.55;
    }

    /* Choices UI */
    .choicesWrap {
      margin-top: 10px;
      padding: 10px;
      border-radius: 16px;
      border: 1px solid rgba(255, 255, 255, .12);
      background: rgba(255, 255, 255, .05);
    }

    .choicesTop {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 10px;
      margin-bottom: 8px;
    }

    .choicesTop .t {
      font-size: 12px;
      color: rgba(255, 255, 255, .62);
      letter-spacing: .4px;
      text-transform: uppercase;
    }

    .choicesRow {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
    }

    .choiceBtn {
      padding: 10px 12px;
      border-radius: 14px;
      border: 1px solid rgba(255, 255, 255, .14);
      background: rgba(0, 0, 0, .18);
      color: rgba(255, 255, 255, .86);
      cursor: pointer;
      transition: transform .08s ease, filter .12s ease, background .12s ease;
      font-weight: 750;
      font-size: 12px;
    }

    .choiceBtn:hover {
      background: rgba(255, 255, 255, .10);
      transform: translateY(-1px);
    }

    .choiceBtn:active {
      transform: translateY(0px) scale(.99);
    }

    .choiceBtn.good {
      border-color: rgba(43, 213, 118, .22);
      background: rgba(43, 213, 118, .10);
    }

    .choiceBtn.bad {
      border-color: rgba(255, 92, 122, .25);
      background: rgba(255, 92, 122, .10);
    }

    .choiceBtn.warn {
      border-color: rgba(255, 200, 80, .25);
      background: rgba(255, 200, 80, .10);
    }

    .inputRow {
      display: flex;
      gap: 10px;
      padding: 10px 12px 12px;
      border-top: 1px solid rgba(255, 255, 255, .10);
      align-items: center;
    }

    input {
      flex: 1;
      padding: 12px 12px;
      border-radius: 14px;
      border: 1px solid rgba(255, 255, 255, .16);
      background: rgba(0, 0, 0, .22);
      color: var(--text);
      outline: none;
    }

    .btn {
      padding: 11px 12px;
      border-radius: 14px;
      border: 1px solid rgba(255, 255, 255, .16);
      background: rgba(255, 255, 255, .07);
      color: var(--text);
      cursor: pointer;
      transition: transform .08s ease, filter .12s ease, background .12s ease;
      font-weight: 650;
      white-space: nowrap;
    }

    .btn:hover {
      background: rgba(255, 255, 255, .10);
      transform: translateY(-1px);
    }

    .btn:active {
      transform: translateY(0px) scale(.99);
    }

    .btnPrimary {
      background: linear-gradient(135deg, rgba(124, 92, 255, .92), rgba(43, 213, 118, .70));
      border-color: rgba(255, 255, 255, .18);
    }

    .btnPrimary:hover {
      filter: brightness(1.05);
    }

    .btnDanger {
      background: rgba(255, 92, 122, .18);
      border-color: rgba(255, 92, 122, .35);
    }

    .btnDanger:hover {
      background: rgba(255, 92, 122, .24);
    }

    .btn[disabled] {
      opacity: .45;
      cursor: not-allowed;
      transform: none;
    }

    /* Battle */
    .battleUI {
      display: none;
      border-top: 1px solid rgba(255, 255, 255, .10);
    }

    .battleBar {
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
      padding: 12px 12px 0;
    }

    .meter {
      flex: 1 1 260px;
      border: 1px solid rgba(255, 255, 255, .12);
      border-radius: 16px;
      padding: 10px 10px;
      background: rgba(255, 255, 255, .05);
    }

    .meter .top {
      display: flex;
      justify-content: space-between;
      gap: 10px;
      color: rgba(255, 255, 255, .70);
      font-size: 12px;
    }

    .barWrap {
      margin-top: 8px;
      height: 10px;
      border-radius: 999px;
      background: rgba(255, 255, 255, .06);
      border: 1px solid rgba(255, 255, 255, .08);
      overflow: hidden;
    }

    .barFill {
      height: 100%;
      width: 50%;
      background: var(--accent);
    }

    .barFill.bad {
      background: var(--bad);
    }

    .barFill.good {
      background: var(--good);
    }

    .skills {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 10px;
      padding: 12px 12px 12px;
    }

    @media (max-width: 520px) {
      .skills {
        grid-template-columns: 1fr;
      }
    }

    /* Sidebar */
    .sidePad {
      padding: 12px 12px 12px;
    }

    .twoCols {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 10px;
      margin-top: 10px;
    }

    .box {
      border: 1px solid rgba(255, 255, 255, .12);
      background: rgba(255, 255, 255, .05);
      border-radius: 16px;
      padding: 10px;
    }

    .k {
      font-size: 12px;
      color: var(--muted);
    }

    .v {
      margin-top: 6px;
      font-size: 16px;
      font-weight: 820;
    }

    .mini {
      font-size: 12px;
      color: rgba(255, 255, 255, .60);
      line-height: 1.45;
      margin-top: 6px;
    }

    .log {
      margin-top: 10px;
      max-height: 320px;
      overflow: auto;
      display: grid;
      gap: 10px;
      padding-right: 6px;
    }

    .logItem {
      padding: 10px;
      border-radius: 14px;
      border: 1px solid rgba(255, 255, 255, .12);
      background: rgba(0, 0, 0, .14);
      color: var(--muted);
      font-size: 12px;
      line-height: 1.55;
    }

    .logItem b {
      color: var(--text);
    }

    .logItem .t {
      color: rgba(255, 255, 255, .40);
      font-size: 11px;
      margin-top: 6px;
    }

    /* Overlays / Modals */
    .overlay {
      position: fixed;
      inset: 0;
      display: none;
      align-items: center;
      justify-content: center;
      background: rgba(0, 0, 0, .60);
      backdrop-filter: blur(10px);
      padding: 12px;
      z-index: 9999;
    }

    .modal {
      width: min(920px, 100%);
      border-radius: 22px;
      border: 1px solid rgba(255, 255, 255, .14);
      background: rgba(15, 22, 40, .92);
      box-shadow: 0 40px 120px rgba(0, 0, 0, .65);
      overflow: hidden;
      max-height: 92vh;
      display: flex;
      flex-direction: column;
    }

    .modalTop {
      padding: 12px 12px 10px;
      border-bottom: 1px solid rgba(255, 255, 255, .10);
      display: flex;
      align-items: flex-start;
      justify-content: space-between;
      gap: 12px;
    }

    .modalTop h2 {
      margin: 0;
      font-size: 16px;
    }

    .modalTop p {
      margin: 6px 0 0;
      color: var(--muted);
      font-size: 12px;
      line-height: 1.55;
    }

    .modalBody {
      padding: 12px 12px 12px;
      display: grid;
      grid-template-columns: 1.1fr .9fr;
      gap: 10px;
      overflow: auto;
    }

    @media (max-width: 900px) {
      .modalBody {
        grid-template-columns: 1fr;
      }

      .brand p {
        display: none;
      }
    }

    .field {
      border: 1px solid rgba(255, 255, 255, .12);
      background: rgba(255, 255, 255, .05);
      border-radius: 16px;
      padding: 10px;
    }

    .field label {
      display: block;
      font-size: 12px;
      color: var(--muted);
    }

    .field input,
    .field select {
      margin-top: 8px;
      width: 100%;
      padding: 10px 12px;
      border-radius: 12px;
      border: 1px solid rgba(255, 255, 255, .14);
      background: rgba(0, 0, 0, .22);
      color: var(--text);
      outline: none;
    }

    .tagList {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-top: 10px;
    }

    .tag {
      padding: 7px 10px;
      border-radius: 999px;
      border: 1px solid rgba(255, 255, 255, .14);
      background: rgba(255, 255, 255, .06);
      color: rgba(255, 255, 255, .75);
      font-size: 12px;
    }

    .row {
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
      justify-content: space-between;
      align-items: center;
      margin-top: 10px;
    }

    .list {
      display: grid;
      gap: 10px;
      margin-top: 10px;
    }

    .listItem {
      border: 1px solid rgba(255, 255, 255, .12);
      background: rgba(255, 255, 255, .05);
      border-radius: 16px;
      padding: 10px;
      display: flex;
      gap: 10px;
      align-items: flex-start;
      justify-content: space-between;
    }

    .listItem .left {
      min-width: 0;
    }

    .listItem .name {
      font-weight: 800;
      font-size: 13px;
    }

    .listItem .desc {
      margin-top: 4px;
      color: rgba(255, 255, 255, .60);
      font-size: 12px;
      line-height: 1.45;
    }

    .rar {
      display: inline-flex;
      padding: 2px 8px;
      border-radius: 999px;
      border: 1px solid rgba(255, 255, 255, .14);
      background: rgba(0, 0, 0, .18);
      color: rgba(255, 255, 255, .72);
      font-size: 11px;
      margin-left: 6px;
      vertical-align: middle;
    }

    .rar.legendary {
      border-color: rgba(255, 215, 0, .35);
      background: rgba(255, 215, 0, .12);
    }

    .rar.legend {
      border-color: rgba(255, 92, 122, .30);
      background: rgba(255, 92, 122, .10);
    }

    .rar.rare {
      border-color: rgba(124, 92, 255, .30);
      background: rgba(124, 92, 255, .10);
    }

    .rar.common {
      border-color: rgba(255, 255, 255, .16);
      background: rgba(255, 255, 255, .06);
    }

    .rar.trash {
      border-color: rgba(180, 180, 180, .18);
      background: rgba(180, 180, 180, .06);
    }

    /* Gacha Animation */
    .gachaBox {
      padding: 20px 14px 14px;
      text-align: center;
    }

    .spinner {
      width: 88px;
      height: 88px;
      border-radius: 26px;
      margin: 0 auto 14px;
      border: 1px solid rgba(255, 255, 255, .14);
      background: rgba(255, 255, 255, .06);
      position: relative;
      overflow: hidden;
      box-shadow: 0 20px 70px rgba(0, 0, 0, .35);
    }

    .spinner::before {
      content: "";
      position: absolute;
      inset: -40%;
      background: conic-gradient(from 0deg, rgba(124, 92, 255, .0), rgba(124, 92, 255, .85), rgba(43, 213, 118, .85), rgba(255, 92, 122, .85), rgba(124, 92, 255, .0));
      animation: spin 1s linear infinite;
    }

    .spinner::after {
      content: "";
      position: absolute;
      inset: 10px;
      border-radius: 18px;
      background: rgba(15, 22, 40, .92);
      border: 1px solid rgba(255, 255, 255, .12);
    }

    @keyframes spin {
      to {
        transform: rotate(360deg);
      }
    }

    .reveal {
      margin-top: 10px;
      border: 1px solid rgba(255, 255, 255, .12);
      background: rgba(255, 255, 255, .05);
      border-radius: 16px;
      padding: 12px;
      text-align: left;
    }

    .reveal .big {
      font-weight: 900;
      font-size: 15px;
      letter-spacing: .2px;
    }

    .reveal .small {
      margin-top: 6px;
      color: rgba(255, 255, 255, .62);
      font-size: 12px;
      line-height: 1.5;
    }

    /* ===== v7 additions ===== */
    .inputRow {
      display: none !important;
    }

    /* commands replaced by buttons */
    .menuBtn {
      position: fixed;
      right: 14px;
      bottom: 14px;
      z-index: 9998;
      border-radius: 16px;
      padding: 12px 14px;
      border: 1px solid rgba(255, 255, 255, .16);
      background: rgba(255, 255, 255, .10);
      color: rgba(255, 255, 255, .92);
      font-weight: 900;
      box-shadow: var(--shadow);
      backdrop-filter: blur(14px);
      cursor: pointer;
    }

    .menuBtn:active {
      transform: scale(.99);
    }

    .menuGrid {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 10px;
      margin-top: 10px;
    }

    @media (max-width: 560px) {
      .menuGrid {
        grid-template-columns: 1fr 1fr;
      }
    }

    .menuCard {
      border: 1px solid rgba(255, 255, 255, .12);
      background: rgba(255, 255, 255, .06);
      border-radius: 18px;
      padding: 12px;
      cursor: pointer;
      transition: transform .08s ease, background .12s ease;
      min-height: 58px;
    }

    .menuCard:hover {
      background: rgba(255, 255, 255, .10);
      transform: translateY(-1px);
    }

    .menuCard .t {
      font-weight: 950;
    }

    .menuCard .d {
      margin-top: 6px;
      color: rgba(255, 255, 255, .62);
      font-size: 12px;
      line-height: 1.4;
    }

    .battleAnimLayer {
      position: relative;
      overflow: hidden;
      border-radius: 18px;
    }

    .fxSlash {
      position: absolute;
      left: -40%;
      top: -30%;
      width: 180%;
      height: 160%;
      background: linear-gradient(90deg, rgba(255, 255, 255, 0), rgba(255, 255, 255, .18), rgba(255, 255, 255, 0));
      transform: rotate(-18deg);
      opacity: 0;
      pointer-events: none;
      z-index: 5;
    }

    .fxSlash.play {
      animation: slash 420ms ease-out 1;
    }

    @keyframes slash {
      0% {
        transform: translateX(-20%) rotate(-18deg);
        opacity: 0;
      }

      25% {
        opacity: 1;
      }

      100% {
        transform: translateX(20%) rotate(-18deg);
        opacity: 0;
      }
    }

    .shake {
      animation: shake .22s ease-in-out 1;
    }

    @keyframes shake {
      0% {
        transform: translateX(0);
      }

      25% {
        transform: translateX(-3px);
      }

      50% {
        transform: translateX(3px);
      }

      75% {
        transform: translateX(-2px);
      }

      100% {
        transform: translateX(0);
      }
    }


    /* Cinematic battle scene */
    .cinematic {
      position: fixed;
      inset: 0;
      display: none;
      align-items: center;
      justify-content: center;
      background: radial-gradient(circle at 50% 40%, rgba(255, 255, 255, 0.08), rgba(0, 0, 0, 0.78));
      z-index: 80;
    }

    .cinBox {
      width: min(520px, 92vw);
      border-radius: 18px;
      padding: 18px 16px;
      background: rgba(20, 20, 24, 0.78);
      border: 1px solid rgba(255, 255, 255, 0.16);
      box-shadow: 0 18px 60px rgba(0, 0, 0, 0.55);
      text-align: center;
      animation: cinPop 0.9s ease both;
    }

    .cinTitle {
      font-size: 20px;
      letter-spacing: 0.12em;
      font-weight: 800;
      text-transform: uppercase;
    }

    .cinSub {
      margin-top: 8px;
      font-size: 13px;
      opacity: 0.9;
    }

    @keyframes cinPop {
      0% {
        transform: translateY(12px) scale(0.98);
        opacity: 0
      }

      40% {
        opacity: 1
      }

      100% {
        transform: translateY(0) scale(1);
      }
    }

    #overlayCheat h2 {
      text-align: center;
    }
  </style>
</head>

<body>
  <div class="wrap">
    <header>
      <div class="brand">
        <div class="logo"></div>
        <div class="brandText">
          <h1>RPG_V11</h1>
          <p>Choices UI • NPC random events tốt/xấu • Talk có thể bị lừa (-50% vàng) • Money có thể bị quỵt lương</p>
        </div>
      </div>
      <div style="display:flex; gap:10px; align-items:center;">
        <button class="btn btnDanger" id="btnReset" style="display:none;">Chơi lại</button>
      </div>
    </header>

    <div class="grid">
      <section class="card">
        <div class="cardHead">
          <p class="sectionTitle">Cốt truyện & Lệnh</p>
          <span class="sectionTitle" id="statusLine">chưa bắt đầu</span>
        </div>
        <div class="pillRow" id="hud"></div>

        <div class="pane">
          <div class="story" id="story"></div>

          <div class="choicesWrap" id="choicesWrap">
            <div class="choicesTop">
              <div class="t" id="choicesTitle">gợi ý hành động</div>
              <div class="t" id="choicesHint">bấm để chạy lệnh</div>
            </div>
            <div class="choicesRow" id="choicesRow"></div>
          </div>

          <div class="help" id="help"></div>
        </div>

        <div class="battleUI" id="battleUI">
          <div class="fxSlash" id="fxSlash"></div>
          <div class="battleBar" id="battleBar"></div>
          <div class="skills" id="skills"></div>
        </div>

        <div class="inputRow">
          <input id="cmd"
            placeholder="Nhập lệnh… help | battle | talk | shop | money | gacha | forge | dungeon | trial | next" />
          <button class="btn btnPrimary" id="send">Gửi</button>
        </div>
      </section>

      <aside class="card sidePad">
        <p class="sectionTitle">Trạng thái</p>
        <div class="twoCols">
          <div class="box">
            <div class="k">Level</div>
            <div class="v" id="lv">-</div>
            <div class="mini" id="xp">EXP: -</div>
          </div>
          <div class="box">
            <div class="k">Tuổi</div>
            <div class="v" id="age">-</div>
            <div class="mini">+1 tuổi mỗi <b>turn</b> (10 hành động). 100 tuổi → chết già.</div>
          </div>
          <div class="box">
            <div class="k">Vàng</div>
            <div class="v" id="gold">-</div>
            <div class="mini">Talk có thể bị lừa (-50% vàng).</div>
          </div>
          <div class="box">
            <div class="k">Chủng tộc</div>
            <div class="v" id="race">-</div>
            <div class="mini" id="raceBonus">-</div>
          </div>
          <div class="box">
            <div class="k">Chức nghiệp</div>
            <div class="v" id="job">-</div>
            <div class="mini" id="jobBonus">-</div>
          </div>
          <div class="box">
            <div class="k">Ultimate</div>
            <div class="v" id="ultimate">-</div>
            <div class="mini" id="ultimateDesc">-</div>
          </div>
          <div class="box">
            <div class="k">Phước lành</div>
            <div class="v" id="blessCount">0</div>
            <div class="mini">Trial: 10 tầng/1 phước. Dungeon: Sứ giả drop phước.</div>
          </div>
          <div class="box">
            <div class="k">Shop Level</div>
            <div class="v" id="shopLevel">0</div>
            <div class="mini">Tip để tăng hàng hiếm.</div>
          </div>
          <div class="box">
            <div class="k">Thể lực</div>
            <div class="v" id="stamina">10/10</div>
            <div class="mini" id="staminaHint">Tiêu hao theo hành động.</div>
          </div>
          <div class="box">
            <div class="k">Turn</div>
            <div class="v" id="turn">0</div>
            <div class="mini" id="ap">Hành động: 0/10</div>
          </div>
          <div class="box">
            <div class="k">Chế độ</div>
            <div class="v" id="mode">Free</div>
            <div class="mini" id="modeHint">-</div>
          </div>
        </div>

        <div style="margin-top:12px;">
          <p class="sectionTitle">Nhật ký</p>
          <div class="log" id="log"></div>
        </div>
      </aside>
    </div>
  </div>

  <div class="overlay" id="overlayCreate">
    <div class="modal">
      <div class="modalTop">
        <div>
          <h2>Tạo nhân vật</h2>
          <p>
            Chủng tộc reroll <b>3 lần</b> (sau đó khóa). Chức nghiệp & Ultimate random theo độ hiếm.
            <br />Thua battle → <b>khởi động lại game</b>.
          </p>
        </div>
        <div style="display:flex; gap:10px;">
          <button class="btn" id="btnRerollAll">Random lại</button>
          <button class="btn btnDanger" id="btnCheat">Cheat</button>
          <button class="btn btnPrimary" id="btnStart">Bắt đầu</button>
        </div>
      </div>
      <div class="modalBody">
        <div class="field">
          <label>Tên</label>
          <input id="nameInput" maxlength="24" placeholder="Ví dụ: Aster" />
          <div class="row">
            <span class="tag" id="tagAge">Tuổi: -</span>
            <span class="tag" id="tagLocation">Nơi: -</span>
            <span class="tag" id="tagNPC">NPC: -</span>
          </div>

          <div class="row" style="margin-top:12px;">
            <div style="flex:1;">
              <label>Chủng tộc (khóa sau khi start)</label>
              <div class="row" style="margin-top:8px;">
                <span class="tag" id="raceTag">-</span>
                <button class="btn" id="btnRerollRace">Reroll tộc (3)</button>
              </div>
              <div class="mini" id="racePerk">-</div>
            </div>
            <div style="flex:1;">
              <label>Chức nghiệp (random)</label>
              <div class="row" style="margin-top:8px;">
                <span class="tag" id="jobTag">-</span>
              </div>
              <div class="mini" id="jobPerk">-</div>
            </div>
          </div>

          <div style="margin-top:12px;">
            <label>Ultimate (random 1 lần)</label>
            <div class="row" style="margin-top:8px;">
              <span class="tag" id="ultTag">-</span>
            </div>
            <div class="mini" id="ultPerk">-</div>
          </div>

          <div class="tagList" id="bonusTags"></div>
        </div>

        <div class="field">
          <label>Stat (random)</label>
          <div class="twoCols" style="margin-top:10px;">
            <div class="box">
              <div class="k">HP</div>
              <div class="v" id="stHP">-</div>
            </div>
            <div class="box">
              <div class="k">MP</div>
              <div class="v" id="stMP">-</div>
            </div>
            <div class="box">
              <div class="k">STR</div>
              <div class="v" id="stSTR">-</div>
            </div>
            <div class="box">
              <div class="k">DEX</div>
              <div class="v" id="stDEX">-</div>
            </div>
            <div class="box">
              <div class="k">INT</div>
              <div class="v" id="stINT">-</div>
            </div>
            <div class="box">
              <div class="k">CHA</div>
              <div class="v" id="stCHA">-</div>
            </div>
            <div class="box">
              <div class="k">LUK</div>
              <div class="v" id="stLUK">-</div>
            </div>
            <div class="box">
              <div class="k">DEF</div>
              <div class="v" id="stDEF">-</div>
            </div>
          </div>
          <div class="mini" style="margin-top:10px;">
            Lệnh: <b>help</b>, <b>battle</b>, <b>dungeon</b>, <b>trial</b>, <b>shop</b>, <b>money</b>, <b>gacha</b>,
            <b>forge</b>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div class="overlay" id="overlayShop">
    <div class="modal">
      <div class="modalTop">
        <div>
          <h2>Shop (tip để lên cấp)</h2>
          <p>Mua đồ hồi phục / vũ khí / giáp. Tip cho chủ quán để shop lên level và xuất hiện hàng hiếm hơn.</p>
        </div>
        <div style="display:flex; gap:10px;">
          <button class="btn" id="btnTipShop">Tip</button>
          <button class="btn btnPrimary" id="btnCloseShop">Đóng</button>
        </div>
      </div>
      <div class="modalBody">
        <div class="field">
          <label>Chủ quán</label>
          <div class="mini" id="shopkeeperLine">-</div>
          <div class="tagList">
            <span class="tag" id="shopLevelTag">Shop level: 0</span>
            <span class="tag" id="shopTipCostTag">Tip cost: -</span>
          </div>
        </div>
        <div class="field">
          <label>Hàng đang bán</label>
          <div class="list" id="shopList"></div>
        </div>
      </div>
    </div>
  </div>

  <div class="overlay" id="overlayForge">
    <div class="modal">
      <div class="modalTop">
        <div>
          <h2>Rèn đồ (+1 đến +100)</h2>
          <p>Chance thành công: <b>1 / 10^n</b> với n là cấp nâng tiếp theo.</p>
        </div>
        <div style="display:flex; gap:10px;">
          <button class="btn btnPrimary" id="btnCloseForge">Đóng</button>
        </div>
      </div>
      <div class="modalBody">
        <div class="field">
          <label>Chọn trang bị để rèn</label>
          <div class="list" id="forgeList"></div>
        </div>
        <div class="field">
          <label>Chi tiết nâng cấp</label>
          <div class="mini" id="forgeDetail">Chọn một trang bị.</div>
          <div class="row">
            <button class="btn btnPrimary" id="btnForgeDo" disabled>Nâng cấp</button>
            <button class="btn" id="btnForgeRefresh">Làm mới</button>
          </div>
          <div class="mini" id="forgeHint" style="margin-top:10px;"></div>
        </div>
      </div>
    </div>
  </div>

  <div class="overlay" id="overlayTrial">
    <div class="modal">
      <div class="modalTop">
        <div>
          <h2>Trial Thần Linh (50 tầng / thần)</h2>
          <p>Nhận phước lành khi vượt <b>mỗi 10 tầng</b>. (10/20/30/40/50)</p>
        </div>
        <div style="display:flex; gap:10px;">
          <button class="btn btnPrimary" id="btnCloseTrial">Đóng</button>
        </div>
      </div>
      <div class="modalBody">
        <div class="field">
          <label>Chọn thần linh</label>
          <select id="trialSelect"></select>
          <div class="tagList" id="trialTags"></div>
          <div class="row">
            <button class="btn btnPrimary" id="btnStartTrial">Bắt đầu / Tiếp tục</button>
          </div>
          <div class="mini">Trong trial, thắng 1 tầng xong gõ <b>next</b> để vào tầng tiếp theo.</div>
        </div>
        <div class="field">
          <label>Tiến trình</label>
          <div class="mini" id="trialProgress">-</div>
        </div>
      </div>

      <!-- Hero Trial Overlay -->
      <div class="overlay" id="overlayHeroTrial">
        <div class="modal">
          <div class="modalTop">
            <div>
              <h2>Trial Anh Hùng (100 tầng)</h2>
              <p>Quái mỗi tầng <b>Lv99</b>. Vượt 100 tầng nhận <b>Phước Lành Anh Hùng</b> + <b>Thánh Kiếm</b> + <b>Thánh
                  Giáp</b>.</p>
            </div>
            <div style="display:flex; gap:10px;">
              <button class="btn btnPrimary" id="btnCloseHeroTrial">Đóng</button>
            </div>
          </div>
          <div class="modalBody">
            <div class="field">
              <div class="tagList" id="heroTrialTags"></div>
              <div class="mini" id="heroTrialProgress">-</div>
              <div class="row" style="margin-top:10px;">
                <button class="btn btnPrimary" id="btnStartHeroTrial">Bắt đầu / Tiếp tục</button>
              </div>
              <div class="mini">Trong Hero Trial, thắng 1 tầng xong bấm <b>Next</b> để vào tầng tiếp theo.</div>
            </div>
          </div>
        </div>
      </div>

      <!-- Talents Overlay -->
      <div class="overlay" id="overlayTalents">
        <div class="modal" style="width:min(820px,100%);">
          <div class="modalTop">
            <div>
              <h2>Talent Trees</h2>
              <p id="talentHint">Mỗi lần lên level: +1 Talent Point.</p>
              <div class="tagList" id="talentTags"></div>
            </div>
            <div style="display:flex; gap:10px;">
              <button class="btn btnPrimary" id="btnCloseTalents">Đóng</button>
            </div>
          </div>
          <div class="modalBody" style="grid-template-columns: 1fr;">
            <div class="field">
              <label>Cây tài năng</label>
              <div id="talentGrid" style="display:grid; gap:10px;"></div>
            </div>
          </div>
        </div>
      </div>

      <!-- Gamble Overlay -->
      <div class="overlay" id="overlayGamble">
        <div class="modal" style="width:min(560px,100%);">
          <div class="modalTop">
            <div>
              <h2>Đánh bạc (Lotto)</h2>
              <p class="mini">Tỉ lệ hiển thị: <b>50%</b> • Tỉ lệ thật: <b>10%</b> (không nói với player).</p>
            </div>
            <div style="display:flex; gap:10px;">
              <button class="btn btnPrimary" id="btnCloseGamble">Đóng</button>
            </div>
          </div>
          <div class="modalBody">
            <div class="field">
              <label>Số tiền cược</label>
              <input id="gambleBet" type="number" min="1" step="1" placeholder="Nhập số vàng cược..." />
              <div class="row" style="margin-top:10px;">
                <button class="btn btnPrimary" id="btnGambleRoll">Quay Lotto</button>
              </div>
              <div class="gachaAnim" style="margin-top:12px;">
                <div class="gachaBox" id="gambleAnimBox">
                  <div class="gachaGlow"></div>
                  <div class="gachaText" id="gambleAnimText">READY</div>
                </div>
              </div>
              <div class="mini" id="gambleResult"></div>
            </div>
          </div>
        </div>
      </div>

    </div>
  </div>

  <div class="overlay" id="overlayGacha">
    <div class="modal" style="width:min(560px,100%);">
      <div class="modalTop">
        <div>
          <h2>Gacha (100 vàng)</h2>
          <p>Legendary 0.1% • Legend 1% • Rare 3% • Common 15.9% • Trash 80%</p>
        </div>
        <div style="display:flex; gap:10px;">
          <button class="btn btnPrimary" id="btnCloseGacha">Đóng</button>
        </div>
      </div>
      <div class="gachaBox">
        <div class="spinner"></div>
        <div class="mini" id="gachaStatus">Đang chuẩn bị…</div>
        <div class="reveal" id="gachaReveal" style="display:none;"></div>
        <div class="row" style="justify-content:center; gap:10px; margin-top: 14px;">
          <button class="btn" id="btnGacha1">Gacha x1</button>
          <button class="btn" id="btnGacha10">Gacha x10</button>
          <button class="btn btnPrimary" id="btnGachaOk" style="display:none;">OK</button>
        </div>
      </div>
    </div>
  </div>

  <!-- Cheat Popup -->
  <div class="overlay" id="overlayCheat" style="display:none;">
    <div class="modal" style="max-width:400px;">
      <h2>RPG_V11</h2>
      <p id="cheatMsg" class="center-text"></p>
      <button class="btn btnPrimary" onclick="closeCheat()">OK</button>
    </div>
  </div>


  <script>
    window.addEventListener("DOMContentLoaded", () => {
      /** ===================== Utilities ===================== **/
      const randInt = (min, max) => Math.floor(Math.random() * (max - min + 1)) + min;
      const clamp = (x, a, b) => Math.max(a, Math.min(b, x));
      const pick = (arr) => arr[Math.floor(Math.random() * arr.length)];
      const nowTag = () => new Date().toLocaleTimeString([], { hour: "2-digit", minute: "2-digit" });
      const uid = () => (Math.random().toString(16).slice(2) + Date.now().toString(16)).slice(0, 16);

      function normalize(s) {
        return (s || "")
          .toLowerCase()
          .normalize("NFD").replace(/[\u0300-\u036f]/g, "")
          .replace(/[^a-z0-9\s]/g, " ")
          .replace(/\s+/g, " ")
          .trim();
      }

      function succeedTenPow(n) {
        for (let i = 0; i < n; i++) {
          if (randInt(0, 9) !== 0) return false;
        }
        return true;
      }

      const LOCATIONS = [
        "Thị trấn Mưa Đêm", "Rừng Sương", "Hẻm Đá Xám", "Cảng Gió", "Đồi Hồng", "Hầm Mỏ Cũ",
        "Đền Lặng", "Chợ Đêm", "Phố Sách", "Sân Đấu Bỏ Hoang", "Đấu Trường Nhỏ", "Bờ Hồ Lấp Lánh", "Thành phố Đạo Tặc"
      ];

      /** ===================== Location Effects (Apocalypse) ===================== **/
      const LOCATION_EFFECTS = [
        {
          key: "Thành Phố Đạo Tặc", match: (name) => /đạo\s*tặc/i.test(name), onEnter: (p) => {
            p.stamina = Math.max(0, p.stamina - 8);
            addLog("🏴 Bạn bước vào <b>Thành Phố Đạo Tặc</b>. Không khí đầy nguy hiểm...");
          },
          onTurn: (p) => {
            if (p.inv && p.inv.length > 0 && Math.random() < 0.40) {
              const idx = randInt(0, p.inv.length - 1);
              const lost = p.inv.splice(idx, 1)[0];
              addLog(`🏴 Bị cướp kho: mất <b>${itemMeta(lost.id).name}</b>!`);
              pushStory(`Bạn bị cướp: mất <b>${itemMeta(lost.id).name}</b> trong kho.`);
              if (p.equipped.weaponUid === lost.uid) p.equipped.weaponUid = null;
              if (p.equipped.armorUid === lost.uid) p.equipped.armorUid = null;
            }
          }
        },
        {
          key: "Vùng Tro Tàn", match: (name) => /tro|ash|tàn/i.test(name), onEnter: (p) => {
            const burn = Math.max(1, Math.floor(p.max.HP * 0.05));
            p.stats.HP = clamp(p.stats.HP - burn, 1, p.max.HP);
            addLog(`🌫️ Tro nóng bỏng: -${burn} HP khi đặt chân vào.`);
          }, onTurn: (p) => {
            p.stamina = Math.max(0, p.stamina - 6);
            addLog("🌫️ Bụi tro làm bạn kiệt sức (-6 STA).");
          }
        },
        {
          key: "Nghĩa Địa", match: (name) => /nghĩa|mộ|grave/i.test(name), onEnter: (p) => {
            p.age = (p.age || 0) + 1;
            addLog("🪦 Hơi lạnh âm giới... Tuổi tăng +1.");
          }, onTurn: (p) => {
            p.stats.MP = clamp(p.stats.MP - 4, 0, p.max.MP);
            addLog("🪦 Âm khí rút mana (-4 MP).");
          }
        },
        {
          key: "Khu Ổ Chuột", match: (name) => /ổ\s*chuột|slum|khu\s*nghèo/i.test(name), onEnter: (p) => {
            const lostGold = Math.min(p.gold, randInt(20, 80));
            p.gold -= lostGold;
            addLog(`🧱 Bị móc túi: -${lostGold} vàng.`);
          }, onTurn: (p) => {
            p._special = p._special || {};
            p._special.locUnlucky = 0.10;
            addLog("🧱 Vận xui bám theo (giảm may mắn tạm thời).");
          }
        },
        {
          key: "Tàn Tích", match: (name) => /tàn\s*tích|ruin/i.test(name), onEnter: (p) => {
            const keys = Object.keys(p.bag || {}).filter(k => (p.bag[k] || 0) > 0);
            if (keys.length && Math.random() < 0.35) {
              const it = pick(keys);
              p.bag[it] = Math.max(0, (p.bag[it] || 0) - 1);
              addLog(`🏚️ Tàn tích phá hỏng 1 <b>${itemMeta(it).name}</b>.`);
            }
          }, onTurn: (p) => {
            const dmg = Math.max(1, Math.floor(p.max.HP * 0.03));
            p.stats.HP = clamp(p.stats.HP - dmg, 1, p.max.HP);
            addLog(`🏚️ Mảnh vỡ cứa rách (-${dmg} HP).`);
          }
        },
      ];

      function getLocationEffect(name) {
        const s = name || "";
        return LOCATION_EFFECTS.find(e => e.match(s)) || null;
      }

      function applyLocationEnter() {
        const eff = getLocationEffect(game.player.location);
        game.player.locationEffectKey = eff ? eff.key : null;
        if (eff?.onEnter) eff.onEnter(game.player);
      }



      const NPC_TRAITS = [
        "hiền lành", "tham lam", "cộc cằn", "hào sảng", "đa nghi", "lãng mạn",
        "thực dụng", "tò mò", "lạnh lùng", "thích giúp người", "hay cáu", "bí hiểm"
      ];

      const NPC_ROLES = [
        "thương nhân", "lính gác", "thầy thuốc", "thợ rèn", "học giả", "kẻ đưa tin",
        "đạo sĩ", "nhà thám hiểm", "kẻ lang thang", "chủ quán", "nghệ sĩ", "tay môi giới"
      ];

      const RACES = [
        { id: "human", name: "Nhân loại", bonus: { CHA: +3, LUK: +1 }, perk: "Đa dụng: +3 CHA, +1 LUK.", maxAge: 90 },
        { id: "elf", name: "Tinh linh", bonus: { DEX: +4, INT: +2 }, perk: "Nhanh & thông minh: +4 DEX, +2 INT.", maxAge: 750 },
        { id: "dwarf", name: "Người lùn", bonus: { DEF: +5, STR: +2, HP: +10 }, perk: "Cứng cáp: +5 DEF, +2 STR, +10 HP.", maxAge: 350 },
        { id: "orc", name: "Orc", bonus: { STR: +6, HP: +12 }, perk: "Sức mạnh cuồng bạo: +6 STR, +12 HP.", maxAge: 75 },
        { id: "kitsune", name: "Hồ ly", bonus: { CHA: +5, LUK: +4 }, perk: "Mê hoặc & may mắn: +5 CHA, +4 LUK.", maxAge: 1000 },
        { id: "undead", name: "Bất tử", bonus: { DEF: +4, INT: +4, HP: +8 }, perk: "Lạnh lẽo: +4 DEF, +4 INT, +8 HP.", maxAge: 9999 },
      ];
      const raceById = (id) => RACES.find(r => r.id === id) || RACES[0];

      const ELEMENTS = ["Lửa", "Băng", "Sấm", "Gió", "Đất", "Bóng", "Ánh", "Nước", "Độc", "Tinh Tú"];
      const FORMS = ["Chém", "Đâm", "Bộc Phá", "Mũi Tên", "Tia", "Vòng Tròn", "Bão", "Kết Giới", "Hút", "Ấn Chú"];
      const MODS = ["Nhanh", "Nặng", "Xuyên Giáp", "Hồi Phục", "Tê Liệt", "Độc Tố", "Tăng Lực", "Suy Yếu", "Bạo Kích", "Thần Tốc"];
      const RARITY = ["trash", "common", "rare", "legend", "legendary"];
      function rarityRank(r) { return ({ trash: 0, common: 1, rare: 2, legend: 3, legendary: 4 }[r] || 0); }
      const rarityLabel = (r) => ({ trash: "Trash", common: "Common", rare: "Rare", legend: "Legend", legendary: "Legendary" }[r] || r);

      function makeActiveSkill(i) {
        const el = ELEMENTS[i % ELEMENTS.length];
        const form = FORMS[(i * 3) % FORMS.length];
        const mod = MODS[(i * 7) % MODS.length];

        let rarity = "common";
        if (i >= 75 && i < 92) rarity = "rare";
        if (i >= 92 && i < 98) rarity = "legend";
        if (i >= 98) rarity = "legendary";

        const baseMp = rarity === "common" ? randInt(2, 4) : rarity === "rare" ? randInt(4, 6) : rarity === "legend" ? randInt(6, 8) : randInt(8, 10);
        const cd = rarity === "common" ? randInt(0, 1) : rarity === "rare" ? randInt(1, 2) : rarity === "legend" ? randInt(2, 3) : randInt(3, 4);
        const mult = rarity === "common" ? (1.05 + (i % 7) * 0.03) : rarity === "rare" ? (1.35 + (i % 7) * 0.04) : rarity === "legend" ? (1.75 + (i % 6) * 0.05) : (2.25 + (i % 5) * 0.06);

        const types = ["dmg", "dmg", "dmg", "heal", "shield", "drain", "poison", "stun", "debuff", "buff"];
        const type = types[i % types.length];
        const scale = (i % 3 === 0) ? "STR" : (i % 3 === 1) ? "INT" : "DEX";

        let extra = {};
        let desc = "";
        if (type === "heal") {
          extra.healPct = rarity === "common" ? 0.18 : rarity === "rare" ? 0.26 : rarity === "legend" ? 0.34 : 0.45;
          desc = `Hồi ${Math.round(extra.healPct * 100)}% HP (dựa trên Max HP).`;
        } else if (type === "shield") {
          extra.shieldPct = rarity === "common" ? 0.18 : rarity === "rare" ? 0.26 : rarity === "legend" ? 0.34 : 0.45;
          desc = `Nhận lá chắn ${Math.round(extra.shieldPct * 100)}% Max HP (2 lượt).`;
        } else if (type === "drain") {
          extra.lifesteal = rarity === "common" ? 0.18 : rarity === "rare" ? 0.24 : rarity === "legend" ? 0.30 : 0.38;
          desc = `Gây sát thương và hút máu (${Math.round(extra.lifesteal * 100)}% dmg).`;
        } else if (type === "poison") {
          extra.dotPct = rarity === "common" ? 0.07 : rarity === "rare" ? 0.10 : rarity === "legend" ? 0.13 : 0.16;
          extra.dotTurns = rarity === "common" ? 2 : rarity === "rare" ? 3 : 4;
          desc = `Gây độc: mất ${Math.round(extra.dotPct * 100)}% Max HP mỗi lượt trong ${extra.dotTurns} lượt.`;
        } else if (type === "stun") {
          extra.stunChance = rarity === "common" ? 0.20 : rarity === "rare" ? 0.28 : rarity === "legend" ? 0.36 : 0.45;
          desc = `Có ${Math.round(extra.stunChance * 100)}% làm choáng (quái mất lượt kế).`;
        } else if (type === "debuff") {
          extra.defDown = rarity === "common" ? 0.12 : rarity === "rare" ? 0.18 : rarity === "legend" ? 0.24 : 0.32;
          extra.debuffTurns = rarity === "common" ? 2 : rarity === "rare" ? 3 : 4;
          desc = `Giảm DEF quái ${Math.round(extra.defDown * 100)}% trong ${extra.debuffTurns} lượt.`;
        } else if (type === "buff") {
          extra.buffStat = (i % 2 === 0) ? "STR" : (i % 3 === 0) ? "DEX" : "INT";
          extra.buffPct = rarity === "common" ? 0.14 : rarity === "rare" ? 0.20 : rarity === "legend" ? 0.27 : 0.36;
          extra.buffTurns = rarity === "common" ? 2 : rarity === "rare" ? 3 : 4;
          desc = `Tăng ${extra.buffStat} ${Math.round(extra.buffPct * 100)}% trong ${extra.buffTurns} lượt.`;
        } else {
          extra.pierce = (mod === "Xuyên Giáp") ? (rarity === "common" ? 0.20 : rarity === "rare" ? 0.30 : rarity === "legend" ? 0.40 : 0.55) : 0.0;
          extra.crit = (mod === "Bạo Kích") ? (rarity === "common" ? 0.12 : rarity === "rare" ? 0.18 : rarity === "legend" ? 0.25 : 0.33) : 0.0;
          desc = `Gây sát thương (${scale})${extra.pierce ? `, xuyên DEF` : ""}${extra.crit ? `, có chí mạng` : ""}.`;
        }

        const name = `${el} ${form} ${mod}`;
        return {
          id: `sk_${i + 1}`,
          name,
          kind: "active",
          rarity,
          mp: baseMp,
          cd,
          mult,
          scale,
          type,
          desc,
          extra,
        };
      }

      const ULTIMATES = [
        { id: "ult_void_break", name: "Void Break", mp: 8, cd: 999, rarity: "legendary", type: "dmg", scale: "STR", mult: 3.0, desc: "Dmg cực lớn, xuyên DEF mạnh.", extra: { pierce: 0.65, crit: 0.18 } },
        { id: "ult_phoenix", name: "Phoenix Rebirth", mp: 9, cd: 999, rarity: "legendary", type: "heal", scale: "INT", mult: 0, desc: "Hồi đầy HP + lá chắn.", extra: { healFull: true, shieldPct: 0.35, shieldTurns: 2 } },
        { id: "ult_time_stop", name: "Time Stop", mp: 9, cd: 999, rarity: "legendary", type: "buff", scale: "INT", mult: 0, desc: "Bạn được thêm 1 lượt + tăng DEX.", extra: { extraTurn: true, buffStat: "DEX", buffPct: 0.30, buffTurns: 2 } },
        { id: "ult_judgement", name: "Judgement", mp: 8, cd: 999, rarity: "legendary", type: "dmg", scale: "INT", mult: 2.6, desc: "Dmg chuẩn + hồi MP theo sát thương.", extra: { pure: true, mpRefund: 0.22 } },
        { id: "ult_meteor", name: "Meteor Fall", mp: 10, cd: 999, rarity: "legendary", type: "dmg", scale: "INT", mult: 3.4, desc: "Dmg cực lớn.", extra: { crit: 0.10 } },
        { id: "ult_dragon_rage", name: "Dragon Rage", mp: 9, cd: 999, rarity: "legendary", type: "buff", scale: "STR", mult: 0, desc: "Tăng STR + DEF, miễn 1 đòn.", extra: { buffStat: "STR", buffPct: 0.35, buffTurns: 3, guard: true } },
        { id: "ult_abyss_chain", name: "Abyss Chain", mp: 8, cd: 999, rarity: "legendary", type: "debuff", scale: "CHA", mult: 1.8, desc: "Gây dmg + giảm DEF mạnh.", extra: { defDown: 0.40, debuffTurns: 4, pierce: 0.25 } },
        { id: "ult_stellar_lance", name: "Stellar Lance", mp: 9, cd: 999, rarity: "legendary", type: "dmg", scale: "DEX", mult: 2.9, desc: "Dmg nhanh + tỉ lệ choáng.", extra: { stunChance: 0.40, pierce: 0.30 } },
        { id: "ult_sanctuary", name: "Sanctuary", mp: 8, cd: 999, rarity: "legendary", type: "shield", scale: "INT", mult: 0, desc: "Kết giới khổng lồ.", extra: { shieldPct: 0.55, shieldTurns: 3, cleanse: true } },
        { id: "ult_blood_oath", name: "Blood Oath", mp: 7, cd: 999, rarity: "legendary", type: "drain", scale: "STR", mult: 2.4, desc: "Hút máu cực mạnh.", extra: { lifesteal: 0.55, crit: 0.20 } },
        { id: "ult_world_cleave", name: "World Cleave", mp: 10, cd: 999, rarity: "legendary", type: "dmg", scale: "STR", mult: 3.2, desc: "Chém nứt đất.", extra: { pierce: 0.45 } },
        { id: "ult_mind_overflow", name: "Mind Overflow", mp: 9, cd: 999, rarity: "legendary", type: "buff", scale: "INT", mult: 0, desc: "Full MP + tăng INT.", extra: { mpFull: true, buffStat: "INT", buffPct: 0.40, buffTurns: 3 } },
      ];

      const ACTIVE_SKILLS = Array.from({ length: 100 }, (_, i) => makeActiveSkill(i)).concat(ULTIMATES.map(u => ({ ...u, kind: "ultimate", cd: 999 })));

      function makePassive(i) {
        let rarity = "common";
        if (i >= 75 && i < 92) rarity = "rare";
        if (i >= 92 && i < 98) rarity = "legend";
        if (i >= 98) rarity = "legendary";

        const types = ["hpRegen", "mpRegen", "crit", "pierce", "gold", "exp", "dmg", "def", "maxHP", "maxMP"];
        const type = types[i % types.length];

        const base = rarity === "common" ? 0.06 : rarity === "rare" ? 0.09 : rarity === "legend" ? 0.12 : 0.16;
        const val = +(base + (i % 7) * 0.01).toFixed(2);

        const name = `Bị Động #${String(i + 1).padStart(3, "0")} — ${type}`;
        const descMap = {
          hpRegen: `Mỗi lượt hồi ${Math.round(val * 100)}% Max HP.`,
          mpRegen: `Mỗi lượt hồi ${Math.round(val * 100)}% Max MP.`,
          crit: `+${Math.round(val * 100)}% tỉ lệ chí mạng.`,
          pierce: `+${Math.round(val * 100)}% xuyên giáp.`,
          gold: `+${Math.round(val * 100)}% vàng khi kiếm tiền.`,
          exp: `+${Math.round(val * 100)}% EXP nhận được.`,
          dmg: `+${Math.round(val * 100)}% sát thương gây ra.`,
          def: `+${Math.round(val * 100)}% DEF tổng.`,
          maxHP: `+${Math.round(val * 100)}% Max HP.`,
          maxMP: `+${Math.round(val * 100)}% Max MP.`,
        };
        return { id: `ps_${i + 1}`, name, rarity, type, val, desc: descMap[type] || "Tăng chỉ số." };
      }
      const PASSIVES = Array.from({ length: 100 }, (_, i) => makePassive(i));

      // =========================
      // PROFESSION SYSTEM (Chức nghiệp)
      // =========================
      const PROF_RARITY_POOL = ["common", "common", "common", "common", "common", "common", "common", "common", "common", "common", "common", "common", "common", "common", "common", "common", "common", "common", "common", "common", "rare", "rare", "rare", "rare", "legend", "legendary", "mythic"];;
      const PROFESSIONS = Array.from({ length: 60 }, (_, i) => makeProfession(i));

      function makeProfession(i) {
        const rarity = pick(PROF_RARITY_POOL);
        const themes = [
          ["Lính đánh thuê", "STR", "DEX"], ["Học giả", "INT", "MP"], ["Nhạc sĩ", "CHA", "MP"], ["Đạo tặc", "DEX", "LUK"],
          ["Hiệp sĩ", "DEF", "HP"], ["Pháp sư", "INT", "MP"], ["Thợ săn", "DEX", "STR"], ["Tu sĩ", "MP", "HP"],
          ["Thợ rèn", "STR", "DEF"], ["Nhà thám hiểm", "DEX", "HP"], ["Nhà giả kim", "INT", "LUK"], ["Thương nhân", "CHA", "LUK"],
          ["Kiếm sĩ", "STR", "DEX"], ["Cung thủ", "DEX", "LUK"], ["Võ tăng", "STR", "HP"], ["Chiến lược gia", "INT", "CHA"],
          ["Truyền giáo", "CHA", "HP"], ["Phù thủy", "INT", "LUK"], ["Đấu sĩ", "STR", "HP"], ["Kỵ binh", "DEX", "DEF"]
        ];
        const t = pick(themes);
        const name = `${t[0]} #${i + 1}`;
        const base = (rarity === "common") ? 1 : (rarity === "rare") ? 7 : (rarity === "legend") ? 12 : (rarity === "legendary") ? 18 : 26;
        const bonus = { HP: 0, MP: 0, STR: 0, DEX: 0, INT: 0, CHA: 0, LUK: 0, DEF: 0 };

        const addKey = (k, v) => { if (k === "HP" || k === "MP") bonus[k] += v * 2; else bonus[k] += v; };
        addKey(t[1], base);
        addKey(t[2], base);
        if (rarity === "rare") { bonus.HP += 4; bonus.DEF += 2; }
        if (rarity === "legend") { bonus.HP += 10; bonus.DEF += 4; bonus.LUK += 1; }
        if (rarity === "legendary" || rarity === "mythic") {
          bonus.HP += base * 2;
          bonus.DEF += Math.max(1, Math.floor(base / 2));
          bonus.LUK += 1;
        }
        const perk = `Bonus: ${fmtBonus(bonus)}.`;
        return { id: `prof_${i}`, name, rarity, bonus, perk };
      }
      function professionById(id) { return PROFESSIONS.find(p => p.id === id) || PROFESSIONS[0]; }
      function rollProfession() { return pick(PROFESSIONS); }

      function fmtBonus(b) {
        const parts = [];
        for (const k of ["HP", "MP", "STR", "DEX", "INT", "CHA", "LUK", "DEF"]) {
          const v = b[k] || 0; if (!v) continue;
          parts.push(`${k}${v > 0 ? "+" : ""}${v}`);
        }
        return parts.join(", ") || "—";
      }


      function makeWeakness(i) {
        const kinds = ["Frail", "Slow", "Cursed", "Greedy", "Forgetful", "Glass Mind", "Hollow Bones", "Coward", "Clumsy", "Sickly"];
        const k = kinds[i % kinds.length];
        const severity = (i % 5) + 1;
        const name = `Nhược #${String(i + 1).padStart(3, "0")} — ${k}`;
        const effects = {
          Frail: { HP: -(4 * severity), DEF: -(1 * severity) },
          Slow: { DEX: -(2 * severity) },
          Cursed: { LUK: -(2 * severity) },
          Greedy: { goldMult: -(0.08 * severity) },
          Forgetful: { mpCostMult: +(0.06 * severity) },
          "Glass Mind": { INT: -(2 * severity), MP: -(2 * severity) },
          "Hollow Bones": { STR: -(2 * severity), HP: -(3 * severity) },
          Coward: { dmgTakenMult: +(0.06 * severity) },
          Clumsy: { critMult: -(0.05 * severity), DEX: -(1 * severity) },
          Sickly: { hpRegenMult: -(0.20 * severity), HP: -(2 * severity) },
        };
        const eff = effects[k];
        const parts = [];
        for (const [kk, vv] of Object.entries(eff)) {
          if (typeof vv === "number" && ["goldMult", "mpCostMult", "dmgTakenMult", "critMult", "hpRegenMult"].includes(kk)) {
            parts.push(`${kk} ${vv > 0 ? "+" : ""}${Math.round(vv * 100)}%`);
          } else {
            parts.push(`${kk} ${vv > 0 ? "+" : ""}${vv}`);
          }
        }
        return { id: `wk_${i + 1}`, name, kind: k, severity, eff, desc: parts.join(", ") };
      }
      const WEAKNESSES = Array.from({ length: 100 }, (_, i) => makeWeakness(i));

      const skillById = (id) => ACTIVE_SKILLS.find(s => s.id === id) || null;
      const passiveById = (id) => PASSIVES.find(p => p.id === id) || null;

      const BLESSINGS = Array.from({ length: 200 }, (_, i) => {
        const themes = ["Mưa", "Gió", "Lửa", "Băng", "Bóng", "Ánh", "Đá", "Sấm", "Mộc", "Tinh Tú"];
        const t = themes[i % themes.length];
        const name = `Phước ${t} #${String(i + 1).padStart(3, "0")}`;
        const effects = [
          { stat: "HP", delta: 2 },
          { stat: "MP", delta: 1 },
          { stat: "STR", delta: 1 },
          { stat: "DEX", delta: 1 },
          { stat: "INT", delta: 1 },
          { stat: "CHA", delta: 1 },
          { stat: "LUK", delta: 1 },
          { stat: "DEF", delta: 1 },
        ];
        const eff = effects[i % effects.length];
        const delta = eff.delta + (i % 12 === 0 ? 1 : 0);
        return { id: `bl_${i + 1}`, name, stat: eff.stat, delta, desc: `+${delta} ${eff.stat}` };
      });
      const HERO_BLESSING = {
        id: "hero_blessing",
        name: "Phước Lành Anh Hùng",
        desc: "Sức mạnh thánh hoá. +20 tất cả stat, +200 HP/MP. Mở giới hạn sức mạnh (Lv hiệu lực 999).",
        bonus: { HP: 200, MP: 200, STR: 20, DEX: 20, INT: 20, CHA: 20, LUK: 20, DEF: 20 },
        special: true
      };

      function randomBlessing() {
        const owned = new Set(game.player.blessings.map(b => b.id));
        const pool = BLESSINGS.filter(b => !owned.has(b.id));
        return pick(pool.length ? pool : BLESSINGS);
      }

      const GODS = [
        { id: "rain", name: "Thần Mưa", desc: "Thiên về HP/DEF/MP. 50 tầng." },
        { id: "flame", name: "Thần Lửa", desc: "Thiên về STR/ATK. 50 tầng." },
        { id: "storm", name: "Thần Sấm", desc: "Thiên về DEX/crit. 50 tầng." },
        { id: "shade", name: "Thần Bóng", desc: "Thiên về độc/nhược hoá. 50 tầng." },
        { id: "light", name: "Thần Ánh", desc: "Thiên về hồi phục/kết giới. 50 tầng." },
        { id: "star", name: "Thần Tinh Tú", desc: "Thiên về INT/MP. 50 tầng." },
      ];
      const godById = (id) => GODS.find(g => g.id === id) || GODS[0];

      const ITEM_DB = {
        potion: { id: "potion", name: "Thuốc Hồi HP", type: "consumable", rarity: "trash", price: 25, desc: "Hồi 15 HP.", eff: { hp: 15 } },
        ether: { id: "ether", name: "Tinh Thể MP", type: "consumable", rarity: "trash", price: 25, desc: "Hồi 8 MP.", eff: { mp: 8 } },
        hi_potion: { id: "hi_potion", name: "Đại Hồi HP", type: "consumable", rarity: "common", price: 80, desc: "Hồi 40 HP.", eff: { hp: 40 } },
        hi_ether: { id: "hi_ether", name: "Đại Hồi MP", type: "consumable", rarity: "common", price: 80, desc: "Hồi 20 MP.", eff: { mp: 20 } },
        lifepotion: { id: "lifepotion", name: "Thuốc Tăng Tuổi Thọ", type: "consumable", rarity: "rare", price: 900, desc: "Tăng tuổi thọ tối đa +15.", eff: { maxAge: 15 } },
        luck_elixir: { id: "luck_elixir", name: "Luck Elixir", type: "consumable", rarity: "legendary", price: 0, desc: "Tăng may mắn trong 2 turn: gacha xịn hơn, rèn dễ hơn.", eff: { luckTurns: 2 } },

        ore: { id: "ore", name: "Quặng Rèn", type: "material", rarity: "common", price: 35, desc: "Dùng để nâng cấp vũ khí/giáp." },

        wooden_sword: { id: "wooden_sword", name: "Kiếm Gỗ", type: "weapon", rarity: "common", price: 120, atk: 3, spd: 0, desc: "ATK +3." },
        iron_sword: { id: "iron_sword", name: "Kiếm Sắt", type: "weapon", rarity: "common", price: 240, atk: 6, spd: 0, desc: "ATK +6." },
        steel_sword: { id: "steel_sword", name: "Kiếm Thép", type: "weapon", rarity: "rare", price: 520, atk: 14, spd: 1, passive: { kind: "crit", crit: 0.10, dmg: 0.08, note: "Bạo kích +10%, sát thương +8%" }, desc: "ATK +10, SPD +1." },
        rune_dagger: { id: "rune_dagger", name: "Dao Khắc Ấn", type: "weapon", rarity: "rare", price: 620, atk: 13, spd: 2, passive: { kind: "speed", evasion: 0.08, note: "Né +8% (ẩn)" }, desc: "ATK +9, SPD +2." },
        dragonblade: { id: "dragonblade", name: "Long Đao", type: "weapon", rarity: "legend", price: 2100, atk: 30, spd: 2, passive: { kind: "pierce", pierce: 0.30, dmg: 0.16, note: "Xuyên giáp 30%, sát thương +16%" }, desc: "ATK +18, SPD +2." },
        archmage_staff: { id: "archmage_staff", name: "Trượng Đại Pháp", type: "weapon", rarity: "legend", price: 2300, atk: 28, spd: 1, passive: { kind: "arcane", mpRegen: 3, pure: 0.12, note: "Hồi MP +3/turn, sát thương thuần +12%" }, desc: "ATK +17, SPD +1." },
        void_sunder: { id: "void_sunder", name: "Hư Vô Đao", type: "weapon", rarity: "legendary", price: 10000, atk: 55, spd: 3, passive: { kind: "execute", dmg: 0.28, crit: 0.15, vsEnraged: 0.35, note: "+28% dmg, +15% crit, thêm +35% vs cuồng nộ" }, desc: "ATK +28, SPD +3." },

        cloth: { id: "cloth", name: "Áo Vải", type: "armor", rarity: "common", price: 120, def: 3, desc: "DEF +3." },
        leather: { id: "leather", name: "Giáp Da", type: "armor", rarity: "common", price: 240, def: 6, desc: "DEF +6." },
        chain: { id: "chain", name: "Giáp Xích", type: "armor", rarity: "rare", price: 560, def: 14, passive: { kind: "guard", reduce: 0.10, note: "Giảm 10% sát thương nhận" }, desc: "DEF +10." },
        robe: { id: "robe", name: "Áo Choàng Pháp", type: "armor", rarity: "rare", price: 640, def: 12, mp: 4, passive: { kind: "mana", mp: 8, mpCost: 0.10, note: "MP +8 (ẩn), giảm 10% tiêu hao MP" }, desc: "DEF +8, MP +4." },
        dragon_mail: { id: "dragon_mail", name: "Long Giáp", type: "armor", rarity: "legend", price: 2100, def: 30, passive: { kind: "barrier", shield: 0.20, reduce: 0.18, note: "Khi vào battle tạo khiên 20% HP, giảm 18% dmg" }, desc: "DEF +18." },
        void_aegis: { id: "void_aegis", name: "Hư Vô Giáp", type: "armor", rarity: "legendary", price: 10000, def: 55, passive: { kind: "aegis", reduce: 0.35, reflect: 0.06, note: "Giảm 35% dmg, phản 6%" }, desc: "DEF +26." },

        crown_null: { id: "crown_null", name: "Vương Miện Tận Diệt", type: "artifact", rarity: "legendary", price: 10000, desc: "+6 tất cả stat (passive)." },

        ma_cuong_robe: {
          id: "ma_cuong_robe", name: "Áo Chỉ Ma Cương", type: "armor", rarity: "legendary", price: 0, def: 40, hp: 60,
          desc: "DEF +40, HP +60. Hiệu ứng: giảm 25% sát thương nhận vào khi mặc."
        },
        hero_will: {
          id: "hero_will", name: "Ý Chí Anh Hùng", type: "artifact", rarity: "legendary", price: 0,
          desc: "+8 tất cả stat. Hiệu ứng: mỗi trận 1 lần, nếu sắp chết sẽ sống lại 1 HP + Guard."
        },
      };
      const itemMeta = (id) => ITEM_DB[id] || null;

      const GACHA_TIERS = {
        legendary: ["void_sunder", "void_aegis", "crown_null"],
        legend: ["dragonblade", "archmage_staff", "dragon_mail"],
        rare: ["steel_sword", "rune_dagger", "chain", "robe"],
        common: ["iron_sword", "wooden_sword", "leather", "cloth", "ore", "hi_potion", "hi_ether"],
        trash: ["potion", "ether"]
      };
      function hasLuckBuff() { return (game.player.buffs?.luckTurns || 0) > 0; }

      function rollGachaTier() {
        let r = randInt(1, 1_000_000);
        // Luck Elixir: tăng cơ hội ra đồ xịn
        if (hasLuckBuff()) r = Math.floor(r * 0.55);
        if (game.player._special?.locUnlucky) r = Math.floor(r * (1 + game.player._special.locUnlucky));
        if (r <= 1_000) return "legendary";           // 0.1%
        if (r <= 11_000) return "legend";             // +1.0%
        if (r <= 41_000) return "rare";               // +3.0%
        if (r <= 200_000) return "common";            // +15.9%
        return "trash";                              // 80%
      }

      const WORLD_EVENTS = [
        {
          id: "hero_ambush", name: "Anh hùng tập kích", hint: "Một nhóm anh hùng hiểu lầm và tấn công bạn.",
          enemy: (pLv) => ({
            name: "Anh Hùng Lưu Động", tier: "boss", level: Math.max(8, pLv + 6),
            hp: 80 + pLv * 18, atk: 12 + pLv * 3, def: 8 + pLv * 2, spd: 7 + Math.floor(pLv * 0.8),
            lootGold: [120, 220], xp: 80 + pLv * 12, enraged: false
          })
        },
        {
          id: "demon_raid", name: "Ma tộc tập kích", hint: "Lũ ma tộc tràn qua khu phố. Bạn bị cuốn vào.",
          enemy: (pLv) => ({
            name: "Ma Tộc Tiên Phong", tier: "boss", level: Math.max(10, pLv + 8),
            hp: 110 + pLv * 22, atk: 14 + pLv * 3, def: 10 + pLv * 2, spd: 6 + Math.floor(pLv * 0.7),
            lootGold: [160, 280], xp: 110 + pLv * 14, enraged: false
          })
        },
        {
          id: "demon_king", name: "Đánh Ma Vương", hint: "Ma Vương xuất hiện. Không thể tránh.",
          enemy: (pLv) => ({
            name: "Ma Vương", tier: "boss", level: Math.max(20, pLv + 14),
            hp: 220 + pLv * 35, atk: 18 + pLv * 4, def: 14 + pLv * 3, spd: 7 + Math.floor(pLv * 0.8),
            lootGold: [260, 420], xp: 220 + pLv * 18, enraged: false
          })
        },
      ];
      function maybeTriggerWorldEvent() {
        if (game.gameOver || game.battle.active) return null;
        if (game.mode.kind !== "free") return null;
        const p = Math.random();
        if (p < 0.06) return WORLD_EVENTS[0];
        if (p < 0.08) return WORLD_EVENTS[1];
        if (p < 0.082) return WORLD_EVENTS[2];
        return null;
      }

      const game = {
        started: false,
        gameOver: false,
        turn: 0,
        actionInTurn: 0,
        story: { seed: "", prologue: "", goal: "", twist: "", nemesis: "" },
        player: {
          name: "Kẻ Ngoài Lề",
          age: 18,
          level: 1,
          exp: 0,
          gold: 120,
          stamina: 100,
          maxStamina: 100,
          professionId: "prof_0",
          location: "Thị trấn Mưa Đêm",
          raceId: "human",
          maxAge: 90,
          raceRerollsLeft: 3,
          learnedSkills: [],
          skillSlots: [null, null, null, null],
          passives: [],
          weaknessId: null,
          talentPoints: 0,
          talents: {},
          buffs: { luckTurns: 0 },
          base: { HP: 20, MP: 8, STR: 6, DEX: 6, INT: 6, CHA: 6, LUK: 6, DEF: 3 },
          stats: { HP: 20, MP: 8, STR: 6, DEX: 6, INT: 6, CHA: 6, LUK: 6, DEF: 3 },
          max: { HP: 20, MP: 8 },
          blessings: [],
          inv: [],
          equipped: { weaponUid: null, armorUid: null },
        },
        world: { heat: 12, npcs: [], hiddenEvents: 0, heroNpc: null, shop: { level: 0, lastRefreshTurn: -1, stock: [] } },
        mode: { kind: "free", hint: "Tự do phiêu lưu." },
        dungeon: { active: false, name: "", floor: 0, maxFloor: 0 },
        trial: { active: false, godId: "rain", floor: 0, maxFloor: 50, progress: {} },
        awaitingNext: null,
        battle: {
          active: false,
          enemy: null,
          enemyHP: 0,
          enemyMaxHP: 0,
          turn: "player",
          guard: false,
          shieldHP: 0,
          statuses: {},
          enemyStatuses: {},
          cds: {},
          log: [],
          heroWillUsed: false,
          context: null,
        },
        log: [],
      };

      const $statusLine = document.getElementById("statusLine");
      const $hud = document.getElementById("hud");
      const $story = document.getElementById("story");
      const $help = document.getElementById("help");
      const $log = document.getElementById("log");

      const $lv = document.getElementById("lv");
      const $xp = document.getElementById("xp");
      const $age = document.getElementById("age");
      const $gold = document.getElementById("gold");
      const $race = document.getElementById("race");
      const $raceBonus = document.getElementById("raceBonus");
      const $job = document.getElementById("job");
      const $jobBonus = document.getElementById("jobBonus");
      const $ultimate = document.getElementById("ultimate");
      const $ultimateDesc = document.getElementById("ultimateDesc");
      const $blessCount = document.getElementById("blessCount");
      const $shopLevel = document.getElementById("shopLevel");
      const $turn = document.getElementById("turn");
      const $ap = document.getElementById("ap");
      const $stamina = document.getElementById("stamina");
      const $staminaHint = document.getElementById("staminaHint");
      const $mode = document.getElementById("mode");
      const $modeHint = document.getElementById("modeHint");

      const $battleUI = document.getElementById("battleUI");
      const $battleBar = document.getElementById("battleBar");
      const $skills = document.getElementById("skills");
      const $fxSlash = document.getElementById("fxSlash");

      const $overlayCreate = document.getElementById("overlayCreate");
      const $btnStart = document.getElementById("btnStart");
      const $btnRerollAll = document.getElementById("btnRerollAll");
      const $btnRerollRace = document.getElementById("btnRerollRace");
      const $nameInput = document.getElementById("nameInput");
      const $tagAge = document.getElementById("tagAge");
      const $tagLocation = document.getElementById("tagLocation");
      const $tagNPC = document.getElementById("tagNPC");
      const $raceTag = document.getElementById("raceTag");
      const $racePerk = document.getElementById("racePerk");
      const $jobTag = document.getElementById("jobTag");
      const $jobPerk = document.getElementById("jobPerk");
      const $ultTag = document.getElementById("ultTag");
      const $ultPerk = document.getElementById("ultPerk");
      const $bonusTags = document.getElementById("bonusTags");

      const $stHP = document.getElementById("stHP");
      const $stMP = document.getElementById("stMP");
      const $stSTR = document.getElementById("stSTR");
      const $stDEX = document.getElementById("stDEX");
      const $stINT = document.getElementById("stINT");
      const $stCHA = document.getElementById("stCHA");
      const $stLUK = document.getElementById("stLUK");
      const $stDEF = document.getElementById("stDEF");

      const $overlayShop = document.getElementById("overlayShop");
      const $btnCloseShop = document.getElementById("btnCloseShop");
      const $btnTipShop = document.getElementById("btnTipShop");
      const $shopList = document.getElementById("shopList");
      const $shopkeeperLine = document.getElementById("shopkeeperLine");
      const $shopLevelTag = document.getElementById("shopLevelTag");
      const $shopTipCostTag = document.getElementById("shopTipCostTag");

      const $overlayForge = document.getElementById("overlayForge");
      const $btnCloseForge = document.getElementById("btnCloseForge");
      const $forgeList = document.getElementById("forgeList");
      const $forgeDetail = document.getElementById("forgeDetail");
      const $btnForgeDo = document.getElementById("btnForgeDo");
      const $btnForgeRefresh = document.getElementById("btnForgeRefresh");
      const $forgeHint = document.getElementById("forgeHint");

      const $overlayTrial = document.getElementById("overlayTrial");
      const $overlayHeroTrial = document.getElementById("overlayHeroTrial");
      const $btnCloseHeroTrial = document.getElementById("btnCloseHeroTrial");
      const $btnStartHeroTrial = document.getElementById("btnStartHeroTrial");
      const $heroTrialTags = document.getElementById("heroTrialTags");
      const $heroTrialProgress = document.getElementById("heroTrialProgress");

      const $overlayTalents = document.getElementById("overlayTalents");
      const $btnCloseTalents = document.getElementById("btnCloseTalents");
      const $talentTags = document.getElementById("talentTags");
      const $talentGrid = document.getElementById("talentGrid");

      const $overlayGamble = document.getElementById("overlayGamble");
      const $btnCloseGamble = document.getElementById("btnCloseGamble");
      const $gambleBet = document.getElementById("gambleBet");
      const $btnGambleRoll = document.getElementById("btnGambleRoll");
      const $gambleAnimText = document.getElementById("gambleAnimText");
      const $gambleResult = document.getElementById("gambleResult");

      const $btnCloseTrial = document.getElementById("btnCloseTrial");
      const $trialSelect = document.getElementById("trialSelect");
      const $trialTags = document.getElementById("trialTags");
      const $btnStartTrial = document.getElementById("btnStartTrial");
      const $trialProgress = document.getElementById("trialProgress");

      const $overlayGacha = document.getElementById("overlayGacha");
      const $btnCloseGacha = document.getElementById("btnCloseGacha");
      const $btnGacha1 = document.getElementById("btnGacha1");
      const $btnGacha10 = document.getElementById("btnGacha10");
      const $gachaStatus = document.getElementById("gachaStatus");
      const $gachaReveal = document.getElementById("gachaReveal");
      const $btnGachaOk = document.getElementById("btnGachaOk");

      const $overlayMenu = document.getElementById("overlayMenu");
      const $btnCloseMenu = document.getElementById("btnCloseMenu");
      const $menuGrid = document.getElementById("menuGrid");
      const $menuChips = document.getElementById("menuChips");
      const $menuHint = document.getElementById("menuHint");
      const $btnMenu = document.getElementById("btnMenu");

      const $overlayTalk = document.getElementById("overlayTalk");
      const $btnCloseTalk = document.getElementById("btnCloseTalk");
      const $talkInput = document.getElementById("talkInput");
      const $btnTalkSend = document.getElementById("btnTalkSend");

      const $overlaySkills = document.getElementById("overlaySkills");
      const $btnCloseSkills = document.getElementById("btnCloseSkills");
      const $skillSlotsWrap = document.getElementById("skillSlotsWrap");
      const $skillListWrap = document.getElementById("skillListWrap");

      const $overlayInv = document.getElementById("overlayInv");
      const $overlayPassives = document.getElementById("overlayPassives");
      const $overlayProfession = document.getElementById("overlayProfession");
      const $passiveListWrap = document.getElementById("passiveListWrap");
      const $weaknessWrap = document.getElementById("weaknessWrap");
      const $professionWrap = document.getElementById("professionWrap");
      const $cinematic = document.getElementById("cinematic");
      const $cinTitle = document.getElementById("cinTitle");
      const $cinSub = document.getElementById("cinSub");
      const $btnCloseInv = document.getElementById("btnCloseInv");
      const $invBody = document.getElementById("invBody");

      function addLog(html) {
        game.log.unshift({ html, t: nowTag() });
        if (game.log.length > 80) game.log.pop();
      }
      function pushStory(text) {
        const sep = $story.textContent ? "\n\n" : "";
        $story.textContent += sep + text;
        $story.scrollTop = $story.scrollHeight;
      }
      function playSlash() {
        $fxSlash.classList.remove("play");
        void $fxSlash.offsetWidth;
        $fxSlash.classList.add("play");
      }
      function shake(el) {
        el.classList.remove("shake");
        void el.offsetWidth;
        el.classList.add("shake");
      }

      function makeNPC() {
        const nameA = ["An", "Bảo", "Chi", "Dũng", "Eri", "Fang", "Gia", "Hà", "Khoa", "Linh", "My", "Nam", "Oanh", "Phúc", "Quân", "Tú", "Uyên", "Vũ"];
        const nameB = ["Lam", "Minh", "Ngọc", "Quỳnh", "Sơn", "Thảo", "Thiên", "Trúc", "Vân", "Vy", "Long", "Khang", "Tâm", "Huy", "Tuyết"];
        const name = pick(nameA) + " " + pick(nameB);
        const role = pick(NPC_ROLES);
        const traits = [...NPC_TRAITS].sort(() => Math.random() - 0.5).slice(0, randInt(2, 3));
        const stats = { empathy: randInt(0, 100), greed: randInt(0, 100), temper: randInt(0, 100), courage: randInt(0, 100), cunning: randInt(0, 100), mood: randInt(-10, 10) };
        return { id: uid(), name, role, traits, stats, location: pick(LOCATIONS), rel: randInt(-5, 5), eventStage: 0 };
      }
      function ensureNPCs() { while (game.world.npcs.length < 12) game.world.npcs.push(makeNPC()); }
      function currentNPC() {
        ensureNPCs();
        let pool = game.world.npcs.filter(n => n.location === game.player.location);
        if (pool.length) return pick(pool);
        const n = makeNPC(); n.location = game.player.location; game.world.npcs.push(n); return n;
      }
      function runHiddenSideEvents() {
        ensureNPCs();
        const count = randInt(1, 3);
        for (let i = 0; i < count; i++) {
          const n = pick(game.world.npcs);
          const k = pick(["empathy", "greed", "temper", "courage", "cunning", "mood"]);
          const delta = randInt(-3, 3);
          n.stats[k] = clamp(n.stats[k] + delta, -50, 110);
          if (Math.random() < 0.10) n.location = pick(LOCATIONS);
          game.world.hiddenEvents += 1;
        }

        // (Bên lề) Có tỉ lệ NPC nhận Phước Lành Anh Hùng
        if (!game.world.heroNpc && Math.random() < 0.015) {
          const n2 = pick(game.world.npcs);
          game.world.heroNpc = { name: n2.name };
          pushStory(`⚠️ Tin đồn: <b>${n2.name}</b> đã nhận <b>Phước Lành Anh Hùng</b>!`);
          addLog(`NPC nhận phước anh hùng: <b>${n2.name}</b>.`);
        }
      }

      const getStacks = () => game.player.inv.filter(x => x.kind === "stack");
      const getGears = () => game.player.inv.filter(x => x.kind === "gear");
      const stackQty = (id) => (getStacks().find(x => x.id === id)?.qty || 0);
      function addStack(id, qty) {
        const it = getStacks().find(x => x.id === id);
        if (it) it.qty += qty;
        else game.player.inv.push({ kind: "stack", id, qty });
      }
      function removeStack(id, qty) {
        const it = getStacks().find(x => x.id === id);
        if (!it || it.qty < qty) return false;
        it.qty -= qty;
        if (it.qty <= 0) game.player.inv = game.player.inv.filter(x => !(x.kind === "stack" && x.id === id));
        return true;
      }
      function addGear(id, enh = 0) { game.player.inv.push({ kind: "gear", uid: uid(), id, enh }); }
      function findGearByUid(gearUid) { return getGears().find(g => g.uid === gearUid) || null; }
      function hasArtifact(id) { return getStacks().some(x => x.id === id && x.qty > 0); }

      const MAX_LV = Infinity;
      function expNeeded(lv) { return Math.floor(70 + 45 * Math.pow(lv, 1.35)); }
      function passiveMult(type) {
        let mult = 1.0;
        for (const pid of game.player.passives) {
          const ps = passiveById(pid);
          if (!ps) continue;
          if (ps.type === type) mult += ps.val;
        }
        return mult;
      }
      function grantExp(amount) {
        if (amount <= 0) return;
        let total = Math.floor(amount * 4.0 * passiveMult("exp"));
        game.player.exp += total;
        addLog(`Nhận <b>+${total} EXP</b>.`);

        if (hasArtifact("hero_will")) {
          const bonus = Math.floor(total * 0.15);
          game.player.exp += bonus;
          addLog(`Ý Chí Anh Hùng: bonus <b>+${bonus} EXP</b>.`);
        }

        while (game.player.exp >= expNeeded(game.player.level)) {
          game.player.exp -= expNeeded(game.player.level);
          game.player.level += 1;
          game.player.base.HP += 6;
          game.player.base.MP += 2;
          game.player.base.STR += 1;
          game.player.base.DEX += 1;
          game.player.base.INT += 1;
          game.player.base.CHA += 1;
          game.player.base.LUK += 1;
          game.player.base.DEF += 1;
          computeStats(true);
          addLog(`<b>LEVEL UP!</b> Bạn lên Lv ${game.player.level}.`);
          pushStory(`=== LEVEL UP ===\nBạn lên Lv ${game.player.level}!\nBase stat tăng và HP/MP hồi đầy.`);
        }

        if (game.player.level >= MAX_LV) {
          game.player.exp = Math.min(game.player.exp, expNeeded(MAX_LV) - 1);
        }
      }


      // Pre-check + spend stamina for an action
      function preAction(cost = 1, label = "hành động") {
        if (!game.started || game.gameOver) return false;
        computeStats(false);
        if (game.player.stamina < cost) {
          pushStory(`\nBạn quá mệt để ${label}. (Thể lực ${game.player.stamina}/${game.player.maxStamina})\nHãy chọn <b>Rest</b> để hồi thể lực.`);
          addLog(`<b>Thiếu thể lực</b> để ${label}.`);
          renderAll();
          return false;
        }
        game.player.stamina = clamp(game.player.stamina - cost, 0, game.player.maxStamina);
        return true;
      }

      function doRest() {
        if (!game.started || game.gameOver) return;
        if (!preAction(0, "nghỉ")) return;
        computeStats(false);
        game.player.stamina = game.player.maxStamina;
        game.player.stats.HP = clamp(game.player.stats.HP + Math.floor(game.player.max.HP * 0.25), 0, game.player.max.HP);
        game.player.stats.MP = clamp(game.player.stats.MP + Math.floor(game.player.max.MP * 0.25), 0, game.player.max.MP);
        pushStory(`\nBạn nghỉ ngơi, hồi đầy <b>thể lực</b> và hồi 25% HP/MP.`);
        addLog(`<b>Rest</b>: hồi thể lực.`);
        countAction();
        renderAll();
      }

      // Manual Save/Load (localStorage)
      const SAVE_KEY = "command_rpg_save_v7";
      function saveGame() {
        try {
          const payload = JSON.stringify(game);
          localStorage.setItem(SAVE_KEY, payload);
          addLog("<b>Đã lưu</b> (Save).");
          pushStory(`\n✅ Đã lưu game.`);
        } catch (e) {
          addLog("<b>Lưu thất bại</b>.");
          pushStory(`\n❌ Lưu thất bại: ${e?.message || e}`);
        }
        renderAll();
      }
      function loadGame() {
        try {
          const raw = localStorage.getItem(SAVE_KEY);
          if (!raw) {
            pushStory(`\nKhông có save để load.`);
            addLog("Load: không có save.");
            renderAll();
            return;
          }
          const saved = JSON.parse(raw);
          for (const k of Object.keys(saved)) game[k] = saved[k];
          game.player.stamina ??= 10;
          game.player.maxStamina ??= 10;
          game.player.professionId ??= "prof_0";
          ensureNPCs();
          computeStats(false);
          pushStory(`\n✅ Đã load game.`);
          addLog("<b>Đã load</b> (Load).");
          renderAll();
        } catch (e) {
          addLog("<b>Load thất bại</b>.");
          pushStory(`\n❌ Load thất bại: ${e?.message || e}`);
          renderAll();
        }
      }


      function applyLocationTurnTick() {
        const eff = getLocationEffect(game.player.location);
        if (game.player._special) delete game.player._special.locUnlucky;
        if (eff?.onTurn) {
          eff.onTurn(game.player);
          computeStats(false);
        }
      }

      function countAction() {
        if (!game.started || game.gameOver) return;
        runHiddenSideEvents();
        game.world.heat = clamp(game.world.heat + randInt(-1, 2), 0, 100);

        game.actionInTurn += 1;
        if (game.actionInTurn >= 10) {
          game.actionInTurn = 0;
          game.turn += 1;
          game.player.age += 1;

          // Buff: Luck Elixir (2 turn)
          if (game.player.buffs && game.player.buffs.luckTurns > 0) {
            game.player.buffs.luckTurns -= 1;
            if (game.player.buffs.luckTurns <= 0) {
              game.player.buffs.luckTurns = 0;
              addLog("<b>Luck</b> đã hết hiệu lực.");
            }
          }

          applyLocationTurnTick();
          // Thuế tận thế: mỗi 6 turn thu 90% vàng
          if (game.turn % 6 === 0) {
            const tax = Math.floor(game.player.gold * 0.90);
            if (tax > 0) {
              game.player.gold -= tax;
              addLog(`<b>Thuế</b>: bạn bị thu <b>${tax} vàng</b> (90%).`);
            }
          }

          // Thành phố Đạo Tặc: 40% bị cướp 1 vật phẩm trong kho (mỗi turn)
          if (game.player.location === "Thành phố Đạo Tặc" && game.player.inv.length) {
            if (Math.random() < 0.40) {
              const idx = randInt(0, game.player.inv.length - 1);
              const it = game.player.inv.splice(idx, 1)[0];
              addLog(`<b>Đạo tặc</b> đã cướp: <b>${itemMeta(it.id)?.name || it.id}</b>!`);
              pushStory(`⚠️ Ở <b>Thành phố Đạo Tặc</b>, bạn bị cướp mất <b>${itemMeta(it.id)?.name || it.id}</b>.`);
            }
          }

          const ev = maybeTriggerWorldEvent();
          if (ev) {
            game.mode = { kind: "forcedEvent", hint: ev.name };
            pushStory(`\n=== SỰ KIỆN BẮT BUỘC ===\n${ev.name}: ${ev.hint}\nBạn buộc phải tham gia chiến đấu!`);
            addLog(`<b>Sự kiện bắt buộc</b>: ${ev.name}.`);
            startBattle(ev.enemy(game.player.level), { kind: "forced", eventName: ev.name });
            return;
          }

          if (game.player.age >= (game.player.maxAge || 100)) {
            game.gameOver = true;
            pushStory("\n\n=== GAME OVER ===\nBạn đã hết tuổi thọ và chết già.");
            addLog("<b>GAME OVER</b>: chết già.");
          }
        }
      }

      function weakness() { return game.player.weaknessId ? WEAKNESSES.find(w => w.id === game.player.weaknessId) : null; }

      function sumBlessingBonuses() {
        const out = { HP: 0, MP: 0, STR: 0, DEX: 0, INT: 0, CHA: 0, LUK: 0, DEF: 0 };
        for (const b of game.player.blessings) {
          if (b && b.bonus) {
            for (const [k, v] of Object.entries(b.bonus)) out[k] = (out[k] || 0) + v;
          } else if (b && b.stat) {
            out[b.stat] = (out[b.stat] || 0) + (b.delta || 0);
          }
        }
        return out;
      }
      function applyWeaknessBase(s) {
        const wk = weakness();
        if (!wk) return { s, mods: {} };
        const mods = { goldMult: 1, mpCostMult: 1, dmgTakenMult: 1, critMult: 1, hpRegenMult: 1 };
        for (const [k, v] of Object.entries(wk.eff)) {
          if (k === "goldMult") mods.goldMult += v;
          else if (k === "mpCostMult") mods.mpCostMult += v;
          else if (k === "dmgTakenMult") mods.dmgTakenMult += v;
          else if (k === "critMult") mods.critMult += v;
          else if (k === "hpRegenMult") mods.hpRegenMult += v;
          else s[k] = (s[k] || 0) + v;
        }
        return { s, mods };
      }

      function computeStats(healFull = false) {
        const p = game.player;
        let s = { ...p.base };

        const r = raceById(p.raceId);
        for (const [k, v] of Object.entries(r.bonus)) s[k] = (s[k] || 0) + v;

        const bsum = sumBlessingBonuses();
        for (const [k, v] of Object.entries(bsum)) s[k] = (s[k] || 0) + v;
        const prof = professionById(p.professionId);
        for (const [k, v] of Object.entries(prof.bonus || {})) s[k] = (s[k] || 0) + v;

        if (hasArtifact("crown_null")) {
          for (const k of ["STR", "DEX", "INT", "CHA", "LUK", "DEF"]) s[k] += 6;
        }
        if (hasArtifact("hero_will")) {
          for (const k of ["STR", "DEX", "INT", "CHA", "LUK", "DEF"]) s[k] += 8;
          s.HP += 8; s.MP += 8;
        }

        const wkApply = applyWeaknessBase(s);
        s = wkApply.s;

        const weapon = p.equipped.weaponUid ? findGearByUid(p.equipped.weaponUid) : null;
        const armor = p.equipped.armorUid ? findGearByUid(p.equipped.armorUid) : null;
        const wMeta = weapon ? itemMeta(weapon.id) : null;
        const aMeta = armor ? itemMeta(armor.id) : null;

        let atk = 0, def = 0, spd = 0, mpBonus = 0, hpBonus = 0;
        if (wMeta) { atk += (wMeta.atk || 0) + (weapon.enh || 0); spd += (wMeta.spd || 0); }
        if (aMeta) { def += (aMeta.def || 0) + (armor.enh || 0); mpBonus += (aMeta.mp || 0); hpBonus += (aMeta.hp || 0); }

        const maxHpMult = passiveMult("maxHP");
        const maxMpMult = passiveMult("maxMP");

        const maxHP = Math.max(10, Math.round((s.HP + hpBonus + Math.floor(s.STR * 1.2) + def) * maxHpMult));
        const maxMP = Math.max(5, Math.round((s.MP + mpBonus + Math.floor(s.INT * 0.9)) * maxMpMult));

        // Stamina (thể lực)
        const staBase = 100 + Math.floor(p.level / 2);
        const staFromDex = Math.floor((s.DEX || 0) / 5);
        p.maxStamina = clamp(staBase + staFromDex, 50, 300);
        if (p.stamina == null) p.stamina = p.maxStamina;
        p.stamina = clamp(p.stamina, 0, p.maxStamina);

        p._derived = {
          atk, def, spd,
          mods: wkApply.mods,
          dmgMult: passiveMult("dmg"),
          critBonus: (passiveMult("crit") - 1),
          pierceBonus: (passiveMult("pierce") - 1),
          goldMult: passiveMult("gold"),
          hpRegen: 0.0,
          mpRegen: 0.0,
        };

        let hpRegen = 0, mpRegen = 0;
        for (const pid of p.passives) {
          const ps = passiveById(pid);
          if (!ps) continue;
          if (ps.type === "hpRegen") hpRegen += ps.val;
          if (ps.type === "mpRegen") mpRegen += ps.val;
        }
        hpRegen *= (p._derived.mods.hpRegenMult || 1);
        p._derived.hpRegen = hpRegen;
        p._derived.mpRegen = mpRegen;

        if (healFull) {
          s.HP = maxHP;
          s.MP = maxMP;
        } else {
          s.HP = clamp(p.stats.HP, 0, maxHP);
          s.MP = clamp(p.stats.MP, 0, maxMP);
        }

        p.stats = s;
        p.max = { HP: maxHP, MP: maxMP };
        p._special = { maCuongEquipped: (armor && armor.id === "ma_cuong_robe") };
      }

      function rollStory() {
        const prologues = [
          "Bạn tỉnh dậy với một dấu ấn lạ trên tay và một ký ức bị xé nát.",
          "Bạn bị ném khỏi dòng thời gian và rơi xuống thế giới này như một lỗi hệ thống.",
          "Một giọng nói thần thánh nói rằng: 'Hãy chứng minh giá trị của ngươi'.",
          "Bạn là kẻ ngoài lề, không thuộc phe nào — nhưng mọi phe đều muốn lợi dụng bạn.",
        ];
        const goals = [
          "Tìm 'Trái Tim Ma Cương' để phá lời nguyền đang bào mòn tuổi thọ.",
          "Truy lùng Ma Vương Lv999 và cắt đứt chu kỳ tái sinh của hắn.",
          "Thu thập 3 phước lành tối thượng để mở cổng về nhà.",
          "Trở thành anh hùng mới bằng cách chiến thắng 50 tầng trial của ít nhất 1 vị thần.",
        ];
        const twists = [
          "NPC bạn tin nhất có thể sẽ phản bội vì một món hàng hiếm.",
          "Mỗi lần bạn quay gacha, thế giới nóng lên… và quái vật mạnh hơn.",
          "Một nhược điểm bẩm sinh có thể biến bạn thành con mồi đúng lúc yếu nhất.",
          "Có những sự kiện bên lề diễn ra mà bạn không thấy, và chúng thay đổi cả thành phố.",
        ];
        const nemesis = ["Hội Đạo Tặc Chợ Đêm", "Kỵ Sĩ Bóng Tối", "Sứ Giả Sa Ngã", "Thánh Đoàn Cuồng Tín", "Ma Vương Tàn Hồn"];
        game.story.seed = uid();
        game.story.prologue = pick(prologues);
        game.story.goal = pick(goals);
        game.story.twist = pick(twists);
        game.story.nemesis = pick(nemesis);
      }

      function shopTipCost(level) { return 80 + Math.floor(120 * Math.pow(level + 1, 1.4)); }
      function refreshShopStock(force = false) {
        const shop = game.world.shop;
        if (!force && shop.lastRefreshTurn === game.turn) return;
        shop.lastRefreshTurn = game.turn;

        const baseStock = ["potion", "ether", "ore", "hi_potion", "hi_ether", "lifepotion"];
        const commons = ["wooden_sword", "iron_sword", "cloth", "leather"];
        const rares = ["steel_sword", "rune_dagger", "chain", "robe"];
        const legends = ["dragonblade", "archmage_staff", "dragon_mail"];
        const legendaries = ["void_sunder", "void_aegis", "crown_null"];

        const lvl = shop.level;
        let picks = [];
        if (lvl >= 1) picks = picks.concat(commons);
        if (lvl >= 2) picks = picks.concat(rares);
        if (lvl >= 3) picks = picks.concat(legends);
        if (lvl >= 4) picks = picks.concat(legendaries);

        const gearSet = new Set();
        const nGear = Math.min(6, 2 + lvl);
        for (let i = 0; i < nGear; i++) {
          if (picks.length === 0) break;
          gearSet.add(pick(picks));
        }

        shop.stock = [];
        for (const id of baseStock) {
          const meta = itemMeta(id);
          shop.stock.push({ kind: "stack", id, price: clamp(Math.floor(meta.price * 0.75), 1, 10000) });
        }
        for (const id of Array.from(gearSet)) {
          const meta = itemMeta(id);
          shop.stock.push({ kind: "gear", id, price: clamp(Math.floor(meta.price * 0.80), 1, 10000) });
        }

        if (game.player.level >= 6) {
          // Sách kỹ năng (Lv6+)
          shop.stock.push({ kind: "stack", id: "skill_book", price: clamp(itemMeta("skill_book").price, 1, 10000) });
          const activePool = ACTIVE_SKILLS.filter(s => s.kind === "active");
          const a1 = pick(activePool);
          shop.stock.push({ kind: "skill", id: a1.id, price: clamp(260 + lvl * 70, 1, 10000) });
        }
        if (game.player.level >= 10) {
          const activePool = ACTIVE_SKILLS.filter(s => s.kind === "active");
          const a2 = pick(activePool);
          shop.stock.push({ kind: "skill", id: a2.id, price: clamp(320 + lvl * 90, 1, 10000) });
          const p1 = pick(PASSIVES);
          shop.stock.push({ kind: "passive", id: p1.id, price: clamp(360 + lvl * 95, 1, 10000) });
        }

        const skLines = [
          "“Muốn gì cũng có… miễn là có tiền.”",
          "“Có tip thì tôi mới mở kho sau.”",
          "“Tôi bắt đầu tin bạn là khách sộp.”",
          "“Hàng hiếm… chỉ bán cho người biết điều.”",
          "“Đừng hỏi nguồn. Mua đi.”",
        ];
        $shopkeeperLine.textContent = skLines[Math.min(skLines.length - 1, shop.level)];
      }

      function openShop() { refreshShopStock(false); renderShop(); $overlayShop.style.display = "flex"; }
      function renderShop() {
        const shop = game.world.shop;
        $shopLevelTag.textContent = `Shop level: ${shop.level}`;
        $shopTipCostTag.textContent = `Tip cost: ${shopTipCost(shop.level)} vàng`;
        $shopList.innerHTML = "";
        for (const entry of shop.stock) {
          let name = "", desc = "", rar = "common";
          if (entry.kind === "stack" || entry.kind === "gear") {
            const meta = itemMeta(entry.id); if (!meta) continue;
            name = meta.name; desc = meta.desc || "—"; rar = meta.rarity || "common";
          } else if (entry.kind === "skill") {
            const s = skillById(entry.id); if (!s) continue;
            name = `Kỹ năng: ${s.name}`; desc = s.desc; rar = s.rarity || "common";
          } else if (entry.kind === "passive") {
            const ps = passiveById(entry.id); if (!ps) continue;
            name = `Bị động: ${ps.name}`; desc = ps.desc; rar = ps.rarity || "common";
          }
          const div = document.createElement("div");
          div.className = "listItem";
          div.innerHTML = `
        <div class="left">
          <div class="name">${name} <span class="rar ${rar}">${rarityLabel(rar)}</span></div>
          <div class="desc">${desc}</div>
        </div>
        <div style="text-align:right;">
          <div style="font-weight:900;">${entry.price} vàng</div>
          <button class="btn btnPrimary" style="margin-top:8px;">Mua</button>
        </div>
      `;
          div.querySelector("button").addEventListener("click", () => buyFromShop(entry));
          $shopList.appendChild(div);
        }
      }
      function learnSkill(skillId) {
        if (!skillById(skillId)) return;
        if (game.player.learnedSkills.includes(skillId)) return;
        game.player.learnedSkills.push(skillId);
        for (let i = 0; i < 4; i++) { if (!game.player.skillSlots[i]) { game.player.skillSlots[i] = skillId; break; } }
      }
      function learnPassive(pid) {
        if (!passiveById(pid)) return;
        if (game.player.passives.includes(pid)) return;
        game.player.passives.push(pid);
      }
      function buyFromShop(entry) {
        if (!preAction(1, "mua hàng")) return;
        if (game.player.gold < entry.price) return;
        game.player.gold -= entry.price;
        // 40% shop lừa đảo (chỉ áp dụng cho vật phẩm/trang bị)
        const SCAM_SHOP = 0.40;
        if ((entry.kind === "stack" || entry.kind === "gear") && Math.random() < SCAM_SHOP) {
          addLog("⚠️ Shop lừa đảo! Bạn mất tiền nhưng không nhận được hàng.");
          pushStory("⚠️ Bạn bị shop lừa: trả tiền nhưng không nhận được món gì.");
          countAction();
          renderAll();
          renderShop();
          return;
        }

        if (entry.kind === "stack") {
          addStack(entry.id, 1);
          addLog(`Mua <b>${itemMeta(entry.id).name}</b> (-${entry.price} vàng).`);
          pushStory(`Bạn mua ${itemMeta(entry.id).name}.`);
        } else if (entry.kind === "gear") {
          addGear(entry.id, 0);
          addLog(`Mua <b>${itemMeta(entry.id).name}</b> (-${entry.price} vàng).`);
          pushStory(`Bạn mua ${itemMeta(entry.id).name} (gear).`);
        } else if (entry.kind === "skill") {
          learnSkill(entry.id);
          addLog(`Mua <b>kỹ năng</b>: ${skillById(entry.id)?.name || entry.id}.`);
          pushStory(`Bạn học kỹ năng: ${skillById(entry.id)?.name || entry.id}.`);
        } else if (entry.kind === "passive") {
          learnPassive(entry.id);
          addLog(`Mua <b>bị động</b>: ${passiveById(entry.id)?.name || entry.id}.`);
          pushStory(`Bạn nhận bị động: ${passiveById(entry.id)?.name || entry.id}.`);
        }
        countAction();
        computeStats(false);
        renderAll();
        renderShop();
      }
      function tipShop() {
        if (!preAction(1, "tip chủ quán")) return;
        const shop = game.world.shop;
        const cost = shopTipCost(shop.level);
        if (game.player.gold < cost) return;
        game.player.gold -= cost;
        shop.level = Math.min(5, shop.level + 1);
        addLog(`Tip shop <b>-${cost} vàng</b>. Shop lên level <b>${shop.level}</b>.`);
        refreshShopStock(true);
        renderShop();
        countAction();
        renderAll();
      }

      let gachaBusy = false;
      function gachaRollOnce() {
        const tier = rollGachaTier();
        const pool = GACHA_TIERS[tier] || GACHA_TIERS.trash;
        const id = pick(pool);
        const meta = itemMeta(id);
        if (meta.type === "weapon" || meta.type === "armor") addGear(id, 0);
        else addStack(id, 1);
        return { id, meta, tier };
      }
      function openGachaMulti(count) {
        if (!preAction(1, "quay gacha")) return;
        if (gachaBusy) return;
        const unit = 100;
        const cost = (count === 10) ? unit * 15 : unit;
        if (game.player.gold < cost) return;
        game.player.gold -= cost;
        countAction();
        renderAll();
        gachaBusy = true;
        $overlayGacha.style.display = "flex";
        $gachaReveal.style.display = "none";
        $btnGachaOk.style.display = "none";
        $gachaStatus.textContent = (count === 10) ? "Đang mở 10 hòm…" : "Đang mở hòm…";
        setTimeout(() => {
          const got = [];
          for (let i = 0; i < count; i++) got.push(gachaRollOnce());
          const tally = { trash: 0, common: 0, rare: 0, legend: 0, legendary: 0 };
          for (const g of got) { const rr = (g.meta.rarity || "common"); tally[rr] = (tally[rr] || 0) + 1; }
          const top = got.slice().sort((a, b) => rarityRank(b.meta.rarity) - rarityRank(a.meta.rarity))[0];
          $gachaStatus.textContent = "Kết quả:";
          $gachaReveal.style.display = "block";
          const lines = got.map(g => `<div class=\"mini\">• ${g.meta.name} <span class=\"rar ${g.meta.rarity}\">${rarityLabel(g.meta.rarity)}</span></div>`).join("");
          $gachaReveal.innerHTML = `
        <div class=\"big\">${(count === 10) ? "Gacha x10" : "Gacha x1"} — Best: ${top.meta.name} <span class=\"rar ${top.meta.rarity}\">${rarityLabel(top.meta.rarity)}</span></div>
        <div class=\"small\">Legendary:${tally.legendary || 0} • Legend:${tally.legend || 0} • Rare:${tally.rare || 0} • Common:${tally.common || 0} • Trash:${tally.trash || 0}</div>
        <div style=\"margin-top:8px; max-height:220px; overflow:auto;\">${lines}</div>
      `;
          addLog(`Gacha x${count}: nhận ${count} món. Best: <b>${top.meta.name}</b>.`);
          pushStory(`Bạn quay gacha x${count} (-${cost} vàng). Best: <b>${top.meta.name}</b>.`);
          $btnGachaOk.style.display = "inline-flex";
          gachaBusy = false;
          computeStats(false);
          renderAll();
        }, 900);
      }

      function openGacha() {
        // mở UI gacha, CHƯA quay
        $overlayGacha.style.display = "flex";
        $gachaReveal.style.display = "block";
        $btnGachaOk.style.display = "none";
        $gachaStatus.textContent = "Chọn gacha x1 hoặc x10.";
        $gachaReveal.innerHTML = `
      <div class="big">Gacha</div>
      <div class="small">Giá: x1 = 100 vàng • x10 = 1500 vàng</div>
      <div class="mini">Tip: Luck Elixir giúp tỉ lệ ra đồ xịn cao hơn.</div>
    `;
      }

      function openGachaAndRoll() { return openGacha(); }

      function _deprecated_openGachaAndRoll_old() {
        if (!preAction(1, "quay gacha")) return;
        if (gachaBusy) return;
        const cost = 100;
        if (game.player.gold < cost) return;
        game.player.gold -= cost;
        countAction();
        renderAll();
        gachaBusy = true;
        $overlayGacha.style.display = "flex";
        $gachaReveal.style.display = "none";
        $btnGachaOk.style.display = "none";
        $gachaStatus.textContent = "Đang mở hòm…";
        setTimeout(() => {
          const tier = rollGachaTier();
          const pool = GACHA_TIERS[tier] || GACHA_TIERS.trash;
          const id = pick(pool);
          const meta = itemMeta(id);
          if (meta.type === "weapon" || meta.type === "armor") addGear(id, 0);
          else addStack(id, 1);
          addLog(`Gacha ra <b>${meta.name}</b> (${rarityLabel(meta.rarity)}).`);
          pushStory(`Bạn quay gacha (-100 vàng)… Bạn nhận: ${meta.name} (${rarityLabel(meta.rarity)}).`);
          $gachaStatus.textContent = "Kết quả:";
          $gachaReveal.style.display = "block";
          $gachaReveal.innerHTML = `<div class="big">${meta.name} <span class="rar ${meta.rarity}">${rarityLabel(meta.rarity)}</span></div><div class="small">${meta.desc || "—"}</div>`;
          $btnGachaOk.style.display = "inline-flex";
          gachaBusy = false;
          computeStats(false);
          renderAll();
        }, 1100);
      }

      let forgeSelectedUid = null;
      function openForge() {
        renderForgeList();
        $forgeDetail.textContent = "Chọn một trang bị.";
        $forgeHint.textContent = "";
        $btnForgeDo.disabled = true;
        forgeSelectedUid = null;
        $overlayForge.style.display = "flex";
      }
      function renderForgeList() {
        const gears = getGears().filter(g => {
          const m = itemMeta(g.id);
          return m && (m.type === "weapon" || m.type === "armor");
        });
        $forgeList.innerHTML = "";
        if (gears.length === 0) { $forgeList.innerHTML = `<div class="mini">Bạn không có vũ khí/giáp.</div>`; return; }
        for (const g of gears) {
          const m = itemMeta(g.id);
          const enh = g.enh || 0;
          const equipped = (game.player.equipped.weaponUid === g.uid || game.player.equipped.armorUid === g.uid);
          const statLine = m.type === "weapon" ? `ATK ${m.atk || 0} (+${enh})` : `DEF ${m.def || 0} (+${enh})`;
          const div = document.createElement("div");
          div.className = "listItem";
          div.innerHTML = `
        <div class="left">
          <div class="name">${m.name} <span class="rar ${m.rarity}">${rarityLabel(m.rarity)}</span> ${equipped ? `<span class="rar common">Equipped</span>` : ""}</div>
          <div class="desc">${statLine}</div>
        </div>
        <div style="text-align:right;"><button class="btn btnPrimary">Chọn</button></div>
      `;
          div.querySelector("button").addEventListener("click", () => { forgeSelectedUid = g.uid; renderForgeDetail(); });
          $forgeList.appendChild(div);
        }
      }
      function forgeCost(targetLevel) { return { gold: 20 * targetLevel * targetLevel, ore: targetLevel }; }
      function forgeChanceText(n) { return n <= 6 ? `1 / ${Math.pow(10, n).toLocaleString()}` : `1 / 10^${n}`; }
      function renderForgeDetail() {
        if (!forgeSelectedUid) { $btnForgeDo.disabled = true; return; }
        const g = findGearByUid(forgeSelectedUid); if (!g) { $btnForgeDo.disabled = true; return; }
        const m = itemMeta(g.id);
        const cur = g.enh || 0;
        const target = cur + 1;
        const cost = forgeCost(target);
        $forgeDetail.innerHTML = `
      <div><b>${m.name}</b> hiện tại: <b>+${cur}</b></div>
      <div style="margin-top:6px;">Nâng lên: <b>+${target}</b></div>
      <div style="margin-top:10px; color: rgba(255,255,255,.62); font-size:12px; line-height:1.55;">
        Cost: <b>${cost.gold}</b> vàng + <b>${cost.ore}</b> Quặng<br>
        Chance: <b>${forgeChanceText(target)}</b>
      </div>`;
        const can = (game.player.gold >= cost.gold) && (stackQty("ore") >= cost.ore) && (target <= 100);
        $btnForgeDo.disabled = !can;
        $forgeHint.textContent = can ? "Nhấn 'Nâng cấp' để thử." : "Không đủ vàng/quặng hoặc đã +100.";
        $btnForgeDo.onclick = () => attemptForge(g.uid, target, cost.gold, cost.ore);
      }
      function attemptForge(gearUid, target, goldCost, oreCost) {
        if (!preAction(2, "rèn đồ")) return;
        const g = findGearByUid(gearUid);
        if (!g || target > 100) return;
        if (game.player.gold < goldCost || stackQty("ore") < oreCost) return;
        game.player.gold -= goldCost;
        removeStack("ore", oreCost);
        let ok = succeedTenPow(target);
        // Luck Elixir: thêm 1 lần thử nữa (tăng tỉ lệ thành công)
        if (!ok && hasLuckBuff()) ok = succeedTenPow(target);
        if (ok) { g.enh = target; addLog(`Rèn thành công: <b>${itemMeta(g.id).name} +${target}</b>.`); pushStory(`RÈN THÀNH CÔNG! ${itemMeta(g.id).name} lên +${target}.`); }
        else {
          // thất bại: xóa item
          const idx = game.player.inv.findIndex(x => x.uid === g.uid);
          if (idx >= 0) game.player.inv.splice(idx, 1);
          if (game.player.equipped.weaponUid === g.uid) game.player.equipped.weaponUid = null;
          if (game.player.equipped.armorUid === g.uid) game.player.equipped.armorUid = null;
          addLog(`Rèn thất bại: <b>${itemMeta(g.id).name}</b> đã vỡ và biến mất!`);
          pushStory(`Rèn thất bại… <b>${itemMeta(g.id).name}</b> bị phá hủy!`);
        }
        countAction(); computeStats(false); renderAll(); renderForgeList(); renderForgeDetail();
      }

      function fillTrialSelect() { $trialSelect.innerHTML = GODS.map(g => `<option value="${g.id}">${g.name} — ${g.desc}</option>`).join(""); }
      function openTrial() { fillTrialSelect(); $trialSelect.value = game.trial.godId; renderTrial(); $overlayTrial.style.display = "flex"; }
      function renderTrial() {
        const g = godById($trialSelect.value);
        const best = game.trial.progress[g.id] || 0;
        $trialTags.innerHTML = `<span class="tag">Bạn đã vượt: ${best}/50</span><span class="tag">Nhận phước mỗi 10 tầng</span>`;
        $trialProgress.textContent = `Tiến trình ${g.name}: ${best}/50.`;
      }

      // ===== Hero Trial (Trial Anh Hùng) =====
      function openHeroTrial() { renderHeroTrial(); $overlayHeroTrial.style.display = "flex"; }
      function renderHeroTrial() {
        const best = game.heroTrial?.best || 0;
        $heroTrialTags.innerHTML = `<span class="tag">Bạn đã vượt: ${best}/100</span><span class="tag">Quái Lv99</span><span class="tag">Thưởng: Phước Lành Anh Hùng + Thánh Kiếm/Thánh Giáp</span>`;
        $heroTrialProgress.textContent = `Tiến trình Trial Anh Hùng: ${best}/100.`;
      }
      function makeHeroTrialEnemy(floor) {
        const scale = 1 + floor * 0.08;
        return {
          name: `Kẻ Canh Tầng ${floor}`, tier: "trialHero", level: 99,
          hp: Math.floor(2800 * scale), atk: Math.floor(140 * scale), def: Math.floor(95 * scale), spd: Math.floor(45 * scale),
          lootGold: [250, 520], xp: Math.floor(900 * scale), enraged: true, justEnraged: false
        };
      }
      function startHeroTrial() {
        normalizeMode();
        if (!preAction(2, "trial anh hùng")) return;
        if (!game.heroTrial) game.heroTrial = { floor: 1, best: 0 };
        game.mode = { kind: "heroTrial" };
        pushStory(`=== TRIAL ANH HÙNG ===\nBạn bước vào thử thách 100 tầng. Mỗi tầng quái Lv99.`);
        addLog("<b>Trial Anh Hùng</b> bắt đầu.");
        countAction();
        startBattle(makeHeroTrialEnemy(game.heroTrial.floor), { kind: "heroTrial" });
      }


      function makeTrialEnemy(floor) {
        const pLv = game.player.level;
        const baseLv = Math.max(5, pLv + Math.floor(floor * 1.0));
        const scale = 1 + floor * 0.18 + pLv * 0.04;
        return { name: `Thử Thách Tầng ${floor}`, tier: "trial", level: baseLv, hp: Math.round(54 * scale + floor * 5), atk: Math.round(14 * scale + floor * 1.2), def: Math.round(8 * scale + floor * 0.9), spd: Math.round(7 * scale + floor * 0.5), lootGold: [0, 0], xp: Math.round(55 + floor * 12), enraged: false, justEnraged: false };
      }
      function startOrResumeTrial(godId) {
        if (!preAction(4, "trial")) return;
        if (game.battle.active) return;
        if (game.mode.kind !== "free") return;
        game.trial.godId = godId;
        const best = game.trial.progress[godId] || 0;
        const nextFloor = best + 1;
        if (nextFloor > 50) return;
        game.trial.active = true;
        game.trial.floor = nextFloor;
        game.mode = { kind: "trial", hint: `Trial ${godById(godId).name} tầng ${game.trial.floor}/50` };
        pushStory(`Bạn bước vào Trial của ${godById(godId).name}. Tầng ${game.trial.floor}/50.`);
        addLog(`Bắt đầu Trial: ${godById(godId).name} tầng ${game.trial.floor}.`);
        countAction();
        startBattle(makeTrialEnemy(game.trial.floor), { kind: "trial", godId, floor: game.trial.floor });
      }

      function envoyEnemy() {
        const pLv = game.player.level;
        const lv = Math.max(70, pLv + 50);
        const scale = 1 + pLv * 0.03;
        return { name: "Sứ Giả của Chúa", tier: "envoy", level: lv, hp: Math.round(520 * scale), atk: Math.round(54 * scale), def: Math.round(34 * scale), spd: Math.round(16 * scale), lootGold: [180, 320], xp: Math.round(360 + pLv * 35), enraged: false, justEnraged: false, dropBlessing: true };
      }
      function spawnEnemy(kind = "normal", floor = 1) {
        if (kind === "dungeon" && Math.random() < 0.20) return envoyEnemy();
        const baseMonsters = [
          { name: "Slime", baseLv: 1, hp: 32, atk: 8, def: 2, spd: 3, lootGold: [18, 28], xp: 28 },
          { name: "Sói Rừng", baseLv: 2, hp: 48, atk: 12, def: 3, spd: 6, lootGold: [22, 34], xp: 36 },
          { name: "Bóng Đêm", baseLv: 3, hp: 44, atk: 14, def: 2, spd: 7, lootGold: [24, 38], xp: 40 },
          { name: "Giáp Sắt", baseLv: 3, hp: 68, atk: 11, def: 9, spd: 3, lootGold: [28, 44], xp: 44 },
          { name: "Đạo Tặc", baseLv: 4, hp: 56, atk: 16, def: 4, spd: 7, lootGold: [30, 48], xp: 48 },
        ];
        const b = pick(baseMonsters);
        const pLv = game.player.level;
        const baseLv = Math.max(1, b.baseLv + Math.floor(pLv * 0.95) + (kind === "dungeon" ? floor : 0));
        const scale = 1 + pLv * 0.12 + (kind === "dungeon" ? floor * 0.26 : 0.0) + 0.10;
        return { name: b.name, tier: kind, level: baseLv, hp: Math.round(b.hp * scale), atk: Math.round(b.atk * scale), def: Math.round(b.def * scale), spd: Math.round(b.spd * scale), lootGold: b.lootGold, xp: Math.round(b.xp * (1 + pLv * 0.10) + (kind === "dungeon" ? floor * 16 : 0)), enraged: false, justEnraged: false };
      }

      function startDungeon() {
        normalizeMode();
        if (!preAction(4, "vào dungeon")) return;
        if (game.battle.active) return;
        if (game.mode.kind !== "free") return;
        const names = ["Hầm Mộ Sương", "Hang Đá Xám", "Tháp Mưa Đêm", "Hầm Ngầm Cảng Gió", "Đền Tàn Tích"];
        game.dungeon.active = true;
        game.dungeon.name = pick(names);
        game.dungeon.floor = 1;
        game.dungeon.maxFloor = randInt(4, 7);
        game.mode = { kind: "dungeon", hint: `Dungeon ${game.dungeon.name} (${game.dungeon.floor}/${game.dungeon.maxFloor})` };
        pushStory(`Bạn bước vào <b>${game.dungeon.name}</b>. Dungeon có ${game.dungeon.maxFloor} tầng.`);
        addLog(`Vào dungeon <b>${game.dungeon.name}</b>.`);
        countAction();
        startBattle(spawnEnemy("dungeon", game.dungeon.floor), { kind: "dungeon", floor: game.dungeon.floor });
      }

      function specialEncounterEnemy() {
        const roll = Math.random();
        if (roll < 0.050) {
          return { name: "Anh Hùng (Lv999)", tier: "boss999", level: 999, hp: 140000, atk: 2800, def: 1800, spd: 120, lootGold: [9000, 16000], xp: 160000, enraged: false, justEnraged: false, dropBossRewards: true };
        }
        if (roll < 0.100) {
          return { name: "Ma Vương (Lv999)", tier: "boss999", level: 999, hp: 230000, atk: 3600, def: 2100, spd: 110, lootGold: [12000, 22000], xp: 220000, enraged: false, justEnraged: false, dropBossRewards: true };
        }
        return null;
      }

      function openSkills() { renderSkillManager(); $overlaySkills.style.display = "flex"; }
      function renderSkillManager() {
        const learned = game.player.learnedSkills.map(id => skillById(id)).filter(Boolean);
        for (let i = 0; i < 4; i++) { if (game.player.skillSlots[i] && !game.player.learnedSkills.includes(game.player.skillSlots[i])) game.player.skillSlots[i] = null; }
        const optsHtml = (selectedId) => {
          const list = learned.slice().sort((a, b) => {
            const ra = RARITY.indexOf(a.rarity || "common");
            const rb = RARITY.indexOf(b.rarity || "common");
            return rb - ra || a.name.localeCompare(b.name);
          });
          const options = [`<option value="">(trống)</option>`].concat(list.map(s => {
            const sel = (s.id === selectedId) ? "selected" : "";
            return `<option ${sel} value="${s.id}">${s.name} • ${rarityLabel(s.rarity)} • MP ${s.mp || 0}</option>`;
          }));
          return options.join("");
        };
        $skillSlotsWrap.innerHTML = "";
        for (let i = 0; i < 4; i++) {
          const row = document.createElement("div");
          row.className = "listItem";
          row.innerHTML = `
        <div class="left">
          <div class="name">Ô skill ${i + 1}</div>
          <div class="desc">Chọn 1 kỹ năng cho slot.</div>
        </div>
        <div style="min-width: 220px;">
          <select style="width:100%; padding:10px 12px; border-radius: 12px; border:1px solid rgba(255,255,255,.14); background: rgba(0,0,0,.22); color: rgba(255,255,255,.92);" data-slot="${i}">
            ${optsHtml(game.player.skillSlots[i])}
          </select>
        </div>`;
          row.querySelector("select").addEventListener("change", (e) => {
            const slot = parseInt(e.target.getAttribute("data-slot"), 10);
            const val = e.target.value || null;
            game.player.skillSlots[slot] = val;
            if (val) {
              for (let j = 0; j < 4; j++) if (j !== slot && game.player.skillSlots[j] === val) game.player.skillSlots[j] = null;
              renderSkillManager();
            }
            renderAll();
          });
          $skillSlotsWrap.appendChild(row);
        }
        const lines = learned.slice().sort((a, b) => {
          const ra = RARITY.indexOf(a.rarity || "common");
          const rb = RARITY.indexOf(b.rarity || "common");
          return rb - ra || a.name.localeCompare(b.name);
        }).map(s => {
          const isInSlot = game.player.skillSlots.includes(s.id);
          return `<div class="listItem"><div class="left"><div class="name">${s.name} <span class="rar ${s.rarity}">${rarityLabel(s.rarity)}</span> ${isInSlot ? `<span class="rar common">In slot</span>` : ""}</div><div class="desc">${s.desc} • MP ${s.mp || 0} • CD ${s.cd || 0} • Scale ${s.scale || "-"}</div></div></div>`;
        }).join("");
        $skillListWrap.innerHTML = lines || `<div class="mini">Bạn chưa có skill nào.</div>`;
      }

      function dmgFormula(att, def, pierce = 0.0, pure = false) {
        if (pure) return Math.max(1, Math.round(att + randInt(-2, 3)));
        const effDef = Math.max(0, Math.round(def * (1 - pierce)));
        const raw = att - Math.floor(effDef * 0.70);
        return Math.max(1, raw + randInt(-2, 3));
      }
      function applyRegenEndTurn() {
        const p = game.player;
        const hpRegenPct = p._derived?.hpRegen || 0;
        const mpRegenPct = p._derived?.mpRegen || 0;
        if (hpRegenPct > 0) {
          const heal = Math.max(1, Math.floor(p.max.HP * hpRegenPct));
          p.stats.HP = clamp(p.stats.HP + heal, 0, p.max.HP);
          game.battle.log.push(`Bị động hồi <b>+${heal} HP</b>.`);
        }
        if (mpRegenPct > 0) {
          const gain = Math.max(1, Math.floor(p.max.MP * mpRegenPct));
          p.stats.MP = clamp(p.stats.MP + gain, 0, p.max.MP);
          game.battle.log.push(`Bị động hồi <b>+${gain} MP</b>.`);
        }
      }
      function tickEnemyDots() {
        const es = game.battle.enemyStatuses;
        if (es.poison && es.poison.turns > 0) {
          const dmg = Math.max(1, Math.floor(game.battle.enemyMaxHP * es.poison.pct));
          game.battle.enemyHP = Math.max(0, game.battle.enemyHP - dmg);
          game.battle.log.push(`Độc gây <b>${dmg}</b> sát thương.`);
          es.poison.turns -= 1;
          if (es.poison.turns <= 0) delete es.poison;
        }
      }
      function decBuffs() {
        const ps = game.battle.statuses;
        const es = game.battle.enemyStatuses;
        for (const key of Object.keys(ps)) {
          if (ps[key]?.turns != null) { ps[key].turns -= 1; if (ps[key].turns <= 0) delete ps[key]; }
        }
        for (const key of Object.keys(es)) {
          if (es[key]?.turns != null) { es[key].turns -= 1; if (es[key].turns <= 0) delete es[key]; }
        }
      }

      function startBattle(enemy, context) {
        computeStats(false);
        if (enemy && (enemy.level >= 999 || /Ma Vương|Anh Hùng/.test(enemy.name))) {
          showCinematic("BATTLE", `${enemy.name} • Lv ${enemy.level}`);
        }
        game.battle.active = true;
        game.battle.enemy = enemy;
        game.battle.enemyHP = enemy.hp;
        game.battle.enemyMaxHP = enemy.hp;
        game.battle.turn = "player";
        game.battle.guard = false;
        game.battle.shieldHP = 0;
        const startShield = game.player._special?.gearStartShield || 0;
        if (startShield > 0) {
          game.battle.shieldHP = Math.floor(game.player.max.HP * startShield);
          if (game.battle.shieldHP > 0) addBattleLog(`🛡️ Khiên khởi đầu: +${game.battle.shieldHP}`);
        }
        game.battle.statuses = {};
        game.battle.enemyStatuses = {};
        game.battle.cds = {};
        game.battle.log = [`Bạn chạm trán <b>${enemy.name}</b> (Lv ${enemy.level}).`];
        game.battle.heroWillUsed = false;
        game.battle.context = context || { kind: "normal" };

        const pSpd = game.player.stats.DEX + (game.player._derived?.spd || 0) + randInt(1, 6);
        const eSpd = enemy.spd + randInt(1, 6);
        game.battle.turn = (pSpd >= eSpd) ? "player" : "enemy";

        addLog(`Battle: <b>${enemy.name}</b> (Lv ${enemy.level}).`);
        renderAll();
        if (game.battle.turn === "enemy") setTimeout(() => enemyTurn(), 420);
      }

      function awardBossRewards() {
        const alreadyGear = getGears().some(g => g.id === "ma_cuong_robe");
        if (!alreadyGear) addGear("ma_cuong_robe", 0);
        if (!hasArtifact("hero_will")) addStack("hero_will", 1);
        pushStory("=== BOSS REWARD ===\nBạn nhận được: Áo Chỉ Ma Cương + Ý Chí Anh Hùng!");
        addLog("<b>Boss reward</b>: Áo Chỉ Ma Cương + Ý Chí Anh Hùng.");
      }

      function endBattle(victory) {
        const ctx = game.battle.context || { kind: "normal" };
        const enemy = game.battle.enemy;
        game.battle.active = false;
        game.battle.enemy = null;
        game.battle.context = null;
        $battleUI.style.display = "none";

        if (victory) {
          grantExp(Math.floor((enemy.xp || Math.max(10, enemy.level * 10)) * 1.6 * (game._forcedRewardMult || 1)));
          if (enemy.lootGold && enemy.lootGold[1] > 0) {
            const gold = Math.floor(randInt(enemy.lootGold[0], enemy.lootGold[1]) * 3.0);
            game.player.gold += gold;
            addLog(`Nhặt <b>+${gold} vàng</b>.`);
          }
          if (enemy.dropBossRewards) awardBossRewards();
          if (enemy.dropBlessing) {
            const b = randomBlessing();
            game.player.blessings.push(b);
            pushStory(`Sứ giả rơi phước: <b>${b.name}</b> (${b.desc}).`);
            addLog(`Drop phước: <b>${b.name}</b>.`);
          }
          if (ctx.kind === "trial") {
            if (ctx.floor >= 20 && Math.random() < 0.18) {
              addStack("luck_elixir", 1);
              pushStory("🍀 Bạn nhận <b>Luck Elixir</b> từ Trial! (dùng để tăng luck 2 turn)");
              addLog("Nhận <b>Luck Elixir</b> từ Trial.");
            }
            game.trial.progress[ctx.godId] = Math.max(game.trial.progress[ctx.godId] || 0, ctx.floor);
            if (ctx.floor % 10 === 0) {
              const b = randomBlessing();
              game.player.blessings.push(b);
              pushStory(`Bạn vượt Trial tầng ${ctx.floor}. Nhận phước: <b>${b.name}</b> (${b.desc}).`);
              addLog(`Trial phước: <b>${b.name}</b>.`);
            } else {
              pushStory(`Bạn vượt Trial tầng ${ctx.floor}. (Phước nhận ở tầng 10/20/30/40/50)`);
            }
            if (ctx.floor >= 50) {
              pushStory(`Bạn đã hoàn thành 50 tầng Trial của ${godById(ctx.godId).name}!`);
              addLog(`Hoàn thành Trial: ${godById(ctx.godId).name}.`);
              game.mode = { kind: "free", hint: "Tự do phiêu lưu." };
              game.trial.active = false;
              game.awaitingNext = null;
            } else {
              game.awaitingNext = { kind: "trial", godId: ctx.godId, nextFloor: ctx.floor + 1 };
              game.mode = { kind: "trial", hint: `Trial ${godById(ctx.godId).name} chờ next` };
            }
          } else if (ctx.kind === "heroTrial") {
            game.heroTrial.best = Math.max(game.heroTrial.best || 0, ctx.floor);
            if (ctx.floor >= 100) {
              // thưởng lớn
              if (!game.player.blessings.some(b => b.id === "hero_blessing")) {
                game.player.blessings.push(HERO_BLESSING);
              }
              // set hiệu lực lv 999
              game.player.level = Math.max(game.player.level, 999);
              // trao đồ
              addItem("holy_sword", 1);
              addItem("holy_armor", 1);
              pushStory("🏆 Bạn chinh phục <b>Trial Anh Hùng</b> 100 tầng! Nhận <b>Phước Lành Anh Hùng</b>, <b>Thánh Kiếm</b> và <b>Thánh Giáp</b>.");
              addLog("<b>Trial Anh Hùng</b>: hoàn thành 100 tầng!");
              game.mode = { kind: "free", hint: "Tự do phiêu lưu." };
              game.awaitingNext = null;
            } else {
              game.awaitingNext = { kind: "heroTrial", nextFloor: ctx.floor + 1 };
              game.mode = { kind: "heroTrial", hint: `Trial Anh Hùng chờ next` };
              pushStory(`Bạn vượt Trial Anh Hùng tầng ${ctx.floor}.`);
            }
          } else if (ctx.kind === "dungeon") {
            // Safety: nếu ctx.floor bị thiếu/khác thường thì dùng game.dungeon.floor hiện tại
            const floor = (typeof ctx.floor === "number" && !Number.isNaN(ctx.floor)) ? ctx.floor : (game.dungeon.floor || 1);
            const maxF = (typeof game.dungeon.maxFloor === "number" && game.dungeon.maxFloor > 0) ? game.dungeon.maxFloor : floor;
            game.dungeon.floor = floor;
            game.dungeon.maxFloor = maxF;

            if (floor >= maxF) {
              pushStory(`Bạn hoàn thành dungeon <b>${game.dungeon.name}</b>!`);
              addLog(`Hoàn thành dungeon <b>${game.dungeon.name}</b>.`);
              game.mode = { kind: "free", hint: "Tự do phiêu lưu." };
              game.dungeon.active = false;
              game.dungeon.floor = 0;
              game.dungeon.maxFloor = 0;
              game.dungeon.name = "";
              game.awaitingNext = null;
            } else {
              game.awaitingNext = { kind: "dungeon", nextFloor: floor + 1 };
              game.mode = { kind: "dungeon", hint: `Dungeon ${game.dungeon.name} chờ next` };
            }
          } else if (ctx.kind === "forced") {
            // forced events are stronger -> reward boost
            game._forcedRewardMult = 2.2;
            enemy._forcedMult = 1.6;
            game.mode = { kind: "free", hint: "Tự do phiêu lưu." };
          }
          computeStats(false);
          renderAll();
          return;
        }


        const lost = Math.floor(game.player.gold * 0.10);
        game.player.gold = Math.max(0, game.player.gold - lost);

        // Nếu thua trong dungeon/trial thì thoát ra để tránh "kẹt trạng thái" không vào battle được
        if (ctx.kind === "dungeon") {
          game.dungeon.active = false;
          game.dungeon.floor = 0;
          game.dungeon.maxFloor = 0;
          game.dungeon.name = "";
          game.awaitingNext = null;
          game.mode = { kind: "free", hint: "Tự do phiêu lưu." };
        }
        if (ctx.kind === "trial") {
          if (ctx.floor >= 20 && Math.random() < 0.18) {
            addStack("luck_elixir", 1);
            pushStory("🍀 Bạn nhận <b>Luck Elixir</b> từ Trial! (dùng để tăng luck 2 turn)");
            addLog("Nhận <b>Luck Elixir</b> từ Trial.");
          }
          game.trial.active = false;
          game.awaitingNext = null;
          game.mode = { kind: "free", hint: "Tự do phiêu lưu." };
        }
        if (ctx.kind === "forced") {
          game.mode = { kind: "free", hint: "Tự do phiêu lưu." };
        }

        // Hồi lại một phần để tiếp tục chơi
        computeStats(false);
        game.player.stats.HP = Math.max(1, Math.floor(game.player.max.HP * 0.25));
        game.player.stats.MP = Math.max(0, Math.floor(game.player.max.MP * 0.25));
        computeStats(false);
        renderAll();
      }


      function tryEnrageInsteadOfDeath() {
        const enemy = game.battle.enemy;
        if (!enemy || enemy.enraged) return false;

        if (enemy.tier === "boss999") {
          enemy.enraged = true;
          enemy.justEnraged = true;
          enemy.name = "CUỒNG NỘ " + enemy.name;
          enemy.atk = Math.max(1, enemy.atk * 10);
          enemy.def = Math.max(1, enemy.def * 10);
          enemy.spd = Math.max(1, enemy.spd * 10);
          enemy.hp = Math.max(1, enemy.hp * 10);
          game.battle.enemyMaxHP = enemy.hp;
          game.battle.enemyHP = enemy.hp;
          game.battle.log.push(`<b>${enemy.name}</b> gầm lên… <b>CUỒNG NỘ</b>! (Boss 999 luôn kích hoạt)`);
          addLog("Boss 999 kích hoạt <b>CUỒNG NỘ</b>.");
          return true;
        }

        if (["boss", "envoy"].includes(enemy.tier)) return false;
        if (Math.random() >= 0.10) return false;

        enemy.enraged = true;
        enemy.justEnraged = true;
        enemy.name = "CUỒNG NỘ " + enemy.name;
        enemy.atk = Math.max(1, enemy.atk * 10);
        enemy.def = Math.max(1, enemy.def * 10);
        enemy.spd = Math.max(1, enemy.spd * 10);
        enemy.hp = Math.max(1, enemy.hp * 10);
        enemy.level = (Math.min(999, enemy.level + 30)) + 30;
        game.battle.enemyMaxHP = enemy.hp;
        game.battle.enemyHP = enemy.hp;
        game.battle.log.push(`<b>${enemy.name}</b> không chết… nó vào trạng thái <b>CUỒNG NỘ</b>! HP hồi đầy + chỉ số x10!`);
        addLog("Quái vào trạng thái <b>CUỒNG NỘ</b> (x10).");
        return true;
      }

      function applyEnemyDefDown(def) {
        const es = game.battle.enemyStatuses;
        if (es.defDown && es.defDown.turns > 0) return Math.max(0, Math.round(def * (1 - es.defDown.pct)));
        return def;
      }
      function applyPlayerBuffs() {
        const ps = game.battle.statuses;
        const out = { STR: 1, DEX: 1, INT: 1 };
        for (const k of ["STR", "DEX", "INT"]) {
          if (ps["buff_" + k] && ps["buff_" + k].turns > 0) out[k] += ps["buff_" + k].pct;
        }
        return out;
      }
      function applySkillMpCost(skill) {
        const base = skill.mp || 0;
        const mult = (game.player._derived?.mods?.mpCostMult || 1);
        return Math.max(0, Math.ceil(base * mult));
      }

      function castSkill(skillId) {
        if (!game.battle.active) return;
        if (game.battle.turn !== "player") return;

        const p = game.player;
        const e = game.battle.enemy;
        const skill = skillById(skillId);
        if (!skill) return;

        const cdLeft = game.battle.cds[skillId] || 0;
        if (cdLeft > 0) { game.battle.log.push("Skill đang cooldown."); renderAll(); return; }

        computeStats(false);
        const mpCost = applySkillMpCost(skill);
        if (p.stats.MP < mpCost) { game.battle.log.push("Không đủ MP."); renderAll(); return; }
        p.stats.MP -= mpCost;
        if ((skill.cd || 0) > 0) game.battle.cds[skillId] = skill.cd;

        playSlash(); shake($battleBar);

        const buffs = applyPlayerBuffs();
        const dmgMult = (p._derived?.dmgMult || 1);

        if (skill.type === "heal") {
          const heal = skill.extra?.healFull ? (p.max.HP) : Math.max(1, Math.floor(p.max.HP * (skill.extra?.healPct || 0.20)));
          p.stats.HP = clamp(p.stats.HP + heal, 0, p.max.HP);
          game.battle.log.push(`Bạn dùng <b>${skill.name}</b> (+${heal} HP).`);
        } else if (skill.type === "shield") {
          const pct = (skill.extra?.shieldPct || 0.20);
          const turns = (skill.extra?.shieldTurns || 2);
          const shield = Math.max(1, Math.floor(p.max.HP * pct));
          game.battle.shieldHP = Math.max(game.battle.shieldHP, shield);
          game.battle.statuses.shield = { turns };
          game.battle.log.push(`Bạn dựng <b>${skill.name}</b> (Shield ${shield} / ${turns} lượt).`);
          if (skill.extra?.cleanse) { game.battle.statuses = {}; game.battle.log.push("Hiệu ứng xấu được gột rửa."); }
        } else if (skill.type === "buff") {
          game.battle.log.push(`Bạn dùng <b>${skill.name}</b>.`);
          if (skill.extra?.extraTurn) game.battle.statuses.extraTurn = { turns: 1 };
          if (skill.extra?.mpFull) { p.stats.MP = p.max.MP; game.battle.log.push("MP hồi đầy."); }
          if (skill.extra?.guard) { game.battle.guard = true; game.battle.log.push("Nhận Guard (giảm mạnh sát thương 1 đòn)."); }
          const stat = skill.extra?.buffStat || "STR";
          const pct = skill.extra?.buffPct || 0.20;
          const turns = skill.extra?.buffTurns || 2;
          game.battle.statuses["buff_" + stat] = { pct, turns };
          game.battle.log.push(`Tăng ${stat} ${Math.round(pct * 100)}% (${turns} lượt).`);
        } else if (skill.type === "debuff") {
          const pierce = (skill.extra?.pierce || 0) + (p._derived?.pierceBonus || 0);
          const critP = (skill.extra?.crit || 0) + (p._derived?.critBonus || 0);
          const pure = !!skill.extra?.pure;

          const scaleStat = skill.scale || "STR";
          const scale = Math.round((p.stats[scaleStat] || p.stats.STR) * (buffs[scaleStat] || 1));
          const att = Math.round((scale + (p._derived?.atk || 0) + Math.floor(p.stats.DEX / 4)) * (skill.mult || 1) * dmgMult);

          let def = applyEnemyDefDown(e.def);
          let dmg = dmgFormula(att, def, pierce, pure);
          if (Math.random() < (critP * (p._derived?.mods?.critMult || 1))) { dmg = Math.round(dmg * 1.6); game.battle.log.push("<b>CRIT!</b>"); }
          game.battle.enemyHP = Math.max(0, game.battle.enemyHP - dmg);
          game.battle.log.push(`Bạn dùng <b>${skill.name}</b> gây <b>${dmg}</b> sát thương.`);

          const pct = skill.extra?.defDown || 0.18;
          const turns = skill.extra?.debuffTurns || 2;
          game.battle.enemyStatuses.defDown = { pct, turns };
          game.battle.log.push(`DEF quái giảm ${Math.round(pct * 100)}% (${turns} lượt).`);
        } else {
          const pierce = (skill.extra?.pierce || 0) + (p._derived?.pierceBonus || 0);
          const critP = (skill.extra?.crit || 0) + (p._derived?.critBonus || 0);
          const pure = !!skill.extra?.pure;

          const scaleStat = skill.scale || "STR";
          const scale = Math.round((p.stats[scaleStat] || p.stats.STR) * (buffs[scaleStat] || 1));
          const att = Math.round((scale + (p._derived?.atk || 0) + Math.floor(p.stats.DEX / 4)) * (skill.mult || 1) * dmgMult);

          let def = applyEnemyDefDown(e.def);
          let dmg = dmgFormula(att, def, pierce, pure);
          if (Math.random() < (critP * (p._derived?.mods?.critMult || 1))) { dmg = Math.round(dmg * 1.6); game.battle.log.push("<b>CRIT!</b>"); }
          game.battle.enemyHP = Math.max(0, game.battle.enemyHP - dmg);
          game.battle.log.push(`Bạn dùng <b>${skill.name}</b> gây <b>${dmg}</b> sát thương.`);

          if (skill.type === "drain") {
            const ls = skill.extra?.lifesteal || 0.22;
            const heal = Math.max(1, Math.floor(dmg * ls));
            p.stats.HP = clamp(p.stats.HP + heal, 0, p.max.HP);
            game.battle.log.push(`Hút <b>+${heal} HP</b>.`);
          }
          if (skill.type === "poison") {
            const pct = skill.extra?.dotPct || 0.08;
            const turns = skill.extra?.dotTurns || 2;
            game.battle.enemyStatuses.poison = { pct, turns };
            game.battle.log.push(`Gắn độc (${turns} lượt).`);
          }
          if (skill.type === "stun") {
            const chance = skill.extra?.stunChance || 0.25;
            if (Math.random() < chance) { game.battle.enemyStatuses.stunned = { turns: 1 }; game.battle.log.push("Quái bị <b>choáng</b>!"); }
          }
        }

        if (game.battle.enemyHP <= 0) {
          const enraged = tryEnrageInsteadOfDeath();
          if (enraged) {
            game.battle.turn = "enemy";
            renderAll();
            setTimeout(() => enemyTurn(), 650);
            return;
          }
          renderAll();
          endBattle(true);
          return;
        }

        game.battle.turn = "enemy";
        renderAll();
        if (game.battle.statuses.extraTurn && game.battle.statuses.extraTurn.turns > 0) {
          delete game.battle.statuses.extraTurn;
          game.battle.turn = "player";
          game.battle.log.push("Bạn có <b>thêm 1 lượt</b>!");
          renderAll();
          return;
        }
        setTimeout(() => enemyTurn(), 550);
      }

      function enemyTurn() {
        if (!game.battle.active) return;
        computeStats(false);
        const p = game.player;
        const e = game.battle.enemy;

        tickEnemyDots();
        if (game.battle.enemyHP <= 0) {
          const enraged = tryEnrageInsteadOfDeath();
          if (enraged) { game.battle.turn = "enemy"; renderAll(); setTimeout(() => enemyTurn(), 650); return; }
          renderAll(); endBattle(true); return;
        }

        if (e.justEnraged) {
          e.justEnraged = false;
          game.battle.log.push(`${e.name} đang gầm… nhưng chưa tấn công!`);
          game.battle.turn = "player";
          renderAll();
          return;
        }

        if (game.battle.enemyStatuses.stunned && game.battle.enemyStatuses.stunned.turns > 0) {
          game.battle.enemyStatuses.stunned.turns -= 1;
          game.battle.log.push(`${e.name} bị <b>choáng</b> và mất lượt!`);
          game.battle.turn = "player";
          renderAll();
          return;
        }

        for (const k of Object.keys(game.battle.cds)) {
          game.battle.cds[k] = Math.max(0, game.battle.cds[k] - 1);
          if (game.battle.cds[k] === 0) delete game.battle.cds[k];
        }
        decBuffs();

        let mult = 1.0;
        if (Math.random() < 0.15) mult = 1.25;
        const pDefTotal = (p.stats.DEF + (p._derived?.def || 0)) * (p._derived?.mods?.dmgTakenMult || 1);
        let dmg = dmgFormula(Math.round(e.atk * mult), pDefTotal, 0.0, false);
        if (p._special?.maCuongEquipped) dmg = Math.max(1, Math.floor(dmg * 0.75));

        if (game.battle.guard) {
          dmg = Math.max(1, Math.floor(dmg * 0.45));
          game.battle.guard = false;
          game.battle.log.push("Bạn <b>Guard</b>! Sát thương giảm.");
        }

        if (game.battle.statuses.shield && game.battle.shieldHP > 0) {
          const absorbed = Math.min(game.battle.shieldHP, dmg);
          game.battle.shieldHP -= absorbed;
          dmg -= absorbed;
          game.battle.log.push(`Shield hấp thụ <b>${absorbed}</b>.`);
          if (game.battle.shieldHP <= 0) { delete game.battle.statuses.shield; game.battle.log.push("Shield vỡ!"); }
        }

        if (dmg > 0) {
          p.stats.HP = Math.max(0, p.stats.HP - dmg);
          game.battle.log.push(`${e.name} tấn công: <b>${dmg}</b> sát thương.`);
          shake($battleBar);
        } else {
          game.battle.log.push(`${e.name} tấn công nhưng không xuyên qua được.`);
        }

        if (p.stats.HP <= 0 && hasArtifact("hero_will") && !game.battle.heroWillUsed) {
          game.battle.heroWillUsed = true;
          p.stats.HP = 1;
          game.battle.guard = true;
          game.battle.log.push("<b>Ý CHÍ ANH HÙNG</b> bùng lên! Bạn sống lại 1 HP và nhận Guard.");
          addLog("<b>Ý Chí Anh Hùng</b> cứu bạn khỏi cái chết.");
        }
        if (p.stats.HP <= 0) { renderAll(); endBattle(false); return; }

        applyRegenEndTurn();
        game.battle.turn = "player";
        renderAll();
      }

      function openMenu() { renderMenu(); $overlayMenu.style.display = "flex"; }
      function closeMenu() { $overlayMenu.style.display = "none"; }

      function openTalk() { $talkInput.value = ""; $overlayTalk.style.display = "flex"; setTimeout(() => $talkInput.focus(), 50); }
      function closeTalk() { $overlayTalk.style.display = "none"; }

      function openInv() { renderInv(); $overlayInv.style.display = "flex"; }

      function openPassives() {
        const p = game.player;
        $overlayPassives.style.display = "flex";
        $passiveListWrap.innerHTML = "";
        if (!p.passives.length) {
          $passiveListWrap.innerHTML = `<div class="listItem"><div><div class="t">(Không có)</div><div class="d">Bạn chưa có bị động.</div></div></div>`;
        } else {
          for (const id of p.passives) {
            const ps = passiveById(id); if (!ps) continue;
            const div = document.createElement("div");
            div.className = "listItem";
            div.innerHTML = `<div><div class="t">${ps.name} <span class="tag">${ps.rarity || "common"}</span></div><div class="d">${ps.desc}</div></div>`;
            $passiveListWrap.appendChild(div);
          }
        }
        const wk = weakness();
        $weaknessWrap.innerHTML = wk
          ? `<div class="listItem"><div><div class="t">${wk.name}</div><div class="d">${wk.desc}</div></div></div>`
          : `<div class="listItem"><div><div class="t">(Không có)</div><div class="d">Không có nhược.</div></div></div>`;
      }

      function openProfession() {
        const p = game.player;
        const prof = professionById(p.professionId);
        $overlayProfession.style.display = "flex";
        $professionWrap.innerHTML = `
      <div class="listItem">
        <div>
          <div class="t">${prof.name} <span class="tag">${prof.rarity}</span></div>
          <div class="d">${prof.perk}</div>
          <div class="d">Bonus: <b>${fmtBonus(prof.bonus || {})}</b></div>
        </div>
      </div>`;
      }

      /** ===================== Talent Trees (v9.1 fix) ===================== **/
      const TALENT_TREES = [
        {
          id: "war", name: "Chiến Tranh", desc: "Tăng STR/DEF/CRIT.",
          nodes: [
            { id: "war_1", name: "Cường Lực I", req: [], cost: 1, bonus: { STR: 2 } },
            { id: "war_2", name: "Cường Lực II", req: ["war_1"], cost: 1, bonus: { STR: 3 } },
            { id: "war_3", name: "Thiết Giáp", req: ["war_2"], cost: 1, bonus: { DEF: 2 } },
            { id: "war_4", name: "Sát Ý", req: ["war_3"], cost: 1, bonus: { LUK: 1 }, special: "crit+5" },
            { id: "war_5", name: "Huyết Chiến", req: ["war_4"], cost: 2, bonus: { HP: 8 }, special: "dmg+6" },
          ]
        },
        {
          id: "survive", name: "Sinh Tồn", desc: "Tăng HP/STA/giảm sát thương.",
          nodes: [
            { id: "sur_1", name: "Dẻo Dai I", req: [], cost: 1, bonus: { HP: 6 } },
            { id: "sur_2", name: "Dẻo Dai II", req: ["sur_1"], cost: 1, bonus: { HP: 8 } },
            { id: "sur_3", name: "Bền Bỉ", req: ["sur_2"], cost: 1, bonus: { DEF: 2 } },
            { id: "sur_4", name: "Nội Công", req: ["sur_3"], cost: 1, bonus: { MP: 4 }, special: "reduce+6" },
            { id: "sur_5", name: "Thể Lực Sắt", req: ["sur_4"], cost: 2, bonus: { DEX: 1 }, special: "sta+30" },
          ]
        },
        {
          id: "arcane", name: "Huyền Thuật", desc: "Tăng INT/MP/pure damage.",
          nodes: [
            { id: "arc_1", name: "Tinh Thông I", req: [], cost: 1, bonus: { INT: 2 } },
            { id: "arc_2", name: "Tinh Thông II", req: ["arc_1"], cost: 1, bonus: { INT: 3 } },
            { id: "arc_3", name: "Mạch Mana", req: ["arc_2"], cost: 1, bonus: { MP: 6 } },
            { id: "arc_4", name: "Quang Ấn", req: ["arc_3"], cost: 1, bonus: { CHA: 1 }, special: "pure+8" },
            { id: "arc_5", name: "Chân Lý", req: ["arc_4"], cost: 2, bonus: { LUK: 1 }, special: "mpregen" },
          ]
        },
      ];

      function talentOwned(id) { return !!game.player.talents?.[id]; }
      function canBuyTalent(node) {
        if (talentOwned(node.id)) return false;
        const pts = game.player.talentPoints || 0;
        if (pts < (node.cost || 1)) return false;
        for (const r of (node.req || [])) if (!talentOwned(r)) return false;
        return true;
      }
      function applyTalentBonuses(baseStats) {
        const t = game.player.talents || {};
        // numeric stat bonuses
        for (const tree of TALENT_TREES) {
          for (const n of tree.nodes) {
            if (!t[n.id]) continue;
            if (n.bonus) {
              for (const [k, v] of Object.entries(n.bonus)) {
                if (k === "HP") { baseStats.HP += v; }
                else if (k === "MP") { baseStats.MP += v; }
                else baseStats[k] = (baseStats[k] || 0) + v;
              }
            }
            // specials stored for combat
            if (n.special) {
              game.player._special = game.player._special || {};
              if (n.special === "crit+5") game.player._special.talentCrit = (game.player._special.talentCrit || 0) + 0.05;
              if (n.special === "dmg+6") game.player._special.talentDmg = (game.player._special.talentDmg || 0) + 0.06;
              if (n.special === "reduce+6") game.player._special.passiveReduce = (game.player._special.passiveReduce || 0) + 0.06;
              if (n.special === "sta+30") game.player._special.talentSta = (game.player._special.talentSta || 0) + 30;
              if (n.special === "pure+8") game.player._special.talentPure = (game.player._special.talentPure || 0) + 0.08;
              if (n.special === "mpregen") game.player._special.talentMpRegen = true;
            }
          }
        }
      }

      function renderTalents() {
        computeStats(false);
        $talentTags.innerHTML = "";
        const tag = (t) => { const d = document.createElement("div"); d.className = "tag"; d.innerHTML = t; return d; };
        $talentTags.appendChild(tag(`<b>Talent Points:</b> ${game.player.talentPoints || 0}`));
        $talentTags.appendChild(tag(`<b>Lv:</b> ${game.player.level}`));
        $talentTags.appendChild(tag(`<b>Race:</b> ${raceById(game.player.raceId).name}`));

        $talentGrid.innerHTML = "";
        for (const tree of TALENT_TREES) {
          const card = document.createElement("div");
          card.className = "card";
          card.innerHTML = `
        <div class="row" style="justify-content:space-between; gap:10px;">
          <div>
            <div class="title" style="font-size:14px;">${tree.name}</div>
            <div class="sub">${tree.desc}</div>
          </div>
        </div>
        <div class="choices" style="margin-top:8px; grid-template-columns:1fr 1fr; gap:8px;"></div>
      `;
          const grid = card.querySelector(".choices");
          for (const node of tree.nodes) {
            const owned = talentOwned(node.id);
            const can = canBuyTalent(node);
            const btn = document.createElement("button");
            btn.className = "btn " + (owned ? "btnPrimary" : "");
            btn.disabled = owned ? true : !can;
            const bonusTxt = node.bonus ? Object.entries(node.bonus).map(([k, v]) => `${k}+${v}`).join(", ") : "";
            const reqTxt = (node.req || []).length ? `Req: ${(node.req || []).join(", ")}` : "Req: -";
            btn.innerHTML = `<b>${node.name}</b><br><span style="color:rgba(255,255,255,.65);font-size:12px;">Cost ${node.cost || 1} • ${bonusTxt}${node.special ? ` • ${node.special}` : ""}<br>${reqTxt}</span>`;
            btn.addEventListener("click", () => {
              if (!canBuyTalent(node)) return;
              game.player.talentPoints -= (node.cost || 1);
              game.player.talents = game.player.talents || {};
              game.player.talents[node.id] = true;
              computeStats(true);
              renderTalents();
              saveAuto();
            });
            grid.appendChild(btn);
          }
          $talentGrid.appendChild(card);
        }
      }

      function openTalents() {
        $overlayTalents.classList.add("show");
        renderTalents();
      }
      $btnCloseTalents?.addEventListener("click", () => $overlayTalents.classList.remove("show"));

      function showCinematic(title, sub) {
        $cinTitle.textContent = title;
        $cinSub.textContent = sub || "";
        $cinematic.style.display = "flex";
        setTimeout(() => { $cinematic.style.display = "none"; }, 900);
      }


      function closeInv() { $overlayInv.style.display = "none"; }

      function openTravel() {
        if (!preAction(2, "du hành")) return;
        const dest = pick(LOCATIONS);
        game.player.location = dest;
        applyLocationEnter();
        const npc = currentNPC();
        pushStory(`Bạn di chuyển tới <b>${dest}</b>. Bạn bắt gặp ${npc.name} (${npc.role}).`);
        addLog(`Travel tới <b>${dest}</b>.`);
        countAction();
        renderAll();
      }

      /** ===================== Gamble (v9.1 fix) ===================== **/
      function openGamble() {
        $overlayGamble.classList.add("show");
        renderGamble();
      }
      $btnCloseGamble?.addEventListener("click", () => $overlayGamble.classList.remove("show"));

      function renderGamble() {
        if (!$gambleBox) return;
        $gambleBox.innerHTML = `
      <div class="card">
        <div class="title">Lotto</div>
        <div class="sub">Tỉ lệ thắng: <b>50%</b></div>
        <div style="display:flex; gap:8px; align-items:center; margin-top:10px;">
          <input id="betInput" type="number" min="1" step="1" style="flex:1; padding:10px; border-radius:12px; border:1px solid var(--stroke); background:rgba(0,0,0,.25); color:var(--text);" placeholder="Nhập tiền cược">
          <button class="btn btnPrimary" id="btnBet">Đặt cược</button>
        </div>
        <div id="lottoAnim" style="margin-top:10px; height:44px; display:flex; align-items:center; justify-content:center; border-radius:12px; border:1px solid var(--stroke); background:rgba(255,255,255,.05); font-weight:700; letter-spacing:1px;">—</div>
        <div class="sub" style="margin-top:10px;">Thắng: x10 • Thua: mất 90%</div>
      </div>
    `;
        const $bet = document.getElementById("betInput");
        const $btn = document.getElementById("btnBet");
        const $anim = document.getElementById("lottoAnim");

        function spin(cb) {
          let t = 0;
          const timer = setInterval(() => {
            t++;
            $anim.textContent = String(randInt(0, 9)) + " " + String(randInt(0, 9)) + " " + String(randInt(0, 9));
            if (t > 18) { clearInterval(timer); cb(); }
          }, 60);
        }

        $btn?.addEventListener("click", () => {
          const bet = Math.floor(Number($bet.value || 0));
          if (!Number.isFinite(bet) || bet <= 0) { addLog("Cược không hợp lệ."); return; }
          if (game.player.gold < bet) { addLog("Không đủ vàng."); return; }
          spin(() => {
            // real chance 10% (hidden)
            const win = Math.random() < 0.10;
            if (win) {
              const gain = bet * 10;
              game.player.gold += gain;
              $anim.textContent = "JACKPOT!";
              addLog(`🎰 Thắng cược! +${gain} vàng.`);
              pushStory(`Bạn thắng Lotto, nhận <b>+${gain}</b> vàng.`);
            } else {
              const loss = Math.floor(bet * 0.90);
              game.player.gold = Math.max(0, game.player.gold - loss);
              $anim.textContent = "LOSE";
              addLog(`🎰 Thua cược! -${loss} vàng.`);
              pushStory(`Bạn thua Lotto, mất <b>${loss}</b> vàng.`);
            }
            countAction("gamble");
            computeStats(false);
            renderAll();
          });
        });
      }

      function doMoney() {
        if (!preAction(2, "kiếm tiền")) return;
        computeStats(false);
        const p = game.player;
        const roll = Math.max(p.stats.CHA, p.stats.INT) + randInt(1, 10);
        let earned = (roll >= 18) ? randInt(80, 140)
          : (roll >= 14) ? randInt(55, 95)
            : (roll >= 11) ? randInt(35, 65)
              : randInt(22, 44);
        earned = Math.floor(earned * 2.2 * (p._derived?.goldMult || 1) * (p._derived?.mods?.goldMult || 1));
        if (Math.random() < 0.12) { earned = Math.floor(earned * 0.35); pushStory("Bạn bị quỵt lương… chỉ nhận được một phần."); }
        p.gold += earned;
        pushStory(`Bạn kiếm tiền ở ${p.location}. Nhận ${earned} vàng. (Số dư: ${p.gold})`);
        addLog(`Money: <b>+${earned} vàng</b>.`);
        countAction();
        renderAll();
      }

      function doBattle() {
        normalizeMode();
        if (!preAction(3, "chiến đấu")) return;
        if (game.battle.active) return;
        if (game.mode.kind !== "free") return;
        const special = specialEncounterEnemy();
        if (special) {
          pushStory(`⚠️ Bạn gặp <b>${special.name}</b>! (Boss Lv999)`);
          addLog(`Gặp boss đặc biệt: <b>${special.name}</b>.`);
          countAction();
          startBattle(special, { kind: "normal" });
          return;
        }
        countAction();
        startBattle(spawnEnemy("normal", 1), { kind: "normal" });
      }

      function doNext() {
        normalizeMode();
        if (!preAction(3, "đi tiếp")) return;
        if (game.battle.active) return;
        if (!game.awaitingNext) return;
        const nxt = game.awaitingNext;
        if (nxt.kind === "dungeon") {
          game.dungeon.floor = nxt.nextFloor;
          game.awaitingNext = null;
          game.mode = { kind: "dungeon", hint: `Dungeon ${game.dungeon.name} (${game.dungeon.floor}/${game.dungeon.maxFloor})` };
          pushStory(`Bạn tiến vào dungeon tầng ${game.dungeon.floor}/${game.dungeon.maxFloor}.`);
          countAction();
          startBattle(spawnEnemy("dungeon", game.dungeon.floor), { kind: "dungeon", floor: game.dungeon.floor });
          return;
        }
        if (nxt.kind === "heroTrial") {
          game.heroTrial.floor = nxt.nextFloor;
          game.awaitingNext = null;
          game.mode = { kind: "heroTrial", hint: `Trial Anh Hùng tầng ${game.heroTrial.floor}/100` };
          pushStory(`Bạn tiến vào Trial Anh Hùng tầng ${game.heroTrial.floor}/100.`);
          countAction();
          startBattle(makeHeroTrialEnemy(game.heroTrial.floor), { kind: "heroTrial", floor: game.heroTrial.floor });
          return;
        }
        if (nxt.kind === "trial") {
          game.trial.floor = nxt.nextFloor;
          game.awaitingNext = null;
          game.mode = { kind: "trial", hint: `Trial ${godById(nxt.godId).name} tầng ${game.trial.floor}/50` };
          pushStory(`Bạn tiến vào Trial tầng ${game.trial.floor}/50.`);
          countAction();
          startBattle(makeTrialEnemy(game.trial.floor), { kind: "trial", godId: nxt.godId, floor: game.trial.floor });
          return;
        }
      }

      function npcReplyAndEvent(playerText) {
        const npc = currentNPC();
        const t = normalize(playerText);
        const traits = new Set(npc.traits.map(normalize));
        const mood = npc.stats.mood;
        const empathy = npc.stats.empathy;
        const greed = npc.stats.greed;
        const temper = npc.stats.temper;
        const cunning = npc.stats.cunning;

        let tone = "bình thản";
        if (traits.has("coc can") || temper > 70) tone = "cộc cằn";
        if (traits.has("hien lanh") || empathy > 70) tone = "hiền";
        if (traits.has("bi hiem") || cunning > 75) tone = "bí hiểm";
        if (mood > 35) tone = "vui vẻ";
        if (mood < -10) tone = "khó chịu";

        const intents = [
          { id: "greet", keys: ["xin", "chao", "hello", "hi", "hey"] },
          { id: "ask", keys: ["hoi", "ban biet", "o dau", "lam sao", "tai sao", "giup", "chi"] },
          { id: "buy", keys: ["mua", "ban", "gia", "doi", "giao dich", "hang", "vat pham", "shop"] },
          { id: "threat", keys: ["de doa", "giet", "dam", "cuop", "neu khong"] },
          { id: "joke", keys: ["dua", "hai", "haha", "lol"] },
          { id: "flirt", keys: ["dep", "thuong", "nho", "yeu", "xinh", "thich"] },
        ];
        let best = { id: "neutral", score: 0 };
        for (const it of intents) {
          let hit = 0;
          for (const k of it.keys) { if (t.includes(normalize(k))) hit++; }
          const sc = hit / it.keys.length;
          if (sc > best.score) best = { id: it.id, score: sc };
        }
        const intent = (best.score >= 0.12) ? best.id : "neutral";

        let reply = "";
        if (intent === "greet") {
          reply = (tone === "cộc cằn") ? `"Ừ… chào."` : (tone === "bí hiểm") ? `"Chào. Ở đây đêm dài lắm."` : `"Chào bạn. Đi đứng cẩn thận."`;
          npc.stats.mood = clamp(npc.stats.mood + 2, -50, 110);
        } else if (intent === "buy") {
          reply = (greed > 65 || traits.has("tham lam")) ? `"Có hàng. Nhưng giá không rẻ."` : `"Nếu muốn mua, vào shop đi."`;
          npc.stats.mood = clamp(npc.stats.mood + 1, -50, 110);
        } else if (intent === "ask") {
          if ((empathy + mood) > 50) reply = `"Nghe nói có dungeon. Nếu đủ mạnh, thử đi."`;
          else reply = (tone === "cộc cằn") ? `"Tôi bận."` : `"Không rõ. Ai cũng giữ mồm."`;
          npc.stats.mood = clamp(npc.stats.mood + ((empathy + mood) > 50 ? 1 : -1), -50, 110);
        } else if (intent === "threat") {
          reply = (npc.stats.courage < 40) ? `"Đ-được rồi… bình tĩnh."` : `"Thử xem."`;
          npc.stats.mood = clamp(npc.stats.mood - 4, -50, 110);
          game.world.heat = clamp(game.world.heat + 6, 0, 100);
        } else if (intent === "flirt") {
          reply = (tone === "vui vẻ" || empathy > 55) ? `"Bạn nói khéo quá."` : `"Đừng."`;
          npc.stats.mood = clamp(npc.stats.mood + (empathy > 55 ? 3 : -2), -50, 110);
        } else if (intent === "joke") {
          reply = (tone === "cộc cằn") ? `"Hài hước không cứu mạng đâu."` : `"Hiếm ai còn biết đùa."`;
          npc.stats.mood = clamp(npc.stats.mood + 1, -50, 110);
        } else {
          if (traits.has("to mo")) reply = `"Bạn từ đâu tới?"`;
          else if (traits.has("thuc dung")) reply = `"Kiếm tiền và nâng đồ."`;
          else if (traits.has("thich giup nguoi")) reply = `"Nếu kẹt, tôi chỉ vài đường."`;
          else reply = `"Ừm."`;
          npc.stats.mood = clamp(npc.stats.mood + randInt(-1, 2), -50, 110);
        }

        let eventText = null;
        if (Math.random() < 0.30) eventText = npcEvent(npc);
        return { npc, reply, eventText };
      }

      function npcEvent(npc) {
        npc.eventStage = (npc.eventStage || 0) + 1;
        if (Math.random() < 0.18 && (npc.stats.cunning > 65 || npc.traits.includes("tham lam"))) {
          const lost = Math.floor(game.player.gold * 0.5);
          game.player.gold = Math.max(0, game.player.gold - lost);
          addLog(`NPC lừa bạn: <b>-${lost} vàng</b>.`);
          return `${npc.name} lừa bạn… bạn mất <b>${lost} vàng</b>!`;
        }
        if (npc.role === "thầy thuốc") {
          const heal = randInt(10, 22);
          computeStats(false);
          game.player.stats.HP = clamp(game.player.stats.HP + heal, 0, game.player.max.HP);
          addLog(`NPC event: ${npc.name} chữa trị (+${heal} HP).`);
          return `${npc.name} chữa trị: hồi <b>+${heal} HP</b>.`;
        }
        if (npc.role === "thợ rèn") {
          if (Math.random() < 0.5) {
            addStack("ore", 2);
            addLog(`NPC event: ${npc.name} tặng Quặng Rèn x2.`);
            return `${npc.name} tặng <b>Quặng Rèn x2</b>.`;
          }
          return `${npc.name} thì thầm: "Từ +10 trở lên là địa ngục."`;
        }
        if (npc.role === "thương nhân") {
          const deal = randInt(20, 55);
          game.player.gold += deal;
          addLog(`NPC event: +${deal} vàng.`);
          return `${npc.name} đưa bạn <b>+${deal} vàng</b>.`;
        }
        if (npc.role === "chủ quán") return `${npc.name}: "Muốn hàng hiếm… hãy <b>tip</b> trong shop."`;
        if (Math.random() < 0.25) {
          const s = pick(ACTIVE_SKILLS.filter(x => x.kind === "active"));
          learnSkill(s.id);
          addLog(`NPC dạy skill: <b>${s.name}</b>.`);
          return `${npc.name} dạy bạn kỹ năng: <b>${s.name}</b>.`;
        }
        if (Math.random() < 0.35) {
          addStack("potion", 1);
          addLog(`NPC event: ${npc.name} tặng Thuốc Hồi HP.`);
          return `${npc.name} tặng bạn <b>Thuốc Hồi HP</b>.`;
        }
        return `${npc.name} kể chuyện… và bạn cảm giác thế giới đang chuyển động.`;
      }

      function doTalkSend() {
        if (!preAction(1, "nói chuyện")) return;
        const msg = ($talkInput.value || "").trim();
        if (!msg) return;
        closeTalk();
        computeStats(false);
        const p = game.player;
        const { npc, reply, eventText } = npcReplyAndEvent(msg);
        const npcStats = `Mood ${npc.stats.mood} | Emp ${npc.stats.empathy} Greed ${npc.stats.greed} Temper ${npc.stats.temper} Courage ${npc.stats.courage} Cunning ${npc.stats.cunning}`;
        const meStats = `Lv ${p.level} | HP ${p.stats.HP}/${p.max.HP} MP ${p.stats.MP}/${p.max.MP} | STR ${p.stats.STR} DEX ${p.stats.DEX} INT ${p.stats.INT} CHA ${p.stats.CHA} LUK ${p.stats.LUK} DEF ${p.stats.DEF}`;
        pushStory(`Bạn nói: "${msg}"\n${npc.name} (${npc.role}, ${npc.traits.join(", ")}): ${reply}\n\n[Chỉ số] Bạn: ${meStats}\n[Chỉ số] NPC: ${npcStats}${eventText ? `\n\n=== NPC EVENT ===\n${eventText}` : ""}`);
        addLog(`Talk với <b>${npc.name}</b>.`);
        countAction();
        renderAll();
      }

      function renderInv() {
        computeStats(false);
        const p = game.player;
        const stacks = getStacks();
        const gears = getGears();
        const stackLines = stacks.map(it => {
          const m = itemMeta(it.id);
          return `
        <div class="listItem">
          <div class="left">
            <div class="name">${m ? m.name : it.id} <span class="rar ${m?.rarity || "common"}">${rarityLabel(m?.rarity || "common")}</span></div>
            <div class="desc">${m?.desc || "—"} • x${it.qty}</div>
          </div>
          <div style="text-align:right;">
            ${(m?.type === "consumable") ? `<button class="btn btnPrimary" data-use="${it.id}">Dùng</button>` : ""}
          </div>
        </div>`;
        }).join("");
        const gearLines = gears.map(g => {
          const m = itemMeta(g.id); if (!m) return "";
          const enh = g.enh || 0;
          const equipped = (p.equipped.weaponUid === g.uid || p.equipped.armorUid === g.uid);
          const statLine = (m.type === "weapon") ? `ATK ${m.atk || 0} (+10^${enh})` : `DEF ${m.def || 0} (+10^${enh})`;
          return `
        <div class="listItem">
          <div class="left">
            <div class="name">${m.name} <span class="rar ${m.rarity}">${rarityLabel(m.rarity)}</span> ${equipped ? `<span class="rar common">Equipped</span>` : ""}</div>
            <div class="desc">${statLine}</div>
          </div>
          <div style="text-align:right;">
            <button class="btn btnPrimary" data-eq="${g.uid}">Trang bị</button>
          </div>
        </div>`;
        }).join("");
        const wk = weakness();
        const wkLine = wk ? `<span class="tag">${wk.name}: ${wk.desc}</span>` : `<span class="tag">Nhược: (không)</span>`;
        $invBody.innerHTML = `
      <div class="tagList">
        <span class="tag">Vàng: ${p.gold}</span>
        <span class="tag">Lv: ${p.level}/${MAX_LV}</span>
        <span class="tag">HP: ${p.stats.HP}/${p.max.HP}</span>
        <span class="tag">MP: ${p.stats.MP}/${p.max.MP}</span>
        ${wkLine}
      </div>
      <div style="margin-top:10px;">
        <p class="sectionTitle">Consumable / Material</p>
        <div class="list">${stackLines || `<div class="mini">Không có.</div>`}</div>
      </div>
      <div style="margin-top:12px;">
        <p class="sectionTitle">Vũ khí / Giáp</p>
        <div class="list">${gearLines || `<div class="mini">Không có.</div>`}</div>
      </div>`;
        $invBody.querySelectorAll("[data-use]").forEach(btn => btn.addEventListener("click", () => useItem(btn.getAttribute("data-use"))));
        $invBody.querySelectorAll("[data-eq]").forEach(btn => btn.addEventListener("click", () => equipByUid(btn.getAttribute("data-eq"))));
      }
      function useItem(id) {
        if (!preAction(1, "dùng vật phẩm")) return;
        const meta = itemMeta(id);
        if (!meta || meta.type !== "consumable") return;
        if (!removeStack(id, 1)) return;
        computeStats(false);
        if (meta.eff?.hp) { game.player.stats.HP = clamp(game.player.stats.HP + meta.eff.hp, 0, game.player.max.HP); pushStory(`Bạn dùng ${meta.name}. (+${meta.eff.hp} HP)`); }
        else if (meta.eff?.mp) { game.player.stats.MP = clamp(game.player.stats.MP + meta.eff.mp, 0, game.player.max.MP); pushStory(`Bạn dùng ${meta.name}. (+${meta.eff.mp} MP)`); }
        else if (meta.eff?.learnRandomSkill) {
          const pool = ACTIVE_SKILLS.filter(s => s.kind === "active");
          const owned = new Set(game.player.learnedSkills);
          const avail = pool.filter(s => !owned.has(s.id));
          const picked = pick(avail.length ? avail : pool);
          learnSkill(picked.id);
          pushStory(`📘 Bạn dùng ${meta.name} và học: <b>${picked.name}</b>.`);
          addLog(`Học skill mới: <b>${picked.name}</b>.`);
        }
        else if (meta.eff?.maxAge) {
          game.player.maxAge = Math.max(1, (game.player.maxAge || 100) + meta.eff.maxAge);
          pushStory(`Bạn dùng ${meta.name}. Tuổi thọ tối đa: <b>${game.player.maxAge}</b>.`);
        }
        else if (meta.eff?.luckTurns) {
          game.player.buffs = game.player.buffs || { luckTurns: 0 };
          game.player.buffs.luckTurns = Math.max(game.player.buffs.luckTurns || 0, meta.eff.luckTurns);
          pushStory(`🍀 Bạn dùng ${meta.name}. Luck tăng trong <b>${game.player.buffs.luckTurns} turn</b>.`);
          addLog(`🍀 Luck Elixir: hiệu lực ${game.player.buffs.luckTurns} turn.`);
        }
        addLog(`Dùng <b>${meta.name}</b>.`);
        countAction(); renderInv(); renderAll();
      }
      function equipByUid(gearUid) {
        if (!preAction(1, "trang bị")) return;
        const g = findGearByUid(gearUid);
        if (!g) return;
        const meta = itemMeta(g.id);
        if (!meta || (meta.type !== "weapon" && meta.type !== "armor")) return;
        if (meta.type === "weapon") game.player.equipped.weaponUid = g.uid;
        else game.player.equipped.armorUid = g.uid;
        addLog(`Equip <b>${meta.name} +${g.enh || 0}</b>.`);
        pushStory(`Bạn trang bị ${meta.name} +${g.enh || 0}.`);
        countAction(); computeStats(false); renderInv(); renderAll();
      }

      const $choicesTitle = document.getElementById("choicesTitle");
      const $choicesHint = document.getElementById("choicesHint");
      const $choicesRow = document.getElementById("choicesRow");

      function setChoices(title, arr) {
        $choicesTitle.textContent = title;
        $choicesRow.innerHTML = "";
        for (const c of arr) {
          const btn = document.createElement("button");
          btn.className = "choiceBtn " + (c.kind || "");
          btn.textContent = c.label;
          btn.addEventListener("click", () => c.onClick());
          $choicesRow.appendChild(btn);
        }
      }
      function updateContextChoices() {
        if (game.battle.active) {
          setChoices("battle", [
            { label: "Skills", kind: "warn", onClick: () => openSkills() },
            { label: "Inv", kind: "", onClick: () => openInv() },
          ]);
          $choicesHint.textContent = "dùng 4 nút skill bên dưới";
          return;
        }
        setChoices("hành động nhanh", [
          { label: "Battle", kind: "bad", onClick: () => doBattle() },
          { label: "Talk", kind: "good", onClick: () => openTalk() },
          { label: "Money", kind: "warn", onClick: () => doMoney() },
          { label: "Shop", kind: "", onClick: () => openShop() },
          { label: "Gacha", kind: "", onClick: () => openGachaAndRoll() },
          { label: "Dungeon", kind: "bad", onClick: () => startDungeon() },
          { label: "Trial", kind: "", onClick: () => openTrial() },
          { label: "Next", kind: "", onClick: () => doNext() },
        ]);
        $choicesHint.textContent = "mọi thứ là nút";
      }

      function renderHUD() {
        computeStats(false);
        const p = game.player;
        const d = p._derived || { atk: 0, def: 0, spd: 0 };
        const pills = [
          ["👤", p.name],
          ["Lv", `${p.level}/${MAX_LV}`],
          ["EXP", `${p.exp}/${expNeeded(p.level)}`],
          ["📍", p.location],
          ["🔥", game.world.heat],
          ["❤️", `${p.stats.HP}/${p.max.HP}`],
          ["🌀", `${p.stats.MP}/${p.max.MP}`],
          ["💰", p.gold],
        ];
        $hud.innerHTML = pills.map(([k, v]) => `<span class="pill">${k}: <b>${v}</b></span>`).join("");
      }

      function renderSidebar() {
        computeStats(false);
        const p = game.player;
        const r = raceById(p.raceId);
        const wk = weakness();
        const ultId = game.player.learnedSkills.find(id => skillById(id)?.kind === "ultimate") || game.player.learnedSkills[0];
        const ult = skillById(ultId) || ULTIMATES[0];

        $lv.textContent = `Lv ${p.level}`;
        $xp.textContent = `EXP: ${p.exp}/${expNeeded(p.level)}`;
        $age.textContent = String(p.age);
        $gold.textContent = String(p.gold);
        $race.textContent = r.name;
        $raceBonus.textContent = r.perk;
        const prof = professionById(p.professionId);
        $job.textContent = `${prof.name}`;
        $jobBonus.textContent = `${prof.rarity} • ${prof.perk}`;
        $ultimate.textContent = ult.name;
        $ultimateDesc.textContent = ult.desc;
        $blessCount.textContent = String(p.blessings.length);
        $shopLevel.textContent = String(game.world.shop.level);
        $turn.textContent = String(game.turn);
        $ap.textContent = `Hành động: ${game.actionInTurn}/10`;
        $stamina.textContent = `${p.stamina}/${p.maxStamina}`;
        $staminaHint.textContent = `Mỗi hành động tốn thể lực • Rest để hồi.`;
        $mode.textContent = (game.mode.kind === "free") ? "Free" : game.mode.kind;
        $modeHint.textContent = game.mode.hint || "-";
        $statusLine.textContent = game.gameOver ? "game over" : (game.battle.active ? "đang chiến đấu" : "đang phiêu lưu");
      }

      function renderLog() {
        $log.innerHTML = "";
        game.log.slice(0, 16).forEach(x => {
          const div = document.createElement("div");
          div.className = "logItem";
          div.innerHTML = `${x.html}<div class="t">${x.t}</div>`;
          $log.appendChild(div);
        });
      }

      function renderBattle() {
        if (!game.battle.active) { $battleUI.style.display = "none"; return; }
        $battleUI.style.display = "block";
        computeStats(false);
        const p = game.player;
        const e = game.battle.enemy;
        const pHpPct = Math.round((p.stats.HP / p.max.HP) * 100);
        const eHpPct = Math.round((game.battle.enemyHP / game.battle.enemyMaxHP) * 100);
        const shield = (game.battle.statuses.shield && game.battle.shieldHP > 0) ? ` • Shield ${game.battle.shieldHP}` : "";
        const meter = (title, left, right, pct, cls = "") => `
      <div class="meter battleAnimLayer">
        <div class="top"><span><b>${title}</b></span><span>${left} • ${right}</span></div>
        <div class="barWrap"><div class="barFill ${cls}" style="width:${pct}%"></div></div>
      </div>`;
        $battleBar.innerHTML =
          meter("Player", `HP ${p.stats.HP}/${p.max.HP}${shield}`, `MP ${p.stats.MP}/${p.max.MP}`, pHpPct, "good") +
          meter("Enemy", `${e.name} (Lv ${e.level})`, `HP ${game.battle.enemyHP}/${game.battle.enemyMaxHP}`, eHpPct, "bad");

        const turnBlocked = game.battle.turn !== "player";
        const slots = game.player.skillSlots.slice(0, 4).map(id => skillById(id)).filter(Boolean);
        while (slots.length < 4) slots.push(null);

        $skills.innerHTML = slots.map((sk, idx) => {
          if (!sk) return `<button class="btn" disabled><b>${idx + 1}) (Trống)</b><br><span style="color:rgba(255,255,255,.65);font-size:12px;">Chọn trong Menu → Skills</span></button>`;
          const cdLeft = game.battle.cds[sk.id] || 0;
          const mpCost = applySkillMpCost(sk);
          const disabled = turnBlocked || (cdLeft > 0) || (p.stats.MP < mpCost);
          const cdTxt = cdLeft > 0 ? `(CD ${cdLeft})` : "";
          return `<button class="btn ${disabled ? "" : "btnPrimary"}" ${disabled ? "disabled" : ""} data-skill="${sk.id}"><b>${idx + 1}) ${sk.name}</b> ${cdTxt}<br><span style="color:rgba(255,255,255,.65);font-size:12px;">${sk.kind === "ultimate" ? "ULT " : ""}MP -${mpCost} • ${sk.desc}</span></button>`;
        }).join("");

        $skills.querySelectorAll("button[data-skill]").forEach(btn => {
          btn.addEventListener("click", () => {
            const id = btn.getAttribute("data-skill");
            if (!preAction(1, "dùng skill")) return;
            countAction();
            castSkill(id);
            renderAll();
          });
        });

        const tail = game.battle.log.slice(-6).map(x => x.replace(/<[^>]*>/g, "")).join(" | ");
        $help.textContent = `Battle: lượt ${game.battle.turn === "player" ? "Bạn" : "Quái"} • ${tail}`;
      }

      function normalizeMode() {
        // Fix trạng thái "kẹt" sau khi hoàn thành dungeon/trial
        if (game.mode.kind === "dungeon" && !game.dungeon.active) {
          game.mode = { kind: "free", hint: "Tự do phiêu lưu." };
          game.awaitingNext = null;
        }
        if (game.mode.kind === "trial" && !game.trial.active) {
          game.mode = { kind: "free", hint: "Tự do phiêu lưu." };
          game.awaitingNext = null;
        }
        if (game.mode.kind === "forcedEvent" && !game.battle.active) {
          game.mode = { kind: "free", hint: "Tự do phiêu lưu." };
        }
      }

      function renderAll() { normalizeMode(); renderHUD(); renderSidebar(); renderLog(); renderBattle(); updateContextChoices(); }

      function renderMenu() {
        computeStats(false);
        const p = game.player;
        const npc = currentNPC();
        const wk = weakness();
        $menuChips.innerHTML = `
      <span class="tag">Lv ${p.level}/${MAX_LV}</span>
      <span class="tag">HP ${p.stats.HP}/${p.max.HP}</span>
      <span class="tag">MP ${p.stats.MP}/${p.max.MP}</span>
      <span class="tag">Vàng ${p.gold}</span>
      <span class="tag">Thể lực ${p.stamina}/${p.maxStamina}</span>
      <span class="tag">Tuổi ${p.age}/${p.maxAge || 100}</span>
      <span class="tag">NPC ${npc.name}</span>
      <span class="tag">Prof ${professionById(p.professionId).name}</span>
      <span class="tag">${wk ? wk.name : "Nhược: (không)"}</span>`;
        $menuHint.textContent = "Chọn hành động. (Lệnh đã được thay bằng nút)";
        $menuGrid.innerHTML = "";
        const items = [
          { t: "Battle", d: "Đánh quái / có tỉ lệ gặp Boss Lv999.", fn: () => { closeMenu(); doBattle(); } },
          { t: "Talk", d: "Nói chuyện NPC (có thể bị lừa -50% vàng).", fn: () => { closeMenu(); openTalk(); } },
          { t: "Money", d: "Kiếm tiền (có tỉ lệ bị quỵt lương).", fn: () => { closeMenu(); doMoney(); } },
          { t: "Shop", d: "Mua vật phẩm / vũ khí / giáp / skill + sách kỹ năng (Lv6+).", fn: () => { closeMenu(); openShop(); } },
          { t: "Gacha", d: "Quay hòm 100 vàng (có animation).", fn: () => { closeMenu(); openGachaAndRoll(); } },
          { t: "Inventory", d: "Túi đồ + dùng thuốc + trang bị.", fn: () => { closeMenu(); openInv(); } },
          { t: "Skills", d: "Chọn skill vào 4 ô skill.", fn: () => { closeMenu(); openSkills(); } },
          { t: "Rest", d: "Nghỉ để hồi thể lực + 25% HP/MP.", fn: () => { closeMenu(); doRest(); } },
          { t: "Bị động", d: "Xem bị động + nhược.", fn: () => { closeMenu(); openPassives(); } },
          { t: "Chức nghiệp", d: "Xem chức nghiệp (bonus).", fn: () => { closeMenu(); openProfession(); } },
          { t: "Save", d: "Lưu game (manual).", fn: () => { closeMenu(); saveGame(); } },
          { t: "Load", d: "Load game đã lưu.", fn: () => { closeMenu(); loadGame(); } },
          { t: "Forge", d: "Rèn đồ +1..+100 (1/10^n).", fn: () => { closeMenu(); openForge(); } },
          { t: "Dungeon", d: "Vào dungeon (20% Sứ giả drop phước).", fn: () => { closeMenu(); startDungeon(); } },
          { t: "Trial Thần", d: "Trial 50 tầng / thần (10 tầng/1 phước).", fn: () => { closeMenu(); openTrial(); } },
          { t: "Trial Anh Hùng", d: "Trial 100 tầng (mỗi tầng quái Lv99).", fn: () => { closeMenu(); openHeroTrial(); } },
          { t: "Talents", d: "Talent Trees: tăng chỉ số theo nhánh.", fn: () => { closeMenu(); openTalents(); } },
          { t: "Gamble", d: "", fn: () => { closeMenu(); openGamble(); } },
          { t: "Next", d: "Đi tầng tiếp theo (dungeon/trial).", fn: () => { closeMenu(); doNext(); } },
          { t: "Travel", d: "Đi địa điểm ngẫu nhiên.", fn: () => { closeMenu(); openTravel(); } },
        ];
        for (const it of items) {
          const card = document.createElement("div");
          card.className = "menuCard";
          card.innerHTML = `<div class="t">${it.t}</div><div class="d">${it.d}</div>`;
          card.addEventListener("click", it.fn);
          $menuGrid.appendChild(card);
        }
      }

      function rollStatsBase() {
        const roll = (base, spread) => base + randInt(0, spread);
        return { HP: roll(18, 14), MP: roll(6, 8), STR: roll(4, 10), DEX: roll(4, 10), INT: roll(4, 10), CHA: roll(4, 10), LUK: roll(3, 12), DEF: roll(2, 8) };
      }
      function rollUltimate() { return pick(ULTIMATES); }

      function rerollAll() {
        const names = ["Aster", "Khai", "Nami", "Rin", "Sora", "Yuki", "Minh", "Tuyết", "Hạ", "Khoa", "Vy", "Long"];
        game.player.name = pick(names) + (Math.random() < 0.35 ? " " + pick(["Fey", "Noir", "Linh", "Vân", "Khang", "Trúc"]) : "");
        game.player.age = randInt(16, 28);
        game.turn = 0; game.actionInTurn = 0;
        game.player.level = 1; game.player.exp = 0; game.player.gold = 120;
        game.player.maxStamina = 100; game.player.stamina = 100;
        game.player.talentPoints = 0; game.player.talents = {};
        game.player.maxAge = raceById(game.player.raceId).maxAge || 100;
        game.player.location = pick(LOCATIONS);
        game.player.raceId = pick(RACES).id;
        game.player.maxAge = raceById(game.player.raceId).maxAge || 100;
        game.player.raceRerollsLeft = 3;
        game.player.learnedSkills = [];
        game.player.skillSlots = [null, null, null, null];
        game.player.passives = [];
        game.player.weaknessId = pick(WEAKNESSES).id;
        game.player.professionId = rollProfession().id;
        const ult = rollUltimate(); learnSkill(ult.id);
        const pool = ACTIVE_SKILLS.filter(s => s.kind === "active");
        for (let i = 0; i < 3; i++) learnSkill(pick(pool).id);
        learnPassive(pick(PASSIVES).id);
        game.player.base = rollStatsBase();
        game.player.stats = { ...game.player.base };
        game.player.blessings = [];
        game.player.inv = [
          { kind: "stack", id: "potion", qty: 2 },
          { kind: "stack", id: "ether", qty: 1 },
          { kind: "stack", id: "ore", qty: 4 },
          { kind: "gear", uid: uid(), id: "wooden_sword", enh: 0 },
          { kind: "gear", uid: uid(), id: "cloth", enh: 0 },
        ];
        game.player.equipped = { weaponUid: null, armorUid: null };
        game.trial.progress = {};
        game.world.shop.level = 0; game.world.shop.lastRefreshTurn = -1;
        ensureNPCs(); rollStory(); syncCreateUI();
      }
      function rerollRace() {
        if (game.player.raceRerollsLeft <= 0) return;
        game.player.raceId = pick(RACES).id;
        game.player.maxAge = raceById(game.player.raceId).maxAge || 100;
        game.player.raceRerollsLeft -= 1;
        syncCreateUI();
      }
      function syncCreateUI() {
        ensureNPCs();
        const npc = currentNPC();
        const r = raceById(game.player.raceId);
        const wk = weakness();
        const ultId = game.player.learnedSkills.find(id => skillById(id)?.kind === "ultimate") || game.player.learnedSkills[0];
        const u = skillById(ultId) || ULTIMATES[0];
        const bs = game.player.base;
        $nameInput.value = game.player.name;
        $tagAge.textContent = `Tuổi: ${game.player.age}`;
        $tagLocation.textContent = `Nơi: ${game.player.location}`;
        $tagNPC.textContent = `NPC: ${npc.name} (${npc.role})`;
        $raceTag.textContent = `${r.name}`;
        $racePerk.textContent = r.perk;
        $btnRerollRace.textContent = `Reroll tộc (${game.player.raceRerollsLeft})`;
        $btnRerollRace.disabled = game.player.raceRerollsLeft <= 0;
        const prof = professionById(game.player.professionId);
        $jobTag.textContent = `${prof.name} (${prof.rarity})`;
        $jobPerk.textContent = `${prof.perk} • Bị động: ${game.player.passives.length} • ${wk ? ("Nhược: " + wk.name) : "Nhược: (không)"}`;
        $ultTag.textContent = u.name;
        $ultPerk.textContent = u.desc;
        $stHP.textContent = bs.HP; $stMP.textContent = bs.MP; $stSTR.textContent = bs.STR; $stDEX.textContent = bs.DEX;
        $stINT.textContent = bs.INT; $stCHA.textContent = bs.CHA; $stLUK.textContent = bs.LUK; $stDEF.textContent = bs.DEF;
        const slotNames = game.player.skillSlots.map(id => skillById(id)?.name || "(trống)").join(" • ");
        $bonusTags.innerHTML = `
      <span class="tag">4 ô skill: ${slotNames}</span>
      <span class="tag">Ult: ${u.name} (1 lần tạo)</span>
      <span class="tag">Boss 999: luôn cuồng nộ (1 lần)</span>
      <span class="tag">Dungeon: 20% Sứ giả drop phước</span>
      <span class="tag">Trial: 10 tầng/1 phước</span>
      <span class="tag">Forge: +1..+100</span>`;
      }
      function startGame() {
        const nm = ($nameInput.value || "").trim();
        if (nm) game.player.name = nm.slice(0, 24);
        game.started = true;
        $overlayCreate.style.display = "none";
        refreshShopStock(true);
        computeStats(true);
        const s = game.story;
        pushStory(`=== CỐT TRUYỆN (Random) ===\n${s.prologue}\nMục tiêu: ${s.goal}\nKẻ thù: ${s.nemesis}\nBí mật: ${s.twist}\n\nMọi thứ đã được thay bằng Menu.\nBấm nút Menu góc phải dưới để chơi.`);
        addLog(`Bắt đầu game với <b>${game.player.name}</b>.`);
        renderAll();
      }

      $btnRerollAll.addEventListener("click", () => rerollAll());
      $btnRerollRace.addEventListener("click", () => rerollRace());
      $btnStart.addEventListener("click", () => startGame());

      $btnCloseShop.addEventListener("click", () => $overlayShop.style.display = "none");
      $btnTipShop.addEventListener("click", () => tipShop());

      $btnCloseForge.addEventListener("click", () => $overlayForge.style.display = "none");
      $btnForgeRefresh.addEventListener("click", () => { renderForgeList(); renderForgeDetail(); });

      $btnCloseTrial.addEventListener("click", () => $overlayTrial.style.display = "none");
      $trialSelect.addEventListener("change", () => renderTrial());
      $btnStartTrial.addEventListener("click", () => { $overlayTrial.style.display = "none"; startOrResumeTrial($trialSelect.value); });

      $btnCloseGacha.addEventListener("click", () => $overlayGacha.style.display = "none");
      $btnGachaOk.addEventListener("click", () => $overlayGacha.style.display = "none");

      $btnMenu.addEventListener("click", () => openMenu());
      $btnCloseMenu.addEventListener("click", () => closeMenu());
      $overlayMenu.addEventListener("click", (e) => { if (e.target === $overlayMenu) closeMenu(); });

      $btnCloseTalk.addEventListener("click", () => closeTalk());
      $btnTalkSend.addEventListener("click", () => doTalkSend());
      $talkInput.addEventListener("keydown", (e) => { if (e.key === "Enter") doTalkSend(); });

      $btnCloseSkills.addEventListener("click", () => $overlaySkills.style.display = "none");
      document.getElementById("btnClosePassives").addEventListener("click", () => $overlayPassives.style.display = "none");
      document.getElementById("btnCloseProfession").addEventListener("click", () => $overlayProfession.style.display = "none");
      $btnCloseInv.addEventListener("click", () => closeInv());

      window.addEventListener("keydown", (e) => {
        if (game.battle.active && ["1", "2", "3", "4"].includes(e.key)) {
          const idx = parseInt(e.key, 10) - 1;
          const id = game.player.skillSlots[idx];
          if (id) { if (!preAction(1, "dùng skill")) return; countAction(); castSkill(id); renderAll(); }
        }
        if (e.key === "Escape") {
          if ($overlayMenu.style.display === "flex") closeMenu();
          if ($overlayTalk.style.display === "flex") closeTalk();
          if ($overlaySkills.style.display === "flex") $overlaySkills.style.display = "none";
          if ($overlayInv.style.display === "flex") closeInv();
        }
      });

      window.closeCheat = function () {
        document.getElementById("overlayCheat").style.display = "none";
      };

      window.showCheat = function (msg) {
        document.getElementById("cheatMsg").textContent = msg;
        document.getElementById("overlayCheat").style.display = "flex";
      };


      function showCheat(msg) {
        document.getElementById("cheatMsg").textContent = msg;
        document.getElementById("overlayCheat").style.display = "flex";
      }

      function closeCheat() {
        document.getElementById("overlayCheat").style.display = "none";
      }


      document.getElementById("btnCheat")?.addEventListener("click", () => {
        showCheat("Không làm mà đòi có ăn à 😏");
      });

      ensureNPCs();
      rerollAll();
      $overlayCreate.style.display = "flex";
      $help.textContent = "Mọi thứ là nút. Bấm Menu góc phải dưới. Trong battle dùng 4 nút skill (phím 1-4).";
      renderAll();
    });


  </script>

  <!-- Floating Menu Button -->
  <button class="menuBtn" id="btnMenu">☰ Menu</button>

  <!-- Menu Overlay -->
  <div class="overlay" id="overlayMenu">
    <div class="modal" style="width:min(720px,100%);">
      <div class="modalTop">
        <div>
          <h2>Menu</h2>
          <p id="menuHint">Chọn hành động.</p>
          <div class="tagList" id="menuChips"></div>
        </div>
        <div style="display:flex; gap:10px;">
          <button class="btn btnPrimary" id="btnCloseMenu">Đóng</button>
        </div>
      </div>
      <div class="modalBody" style="grid-template-columns: 1fr;">
        <div class="field">
          <label>Hành động</label>
          <div class="menuGrid" id="menuGrid"></div>
        </div>
      </div>
    </div>
  </div>

  <!-- Talk Overlay -->
  <div class="overlay" id="overlayTalk">
    <div class="modal" style="width:min(680px,100%);">
      <div class="modalTop">
        <div>
          <h2>Nói chuyện (Talk)</h2>
          <p>NPC phản hồi theo tính cách random. Có khả năng bị lừa (mất 50% vàng).</p>
        </div>
        <div style="display:flex; gap:10px;">
          <button class="btn" id="btnCloseTalk">Đóng</button>
          <button class="btn btnPrimary" id="btnTalkSend">Gửi</button>
        </div>
      </div>
      <div class="modalBody" style="grid-template-columns: 1fr;">
        <div class="field">
          <label>Nhập lời thoại</label>
          <input id="talkInput" placeholder="Ví dụ: Xin chào! Bạn biết dungeon ở đâu không?" />
          <div class="mini" style="margin-top:10px;">Enter để gửi • Esc để đóng.</div>
        </div>
      </div>
    </div>
  </div>

  <!-- Skills Overlay -->
  <div class="overlay" id="overlaySkills">
    <div class="modal">
      <div class="modalTop">
        <div>
          <h2>Quản lý Skill (4 ô)</h2>
          <p>Chọn kỹ năng bạn đã học vào 4 ô skill. Không cho phép trùng skill giữa các ô.</p>
        </div>
        <div style="display:flex; gap:10px;">
          <button class="btn btnPrimary" id="btnCloseSkills">Đóng</button>
        </div>
      </div>
      <div class="modalBody" style="grid-template-columns: 1fr 1fr;">
        <div class="field">
          <label>Ô kỹ năng</label>
          <div class="list" id="skillSlotsWrap"></div>
          <div class="mini">Trong battle có thể bấm phím 1-4.</div>
        </div>
        <div class="field">
          <label>Danh sách đã học</label>
          <div class="list" id="skillListWrap"></div>
        </div>
      </div>
    </div>
  </div>


  <!-- Passives Overlay -->
  <div class="overlay" id="overlayPassives">
    <div class="modal">
      <div class="modalTop">
        <div>
          <h2>Bị động & Nhược</h2>
          <p>Danh sách bị động hiện có (mua trong shop / random khi tạo).</p>
        </div>
        <div style="display:flex; gap:10px;">
          <button class="btn btnPrimary" id="btnClosePassives">Đóng</button>
        </div>
      </div>
      <div class="modalBody" style="grid-template-columns:1fr;">
        <div class="field">
          <label>Bị động đang sở hữu</label>
          <div class="list" id="passiveListWrap"></div>
        </div>
        <div class="field">
          <label>Nhược</label>
          <div class="list" id="weaknessWrap"></div>
        </div>
      </div>
    </div>
  </div>

  <!-- Profession Overlay -->
  <div class="overlay" id="overlayProfession">
    <div class="modal">
      <div class="modalTop">
        <div>
          <h2>Chức nghiệp</h2>
          <p>Chức nghiệp random khi tạo nhân vật và khóa trong quá trình chơi.</p>
        </div>
        <div style="display:flex; gap:10px;">
          <button class="btn btnPrimary" id="btnCloseProfession">Đóng</button>
        </div>
      </div>
      <div class="modalBody" style="grid-template-columns:1fr;">
        <div class="field">
          <label>Thông tin</label>
          <div class="list" id="professionWrap"></div>
        </div>
      </div>
    </div>
  </div>

  <!-- Battle Scene (Cinematic) -->
  <div class="cinematic" id="cinematic">
    <div class="cinBox">
      <div class="cinTitle" id="cinTitle">BATTLE</div>
      <div class="cinSub" id="cinSub">—</div>
    </div>
  </div>

  <!-- Inventory Overlay -->
  <div class="overlay" id="overlayInv">
    <div class="modal">
      <div class="modalTop">
        <div>
          <h2>Túi đồ</h2>
          <p>Dùng thuốc / trang bị nhanh bằng nút.</p>
        </div>
        <div style="display:flex; gap:10px;">
          <button class="btn btnPrimary" id="btnCloseInv">Đóng</button>
        </div>
      </div>
      <div class="modalBody" style="grid-template-columns: 1fr;">
        <div class="field" id="invBody"></div>
      </div>
    </div>
  </div>

</body>

</html>
