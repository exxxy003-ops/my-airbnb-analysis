---
layout: splash
title: "NYC Airbnb Data Dashboard"
permalink: /dashboard/
---

<style>
  .db-hero {
    background: linear-gradient(135deg, #0d1117 0%, #161b22 100%);
    border-bottom: 1px solid #30363d;
    padding: 48px 32px 40px;
    margin: -32px -32px 40px;
    text-align: center;
  }
  .db-hero h1 {
    font-size: clamp(1.6rem, 4vw, 2.4rem);
    font-weight: 700;
    color: #f0f6fc;
    margin-bottom: 10px;
    letter-spacing: -0.02em;
  }
  .db-hero p {
    color: #8b949e;
    font-size: 1rem;
    max-width: 600px;
    margin: 0 auto;
  }

  .db-section {
    margin-bottom: 48px;
  }
  .db-section-title {
    font-size: 0.75rem;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: #8b949e;
    border-bottom: 1px solid #21262d;
    padding-bottom: 8px;
    margin-bottom: 20px;
  }

  .stat-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
    gap: 16px;
    margin-bottom: 40px;
  }
  .stat-card {
    background: #161b22;
    border: 1px solid #30363d;
    border-radius: 8px;
    padding: 20px 24px;
    text-align: center;
  }
  .stat-card .stat-value {
    font-size: 2rem;
    font-weight: 700;
    color: #58a6ff;
    line-height: 1;
    margin-bottom: 6px;
  }
  .stat-card .stat-label {
    font-size: 0.78rem;
    color: #8b949e;
    text-transform: uppercase;
    letter-spacing: 0.06em;
  }

  .map-wrap {
    border: 1px solid #30363d;
    border-radius: 10px;
    overflow: hidden;
    background: #0d1117;
  }
  .map-wrap iframe {
    display: block;
    width: 100%;
    height: 580px;
    border: none;
  }

  .chart-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
  }
  @media (max-width: 700px) {
    .chart-grid { grid-template-columns: 1fr; }
  }
  .chart-card {
    background: #161b22;
    border: 1px solid #30363d;
    border-radius: 8px;
    overflow: hidden;
  }
  .chart-card iframe {
    display: block;
    width: 100%;
    height: 320px;
    border: none;
    background: #161b22;
  }
  .chart-card-full {
    background: #161b22;
    border: 1px solid #30363d;
    border-radius: 8px;
    overflow: hidden;
  }
  .chart-card-full iframe {
    display: block;
    width: 100%;
    height: 360px;
    border: none;
    background: #161b22;
  }
</style>

<div class="db-hero">
  <h1>NYC Airbnb Distribution Analysis</h1>
  <p>Geographic intelligence across 35,000+ listings — explore neighbourhood clusters, pricing patterns, and hosting trends across New York City.</p>
</div>

<!-- Stats row -->
<div class="stat-grid">
  <div class="stat-card">
    <div class="stat-value">35,994</div>
    <div class="stat-label">Total Listings</div>
  </div>
  <div class="stat-card">
    <div class="stat-value">79</div>
    <div class="stat-label">Neighbourhoods</div>
  </div>
  <div class="stat-card">
    <div class="stat-value">5</div>
    <div class="stat-label">Market Clusters</div>
  </div>
  <div class="stat-card">
    <div class="stat-value">$141</div>
    <div class="stat-label">Median Nightly Price</div>
  </div>
</div>

<!-- Interactive map -->
<div class="db-section">
  <div class="db-section-title">Geographic Distribution</div>
  <div class="map-wrap">
    <iframe src="/charts/dashboard_map.html" title="NYC Airbnb Distribution Map"></iframe>
  </div>
</div>

<!-- Secondary charts -->
<div class="db-section">
  <div class="db-section-title">Hosting Trends</div>
  <div class="chart-grid">
    <div class="chart-card">
      <iframe src="/charts/hvplot_host_year.html" title="Listings by Host Year"></iframe>
    </div>
    <div class="chart-card">
      <iframe src="/charts/hvplot_response_time.html" title="Host Response Time"></iframe>
    </div>
  </div>
</div>

<div class="db-section">
  <div class="db-section-title">Host Verification &amp; Booking Behavior</div>
  <div class="chart-grid">
    <div class="chart-card">
      <iframe src="/charts/hvplot_host_identity.html" title="Host Identity Verification"></iframe>
    </div>
    <div class="chart-card">
      <iframe src="/charts/hvplot_instant_bookable.html" title="Instant Bookable Listings"></iframe>
    </div>
  </div>
</div>

<!-- Model insights -->
<div class="db-section">
  <div class="db-section-title">Price Prediction — Feature Importance</div>
  <div class="chart-card-full">
    <iframe src="/charts/importance_bar.html" title="Random Forest Feature Importance"></iframe>
  </div>
</div>
