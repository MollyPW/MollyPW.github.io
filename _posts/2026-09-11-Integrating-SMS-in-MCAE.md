---
title: "Integrating SMS in MCAE: Two Paths to Consider"
layout: post
---
<article class="one-pager">
  <header>
    <p class="overline">MARKETING OPS TEARDOWN · AUGUST 2026</p>
    <h1>Three ways to text a prospect<br/>out of MCAE<span class="asterisk">*</span></h1>
    <p class="subhead">I have not built this in production. This is the map I would draw if someone asked, with the documentation checked and the gotchas that are not in the sales deck.</p>
  </header>

  <div class="paths">
    <section>
      <h2><span class="number">1</span> Mogli <small>no developer required</small></h2>
      <ol>
        <li>A completion action called <b>Create Salesforce Task</b> fires on the form fill.</li>
        <li>The Task subject reads <b>"Mogli #keyword"</b>. The keyword after the # has to match the name of an SMS Template you built in Mogli.</li>
        <li>Task creation triggers a Flow. It finds the related contact through the WhoID, sets the SMS fields, and creates the record in <b>Queued</b> status.</li>
        <li>Mogli sends it from the Default Gateway on the record, or from a Gateway ID you hardcode in the Create Records element.</li>
      </ol>
      <p class="watchout">The recipient needs a Mogli Number and must not be opted out, or nothing happens and nothing tells you. Mogli recommends a <b>5-minute delay scheduled path</b> so the send leans on bulk architecture instead of blowing through processing limits. Mogli also sells an out-of-the-box Account Engagement package - the flow above is the build-it-yourself version.</p>
    </section>

    <section>
      <h2><span class="number">2</span> External Actions <small>developer required</small></h2>
      <ol>
        <li>A developer writes an <b>invocable Apex action</b>, plus a named credential and external service pointed at Twilio.</li>
        <li>It gets registered as a <b>MarketingAppExtAction</b> on a Marketing App Extension, with <b>Active in Automations</b> checked.</li>
        <li>It appears as a <b>Custom Action</b> step in Engagement Studio - and since Summer '23, as a completion action on assets too, so it can fire off the same form fill as path 1.</li>
        <li>The prospect hits the step and it calls Twilio in real time.</li>
      </ol>
      <p class="watchout"><b>Plus, Advanced and Premium editions only</b> - Growth cannot do this at all. It is fire and forget, so no error handling inside the program, and it is not bulkified, meaning one API call per prospect. 100,000 external actions per business unit per day, 10 per extension. It runs as your Connector User, so a missing field permission fails silently. Nothing retries on its own, and you are aiming for a 2-second response.</p>
    </section>
  </div>

  <section class="path-3">
    <h2><span class="number">3</span> Account Engagement + Marketing Cloud PSLs <small>the almost-native one, and the reason this page has an asterisk</small></h2>
    <p>Salesforce's own answer, live since Winter '25: every MCAE customer on Growth, Plus, Advanced and Premium can send multichannel journeys with SMS, no third-party app. So the honest version of "MCAE has no native SMS" is that it has one, behind a shopping list.</p>
    <p><b>You need first:</b> Data Cloud provisioned and connected through the Account Engagement Data Cloud Connector · Sales or Service Cloud Enterprise Edition or higher · PSLs configured by an admin · and separately purchased Data Cloud, messaging and AI-request credits.</p>
  </section>

  <section class="tell">
    <h3>THE TELL</h3>
    <p>Mogli tells you to build in a five minute delay so you do not hit processing limits. External Actions tells you to answer in under two seconds and write your own retry logic. Same prospect, same text message, opposite instruction. Pick the path, then pick which limit you would rather explain to somebody.</p>
  </section>

  <footer>
    <hr/>
    <p class="sources">
      Verified August 2026  ·  Sources: Mogli Account Engagement integration guide  ·  Salesforce Developers, Winter '23<br/>
      MCAE Summer '23 release notes  ·  salesforce.com/blog, Account Engagement + Marketing Cloud Permission Set Licenses
    </p>
    <p class="name">Molly Purcell-Weatherwalks</p>
  </footer>
</article>
