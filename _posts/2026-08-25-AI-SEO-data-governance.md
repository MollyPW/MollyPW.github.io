---
title: "My Foolproof* System for Combining MCAE and Salesforce Email Data"
layout: post
---
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>AI SEO is a data governance problem</title>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,900&family=Cormorant+Garamond:ital,wght@0,600;1,500&family=Poppins:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --navy:#1D3557; --red:#E63946; --steel:#457B9D;
    --teal:#A8DADC; --offwhite:#F1FAEE; --gold:#C9A227;
  }
  *{margin:0;padding:0;box-sizing:border-box}
  body{background:var(--offwhite);color:var(--navy);
       font-family:Poppins,system-ui,sans-serif;line-height:1.6;
       padding:52px 22px 90px}
  .page{max-width:760px;margin:0 auto}

  /* --- cover block: Register B --- */
  .eyebrow{font-family:Poppins;font-size:12px;letter-spacing:2.4px;
           text-transform:uppercase;color:var(--steel);
           background:#fff;display:inline-block;padding:3px 0;margin-bottom:18px}
  h1{font-family:Fraunces,Georgia,serif;font-weight:900;font-size:52px;
     line-height:1.06;letter-spacing:-1px;margin-bottom:16px}
  .standfirst{font-family:"Cormorant Garamond",Georgia,serif;
              font-style:italic;font-weight:500;font-size:23px;
              line-height:1.45;color:var(--navy);max-width:600px}
  .rule{height:3px;background:var(--gold);width:120px;margin:34px 0 40px}

  h2{font-family:"Cormorant Garamond",Georgia,serif;font-weight:600;
     font-size:30px;line-height:1.2;margin:42px 0 12px}
  h3{font-family:Poppins,system-ui,sans-serif;font-weight:500;font-size:12.5px;
     letter-spacing:1.8px;text-transform:uppercase;color:var(--steel);
     margin:26px 0 8px}
  p{font-size:15.5px;margin-bottom:15px}
  strong{font-weight:500;color:var(--navy)}
  code{font-family:"DejaVu Sans Mono",ui-monospace,monospace;font-size:13px;
       background:#fff;padding:1px 5px;border-bottom:1px solid var(--teal)}

  .pull{background:var(--teal);padding:22px 26px;margin:30px 0;
        font-family:"Cormorant Garamond",Georgia,serif;font-size:24px;
        font-style:italic;line-height:1.35}

  ol{margin:0 0 18px 0;list-style:none;counter-reset:step}
  ol li{counter-increment:step;position:relative;padding-left:44px;
        margin-bottom:16px;font-size:15.5px}
  ol li::before{content:counter(step);position:absolute;left:0;top:1px;
        width:28px;height:28px;background:var(--navy);color:var(--offwhite);
        border-radius:50%;display:flex;align-items:center;
        justify-content:center;font-size:13px;font-weight:500}

  table{border-collapse:collapse;width:100%;margin:18px 0 22px;
        font-size:12.5px;background:#fff}
  thead th{background:var(--navy);color:var(--offwhite);text-align:left;
        font-weight:500;font-size:10.5px;letter-spacing:1px;
        text-transform:uppercase;padding:9px 9px}
  tbody td{padding:10px 9px;border-bottom:1px solid #DDE6E2;
        vertical-align:top;line-height:1.45}
  tbody tr:last-child td{border-bottom:none}
  tbody td:first-child{font-weight:500;width:15%}
  tbody td:nth-child(2){width:23%}
  tbody td:nth-child(3){width:29%}
  tbody td:nth-child(4){width:33%}
  tbody td code{font-size:12px;padding:0 3px;word-break:break-word}

  .flag{border-left:5px solid var(--red);background:#fff;
        padding:16px 22px;margin:28px 0;font-size:15px}

  .foot{margin-top:52px;padding-top:18px;border-top:1px solid #D4DBD6;
        font-size:12.5px;color:var(--steel);background:transparent}
  .foot span{background:#fff;padding:0 2px}
  a{color:var(--steel)}
</style>
</head>
<body>
<div class="page">

  <div class="eyebrow">Marketing operations · point of view</div>
  <h1>AI SEO is a data<br>governance problem</h1>
  <div class="standfirst">Most teams are treating generative search as a content problem. It is mostly a question of whether your systems emit clean, consistent, machine-readable signals - which is an operations job.</div>
  <div class="rule"></div>

  <h2>What actually changed</h2>
  <p>An AI search engine does not hand your question to a search index. It splits it into sub-queries and runs each one separately - ask for the best VPN for streaming in Europe and it may search three different things, then assemble one answer. Your page is not competing for a ranking. It is competing to be one of the sources worth quoting on one of the sub-queries.</p>
  <p>Gartner projected in 2024 that traditional search volume would fall by roughly a quarter by 2026, and AI Overviews now resolve a large share of queries before anyone clicks. The click was the unit of measurement for twenty years. It is no longer the only one.</p>

  <div class="pull">The question is no longer "does this page rank." It is "can a machine read this page, understand what entity it describes, and find a passage worth quoting."</div>

  <h2>Why this lands on operations</h2>
  <p>Google's own 2026 guidance says there is no special markup or separate technical requirement for appearing in its generative results - foundational SEO still drives them. That sounds like relief. It is not. It means the differentiator moves to the things ops teams already own: <strong>entity clarity, structured data that matches visible content, and consistent naming across every property and profile.</strong></p>
  <p>If your brand is described three different ways across your site, your knowledge panel, and your partner listings, you have the same problem as a campaign taxonomy with three abbreviations for one product. Reporting fragments. So does citation.</p>

  <div class="flag"><strong>The failure nobody checks for:</strong> AI crawlers can only read the HTML your server returns. Content rendered client-side is invisible to them. And Cloudflare changed its default to block AI bots - so a site can be fully optimized and completely unreachable, with nothing in any dashboard to say so.</div>

  <h2>Schema and naming, specifically</h2>
  <p>Structured data is not a switch that turns on AI visibility. Google's position is that no special markup is required for its generative results, and nobody has produced a documented mechanism that says otherwise. What schema does is remove ambiguity. It states, in a form a machine does not have to infer, who published this page, what entity it describes, and how that entity connects to everything else you publish.</p>
  <p>That is a smaller claim than most of what gets sold, and it is also the entire point. A system deciding whether to quote you has to resolve your entity first. When it cannot, the safest thing it can do is quote someone else.</p>

  <h3>Three types, done consistently</h3>
  <p>A small stack maintained properly beats nine types filled in halfway. <strong>Organization</strong> on the homepage, <strong>WebPage</strong> sitewide, and <strong>Article</strong> or <strong>Product</strong> where the page genuinely is one. Half-populated markup is worse than none, because every property you declare is a claim the system then has to reconcile against what is visible on the page. If the two disagree, you have taught it that your markup is unreliable.</p>

  <h3>@id is a primary key</h3>
  <p>Give the organization one stable identifier - conventionally the homepage URL with a fragment, like <code>https://yourdomain.com/#organization</code> - and have every other block on every other page reference that string instead of redeclaring the brand from scratch. It behaves exactly like a primary key, and it fails exactly like one. Two spellings of the identifier means two records, split evidence, and no single entity with the full history behind it.</p>

  <h3>sameAs is the join to everything you don't control</h3>
  <p>The <code>sameAs</code> array points at the profiles that corroborate you: LinkedIn, Wikidata, Crunchbase, verified social accounts, the industry directory your category actually uses. Each of those should carry the same name string and the same description as the markup does. Never declare a profile that does not exist. These are checkable claims, and a wrong one costs more than a missing one.</p>

  <h3>The naming convention is the deliverable</h3>
  <p>None of the above holds together without a written decision about what each thing is called. One string per entity, chosen once, documented, and enforced in every system that emits it.</p>

  <table>
    <thead>
      <tr><th>Signal</th><th>Canonical form</th><th>Example</th><th>Has to match everywhere it appears</th></tr>
    </thead>
    <tbody>
      <tr>
        <td>Brand name</td>
        <td>One exact string, including the ampersand-or-and call and whether the entity suffix is part of it</td>
        <td><code>Acme Analytics, Inc.</code> every time, never <code>Acme</code> in the footer and <code>Acme Analytics LLC</code> in a directory listing</td>
        <td>Site header and footer, Organization markup, knowledge panel, LinkedIn, partner listings, press boilerplate</td>
      </tr>
      <tr>
        <td>Entity <code>@id</code></td>
        <td>One URI, set once, never regenerated per template</td>
        <td><code>https://acmeanalytics.com/#organization</code>, referenced by every other block rather than redeclared</td>
        <td>Every schema block on every page, including blog, careers, and any subdomain</td>
      </tr>
      <tr>
        <td>sameAs profiles</td>
        <td>Verified, live URLs only</td>
        <td><code>linkedin.com/company/acme-analytics</code>, <code>wikidata.org/wiki/Q00000</code>. No Wikipedia URL if there is no Wikipedia page</td>
        <td>The profiles themselves, which have to name you the same way back</td>
      </tr>
      <tr>
        <td>Product and service names</td>
        <td>One string per thing, no internal abbreviations, no regional variants</td>
        <td><code>Acme Pipeline Monitor</code>. Never <code>APM</code>, never <code>the Monitor</code>, never <code>Pipeline Monitor Pro</code> on a reseller site</td>
        <td>Navigation, page titles, markup, sales collateral, partner and reseller sites</td>
      </tr>
      <tr>
        <td>People</td>
        <td>Full name as published, one form, middle initial in or out</td>
        <td><code>Jordan A. Reyes</code> on the byline and in Person markup, not <code>J. Reyes</code> in one and <code>Jordan Reyes</code> in the other</td>
        <td>Bylines, Person markup, the about page, LinkedIn, conference bios</td>
      </tr>
    </tbody>
  </table>

  <p>If that table looks like a campaign taxonomy document, that is because it is one. Same discipline, different table. And it is missing at most companies for the same reason taxonomy documents are missing: it is nobody's job until reporting breaks. Citation is the version of reporting that breaks silently.</p>

  <h3>Where it drifts</h3>
  <p>Drift is the normal state, not the failure state. The predictable points: <code>dateModified</code> never updated after a revision, prices in markup that no longer match the page, contact details changed in the CMS but not in the JSON-LD, and blocks inherited from a template that survived a migration and now describe a page that no longer exists in that shape. Treat schema as maintenance with an owner and a review trigger - after every migration, every template change, every rebrand - rather than as a launch task somebody ticked off in 2023.</p>

  <div class="flag"><strong>A caution on the numbers:</strong> vendor studies circulating this year claim large citation lifts for pages carrying structured data - 2.7x, 3.1x, plus 73 percent. Those come from third-party panels rather than from Google, and they are correlational. Sites that maintain clean schema tend to maintain everything else too. Implement schema for disambiguation, which is defensible on the mechanics. Do not put a multiplier in the business case.</div>

  <h2>Five things worth doing</h2>
  <ol>
    <li><strong>Check you are reachable at all.</strong> Robots.txt, CDN configuration, server logs for AI user agents. This is the most common failure and the cheapest to fix.</li>
    <li><strong>Write self-contained passages.</strong> AI systems pull blocks, not narrative. A short direct answer near the top of each page, forty to sixty words, is the single highest-leverage content change.</li>
    <li><strong>Raise fact density.</strong> A verifiable statistic with a named source every 150 to 200 words. Cited claims get cited.</li>
    <li><strong>Use tables where a comparison exists.</strong> Tables are among the most quotable structures on a page.</li>
    <li><strong>Name entities identically everywhere.</strong> Site, schema, profiles, partner listings. Same string every time, per the convention above.</li>
  </ol>

  <h2>The sourcing gap</h2>
  <p>This one is a bet rather than a finding, and it is worth saying so before making it. The pool of sources these systems can retrieve is shrinking at the top. Reddit blocked ChatGPT's crawlers domain-wide in August 2026 and its citations there fell by 86 percent. The New York Times refuses every major AI user agent, and across a study of 31 million citations it was quoted zero times by ChatGPT and zero times by Gemini. Those slots do not sit empty. They go to whatever the system can still read.</p>
  <p>Two things keep this from being a free win. Blocking only works against the labs that honor robots.txt - the same study found Grok, AI Overviews, and DeepSeek producing roughly half the news citations in the sample with no functioning opt-out, so a blocked source is absent from some answers and present in others. And the vacancy is topic-shaped. It is largest in the categories where those sources were the corpus, which is forum opinion, product experience, and news, and considerably smaller everywhere else.</p>
  <p>The odd part is how thin the competition for the opening is. A July 2026 audit of the top 1,000 sites found 40.9 percent unreadable to GPTBot, 18.4 percent dark to every AI crawler tested, and 17.6 percent that permit GPTBot in robots.txt and then return a 403 when it actually requests a page. That last group has a published policy saying yes and a CDN saying no, and nothing anywhere tells them which one is winning.</p>
  <p>So the bet, in operations terms: the gap gets filled by whoever is readable, and schema decides whether the system can tell the readable thing is you. It does not win the slot by itself. Retrievable, self-contained, specific content wins the slot. Treat this as a window rather than a strategy, because a licensing deal can close it in a quarter.</p>

  <h2>Measurement is the gap</h2>
  <p>None of this shows up cleanly in analytics. Someone asks an AI for a recommendation, reads the answer, and searches your brand by name two days later - that arrives as direct or branded traffic with no attribution trail back to the AI that recommended you.</p>
  <p>Google shipped part of the instrument in June 2026: a generative AI performance report in Search Console covering impressions inside AI Overviews and AI Mode, rolling out in stages and starting with a subset of UK sites. Turn it on when it reaches you. It does not close the gap. There are no clicks in it, no queries, and no conversions, so it tells you that you appeared and not what appearing was worth. And it covers Google only, which leaves ChatGPT, Perplexity, and Copilot unmeasured.</p>
  <p>The rest of the measurement layer is citation coverage and share of voice inside AI answers, and it is a separate instrument from the one on your dashboard. Which is the familiar shape of every marketing operations problem: the thing driving the outcome is not the thing being measured, and someone has to go build the instrument before anyone can argue about the result.</p>

  <div class="foot">
    <span>Molly E. Purcell-Weatherwalks · Marketing Operations &amp; CRM Analytics · linkedin.com/in/purcell-molly</span><br>
    <span>Sources: Google generative AI search guidance and Search Central structured data documentation (2026); Search Console generative AI performance reports (June 2026); Gartner search volume projection (2024); Princeton/Allen Institute research on generative visibility; Schema.org; Goodie study of 31 million AI citations across 105 publishers (2026); Vidern crawler accessibility audit of the top 1,000 sites (July 2026); industry GEO practice guides, 2026. Updated August 2026.</span>
  </div>

</div>
</body>
</html>
