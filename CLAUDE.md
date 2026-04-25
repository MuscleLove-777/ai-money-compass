# AIマネー羅針盤 - スケジュールエージェントガイド

このリポジトリは **AI×自動化で資産形成** を支援する `AIマネー羅針盤` の本体です。
あなた（スケジュールエージェント）は毎日JST 09:31に起動し、最新マネー情報をリサーチして記事を3本生成します。

## 1日のタスク

1. **リサーチ**: WebSearchで以下のトピックから **3件** の最新ネタ
   - 主要証券口座のキャンペーン・新NISA関連
   - ロボアドの実績推移・新サービス
   - 仮想通貨の規制動向・取引所キャンペーン
   - FX口座のスプレッド改定・スワップ動向
   - 家計簿アプリの新機能
   - 保険見直しの最新トレンド・節約事例
2. **画像選定**: Unsplash無料画像（クエリ例: `site:unsplash.com finance chart`, `site:unsplash.com money saving`, `site:unsplash.com investment laptop`）
3. **記事生成**: `articles/YYYY-MM-DD-<slug>.html`、本文1200-1800字、h2を2-3本
4. **index.html更新**: `<div class="blog-grid">` 内を最新6件、stat-articles更新
5. **sitemap.xml更新**: 新3本を追記
6. **IndexNow通知**: indexnow-key.txt の値で `https://api.indexnow.org/indexnow` へPOST
7. **git push**: `[auto] Add daily articles YYYY-MM-DD`

## 執筆ルール

- 日本語、信頼感ある中立トーン
- タイトル28-40字、数字・年・利率を入れる
- 投資・資産運用は **元本保証ではない旨** を末尾に毎回1行記載
- 「絶対儲かる」「楽して◯倍」等の誇張NG
- 金商法/景表法に抵触する断定的表現NG
- 個別銘柄推奨は控えめに、サービス比較中心
- 実在人物の写真NG、Unsplashのみ

## 記事HTMLテンプレート

`articles/YYYY-MM-DD-<slug>.html`:

```html
<!DOCTYPE html>
<html lang="ja"><head>
<meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>{{記事タイトル}} | AIマネー羅針盤</title>
<meta name="description" content="{{150字以内}}">
<link rel="canonical" href="https://musclelove-777.github.io/ai-money-compass/articles/{{slug}}.html">
<meta property="og:type" content="article"><meta property="og:title" content="{{タイトル}}">
<meta property="og:description" content="{{要約}}"><meta property="og:image" content="{{Unsplash}}">
<meta property="og:url" content="https://musclelove-777.github.io/ai-money-compass/articles/{{slug}}.html">
<meta name="twitter:card" content="summary_large_image"><meta name="twitter:image" content="{{Unsplash}}">
<script type="application/ld+json">{"@context":"https://schema.org","@type":"Article","headline":"{{タイトル}}","image":"{{Unsplash}}","datePublished":"{{YYYY-MM-DD}}","author":{"@type":"Organization","name":"AIマネー羅針盤"}}</script>
<link rel="stylesheet" href="../assets/style.css"></head><body>
<nav class="filter-nav"><a href="../index.html" class="filter-btn">← トップに戻る</a></nav>
<main class="article-body">
<img class="article-hero-img" src="{{Unsplash}}" alt="{{タイトル}}">
<p class="article-meta">📅 {{YYYY-MM-DD}} · 🏷️ {{カテゴリ}}</p>
<h1>{{タイトル}}</h1>
<p>{{リード文}}</p>
<h2>{{見出し1}}</h2><p>{{本文}}</p>
<h2>{{見出し2}}</h2><p>{{本文}}</p>
<h2>まとめ</h2><p>{{結論+CTA}}</p>
<p style="color:#6b7280;font-size:0.8rem;margin-top:40px;">※ 投資・運用は元本割れリスクがあります。利率・条件は変動するため最新情報は各社公式サイトをご確認ください。本記事は情報提供のみで投資勧誘ではありません。</p>
<a href="../index.html" class="back-link">← 他の記事を見る</a>
</main>
<footer class="site-footer"><div class="footer-inner">
<div class="footer-promo"><p class="promo-label">― Powered by MuscleLove ―</p>
<div class="footer-links">
<a href="https://x.com/MuscleGirlLove7" target="_blank" rel="noopener">𝕏 @MuscleGirlLove7</a>
<a href="https://www.patreon.com/MuscleLove" target="_blank" rel="noopener">💪 Patreon</a>
<a href="https://musclelove-777.github.io/ai-fukugyo-compass/" target="_blank" rel="noopener">🧭 AI副業コンパス</a>
<a href="https://musclelove-777.github.io/ai-tenshoku-compass/" target="_blank" rel="noopener">🚀 AI転職コンパス</a>
</div></div>
<p class="copyright">© 2026 AIマネー羅針盤</p></div></footer>
</body></html>
```

## index.html blog-grid 更新

最新6件カード（CLAUDE.mdの他姉妹サイトと同じ形式）。blog-emptyは新規記事追加時に削除。

## sitemap.xml 更新

```xml
<url>
  <loc>https://musclelove-777.github.io/ai-money-compass/articles/{{slug}}.html</loc>
  <lastmod>{{今日}}</lastmod>
  <changefreq>weekly</changefreq>
  <priority>0.8</priority>
</url>
```

## 守ること

- 毎日3本、タイトル重複NG
- 元本保証ではない旨末尾必須
- フッターのMuscleLove広告+姉妹3サイトリンクは全ページ必須
- pages.yml は変更しない
