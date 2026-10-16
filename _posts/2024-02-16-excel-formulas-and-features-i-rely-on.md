---
layout: post
title: "My 15 Secrets* to Convincing People I'm an Excel Expert"
date: 2024-02-16
description: "Seven Excel features and eight formulas, from TEXTJOIN to VLOOKUP, that casual Excel users often miss and that make data cleaning faster."
teaser: "Seven Excel features and eight formulas I rely on for cleaning data and prepping CRM imports, from Text to Columns and Remove Duplicates to TEXTJOIN, VLOOKUP, and PROPER."
image: "assets/images/excel-formulas-features-expert.png"
categories: [Reporting]
hide_title: true
tags: [excel, data-cleaning, formulas, marketing-operations]
---

<div class="mcae-article">
<style>
.mcae-article {
  --navy: #1D3557;
  --red: #E63946;
  --steel: #457B9D;
  --teal: #A8DADC;
  --offwhite: #F1FAEE;
  font-family: 'DM Sans', 'Poppins', -apple-system, BlinkMacSystemFont, sans-serif;
  color: var(--navy);
  max-width: 720px;
  margin: 0 auto;
  line-height: 1.6;
  font-size: 1.05rem;
}
.mcae-article * { box-sizing: border-box; }
.mcae-article h1.mc-title {
  font-family: 'DM Sans', sans-serif;
  font-weight: 800;
  font-size: 2rem;
  line-height: 1.25;
  color: var(--navy);
  text-align: left;
  margin: 0 0 0.75rem 0;
}
.mcae-article .mc-subnote {
  font-style: italic;
  color: #6b7a8f;
  font-size: 0.85rem;
  margin: 0 0 1.75rem 0;
}
.mcae-article .mc-quickbox {
  background: var(--offwhite);
  border-left: 4px solid var(--teal);
  border-radius: 4px;
  padding: 1.25rem 1.5rem;
  margin: 0 0 2rem 0;
}
.mcae-article .mc-quickbox h2 {
  font-family: 'DM Sans', sans-serif;
  font-weight: 700;
  font-size: 1.1rem;
  color: var(--navy);
  margin: 0 0 0.5rem 0;
}
.mcae-article .mc-quickbox p { margin: 0 0 0.75rem 0; }
.mcae-article .mc-quickbox ul { margin: 0; padding-left: 1.25rem; }
.mcae-article .mc-quickbox li { margin-bottom: 0.35rem; }
.mcae-article h2.mc-h2 {
  font-family: 'DM Sans', sans-serif;
  font-weight: 700;
  font-size: 1.4rem;
  color: var(--navy);
  border-bottom: 2px solid var(--navy);
  padding-bottom: 0.4rem;
  margin: 2.5rem 0 1rem 0;
}
.mcae-article h3.mc-h3 {
  font-family: 'DM Sans', sans-serif;
  font-weight: 700;
  font-size: 1.05rem;
  color: var(--steel-on-white, var(--navy));
  margin: 1.25rem 0 0.4rem 0;
}
.mcae-article p { margin: 0 0 1.1rem 0; }
.mcae-article ol, .mcae-article ul.hs-list { padding-left: 1.4rem; margin: 0 0 1.1rem 0; }
.mcae-article ol li, .mcae-article ul.hs-list li { margin-bottom: 0.5rem; }
.mcae-article strong { color: var(--navy); }
.mcae-article .hs-faq dt {
  font-weight: 700;
  color: var(--navy);
  margin-top: 1.1rem;
}
.mcae-article .hs-faq dd {
  margin: 0.25rem 0 0 0;
}
.mcae-article .hs-credit {
  font-style: italic;
  color: #6b7a8f;
  font-size: 0.85rem;
  margin-top: 2.5rem;
  border-top: 1px solid var(--teal);
  padding-top: 0.75rem;
}
.mcae-article a { color: var(--steel); text-decoration: underline; }
.mcae-article a:hover { color: var(--red); }

.mcae-article .table-wrap { overflow-x: auto; margin: 0 0 1.5rem 0; }
.mcae-article table { width: 100%; border-collapse: collapse; font-size: 0.95rem; }
.mcae-article th, .mcae-article td { border: 1px solid rgba(29,53,87,0.2); padding: 0.6rem 0.75rem; text-align: left; vertical-align: top; }
.mcae-article th { background: var(--navy); color: var(--offwhite); }
.mcae-article tbody tr:nth-child(even) { background: var(--offwhite); }
.mcae-article code { background: var(--offwhite); padding: 0.1rem 0.35rem; border-radius: 3px; font-size: 0.9em; }
.mcae-article img.mc-shot { display: block; max-width: 100%; height: auto; margin: 0.5rem 0 1.5rem 0; border: 1px solid rgba(29,53,87,0.2); border-radius: 4px; }
</style>

<h1 class="mc-title">My 15 Secrets* to Convincing People I'm an Excel Expert</h1>

<p><em>(Even if you don't know the difference between Concatenate and Text Join)</em></p>
<p>So, these aren't secrets exactly, nor is this a tutorial on how everything works. This is a collection of Excel features and formulas that I rely on and discovered casual Excel Users might not know about.</p>
<p>I'm no expert. I'm not the best at logic arguments and am not ashamed to say that Google has been my strongest tool for understanding Excel. But I am sure there are a few people out there who already know some basic formulas and could use a couple of suggestions to bump up their skills to the next level. So, if you find yourself manually fixing the information in Excel documents or doing the same steps over and over, this article should provide some ideas on ways to make your life (slightly) easier by mastering these 8 formulas.</p>
<p>The great thing about Excel is that you only need to know a small handful of formulas to do most of your tasks. Better yet, you can combine these formulas with the features I mention to supercharge your experience and cut down your Excel-related stress.</p>

<h2 class="mc-h2">7 Excel Features Everyone Should Know</h2>
<ol>
<li><strong>Filter</strong> - Allows you to filter and sort columns for sheet organization, data cleaning, and analysis</li>
<li><strong>Text to Columns</strong> - Lets you split up the contents of a cell into adjoining columns for sheet organization, data cleaning, and analysis</li>
<li><strong>Remove Duplicates</strong> - Does exactly what it sounds like, but the cool thing is you get to decide which columns should be assessed when identifying duplicates. It's fantastic for data cleaning.</li>
<li><strong>Record Macro</strong> - To make repetitive tasks go by faster - especially tasks related to sheet formatting. It can be tricky, so I recommend watching a few demonstrations before trying it on your own.</li>
<li><strong>Set Data Types</strong> - Excel can identify Countries and States based on Zip Codes or abbreviations and can convert prices into different currencies.<br><img class="mc-shot" src="{{ site.baseurl }}/assets/images/excel-data-types-geography-popup.png" alt="A screenshot of the Data Types section of the Data tab in Excel, with a pop up explaining how to use the Geography data type" width="327" loading="lazy"></li>
<li><strong>Copy/Paste as Value</strong> - Allows you to copy and paste cells/rows/columns in a spreadsheet without formulas or cell formatting.</li>
<li><strong>Conditional Formatting</strong> - Set up formatting rules based on cell content.</li>
</ol>
<p>Need to identify dates where total sales exceeded a certain amount? Use the "Greater Than..." option.</p>
<img class="mc-shot" src="{{ site.baseurl }}/assets/images/excel-conditional-formatting-greater-than.png" alt="A screenshot of the Greater Than option under Highlight Cells Rules in the Conditional Formatting menu in Excel" width="424" loading="lazy">
<p>Want to identify the webpage that received the top 10% of traffic last month?</p>
<img class="mc-shot" src="{{ site.baseurl }}/assets/images/excel-conditional-formatting-top-10-percent.png" alt="A screenshot of the Top 10% option under Top/Bottom Rules in the Conditional Formatting menu in Excel" width="390" loading="lazy">
<p>Excel has you covered with the "Top 10%" conditional formatting rule all set up!</p>
<p>I especially love combining the Highlight Duplicate Values rule with the "Sort by Color" then "Filter By Color" to identify datasets that share identical attributes. See what I mean about combining features?</p>

<h2 class="mc-h2">My 8 Favorite Formulas for Excel</h2>
<ol>
<li><strong>Text Join</strong> (<code>=TEXTJOIN</code>) Combines the text in two or more cells together with a designated separation like a space or period.<br>I've used this to create spreadsheets of social media posts for bulk uploading into #hubspot and #hootsuite</li>
<li><strong>Concatenate</strong> (<code>=CONCAT</code>) Similar to Text Join, Concatenate allows you to add text to one or more cells together.<br>I've used this to add a website's main URL to another cell which has the slug.</li>
<li><strong>VLookup</strong> (<code>=VLOOKUP</code>) This one is a bit complicated, and I would recommend watching a few examples first. It allows you to search for the contents of one cell (Like the abbreviation of a state) within a column in another Excel spreadsheet or document. If the value is found, the contents of the cell in one of the columns to the right of the matching value are returned.<br>For example, if I have a long column of state abbreviations, and I don't want to copy/paste over and over again, I'd add a blank column next to the abbreviations and use a VLOOKUP formula to search for each abbreviation in another document and return the full name of the state. So "NJ" returns a value of "New Jersey".</li>
<li><strong>Proper</strong> (<code>=PROPER</code>) Capitalizes the first letter of a word after each space.<br>Incredibly handy for cleaning First Names before importing them into your CRM. Who wants to get an email that says, "Hello MOLLY,"?</li>
<li><strong>Length</strong> (<code>=LEN</code>) Calculates the total number of characters in a particular cell.<br>I've used this to measure the length of social media posts for bulk scheduling and make sure they don't exceed the character limit.</li>
<li><strong>Identify if the cell has a number in it</strong> <code>=COUNT(FIND({0,1,2,3,4,5,6,7,8,9},CELL))&gt;0</code><br>Lets you find those sneaky numbers in cells that should be all text</li>
<li><strong>Left</strong> (<code>=LEFT</code>) Allows you to manipulate the contents of a cell based on its relation to the left-most position in the cell for example:<br>Remove EVERYTHING but the first character from the left of a string <code>=LEFT(CELL,1)</code><br>or<br>Remove the LAST character from the right of a string. <code>=LEFT(CELL, LEN(CELL) - 1)</code><br>Works great if you have a very large data set and want to organize your work by the first letter of someone's last name. Adjust the number to change the number of characters that need to be removed.</li>
<li><strong>Right</strong> (<code>=RIGHT</code>) Allows you to manipulate the contents of a cell based on its relation to the right-most or left-most position in the cell for example:<br>Remove EVERYTHING but the last character from the right of a string <code>=RIGHT(CELL,1)</code><br>or<br>Remove the LAST character from the left of a string <code>=RIGHT(CELL, LEN(CELL) - 1)</code><br>This is particularly helpful in removing strings of random numbers or symbols from a group of cells. Like if you are given a full list of membership numbers, but for privacy reasons, want to remove all but need the last 4 digits.</li>
</ol>
<p>I'm constantly on the lookout for new formulas to add to my arsenal, so let me know your favorites in the comments below.</p>

</div>
