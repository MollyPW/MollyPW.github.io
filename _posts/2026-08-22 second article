
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>TrueTail Pet Insurance — Coverage Match Nurture Program</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --bg:#F7F5F0;
    --panel:#FFFFFF;
    --ink:#1C1C1A;
    --ink-soft:#5B5B56;
    --ink-faint:#8B8A82;
    --brand:#16333A;
    --brand-soft:#3E5A61;
    --line:#D8D4C8;

    --dog:#B8860B;      --dog-bg:#FBF2DD;      --dog-ink:#6B4E06;
    --cat:#6E4B8A;       --cat-bg:#F1EBF6;      --cat-ink:#4A3160;
    --rabbit:#B85C38;    --rabbit-bg:#F8E9E1;   --rabbit-ink:#7A3B22;
    --fish:#2E8B8B;      --fish-bg:#E5F3F3;     --fish-ink:#1D5A5A;
    --bird:#B23A48;      --bird-bg:#F9E4E7;     --bird-ink:#7A2531;
  }
  *{box-sizing:border-box;}
  body{
    margin:0; padding:48px 24px 80px; background:var(--bg);
    font-family:'Inter',system-ui,sans-serif; color:var(--ink);
  }
  .wrap{max-width:980px; margin:0 auto;}

  header{margin-bottom:40px;}
  .eyebrow{
    font-family:'JetBrains Mono',monospace; font-size:12px; letter-spacing:.06em;
    color:var(--brand-soft); text-transform:uppercase; margin:0 0 10px;
  }
  h1{font-size:30px; font-weight:700; margin:0 0 8px; letter-spacing:-.01em;}
  .sub{font-size:15px; color:var(--ink-soft); max-width:640px; line-height:1.55; margin:0;}
  .fictional-tag{
    display:inline-block; margin-top:14px; font-family:'JetBrains Mono',monospace;
    font-size:11px; color:var(--ink-faint); border:1px solid var(--line); border-radius:4px;
    padding:4px 8px; letter-spacing:.02em;
  }

  .legend{
    display:flex; flex-wrap:wrap; gap:10px; margin:28px 0 44px;
    padding:16px 18px; background:var(--panel); border:1px solid var(--line); border-radius:10px;
  }
  .legend-item{display:flex; align-items:center; gap:7px; font-size:13px; color:var(--ink-soft);}
  .swatch{width:11px; height:11px; border-radius:3px; flex:none;}

  .section-label{
    font-family:'JetBrains Mono',monospace; font-size:11px; letter-spacing:.06em;
    text-transform:uppercase; color:var(--brand-soft); margin:0 0 14px;
    display:flex; align-items:center; gap:10px;
  }
  .section-label::after{content:""; flex:1; height:1px; background:var(--line);}

  .flow-col{display:flex; flex-direction:column; align-items:center; margin-bottom:8px;}

  .node{
    background:var(--panel); border:1px solid var(--line); border-radius:10px;
    padding:14px 20px; text-align:center; box-shadow:0 1px 2px rgba(0,0,0,.03);
    max-width:520px; width:100%;
  }
  .node .t{font-size:14px; font-weight:600; line-height:1.4;}
  .node .s{font-size:12.5px; color:var(--ink-soft); margin-top:3px; line-height:1.45;}
  .node.neutral{background:#FBFAF7;}
  .node.brand{background:var(--brand); border-color:var(--brand);}
  .node.brand .t{color:#fff;}
  .node.brand .s{color:#B9C7C9;}

  .arrow{width:1.5px; height:26px; background:var(--line); position:relative;}
  .arrow::after{
    content:""; position:absolute; bottom:-1px; left:50%; transform:translateX(-50%);
    border-left:5px solid transparent; border-right:5px solid transparent;
    border-top:6px solid var(--line);
  }

  .branch-row{
    display:flex; gap:14px; flex-wrap:wrap; justify-content:center; width:100%; margin:4px 0;
  }
  .pill{
    flex:1 1 150px; min-width:130px; border-radius:10px; padding:12px 14px;
    text-align:center; border:1px solid transparent;
  }
  .pill .t{font-size:13px; font-weight:600;}
  .pill .s{font-size:11.5px; margin-top:2px; opacity:.85;}
  .pill.dog{background:var(--dog-bg); color:var(--dog-ink); border-color:var(--dog);}
  .pill.cat{background:var(--cat-bg); color:var(--cat-ink); border-color:var(--cat);}
  .pill.rabbit{background:var(--rabbit-bg); color:var(--rabbit-ink); border-color:var(--rabbit);}
  .pill.fish{background:var(--fish-bg); color:var(--fish-ink); border-color:var(--fish);}
  .pill.bird{background:var(--bird-bg); color:var(--bird-ink); border-color:var(--bird);}

  .or-label{
    font-family:'JetBrains Mono',monospace; font-size:10.5px; color:var(--ink-faint);
    margin:2px 0; letter-spacing:.05em;
  }

  .node.concept{
    background:var(--panel); border:1.5px dashed var(--brand-soft); position:relative;
  }
  .concept-badge{
    display:inline-block; font-family:'JetBrains Mono',monospace; font-size:9.5px;
    font-weight:600; letter-spacing:.04em; text-transform:uppercase; color:var(--brand-soft);
    border:1px solid var(--brand-soft); border-radius:20px; padding:2px 8px; margin-bottom:6px;
  }

  .panel-note{
    background:var(--panel); border:1px dashed var(--line); border-radius:10px;
    padding:14px 18px; font-size:12.5px; color:var(--ink-soft); max-width:560px;
    margin:18px auto 0; text-align:center; line-height:1.55;
  }
  .panel-note b{color:var(--ink); font-weight:600;}

  /* bird branch detail */
  .branch-detail{
    margin-top:64px; border-top:2px solid var(--bird); padding-top:36px;
  }
  .branch-title{display:flex; align-items:center; gap:10px; margin-bottom:6px;}
  .branch-title .dot{width:10px; height:10px; border-radius:50%; background:var(--bird);}
  .branch-title h2{font-size:19px; font-weight:700; margin:0;}
  .branch-desc{font-size:13.5px; color:var(--ink-soft); margin:0 0 30px; max-width:600px; line-height:1.55;}

  .node.bird{background:var(--bird-bg); border-color:var(--bird);}
  .node.bird .t{color:var(--bird-ink);}
  .node.bird .s{color:var(--bird-ink); opacity:.8;}

  .decision{
    width:170px; height:170px; background:var(--panel); border:1.5px solid var(--brand-soft);
    transform:rotate(45deg); display:flex; align-items:center; justify-content:center;
    margin:10px 0;
  }
  .decision-inner{transform:rotate(-45deg); text-align:center; padding:0 20px;}
  .decision-inner .t{font-size:13px; font-weight:600;}
  .decision-inner .s{font-size:11px; color:var(--ink-soft); margin-top:2px;}

  .yn-row{display:flex; width:100%; max-width:560px; justify-content:space-between; margin-top:-6px;}
  .yn-branch{display:flex; flex-direction:column; align-items:center; width:47%;}
  .yn-tag{
    font-family:'JetBrains Mono',monospace; font-size:11px; font-weight:500;
    padding:2px 10px; border-radius:20px; margin-bottom:4px;
  }
  .yn-tag.yes{background:#E2F0E4; color:#2A6B39;}
  .yn-tag.no{background:#F3E6E6; color:#8A3838;}

  .loop-note{
    display:flex; align-items:center; gap:8px; font-size:12px; color:var(--ink-faint);
    font-family:'JetBrains Mono',monospace; margin:14px 0;
  }
  .loop-note .line{flex:none; width:24px; height:1px; background:var(--line); position:relative;}
  .loop-note .line::after{content:"↻"; position:absolute; left:-4px; top:-9px; font-size:14px;}

  .end-node{
    background:var(--brand); color:#fff; border-radius:20px; padding:8px 22px;
    font-size:12.5px; font-weight:600; font-family:'JetBrains Mono',monospace;
    letter-spacing:.02em;
  }

  .other-branches{margin-top:56px;}
  .other-grid{display:flex; gap:14px; flex-wrap:wrap;}
  .other-card{
    flex:1 1 200px; background:var(--panel); border:1px solid var(--line); border-radius:10px;
    padding:16px 18px; min-width:190px;
  }
  .other-card .head{display:flex; align-items:center; gap:8px; margin-bottom:6px;}
  .other-card .dot{width:9px; height:9px; border-radius:50%; flex:none;}
  .other-card .t{font-size:13.5px; font-weight:600;}
  .other-card .s{font-size:12px; color:var(--ink-soft); line-height:1.5;}
  .other-card .dot.dog{background:var(--dog);}
  .other-card .dot.cat{background:var(--cat);}
  .other-card .dot.rabbit{background:var(--rabbit);}
  .other-card .dot.fish{background:var(--fish);}

  footer{
    margin-top:60px; padding-top:24px; border-top:1px solid var(--line);
    display:flex; flex-direction:column; gap:10px;
  }
  .footnote{display:flex; gap:10px; font-size:12.5px; color:var(--ink-soft); line-height:1.6;}
  .footnote .tag{
    flex:none; font-family:'JetBrains Mono',monospace; font-size:10px; font-weight:600;
    background:var(--brand); color:#fff; border-radius:4px; padding:2px 7px; height:fit-content;
  }
</style>
</head>
<body>
<div class="wrap">

  <header>
    <p class="eyebrow">Marketing operations — automated journey design</p>
    <h1>TrueTail Pet Insurance: coverage-match nurture program</h1>
    <p class="sub">A single welcome email routes new pet parents into one of five species-specific nurture tracks based on first-party click behavior — no guessing, no generic follow-up. Built to demonstrate multi-program MCAE/Pardot architecture: page-action based segmentation, completion-action enrollment, action-rule suppression, and ad-hoc list overrides for manual sales requests.</p>
    <span class="fictional-tag">Fictional brand — illustrative data only</span>
  </header>

  <div class="legend">
    <div class="legend-item"><span class="swatch" style="background:var(--dog)"></span>Dog coverage</div>
    <div class="legend-item"><span class="swatch" style="background:var(--cat)"></span>Cat coverage</div>
    <div class="legend-item"><span class="swatch" style="background:var(--rabbit)"></span>Rabbit coverage</div>
    <div class="legend-item"><span class="swatch" style="background:var(--fish)"></span>Fish &amp; aquatic coverage</div>
    <div class="legend-item"><span class="swatch" style="background:var(--bird)"></span>Bird coverage</div>
  </div>

  <p class="section-label">Entry &amp; routing — shared across all five programs</p>

  <div class="flow-col">
    <div class="node neutral">
      <div class="t">New pet parent enters welcome series</div>
      <div class="s">General "New Pet Parent" Salesforce campaign</div>
    </div>
    <div class="arrow"></div>
    <div class="node brand">
      <div class="t">Welcome email sent</div>
      <div class="s">Features the top article, video, and podcast for each of the five coverage types — one link per pet</div>
    </div>
    <div class="arrow"></div>
    <div class="node concept">
      <span class="concept-badge">design extension — not built</span>
      <div class="t">SMS sent same day</div>
      <div class="s">Third-party SMS platform, triggered via Salesforce Flow · invites a reply confirming pet name, type, age, sex, and location to sharpen content matching beyond click behavior alone</div>
    </div>
    <div class="arrow"></div>
    <div class="or-label">prospect clicks an email asset — OR — replies to the SMS — OR — visits a matching page directly (e.g. via social)</div>
    <div class="arrow"></div>
    <div class="node neutral">
      <div class="t">Page action / completion action fires</div>
      <div class="s">Adds prospect to the matching coverage list, now informed by declared profile data · action rule removes them from the general welcome campaign</div>
    </div>
    <div class="arrow"></div>
    <div class="branch-row" style="margin-top:6px;">
      <div class="pill dog"><div class="t">Dog</div><div class="s">coverage program</div></div>
      <div class="pill cat"><div class="t">Cat</div><div class="s">coverage program</div></div>
      <div class="pill rabbit"><div class="t">Rabbit</div><div class="s">coverage program</div></div>
      <div class="pill fish"><div class="t">Fish</div><div class="s">coverage program</div></div>
      <div class="pill bird"><div class="t">Bird</div><div class="s">coverage program</div></div>
    </div>
  </div>

  <div class="branch-detail">
    <div class="branch-title"><span class="dot"></span><h2>Bird coverage program — shown in full</h2></div>
    <p class="branch-desc">All five programs share this exact structure. Bird is drawn in detail here; the other four are identical in mechanism with species-specific content, shown condensed below.</p>

    <div class="flow-col">
      <div class="node bird">
        <div class="t">Entry: "bird_coverage_page_action" tag added to profile</div>
        <div class="s">Fires on email click OR direct page visit</div>
      </div>
      <div class="arrow"></div>
      <div class="node neutral">
        <div class="t">Added to Bird Coverage static enrollment list</div>
        <div class="s">Ad-hoc list — sales can manually add or exclude specific prospects regardless of behavior</div>
      </div>
      <div class="arrow"></div>
      <div class="node neutral">
        <div class="t">Added to Bird Coverage Nurture Salesforce campaign</div>
      </div>
      <div class="arrow"></div>
      <div class="node bird">
        <div class="t">Email sent</div>
        <div class="s">Bird-specific coverage content</div>
      </div>
      <div class="arrow"></div>
      <div class="node neutral">
        <div class="t">Wait 3 days</div>
      </div>
      <div class="arrow"></div>
      <div class="decision">
        <div class="decision-inner">
          <div class="t">Link clicked?</div>
        </div>
      </div>
      <div class="yn-row">
        <div class="yn-branch">
          <span class="yn-tag yes">yes</span>
          <div class="node bird" style="max-width:100%;">
            <div class="t">Added to Bird Coverage success list</div>
            <div class="s">Suppressed from further nurture</div>
          </div>
          <div class="arrow"></div>
          <div class="end-node">end — sales handoff</div>
        </div>
        <div class="yn-branch">
          <span class="yn-tag no">no</span>
          <div class="node neutral" style="max-width:100%;">
            <div class="t">Continues to next email</div>
          </div>
          <div class="loop-note"><span class="line"></span>repeats through emails 2–4, same send → wait → click check</div>
          <div class="arrow"></div>
          <div class="end-node" style="background:#7A2531;">end — unsuccessful list, tagged for 6-month re-engagement</div>
        </div>
      </div>
    </div>
  </div>

  <div class="other-branches">
    <p class="section-label">Same structure, remaining four programs</p>
    <div class="other-grid">
      <div class="other-card">
        <div class="head"><span class="dot dog"></span><span class="t">Dog coverage</span></div>
        <div class="s">Identical 4-email nurture cycle, dog-specific content and completion lists</div>
      </div>
      <div class="other-card">
        <div class="head"><span class="dot cat"></span><span class="t">Cat coverage</span></div>
        <div class="s">Identical 4-email nurture cycle, cat-specific content and completion lists</div>
      </div>
      <div class="other-card">
        <div class="head"><span class="dot rabbit"></span><span class="t">Rabbit coverage</span></div>
        <div class="s">Identical 4-email nurture cycle, rabbit-specific content and completion lists</div>
      </div>
      <div class="other-card">
        <div class="head"><span class="dot fish"></span><span class="t">Fish &amp; aquatic coverage</span></div>
        <div class="s">Identical 4-email nurture cycle, fish-specific content and completion lists</div>
      </div>
    </div>
  </div>

  <footer>
    <div class="footnote"><span class="tag">design extension</span>SMS paired with email for a reason: a short reply-to-confirm text converts declared data (species, age, sex, location) that an email click alone can't capture, so the routing decision downstream relies on stated facts rather than inferred interest — fewer prospects land in the wrong coverage track, and profile data collected here can also inform future personalization beyond just which program they enter.</div>
    <div class="footnote"><span class="tag">note</span>Every branch supports static ad-hoc lists layered on top of the behavioral logic — sales can request a specific prospect be manually added to or excluded from any program at any time, independent of their click behavior.</div>
    <div class="footnote"><span class="tag">note</span>Entering any coverage-specific program always triggers suppression from the general welcome campaign via an action rule, so no prospect receives both tracks simultaneously.</div>
  </footer>

</div>
</body>
</html>

