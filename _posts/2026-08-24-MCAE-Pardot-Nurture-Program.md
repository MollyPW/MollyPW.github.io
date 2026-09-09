
<html lang="en">
<head>
<meta charset="UTF-8">
<title>TrueTail Pet Insurance - Coverage Match Nurture Program</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">
<style>
  :root{
    --navy:#1D3557;
    --red:#E63946;
    --steel:#457B9D;
    --teal:#A8DADC;
    --offwhite:#F1FAEE;
    --white:#FFFFFF;
    --line:rgba(29,53,87,.18);
    --navy-soft:rgba(29,53,87,.68);
    --navy-faint:rgba(29,53,87,.48);
  }
  *{box-sizing:border-box;}
  body{
    margin:0; padding:48px 24px 80px; background:var(--offwhite);
    font-family:'DM Sans',system-ui,sans-serif; color:var(--navy);
  }
  .wrap{max-width:980px; margin:0 auto;}

  header{margin-bottom:40px;}
  .eyebrow{
    font-family:'DM Sans',sans-serif; font-size:12px; font-weight:700; letter-spacing:.08em;
    color:var(--navy-soft); text-transform:uppercase; margin:0 0 10px;
  }
  h1{font-size:30px; font-weight:800; margin:0 0 8px; letter-spacing:-.01em; color:var(--navy); text-align:left;}
  .sub{font-size:15px; color:var(--navy-soft); max-width:640px; line-height:1.55; margin:0;}
  .fictional-tag{
    display:inline-block; margin-top:14px; font-family:'DM Sans',sans-serif; font-weight:600;
    font-size:11px; color:var(--navy-soft); border:1px solid var(--line); border-radius:4px;
    padding:4px 8px; letter-spacing:.03em;
  }

  .legend{
    display:flex; flex-wrap:wrap; gap:20px; margin:28px 0 44px;
    padding:16px 18px; background:var(--white); border:1px solid var(--line); border-radius:10px;
  }
  .legend-item{display:flex; align-items:center; gap:9px; font-size:13px; color:var(--navy);}
  .swatch{width:14px; height:14px; border-radius:3px; flex:none;}

  .section-label{
    font-family:'DM Sans',sans-serif; font-size:11px; font-weight:700; letter-spacing:.08em;
    text-transform:uppercase; color:var(--navy-soft); margin:0 0 14px;
    display:flex; align-items:center; gap:10px;
  }
  .section-label::after{content:""; flex:1; height:1px; background:var(--line);}

  .flow-col{display:flex; flex-direction:column; align-items:center; margin-bottom:8px;}

  .node{
    background:var(--white); border:1px solid var(--line); border-radius:10px;
    padding:14px 20px; text-align:center; box-shadow:0 1px 2px rgba(29,53,87,.04);
    max-width:520px; width:100%;
  }
  .node .t{font-size:14px; font-weight:700; line-height:1.4; color:var(--navy);}
  .node .s{font-size:12.5px; color:var(--steel); margin-top:3px; line-height:1.45;}
  .node.neutral{background:var(--offwhite);}
  .node.brand{background:var(--navy); border-color:var(--navy);}
  .node.brand .t{color:var(--white);}
  .node.brand .s{color:var(--teal);}

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
  .pill .t{font-size:13px; font-weight:700;}
  .pill .s{font-size:11.5px; margin-top:2px; opacity:.85;}
  .pill.condensed{background:var(--teal); color:var(--navy); border-color:var(--teal);}
  .pill.featured{background:var(--white); color:var(--navy); border:1.5px solid var(--red);}

  .or-label{
    font-family:'DM Sans',sans-serif; font-size:10.5px; font-weight:600; color:var(--navy-faint);
    margin:2px 0; letter-spacing:.05em; text-transform:uppercase;
  }

  .node.concept{
    background:var(--white); border:1.5px dashed var(--navy-soft); position:relative;
  }
  .concept-badge{
    display:inline-block; font-family:'DM Sans',sans-serif; font-size:9.5px;
    font-weight:700; letter-spacing:.05em; text-transform:uppercase; color:var(--navy-soft);
    border:1px solid var(--navy-soft); border-radius:20px; padding:2px 8px; margin-bottom:6px;
  }

  .panel-note{
    background:var(--white); border:1px dashed var(--line); border-radius:10px;
    padding:14px 18px; font-size:12.5px; color:var(--steel); max-width:560px;
    margin:18px auto 0; text-align:center; line-height:1.55;
  }
  .panel-note b{color:var(--navy); font-weight:700;}

  /* bird branch detail */
  .branch-detail{
    margin-top:64px; border-top:2px solid var(--red); padding-top:36px;
  }
  .branch-title{display:flex; align-items:center; gap:10px; margin-bottom:6px;}
  .branch-title .dot{width:10px; height:10px; border-radius:50%; background:var(--red);}
  .branch-title h2{font-size:19px; font-weight:800; margin:0; color:var(--navy);}
  .branch-desc{font-size:13.5px; color:var(--navy-soft); margin:0 0 30px; max-width:600px; line-height:1.55;}

  .node.bird{background:var(--white); border-color:var(--line); border-left:4px solid var(--red);}
  .node.bird .t{color:var(--navy);}
  .node.bird .s{color:var(--steel);}

  .decision{
    width:170px; height:170px; background:var(--white); border:1.5px solid var(--navy-soft);
    transform:rotate(45deg); display:flex; align-items:center; justify-content:center;
    margin:10px 0;
  }
  .decision-inner{transform:rotate(-45deg); text-align:center; padding:0 20px;}
  .decision-inner .t{font-size:13px; font-weight:700; color:var(--navy);}
  .decision-inner .s{font-size:11px; color:var(--steel); margin-top:2px;}

  .yn-row{display:flex; width:100%; max-width:560px; justify-content:space-between; margin-top:-6px;}
  .yn-branch{display:flex; flex-direction:column; align-items:center; width:47%;}
  .yn-tag{
    font-family:'DM Sans',sans-serif; font-size:11px; font-weight:700;
    padding:2px 10px; border-radius:20px; margin-bottom:4px; text-transform:uppercase; letter-spacing:.03em;
  }
  .yn-tag.yes{background:var(--teal); color:var(--navy);}
  .yn-tag.no{background:var(--white); color:var(--steel); border:1px solid var(--line);}

  .loop-note{
    display:flex; align-items:center; gap:8px; font-size:12px; color:var(--navy-faint);
    font-family:'DM Sans',sans-serif; font-weight:500; margin:14px 0;
  }
  .loop-note .line{flex:none; width:24px; height:1px; background:var(--line); position:relative;}
  .loop-note .line::after{content:"↻"; position:absolute; left:-4px; top:-9px; font-size:14px;}

  .end-node{
    color:var(--white); border-radius:20px; padding:8px 22px;
    font-size:12.5px; font-weight:700; font-family:'DM Sans',sans-serif;
    letter-spacing:.02em;
  }
  .end-node.success{background:var(--red);}
  .end-node.close{background:var(--navy);}

  .other-branches{margin-top:56px;}
  .other-grid{display:flex; gap:14px; flex-wrap:wrap;}
  .other-card{
    flex:1 1 200px; background:var(--teal); border:1px solid var(--teal); border-radius:10px;
    padding:16px 18px; min-width:190px;
  }
  .other-card .head{display:flex; align-items:center; gap:8px; margin-bottom:6px;}
  .other-card .dot{width:9px; height:9px; border-radius:50%; flex:none; background:var(--navy);}
  .other-card .t{font-size:13.5px; font-weight:700; color:var(--navy);}
  .other-card .s{font-size:12px; color:var(--navy-soft); line-height:1.5;}

  footer{
    margin-top:60px; padding-top:24px; border-top:1px solid var(--line);
    display:flex; flex-direction:column; gap:10px;
  }
  .footnote{display:flex; gap:10px; font-size:12.5px; color:var(--navy-soft); line-height:1.6;}
  .footnote .tag{
    flex:none; font-family:'DM Sans',sans-serif; font-size:10px; font-weight:700;
    background:var(--navy); color:var(--white); border-radius:4px; padding:2px 7px; height:fit-content;
    text-transform:uppercase; letter-spacing:.03em;
  }

  .brief{margin-top:64px; padding-top:36px; border-top:2px solid var(--line);}
  .brief-eyebrow{font-size:11px; font-weight:700; letter-spacing:.08em; text-transform:uppercase; color:var(--red); margin:0 0 8px;}
  .brief h2{font-size:22px; font-weight:800; color:var(--navy); margin:0 0 4px;}
  .brief .brief-sub{font-size:13.5px; color:var(--steel); margin:0 0 28px; max-width:620px; line-height:1.5;}
  .brief h3{font-size:15px; font-weight:700; color:var(--navy); margin:28px 0 10px;}
  .brief p{font-size:13.5px; color:var(--navy); line-height:1.65; max-width:640px; margin:0 0 4px;}
  .brief ul{list-style:none; margin:0 0 4px; padding:0; max-width:640px;}
  .brief li{font-size:13.5px; color:var(--navy); line-height:1.6; padding-left:20px; position:relative; margin-bottom:9px;}
  .brief li::before{content:"\2022"; color:var(--red); position:absolute; left:0; font-weight:700;}
  .brief .ext-label{
    display:inline-block; font-size:10.5px; font-weight:700; letter-spacing:.04em; text-transform:uppercase;
    color:var(--navy-soft); border:1px solid var(--navy-soft); border-radius:20px; padding:2px 9px; margin:2px 0 10px;
  }
</style>
</head>
<body>
<div class="wrap">

  <header>
    <p class="eyebrow">Marketing operations - automated journey design</p>
    <h1>TrueTail Pet Insurance: coverage-match nurture program</h1>
    <p class="sub">A single welcome email routes new pet parents into one of five species-specific nurture tracks based on first-party click behavior - no guessing, no generic follow-up. Built to demonstrate multi-program MCAE/Pardot architecture: page-action based segmentation, completion-action enrollment, action-rule suppression, and ad-hoc list overrides for manual sales requests.</p>
    <span class="fictional-tag">Fictional brand - illustrative data only</span>
  </header>

  <div class="legend">
    <div class="legend-item"><span class="swatch" style="background:var(--white); border:1.5px solid var(--red);"></span>Shown in full: Bird coverage</div>
    <div class="legend-item"><span class="swatch" style="background:var(--teal);"></span>Shown condensed: Dog, Cat, Rabbit, Fish &amp; aquatic (identical structure)</div>
  </div>

  <p class="section-label">Entry &amp; routing - shared across all five programs</p>

  <div class="flow-col">
    <div class="node neutral">
      <div class="t">New pet parent enters welcome series</div>
      <div class="s">General "New Pet Parent" Salesforce campaign</div>
    </div>
    <div class="arrow"></div>
    <div class="node brand">
      <div class="t">Welcome email sent</div>
      <div class="s">Features the top article, video, and podcast for each of the five coverage types - one link per pet</div>
    </div>
    <div class="arrow"></div>
    <div class="node concept">
      <span class="concept-badge">design extension - not built</span>
      <div class="t">SMS sent same day</div>
      <div class="s">Third-party SMS platform, triggered via Salesforce Flow &middot; invites a reply confirming pet name, type, age, sex, and location to sharpen content matching beyond click behavior alone</div>
    </div>
    <div class="arrow"></div>
    <div class="or-label">prospect clicks an email asset - OR - replies to the SMS - OR - visits a matching page directly (e.g. via social)</div>
    <div class="arrow"></div>
    <div class="node neutral">
      <div class="t">Page action / completion action fires</div>
      <div class="s">Adds prospect to the matching coverage list, now informed by declared profile data &middot; action rule removes them from the general welcome campaign</div>
    </div>
    <div class="arrow"></div>
    <div class="branch-row" style="margin-top:6px;">
      <div class="pill condensed"><div class="t">Dog</div><div class="s">coverage program</div></div>
      <div class="pill condensed"><div class="t">Cat</div><div class="s">coverage program</div></div>
      <div class="pill condensed"><div class="t">Rabbit</div><div class="s">coverage program</div></div>
      <div class="pill condensed"><div class="t">Fish</div><div class="s">coverage program</div></div>
      <div class="pill featured"><div class="t">Bird</div><div class="s">coverage program</div></div>
    </div>
  </div>

  <div class="branch-detail">
    <div class="branch-title"><span class="dot"></span><h2>Bird coverage program - shown in full</h2></div>
    <p class="branch-desc">All five programs share this exact structure. Bird is drawn in detail here. The other four are identical in mechanism with species-specific content, shown condensed below.</p>

    <div class="flow-col">
      <div class="node bird">
        <div class="t">Entry: "bird_coverage_page_action" tag added to profile</div>
        <div class="s">Fires on email click OR direct page visit</div>
      </div>
      <div class="arrow"></div>
      <div class="node neutral">
        <div class="t">Added to Bird Coverage static enrollment list</div>
        <div class="s">Ad-hoc list - sales can manually add or exclude specific prospects regardless of behavior</div>
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
          <div class="end-node success">end - sales handoff</div>
        </div>
        <div class="yn-branch">
          <span class="yn-tag no">no</span>
          <div class="node neutral" style="max-width:100%;">
            <div class="t">Continues to next email</div>
          </div>
          <div class="loop-note"><span class="line"></span>repeats through emails 2-4, same send &rarr; wait &rarr; click check</div>
          <div class="arrow"></div>
          <div class="end-node close">end - unsuccessful list, tagged for 6-month re-engagement</div>
        </div>
      </div>
    </div>
  </div>

  <div class="other-branches">
    <p class="section-label">Same structure, remaining four programs</p>
    <div class="other-grid">
      <div class="other-card">
        <div class="head"><span class="dot"></span><span class="t">Dog coverage</span></div>
        <div class="s">Identical 4-email nurture cycle, dog-specific content and completion lists</div>
      </div>
      <div class="other-card">
        <div class="head"><span class="dot"></span><span class="t">Cat coverage</span></div>
        <div class="s">Identical 4-email nurture cycle, cat-specific content and completion lists</div>
      </div>
      <div class="other-card">
        <div class="head"><span class="dot"></span><span class="t">Rabbit coverage</span></div>
        <div class="s">Identical 4-email nurture cycle, rabbit-specific content and completion lists</div>
      </div>
      <div class="other-card">
        <div class="head"><span class="dot"></span><span class="t">Fish &amp; aquatic coverage</span></div>
        <div class="s">Identical 4-email nurture cycle, fish-specific content and completion lists</div>
      </div>
    </div>
  </div>

  <div class="brief">
    <p class="brief-eyebrow">Results brief</p>
    <h2>Why this was built, and what happened</h2>
    <p class="brief-sub">The architecture above recreates a real Salesforce Marketing Cloud Account Engagement program I built and owned. The results below reflect real reporting from that program, described as patterns and ranges rather than exact figures.</p>

    <h3>The problem</h3>
    <p>New prospects moving through TrueTail's general welcome series received identical messaging regardless of which pet they actually needed coverage for. There was no way to identify a species-specific interest until someone filled out a form, and most people never did.</p>

    <h3>The approach</h3>
    <ul>
      <li>Welcome email surfaced the best article, video, and podcast for all five coverage types at once, and a click became the routing signal</li>
      <li>A page action captured the same signal from direct page visits, so social traffic routed identically to email clicks</li>
      <li>An action rule removed a prospect from the general campaign the instant they entered a species-specific branch</li>
      <li>Static ad-hoc lists let sales manually add or exclude specific prospects, independent of the automated logic</li>
    </ul>

    <h3>The result</h3>
    <ul>
      <li>Every branch total reconciled exactly against the program-wide totals across a full year of reporting</li>
      <li>Branch-specific email engagement outperformed the general campaign by roughly 2x on average, with the strongest branch trending closer to 2.5x</li>
      <li>Prospects who self-identified into a coverage-specific branch represented a small share of the overall population, well under 5 percent, consistent with an opt-in signal rather than a shortfall</li>
      <li>The ad-hoc override mechanism saw real production use: leads and a closed opportunity appeared attributed to a branch with zero formal email enrollments</li>
    </ul>

    <h3>Design extension: SMS profile enrichment</h3>
    <span class="ext-label">not built</span>
    <p>The SMS step above is a forward extension, not part of the original build. Validating it would mean tracking SMS opt-in rate, how often a reply's stated pet type matched the branch a prospect eventually clicked into, and whether branch-assignment accuracy improved for SMS responders compared to click-only routing.</p>
  </div>

  <footer>
    <div class="footnote"><span class="tag">note</span>Every branch supports static ad-hoc lists layered on top of the behavioral logic. Sales can request a specific prospect be manually added to or excluded from any program at any time, independent of their click behavior.</div>
    <div class="footnote"><span class="tag">note</span>Entering any coverage-specific program always triggers suppression from the general welcome campaign via an action rule, so no prospect receives both tracks simultaneously.</div>
  </footer>

</div>
</body>
</html>
