---
title: "My Foolproof* System for Combining MCAE and Salesforce Email Data"
layout: post
---
So, this isn't foolproof, and it isn't a tutorial on how MCAE reporting works under the hood. It's the process I use for combining MCAE and Salesforce email data into one quarterly report. I'm not a data engineer. A fair amount of what's below comes straight out of Salesforce's own documentation, which is better than people give it credit for once you know which article you need.

But if you find yourself pulling exports out of MCAE and Salesforce and squinting at why the open rates don't match, or rebuilding the same merge by hand every single month, there should be a few things in here worth stealing.

The good news is that the hard part usually isn't technical. You don't need new tooling for it. You mostly need to know what each number is counting before you set it in a column next to another number. Which sounds obvious written down, and is very easy to skip.

<h2>Why the numbers don't line up</h2>
Naming is the mismatch everybody expects. MCAE's List Email report gives you HTML Open Rate. Something else in your stack calls the same idea Opens, or Unique Opens, or whatever a spreadsheet somebody has maintained since 2019 calls it. Renaming columns is tedious and it's fine, you can do that in your sleep.

The harder version is that those reports don't carry the same metrics in the first place. List Email is the rich one. Template Emails has much more limited analytic options, so a metric you lean on in one place simply isn't available in the other, and there's nothing to map it to. When that happens you have to calculate the missing metric yourself out of whatever counts the thinner report does give you.

Which is where the bottom half of the fraction starts to matter. Every rate is a count divided by something, and the sources don't agree on what that something is. MCAE calculates unique open rate against DELIVERED, meaning sent minus bounces. Plenty of platforms calculate it against SENT. Derive one rate against one denominator, pull the other straight from a report using the other denominator, stack them in the same column, and you get a number that describes nothing at all. It charts beautifully. Nobody will question it.

The way I get around all of this is to stop trusting the rate columns entirely. I pull the raw counts, so sent, delivered, bounces, unique opens, unique clicks, opt-outs, and then calculate every percentage myself in the merged file. One formula, one denominator, applied to every source. It's faster than auditing what each report meant by its own rate column, and when somebody asks what a number is divided by, the formula is right there.

<h2>Getting the data out of MCAE</h2>
Which means the raw counts are what you're actually going after, not the pre-calculated rate columns.

<h3>In the Account Engagement Lightning app:</h3>
<ul>
  <li></li>Account Engagement Reports > Marketing Assets > Emails > List Emails > Tools</ul>

<li>From there, "Export custom table to CSV" or "Export all items to CSV."</li>

<li>You need the Administrator, Marketing, or Sales Manager role to export at all.</li>
</ul>
<h3></h3>Three things about that export are worth knowing before you rely on it.

Percentages come out as decimals. A 27% open rate exports as 0.27. If your template already formats that column as a percentage you get 27%. If it doesn't, you get 0.27 sitting next to a column of whole numbers, and you will not notice until somebody asks why open rate is under 1%. Convert it once, at ingest, and don't think about it again.

In Excel: select the column, then Home > Number Format > Percentage. That displays 0.27 as 27% and leaves the underlying value alone, which is what you want if anything downstream is doing math on it.

In Power BI: Column tools > Format > Percentage.

"Export all items" means all items. Every metric, for every list email ever sent out of that business unit. It isn't a deal breaker, but if you came for one month of stats you will be swimming in data you didn't ask for. Yikes!

Customizing the table changes the export. "Export custom table to CSV" gives you whatever columns are showing right now. So if you reordered the table last week, or applied a specific "sent on" filter, this month's table is a different shape than last month's. There's a "Reset table to default" option under Tools. 

One more thing that isn't in that export at all. For bounce detail, skip the List Email Statistics table. The Email Bounce Report is what you want. It covers soft and hard bounces across all send types for the past year and it includes the bounce reason, which is the whole point. The reason tells you whether you're looking at a list quality problem or a receiving server problem, and those get handled completely differently. 

For detailed- regular bounce reporting (say for specific error types) I recommend cultivating a friendship with your org's Looker/Tableau/Datorama/Marketing Cloud Intelligence Analyst and asking them to help create a custom dimension report for you.

Getting engagement data out of Salesforce Sales
This is where the most bad advice gets repeated.

The Campaign with Campaign Members type report does not carry email engagement metrics. It carries campaign membership. If you build your report on that report type you'll spend an afternoon hunting for fields that were never there.

Marketing email engagement lives on the prospect record's Engagement History. To report on it in Salesforce you still need a custom report type, built in Setup, and then a report built on top of that in Sales reports. The MCAE and Sales Cloud split trips up casual users constantly, so it's worth being precise about which side you're standing on.

The report type most people are after uses Campaigns as the primary object with List Emails as the A-to-B relationship. When you build it you'll be asked whether each campaign record must have at least one related list email, or whether campaigns may or may not have one. Choose "must have at least one." Plenty of campaigns get created and never get a list email attached, and that setting is what keeps them out of your engagement report instead of padding it with empty rows. Salesforce has a knowledge article covering five recommended report types, and it's worth building all five while you're already in Setup.

Two prerequisites will stop you cold. Connected Campaigns and Engagement History have to be enabled, and creating the report type requires the Manage Custom Report Types permission. No Setup access means this is a conversation with your admin.

There's also a known issue that presents as a data problem. Non-admin users see blank engagement metrics on the List Email object in these reports. The fix is changing org-wide default sharing on the List Email object from Private to Public Read Only.

Normalize before you merge
The requirements here are small and boring and I'm not going to pretend otherwise. Especially when you are pulling reports on prospect records.

Lowercase and trim every email address. Convert every date to ISO 8601, so YYYY-MM-DD, because Salesforce export formats follow the user's locale settings and the person running the export this month might not be the one who ran it last month. Standardize company name formatting. One column schema across every file.

For example: Before normalization these are treaded as two records:

jane.doe@acme.com  | Acme Corp | 08/01/2026
Jane.Doe@ACME.COM  | ACME CORP | 2026-08-01 
After, they're one.

Here's how to get there. Copy the contents of your working column into a new helper column next to each field you're normalizing. Make your corrections/change your field formatting, then paste the values back over the original when you're done.

Using the above two Jane Doe records as an example:

Email address, lowercase and trimmed of stray spaces:

=TRIM(LOWER(A2))

Company name, same treatment:

=TRIM(UPPER(B2))

Dates are the fiddly one, because it depends on whether Excel parsed the export as a real date or left it as text. Click the cell and look at how it sits. Dates right-align, text left-aligns.

If it's a real date:

=TEXT(C2,"yyyy-mm-dd")

If it's text:

=TEXT(DATEVALUE(C2),"yyyy-mm-dd")

Then select your helper columns, copy, and Paste Special > Values over the originals. Do this before the merge, not after, because a formula referencing a column you're about to delete will break in a way that's tedious to unpick.

I can hear you wail: But Molly, data cleaning is boring - I want to get to the fun stuff! Yes yes, I understand. However, skip normalization and those two rows survive the merge as separate records. Your record count is now one too high for that person, so any per-person count you report are all overstated by however many duplicates you carried in. You'll also have two rows with conflicting company name and date values for the same address, and whichever one happens to sort first is the one that ends up in your summary. Which is a dedup problem, and dedup in MCAE has a wrinkle worth its own section below.

While you're at it, carry a source system column and campaign name on every row from the very beginning. Works great when you're most of a year into a dataset, somebody questions a single number in a leadership meeting, and you need to explain the data without re-pulling everything. If you don't or your intrepid leader asks follow up questions, repeat after me: "I don't have that data ready at the moment. I will follow up with you on that."

Where AI helps, and where it doesn't
I do use AI in this workflow. Not the way most tutorials describe it.

Don't paste prospect-level data into a general purpose chatbot.
Email addresses are personal data. Whether moving them into a given tool is allowed is a question for whoever owns data governance where you work, and the answer usually turns on what agreement is in place with that vendor rather than on how careful you personally intend to be. Microsoft Copilot under an enterprise agreement is a genuinely different governance posture than a consumer account. Know which one you're sitting in before you paste anything or share super duper company secrets. Your IT team should be able to help you with this. 

Aggregating first gets you most of the way out of the problem. Send-level and campaign-level rows carry no individual records: campaign name, date, sent, delivered, bounces, unique opens, unique clicks, opt-outs, complaints. Almost every reporting question you have can be answered at that grain, which is good, because that grain is also the safe one.

Most of the way, though, not all of it. Aggregating reduces identifiability without automatically eliminating it. The ICO (Information Commissioner's Office [UK GDPR enforcement])treats identifiability as a spectrum and applies a "motivated intruder" test, asking whether a determined person with resources could work out who's in the data. A row summarizing the open rate of an email sent to a list of 40,000 prospects is fine by anyone's reading. A row summarizing a send to eleven named accounts in one territory is a different conversation. Use judgment at the small end.

Don't use a model as your extraction or math layer. 
Asking a model to read several thousand rows and hand back structured output with correct numbers is asking it to do the thing it's worst at, and the output looks right either way.

There's a really useful paper on this called "Lost in the Middle," by Nelson Liu and colleagues. They tested how well models find one specific piece of information depending on where it sits in a long input. Anything near the very top or the very bottom gets found. Anything in the middle gets missed, and the falloff is steep. They saw the same pattern in every model family they tried.

Which is exactly what you're asking for when you paste in eleven months of sends and say "tell me which one looks off." The weird row is hardly ever the first one or the last one.

Excel, Power Query and Python don't have this problem. Same input, same output, every single time, and when they break they break loudly instead of handing you a confident wrong answer.

There's still a real job for AI here, just later in the process. Once you've aggregated the data and you trust the numbers, hand it the table and let it write the summary and point at what's worth a second look. Writing and judgment is the part it's actually good at. Here's a prompt for that, on aggregated data only:

You are helping me write the summary section of a monthly email
performance report. I am providing aggregated, send-level data.
No personal data is included.

About this file:
- It was exported from [SOURCE] on [DATE] and covers [DATE RANGE].
- One row per list email send.
- Column [NAME] is [WHAT IT COUNTS]. Rates are already calculated
  as [NUMERATOR] divided by [DENOMINATOR].
- [Repeat for every column you want it to use.]
- Ignore any column not described above.

Baselines, calculated from our own send history:
- Average CTR: [X]%
- Average CTOR: [X]%

Write:
1. Three to five bullets covering the most important changes
   versus the prior period.
2. A list of any sends that fall meaningfully above or below the
   baselines, with the metric and the figure.

Rules:
- Use only the numbers I provide. Do not calculate new metrics,
  do not estimate, and do not infer anything not present.
- If something looks unusual but you cannot tell why from this
  data, say so rather than guessing at a cause.
- Plain language. No marketing adjectives.

Data:
{{PASTE_AGGREGATED_TABLE_HERE}} 
The "about this file" block is the part that actually matters, and it's the part everybody skips. Tell it what the export is, when it was pulled, what period it covers, what every column is named and what that column is counting. Without it the model will make reasonable-sounding assumptions about which column is which and which rows belong to the period you asked about, and you will not be able to tell from the output that it guessed.

For the baselines, don't reach for a published industry benchmark. Calculate your own from the list send data you already have. I will average CTR and CTOR across the available send history and use those figures as the definition of a successful send, so if the trailing two-year CTR sat at 4.9%, a send landing at 7% will be considered a clear win. 

What counts as meaningful variance from that baseline is a judgment call and it should be, because it depends on what the channel is being asked to do. A reactivation send and a monthly promotional send do not deserve the same tolerance.

This same setup handles the two comparisons that are genuinely tedious by hand. Swap the "write" instructions for either of these:

Compare performance across the segments in this file. Group the
sends by [SEGMENT COLUMN] and tell me which segments are above
and below the baselines above, using only the figures provided. 
These sends all belong to campaign [NAME] and are scattered
through the file. Pull them into one list in date order and tell
me how performance moved across the sequence. 
Run it twice on the same table and compare the two summaries before you trust either one. If the model is inventing numbers, hallucinating, or experiencing conversational drift, that's usually where it shows. Then check the summary against the table before it goes anywhere. I validated every AI-generated output against source reporting before I used it, every time, and that step is what makes the whole approach defensible when somebody asks where a number came from. Never forget to CYA - cover your ass.

Two things that will make your report wrong
Open rate isn't a clean metric anymore.
Since Apple Mail Privacy Protection shipped with iOS 15, Apple preloads remote content through its proxy servers for anybody who has it turned on. That registers an open whether or not a human ever saw the message. Published estimates of how much of total open volume that accounts for vary a lot depending on audience mix, and the honest answer is you can't separate machine opens from human opens in standard MCAE reporting.

Salesforce has acknowledged this directly. MCAE has an Open Rules Audit page that identifies which of your automations depend on open data, specifically so you can move them onto more reliable signals. If you have engagement programs or scoring branching on opens, go run it. Metrics Guard is a separate tool, and it filters bursts of scanner and bot activity out of your metrics with no setup at all, though Salesforce is clear it doesn't catch everything and that it evaluates open and click thresholds separately.

The workaround is the same baseline approach from the prompt above. Trend open rate against your own send history rather than a published benchmark, and lead with click-through rate and click-to-open rate. Those require an action a proxy server won't take. When open rate moves and click rate stays flat, it's usually measurement noise, and saying so in the report before anyone asks saves a whole meeting.

Use Google Postmaster Tools v2 to see the number Gmail is judging you on.
MCAE records complaints that come back through provider feedback loops, which hand over the complaining recipient's address so it can be logged against that prospect. Gmail doesn't work that way. Seeing a 0% spam complaint rate on your list email reports doesn't mean your emails are golden.

Google does run a feedback loop, but it's header-based and aggregate. You embed a Feedback-ID header with identifiers you pick (talk to Salesforce Support if you need clarification on this), and Google reports spam rates per identifier in the Postmaster Tools (version 2) dashboard, and only when an identifier clears both a volume threshold and a distinct-complaint threshold. You never get the address of anyone who complained OR the specific email send that triggered the complaint. Google is also explicit that the data covers @gmail.com recipients only.

So Gmail complaints never arrive in MCAE as individual records, and the thresholds Google enforces are written against the Postmaster number. Remember that sends above 0.30% are a policy violation that will send your future emails to Spam Jail.

This matters a lot for anyone with a Gmail-heavy database, which in B2B is more common than people assume. If a big share of your recipients are on Gmail and you're reporting a complaint rate calculated from MCAE data alone, your denominator covers the whole send while your numerator is missing an entire provider. The number looks great and you have no way to know whether it is. Report Postmaster complaint* and MCAE complaint data as two separate metrics, labeled so it's obvious which providers each one covers. 

*You will need to manually pull the Postmaster spam rate regularly.

Keep the @gmail.com scope in mind when you're sizing that gap, too. Recipients on Google Workspace custom domains are a different population from the one Postmaster reports on, and in a B2B database that's often the bigger share.

If you're not in Postmaster Tools yet, that's a bigger gap than anything else in this article. It's free and it takes a DNS record.

What actually goes in the report
Personally, I like making a PowerPoint Slide - it's easy to build, easy to share, and easy to iterate for repeatable reports. 

Report Structure:
Executive summary at the top. 
Three to five bullets, findings only, no methodology details. 
A KPI snapshot covering delivery, engagement, list health and complaints. Trend against the prior period (because a single period on its own can't be interpreted). Then anomalies, with the reason if you know it and an honest note if you don't.

Flat one-row-per-send files are for analysis and downstream imports. The summary view is what leadership sees. Sending an executive the raw file and hoping interpretation happens on their end is how reporting loses credibility, and that's hard to win back.

Every metric should trace to a source record. Most of the time nobody checks. The time somebody does is the time it counts.

Where this goes next
Everything above is a manual process. That's fine for a quarterly report and it gets old fast if you need it monthly.

It can be automated. There are people who are genuinely good at piping MCAE data into Power BI, Looker or Tableau on a schedule, and I'm not one of them yet, so I'm not going to pretend I can walk you through it.

What I can tell you is the part that doesn't change once you automate it.

Say you build a lens in Tableau combining List Email data with Template Email data. You're still capped by the thinner of the two sources. Template reporting has the slim analytics options, so the combined view can only show you what both sides are able to supply. Pointing a more powerful tool at the data doesn't conjure up metrics that were never collected in the first place.

You can't compare apples to oranges if the oranges don't exist.
