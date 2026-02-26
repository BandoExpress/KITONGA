<!DOCTYPE html>
<html lang="sw">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bando Express - Mzigo wa Kutosha</title>
<link href="https://fonts.googleapis.com/css2?family=Black+Han+Sans&family=Nunito:wght@400;700;900&display=swap" rel="stylesheet">
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: #0a0a0a;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    font-family: 'Nunito', sans-serif;
  }

  .flyer {
    width: 480px;
    background: #0d1b2a;
    border-radius: 24px;
    overflow: hidden;
    position: relative;
    box-shadow: 0 0 60px rgba(0,200,255,0.2), 0 0 120px rgba(255,80,0,0.1);
  }

  /* Animated BG */
  .flyer::before {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(ellipse at 20% 10%, rgba(0,200,255,0.12) 0%, transparent 60%),
                radial-gradient(ellipse at 80% 90%, rgba(255,100,0,0.12) 0%, transparent 60%);
    z-index: 0;
  }

  .content { position: relative; z-index: 1; }

  /* Header */
  .header {
    background: linear-gradient(135deg, #ff6a00, #ee0979);
    padding: 28px 24px 20px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .header::after {
    content: '';
    position: absolute;
    bottom: -16px; left: 0; right: 0;
    height: 32px;
    background: #0d1b2a;
    border-radius: 50% 50% 0 0 / 100% 100% 0 0;
  }

  .brand {
    font-family: 'Black Han Sans', sans-serif;
    font-size: 42px;
    color: #fff;
    letter-spacing: 2px;
    text-shadow: 0 4px 20px rgba(0,0,0,0.3);
    animation: pulse 2s ease-in-out infinite;
  }
  @keyframes pulse {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.03); }
  }

  .tagline {
    font-size: 13px;
    color: rgba(255,255,255,0.9);
    font-weight: 700;
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-top: 4px;
  }

  /* Announcement Banner */
  .announcement {
    margin: 32px 20px 0;
    background: linear-gradient(135deg, rgba(0,200,255,0.15), rgba(0,200,255,0.05));
    border: 1.5px solid rgba(0,200,255,0.4);
    border-radius: 14px;
    padding: 14px 18px;
    text-align: center;
  }
  .announcement .main-text {
    color: #00c8ff;
    font-size: 17px;
    font-weight: 900;
    text-transform: uppercase;
    letter-spacing: 1px;
  }
  .announcement .sub-text {
    color: rgba(255,255,255,0.7);
    font-size: 13px;
    margin-top: 4px;
    font-weight: 700;
  }
  .highlight {
    color: #ff6a00;
    font-weight: 900;
  }

  /* Location badge */
  .location {
    margin: 12px 20px 0;
    background: linear-gradient(135deg, rgba(255,106,0,0.2), rgba(238,9,121,0.1));
    border: 1.5px solid rgba(255,106,0,0.4);
    border-radius: 10px;
    padding: 10px 16px;
    text-align: center;
    color: #fff;
    font-size: 13px;
    font-weight: 700;
  }
  .location .loc-name {
    color: #ffb347;
    font-weight: 900;
    font-size: 14px;
  }

  /* Section title */
  .section-title {
    text-align: center;
    margin: 20px 0 12px;
    color: #fff;
    font-size: 11px;
    font-weight: 900;
    letter-spacing: 4px;
    text-transform: uppercase;
    opacity: 0.5;
  }

  /* Plans grid */
  .plans {
    padding: 0 20px 12px;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
  }

  .plan {
    background: rgba(255,255,255,0.04);
    border: 1px solid rgba(255,255,255,0.08);
    border-radius: 14px;
    padding: 14px 12px;
    position: relative;
    transition: transform 0.2s, border-color 0.2s;
    cursor: default;
    overflow: hidden;
  }
  .plan:hover {
    transform: translateY(-3px);
    border-color: rgba(0,200,255,0.4);
  }
  .plan::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 3px;
    background: linear-gradient(90deg, #ff6a00, #ee0979);
    opacity: 0;
    transition: opacity 0.2s;
  }
  .plan:hover::before { opacity: 1; }

  .plan.popular {
    border-color: rgba(0,200,255,0.5);
    background: rgba(0,200,255,0.07);
  }
  .plan.popular::before { opacity: 1; background: linear-gradient(90deg, #00c8ff, #0080ff); }

  .popular-badge {
    position: absolute;
    top: 8px; right: 8px;
    background: #00c8ff;
    color: #000;
    font-size: 9px;
    font-weight: 900;
    letter-spacing: 1px;
    padding: 2px 7px;
    border-radius: 20px;
  }

  .plan-data {
    font-family: 'Black Han Sans', sans-serif;
    font-size: 30px;
    color: #fff;
    line-height: 1;
  }
  .plan-data span {
    font-family: 'Nunito', sans-serif;
    font-size: 14px;
    color: rgba(255,255,255,0.5);
    font-weight: 700;
  }

  .plan-price {
    margin-top: 8px;
    color: #ffb347;
    font-size: 15px;
    font-weight: 900;
  }
  .plan-price small {
    color: rgba(255,255,255,0.4);
    font-size: 11px;
    font-weight: 700;
  }

  /* CTA */
  .cta {
    margin: 8px 20px 20px;
    background: linear-gradient(135deg, #ff6a00, #ee0979);
    border-radius: 16px;
    padding: 18px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .cta::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(255,255,255,0.1), transparent);
  }
  .cta-label {
    color: rgba(255,255,255,0.85);
    font-size: 11px;
    font-weight: 900;
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 8px;
  }
  .cta-phones {
    display: flex;
    gap: 10px;
    justify-content: center;
  }
  .phone-number {
    background: rgba(255,255,255,0.2);
    border: 1px solid rgba(255,255,255,0.3);
    border-radius: 8px;
    padding: 8px 14px;
    color: #fff;
    font-size: 16px;
    font-weight: 900;
    letter-spacing: 1px;
    backdrop-filter: blur(4px);
  }
</style>
</head>
<body>
<div class="flyer">
  <div class="content">
    <!-- Header -->
    <div class="header">
      <div class="brand">BANDO EXPRESS</div>
      <div class="tagline">Bei Kitonga • Halotel Pekee</div>
    </div>

    <!-- Announcement -->
    <div class="announcement">
      <div class="main-text">🚀 Mzigo Upo wa Kutosha!</div>
      <div class="sub-text">Bei <span class="highlight">bora zaidi</span> kwa mtandao wa <span class="highlight">Halotel</span></div>
    </div>

    <!-- Location -->
    <div class="location">
      📍 Mzigo Umefika Mtaani Kwako — <span class="loc-name">Ruaha Kilombero</span>
    </div>

    <div class="section-title">Chagua Pakiti Yako</div>

    <!-- Plans -->
    <div class="plans">
      <div class="plan">
        <div class="plan-data">5 <span>GB</span></div>
        <div class="plan-price">5,000 TZS <small>/ mwezi</small></div>
      </div>
      <div class="plan">
        <div class="plan-data">10 <span>GB</span></div>
        <div class="plan-price">10,000 TZS <small>/ mwezi</small></div>
      </div>
      <div class="plan popular">
        <div class="popular-badge">MAARUFU</div>
        <div class="plan-data">18 <span>GB</span></div>
        <div class="plan-price">15,000 TZS <small>/ mwezi</small></div>
      </div>
      <div class="plan">
        <div class="plan-data">22 <span>GB</span></div>
        <div class="plan-price">20,000 TZS <small>/ mwezi</small></div>
      </div>
      <div class="plan">
        <div class="plan-data">25 <span>GB</span></div>
        <div class="plan-price">23,000 TZS <small>/ mwezi</small></div>
      </div>
      <div class="plan">
        <div class="plan-data">30 <span>GB</span></div>
        <div class="plan-price">26,000 TZS <small>/ mwezi</small></div>
      </div>
      <div class="plan">
        <div class="plan-data">35 <span>GB</span></div>
        <div class="plan-price">34,000 TZS <small>/ mwezi</small></div>
      </div>
      <div class="plan">
        <div class="plan-data">40 <span>GB</span></div>
        <div class="plan-price">39,000 TZS <small>/ mwezi</small></div>
      </div>
      <div class="plan popular">
        <div class="popular-badge">BORA</div>
        <div class="plan-data">50 <span>GB</span></div>
        <div class="plan-price">45,000 TZS <small>/ mwezi</small></div>
      </div>
      <div class="plan">
        <div class="plan-data">60 <span>GB</span></div>
        <div class="plan-price">55,000 TZS <small>/ mwezi</small></div>
      </div>
    </div>

    <!-- CTA -->
    <div class="cta">
      <div class="cta-label">📞 Piga Simu Sasa</div>
      <div class="cta-phones">
        <div class="phone-number">0714 928 111</div>
        <div class="phone-number">0735 928 111</div>
      </div>
    </div>
  </div>
</div>
</body>
</html>
