---
title: "Integrating SMS in MCAE: Two Paths to Consider"
layout: post
---
        <h1>Integrating SMS in MCAE: Two Paths to Consider</h1>
        
        <p>I've never actually built this, but if someone asked me how I'd bolt SMS onto a customer journey inside MCAE, here's the two paths I'd map out.</p>
        
        <section>
            <h2>External Actions, Heavy Salesforce Admin or Dev Assistance Required:</h2>
            <ol>
                <li>Someone writes an invocable Apex action</li>
                <li>Registers it as a MarketingAppExtAction</li>
                <li>Uses turns up as a step in Engagement Studio, or as a completion action on the consent form fill (which nobody seems to mention)</li>
            </ol>
        </section>
        
        <section>
            <h2>With an External Tool Like <a href="https://www.linkedin.com/feed/#">Mogli</a>, Minimal Back-end Salesforce Assistance Needed:</h2>
            <ol>
                <li>A completion action creates a Salesforce Task</li>
                <li>The subject reads "Mogli #keyword"</li>
                <li>Task creation triggers a Flow that finds the contact and drops a queued SMS record (<a href="https://guide.mogli.com/shared/689f46b6-d10a-4ada-93f8-731ab83fe6a4">link</a>)</li>
            </ol>
        </section>
        
        <p>Personally, I think the external tool route will work best for most MCAE users.</p>
        
        <p>Before anyone links me the blog post - yes, MCAE can send SMS now, through Account Engagement + Marketing Cloud PSLs. BUT the barrier to implementation is an issue. Orgs will need Data Cloud, Enterprise edition, and three separate kinds of credits first. 🧐</p>
        
        <p>Bonus: Mogli's support documentation is top-notch - as a visual learner, I love the diagrams and screenshots 🧡</p>
        
        <p>Good to know: Mogli strongly advises users to build in a 5-minute delay so they don't blow through processing limits. Reasonable people build in buffers. I respect that - everyone needs boundaries.</p>
        
        <p>No universal native feature doesn't mean no feature. It means someone on the team gets to be a little annoying about architecture for a week. 🥳</p>
