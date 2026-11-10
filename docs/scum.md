<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SCUM キノコ図鑑</title>
  <style>
    :root {
      --bg-color: #121417;
      --card-bg: #1c2026;
      --border-color: #2b323b;
      --text-main: #e2e8f0;
      --text-sub: #94a3b8;
      
      --accent-edible: #10B981;
      --accent-poison: #EF4444;
      
      /* タグ別カラー定義 */
      --accent-vitamin-d: #F59E0B; /* ビタミンD */
      --accent-vitamin-e: #10B981; /* ビタミンE */
      --accent-protein: #3B82F6;   /* タンパク質 */
      --accent-vitamin-b: #8B5CF6; /* ビタミンB群 */
      --accent-sugar: #EC4899;     /* 糖分 */
      --accent-lethal: #991B1B;    /* 致死性 */
      --accent-hallu: #8B5CF6;     /* 幻覚・錯乱・行動不能 */
      --accent-fatigue: #D97706;   /* 幻覚・疲労 */
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      background-color: var(--bg-color);
      color: var(--text-main);
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
      line-height: 1.6;
      padding: 2rem 1rem;
    }

    .container {
      max-width: 900px;
      margin: 0 auto;
    }

    h1 {
      font-size: 2rem;
      font-weight: 700;
      margin-bottom: 0.75rem;
      border-bottom: 2px solid var(--border-color);
      padding-bottom: 0.5rem;
    }

    .description {
      color: var(--text-sub);
      margin-bottom: 2rem;
      font-size: 0.95rem;
      background: var(--card-bg);
      padding: 1rem;
      border-radius: 6px;
      border-left: 4px solid var(--border-color);
    }

    .section-title {
      font-size: 1.35rem;
      margin: 2.5rem 0 0.5rem 0;
      display: flex;
      align-items: center;
      gap: 0.5rem;
    }

    .section-title.edible {
      color: var(--accent-edible);
      border-bottom: 2px solid rgba(16, 185, 129, 0.3);
      padding-bottom: 0.3rem;
    }

    .section-title.poisonous {
      color: var(--accent-poison);
      border-bottom: 2px solid rgba(239, 68, 68, 0.3);
      padding-bottom: 0.3rem;
    }

    .section-desc {
      color: var(--text-sub);
      font-size: 0.85rem;
      margin-bottom: 1rem;
    }

    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
      gap: 1rem;
    }

    .card {
      background-color: var(--card-bg);
      border: 1px solid var(--border-color);
      border-radius: 8px;
      overflow: hidden;
      transition: transform 0.2s ease, border-color 0.2s ease;
    }

    .card:hover {
      transform: translateY(-2px);
      border-color: #3b4452;
    }

    .card-img {
      width: 100%;
      height: 160px;
      object-fit: contain;
      padding: 0.5rem;
      background-color: #0d0f12;
      display: block;
    }

    .card-content {
      padding: 0.85rem 1rem;
    }

    .jp-name {
      font-size: 1.1rem;
      font-weight: 600;
      color: var(--text-main);
      margin-bottom: 0.2rem;
    }

    .en-name {
      font-size: 0.85rem;
      color: var(--text-sub);
      font-style: italic;
    }

    /* バッジ基本設定 */
    .badge-container {
      display: flex;
      flex-wrap: wrap;
      gap: 0.35rem;
      margin-top: 0.5rem;
    }

    .badge {
      display: inline-block;
      font-size: 0.75rem;
      padding: 0.15rem 0.5rem;
      border-radius: 4px;
      font-weight: 600;
    }

    /* 通常バッジカラー設定 */
    .badge-protein { background-color: rgba(59, 130, 246, 0.15); color: var(--accent-protein); }
    .badge-vit-b { background-color: rgba(139, 92, 246, 0.15); color: var(--accent-vitamin-b); }
    .badge-sugar { background-color: rgba(236, 72, 153, 0.15); color: var(--accent-sugar); }
    .badge-lethal { background-color: rgba(153, 27, 27, 0.25); color: #FCA5A5; border: 1px solid rgba(239, 68, 68, 0.3); }
    .badge-hallu { background-color: rgba(139, 92, 246, 0.15); color: var(--accent-hallu); }
    .badge-fatigue { background-color: rgba(217, 119, 6, 0.15); color: var(--accent-fatigue); }

    /* 【目立つ設定】ビタミンD & ビタミンE 特有スタイル */
    .badge-vit-d {
      background: linear-gradient(135deg, rgba(245, 158, 11, 0.3), rgba(217, 119, 6, 0.15));
      color: #FBBF24;
      border: 1px solid rgba(245, 158, 11, 0.6);
      box-shadow: 0 0 8px rgba(245, 158, 11, 0.25);
      font-weight: 700;
      letter-spacing: 0.02em;
    }

    .badge-vit-e {
      background: linear-gradient(135deg, rgba(16, 185, 129, 0.3), rgba(5, 150, 105, 0.15));
      color: #34D399;
      border: 1px solid rgba(16, 185, 129, 0.6);
      box-shadow: 0 0 8px rgba(16, 185, 129, 0.25);
      font-weight: 700;
      letter-spacing: 0.02em;
    }
  </style>
</head>
<body>

  <div class="container">
    <h1>キノコ（Mushrooms）</h1>
    <p class="description">
      キノコは、森林や山岳地帯で時折見つかる子実体です。森を探索していてしばらく何も食べていないときなどは、地面のキノコに気を配っておくのが腹を満たす良い手段になります。ただし、すべてのキノコが安全に食べられるわけではなく、食べてしまうと極度の疲労や衰弱、あるいは死に至ることもあります。
    </p>

    <!-- 食用キノコセクション -->
    <h2 class="section-title edible">食用キノコ（Edible mushrooms）</h2>
    <p class="section-desc">安全に食べることができるキノコの一覧です。</p>
    
    <div class="grid">
      <div class="card">
        <img class="card-img" src="https://static.wikia.nocookie.net/scum_gamepedia_en/images/d/db/Agaricus_Augustus.png/revision/latest/scale-to-width-down/92?cb=20220808050528" alt="アガリクス属の担子菌類">
        <div class="card-content">
          <div class="jp-name">アガリクス属の担子菌類</div>
          <div class="en-name">Agaricus Augustus</div>
          <div class="badge-container"></div>
        </div>
      </div>

      <div class="card">
        <img class="card-img" src="https://static.wikia.nocookie.net/scum_gamepedia_en/images/3/36/Armillaria_Mellea.png/revision/latest/scale-to-width-down/92?cb=20221125022631" alt="ナラタケ">
        <div class="card-content">
          <div class="jp-name">ナラタケ</div>
          <div class="en-name">Armillaria Mellea</div>
          <div class="badge-container">
            <span class="badge badge-vit-b">ビタミンB群</span>
          </div>
        </div>
      </div>

      <div class="card">
        <img class="card-img" src="https://static.wikia.nocookie.net/scum_gamepedia_en/images/e/e0/Cantharellus_Cibarius.png/revision/latest/scale-to-width-down/92?cb=20220808051029" alt="アンズタケ">
        <div class="card-content">
          <div class="jp-name">アンズタケ</div>
          <div class="en-name">Cantharellus Cibarius</div>
          <div class="badge-container">
            <span class="badge badge-vit-d">★ ビタミンD</span>
          </div>
        </div>
      </div>

      <div class="card">
        <img class="card-img" src="https://static.wikia.nocookie.net/scum_gamepedia_en/images/9/98/Lepiota_Procera.png/revision/latest/scale-to-width-down/92?cb=20220808051614" alt="カラカサタケ">
        <div class="card-content">
          <div class="jp-name">カラカサタケ</div>
          <div class="en-name">Lepiota Procera</div>
          <div class="badge-container"></div>
        </div>
      </div>

      <div class="card">
        <img class="card-img" src="https://static.wikia.nocookie.net/scum_gamepedia_en/images/8/88/Agaricus_Campestris.png/revision/latest/scale-to-width-down/92?cb=20220808050538" alt="ハラタケ">
        <div class="card-content">
          <div class="jp-name">ハラタケ</div>
          <div class="en-name">Agaricus Campestris</div>
          <div class="badge-container"></div>
        </div>
      </div>

      <div class="card">
        <img class="card-img" src="https://static.wikia.nocookie.net/scum_gamepedia_en/images/3/3e/Boletus_Edilus.png/revision/latest?cb=20180906232702" alt="ヤマドリタケ">
        <div class="card-content">
          <div class="jp-name">ヤマドリタケ</div>
          <div class="en-name">Boletus Edulis</div>
          <div class="badge-container">
            <span class="badge badge-vit-e">★ ビタミンE</span>
          </div>
        </div>
      </div>

      <div class="card">
        <img class="card-img" src="https://static.wikia.nocookie.net/scum_gamepedia_en/images/4/4e/Coprinus_Comatus.png/revision/latest/scale-to-width-down/92?cb=20220808051214" alt="ササクレヒトヨタケ">
        <div class="card-content">
          <div class="jp-name">ササクレヒトヨタケ</div>
          <div class="en-name">Coprinus Comatus</div>
          <div class="badge-container"></div>
        </div>
      </div>

      <div class="card">
        <img class="card-img" src="https://static.wikia.nocookie.net/scum_gamepedia_en/images/c/c9/Lycoperdon_Gigantea.png/revision/latest/scale-to-width-down/92?cb=20220808051629" alt="ジャイアント・パフボール">
        <div class="card-content">
          <div class="jp-name">ジャイアント・パフボール</div>
          <div class="en-name">Lycoperdon Gigantea</div>
          <div class="badge-container">
            <span class="badge badge-protein">タンパク質</span>
            <span class="badge badge-sugar">糖分</span>
          </div>
        </div>
      </div>
    </div>

    <!-- 毒キノコセクション -->
    <h2 class="section-title poisonous">毒キノコ（Poisonous mushrooms）</h2>
    <p class="section-desc">摂取すると害を及ぼしたり、様々な症状を引き起こすキノコの一覧です。</p>

    <div class="grid">
      <div class="card">
        <img class="card-img" src="https://static.wikia.nocookie.net/scum_gamepedia_en/images/4/42/Amantia_Pantherina.png/revision/latest/scale-to-width-down/62?cb=20221014171539" alt="イボテングタケ">
        <div class="card-content">
          <div class="jp-name">イボテングタケ</div>
          <div class="en-name">Amanita Pantheria</div>
          <div class="badge-container">
            <span class="badge badge-hallu">幻覚・錯乱・行動不能</span>
          </div>
        </div>
      </div>

      <div class="card">
        <img class="card-img" src="https://static.wikia.nocookie.net/scum_gamepedia_en/images/d/db/Amantia_Muscaria.png/revision/latest/scale-to-width-down/68?cb=20221014171557" alt="ベニテングタケ">
        <div class="card-content">
          <div class="jp-name">ベニテングタケ</div>
          <div class="en-name">Amanita Muscaria</div>
          <div class="badge-container">
            <span class="badge badge-hallu">幻覚・錯乱・行動不能</span>
          </div>
        </div>
      </div>

      <div class="card">
        <img class="card-img" src="https://static.wikia.nocookie.net/scum_gamepedia_en/images/d/d2/Amantia_Virosa.png/revision/latest/scale-to-width-down/73?cb=20221014171618" alt="ドクツルタケ">
        <div class="card-content">
          <div class="jp-name">ドクツルタケ</div>
          <div class="en-name">Amanita Virosa</div>
          <div class="badge-container">
            <span class="badge badge-lethal">致死性</span>
          </div>
        </div>
      </div>

      <div class="card">
        <img class="card-img" src="https://static.wikia.nocookie.net/scum_gamepedia_en/images/c/c8/Amantia_Phalloides.png/revision/latest/scale-to-width-down/78?cb=20221014171608" alt="タマゴテングタケ">
        <div class="card-content">
          <div class="jp-name">タマゴテングタケ</div>
          <div class="en-name">Amanita Phalloides</div>
          <div class="badge-container">
            <span class="badge badge-lethal">致死性</span>
          </div>
        </div>
      </div>

      <div class="card">
        <img class="card-img" src="https://static.wikia.nocookie.net/scum_gamepedia_en/images/e/e7/Psilocybe_Cyanescens.png/revision/latest/scale-to-width-down/92?cb=20221014171640" alt="シビレタケ属の一種">
        <div class="card-content">
          <div class="jp-name">シビレタケ属の一種</div>
          <div class="en-name">Psilocybe Cyanescens</div>
          <div class="badge-container">
            <span class="badge badge-fatigue">幻覚・疲労</span>
          </div>
        </div>
      </div>
    </div>
  </div>

</body>
</html>
