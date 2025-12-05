Prompt engineering
Be clear, direct, and detailed

Copy page

While these tips apply broadly to all Claude models, you can find prompting tips specific to extended thinking models here.

When interacting with Claude, think of it as a brilliant but very new employee (with amnesia) who needs explicit instructions. Like any new employee, Claude does not have context on your norms, styles, guidelines, or preferred ways of working. The more precisely you explain what you want, the better Claude's response will be.

The golden rule of clear prompting
Show your prompt to a colleague, ideally someone who has minimal context on the task, and ask them to follow the instructions. If they're confused, Claude will likely be too.
How to be clear, contextual, and specific
Give Claude contextual information: Just like you might be able to better perform on a task if you knew more context, Claude will perform better if it has more contextual information. Some examples of contextual information:
What the task results will be used for
What audience the output is meant for
What workflow the task is a part of, and where this task belongs in that workflow
The end goal of the task, or what a successful task completion looks like
Be specific about what you want Claude to do: For example, if you want Claude to output only code and nothing else, say so.
Provide instructions as sequential steps: Use numbered lists or bullet points to better ensure that Claude carries out the task the exact way you want it to.
Examples

Example: Anonymizing customer feedback
Notice that Claude still makes mistakes in the unclear prompting example, such as leaving in a customer's name.

Role	Unclear Prompt	Clear Prompt
User	Please remove all personally identifiable information from these customer feedback messages: {{FEEDBACK_DATA}}	Your task is to anonymize customer feedback for our quarterly review.

Instructions:
1. Replace all customer names with "CUSTOMER_[ID]" (e.g., "Jane Doe" → "CUSTOMER_001").
2. Replace email addresses with "EMAIL_[ID]@example.com".
3. Redact phone numbers as "PHONE_[ID]".
4. If a message mentions a specific product (e.g., "AcmeCloud"), leave it intact.
5. If no PII is found, copy the message verbatim.
6. Output only the processed messages, separated by "---".

Data to process: {{FEEDBACK_DATA}}
Assistant (Claude's response)	Here are the anonymized customer feedback messages:
1. I've been using your software for years, and it's been great. But lately, AcmeCloud has been crashing a lot. Fix it!
2. XXX, your customer support rep, was incredibly helpful. He guided me through the whole process. My email is XXX if you want to send a survey.
3. I'm John Smith, and I'm not happy. I've been on hold for 2 hours trying to reach someone at XXX. This is unacceptable!	CUSTOMER_001: I've been using your software for years, and it's been great. But lately, AcmeCloud has been crashing a lot. Fix it!
---
CUSTOMER_002: CUSTOMER_SERVICE_001, your customer support rep, was incredibly helpful. He guided me through the whole process. My email is EMAIL_002@example.com if you want to send a survey.
---
CUSTOMER_003: I'm CUSTOMER_003, and I'm not happy. I've been on hold for 2 hours trying to reach someone at PHONE_001. This is unacceptable!

Example: Crafting a marketing email campaign
Notice that Claude makes up details to fill in the gaps where it lacks context with the vague prompt.

Role	Vague Prompt	Specific Prompt
User	Write a marketing email for our new AcmeCloud features.	Your task is to craft a targeted marketing email for our Q3 AcmeCloud feature release.

Instructions:
1. Write for this target audience: Mid-size tech companies (100-500 employees) upgrading from on-prem to cloud.
2. Highlight 3 key new features: advanced data encryption, cross-platform sync, and real-time collaboration.
3. Tone: Professional yet approachable. Emphasize security, efficiency, and teamwork.
4. Include a clear CTA: Free 30-day trial with priority onboarding.
5. Subject line: Under 50 chars, mention "security" and "collaboration".
6. Personalization: Use {{COMPANY_NAME}} and {{CONTACT_NAME}} variables.

Structure:
1. Subject line
2. Email body (150-200 words)
3. CTA button text
Assistant (Claude's response)	Here's a draft marketing email for our new features:

Subject: Boost Your Business with AcmeCloud's Latest Features

Dear Valued Customer,

We're excited to introduce three powerful features to AcmeCloud that will revolutionize your workflow:

1. Real-Time Collaboration: Work on documents simultaneously with your team. No more version control issues!
2. AI-Powered Insights: Make data-driven decisions with AI that analyzes trends and automates tasks.
3. Advanced Security Suite: End-to-end encryption, multi-factor auth, and threat detection keep your data safe.

Limited Offer: Upgrade now for a 20% first-year discount. Plus, refer a friend for an extra 10% off!

Best,
The AcmeCloud Team	Subject line: AcmeCloud: Enterprise security meets real-time teamwork

Email body:
Dear {{CONTACT_NAME}},

At {{COMPANY_NAME}}, you're scaling fast and eyeing the cloud. But with growth comes the challenge of keeping data secure while fostering collaboration. That's where AcmeCloud's Q3 release comes in, tailor-made for tech innovators like you.

1. Fort Knox for Your Files: Military-grade encryption now safeguards your data, both in motion and at rest. Your intellectual property stays yours, period.
2. Sync Without Borders: Windows, Mac, or Linux—AcmeCloud speaks all languages. Unified version control means no more "final_v2_REALLY_FINAL.doc".
3. Collaborate at Light Speed: Ditch the attachment ping-pong. Now your devs, designers, and data scientists co-create in real-time, slashing time-to-market.

Don't just take our word for it. Experience the AcmeCloud difference with our 30-day trial. And because we know time is your most precious asset, we're throwing in priority onboarding.

Elevate Your Team Now - Free 30-Day Trial

Example: Incident response
Notice that Claude outputs superfluous text and different formating with the vague prompt.

Role	Vague Prompt	Detailed Prompt
User	Analyze this AcmeCloud outage report and summarize the key points.

{{REPORT}}	Analyze this AcmeCloud outage report. Skip the preamble. Keep your response terse and write only the bare bones necessary information. List only:
1) Cause
2) Duration
3) Impacted services
4) Number of affected users
5) Estimated revenue loss.

Here's the report: {{REPORT}}
Assistant (Claude's response)	Here's a summary of the key points from the AcmeCloud outage report:

On May 15th, a misconfigured load balancer update caused significant traffic routing issues, resulting in a service outage from 09
to 13
UTC. The 4-hour 37-minute disruption impacted our core file syncing service and admin dashboard, rendering them inaccessible. Additionally, the mobile app experienced partial functionality loss. Approximately 68% of our user base, totaling 1.3 million users, were affected. Based on our Service Level Agreements (SLAs) and average revenue per user, we estimate a financial impact of $420,000 in service credits and potential customer churn.	1) Cause: Misconfigured load balancer update
2) Duration: 4h 37m (09:15-13
UTC, May 15)
3) Impacted: Core sync, admin dashboard (down); mobile app (partial)
4) Affected users: 1.3M (68% of base)
5) Est. revenue loss: $420,000

Use examples (multishot prompting) to guide Claude's behavior

Copy page

While these tips apply broadly to all Claude models, you can find prompting tips specific to extended thinking models here.

Examples are your secret weapon shortcut for getting Claude to generate exactly what you need. By providing a few well-crafted examples in your prompt, you can dramatically improve the accuracy, consistency, and quality of Claude's outputs. This technique, known as few-shot or multishot prompting, is particularly effective for tasks that require structured outputs or adherence to specific formats.

Power up your prompts: Include 3-5 diverse, relevant examples to show Claude exactly what you want. More examples = better performance, especially for complex tasks.
Why use examples?
Accuracy: Examples reduce misinterpretation of instructions.
Consistency: Examples enforce uniform structure and style.
Performance: Well-chosen examples boost Claude's ability to handle complex tasks.
Crafting effective examples
For maximum effectiveness, make sure that your examples are:

Relevant: Your examples mirror your actual use case.
Diverse: Your examples cover edge cases and potential challenges, and vary enough that Claude doesn't inadvertently pick up on unintended patterns.
Clear: Your examples are wrapped in <example> tags (if multiple, nested within <examples> tags) for structure.
Ask Claude to evaluate your examples for relevance, diversity, or clarity. Or have Claude generate more examples based on your initial set.

Example: Analyzing customer feedback
Notice that in the "no examples" version, Claude does not list multiple options for each category, despite its written analysis indicating that there are multiple categories for certain feedback. It also includes a long explanation when we may not want it to.

Role	No Examples	With Examples
User	Analyze this customer feedback and categorize the issues. Use these categories: UI/UX, Performance, Feature Request, Integration, Pricing, and Other. Also rate the sentiment (Positive/Neutral/Negative) and priority (High/Medium/Low).

Here is the feedback: {{FEEDBACK}}	Our CS team is overwhelmed with unstructured feedback. Your task is to analyze feedback and categorize issues for our product and engineering teams. Use these categories: UI/UX, Performance, Feature Request, Integration, Pricing, and Other. Also rate the sentiment (Positive/Neutral/Negative) and priority (High/Medium/Low). Here is an example:

<example>
Input: The new dashboard is a mess! It takes forever to load, and I can't find the export button. Fix this ASAP!
Category: UI/UX, Performance
Sentiment: Negative
Priority: High</example>

Now, analyze this feedback: {{FEEDBACK}}
Assistant (Claude's response)	Here's the analysis of the customer feedback:

Issue: UI/UX
Sentiment: Negative
Priority: High
The customer is frustrated with the new dashboard design, which they find cluttered and slow to load. They specifically call out the missing "export" button, which is likely a critical feature. This issue needs to be addressed as a high priority.

Issue: Integration
Sentiment: Positive
Priority: Medium
The customer is pleased with the existing Salesforce integration but would like to see support for Hubspot as well. This is a feature request that could be considered for a future product update.

Issue: Pricing
Sentiment: Negative
Priority: High
The customer finds the pricing to be unreasonable, especially for the basic features. They are threatening to switch to a competitor, so this is a high-priority issue that needs to be reviewed.

Issue: Performance
Sentiment Negative
Priority: High
The customer is experiencing critical issues with the mobile app, where large file uploads consistently result in crashes. This is a significant problem that impacts the customer's ability to use the product effectively and should be addressed as a high priority.

Issue: UI/UX
Sentiment: Positive
Priority: Low
The customer is overall satisfied with the product, specifically calling out the intuitive UI and excellent customer support. This is a positive piece of feedback that does not require any immediate action.	Here's the analysis of the customer feedback:

1. The new dashboard is a mess! It takes forever to load, and I can't find the export button. Fix this ASAP!
Category: UI/UX, Performance
Sentiment: Negative
Priority: High

2. Love the Salesforce integration! But it'd be great if you could add Hubspot too.
Category: Integration, Feature Request
Sentiment: Positive
Priority: Medium

3. Your pricing is ridiculous! $99/mo for basic features? I'm switching to Competitor X.
Category: Pricing
Sentiment: Negative
Priority: High

4. The mobile app keeps crashing when I try to upload large files (>50MB). This is critical for our field agents.
Category: Performance
Sentiment: Negative
Priority: High

5. Overall, I'm happy with the product. The UI is intuitive, and the customer support is top-notch. Keep it up!
Category: UI/UX, Other (Customer Support)
Sentiment: Positive
Priority: Low
Let Claude think (chain of thought prompting) to increase performance

Copy page

While these tips apply broadly to all Claude models, you can find prompting tips specific to extended thinking models here.

When faced with complex tasks like research, analysis, or problem-solving, giving Claude space to think can dramatically improve its performance. This technique, known as chain of thought (CoT) prompting, encourages Claude to break down problems step-by-step, leading to more accurate and nuanced outputs.

Before implementing CoT
Why let Claude think?
Accuracy: Stepping through problems reduces errors, especially in math, logic, analysis, or generally complex tasks.
Coherence: Structured thinking leads to more cohesive, well-organized responses.
Debugging: Seeing Claude's thought process helps you pinpoint where prompts may be unclear.
Why not let Claude think?
Increased output length may impact latency.
Not all tasks require in-depth thinking. Use CoT judiciously to ensure the right balance of performance and latency.
Use CoT for tasks that a human would need to think through, like complex math, multi-step analysis, writing complex documents, or decisions with many factors.
How to prompt for thinking
The chain of thought techniques below are ordered from least to most complex. Less complex methods take up less space in the context window, but are also generally less powerful.

CoT tip: Always have Claude output its thinking. Without outputting its thought process, no thinking occurs!
Basic prompt: Include "Think step-by-step" in your prompt.
Lacks guidance on how to think (which is especially not ideal if a task is very specific to your app, use case, or organization)

Example: Writing donor emails (basic CoT)
Role	Content
User	Draft personalized emails to donors asking for contributions to this year's Care for Kids program.

Program information:
<program>{{PROGRAM_DETAILS}}
</program>

Donor information:
<donor>{{DONOR_DETAILS}}
</donor>

Think step-by-step before you write the email.
Guided prompt: Outline specific steps for Claude to follow in its thinking process.
Lacks structuring to make it easy to strip out and separate the answer from the thinking.

Example: Writing donor emails (guided CoT)
Role	Content
User	Draft personalized emails to donors asking for contributions to this year's Care for Kids program.

Program information:
<program>{{PROGRAM_DETAILS}}
</program>

Donor information:
<donor>{{DONOR_DETAILS}}
</donor>

Think before you write the email. First, think through what messaging might appeal to this donor given their donation history and which campaigns they've supported in the past. Then, think through what aspects of the Care for Kids program would appeal to them, given their history. Finally, write the personalized donor email using your analysis.
Structured prompt: Use XML tags like <thinking> and <answer> to separate reasoning from the final answer.

Example: Writing donor emails (structured guided CoT)
Role	Content
User	Draft personalized emails to donors asking for contributions to this year's Care for Kids program.

Program information:
<program>{{PROGRAM_DETAILS}}
</program>

Donor information:
<donor>{{DONOR_DETAILS}}
</donor>

Think before you write the email in <thinking> tags. First, think through what messaging might appeal to this donor given their donation history and which campaigns they've supported in the past. Then, think through what aspects of the Care for Kids program would appeal to them, given their history. Finally, write the personalized donor email in <email> tags, using your analysis.
Examples

Example: Financial analysis without thinking
Without step-by-step thinking, Claude gives a recommendation that seems reasonable but lacks depth. It doesn't quantify the potential outcomes or consider historical market performance, which are crucial for making an informed decision.

Role	Content
User	You're a financial advisor. A client wants to invest $10,000. They can choose between two options: A) A stock that historically returns 12% annually but is volatile, or B) A bond that guarantees 6% annually. The client needs the money in 5 years for a down payment on a house. Which option do you recommend?
Assistant	Based on the information provided, I would recommend option B, the bond that guarantees a 6% annual return. Here's why:

1. Certainty: The bond offers a guaranteed 6% annual return, which provides certainty in financial planning. This is crucial when the client has a specific financial goal (down payment) with a fixed timeline (5 years).
2. Risk aversion: Since the client needs this money for an important life event (buying a house), they likely have a low risk tolerance. The volatility of the stock market could jeopardize their plans if there's a downturn close to when they need the funds.
3. Time horizon: With only 5 years, there's less time to recover from potential stock market downturns. Longer investment horizons (10+ years) are generally better suited for weathering stock market volatility.

While the stock's historical 12% return is attractive, past performance doesn't guarantee future results. The guaranteed 6% from the bond ensures the client will have the funds they need when it's time to make the down payment.

Example: Financial analysis with thinking
With step-by-step thinking, the advisor provides a much richer analysis. It calculates exact figures for both scenarios, considers historical market volatility, and deeply analyzes the client's risk tolerance. This thorough reasoning leads to a more confident and justifiable recommendation.

Role	Content
User	You're a financial advisor. A client wants to invest $10,000. They can choose between two options: A) A stock that historically returns 12% annually but is volatile, or B) A bond that guarantees 6% annually. The client needs the money in 5 years for a down payment on a house. Which option do you recommend? Think step-by-step.
Assistant	To determine the best investment option for our client, I'll consider several factors step-by-step:

<thinking>
1. Understand the client's goal and timeline:
- Goal: Down payment for a house
- Timeline: 5 years
- Implication: This is a short-term, high-priority financial goal. The client likely cannot afford significant risk or volatility.

2. Analyze Option A (Stock):
- Pro: Higher historical return (12% annually)
- Con: Volatile (implying potential for significant gains or losses)
- Calculate potential 5-year return:
- Best case (12% annually): $10,000 * (1.12)^5 ≈ $17,623.42
- Worst case (market crash): Could lose a substantial portion, e.g., 50% crash = $5,000

3. Analyze Option B (Bond):
- Pro: Guaranteed return (6% annually)
- Con: Lower return compared to historical stock performance
- Calculate 5-year return:
- Guaranteed: $10,000 * (1.06)^5 ≈ $13,382.25

4. Consider risk tolerance:
- Goal is a house down payment (essential, not discretionary)
- Short timeline (5 years) limits ability to recover from market downturns
- Conclusion: Client likely has low risk tolerance

5. Historical perspective:
- Stock's 12% is historical, not guaranteed
- In 5-year periods, stock market can vary wildly:
- 2003-2007 (pre-financial crisis): S&P 500 up ~82%
- 2007-2011 (during crisis): S&P 500 down ~2%
- Conclusion: Past performance doesn't guarantee future results, especially short-term

6. Final analysis:
- Option A (Stock): Higher potential return but unacceptable risk of not meeting the down payment goal
- Option B (Bond): Guaranteed to meet ~80% of best-case stock scenario, 100% certainty of having funds
</thinking>

<answer>
I recommend Option B, the bond with a guaranteed 6% annual return. While the stock's historical 12% return is tempting, the bond ensures you'll have $13,382.25 in 5 years for your house down payment. Given the importance and short timeline of your goal, the stock's volatility poses an unacceptable risk. The bond provides certainty, which is invaluable for such a crucial financial milestone.
</answer>

Use XML tags to structure your prompts

Copy page

While these tips apply broadly to all Claude models, you can find prompting tips specific to extended thinking models here.

When your prompts involve multiple components like context, instructions, and examples, XML tags can be a game-changer. They help Claude parse your prompts more accurately, leading to higher-quality outputs.

XML tip: Use tags like <instructions>, <example>, and <formatting> to clearly separate different parts of your prompt. This prevents Claude from mixing up instructions with examples or context.
Why use XML tags?
Clarity: Clearly separate different parts of your prompt and ensure your prompt is well structured.
Accuracy: Reduce errors caused by Claude misinterpreting parts of your prompt.
Flexibility: Easily find, add, remove, or modify parts of your prompt without rewriting everything.
Parseability: Having Claude use XML tags in its output makes it easier to extract specific parts of its response by post-processing.
There are no canonical "best" XML tags that Claude has been trained with in particular, although we recommend that your tag names make sense with the information they surround.
Tagging best practices
Be consistent: Use the same tag names throughout your prompts, and refer to those tag names when talking about the content (e.g, Using the contract in <contract> tags...).
Nest tags: You should nest tags <outer><inner></inner></outer> for hierarchical content.
Power user tip: Combine XML tags with other techniques like multishot prompting (<examples>) or chain of thought (<thinking>, <answer>). This creates super-structured, high-performance prompts.
Examples

Example: Generating financial reports
Without XML tags, Claude misunderstands the task and generates a report that doesn't match the required structure or tone. After substitution, there is also a chance that Claude misunderstands where one section (like the the Q1 report example) stops and another begins.

Role	No XML Tags	With XML Tags
User	You're a financial analyst at AcmeCorp. Generate a Q2 financial report for our investors. Include sections on Revenue Growth, Profit Margins, and Cash Flow, like with this example from last year: {{Q1_REPORT}}. Use data points from this spreadsheet: {{SPREADSHEET_DATA}}. The report should be extremely concise, to the point, professional, and in list format. It should and highlight both strengths and areas for improvement.	You're a financial analyst at AcmeCorp. Generate a Q2 financial report for our investors.

AcmeCorp is a B2B SaaS company. Our investors value transparency and actionable insights.

Use this data for your report:<data>{{SPREADSHEET_DATA}}</data>

<instructions>
1. Include sections: Revenue Growth, Profit Margins, Cash Flow.
2. Highlight strengths and areas for improvement.
</instructions>

Make your tone concise and professional. Follow this structure:
<formatting_example>{{Q1_REPORT}}</formatting_example>
Assistant	Q2 Financial Report for AcmeCorp Investors

Dear Valued Investors,

I am pleased to present our Q2 financial report, showcasing AcmeCorp's continued growth and resilience in the B2B SaaS market.

1. Revenue Growth:
Our Q2 revenue reached $15.2M, a 22% YoY increase. This growth is primarily driven by a 30% expansion in our enterprise client base. However, our SMB segment saw a slight decline of 5%, which we aim to address through targeted marketing initiatives in Q3.

2. Profit Margins:
Gross margin improved to 72% (up 3% from Q1) due to infrastructure optimizations. EBITDA margin, however, dipped to 18% (down 2%) as we invested heavily in R&D for our upcoming AI-driven features.

3. Cash Flow:
Operating cash flow remains strong at $4.1M. Our cash reserves stand at $28M, providing a 15-month runway at current burn rate. We did see a 20% increase in customer acquisition costs, which we're addressing through more efficient sales strategies.

In summary, AcmeCorp's core financials remain robust. We're balancing growth investments with prudent cash management. Our focus for Q3 will be revitalizing SMB growth and optimizing sales efficiency.

Thank you for your continued trust.

Sincerely,
CFO, AcmeCorp	Q2 Financial Report for AcmeCorp Investors</output>

Revenue Growth:
- Q2 revenue: $15.2M (22% YoY ↑)
- Enterprise clients: 30% ↑
- SMB segment: 5% ↓
Action: Targeted Q3 marketing

Profit Margins:
- Gross margin: 72% (3% ↑ from Q1)
Reason: Infrastructure optimizations
- EBITDA margin: 18% (2% ↓)
Reason: R&D investment in AI features

Cash Flow:
- Operating cash flow: $4.1M (strong)
- Cash reserves: $28M (15-month runway)
- Customer acquisition cost: 20% ↑
Action: Optimize sales strategies

Outlook:
- Core financials: Robust
- Q3 focus: Revitalize SMB, optimize sales

Management remains committed to balancing growth investments with financial discipline.

Example: Legal contract analysis
Without XML tags, Claude's analysis is disorganized and misses key points. With tags, it provides a structured, thorough analysis that a legal team can act on.

Role	No XML Tags	With XML Tags
User	Analyze this software licensing agreement for potential risks and liabilities: {{CONTRACT}}. Focus on indemnification, limitation of liability, and IP ownership clauses. Also, note any unusual or concerning terms. Here's our standard contract for reference: {{STANDARD_CONTRACT}}. Give a summary of findings and recommendations for our legal team.	Analyze this software licensing agreement for legal risks and liabilities.

We're a multinational enterprise considering this agreement for our core data infrastructure.

<agreement>
{{CONTRACT}}</agreement>

This is our standard contract for reference:
<standard_contract>{{STANDARD_CONTRACT}}</standard_contract>

<instructions>
1. Analyze these clauses:
- Indemnification
- Limitation of liability
- IP ownership

2. Note unusual or concerning terms.

3. Compare to our standard contract.

4. Summarize findings in <findings> tags.

5. List actionable recommendations in <recommendations> tags.</instructions>
Assistant	The provided software licensing agreement presents several concerning aspects. The indemnification clause is overly broad, potentially exposing us to significant liabilities. The limitation of liability section caps damages at a mere $500, which is inadequate for our enterprise-level usage. Regarding IP, the agreement grants the vendor joint ownership of any modifications or integrations we create.

In summary, this agreement is not in our best interest. It exposes us to undue risk, limits our recourse in case of failures, and compromises our intellectual property rights. I recommend renegotiating these terms or seeking alternative vendors.	<findings>
1. Indemnification (Clause 8):
- Issue: Overly broad. We indemnify vendor against "any and all claims" arising from our use.
- Risk: Could hold us liable even for vendor's negligence or product defects.
- Deviation: Our standard limits indemnity to claims arising from our violation of agreement.

2. Limitation of Liability (Clause 9):
- Issue: Caps all damages at $500, including direct damages.
- Risk: Grossly inadequate for enterprise use. A critical failure could cost millions.
- Deviation: Our standard allows for direct damages up to 12 months of fees paid.

3. IP Ownership (Clause 12):
- Issue: Grants vendor joint ownership of our modifications/integrations.
- Risk: Vendor could use or sell our proprietary algorithms or data insights.
- Deviation: Our standard retains full ownership of our work.

4. Unusual Terms:
- Clause 5.3: Vendor can use our usage data for "any purpose."
- Clause 7.2: Vendor can terminate for "convenience" with only 7 days' notice.
- Clause 11: No warranties of any kind, even for basic merchantability.
</findings>

<recommendations>
1. Reject this agreement. Risks far outweigh benefits for an enterprise.
2. Counter-propose:
- Indemnification: Limit to claims arising from our violation of agreement.
- Liability: Cap at 12 months' fees for direct damages; negotiate for indirect.
- IP: Full ownership of our modifications/integrations.
- Data Use: Restrict to service improvement only.
- Termination: Minimum 90 days' notice; only for cause.
- Warranties: Demand basic merchantability and fitness for purpose.
3. If vendor refuses, explore alternative providers or in-house solutions.
4. Engage legal counsel for contract negotiation given high stakes.
</recommendations>

Legal contract analysis without role prompting
Role	Content
User	Analyze this software licensing agreement for potential risks:
<contract>
{{CONTRACT}}
</contract>

Focus on indemnification, liability, and IP ownership.
Assistant	Here's a summary of the key points in the software licensing agreement:

1. Indemnification (Section 8):
- We indemnify the vendor against claims arising from our use.

2. Limitation of Liability (Section 9):
- Damages capped at $500.

3. IP Ownership (Section 12):
- We retain ownership of our modifications.

Overall, the agreement seems standard. The indemnification and liability clauses are typical, and we maintain our IP rights.
With a role, Claude catches critical issues that could cost millions:


Legal contract analysis with role prompting
Role	Content
User	You are the General Counsel of a Fortune 500 tech company. We're considering this software licensing agreement for our core data infrastructure:
<contract>
{{CONTRACT}}
</contract>

Analyze it for potential risks, focusing on indemnification, liability, and IP ownership. Give your professional opinion.
Assistant	I've reviewed the software licensing agreement, and I have serious concerns that could expose our company to significant risks:

1. Indemnification (Section 8):
- Critical Issue: We indemnify the vendor against "any and all claims" arising from our use.
- Risk: This could hold us liable even for the vendor's negligence or product defects.
- Recommendation: Reject. Limit our indemnity to claims arising from our violation of the agreement.

2. Limitation of Liability (Section 9):
- Critical Issue: Damages capped at $500, including direct damages.
- Risk: Grossly inadequate. A critical failure in our data infrastructure could cost us millions in lost revenue and reputational damage.
- Recommendation: Reject. Negotiate for cap at 12 months of fees for direct damages, and carve-outs for data breaches.

3. IP Ownership (Section 12):
- Critical Issue: Vendor gains joint ownership of our modifications and integrations.
- Risk: They could use or sell our proprietary algorithms or data insights to competitors.
- Recommendation: Reject. We must retain full ownership of our work.

Professional Opinion: Do not sign this agreement. It is grossly unfavorable and exposes us to unacceptable levels of risk. If the vendor refuses to renegotiate these terms, I strongly advise exploring alternative providers or accelerating our in-house solution. The potential costs of proceeding with this agreement far outweigh any short-term gains.
Example 2: Financial analysis
Without a role, Claude's analysis lacks depth:


Financial analysis without role prompting
Role	Content
User	Analyze this dataset of our Q2 financials:
<data>
{{FINANCIALS}}
</data>

Highlight key trends and recommend actions.
Assistant	Here's a summary of your Q2 financials:

1. Revenue: $15.2M, up 22% YoY. Enterprise client base grew 30%.
2. Gross Margin: 72%, up 3% from Q1.
3. EBITDA Margin: 18%, down 2% due to R&D investments.
4. Cash Flow: $4.1M operating, $28M in reserves.

Overall, financials look strong with revenue growth and healthy margins. Increased R&D spending is impacting profitability but could pay off long-term. Maintain current course.
With a role, Claude delivers actionable insights:


Financial analysis with role prompting
Role	Content
User	You are the CFO of a high-growth B2B SaaS company. We're in a board meeting discussing our Q2 financials:
<data>
{{FINANCIALS}}
</data>

Analyze key trends, flag concerns, and recommend strategic actions. Our investors want aggressive growth but are wary of our burn rate.
Assistant	Board members, here's my analysis of our Q2 financials:

1. Revenue ($15.2M, +22% YoY):
- Insight: Enterprise growth (+30%) is outpacing overall growth.
- Flag: SMB segment declined 5%.
- Action: Reallocate 20% of SMB marketing budget to enterprise sales. Task product to simplify SMB onboarding.

2. Margins (Gross: 72%, +3% QoQ; EBITDA: 18%, -2% QoQ):
- Insight: Infrastructure optimizations boosted gross margins.
- Flag: R&D spend on AI features dented EBITDA.
- Action: No change. Our AI roadmap is critical for enterprise stickiness.

3. Cash ($4.1M OCF, $28M reserves):
- Insight: 15-month runway at current burn.
- Flag: CAC up 20%, eroding LTV/CAC.
- Action: Freeze non-essential hires. Implement sales funnel analytics to cut CAC by 15% in Q3.

Strategic Stance: We're threading the needle between growth and burn. Enterprise focus is our growth engine—invest there. But watch SMB churn; it could bleed into enterprise. Our AI bet is sound, but we must convert it to ARR by Q4, or we cut R&D by 30%.

In sum: Double down on enterprise, streamline SMB, optimize sales, and monetize AI. Questions?
Prefill Claude's response for greater output control

Copy page

While these tips apply broadly to all Claude models, you can find prompting tips specific to extended thinking models here.

Prefilling is only available for non-extended thinking modes. It's not currently supported with extended thinking.

When using Claude, you have the unique ability to guide its responses by prefilling the Assistant message. This powerful technique allows you to direct Claude's actions, skip preambles, enforce specific formats like JSON or XML, and even help Claude maintain character consistency in role-play scenarios.

In some cases where Claude is not performing as expected, a few prefilled sentences can vastly improve Claude's performance. A little prefilling goes a long way!

How to prefill Claude's response
To prefill, include the desired initial text in the Assistant message (Claude's response will continue from where the Assistant message leaves off):

import anthropic

client = anthropic.Anthropic()
response = client.messages.create(
    model="claude-sonnet-4-5",
    max_tokens=1024,
    messages=[
        {"role": "user", "content": "What is your favorite color?"},
        {"role": "assistant", "content": "As an AI assistant, I don't have a favorite color, But if I had to pick, it would be green because"}  # Prefill here
    ]
)
The prefill content cannot end with trailing whitespace. A prefill like "As an AI assistant, I " (with a space at the end) will result in an error.

Examples
Example 1: Controlling output formatting and skipping the preamble
Power user tip: Prefilling { forces Claude to skip the preamble and directly output the JSON object. This is cleaner, more concise, and easier for programs to parse without additional processing. For guaranteed JSON output that conforms to a specific schema, consider using Structured Outputs instead of prefilling. Structured outputs ensure Claude's response always matches your defined JSON schema, making it ideal for production applications that require strict format compliance.

Example: Structured data extraction without prefilling
Role	Content
User	Extract the name, size, price, and color from this product description as a JSON object:

<description>
The SmartHome Mini is a compact smart home assistant available in black or white for only $49.99. At just 5 inches wide, it lets you control lights, thermostats, and other connected devices via voice or app—no matter where you place it in your home. This affordable little hub brings convenient hands-free control to your smart devices.
</description>
Assistant	Here's the extracted information in JSON format:

```json
{
"name": "SmartHome Mini",
"size": "5 inches wide",
"price": "$49.99",
"colors": ["black", "white"]
}
```

I've extracted the following details from the product description:
- Name: SmartHome Mini
- Size: 5 inches wide
- Price: $49.99
- Colors: Available in black and white

The JSON object provides a structured format that's easy for programs to parse and use. Let me know if you need any modifications or have any other questions!

Example: Structured data extraction with prefilling
Role	Content
User	Extract the name, size, price, and color from this product description as a JSON object:

<description>
The SmartHome Mini is a compact smart home assistant available in black or white for only $49.99. At just 5 inches wide, it lets you control lights, thermostats, and other connected devices via voice or app—no matter where you place it in your home. This affordable little hub brings convenient hands-free control to your smart devices.
</description>
Assistant (prefill)	{
Assistant (Claude's response)	"name": "SmartHome Mini",
"size": "5 inches wide",
"price": "$49.99",
"colors": [
"black",
"white"
]
}
Example 2: Maintaining character in roleplay scenarios
Role-play tip: Prefilling a bracketed [ROLE_NAME] can remind Claude stay in character, even for longer and more complex conversations. This is especially powerful when combined with role prompting in the system parameter.

Example: Maintaining character without role prompting
Role	Content
User (50 conversation turns in with "Sherlock Holmes" Claude)	What do you deduce about the owner of this shoe? <image>muddy_shoe.jpg</image>
Assistant	As an AI assistant, I would be happy to analyze the image of a muddy shoe as if you had provided it. Here's my deduction...

Example: Maintaining character with role prompting
Role	Content
User (50 conversation turns in with "Sherlock Holmes" Claude)	What do you deduce about the owner of this shoe?
<image>muddy_shoe.jpg</image>
Assistant (prefill)	[Sherlock Holmes]
Assistant (Claude's response)	Ah, what have we here? A most curious specimen, Watson! Let us examine this shoe with a discerning eye. The mud, you see, is not your common London clay, but rather the distinctive reddish hue of the iron-rich soil found only in the environs of Hampstead Heath. And yet, the wear on the sole suggests a gait more suited to the cobblestones of Whitechapel than the gentle slopes of the Heath.

Now, observe the laces! They are tied with a particular knot favored by those in the medical profession—doubtless a habit acquired during years of tying surgical gowns. But the scuff marks on the toe box tell a different tale: they are consistent with the kicking motion one might employ in the martial arts, specifically Baritsu.

We may conclude, then, that our absent shoe owner is a doctor, possibly a surgeon, who resides in Whitechapel but frequents Hampstead Heath—perhaps for a secret Baritsu practice, away from prying eyes. A most intriguing case, Watson! We must make haste; the game is afoot!
Prompt engineering
Chain complex prompts for stronger performance

Copy page

While these tips apply broadly to all Claude models, you can find prompting tips specific to extended thinking models here.

When working with complex tasks, Claude can sometimes drop the ball if you try to handle everything in a single prompt. Chain of thought (CoT) prompting is great, but what if your task has multiple distinct steps that each require in-depth thought?

Enter prompt chaining: breaking down complex tasks into smaller, manageable subtasks.

Why chain prompts?
Accuracy: Each subtask gets Claude's full attention, reducing errors.
Clarity: Simpler subtasks mean clearer instructions and outputs.
Traceability: Easily pinpoint and fix issues in your prompt chain.
When to chain prompts
Use prompt chaining for multi-step tasks like research synthesis, document analysis, or iterative content creation. When a task involves multiple transformations, citations, or instructions, chaining prevents Claude from dropping or mishandling steps.

Remember: Each link in the chain gets Claude's full attention!

Debugging tip: If Claude misses a step or performs poorly, isolate that step in its own prompt. This lets you fine-tune problematic steps without redoing the entire task.
How to chain prompts
Identify subtasks: Break your task into distinct, sequential steps.
Structure with XML for clear handoffs: Use XML tags to pass outputs between prompts.
Have a single-task goal: Each subtask should have a single, clear objective.
Iterate: Refine subtasks based on Claude's performance.
Example chained workflows:
Multi-step analysis: See the legal and business examples below.
Content creation pipelines: Research → Outline → Draft → Edit → Format.
Data processing: Extract → Transform → Analyze → Visualize.
Decision-making: Gather info → List options → Analyze each → Recommend.
Verification loops: Generate content → Review → Refine → Re-review.
Optimization tip: For tasks with independent subtasks (like analyzing multiple docs), create separate prompts and run them in parallel for speed.
Advanced: Self-correction chains
You can chain prompts to have Claude review its own work! This catches errors and refines outputs, especially for high-stakes tasks.


Example: Self-correcting research summary
Examples

Example: Analyzing a legal contract (without chaining)
Note that Claude misses the instruction to provide proposed changes in its email draft.

Role	Content
User	You're our Chief Legal Officer. Review this SaaS contract for risks, focusing on data privacy, SLAs, and liability caps.

<contract>
{{CONTRACT}}
</contract>

Then draft an email to the vendor with your concerns and proposed changes.
Assistant	After reviewing the SaaS contract, I've identified several concerns:

1. Data Privacy (Section 7):
- Issue: Vendor has broad rights to use client data for "service improvement."
- Risk: Could lead to unauthorized data sharing or monetization.

2. SLAs (Section 5):
- Issue: 99.5% uptime guarantee is below industry standard.
- Risk: Excessive downtime could impact our operations.

3. Liability (Section 9):
- Issue: Cap set at 3 months of fees.
- Risk: Inadequate for potential data breaches or service failures.

Draft email:

Dear {{VENDOR}},

After reviewing the SaaS agreement, we have concerns:

1. Data Privacy: We require that our data only be used for direct service provision, not broad "service improvement." Please amend Section 7.

2. SLAs: 99.5% uptime is insufficient. We need 99.99% with clearly defined penalties. Please revise Section 5.

3. Liability: The current cap of 3 months' fees is inadequate. We propose a cap of 12 months' fees, with no cap for data breaches or willful misconduct.

We value our potential partnership and believe these changes will set us up for success. Please send a revised agreement.

Best regards,
{{CLO_NAME}}

Example: Analyzing a legal contract (with chaining)
Prompt 1
Role	Content
User	You're our Chief Legal Officer. Review this SaaS contract for risks, focusing on data privacy, SLAs, and liability caps.

<contract>
{{CONTRACT}}
</contract>

Output your findings in <risks> tags.
Assistant
{{CONCERNS}}	1. Data Privacy (Section 7):
- Issue: Vendor has broad rights to use client data for "service improvement."
- Risk: Could lead to unauthorized data sharing or monetization of client data.
- Impact: Potential breach of client trust, regulatory fines (GDPR, CCPA).

2. SLAs (Section 5):
- Issue: 99.5% uptime guarantee is below industry standard (typically 99.99%).
- Risk: Up to 43.8 hours of downtime per year vs. 52.6 minutes at 99.99%.
- Impact: Operational disruptions, revenue loss, client dissatisfaction.

3. Liability (Section 9):
- Issue: Liability cap set at 3 months of fees.
- Risk: Inadequate for potential data breaches, IP theft, or prolonged service failures.
- Impact: Insufficient compensation for damages that could far exceed the cap, like class-action lawsuits or regulatory fines.
Prompt 2
Role	Content
User	Draft an email to a SaaS product vendor outlining the following concerns and proposing changes. Here are the concerns:
<concerns>
{{CONCERNS}}
</concerns>

Assistant
{{EMAIL}}	Dear {{VENDOR}},

After a thorough review of the proposed SaaS agreement, our legal team has identified several high-priority concerns that must be addressed before we can proceed:

1. Data Privacy (Section 7):
- Current: Broad rights to use client data for "service improvement."
- Concern: Potential unauthorized data sharing or monetization.
- Proposed Change: Limit data use to direct service provision. Any use for improvement, analytics, or marketing must be opt-in, revocable, and anonymized.

2. SLAs (Section 5):
- Current: 99.5% uptime guarantee.
- Concern: Up to 43.8 hours of downtime per year, risking operational disruptions.
- Proposed Change: 99.99% uptime with tiered service credits. E.g., 10% credit for <99.99%, 25% for <99.9%, 50% for <99.5%.

3. Liability (Section 9):
- Current: Cap at 3 months of fees.
- Concern: Grossly inadequate for data breaches, IP theft, or prolonged outages.
- Proposed Change: 12 months' fees for general liability. Uncapped for data breaches, willful misconduct, IP infringement.

These changes are non-negotiable for us. They align with industry standards and our commitment to data security, operational excellence, and fiduciary responsibility. We value the potential of our partnership, and addressing these will set a strong foundation.

Please have your legal team review and incorporate these changes. We're happy to discuss further to ensure mutual understanding and agreement.

Best regards,
{{CLO_NAME}}
Prompt 3
Role	Content
User	Your task is to review an email and provide feedback. Here is the email:
<email>
{{EMAIL}}
</email>

Give feedback on tone, clarity, and professionalism.
Assistant	1. Tone:
- Professional and assertive without being confrontational.
- Use of "non-negotiable" is strong but justified given the criticality of the issues.
- Collaborative language ("we value," "happy to discuss") balances the firmness, maintaining a constructive tone.

2. Clarity:
- Excellent structuring: Current state, concern, and proposed change for each issue.
- Technical terms (e.g., "EBITDA," "tiered service credits") are appropriate for a B2B SaaS context.
- Action items are clear: vendor's legal team to review and incorporate changes.

3. Professionalism:
- Focuses on mutual benefit and industry standards, not just our demands.
- Mentions broader responsibilities (data security, operational excellence, fiduciary duty), elevating the discussion.
- Offers further discussion, showing commitment to understanding and resolving issues.

Overall, the email strikes the right balance of assertiveness and collaboration. It clearly articulates our concerns, proposes specific solutions, and maintains a professional, partnership-oriented tone. No revisions needed; proceed with sending.

Example: Multitenancy strategy review
Prompt 1
Role	Content
User	As a senior solutions architect, review and analyze this multitenancy strategy for our new enterprise SaaS product.

<strategy>
{{STRATEGY}}
</strategy>

Focus on scalability, security, and cost-effectiveness.
Assistant
{{ANALYSIS}}	1. Scalability:
+ Database sharding by tenant reduces contention, supports high growth.
+ Microservices allow independent scaling of components.
- Shared app servers could bottleneck under extreme load.
- No mention of auto-scaling or load balancing for app tier.

2. Security:
+ Tenant data isolation via sharding mitigates data leaks.
+ JWT with short expiry and refresh tokens is industry best practice.
- No mention of encryption (at rest, in transit) or key management.
- IAM strategy lacks detail on roles, permissions, or RBAC.

3. Cost-effectiveness:
+ Shared app servers reduce idle resource costs.
+ Serverless functions for infrequent tasks optimize costs.
- Per-tenant DB could increase costs at scale vs. optimized multi-tenant DB.
- No discussion of reserved instances or spot instances for cost saving.
Prompt 2
Role	Content
User	Draft a strategy review document for engineering leadership based on this analysis of a multitenancy strategy.

<strategy>
{{STRATEGY}}
</strategy>

<analysis>
{{ANALYSIS}}
</analysis>

Include an executive summary, detailed analysis, and recommendations.
Assistant
{{STRATEGY_DOC}}	# Multitenancy Strategy Review: SaaS Enterprise Product

## Executive Summary
The proposed strategy demonstrates a solid foundation in scalability and security principles but has gaps in implementation details. It excels in data isolation and component-level scaling but lacks robust app-tier scaling and advanced security measures. Cost optimizations are present but may falter at high scale. With targeted enhancements, this strategy can effectively support our enterprise SaaS ambitions.

## Detailed Analysis

### 1. Scalability: B+

Strengths:
- Database sharding by tenant is excellent. It minimizes query latency, supports high data growth, and facilitates seamless per-tenant scaling.
- Microservices architecture allows scaling individual components based on demand, crucial for handling diverse enterprise workloads.

Weaknesses:
- Shared application servers risk becoming a bottleneck. As tenant count and traffic grow, these could degrade performance across all tenants.
- Absence of auto-scaling and load balancing for the app tier is a critical oversight. These are essential for handling traffic spikes without over-provisioning.

### 2. Security: B-

Strengths:
- Sharded databases provide strong tenant data isolation, mitigating risks of data leaks or unauthorized access between tenants.
- JWT with short expiry and refresh tokens align with OWASP best practices, reducing token vulnerability windows.

Weaknesses:
- No mention of data encryption at rest or in transit (TLS 1.3). This is non-negotiable for enterprise data.
- Key management strategy is missing. How are encryption keys, JWT secrets, and DB credentials managed and rotated?
- IAM lacks depth. We need RBAC with well-defined roles, attribute-based access control (ABAC) for fine-grained permissions, and integration with enterprise identity providers (SAML, OIDC).

### 3. Cost-effectiveness: B

Strengths:
- Shared app servers reduce idle capacity costs, good for steady-state traffic.
- Serverless for infrequent tasks (e.g., reporting) is smart; pay only when these resources are used.

Weaknesses:
- Per-tenant databases may not be cost-effective at scale compared to a well-designed multi-tenant database with robust data partitioning.
- No mention of cost-saving measures like reserved instances for predictable workloads or spot instances for fault-tolerant tasks.
- Lack of app-tier auto-scaling could lead to over-provisioning, increasing costs.

## Recommendations

1. App Tier Resilience: Implement auto-scaling with Kubernetes or cloud-native services (EKS, GKE). Deploy across availability zones with a CDN for static assets.

2. Security Hardening:
a. Encrypt data at rest (AES-256) and in transit (TLS 1.3).
b. Use a managed KMS (AWS KMS, GCP KMS) for key management.
c. Enhance IAM with RBAC, ABAC, and SAML/OIDC for enterprise SSO.

3. Cost Optimization:
a. Evaluate columnar multi-tenant DB (e.g., Snowflake) vs. sharding at scale.
b. Use reserved instances for app servers, spot instances for non-critical workloads.
c. Implement proactive monitoring and right-sizing to avoid overprovisioning.

4. Proof of Concept (PoC): Before full implementation, conduct a PoC with a high-scale simulation:
a. Test sharded DB vs. optimized multi-tenant DB for cost and performance.
b. Stress-test app tier with simulated enterprise-level traffic spikes.
c. Conduct third-party security audit, focusing on data isolation and access controls.

With these enhancements, our multi-tenancy strategy will be enterprise-grade: scalable, secure, and cost-effective. The PoC will validate our design choices and instill confidence in our enterprise clients.
Prompt 3
Role	Content
User	Grade this strategy review document for clarity, actionability, and alignment with enterprise priorities.

<priorities>
{{PRIORITIES}}
</priorities>

<strategy_doc>
{{STRATEGY_DOC}}
</strategy_doc>
Assistant	1. Clarity: A
+ Clear structure with Executive Summary, Detailed Analysis, and Recommendations.
+ Analysis uses a grading system (B+, B-) for quick grasp of strengths/weaknesses.
+ Technical terms (RBAC, ABAC, TLS) are explained or contextualized, aiding non-technical leadership.
+ Visual aids (bullet points, indentation) enhance readability.

2. Actionability: A-
+ Recommendations are specific and technical (e.g., "Implement auto-scaling with Kubernetes").
+ PoC plan with clear objectives provides a roadmap.
+ Missing: Timelines, resource requirements, or team assignments for each recommendation.
+ Consider: Add a "Next Steps" section with immediate actions, roles, and a high-level timeline.

3. Enterprise Alignment: A+
+ Directly addresses enterprise priorities:
- Scalability: Discusses handling enterprise-level traffic spikes.
- Security: Focuses on data isolation, encryption, and enterprise IAM.
- Cost: Strategies align with enterprise FinOps (reserved instances, right-sizing).
+ PoC with "high-scale simulation" and security audit shows commitment to enterprise-grade quality.
+ Language resonates with enterprise concerns: "unacceptable risk," "enterprise-grade," "instill confidence."

Overall, the document excels in clarity and enterprise alignment. The actionability is strong but could be elevated to A+ with a "Next Steps" section. The technical depth, coupled with clear explanations, makes this highly effective for both technical and non-technical leadership. Great work!
Prompt engineering
Long context prompting tips

Copy page

While these tips apply broadly to all Claude models, you can find prompting tips specific to extended thinking models here.

Claude's extended context window (200K tokens for Claude 3 models) enables handling complex, data-rich tasks. This guide will help you leverage this power effectively.

Essential tips for long context prompts
Put longform data at the top: Place your long documents and inputs (~20K+ tokens) near the top of your prompt, above your query, instructions, and examples. This can significantly improve Claude's performance across all models.

Queries at the end can improve response quality by up to 30% in tests, especially with complex, multi-document inputs.
Structure document content and metadata with XML tags: When using multiple documents, wrap each document in <document> tags with <document_content> and <source> (and other metadata) subtags for clarity.


Example multi-document structure
<documents>
  <document index="1">
    <source>annual_report_2023.pdf</source>
    <document_content>
      {{ANNUAL_REPORT}}
    </document_content>
  </document>
  <document index="2">
    <source>competitor_analysis_q2.xlsx</source>
    <document_content>
      {{COMPETITOR_ANALYSIS}}
    </document_content>
  </document>
</documents>

Analyze the annual report and competitor analysis. Identify strategic advantages and recommend Q3 focus areas.
Ground responses in quotes: For long document tasks, ask Claude to quote relevant parts of the documents first before carrying out its task. This helps Claude cut through the "noise" of the rest of the document's contents.


Example quote extraction
You are an AI physician's assistant. Your task is to help doctors diagnose possible patient illnesses.

<documents>
  <document index="1">
    <source>patient_symptoms.txt</source>
    <document_content>
      {{PATIENT_SYMPTOMS}}
    </document_content>
  </document>
  <document index="2">
    <source>patient_records.txt</source>
    <document_content>
      {{PATIENT_RECORDS}}
    </document_content>
  </document>
  <document index="3">
    <source>patient01_appt_history.txt</source>
    <document_content>
      {{PATIENT01_APPOINTMENT_HISTORY}}
    </document_content>
  </document>
</documents>

Find quotes from the patient records and appointment history that are relevant to diagnosing the patient's reported symptoms. Place these in <quotes> tags. Then, based on these quotes, list all information that would help the doctor diagnose the patient's symptoms. Place your diagnostic information in <info> tags.
