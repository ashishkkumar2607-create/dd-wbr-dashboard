<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Double Dragon — Weekly Business Review</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=JetBrains+Mono:wght@400;500;700&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.min.js"></script>
<style>
:root {
  --bg-base:#080c12;--bg-panel:#0d1320;--bg-card:#111827;
  --border:rgba(255,255,255,0.06);--border-bright:rgba(255,255,255,0.12);
  --neon-green:#00ff9d;--neon-red:#ff3b5c;--neon-cyan:#00e5ff;
  --neon-purple:#b845ff;--neon-amber:#ffb800;--neon-blue:#4d9fff;
  --text-primary:#f0f4ff;--text-secondary:#8892a4;--text-muted:#4a5568;
  --font-display:'Syne',sans-serif;--font-mono:'JetBrains Mono',monospace;--font-body:'Inter',sans-serif;
  --glow-cyan:0 0 20px rgba(0,229,255,0.3);--radius:12px;--radius-sm:8px;
}
*{margin:0;padding:0;box-sizing:border-box;}
body{background:var(--bg-base);color:var(--text-primary);font-family:var(--font-body);min-height:100vh;overflow-x:hidden;}
body::before{content:'';position:fixed;inset:0;background-image:linear-gradient(rgba(0,229,255,0.03) 1px,transparent 1px),linear-gradient(90deg,rgba(0,229,255,0.03) 1px,transparent 1px);background-size:40px 40px;pointer-events:none;z-index:0;}
.wrapper{position:relative;z-index:1;}

.header{display:flex;align-items:center;justify-content:space-between;padding:18px 32px;border-bottom:1px solid var(--border);background:rgba(8,12,18,0.97);backdrop-filter:blur(20px);position:sticky;top:0;z-index:100;}
.logo{display:flex;align-items:center;gap:12px;}
.logo-icon{width:36px;height:36px;background:linear-gradient(135deg,var(--neon-cyan),var(--neon-purple));border-radius:8px;display:flex;align-items:center;justify-content:center;font-size:18px;box-shadow:var(--glow-cyan);}
.logo-text{font-family:var(--font-display);font-size:18px;font-weight:800;letter-spacing:-0.5px;}
.logo-text span{color:var(--neon-cyan);}
.header-center{display:flex;gap:4px;background:var(--bg-card);border:1px solid var(--border);border-radius:10px;padding:4px;}
.tab-btn{padding:8px 24px;border:none;background:transparent;color:var(--text-secondary);font-family:var(--font-display);font-size:13px;font-weight:600;cursor:pointer;border-radius:7px;transition:all .2s;letter-spacing:.5px;text-transform:uppercase;}
.tab-btn.active{background:linear-gradient(135deg,rgba(0,229,255,0.15),rgba(184,69,255,0.15));color:var(--neon-cyan);border:1px solid rgba(0,229,255,0.3);box-shadow:var(--glow-cyan);}
.header-right{display:flex;align-items:center;gap:16px;}
.refresh-btn{display:flex;align-items:center;gap:8px;padding:8px 16px;background:transparent;border:1px solid var(--border-bright);border-radius:var(--radius-sm);color:var(--text-secondary);font-family:var(--font-mono);font-size:12px;cursor:pointer;transition:all .2s;}
.refresh-btn:hover{border-color:var(--neon-cyan);color:var(--neon-cyan);}
.refresh-btn.spinning .ri{display:inline-block;animation:spin 1s linear infinite;}
@keyframes spin{to{transform:rotate(360deg);}}
.live-badge{display:flex;align-items:center;gap:6px;font-family:var(--font-mono);font-size:11px;color:var(--neon-green);}
.live-dot{width:7px;height:7px;background:var(--neon-green);border-radius:50%;animation:pulse 2s infinite;box-shadow:0 0 8px var(--neon-green);}
@keyframes pulse{0%,100%{opacity:1;transform:scale(1)}50%{opacity:.5;transform:scale(.8)}}

.loading-screen{position:fixed;inset:0;background:var(--bg-base);display:flex;flex-direction:column;align-items:center;justify-content:center;gap:20px;z-index:999;}
.loading-spinner{width:48px;height:48px;border:3px solid var(--border);border-top-color:var(--neon-cyan);border-radius:50%;animation:spin .8s linear infinite;}
.loading-text{font-family:var(--font-mono);font-size:13px;color:var(--text-secondary);}
.loading-sub{font-family:var(--font-mono);font-size:11px;color:var(--text-muted);}

.page{display:none;}.page.active{display:block;}
.layout{padding:28px 32px;max-width:1600px;margin:0 auto;}
.section-title{font-family:var(--font-display);font-size:12px;font-weight:700;text-transform:uppercase;letter-spacing:2px;color:var(--text-muted);margin-bottom:16px;display:flex;align-items:center;gap:10px;}
.section-title::after{content:'';flex:1;height:1px;background:var(--border);}

.week-banner{display:flex;align-items:center;justify-content:space-between;background:linear-gradient(135deg,rgba(0,229,255,0.05),rgba(184,69,255,0.05));border:1px solid rgba(0,229,255,0.15);border-radius:var(--radius);padding:16px 24px;margin-bottom:28px;}
.week-label{font-family:var(--font-mono);font-size:11px;color:var(--text-muted);text-transform:uppercase;letter-spacing:1px;margin-bottom:4px;}
.week-value{font-family:var(--font-display);font-size:22px;font-weight:700;color:var(--neon-cyan);}
.week-vs{font-family:var(--font-mono);font-size:11px;color:var(--text-secondary);margin-top:4px;}
.auto-badge{background:rgba(0,255,157,0.1);border:1px solid rgba(0,255,157,0.3);border-radius:6px;padding:6px 12px;font-family:var(--font-mono);font-size:11px;color:var(--neon-green);}

/* KPI CARDS — 7 per row */
.kpi-grid{display:grid;grid-template-columns:repeat(7,1fr);gap:14px;margin-bottom:28px;}
.kpi-card{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--radius);padding:18px;position:relative;overflow:hidden;transition:all .2s;}
.kpi-card::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:var(--accent,var(--neon-cyan));opacity:.7;}
.kpi-card:hover{border-color:var(--border-bright);transform:translateY(-2px);}
.kpi-label{font-family:var(--font-mono);font-size:10px;color:var(--text-muted);text-transform:uppercase;letter-spacing:1px;margin-bottom:10px;}
.kpi-value{font-family:var(--font-display);font-size:22px;font-weight:800;color:var(--text-primary);margin-bottom:8px;line-height:1;}
.kpi-wow{display:flex;align-items:center;gap:6px;font-family:var(--font-mono);font-size:11px;flex-wrap:wrap;}
.kpi-wow.up{color:var(--neon-green);}.kpi-wow.down{color:var(--neon-red);}.kpi-wow.flat{color:var(--text-muted);}
.kpi-breakdown{margin-top:10px;padding-top:10px;border-top:1px solid var(--border);display:flex;flex-direction:column;gap:5px;}
.kpi-breakdown-row{display:flex;justify-content:space-between;align-items:center;gap:4px;}
.kpi-breakdown-label{font-family:var(--font-mono);font-size:9px;color:var(--text-muted);}
.kpi-breakdown-val{font-family:var(--font-mono);font-size:10px;font-weight:700;}
.kpi-breakdown-wow{font-family:var(--font-mono);font-size:10px;}
.kpi-breakdown-wow.up{color:var(--neon-green);}.kpi-breakdown-wow.down{color:var(--neon-red);}

.charts-row{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-bottom:28px;}
.chart-card{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--radius);padding:20px;}
.chart-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:16px;}
.chart-title{font-family:var(--font-display);font-size:14px;font-weight:700;color:var(--text-primary);}
.chart-subtitle{font-family:var(--font-mono);font-size:10px;color:var(--text-muted);margin-top:2px;}
.chart-wrap{position:relative;height:200px;}

.category-grid{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-bottom:28px;}
.cat-table-card{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--radius);overflow:hidden;}
.cat-table-header{padding:16px 20px;border-bottom:1px solid var(--border);}
.cat-row{display:grid;grid-template-columns:1fr 100px 80px 80px;padding:12px 20px;border-bottom:1px solid var(--border);align-items:center;transition:background .15s;}
.cat-row:hover{background:rgba(255,255,255,0.02);}
.cat-row.hdr{background:rgba(0,0,0,0.2);}
.cat-row-name{font-size:13px;color:var(--text-primary);font-weight:500;}
.cat-row.hdr .cat-row-name,.cat-row.hdr .crv{font-family:var(--font-mono);font-size:10px;color:var(--text-muted);text-transform:uppercase;letter-spacing:.5px;font-weight:400;}
.crv{font-family:var(--font-mono);font-size:12px;text-align:right;}
.crw{font-family:var(--font-mono);font-size:11px;text-align:right;font-weight:700;}
.crw.up{color:var(--neon-green);}.crw.down{color:var(--neon-red);}.crw.flat{color:var(--text-muted);}

.donut-card{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--radius);overflow:hidden;display:flex;flex-direction:column;}
.donut-wrap{padding:16px;height:220px;position:relative;}
.donut-stats{border-top:1px solid var(--border);padding:16px 20px;display:grid;grid-template-columns:1fr 1fr;gap:10px;}
.donut-stat{display:flex;flex-direction:column;gap:3px;}
.donut-stat-label{font-family:var(--font-mono);font-size:9px;color:var(--text-muted);text-transform:uppercase;letter-spacing:.8px;}
.donut-stat-val{font-family:var(--font-display);font-size:15px;font-weight:700;}
.donut-stat-sub{font-family:var(--font-mono);font-size:9px;}
.donut-stat-sub.up{color:var(--neon-green);}.donut-stat-sub.down{color:var(--neon-red);}

.asin-card{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--radius);overflow:hidden;margin-bottom:28px;}
.asin-card-header{padding:16px 20px;border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between;}
.asin-filters{display:flex;gap:8px;}
.filter-btn{padding:5px 12px;background:transparent;border:1px solid var(--border);border-radius:6px;color:var(--text-secondary);font-family:var(--font-mono);font-size:10px;cursor:pointer;transition:all .15s;text-transform:uppercase;letter-spacing:.5px;}
.filter-btn.active,.filter-btn:hover{border-color:var(--neon-cyan);color:var(--neon-cyan);background:rgba(0,229,255,0.05);}
.asin-table{width:100%;border-collapse:collapse;}
.asin-table th{background:rgba(0,0,0,0.3);padding:10px 14px;text-align:left;font-family:var(--font-mono);font-size:10px;color:var(--text-muted);text-transform:uppercase;letter-spacing:.5px;border-bottom:1px solid var(--border);white-space:nowrap;}
.asin-table th:not(:first-child){text-align:right;}
.asin-table td{padding:11px 14px;border-bottom:1px solid rgba(255,255,255,0.03);vertical-align:middle;}
.asin-table tr:hover td{background:rgba(255,255,255,0.02);}
.asin-title{font-size:12px;color:var(--text-primary);max-width:220px;overflow:hidden;text-overflow:ellipsis;white-space:nowrap;}
.asin-code{font-family:var(--font-mono);font-size:10px;color:var(--neon-cyan);margin-top:2px;text-decoration:none;}
.asin-code:hover{text-decoration:underline;}
.cat-badge{display:inline-block;padding:2px 8px;background:rgba(0,229,255,0.08);border:1px solid rgba(0,229,255,0.15);border-radius:4px;font-family:var(--font-mono);font-size:9px;color:var(--neon-cyan);}
.tdr{text-align:right;font-family:var(--font-mono);font-size:12px;}
.wow-pill{display:inline-flex;align-items:center;gap:3px;padding:3px 8px;border-radius:4px;font-family:var(--font-mono);font-size:10px;font-weight:700;}
.wow-pill.up{background:rgba(0,255,157,0.1);color:var(--neon-green);}
.wow-pill.down{background:rgba(255,59,92,0.1);color:var(--neon-red);}
.wow-pill.flat{background:rgba(255,255,255,0.05);color:var(--text-muted);}

.insights-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;margin-bottom:28px;}
.insight-card{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--radius);padding:20px;position:relative;overflow:hidden;}
.insight-card::before{content:'';position:absolute;left:0;top:0;bottom:0;width:3px;background:var(--ic,var(--neon-cyan));}
.insight-type{display:flex;align-items:center;gap:8px;margin-bottom:10px;}
.insight-tag{font-family:var(--font-mono);font-size:9px;text-transform:uppercase;letter-spacing:1px;padding:2px 8px;border-radius:4px;font-weight:700;}
.insight-tag.win{background:rgba(0,255,157,0.1);color:var(--neon-green);}
.insight-tag.loss{background:rgba(255,59,92,0.1);color:var(--neon-red);}
.insight-tag.watch{background:rgba(255,184,0,0.1);color:var(--neon-amber);}
.insight-title{font-family:var(--font-display);font-size:14px;font-weight:700;margin-bottom:8px;line-height:1.3;}
.insight-body{font-size:12px;color:var(--text-secondary);line-height:1.7;}
.insight-body strong{color:var(--text-primary);}
.iwl{margin-top:8px;font-size:11px;line-height:1.6;}
.ilb{font-family:var(--font-mono);font-size:9px;text-transform:uppercase;letter-spacing:1px;color:var(--text-muted);display:block;margin-bottom:2px;}

.history-card{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--radius);overflow:hidden;margin-bottom:28px;}
.history-scroll{overflow-x:auto;}
.history-table{width:100%;border-collapse:collapse;min-width:900px;}
.history-table th{background:rgba(0,0,0,0.4);padding:10px 14px;font-family:var(--font-mono);font-size:10px;color:var(--text-muted);text-transform:uppercase;letter-spacing:.5px;white-space:nowrap;border-bottom:1px solid var(--border);}
.history-table th:not(:first-child){text-align:right;}
.history-table td{padding:9px 14px;border-bottom:1px solid rgba(255,255,255,0.03);font-family:var(--font-mono);font-size:11px;white-space:nowrap;}
.history-table td:not(:first-child){text-align:right;}
.history-table tr:hover td{background:rgba(255,255,255,0.02);}
.history-table tr.cur-wk td{background:rgba(0,229,255,0.04);}
.history-table tr.cur-wk td:first-child{border-left:2px solid var(--neon-cyan);padding-left:12px;color:var(--neon-cyan);font-weight:700;}

/* EU marketplace tabs */
.eu-mkt-tabs{display:flex;gap:8px;margin-bottom:24px;flex-wrap:wrap;}
.mkt-tab{padding:8px 20px;border:1px solid var(--border);border-radius:8px;background:transparent;color:var(--text-secondary);font-family:var(--font-display);font-size:12px;font-weight:700;cursor:pointer;transition:all .2s;text-transform:uppercase;letter-spacing:.5px;}
.mkt-tab.active{background:rgba(184,69,255,0.1);border-color:rgba(184,69,255,0.4);color:var(--neon-purple);box-shadow:0 0 16px rgba(184,69,255,0.2);}

.error-banner{background:rgba(255,59,92,0.1);border:1px solid rgba(255,59,92,0.3);border-radius:var(--radius);padding:16px 20px;margin-bottom:20px;font-family:var(--font-mono);font-size:12px;color:var(--neon-red);display:none;}
.no-data{padding:40px;text-align:center;color:var(--text-muted);font-family:var(--font-mono);font-size:13px;}

/* ADS */
.ads-summary-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:16px;margin-bottom:20px;}
.ads-kpi-card{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--radius);padding:18px;position:relative;overflow:hidden;transition:all .2s;}
.ads-kpi-card::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:var(--ac,var(--neon-cyan));opacity:.8;}
.ads-kpi-card:hover{border-color:var(--border-bright);transform:translateY(-1px);}
.ads-cat-card{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--radius);overflow:hidden;margin-bottom:28px;}
.ads-cat-header{padding:16px 20px;border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between;}
.ads-table{width:100%;border-collapse:collapse;}
.ads-table th{background:rgba(0,0,0,0.3);padding:10px 14px;text-align:left;font-family:var(--font-mono);font-size:10px;color:var(--text-muted);text-transform:uppercase;letter-spacing:.5px;border-bottom:1px solid var(--border);white-space:nowrap;}
.ads-table th:not(:first-child){text-align:right;}
.ads-table td{padding:11px 14px;border-bottom:1px solid rgba(255,255,255,0.03);vertical-align:middle;}
.ads-table td:not(:first-child){text-align:right;font-family:var(--font-mono);font-size:12px;}
.ads-table tr:hover td{background:rgba(255,255,255,0.02);}
.ads-chart-row{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-bottom:28px;}
.eff-badge{display:inline-flex;align-items:center;padding:2px 9px;border-radius:4px;font-family:var(--font-mono);font-size:10px;font-weight:700;}
.eff-badge.great{background:rgba(0,255,157,0.12);color:var(--neon-green);border:1px solid rgba(0,255,157,0.3);}
.eff-badge.ok{background:rgba(255,184,0,0.12);color:var(--neon-amber);border:1px solid rgba(255,184,0,0.3);}
.eff-badge.poor{background:rgba(255,59,92,0.12);color:var(--neon-red);border:1px solid rgba(255,59,92,0.3);}
.cat-name-cell{font-size:13px;color:var(--text-primary);font-weight:500;display:flex;align-items:center;gap:8px;}
.cat-dot{width:8px;height:8px;border-radius:50%;flex-shrink:0;}

/* SPLIT */
.split-row{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-bottom:28px;}
.split-card{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--radius);padding:20px;}
.split-title{font-family:var(--font-display);font-size:14px;font-weight:700;margin-bottom:4px;}
.split-sub{font-family:var(--font-mono);font-size:10px;color:var(--text-muted);margin-bottom:16px;}
.split-big{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:16px;}
.split-big-item{display:flex;flex-direction:column;gap:4px;}
.split-big-label{font-family:var(--font-mono);font-size:9px;color:var(--text-muted);text-transform:uppercase;letter-spacing:.8px;}
.split-big-val{font-family:var(--font-display);font-size:22px;font-weight:800;}
.split-big-sub{font-family:var(--font-mono);font-size:10px;}
.split-big-sub.up{color:var(--neon-green);}.split-big-sub.down{color:var(--neon-red);}.split-big-sub.flat{color:var(--text-muted);}
.split-bar-wrap{margin:4px 0 12px;}
.split-bar-label{display:flex;justify-content:space-between;font-family:var(--font-mono);font-size:9px;color:var(--text-muted);margin-bottom:6px;}
.split-bar-track{height:12px;background:rgba(255,255,255,0.04);border-radius:6px;overflow:hidden;display:flex;}
.split-bar-paid{background:linear-gradient(90deg,#ff3b5c,#ff7c2a);transition:width .6s ease;}
.split-bar-organic{background:linear-gradient(90deg,#00e5ff,#00ff9d);transition:width .6s ease;}
.split-legend{display:flex;gap:20px;margin-top:10px;}
.split-leg-item{display:flex;align-items:center;gap:6px;font-family:var(--font-mono);font-size:10px;color:var(--text-secondary);}
.split-leg-dot{width:8px;height:8px;border-radius:50%;}
.split-divider{height:1px;background:var(--border);margin:16px 0;}
.split-metrics-row{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;}
.split-metric{display:flex;flex-direction:column;gap:2px;}
.split-metric-label{font-family:var(--font-mono);font-size:9px;color:var(--text-muted);text-transform:uppercase;letter-spacing:.8px;}
.split-metric-val{font-family:var(--font-display);font-size:15px;font-weight:700;}
.split-metric-sub{font-family:var(--font-mono);font-size:9px;}
.split-metric-sub.up{color:var(--neon-green);}.split-metric-sub.down{color:var(--neon-red);}

/* INVENTORY */
.inv-section-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:16px;}
.inv-summary-pills{display:flex;gap:10px;}
.inv-pill{padding:4px 12px;border-radius:20px;font-family:var(--font-mono);font-size:10px;font-weight:700;}
.inv-pill.critical{background:rgba(255,59,92,0.15);color:var(--neon-red);border:1px solid rgba(255,59,92,0.3);}
.inv-pill.warning{background:rgba(255,184,0,0.15);color:var(--neon-amber);border:1px solid rgba(255,184,0,0.3);}
.inv-pill.healthy{background:rgba(0,255,157,0.1);color:var(--neon-green);border:1px solid rgba(0,255,157,0.25);}
.inv-filter-tabs{display:flex;gap:8px;margin-bottom:0;flex-wrap:wrap;}
.inv-tab{padding:6px 14px;border:1px solid var(--border);border-radius:6px;background:transparent;color:var(--text-secondary);font-family:var(--font-mono);font-size:10px;cursor:pointer;transition:all .15s;text-transform:uppercase;letter-spacing:.5px;}
.inv-tab.active,.inv-tab:hover{border-color:var(--neon-amber);color:var(--neon-amber);background:rgba(255,184,0,0.05);}
.inv-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(265px,1fr));gap:14px;margin-bottom:28px;}
.inv-card{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--radius);padding:16px;position:relative;overflow:hidden;transition:all .2s;}
.inv-card:hover{border-color:var(--border-bright);transform:translateY(-1px);}
.inv-card::before{content:'';position:absolute;left:0;top:0;bottom:0;width:3px;background:var(--ih,#4d9fff);}
.inv-card-top{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:10px;}
.inv-info{flex:1;min-width:0;}
.inv-asin-title{font-size:12px;color:var(--text-primary);font-weight:500;overflow:hidden;text-overflow:ellipsis;white-space:nowrap;margin-right:8px;}
.inv-asin-code{font-family:var(--font-mono);font-size:10px;color:var(--neon-cyan);margin-top:2px;}
.inv-health-badge{padding:3px 9px;border-radius:4px;font-family:var(--font-mono);font-size:9px;font-weight:700;white-space:nowrap;flex-shrink:0;}
.inv-health-badge.critical{background:rgba(255,59,92,0.15);color:var(--neon-red);border:1px solid rgba(255,59,92,0.3);}
.inv-health-badge.warning{background:rgba(255,184,0,0.15);color:var(--neon-amber);border:1px solid rgba(255,184,0,0.3);}
.inv-health-badge.healthy{background:rgba(0,255,157,0.1);color:var(--neon-green);border:1px solid rgba(0,255,157,0.25);}
.inv-health-badge.new{background:rgba(77,159,255,0.1);color:var(--neon-blue);border:1px solid rgba(77,159,255,0.25);}
.inv-metrics{display:grid;grid-template-columns:1fr 1fr 1fr;gap:8px;margin-top:10px;}
.inv-metric{display:flex;flex-direction:column;gap:2px;}
.inv-metric-label{font-family:var(--font-mono);font-size:9px;color:var(--text-muted);text-transform:uppercase;letter-spacing:.5px;}
.inv-metric-val{font-family:var(--font-mono);font-size:12px;font-weight:700;}
.inv-vel-wrap{margin-top:10px;}
.inv-vel-label{font-family:var(--font-mono);font-size:9px;color:var(--text-muted);margin-bottom:4px;display:flex;justify-content:space-between;}
.inv-vel-track{height:3px;background:rgba(255,255,255,0.06);border-radius:2px;overflow:hidden;}
.inv-vel-fill{height:3px;border-radius:2px;}

/* EU per-marketplace inventory accordion */
.eu-inv-section{margin-bottom:20px;}
.eu-inv-mkt-header{display:flex;align-items:center;justify-content:space-between;padding:12px 20px;background:var(--bg-card);border:1px solid var(--border);border-radius:var(--radius);cursor:pointer;margin-bottom:12px;transition:border-color .2s;}
.eu-inv-mkt-header:hover{border-color:var(--border-bright);}
.eu-inv-mkt-title{font-family:var(--font-display);font-size:14px;font-weight:700;}
.eu-inv-mkt-pills{display:flex;gap:8px;align-items:center;}

/* EU marketplace detail panels */
.eu-mkt-panel{display:none;}.eu-mkt-panel.active{display:block;}

::-webkit-scrollbar{width:6px;height:6px;}
::-webkit-scrollbar-track{background:transparent;}
::-webkit-scrollbar-thumb{background:var(--border-bright);border-radius:3px;}

@media(max-width:1400px){.kpi-grid{grid-template-columns:repeat(4,1fr);}}
@media(max-width:1200px){
  .kpi-grid{grid-template-columns:repeat(3,1fr);}
  .charts-row,.ads-chart-row,.split-row{grid-template-columns:1fr;}
  .insights-grid{grid-template-columns:1fr 1fr;}
  .ads-summary-grid{grid-template-columns:1fr 1fr;}
}
@media(max-width:768px){
  .header{padding:14px 16px;}.layout{padding:16px;}
  .kpi-grid,.ads-summary-grid{grid-template-columns:1fr 1fr;}
  .category-grid,.insights-grid{grid-template-columns:1fr;}
  .header-center{display:none;}
}
</style>
</head>
<body>

<div class="loading-screen" id="loadingScreen">
  <div class="loading-spinner"></div>
  <div class="loading-text">Fetching live data...</div>
  <div class="loading-sub" id="loadingStatus">Connecting to Google Sheets</div>
</div>

<div class="wrapper">
  <header class="header">
    <div class="logo">
      <div class="logo-icon">🐉</div>
      <div class="logo-text">Double Dragon <span>WBR</span></div>
    </div>
    <div class="header-center">
      <button class="tab-btn active" onclick="showPage('uk',event)">🇬🇧 UK</button>
      <button class="tab-btn" onclick="showPage('eu',event)">🇪🇺 EU</button>
    </div>
    <div class="header-right">
      <button class="refresh-btn" id="refreshBtn" onclick="refreshData()">
        <span class="ri" id="refreshIcon">↻</span>
        <span id="refreshLabel">Refresh</span>
      </button>
      <div class="live-badge"><div class="live-dot"></div><span id="lastUpdated">Live</span></div>
    </div>
  </header>

  <!-- UK PAGE -->
  <div class="page active" id="page-uk">
    <div class="layout">
      <div class="error-banner" id="ukError"></div>
      <div class="week-banner">
        <div>
          <div class="week-label">Current Week</div>
          <div class="week-value" id="ukCurrentWeek">—</div>
          <div class="week-vs" id="ukVsWeek">vs —</div>
        </div>
        <div style="text-align:center">
          <div class="week-label">Channel</div>
          <div style="font-family:var(--font-display);font-size:16px;font-weight:700;color:var(--neon-amber)">UK Retail + Business</div>
        </div>
        <div class="auto-badge">⚡ Auto-detecting latest week</div>
      </div>

      <div class="section-title">Performance KPIs — Consolidated</div>
      <div class="kpi-grid" id="ukKpiGrid"></div>

      <div class="section-title">📊 Weekly Intelligence — What · Why · How</div>
      <div class="insights-grid" id="ukInsights"></div>

      <div class="section-title">Trend Analysis — Last 12 Weeks</div>
      <div class="charts-row">
        <div class="chart-card">
          <div class="chart-header"><div><div class="chart-title">GMV Trend</div><div class="chart-subtitle">Retail + Business · £GBP</div></div></div>
          <div class="chart-wrap"><canvas id="ukGmvChart"></canvas></div>
        </div>
        <div class="chart-card">
          <div class="chart-header"><div><div class="chart-title">Ad Spend vs Ad Sales</div><div class="chart-subtitle">Weekly trend · £GBP</div></div></div>
          <div class="chart-wrap"><canvas id="ukAdsChart"></canvas></div>
        </div>
      </div>

      <div class="section-title">Category Performance</div>
      <div class="category-grid">
        <div class="cat-table-card">
          <div class="cat-table-header"><div class="chart-title">GMV by Category</div></div>
          <div class="cat-row hdr"><div class="cat-row-name">Category</div><div class="crv">GMV</div><div class="crv">Units</div><div class="crw">WoW</div></div>
          <div id="ukCatRows"></div>
        </div>
        <div class="donut-card">
          <div class="cat-table-header"><div class="chart-title">Category Split</div></div>
          <div class="donut-wrap"><canvas id="ukCatChart"></canvas></div>
          <div class="donut-stats" id="ukDonutStats"></div>
        </div>
      </div>

      <div class="section-title">💰 Ads Performance — Category Level</div>
      <div class="ads-summary-grid" id="ukAdsSummary"></div>
      <div class="ads-cat-card">
        <div class="ads-cat-header">
          <div class="chart-title">Category Ad Breakdown — Spend · Sales · ACOS · ROAS · WoW</div>
          <div style="font-family:var(--font-mono);font-size:10px;color:var(--text-muted)">Sorted by Ad Spend ↓</div>
        </div>
        <div style="overflow-x:auto">
          <table class="ads-table">
            <thead><tr>
              <th>Category</th>
              <th>Ad Spend</th><th>WoW Spend</th>
              <th>Ad Sales</th><th>WoW Sales</th>
              <th>ACOS</th><th>ROAS</th>
              <th>TACOS</th><th>Total GMV</th>
              <th>Efficiency</th>
            </tr></thead>
            <tbody id="ukAdsBody"></tbody>
          </table>
        </div>
      </div>
      <div class="ads-chart-row">
        <div class="chart-card">
          <div class="chart-header"><div><div class="chart-title">Ad Spend by Category</div><div class="chart-subtitle">Current week · £GBP</div></div></div>
          <div class="chart-wrap"><canvas id="ukAdsSpendChart"></canvas></div>
        </div>
        <div class="chart-card">
          <div class="chart-header"><div><div class="chart-title">ACOS by Category</div><div class="chart-subtitle">Lower is better · target &lt;15%</div></div></div>
          <div class="chart-wrap"><canvas id="ukAcosChart"></canvas></div>
        </div>
      </div>

      <div class="section-title">🔀 Organic vs Paid Sales Split</div>
      <div class="split-row">
        <div class="split-card" id="ukSplitCard"></div>
        <div class="chart-card">
          <div class="chart-header"><div><div class="chart-title">Paid vs Organic — 12 Week Trend</div><div class="chart-subtitle">Ad Sales vs estimated organic GMV</div></div></div>
          <div class="chart-wrap"><canvas id="ukSplitChart"></canvas></div>
        </div>
      </div>

      <div class="section-title">📦 Inventory Health — Velocity &amp; Risk Monitor</div>
      <div class="inv-section-header">
        <div class="inv-filter-tabs">
          <button class="inv-tab active" onclick="filterInv('all','uk',this)">All ASINs</button>
          <button class="inv-tab" onclick="filterInv('critical','uk',this)">🔴 Critical (&lt;2 wks)</button>
          <button class="inv-tab" onclick="filterInv('warning','uk',this)">🟡 Warning (2–4 wks)</button>
          <button class="inv-tab" onclick="filterInv('healthy','uk',this)">🟢 Healthy (&gt;4 wks)</button>
        </div>
        <div class="inv-summary-pills" id="ukInvPills"></div>
      </div>
      <div class="inv-grid" id="ukInvGrid"></div>

      <div class="section-title">ASIN Performance</div>
      <div class="asin-card">
        <div class="asin-card-header">
          <div class="chart-title">Product Detail — Current Week</div>
          <div class="asin-filters">
            <button class="filter-btn active" onclick="filterAsins('all','uk',this)">All</button>
            <button class="filter-btn" onclick="filterAsins('winners','uk',this)">↑ Winners</button>
            <button class="filter-btn" onclick="filterAsins('losers','uk',this)">↓ Losers</button>
            <button class="filter-btn" onclick="filterAsins('hero','uk',this)">⭐ Hero</button>
          </div>
        </div>
        <div style="overflow-x:auto">
          <table class="asin-table">
            <thead><tr>
              <th>Product</th><th>Category</th>
              <th style="text-align:right">GMV</th><th style="text-align:right">Units</th>
              <th style="text-align:right">Traffic</th><th style="text-align:right">Conv%</th>
              <th style="text-align:right">Ad Spend</th><th style="text-align:right">TACOS</th>
              <th style="text-align:right">WoW GMV</th>
            </tr></thead>
            <tbody id="ukAsinBody"></tbody>
          </table>
        </div>
      </div>

      <div class="section-title">Full Weekly History — All Weeks Reference</div>
      <div class="history-card"><div class="history-scroll">
        <table class="history-table">
          <thead><tr><th>Week</th><th>GMV</th><th>Units</th><th>Traffic</th><th>Conv%</th><th>Ad Spend</th><th>Ad Sales</th><th>TACOS</th><th>WoW GMV</th></tr></thead>
          <tbody id="ukHistoryBody"></tbody>
        </table>
      </div></div>
    </div>
  </div>

  <!-- EU PAGE -->
  <div class="page" id="page-eu">
    <div class="layout">
      <div class="error-banner" id="euError"></div>
      <div class="week-banner" style="border-color:rgba(184,69,255,0.2);background:linear-gradient(135deg,rgba(184,69,255,0.05),rgba(0,229,255,0.05))">
        <div>
          <div class="week-label">Current Week</div>
          <div class="week-value" style="color:var(--neon-purple)" id="euCurrentWeek">—</div>
          <div class="week-vs" id="euVsWeek">vs —</div>
        </div>
        <div style="text-align:center">
          <div class="week-label">Markets</div>
          <div style="font-family:var(--font-display);font-size:16px;font-weight:700;color:var(--neon-purple)">DE · FR · IT · ES</div>
        </div>
        <div class="auto-badge" style="border-color:rgba(184,69,255,0.3);color:var(--neon-purple);background:rgba(184,69,255,0.08)">⚡ Auto-detecting latest week</div>
      </div>

      <div class="section-title">Combined EU KPIs</div>
      <div class="kpi-grid" id="euKpiGrid"></div>

      <div class="section-title">📊 EU Weekly Intelligence</div>
      <div class="insights-grid" id="euInsights"></div>

      <div class="section-title">Marketplace Breakdown</div>
      <div class="eu-mkt-tabs">
        <button class="mkt-tab active" onclick="showEuMkt('combined',this)">🌍 Combined</button>
        <button class="mkt-tab" onclick="showEuMkt('eu_de',this)">🇩🇪 Germany</button>
        <button class="mkt-tab" onclick="showEuMkt('eu_fr',this)">🇫🇷 France</button>
        <button class="mkt-tab" onclick="showEuMkt('eu_it',this)">🇮🇹 Italy</button>
        <button class="mkt-tab" onclick="showEuMkt('eu_es',this)">🇪🇸 Spain</button>
      </div>

      <!-- Combined panel -->
      <div class="eu-mkt-panel active" id="euPanel_combined">
        <div class="charts-row">
          <div class="chart-card">
            <div class="chart-header"><div><div class="chart-title">GMV by Marketplace</div><div class="chart-subtitle">Current week · €EUR</div></div></div>
            <div class="chart-wrap"><canvas id="euMktChart"></canvas></div>
          </div>
          <div class="chart-card">
            <div class="chart-header"><div><div class="chart-title">EU GMV Trend — 12 Weeks</div><div class="chart-subtitle">All markets combined</div></div></div>
            <div class="chart-wrap"><canvas id="euTrendChart"></canvas></div>
          </div>
        </div>
        <div class="section-title">Category Performance — EU Combined</div>
        <div class="category-grid">
          <div class="cat-table-card">
            <div class="cat-table-header"><div class="chart-title">GMV by Category</div></div>
            <div class="cat-row hdr"><div class="cat-row-name">Category</div><div class="crv">GMV</div><div class="crv">Units</div><div class="crw">WoW</div></div>
            <div id="euCatRows"></div>
          </div>
          <div class="donut-card">
            <div class="cat-table-header"><div class="chart-title">Marketplace Split</div></div>
            <div class="donut-wrap"><canvas id="euPieChart"></canvas></div>
            <div class="donut-stats" id="euDonutStats"></div>
          </div>
        </div>
      </div>

      <!-- Per-marketplace panels (DE / FR / IT / ES) — rendered dynamically -->
      <div class="eu-mkt-panel" id="euPanel_eu_de"></div>
      <div class="eu-mkt-panel" id="euPanel_eu_fr"></div>
      <div class="eu-mkt-panel" id="euPanel_eu_it"></div>
      <div class="eu-mkt-panel" id="euPanel_eu_es"></div>

      <div class="section-title">💰 Ads Performance — Category Level</div>
      <div class="ads-summary-grid" id="euAdsSummary"></div>
      <div class="ads-cat-card">
        <div class="ads-cat-header">
          <div class="chart-title">Category Ad Breakdown — Spend · Sales · ACOS · ROAS · WoW</div>
          <div style="font-family:var(--font-mono);font-size:10px;color:var(--text-muted)">Sorted by Ad Spend ↓</div>
        </div>
        <div style="overflow-x:auto">
          <table class="ads-table">
            <thead><tr>
              <th>Category</th>
              <th>Ad Spend</th><th>WoW Spend</th>
              <th>Ad Sales</th><th>WoW Sales</th>
              <th>ACOS</th><th>ROAS</th>
              <th>TACOS</th><th>Total GMV</th>
              <th>Efficiency</th>
            </tr></thead>
            <tbody id="euAdsBody"></tbody>
          </table>
        </div>
      </div>
      <div class="ads-chart-row">
        <div class="chart-card">
          <div class="chart-header"><div><div class="chart-title">Ad Spend by Category</div><div class="chart-subtitle">Current week · €EUR</div></div></div>
          <div class="chart-wrap"><canvas id="euAdsSpendChart"></canvas></div>
        </div>
        <div class="chart-card">
          <div class="chart-header"><div><div class="chart-title">ACOS by Category</div><div class="chart-subtitle">Lower is better · target &lt;15%</div></div></div>
          <div class="chart-wrap"><canvas id="euAcosChart"></canvas></div>
        </div>
      </div>

      <div class="section-title">🔀 Organic vs Paid Sales Split</div>
      <div class="split-row">
        <div class="split-card" id="euSplitCard"></div>
        <div class="chart-card">
          <div class="chart-header"><div><div class="chart-title">Paid vs Organic — 12 Week Trend</div><div class="chart-subtitle">Ad Sales vs estimated organic GMV</div></div></div>
          <div class="chart-wrap"><canvas id="euSplitChart"></canvas></div>
        </div>
      </div>

      <div class="section-title">📦 Inventory Health — Per Marketplace</div>
      <div id="euInvPerMarket"></div>

      <div class="section-title">ASIN Performance — EU</div>
      <div class="asin-card">
        <div class="asin-card-header">
          <div class="chart-title">Product Detail — Current Week</div>
          <div class="asin-filters">
            <button class="filter-btn active" onclick="filterAsins('all','eu',this)">All</button>
            <button class="filter-btn" onclick="filterAsins('winners','eu',this)">↑ Winners</button>
            <button class="filter-btn" onclick="filterAsins('losers','eu',this)">↓ Losers</button>
            <button class="filter-btn" onclick="filterAsins('hero','eu',this)">⭐ Hero</button>
          </div>
        </div>
        <div style="overflow-x:auto">
          <table class="asin-table">
            <thead><tr>
              <th>Product</th><th>Category</th>
              <th style="text-align:right">GMV (€)</th><th style="text-align:right">Units</th>
              <th style="text-align:right">Traffic</th><th style="text-align:right">Conv%</th>
              <th style="text-align:right">Ad Spend</th><th style="text-align:right">TACOS</th>
              <th style="text-align:right">WoW GMV</th>
            </tr></thead>
            <tbody id="euAsinBody"></tbody>
          </table>
        </div>
      </div>

      <div class="section-title">Full Weekly History — EU Combined</div>
      <div class="history-card"><div class="history-scroll">
        <table class="history-table">
          <thead><tr><th>Week</th><th>GMV (€)</th><th>Units</th><th>Traffic</th><th>Conv%</th><th>Ad Spend</th><th>TACOS</th><th>WoW GMV</th></tr></thead>
          <tbody id="euHistoryBody"></tbody>
        </table>
      </div></div>
    </div>
  </div>
</div>

<script>
// ═══════════════════════════════════════════════════════
// CONFIG
// ═══════════════════════════════════════════════════════
const GAS_URL = 'https://script.google.com/macros/s/AKfycbztZ0jEhPR91V6fmytAKNxL7U9kTGcUCW6HwizuPRiDqqT6lGfnO_ocepFFOqJDy-ZH/exec';
const REFRESH_MS = 5 * 60 * 1000;
const SHEET_KEYS = ['uk_retail','uk_business','eu_de','eu_fr','eu_it','eu_es'];
const MKT_META = {
  eu_de:{label:'🇩🇪 Germany',color:'#00e5ff'},
  eu_fr:{label:'🇫🇷 France', color:'#00ff9d'},
  eu_it:{label:'🇮🇹 Italy',  color:'#b845ff'},
  eu_es:{label:'🇪🇸 Spain',  color:'#ffb800'}
};
const CAT_PALETTE = ['#00e5ff','#ff3b5c','#00ff9d','#ffb800','#b845ff','#ff7c2a','#4d9fff','#ff4db8','#39ffd6','#fff040','#7fff4f','#ff6b6b'];
const _catColorCache = {}; let _catColorIdx = 0;
function getCatColor(cat) {
  if (!_catColorCache[cat]) { _catColorCache[cat] = CAT_PALETTE[_catColorIdx % CAT_PALETTE.length]; _catColorIdx++; }
  return _catColorCache[cat];
}

let rawData = {}, ukAsins = [], euAsins = [], ukAllAsins = [], euAllAsins = [], charts = {};

// ═══════════════════════════════════════════════════════
// CSV PARSER
// ═══════════════════════════════════════════════════════
function parseCSV(text) {
  const lines = []; let row = [], cur = '', inQ = false;
  for (let i = 0; i < text.length; i++) {
    const c = text[i];
    if (c === '"') { if (inQ && text[i+1]==='"'){cur+='"';i++;}else inQ=!inQ; }
    else if (c===',' && !inQ){ row.push(cur.trim()); cur=''; }
    else if ((c==='\n'||c==='\r') && !inQ){
      if(c==='\r'&&text[i+1]==='\n')i++;
      row.push(cur.trim()); cur=''; lines.push(row); row=[];
    } else cur+=c;
  }
  if(cur||row.length){row.push(cur.trim());lines.push(row);}
  return lines;
}

function cleanNum(v) {
  if(v==null)return 0;
  const s=String(v).replace(/[£€$,\s]/g,'').replace('%','').trim();
  if(!s||s==='#DIV/0!'||s==='N/A'||s==='#VALUE!'||s==='#REF!'||s==='-')return 0;
  const n=parseFloat(s); return isNaN(n)?0:n;
}

// ═══════════════════════════════════════════════════════
// FORMATTERS
// ═══════════════════════════════════════════════════════
function fmt(n,pre='£'){
  if(n===0)return pre+'0';
  if(Math.abs(n)>=1000000)return pre+(n/1000000).toFixed(2)+'M';
  if(Math.abs(n)>=1000)return pre+(n/1000).toFixed(1)+'K';
  return pre+n.toFixed(0);
}
function fmtU(n){ if(n>=1000000)return(n/1000000).toFixed(2)+'M'; if(n>=1000)return(n/1000).toFixed(1)+'K'; return Math.round(n)+''; }
function pct(c,p){ return p?((c-p)/Math.abs(p))*100:0; }
function wCls(p){ return p>2?'up':p<-2?'down':'flat'; }
function wArr(p){ return p>2?'▲':p<-2?'▼':'—'; }
function fmtPct(p){ return (p>=0?'+':'')+p.toFixed(1)+'%'; }

// ═══════════════════════════════════════════════════════
// SHEET PARSER — header-driven column detection
// ═══════════════════════════════════════════════════════
const MONTH_RE = /\b(Jan|Feb|Mar|Apr|May|Jun|Jul|Aug|Sep|Oct|Nov|Dec)\b/i;

const COL_PATTERNS = {
  adSpend: /^ad[\s_-]?spend$|^spend$/i,
  adSales: /^ad[\s_-]?sales$|^ppc[\s_-]?sales$/i,
  units:   /^units[\s_-]?sold$|^units$|^qty$/i,
  gmv:     /^gmv$|^ordered[\s_-]?product[\s_-]?sales$|^revenue$|^total[\s_-]?sales$/i,
  asp:     /^asp$|^avg[\s_-]?price$|^average[\s_-]?price$/i,
  traffic: /^traffic$|^sessions$|^page[\s_-]?views$|^glance[\s_-]?views$|^detail[\s_-]?page[\s_-]?views$/i,
  conv:    /^conv[\w]*$|^cvr$|^unit[\s_-]?session[\s_-]?%?$|^conversion[\s_-]?rate$/i,
  tacos:   /^tacos$|^total[\s_-]?acos$/i,
};

const COL_PATTERNS_LOOSE = {
  adSpend: /ad.?spend|spend/i,
  adSales: /ad.?sales|ppc.?sales/i,
  units:   /units.?sold|units|qty/i,
  gmv:     /gmv|ordered.?product.?sales|revenue/i,
  asp:     /asp|avg.?price|average.?price/i,
  traffic: /^traffic$|^sessions$|glance.?view|detail.?page/i,
  conv:    /conv|cvr|unit.?session/i,
  tacos:   /tacos/i,
};

function findColsForWeek(headerRow, startCol, endCol) {
  const cols = {};
  const slice = headerRow.slice(startCol, endCol);
  for (const [metric, pattern] of Object.entries(COL_PATTERNS)) {
    let found = -1;
    for (let i = 0; i < slice.length; i++) {
      const h = String(slice[i]||'').trim();
      if (!h) continue;
      if (pattern.test(h)) {
        if (metric==='gmv' && /ad.?sales|ppc.?sales/i.test(h)) continue;
        if (metric==='traffic' && /ad|spend|sales|acos|tacos/i.test(h)) continue;
        found = startCol + i; break;
      }
    }
    cols[metric] = found;
  }
  for (const [metric, pattern] of Object.entries(COL_PATTERNS_LOOSE)) {
    if (cols[metric] >= 0) continue;
    for (let i = 0; i < slice.length; i++) {
      const h = String(slice[i]||'').trim();
      if (!h) continue;
      if (pattern.test(h)) {
        if (metric==='gmv' && /ad.?sales|ppc.?sales/i.test(h)) continue;
        if (metric==='traffic' && /ad|spend|sales|acos|tacos/i.test(h)) continue;
        const alreadyUsed = Object.values(cols).includes(startCol + i);
        if (!alreadyUsed) { cols[metric] = startCol + i; break; }
      }
    }
  }
  return cols;
}

function parseSheetData(csv) {
  const rows = parseCSV(csv);
  if(rows.length < 4) return null;
  const weekLabelRow = rows[1]||[], headerRow = rows[2]||[];

  console.log('[PARSE] Sheet header row:', headerRow.slice(0,30));

  const weekStarts = [];
  for(let i=0;i<weekLabelRow.length;i++){
    const label=String(weekLabelRow[i]||'').trim();
    if(!label) continue;
    if(MONTH_RE.test(label)) weekStarts.push({label, startCol:i});
  }
  if(weekStarts.length===0) return null;

  const deduped = [];
  for(const wk of weekStarts){
    const prev = deduped[deduped.length-1];
    if(prev && prev.label===wk.label && wk.startCol - prev.startCol <= 3) continue;
    if(prev && wk.startCol - prev.startCol === 1) continue;
    deduped.push(wk);
  }

  const weeks = deduped.map((wk,wi)=>{
    const nextStart = wi<deduped.length-1 ? deduped[wi+1].startCol : weekLabelRow.length;
    const cols = findColsForWeek(headerRow, wk.startCol, nextStart);
    return {label:wk.label, startCol:wk.startCol, cols};
  });

  let latestIdx = -1;
  for(let wi=weeks.length-1;wi>=0;wi--){
    const gc=weeks[wi].cols.gmv; if(gc<0) continue;
    let has=false;
    for(let ri=3;ri<Math.min(rows.length,35);ri++){if(cleanNum(rows[ri][gc])>0){has=true;break;}}
    if(has){latestIdx=wi;break;}
  }

  if(latestIdx<0) latestIdx=weeks.length-1;
  const prevIdx = latestIdx>0?latestIdx-1:0;

  const getW=(row,wi)=>{
    if(wi<0||wi>=weeks.length) return {adSpend:0,adSales:0,units:0,gmv:0,asp:0,traffic:0,conv:0,tacos:0};
    const c=weeks[wi].cols;
    return {
      adSpend: c.adSpend>=0?cleanNum(row[c.adSpend]):0,
      adSales: c.adSales>=0?cleanNum(row[c.adSales]):0,
      units:   c.units  >=0?cleanNum(row[c.units])  :0,
      gmv:     c.gmv    >=0?cleanNum(row[c.gmv])    :0,
      asp:     c.asp    >=0?cleanNum(row[c.asp])     :0,
      traffic: c.traffic>=0?cleanNum(row[c.traffic]) :0,
      conv:    c.conv   >=0?cleanNum(row[c.conv])    :0,
      tacos:   c.tacos  >=0?cleanNum(row[c.tacos])   :0,
    };
  };

  // ─── FIX 1: Include ALL rows with a valid ASIN, even if GMV=0
  // This ensures traffic-only rows are counted correctly.
  // We do exclude rows where ALL metrics are zero (completely blank rows).
  const asins = [];
  for(let ri=3;ri<rows.length;ri++){
    const row=rows[ri], id=String(row[0]||'').trim();
    if(!id||id.length<8||!/^[A-Z0-9]+$/i.test(id)) continue;
    const title=String(row[1]||'').trim(), category=String(row[5]||'Other').trim()||'Other';
    const cur=getW(row,latestIdx), prev=getW(row,prevIdx);
    // Only skip rows that are completely empty (no traffic, no units, no gmv, no spend)
    if(cur.gmv===0&&cur.units===0&&cur.traffic===0&&cur.adSpend===0) continue;
    asins.push({asin:id,title,category,cur,prev});
  }

  const history=weeks.map((wk,wi)=>{
    const c=wk.cols;
    let gmv=0,units=0,traffic=0,adSpend=0,adSales=0,convSum=0,convCount=0;
    for(let ri=3;ri<rows.length;ri++){
      const row=rows[ri],id=String(row[0]||'').trim();
      if(!id||id.length<8||!/^[A-Z0-9]+$/i.test(id)) continue;
      if(c.gmv    >=0) gmv    +=cleanNum(row[c.gmv]);
      if(c.units  >=0) units  +=cleanNum(row[c.units]);
      if(c.traffic>=0) traffic+=cleanNum(row[c.traffic]);
      if(c.adSpend>=0) adSpend+=cleanNum(row[c.adSpend]);
      if(c.adSales>=0) adSales+=cleanNum(row[c.adSales]);
      if(c.conv   >=0){const cv=cleanNum(row[c.conv]);if(cv>0){convSum+=cv;convCount++;}}
    }
    return {label:wk.label,gmv,units,traffic,adSpend,adSales,conv:convCount?convSum/convCount:0,tacos:gmv?(adSpend/gmv)*100:0,isCurrent:wi===latestIdx};
  });

  return {asins,history,curWk:weeks[latestIdx],prevWk:weeks[prevIdx],latestIdx};
}

// ═══════════════════════════════════════════════════════
// AGGREGATION
// ═══════════════════════════════════════════════════════
function agg(asins,f='cur'){
  return asins.reduce((a,x)=>({
    gmv:a.gmv+x[f].gmv,
    units:a.units+x[f].units,
    traffic:a.traffic+x[f].traffic,
    adSpend:a.adSpend+x[f].adSpend,
    adSales:a.adSales+x[f].adSales
  }),{gmv:0,units:0,traffic:0,adSpend:0,adSales:0});
}

function aggConv(asins,f='cur'){
  const t=agg(asins,f);
  return t.traffic>0?(t.units/t.traffic)*100:0;
}

function aggTacos(asins,f='cur'){
  const t=agg(asins,f);
  return t.gmv>0?(t.adSpend/t.gmv)*100:0;
}

function byCat(asins){
  const m={};
  for(const a of asins){
    const cat=a.category||'Other';
    if(!m[cat]) m[cat]={cur:{gmv:0,units:0,adSpend:0,adSales:0,traffic:0},prev:{gmv:0,units:0,adSpend:0,adSales:0,traffic:0},asins:[]};
    m[cat].cur.gmv+=a.cur.gmv; m[cat].cur.units+=a.cur.units; m[cat].cur.adSpend+=a.cur.adSpend; m[cat].cur.adSales+=a.cur.adSales; m[cat].cur.traffic+=a.cur.traffic;
    m[cat].prev.gmv+=a.prev.gmv; m[cat].prev.units+=a.prev.units; m[cat].prev.adSpend+=a.prev.adSpend; m[cat].prev.adSales+=a.prev.adSales; m[cat].prev.traffic+=a.prev.traffic;
    m[cat].asins.push(a);
  }
  return m;
}

// ═══════════════════════════════════════════════════════
// KPI CARD
// ═══════════════════════════════════════════════════════
function kpiCard(label,cur,prev,fmtFn,accent,breakdown){
  const p=pct(cur,prev),cls=wCls(p),arr=wArr(p);
  let bHtml='';
  if(breakdown&&breakdown.length){
    bHtml='<div class="kpi-breakdown">';
    for(const b of breakdown){
      const bp=pct(b.cur,b.prev),bc=wCls(bp);
      bHtml+=`<div class="kpi-breakdown-row"><span class="kpi-breakdown-label">${b.label}</span><span class="kpi-breakdown-val">${fmtFn(b.cur)}</span><span class="kpi-breakdown-wow ${bc}">${wArr(bp)} ${Math.abs(bp).toFixed(1)}%</span></div>`;
    }
    bHtml+='</div>';
  }
  return `<div class="kpi-card" style="--accent:${accent}"><div class="kpi-label">${label}</div><div class="kpi-value">${fmtFn(cur)}</div><div class="kpi-wow ${cls}">${arr} ${Math.abs(p).toFixed(1)}% WoW <span style="color:var(--text-muted);font-size:10px;margin-left:4px">${fmtFn(prev)} prev</span></div>${bHtml}</div>`;
}

// ═══════════════════════════════════════════════════════
// CATEGORY ROWS
// ═══════════════════════════════════════════════════════
function catRows(cats,pre='£'){
  const sorted=Object.entries(cats).sort((a,b)=>b[1].cur.gmv-a[1].cur.gmv);
  const maxG=sorted[0]?.[1]?.cur?.gmv||1;
  return sorted.map(([cat,d])=>{
    const p=pct(d.cur.gmv,d.prev.gmv),cls=wCls(p),bw=((d.cur.gmv/maxG)*80).toFixed(0),col=getCatColor(cat);
    return `<div class="cat-row"><div class="cat-row-name"><span style="display:inline-block;width:8px;height:8px;border-radius:50%;background:${col};margin-right:8px;vertical-align:middle"></span>${cat}<div style="height:2px;width:${bw}%;background:${col};opacity:.4;margin-top:3px;border-radius:2px"></div></div><div class="crv">${fmt(d.cur.gmv,pre)}</div><div class="crv">${fmtU(d.cur.units)}</div><div class="crw ${cls}">${wArr(p)} ${Math.abs(p).toFixed(1)}%</div></div>`;
  }).join('')||'<div class="no-data">No data</div>';
}

function renderDonutStats(cats,pre,targetId){
  const sorted=Object.entries(cats).sort((a,b)=>b[1].cur.gmv-a[1].cur.gmv).slice(0,4);
  const total=sorted.reduce((s,[,d])=>s+d.cur.gmv,0);
  document.getElementById(targetId).innerHTML=sorted.map(([cat,d])=>{
    const p=pct(d.cur.gmv,d.prev.gmv),cls=wCls(p),share=total>0?((d.cur.gmv/total)*100).toFixed(0):0,col=getCatColor(cat);
    return `<div class="donut-stat"><div class="donut-stat-label"><span style="display:inline-block;width:6px;height:6px;border-radius:50%;background:${col};margin-right:5px;vertical-align:middle"></span>${cat}</div><div class="donut-stat-val" style="color:${col}">${fmt(d.cur.gmv,pre)}</div><div class="donut-stat-sub ${cls}">${share}% share · ${wArr(p)}${Math.abs(p).toFixed(1)}% WoW</div></div>`;
  }).join('');
}

// ═══════════════════════════════════════════════════════
// ADS PERFORMANCE
// ═══════════════════════════════════════════════════════
function renderAdsPerformance(asins, pre, summaryId, bodyId, spendChartId, acosChartId){
  const cats = byCat(asins);
  const totC = agg(asins,'cur'), totP = agg(asins,'prev');
  const totalSpend=totC.adSpend,totalSales=totC.adSales,totalGmv=totC.gmv;
  const prevSpend=totP.adSpend,prevSales=totP.adSales;
  const totalAcos=totalSales>0?(totalSpend/totalSales)*100:0;
  const totalRoas=totalSpend>0?totalSales/totalSpend:0;
  const totalTacos=totalGmv>0?(totalSpend/totalGmv)*100:0;
  const spendWow=pct(totalSpend,prevSpend),salesWow=pct(totalSales,prevSales);

  document.getElementById(summaryId).innerHTML=[
    `<div class="ads-kpi-card" style="--ac:#ff3b5c"><div class="kpi-label">Total Ad Spend</div><div class="kpi-value">${fmt(totalSpend,pre)}</div><div class="kpi-wow ${wCls(spendWow)}">${wArr(spendWow)} ${Math.abs(spendWow).toFixed(1)}% WoW <span style="color:var(--text-muted);font-size:10px;margin-left:4px">${fmt(prevSpend,pre)} prev</span></div></div>`,
    `<div class="ads-kpi-card" style="--ac:#00ff9d"><div class="kpi-label">Total Ad Sales</div><div class="kpi-value">${fmt(totalSales,pre)}</div><div class="kpi-wow ${wCls(salesWow)}">${wArr(salesWow)} ${Math.abs(salesWow).toFixed(1)}% WoW <span style="color:var(--text-muted);font-size:10px;margin-left:4px">${fmt(prevSales,pre)} prev</span></div></div>`,
    `<div class="ads-kpi-card" style="--ac:#ffb800"><div class="kpi-label">Overall ACOS</div><div class="kpi-value" style="color:${totalAcos<15?'var(--neon-green)':totalAcos<25?'var(--neon-amber)':'var(--neon-red)'}">${totalAcos.toFixed(1)}%</div><div class="kpi-wow flat">ROAS: ${totalRoas.toFixed(2)}x &nbsp;·&nbsp; TACOS: ${totalTacos.toFixed(1)}%</div></div>`,
    `<div class="ads-kpi-card" style="--ac:#b845ff"><div class="kpi-label">Ad Attributed Sales</div><div class="kpi-value">${totalGmv>0?((totalSales/totalGmv)*100).toFixed(1):0}%</div><div class="kpi-wow flat" style="color:var(--text-secondary);font-size:11px">of total GMV driven by ads</div></div>`,
  ].join('');

  const catArr=Object.entries(cats).sort((a,b)=>b[1].cur.adSpend-a[1].cur.adSpend);
  document.getElementById(bodyId).innerHTML=catArr.map(([cat,d])=>{
    const col=getCatColor(cat);
    const acos=d.cur.adSales>0?(d.cur.adSpend/d.cur.adSales)*100:0;
    const roas=d.cur.adSpend>0?d.cur.adSales/d.cur.adSpend:0;
    const tacos=d.cur.gmv>0?(d.cur.adSpend/d.cur.gmv)*100:0;
    const spWow=pct(d.cur.adSpend,d.prev.adSpend),saWow=pct(d.cur.adSales,d.prev.adSales);
    const effCls=acos<15?'great':acos<25?'ok':'poor';
    const effLabel=acos<15?'✓ Efficient':acos<25?'⚠ Monitor':'✗ Review';
    return `<tr>
      <td><div class="cat-name-cell"><span class="cat-dot" style="background:${col}"></span>${cat}</div></td>
      <td>${fmt(d.cur.adSpend,pre)}</td>
      <td><span class="wow-pill ${wCls(spWow)}">${wArr(spWow)} ${Math.abs(spWow).toFixed(1)}%</span></td>
      <td>${fmt(d.cur.adSales,pre)}</td>
      <td><span class="wow-pill ${wCls(saWow)}">${wArr(saWow)} ${Math.abs(saWow).toFixed(1)}%</span></td>
      <td style="color:${acos<15?'var(--neon-green)':acos<25?'var(--neon-amber)':'var(--neon-red)'};font-family:var(--font-mono);font-size:12px">${acos.toFixed(1)}%</td>
      <td style="font-family:var(--font-mono);font-size:12px">${roas.toFixed(2)}x</td>
      <td style="font-family:var(--font-mono);font-size:12px">${tacos.toFixed(1)}%</td>
      <td style="font-family:var(--font-mono);font-size:12px">${fmt(d.cur.gmv,pre)}</td>
      <td><span class="eff-badge ${effCls}">${effLabel}</span></td>
    </tr>`;
  }).join('')||'<tr><td colspan="10" class="no-data">No ad data</td></tr>';

  const labels=catArr.map(([c])=>c);
  const spends=catArr.map(([,d])=>d.cur.adSpend);
  const acosList=catArr.map(([,d])=>d.cur.adSales>0?(d.cur.adSpend/d.cur.adSales)*100:0);
  const cols=catArr.map(([c])=>getCatColor(c));

  const ctx1=document.getElementById(spendChartId);
  if(ctx1){if(charts[spendChartId])charts[spendChartId].destroy();charts[spendChartId]=new Chart(ctx1,{type:'bar',data:{labels,datasets:[{label:'Ad Spend',data:spends,backgroundColor:cols.map(c=>c+'99'),borderColor:cols,borderWidth:2,borderRadius:6}]},options:{...CD,plugins:{legend:{display:false}},scales:{...CD.scales,y:{ticks:{color:'#4a5568',font:{family:'JetBrains Mono',size:9},callback:v=>pre+(v>=1000?(v/1000).toFixed(0)+'K':v)},grid:{color:'rgba(255,255,255,0.05)'}}}}});}
  const ctx2=document.getElementById(acosChartId);
  if(ctx2){if(charts[acosChartId])charts[acosChartId].destroy();charts[acosChartId]=new Chart(ctx2,{type:'bar',data:{labels,datasets:[{label:'ACOS %',data:acosList,backgroundColor:acosList.map(a=>a<15?'rgba(0,255,157,0.3)':a<25?'rgba(255,184,0,0.3)':'rgba(255,59,92,0.3)'),borderColor:acosList.map(a=>a<15?'#00ff9d':a<25?'#ffb800':'#ff3b5c'),borderWidth:2,borderRadius:6}]},options:{...CD,plugins:{legend:{display:false}},scales:{...CD.scales,y:{ticks:{color:'#4a5568',font:{family:'JetBrains Mono',size:9},callback:v=>v+'%'},grid:{color:'rgba(255,255,255,0.05)'}}}}});}
}

// ═══════════════════════════════════════════════════════
// ORGANIC vs PAID SPLIT
// ═══════════════════════════════════════════════════════
function renderSplit(asins,history,pre,cardId,chartId){
  const tC=agg(asins,'cur'),tP=agg(asins,'prev');
  const paidSales=tC.adSales,totalGmv=tC.gmv;
  const organicSales=Math.max(0,totalGmv-paidSales);
  const paidPct=totalGmv>0?(paidSales/totalGmv)*100:0,orgPct=100-paidPct;
  const prevPaid=tP.adSales,prevTotal=tP.gmv;
  const prevPaidPct=prevTotal>0?(prevPaid/prevTotal)*100:0;
  const paidPctWow=paidPct-prevPaidPct;
  const organicWow=pct(Math.max(0,totalGmv-paidSales),Math.max(0,prevTotal-prevPaid));
  const paidWow=pct(paidSales,prevPaid);

  document.getElementById(cardId).innerHTML=`
    <div class="split-title">Organic vs Paid Split</div>
    <div class="split-sub">How much of your GMV is driven by ads vs organic ranking</div>
    <div class="split-big">
      <div class="split-big-item"><div class="split-big-label">Paid (Ad Sales)</div><div class="split-big-val" style="color:var(--neon-red)">${fmt(paidSales,pre)}</div><div class="split-big-sub ${wCls(paidWow)}">${paidPct.toFixed(1)}% of GMV · ${wArr(paidWow)}${Math.abs(paidWow).toFixed(1)}% WoW</div></div>
      <div class="split-big-item"><div class="split-big-label">Organic (Est.)</div><div class="split-big-val" style="color:var(--neon-cyan)">${fmt(organicSales,pre)}</div><div class="split-big-sub ${wCls(organicWow)}">${orgPct.toFixed(1)}% of GMV · ${wArr(organicWow)}${Math.abs(organicWow).toFixed(1)}% WoW</div></div>
    </div>
    <div class="split-bar-wrap">
      <div class="split-bar-label"><span>Paid ${paidPct.toFixed(1)}%</span><span>Organic ${orgPct.toFixed(1)}%</span></div>
      <div class="split-bar-track"><div class="split-bar-paid" style="width:${paidPct}%"></div><div class="split-bar-organic" style="width:${orgPct}%"></div></div>
    </div>
    <div class="split-legend">
      <div class="split-leg-item"><div class="split-leg-dot" style="background:linear-gradient(135deg,#ff3b5c,#ff7c2a)"></div>Paid / Ad-driven</div>
      <div class="split-leg-item"><div class="split-leg-dot" style="background:linear-gradient(135deg,#00e5ff,#00ff9d)"></div>Organic</div>
    </div>
    <div class="split-divider"></div>
    <div class="split-metrics-row">
      <div class="split-metric"><div class="split-metric-label">Total GMV</div><div class="split-metric-val">${fmt(totalGmv,pre)}</div><div class="split-metric-sub ${wCls(pct(totalGmv,prevTotal))}">${wArr(pct(totalGmv,prevTotal))}${Math.abs(pct(totalGmv,prevTotal)).toFixed(1)}% WoW</div></div>
      <div class="split-metric"><div class="split-metric-label">Paid Dependency</div><div class="split-metric-val" style="color:${paidPct>60?'var(--neon-red)':paidPct>40?'var(--neon-amber)':'var(--neon-green)'}">${paidPct.toFixed(0)}%</div><div class="split-metric-sub flat">${paidPctWow>=0?'+':''}${paidPctWow.toFixed(1)}pp WoW</div></div>
      <div class="split-metric"><div class="split-metric-label">Organic Health</div><div class="split-metric-val" style="color:${orgPct>60?'var(--neon-green)':orgPct>40?'var(--neon-amber)':'var(--neon-red)'}">${orgPct.toFixed(0)}%</div><div class="split-metric-sub flat">${orgPct>50?'Strong':'Build organic'}</div></div>
    </div>`;

  const last12=history.slice(-12);
  const labels=last12.map(h=>h.label.split(/[\s-]+/).slice(0,3).join(' '));
  const paidD=last12.map(h=>h.adSales);
  const orgD=last12.map(h=>Math.max(0,h.gmv-h.adSales));
  const ctx=document.getElementById(chartId); if(!ctx)return;
  if(charts[chartId])charts[chartId].destroy();
  charts[chartId]=new Chart(ctx,{type:'bar',data:{labels,datasets:[
    {label:'Ad Sales (Paid)',data:paidD,backgroundColor:'rgba(255,59,92,0.5)',borderColor:'#ff3b5c',borderWidth:1,stack:'s'},
    {label:'Organic GMV',data:orgD,backgroundColor:'rgba(0,229,255,0.3)',borderColor:'#00e5ff',borderWidth:1,stack:'s'}
  ]},options:{...CD,scales:{x:{...CD.scales.x,stacked:true},y:{...CD.scales.y,stacked:true,ticks:{color:'#4a5568',font:{family:'JetBrains Mono',size:9},callback:v=>pre+(v>=1000?(v/1000).toFixed(0)+'K':v)}}}}});
}

// ═══════════════════════════════════════════════════════
// INVENTORY HEALTH
// ═══════════════════════════════════════════════════════
function calcInventoryHealth(asins){
  return asins.map(a=>{
    const weeklySold=a.cur.units,prevSold=a.prev.units;
    const velChange=prevSold>0?((weeklySold-prevSold)/prevSold)*100:0;
    const isDropping=velChange<-30;
    let weeksOfCover,status;
    if(weeklySold===0&&prevSold>0){weeksOfCover=0;status='critical';}
    else if(isDropping&&velChange<-60){weeksOfCover=1.5;status='critical';}
    else if(isDropping&&velChange<-30){weeksOfCover=3;status='warning';}
    else if(weeklySold>0){weeksOfCover=6;status='healthy';}
    else{weeksOfCover=0;status='new';}
    return {...a,weeklySold,prevSold,avgSold:(weeklySold+prevSold)/2||1,velChange,weeksOfCover,status};
  });
}

function renderInvGrid(asinsWithHealth, pre, gridId, pillsId){
  const counts={critical:0,warning:0,healthy:0,new:0};
  asinsWithHealth.forEach(a=>counts[a.status]=(counts[a.status]||0)+1);
  if(pillsId&&document.getElementById(pillsId)){
    document.getElementById(pillsId).innerHTML=[
      `<span class="inv-pill critical">🔴 ${counts.critical} Critical</span>`,
      `<span class="inv-pill warning">🟡 ${counts.warning} Warning</span>`,
      `<span class="inv-pill healthy">🟢 ${counts.healthy} Healthy</span>`,
    ].join('');
  }
  const statusColor={critical:'var(--neon-red)',warning:'var(--neon-amber)',healthy:'var(--neon-green)',new:'var(--neon-blue)'};
  const sorted=[...asinsWithHealth].sort((a,b)=>{const o={critical:0,warning:1,new:2,healthy:3};return o[a.status]-o[b.status]||b.cur.gmv-a.cur.gmv;});
  const el=document.getElementById(gridId); if(!el)return;
  el.innerHTML=sorted.slice(0,40).map(a=>{
    const col=statusColor[a.status]||'var(--neon-blue)';
    const velCls=a.velChange>=0?'up':a.velChange>-30?'flat':'down';
    const coverLabel=a.status==='critical'?'⚠ Stock Risk':a.status==='warning'?'~3 wks cover':a.status==='healthy'?'Stable':'New/No hist.';
    const barW=Math.min(100,Math.max(0,a.status==='critical'?10:a.status==='warning'?40:85));
    return `<div class="inv-card" style="--ih:${col}" data-status="${a.status}">
      <div class="inv-card-top">
        <div class="inv-info"><div class="inv-asin-title" title="${a.title}">${a.title||a.asin}</div><div class="inv-asin-code">${a.asin} · ${a.category}</div></div>
        <span class="inv-health-badge ${a.status}">${coverLabel}</span>
      </div>
      <div class="inv-metrics">
        <div class="inv-metric"><div class="inv-metric-label">Units/wk</div><div class="inv-metric-val" style="color:${col}">${fmtU(a.weeklySold)}</div></div>
        <div class="inv-metric"><div class="inv-metric-label">Prev wk</div><div class="inv-metric-val">${fmtU(a.prevSold)}</div></div>
        <div class="inv-metric"><div class="inv-metric-label">GMV</div><div class="inv-metric-val">${fmt(a.cur.gmv,pre)}</div></div>
      </div>
      <div class="inv-vel-wrap">
        <div class="inv-vel-label"><span>Velocity trend</span><span class="${velCls}" style="color:${a.velChange>=0?'var(--neon-green)':a.velChange>-30?'var(--neon-amber)':'var(--neon-red)'}">${a.velChange>=0?'+':''}${a.velChange.toFixed(1)}% WoW</span></div>
        <div class="inv-vel-track"><div class="inv-vel-fill" style="width:${barW}%;background:${col}"></div></div>
      </div>
    </div>`;
  }).join('')||'<div class="no-data">No inventory data</div>';
}

function filterInv(type,page,btn){
  btn.closest('.inv-filter-tabs').querySelectorAll('.inv-tab').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  const src=page==='uk'?ukAllAsins:euAllAsins;
  const pre=page==='uk'?'£':'€';
  const health=calcInventoryHealth(src);
  const filtered=type==='all'?health:health.filter(a=>a.status===type);
  renderInvGrid(filtered,pre,page+'InvGrid',null);
}

// EU per-marketplace inventory accordion
function renderEuInvPerMarket(available){
  const container=document.getElementById('euInvPerMarket');
  if(!container) return;
  let html='';
  for(const mkt of available){
    const meta=MKT_META[mkt];
    const mktAsins=rawData[mkt].asins;
    const health=calcInventoryHealth(mktAsins);
    const counts={critical:0,warning:0,healthy:0,new:0};
    health.forEach(a=>counts[a.status]=(counts[a.status]||0)+1);
    const gridId=`invGrid_${mkt}`;
    html+=`<div class="eu-inv-section">
      <div class="eu-inv-mkt-header" onclick="toggleEuInvSection('${mkt}')">
        <div class="eu-inv-mkt-title" style="color:${meta.color}">${meta.label} — ${mktAsins.length} ASINs</div>
        <div class="eu-inv-mkt-pills">
          <span class="inv-pill critical">🔴 ${counts.critical}</span>
          <span class="inv-pill warning">🟡 ${counts.warning}</span>
          <span class="inv-pill healthy">🟢 ${counts.healthy}</span>
          <span style="font-family:var(--font-mono);font-size:10px;color:var(--text-muted);margin-left:8px">▼ expand</span>
        </div>
      </div>
      <div id="euInvBody_${mkt}" style="display:none">
        <div style="display:flex;gap:8px;margin-bottom:12px;flex-wrap:wrap">
          <button class="inv-tab active" onclick="filterEuMktInv('all','${mkt}',this)">All ASINs</button>
          <button class="inv-tab" onclick="filterEuMktInv('critical','${mkt}',this)">🔴 Critical</button>
          <button class="inv-tab" onclick="filterEuMktInv('warning','${mkt}',this)">🟡 Warning</button>
          <button class="inv-tab" onclick="filterEuMktInv('healthy','${mkt}',this)">🟢 Healthy</button>
        </div>
        <div class="inv-grid" id="${gridId}"></div>
      </div>
    </div>`;
  }
  container.innerHTML=html;
  for(const mkt of available){
    const health=calcInventoryHealth(rawData[mkt].asins);
    renderInvGrid(health,'€',`invGrid_${mkt}`,null);
  }
}

function toggleEuInvSection(mkt){
  const body=document.getElementById(`euInvBody_${mkt}`);
  if(!body) return;
  body.style.display=body.style.display==='none'?'block':'none';
}

function filterEuMktInv(type,mkt,btn){
  btn.closest('div').querySelectorAll('.inv-tab').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  const health=calcInventoryHealth(rawData[mkt].asins);
  const filtered=type==='all'?health:health.filter(a=>a.status===type);
  renderInvGrid(filtered,'€',`invGrid_${mkt}`,null);
}

// ═══════════════════════════════════════════════════════
// ASIN TABLE
// ═══════════════════════════════════════════════════════
function asinRows(asins,pre='£',limit=40){
  const sorted=[...asins].sort((a,b)=>b.cur.gmv-a.cur.gmv).slice(0,limit);
  return sorted.map(a=>{
    const p=pct(a.cur.gmv,a.prev.gmv),cls=wCls(p);
    const tacos=a.cur.gmv>0?(a.cur.adSpend/a.cur.gmv)*100:0;
    return `<tr><td><div class="asin-title" title="${a.title}">${a.title||a.asin}</div><a class="asin-code" href="https://www.amazon.co.uk/dp/${a.asin}" target="_blank">${a.asin}</a></td><td><span class="cat-badge">${a.category}</span></td><td class="tdr">${fmt(a.cur.gmv,pre)}</td><td class="tdr">${fmtU(a.cur.units)}</td><td class="tdr">${fmtU(a.cur.traffic)}</td><td class="tdr">${a.cur.conv.toFixed(1)}%</td><td class="tdr">${fmt(a.cur.adSpend,pre)}</td><td class="tdr">${tacos.toFixed(1)}%</td><td class="tdr"><span class="wow-pill ${cls}">${wArr(p)} ${Math.abs(p).toFixed(1)}%</span></td></tr>`;
  }).join('')||'<tr><td colspan="9" class="no-data">No data</td></tr>';
}

// ═══════════════════════════════════════════════════════
// HISTORY TABLE
// ═══════════════════════════════════════════════════════
function histRows(history,pre='£'){
  let html='';
  for(let i=history.length-1;i>=0;i--){
    const h=history[i]; if(h.gmv===0)continue;
    const prev=i>0?history[i-1]:null,p=prev?pct(h.gmv,prev.gmv):0,cls=wCls(p);
    html+=`<tr class="${h.isCurrent?'cur-wk':''}"><td>${h.label}${h.isCurrent?' ◀ Current':''}</td><td>${fmt(h.gmv,pre)}</td><td>${fmtU(h.units)}</td><td>${fmtU(h.traffic)}</td><td>${h.conv>0?h.conv.toFixed(1)+'%':'—'}</td><td>${fmt(h.adSpend,pre)}</td><td>${fmt(h.adSales,pre)}</td><td>${h.tacos>0?h.tacos.toFixed(1)+'%':'—'}</td><td><span class="wow-pill ${cls}">${prev?wArr(p)+' '+Math.abs(p).toFixed(1)+'%':'—'}</span></td></tr>`;
  }
  return html;
}

// ═══════════════════════════════════════════════════════
// INSIGHTS ENGINE
// ═══════════════════════════════════════════════════════
function buildInsights(asins,pre='£'){
  const ins=[];
  const totC=agg(asins,'cur'),totP=agg(asins,'prev');
  const totalPct=pct(totC.gmv,totP.gmv);
  const cats=byCat(asins);
  const catArr=Object.entries(cats).sort((a,b)=>b[1].cur.gmv-a[1].cur.gmv);

  ins.push({type:totalPct>=0?'win':'loss',icon:totalPct>=0?'📈':'📉',color:totalPct>=0?'#00ff9d':'#ff3b5c',
    title:`Overall GMV ${totalPct>=0?'▲':'▼'} ${Math.abs(totalPct).toFixed(1)}%`,
    body:`Total GMV moved from <strong>${fmt(totP.gmv,pre)}</strong> to <strong>${fmt(totC.gmv,pre)}</strong> this week.`,
    what:`Week-on-week GMV ${totalPct>=0?'grew':'declined'} by ${Math.abs(totalPct).toFixed(1)}% across all channels.`,
    why:totalPct>=0?`Units rose from ${fmtU(totP.units)} to ${fmtU(totC.units)} with ${fmtU(totC.traffic)} sessions driving ${(totC.units/Math.max(totC.traffic,1)*100).toFixed(1)}% conversion.`:`Units fell from ${fmtU(totP.units)} to ${fmtU(totC.units)}. ${totC.traffic<totP.traffic?'Traffic also dropped.':'Traffic held but conversion weakened.'}`,
    how:totalPct>=0?`Protect rankings on top ASINs, keep ad budgets uncapped on winners.`:`Check suppressed listings, review pricing vs competitors, ensure ads are active.`
  });

  if(catArr.length>0){
    const[cat,d]=catArr[0],p=pct(d.cur.gmv,d.prev.gmv);
    const hero=d.asins.sort((a,b)=>b.cur.gmv-a.cur.gmv)[0];
    ins.push({type:p>=0?'win':'loss',icon:p>=0?'🏆':'⚠️',color:p>=0?'#00ff9d':'#ff3b5c',
      title:`${cat}: ${p>=0?'Top Performer':'Needs Attention'}`,
      body:`<strong>${fmt(d.cur.gmv,pre)}</strong> GMV (${fmtPct(p)} WoW) — ${fmtU(d.cur.units)} units.`,
      what:`${cat} is your ${p>=0?'best-performing':'most impacted'} category with ${d.asins.length} active ASINs.`,
      why:p>=0?`Strong demand. Hero ASIN: ${hero?.title?.slice(0,45)||hero?.asin}.`:`GMV dropped from ${fmt(d.prev.gmv,pre)} to ${fmt(d.cur.gmv,pre)}.`,
      how:p>=0?`Scale ads on hero ASINs, defend Buy Box pricing.`:`Audit Buy Box ownership, boost bids on top ASINs immediately.`
    });
  }

  const tacos=totC.gmv>0?(totC.adSpend/totC.gmv)*100:0,prevTacos=totP.gmv>0?(totP.adSpend/totP.gmv)*100:0,td=tacos-prevTacos;
  const acos=totC.adSales>0?(totC.adSpend/totC.adSales)*100:0;
  ins.push({type:acos<15?'win':acos>25?'loss':'watch',icon:'💰',color:acos<15?'#00ff9d':acos>25?'#ff3b5c':'#ffb800',
    title:`ACOS ${acos.toFixed(1)}% · TACOS ${tacos.toFixed(1)}% — ${acos<15?'Efficient':acos>25?'Overspending':'Monitor'}`,
    body:`Ad Spend: <strong>${fmt(totC.adSpend,pre)}</strong> · Ad Sales: <strong>${fmt(totC.adSales,pre)}</strong>`,
    what:`ACOS ${acos.toFixed(1)}%, TACOS ${tacos.toFixed(1)}% (${td>=0?'+':''}${td.toFixed(1)}pp WoW).`,
    why:td>2?`TACOS rose — spend grew faster than GMV.`:td<-2?`TACOS improved — GMV grew faster than spend.`:`Ad efficiency broadly stable.`,
    how:acos>20?`Pause low-converting keywords, reduce bids where ACOS >25%.`:`Good efficiency. Reinvest in scaling top-performing categories.`
  });

  const winners=[...asins].filter(a=>a.prev&&a.prev.gmv>0).sort((a,b)=>pct(b.cur.gmv,b.prev.gmv)-pct(a.cur.gmv,a.prev.gmv));
  if(winners.length>0){
    const w=winners[0],wp=pct(w.cur.gmv,w.prev.gmv);
    ins.push({type:'win',icon:'⭐',color:'#00ff9d',
      title:`Hero ASIN +${wp.toFixed(0)}%: ${w.title?.slice(0,38)||w.asin}`,
      body:`GMV: <strong>${fmt(w.prev.gmv,pre)} → ${fmt(w.cur.gmv,pre)}</strong> · ${fmtU(w.prev.units)} → ${fmtU(w.cur.units)} units`,
      what:`${w.asin} in ${w.category} is the fastest-growing ASIN at +${wp.toFixed(1)}% GMV.`,
      why:`${w.cur.traffic>w.prev.traffic?'Traffic increased from '+fmtU(w.prev.traffic)+' to '+fmtU(w.cur.traffic)+'.':'Conversion improved despite flat traffic.'}`,
      how:`Protect momentum: ensure Buy Box, stack reviews, consider Sponsored Brand.`
    });
  }

  const losers=[...asins].filter(a=>a.prev&&a.prev.gmv>300).sort((a,b)=>pct(a.cur.gmv,a.prev.gmv)-pct(b.cur.gmv,b.prev.gmv));
  if(losers.length>0){
    const l=losers[0],lp=pct(l.cur.gmv,l.prev.gmv);
    if(lp<-10) ins.push({type:'loss',icon:'🚨',color:'#ff3b5c',
      title:`Alert: ${l.title?.slice(0,33)||l.asin} ↓${Math.abs(lp).toFixed(0)}%`,
      body:`GMV dropped: <strong>${fmt(l.prev.gmv,pre)} → ${fmt(l.cur.gmv,pre)}</strong>`,
      what:`${l.asin} lost ${Math.abs(lp).toFixed(1)}% GMV — steepest drop this week.`,
      why:`${l.cur.traffic<l.prev.traffic*0.8?'Traffic dropped sharply — ranking loss or listing suppression.':'Traffic held but conversion fell — Buy Box loss or pricing issue.'}`,
      how:`(1) Verify listing status, (2) Check Buy Box, (3) Confirm ads running, (4) Compare price vs competitors.`
    });
  }

  const convR=totC.traffic>0?(totC.units/totC.traffic)*100:0,prevConvR=totP.traffic>0?(totP.units/totP.traffic)*100:0,cd=convR-prevConvR;
  ins.push({type:Math.abs(cd)<1?'watch':cd>0?'win':'loss',icon:'🎯',color:cd>=0?'#4d9fff':'#ffb800',
    title:`Traffic ${fmtU(totC.traffic)} · Conv ${convR.toFixed(1)}%`,
    body:`Traffic ${totC.traffic>=totP.traffic?'▲':'▼'} ${fmtPct(pct(totC.traffic,totP.traffic))} · Conversion ${cd>=0?'+':''}${cd.toFixed(1)}pp WoW`,
    what:`${fmtU(totC.traffic)} sessions → ${fmtU(totC.units)} units at ${convR.toFixed(1)}% conversion.`,
    why:totC.traffic>totP.traffic&&totC.units<totP.units?`Traffic grew but units fell — conversion dropped.`:totC.traffic<totP.traffic&&totC.units>totP.units?`Fewer sessions but more units — conversion improved.`:`Traffic and conversion moved consistently.`,
    how:convR<prevConvR?`Audit main images, A+ content, pricing on top-traffic ASINs.`:`Maintain listing quality. Scale ads on top-converting ASINs.`
  });

  return ins;
}

function renderInsights(ins,id){
  document.getElementById(id).innerHTML=ins.map(i=>`<div class="insight-card" style="--ic:${i.color}"><div class="insight-type"><span style="font-size:16px">${i.icon}</span><span class="insight-tag ${i.type}">${i.type.toUpperCase()}</span></div><div class="insight-title">${i.title}</div><div class="insight-body">${i.body}</div><div class="iwl"><span class="ilb">WHAT</span>${i.what}</div><div class="iwl"><span class="ilb">WHY</span>${i.why}</div><div class="iwl"><span class="ilb">HOW</span>${i.how}</div></div>`).join('');
}

// ═══════════════════════════════════════════════════════
// CHART HELPERS
// ═══════════════════════════════════════════════════════
const CD={responsive:true,maintainAspectRatio:false,plugins:{legend:{labels:{color:'#8892a4',font:{family:'JetBrains Mono',size:10},boxWidth:12}}},scales:{x:{ticks:{color:'#4a5568',font:{family:'JetBrains Mono',size:9},maxRotation:45},grid:{color:'rgba(255,255,255,0.03)'}},y:{ticks:{color:'#4a5568',font:{family:'JetBrains Mono',size:9}},grid:{color:'rgba(255,255,255,0.05)'}}}};

function lineChart(id,labels,data,label,color){const ctx=document.getElementById(id);if(!ctx)return;if(charts[id])charts[id].destroy();charts[id]=new Chart(ctx,{type:'line',data:{labels,datasets:[{label,data,borderColor:color,backgroundColor:color+'18',borderWidth:2,pointBackgroundColor:color,pointRadius:4,tension:.4,fill:true}]},options:{...CD}});}
function barChart(id,labels,ds1,ds2){const ctx=document.getElementById(id);if(!ctx)return;if(charts[id])charts[id].destroy();charts[id]=new Chart(ctx,{type:'bar',data:{labels,datasets:[{label:'Ad Spend',data:ds1,backgroundColor:'#ff3b5c55',borderColor:'#ff3b5c',borderWidth:1},{label:'Ad Sales',data:ds2,backgroundColor:'#00ff9d33',borderColor:'#00ff9d',borderWidth:1}]},options:{...CD}});}
function hBarChart(id,labels,data,colors){const ctx=document.getElementById(id);if(!ctx)return;if(charts[id])charts[id].destroy();charts[id]=new Chart(ctx,{type:'bar',data:{labels,datasets:[{label:'GMV',data,backgroundColor:colors.map(c=>c+'88'),borderColor:colors,borderWidth:2,borderRadius:6}]},options:{...CD,indexAxis:'y',plugins:{legend:{display:false}}}});}
function doughnut(id,labels,data,colors){const ctx=document.getElementById(id);if(!ctx)return;if(charts[id])charts[id].destroy();charts[id]=new Chart(ctx,{type:'doughnut',data:{labels,datasets:[{data,backgroundColor:colors.map(c=>c+'cc'),borderColor:'#0d1320',borderWidth:3,hoverBackgroundColor:colors}]},options:{responsive:true,maintainAspectRatio:false,cutout:'60%',plugins:{legend:{position:'right',labels:{color:'#8892a4',font:{family:'JetBrains Mono',size:10},boxWidth:10,padding:12}}}}});}

// ═══════════════════════════════════════════════════════
// UK RENDER
// ═══════════════════════════════════════════════════════
function renderUK(){
  const R=rawData.uk_retail,B=rawData.uk_business;
  if(!R){showErr('ukError','UK Retail data failed to load.');return;}

  document.getElementById('ukCurrentWeek').textContent=R.curWk.label;
  document.getElementById('ukVsWeek').textContent=`vs ${R.prevWk?.label||'prior week'}`;

  const rC=agg(R.asins,'cur'),rP=agg(R.asins,'prev');
  const bC=B?agg(B.asins,'cur'):{gmv:0,units:0,traffic:0,adSpend:0,adSales:0};
  const bP=B?agg(B.asins,'prev'):{gmv:0,units:0,traffic:0,adSpend:0,adSales:0};
  const tC={gmv:rC.gmv+bC.gmv,units:rC.units+bC.units,traffic:rC.traffic+bC.traffic,adSpend:rC.adSpend+bC.adSpend,adSales:rC.adSales+bC.adSales};
  const tP={gmv:rP.gmv+bP.gmv,units:rP.units+bP.units,traffic:rP.traffic+bP.traffic,adSpend:rP.adSpend+bP.adSpend,adSales:rP.adSales+bP.adSales};

  const merged=JSON.parse(JSON.stringify(R.asins));
  if(B){for(const b of B.asins){const ex=merged.find(x=>x.asin===b.asin);if(ex){ex.cur.gmv+=b.cur.gmv;ex.cur.units+=b.cur.units;ex.cur.traffic+=b.cur.traffic;ex.cur.adSpend+=b.cur.adSpend;ex.cur.adSales+=b.cur.adSales;ex.prev.gmv+=b.prev.gmv;ex.prev.units+=b.prev.units;ex.prev.traffic+=b.prev.traffic;ex.prev.adSpend+=b.prev.adSpend;ex.prev.adSales+=b.prev.adSales;}else merged.push(JSON.parse(JSON.stringify(b)));}}
  ukAsins=merged; ukAllAsins=merged;

  const curConvR = tC.traffic>0?(tC.units/tC.traffic)*100:0;
  const prevConvR = tP.traffic>0?(tP.units/tP.traffic)*100:0;
  const curTacos = tC.gmv>0?(tC.adSpend/tC.gmv)*100:0;
  const prevTacos = tP.gmv>0?(tP.adSpend/tP.gmv)*100:0;
  const rCurConv = rC.traffic>0?(rC.units/rC.traffic)*100:0, rPrevConv = rP.traffic>0?(rP.units/rP.traffic)*100:0;
  const bCurConv = bC.traffic>0?(bC.units/bC.traffic)*100:0, bPrevConv = bP.traffic>0?(bP.units/bP.traffic)*100:0;
  const rCurTacos = rC.gmv>0?(rC.adSpend/rC.gmv)*100:0, rPrevTacos = rP.gmv>0?(rP.adSpend/rP.gmv)*100:0;
  const bCurTacos = bC.gmv>0?(bC.adSpend/bC.gmv)*100:0, bPrevTacos = bP.gmv>0?(bP.adSpend/bP.gmv)*100:0;

  document.getElementById('ukKpiGrid').innerHTML=[
    kpiCard('Total GMV',tC.gmv,tP.gmv,v=>fmt(v,'£'),'#00e5ff',[{label:'Retail',cur:rC.gmv,prev:rP.gmv},{label:'Business',cur:bC.gmv,prev:bP.gmv}]),
    kpiCard('Total Units',tC.units,tP.units,v=>fmtU(v),'#00ff9d',[{label:'Retail',cur:rC.units,prev:rP.units},{label:'Business',cur:bC.units,prev:bP.units}]),
    kpiCard('Traffic',tC.traffic,tP.traffic,v=>fmtU(v),'#b845ff',[{label:'Retail',cur:rC.traffic,prev:rP.traffic},{label:'Business',cur:bC.traffic,prev:bP.traffic}]),
    `<div class="kpi-card" style="--accent:#39ffd6">
      <div class="kpi-label">Conversion Rate</div>
      <div class="kpi-value">${curConvR.toFixed(1)}%</div>
      <div class="kpi-wow ${wCls(curConvR-prevConvR)}">${curConvR>=prevConvR?'▲':'▼'} ${Math.abs(curConvR-prevConvR).toFixed(2)}pp WoW <span style="color:var(--text-muted);font-size:10px;margin-left:4px">${prevConvR.toFixed(1)}% prev</span></div>
      <div class="kpi-breakdown">
        <div class="kpi-breakdown-row"><span class="kpi-breakdown-label">Retail</span><span class="kpi-breakdown-val">${rCurConv.toFixed(1)}%</span><span class="kpi-breakdown-wow ${wCls(rCurConv-rPrevConv)}">${rCurConv>=rPrevConv?'▲':'▼'} ${Math.abs(rCurConv-rPrevConv).toFixed(2)}pp</span></div>
        <div class="kpi-breakdown-row"><span class="kpi-breakdown-label">Business</span><span class="kpi-breakdown-val">${bCurConv.toFixed(1)}%</span><span class="kpi-breakdown-wow ${wCls(bCurConv-bPrevConv)}">${bCurConv>=bPrevConv?'▲':'▼'} ${Math.abs(bCurConv-bPrevConv).toFixed(2)}pp</span></div>
      </div>
    </div>`,
    kpiCard('Ad Spend',tC.adSpend,tP.adSpend,v=>fmt(v,'£'),'#ff3b5c',[{label:'Retail',cur:rC.adSpend,prev:rP.adSpend},{label:'Business',cur:bC.adSpend,prev:bP.adSpend}]),
    kpiCard('Ad Sales',tC.adSales,tP.adSales,v=>fmt(v,'£'),'#ffb800',[{label:'Retail',cur:rC.adSales,prev:rP.adSales},{label:'Business',cur:bC.adSales,prev:bP.adSales}]),
    `<div class="kpi-card" style="--accent:#ff7c2a">
      <div class="kpi-label">TACOS</div>
      <div class="kpi-value" style="color:${curTacos<10?'var(--neon-green)':curTacos<20?'var(--neon-amber)':'var(--neon-red)'}">${curTacos.toFixed(1)}%</div>
      <div class="kpi-wow ${curTacos<=prevTacos?'up':'down'}">${curTacos<=prevTacos?'▼':'▲'} ${Math.abs(curTacos-prevTacos).toFixed(2)}pp WoW <span style="color:var(--text-muted);font-size:10px;margin-left:4px">${prevTacos.toFixed(1)}% prev</span></div>
      <div class="kpi-breakdown">
        <div class="kpi-breakdown-row"><span class="kpi-breakdown-label">Retail</span><span class="kpi-breakdown-val" style="color:${rCurTacos<15?'var(--neon-green)':rCurTacos<25?'var(--neon-amber)':'var(--neon-red)'}">${rCurTacos.toFixed(1)}%</span><span class="kpi-breakdown-wow ${rCurTacos<=rPrevTacos?'up':'down'}">${rCurTacos<=rPrevTacos?'▼':'▲'} ${Math.abs(rCurTacos-rPrevTacos).toFixed(2)}pp</span></div>
        <div class="kpi-breakdown-row"><span class="kpi-breakdown-label">Business</span><span class="kpi-breakdown-val" style="color:${bCurTacos<15?'var(--neon-green)':bCurTacos<25?'var(--neon-amber)':'var(--neon-red)'}">${bCurTacos.toFixed(1)}%</span><span class="kpi-breakdown-wow ${bCurTacos<=bPrevTacos?'up':'down'}">${bCurTacos<=bPrevTacos?'▼':'▲'} ${Math.abs(bCurTacos-bPrevTacos).toFixed(2)}pp</span></div>
      </div>
    </div>`,
  ].join('');

  renderInsights(buildInsights(merged,'£'),'ukInsights');

  const rH=R.history,bH=B?B.history:[];
  const last12=rH.slice(-12);
  const labels=last12.map(h=>h.label.split(/[\s-]+/).slice(0,3).join(' '));
  const gmvData=last12.map((h,i)=>h.gmv+(bH[rH.length-12+i]?.gmv||0));
  const spData=last12.map((h,i)=>h.adSpend+(bH[rH.length-12+i]?.adSpend||0));
  const saData=last12.map((h,i)=>h.adSales+(bH[rH.length-12+i]?.adSales||0));
  lineChart('ukGmvChart',labels,gmvData,'GMV (£)','#00e5ff');
  barChart('ukAdsChart',labels,spData,saData);

  const cats=byCat(merged);
  document.getElementById('ukCatRows').innerHTML=catRows(cats,'£');
  const cNames=Object.keys(cats).sort((a,b)=>cats[b].cur.gmv-cats[a].cur.gmv);
  doughnut('ukCatChart',cNames,cNames.map(c=>cats[c].cur.gmv),cNames.map(c=>getCatColor(c)));
  renderDonutStats(cats,'£','ukDonutStats');

  renderAdsPerformance(merged,'£','ukAdsSummary','ukAdsBody','ukAdsSpendChart','ukAcosChart');

  const combHist=R.history.map((h,i)=>{const b=bH[i];return{...h,gmv:h.gmv+(b?.gmv||0),units:h.units+(b?.units||0),traffic:h.traffic+(b?.traffic||0),adSpend:h.adSpend+(b?.adSpend||0),adSales:h.adSales+(b?.adSales||0)};});

  renderSplit(merged,combHist,'£','ukSplitCard','ukSplitChart');

  const health=calcInventoryHealth(merged);
  renderInvGrid(health,'£','ukInvGrid','ukInvPills');

  document.getElementById('ukAsinBody').innerHTML=asinRows(merged,'£');
  document.getElementById('ukHistoryBody').innerHTML=histRows(combHist,'£');
}

// ═══════════════════════════════════════════════════════
// EU PER-MARKETPLACE PANEL RENDERER
// ═══════════════════════════════════════════════════════
function renderEuMktPanel(mkt) {
  const meta = MKT_META[mkt];
  if (!rawData[mkt]) return;
  const mktAsins = rawData[mkt].asins;
  const mktHist  = rawData[mkt].history;
  const tC = agg(mktAsins,'cur'), tP = agg(mktAsins,'prev');
  const cats = byCat(mktAsins);
  const cNames = Object.keys(cats).sort((a,b)=>cats[b].cur.gmv-cats[a].cur.gmv);
  const convR = tC.traffic>0?(tC.units/tC.traffic)*100:0;
  const tacos  = tC.gmv>0?(tC.adSpend/tC.gmv)*100:0;
  const panelId = `euPanel_${mkt}`;
  const spChartId  = `${mkt}_spendChart`;
  const acosChId   = `${mkt}_acosChart`;
  const gmvChId    = `${mkt}_gmvChart`;
  const catChId    = `${mkt}_catChart`;
  const statId     = `${mkt}_donutStats`;
  const catRowsId  = `${mkt}_catRows`;
  const kpiId      = `${mkt}_kpiGrid`;
  const asinBodyId = `${mkt}_asinBody`;
  const histBodyId = `${mkt}_histBody`;
  const adsSumId   = `${mkt}_adsSummary`;
  const adsBodyId  = `${mkt}_adsBody`;
  const splitCardId= `${mkt}_splitCard`;
  const splitChId  = `${mkt}_splitChart`;

  const panel = document.getElementById(panelId);
  if (!panel) return;

  panel.innerHTML = `
    <div style="margin-bottom:20px;padding:14px 20px;background:rgba(${meta.color==='#00e5ff'?'0,229,255':meta.color==='#00ff9d'?'0,255,157':meta.color==='#b845ff'?'184,69,255':'255,184,0'},0.06);border:1px solid ${meta.color}33;border-radius:12px;display:flex;gap:40px;align-items:center;flex-wrap:wrap;">
      <div><div style="font-family:var(--font-mono);font-size:10px;color:var(--text-muted);text-transform:uppercase;letter-spacing:1px;margin-bottom:4px">GMV</div><div style="font-family:var(--font-display);font-size:24px;font-weight:800;color:${meta.color}">${fmt(tC.gmv,'€')}</div><div style="font-family:var(--font-mono);font-size:11px;color:${wCls(pct(tC.gmv,tP.gmv))==='up'?'var(--neon-green)':'var(--neon-red)'}">${wArr(pct(tC.gmv,tP.gmv))} ${Math.abs(pct(tC.gmv,tP.gmv)).toFixed(1)}% WoW</div></div>
      <div><div style="font-family:var(--font-mono);font-size:10px;color:var(--text-muted);text-transform:uppercase;letter-spacing:1px;margin-bottom:4px">Units</div><div style="font-family:var(--font-display);font-size:24px;font-weight:800">${fmtU(tC.units)}</div><div style="font-family:var(--font-mono);font-size:11px;color:${wCls(pct(tC.units,tP.units))==='up'?'var(--neon-green)':'var(--neon-red)'}">${wArr(pct(tC.units,tP.units))} ${Math.abs(pct(tC.units,tP.units)).toFixed(1)}% WoW</div></div>
      <div><div style="font-family:var(--font-mono);font-size:10px;color:var(--text-muted);text-transform:uppercase;letter-spacing:1px;margin-bottom:4px">Traffic</div><div style="font-family:var(--font-display);font-size:24px;font-weight:800">${fmtU(tC.traffic)}</div></div>
      <div><div style="font-family:var(--font-mono);font-size:10px;color:var(--text-muted);text-transform:uppercase;letter-spacing:1px;margin-bottom:4px">Conv Rate</div><div style="font-family:var(--font-display);font-size:24px;font-weight:800">${convR.toFixed(1)}%</div></div>
      <div><div style="font-family:var(--font-mono);font-size:10px;color:var(--text-muted);text-transform:uppercase;letter-spacing:1px;margin-bottom:4px">Ad Spend</div><div style="font-family:var(--font-display);font-size:24px;font-weight:800;color:var(--neon-red)">${fmt(tC.adSpend,'€')}</div></div>
      <div><div style="font-family:var(--font-mono);font-size:10px;color:var(--text-muted);text-transform:uppercase;letter-spacing:1px;margin-bottom:4px">TACOS</div><div style="font-family:var(--font-display);font-size:24px;font-weight:800;color:${tacos<15?'var(--neon-green)':tacos<25?'var(--neon-amber)':'var(--neon-red)'}">${tacos.toFixed(1)}%</div></div>
    </div>

    <div class="section-title">Category Performance — ${meta.label}</div>
    <div class="category-grid">
      <div class="cat-table-card">
        <div class="cat-table-header"><div class="chart-title">GMV by Category</div></div>
        <div class="cat-row hdr"><div class="cat-row-name">Category</div><div class="crv">GMV</div><div class="crv">Units</div><div class="crw">WoW</div></div>
        <div id="${catRowsId}"></div>
      </div>
      <div class="donut-card">
        <div class="cat-table-header"><div class="chart-title">Category Split</div></div>
        <div class="donut-wrap"><canvas id="${catChId}"></canvas></div>
        <div class="donut-stats" id="${statId}"></div>
      </div>
    </div>

    <div class="section-title">GMV Trend — ${meta.label}</div>
    <div class="chart-card" style="margin-bottom:28px">
      <div class="chart-header"><div><div class="chart-title">12-Week GMV Trend</div><div class="chart-subtitle">${meta.label} · €EUR</div></div></div>
      <div class="chart-wrap"><canvas id="${gmvChId}"></canvas></div>
    </div>

    <div class="section-title">💰 Ads Performance — ${meta.label}</div>
    <div class="ads-summary-grid" id="${adsSumId}"></div>
    <div class="ads-cat-card" style="margin-bottom:28px">
      <div class="ads-cat-header"><div class="chart-title">Category Ad Breakdown</div></div>
      <div style="overflow-x:auto">
        <table class="ads-table">
          <thead><tr><th>Category</th><th>Ad Spend</th><th>WoW Spend</th><th>Ad Sales</th><th>WoW Sales</th><th>ACOS</th><th>ROAS</th><th>TACOS</th><th>Total GMV</th><th>Efficiency</th></tr></thead>
          <tbody id="${adsBodyId}"></tbody>
        </table>
      </div>
    </div>
    <div class="ads-chart-row">
      <div class="chart-card">
        <div class="chart-header"><div><div class="chart-title">Ad Spend by Category</div></div></div>
        <div class="chart-wrap"><canvas id="${spChartId}"></canvas></div>
      </div>
      <div class="chart-card">
        <div class="chart-header"><div><div class="chart-title">ACOS by Category</div></div></div>
        <div class="chart-wrap"><canvas id="${acosChId}"></canvas></div>
      </div>
    </div>

    <div class="section-title">🔀 Organic vs Paid — ${meta.label}</div>
    <div class="split-row" style="margin-bottom:28px">
      <div class="split-card" id="${splitCardId}"></div>
      <div class="chart-card">
        <div class="chart-header"><div><div class="chart-title">Paid vs Organic — 12 Week Trend</div></div></div>
        <div class="chart-wrap"><canvas id="${splitChId}"></canvas></div>
      </div>
    </div>

    <div class="section-title">ASIN Performance — ${meta.label}</div>
    <div class="asin-card" style="margin-bottom:28px">
      <div class="asin-card-header"><div class="chart-title">Top Products</div></div>
      <div style="overflow-x:auto">
        <table class="asin-table">
          <thead><tr><th>Product</th><th>Category</th><th style="text-align:right">GMV (€)</th><th style="text-align:right">Units</th><th style="text-align:right">Traffic</th><th style="text-align:right">Conv%</th><th style="text-align:right">Ad Spend</th><th style="text-align:right">TACOS</th><th style="text-align:right">WoW GMV</th></tr></thead>
          <tbody id="${asinBodyId}"></tbody>
        </table>
      </div>
    </div>`;

  // Render data into the panel
  document.getElementById(catRowsId).innerHTML = catRows(cats,'€');
  doughnut(catChId, cNames, cNames.map(c=>cats[c].cur.gmv), cNames.map(c=>getCatColor(c)));
  renderDonutStats(cats,'€',statId);

  const last12 = mktHist.slice(-12);
  lineChart(gmvChId, last12.map(h=>h.label.split(/[\s-]+/).slice(0,3).join(' ')), last12.map(h=>h.gmv), `${meta.label} GMV (€)`, meta.color);

  renderAdsPerformance(mktAsins,'€',adsSumId,adsBodyId,spChartId,acosChId);
  renderSplit(mktAsins,mktHist,'€',splitCardId,splitChId);
  document.getElementById(asinBodyId).innerHTML = asinRows(mktAsins,'€');
}

// ═══════════════════════════════════════════════════════
// EU RENDER
// ═══════════════════════════════════════════════════════
function renderEU(){
  const available=['eu_de','eu_fr','eu_it','eu_es'].filter(m=>rawData[m]);
  if(!available.length){showErr('euError','No EU market data loaded.');return;}

  const ref=rawData[available[0]];
  document.getElementById('euCurrentWeek').textContent=ref.curWk.label;
  document.getElementById('euVsWeek').textContent=`vs ${ref.prevWk?.label||'prior week'}`;

  const all=[];
  for(const m of available){
    for(const a of rawData[m].asins){
      const ex=all.find(x=>x.asin===a.asin);
      if(ex){
        ex.cur.gmv+=a.cur.gmv; ex.cur.units+=a.cur.units; ex.cur.traffic+=a.cur.traffic; ex.cur.adSpend+=a.cur.adSpend; ex.cur.adSales+=a.cur.adSales;
        ex.prev.gmv+=a.prev.gmv; ex.prev.units+=a.prev.units; ex.prev.traffic+=a.prev.traffic; ex.prev.adSpend+=a.prev.adSpend; ex.prev.adSales+=a.prev.adSales;
      } else {
        all.push(JSON.parse(JSON.stringify(a)));
      }
    }
  }
  euAsins=all; euAllAsins=all;

  const tC=agg(all,'cur'),tP=agg(all,'prev');
  const mktAgg = available.map(m=>({
    key:m, label:MKT_META[m].label,
    cur:agg(rawData[m].asins,'cur'),
    prev:agg(rawData[m].asins,'prev'),
  }));

  const curConvR = tC.traffic>0?(tC.units/tC.traffic)*100:0;
  const prevConvR = tP.traffic>0?(tP.units/tP.traffic)*100:0;
  const curTacos = tC.gmv>0?(tC.adSpend/tC.gmv)*100:0;
  const prevTacos = tP.gmv>0?(tP.adSpend/tP.gmv)*100:0;

  document.getElementById('euKpiGrid').innerHTML=[
    kpiCard('Total GMV (€)',tC.gmv,tP.gmv,v=>fmt(v,'€'),'#b845ff',mktAgg.map(m=>({label:m.label,cur:m.cur.gmv,prev:m.prev.gmv}))),
    kpiCard('Total Units',tC.units,tP.units,v=>fmtU(v),'#00ff9d',mktAgg.map(m=>({label:m.label,cur:m.cur.units,prev:m.prev.units}))),
    kpiCard('Traffic',tC.traffic,tP.traffic,v=>fmtU(v),'#00e5ff',mktAgg.map(m=>({label:m.label,cur:m.cur.traffic,prev:m.prev.traffic}))),
    `<div class="kpi-card" style="--accent:#39ffd6">
      <div class="kpi-label">Conversion Rate</div>
      <div class="kpi-value">${curConvR.toFixed(1)}%</div>
      <div class="kpi-wow ${wCls(curConvR-prevConvR)}">${curConvR>=prevConvR?'▲':'▼'} ${Math.abs(curConvR-prevConvR).toFixed(2)}pp WoW <span style="color:var(--text-muted);font-size:10px;margin-left:4px">${prevConvR.toFixed(1)}% prev</span></div>
      <div class="kpi-breakdown">${mktAgg.map(m=>{const cc=m.cur.traffic>0?(m.cur.units/m.cur.traffic)*100:0;const pc=m.prev.traffic>0?(m.prev.units/m.prev.traffic)*100:0;const diff=cc-pc;return`<div class="kpi-breakdown-row"><span class="kpi-breakdown-label">${m.label}</span><span class="kpi-breakdown-val">${cc.toFixed(1)}%</span><span class="kpi-breakdown-wow ${wCls(diff)}">${diff>=0?'▲':'▼'} ${Math.abs(diff).toFixed(2)}pp</span></div>`;}).join('')}</div>
    </div>`,
    kpiCard('Ad Spend',tC.adSpend,tP.adSpend,v=>fmt(v,'€'),'#ff3b5c',mktAgg.map(m=>({label:m.label,cur:m.cur.adSpend,prev:m.prev.adSpend}))),
    kpiCard('Ad Sales',tC.adSales,tP.adSales,v=>fmt(v,'€'),'#ffb800',mktAgg.map(m=>({label:m.label,cur:m.cur.adSales,prev:m.prev.adSales}))),
    `<div class="kpi-card" style="--accent:#ff7c2a">
      <div class="kpi-label">TACOS</div>
      <div class="kpi-value" style="color:${curTacos<10?'var(--neon-green)':curTacos<20?'var(--neon-amber)':'var(--neon-red)'}">${curTacos.toFixed(1)}%</div>
      <div class="kpi-wow ${curTacos<=prevTacos?'up':'down'}">${curTacos<=prevTacos?'▼':'▲'} ${Math.abs(curTacos-prevTacos).toFixed(2)}pp WoW <span style="color:var(--text-muted);font-size:10px;margin-left:4px">${prevTacos.toFixed(1)}% prev</span></div>
      <div class="kpi-breakdown">${mktAgg.map(m=>{const ct=m.cur.gmv>0?(m.cur.adSpend/m.cur.gmv)*100:0;const pt=m.prev.gmv>0?(m.prev.adSpend/m.prev.gmv)*100:0;const diff=ct-pt;return`<div class="kpi-breakdown-row"><span class="kpi-breakdown-label">${m.label}</span><span class="kpi-breakdown-val" style="color:${ct<15?'var(--neon-green)':ct<25?'var(--neon-amber)':'var(--neon-red)'}">${ct.toFixed(1)}%</span><span class="kpi-breakdown-wow ${ct<=pt?'up':'down'}">${ct<=pt?'▼':'▲'} ${Math.abs(diff).toFixed(2)}pp</span></div>`;}).join('')}</div>
    </div>`,
  ].join('');

  renderInsights(buildInsights(all,'€'),'euInsights');

  const mktLabels=available.map(m=>MKT_META[m].label);
  const mktGmvs=available.map(m=>agg(rawData[m].asins,'cur').gmv);
  const mktColors=available.map(m=>MKT_META[m].color);
  hBarChart('euMktChart',mktLabels,mktGmvs,mktColors);

  const refH=ref.history,hLen=refH.length,l12=Math.max(0,hLen-12);
  lineChart('euTrendChart',refH.slice(l12).map(h=>h.label.split(/[\s-]+/).slice(0,3).join(' ')),refH.slice(l12).map((_,i)=>available.reduce((s,m)=>s+(rawData[m].history[l12+i]?.gmv||0),0)),'EU GMV (€)','#b845ff');

  doughnut('euPieChart',mktLabels,mktGmvs,mktColors);
  const totalEuGmv=mktGmvs.reduce((s,v)=>s+v,0);
  document.getElementById('euDonutStats').innerHTML=available.slice(0,4).map((m,i)=>{
    const cur=mktGmvs[i],prev=agg(rawData[m].asins,'prev').gmv,p=pct(cur,prev),cls=wCls(p),share=totalEuGmv>0?((cur/totalEuGmv)*100).toFixed(0):0;
    return `<div class="donut-stat"><div class="donut-stat-label"><span style="display:inline-block;width:6px;height:6px;border-radius:50%;background:${MKT_META[m].color};margin-right:5px;vertical-align:middle"></span>${MKT_META[m].label}</div><div class="donut-stat-val" style="color:${MKT_META[m].color}">${fmt(cur,'€')}</div><div class="donut-stat-sub ${cls}">${share}% share · ${wArr(p)}${Math.abs(p).toFixed(1)}% WoW</div></div>`;
  }).join('');

  const cats=byCat(all);
  document.getElementById('euCatRows').innerHTML=catRows(cats,'€');

  renderAdsPerformance(all,'€','euAdsSummary','euAdsBody','euAdsSpendChart','euAcosChart');

  const euHist=ref.history.map((h,i)=>{
    let gmv=0,units=0,traffic=0,adSpend=0,adSales=0;
    for(const m of available){const mh=rawData[m].history[i];if(mh){gmv+=mh.gmv;units+=mh.units;traffic+=mh.traffic;adSpend+=mh.adSpend;adSales+=mh.adSales;}}
    return{...h,gmv,units,traffic,adSpend,adSales};
  });

  renderSplit(all,euHist,'€','euSplitCard','euSplitChart');
  renderEuInvPerMarket(available);
  document.getElementById('euAsinBody').innerHTML=asinRows(all,'€');

  let euHistHtml='';
  for(let i=euHist.length-1;i>=0;i--){
    const h=euHist[i];if(h.gmv===0)continue;
    const prev=i>0?euHist[i-1]:null,p=prev?pct(h.gmv,prev.gmv):0,cls=wCls(p),tacos=h.gmv>0?(h.adSpend/h.gmv)*100:0;
    const convR=h.traffic>0?(h.units/h.traffic)*100:0;
    euHistHtml+=`<tr class="${h.isCurrent?'cur-wk':''}"><td>${h.label}${h.isCurrent?' ◀ Current':''}</td><td>${fmt(h.gmv,'€')}</td><td>${fmtU(h.units)}</td><td>${fmtU(h.traffic)}</td><td>${convR>0?convR.toFixed(1)+'%':'—'}</td><td>${fmt(h.adSpend,'€')}</td><td>${tacos>0?tacos.toFixed(1)+'%':'—'}</td><td><span class="wow-pill ${cls}">${prev?wArr(p)+' '+Math.abs(p).toFixed(1)+'%':'—'}</span></td></tr>`;
  }
  document.getElementById('euHistoryBody').innerHTML=euHistHtml;

  // ─── FIX 2: Pre-render all per-marketplace panels so tabs work immediately
  for(const mkt of available){
    renderEuMktPanel(mkt);
  }
}

// ═══════════════════════════════════════════════════════
// INTERACTION
// ═══════════════════════════════════════════════════════
function filterAsins(type,page,btn){
  btn.closest('.asin-filters').querySelectorAll('.filter-btn').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  const src=page==='uk'?ukAsins:euAsins,pre=page==='uk'?'£':'€';
  let filtered=src;
  if(type==='winners') filtered=[...src].filter(a=>a.prev&&pct(a.cur.gmv,a.prev.gmv)>5).sort((a,b)=>pct(b.cur.gmv,b.prev.gmv)-pct(a.cur.gmv,a.prev.gmv));
  else if(type==='losers') filtered=[...src].filter(a=>a.prev&&pct(a.cur.gmv,a.prev.gmv)<-5).sort((a,b)=>pct(a.cur.gmv,a.prev.gmv)-pct(b.cur.gmv,b.prev.gmv));
  else if(type==='hero') filtered=[...src].sort((a,b)=>b.cur.gmv-a.cur.gmv).slice(0,10);
  document.getElementById(page+'AsinBody').innerHTML=asinRows(filtered,pre);
}

// ─── FIX 2: showEuMkt now actually switches visible panels
function showEuMkt(mkt, btn) {
  // Update tab active state
  document.querySelectorAll('.mkt-tab').forEach(b => b.classList.remove('active'));
  btn.classList.add('active');
  // Show the correct panel, hide the rest
  ['combined','eu_de','eu_fr','eu_it','eu_es'].forEach(key => {
    const panel = document.getElementById(`euPanel_${key}`);
    if (panel) {
      panel.classList.toggle('active', key === mkt);
    }
  });
}

function showPage(page,evt){document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));document.querySelectorAll('.tab-btn').forEach(b=>b.classList.remove('active'));document.getElementById('page-'+page).classList.add('active');if(evt&&evt.target)evt.target.classList.add('active');}
function showErr(id,msg){const el=document.getElementById(id);if(el){el.style.display='block';el.textContent=msg;}}

// ═══════════════════════════════════════════════════════
// DATA FETCH
// ═══════════════════════════════════════════════════════
function fetchSheet(key){
  return new Promise((resolve,reject)=>{
    const cb='cb_'+key+'_'+Date.now(),script=document.createElement('script');
    const timer=setTimeout(()=>{delete window[cb];if(document.body.contains(script))document.body.removeChild(script);reject(new Error('Timeout: '+key));},25000);
    window[cb]=data=>{clearTimeout(timer);delete window[cb];if(document.body.contains(script))document.body.removeChild(script);data.error?reject(new Error(data.error)):resolve(data.csv);};
    script.src=`${GAS_URL}?sheet=${key}&callback=${cb}`;
    script.onerror=()=>{clearTimeout(timer);reject(new Error('Load failed: '+key));};
    document.body.appendChild(script);
  });
}

async function loadAllData(){
  const status=document.getElementById('loadingStatus');
  for(const key of SHEET_KEYS){
    try{
      status.textContent='Loading '+key.replace(/_/g,' ').toUpperCase()+'...';
      const csv=await fetchSheet(key);
      const parsed=parseSheetData(csv);
      if(parsed) rawData[key]=parsed;
      else console.warn(`⚠️ ${key}: parsed but no data`);
    }catch(e){console.warn(`❌ ${key}: ${e.message}`);}
  }
  document.getElementById('loadingScreen').style.display='none';
  document.getElementById('lastUpdated').textContent='Updated '+new Date().toLocaleTimeString();
  if(rawData.uk_retail||rawData.uk_business) renderUK();
  if(rawData.eu_de||rawData.eu_fr||rawData.eu_it||rawData.eu_es) renderEU();
}

async function refreshData(){
  const btn=document.getElementById('refreshBtn');
  btn.classList.add('spinning');
  document.getElementById('refreshLabel').textContent='Refreshing...';
  rawData={};
  try{await loadAllData();}finally{btn.classList.remove('spinning');document.getElementById('refreshLabel').textContent='Refresh';}
}

setInterval(refreshData,REFRESH_MS);
loadAllData();
</script>
</body>
</html>
