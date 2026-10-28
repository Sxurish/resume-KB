---
framework_version: 1.0.0
---

# Interview Preparation Guide

<!-- SETUP: STAR examples are personalized by running /setup based on your actual experience -->

## STAR Format

Structure answers as: **Situation** (context), **Task** (your responsibility), **Action** (what you did), **Result** (outcome).

Keep answers to 1-2 minutes. Be specific. End with what you learned or would do differently.

## Ready-Made STAR Examples

<!-- These are populated by /setup from your actual experience. Below are templates showing the format. -->

Facts below come from the /setup interview (2026-10-28) and the project READMEs. Items marked **[confirm]** need Kayky's details before use; never invent numbers in an interview.

### 1. Pedido Certo database design (data modeling, SQL, security)
**S:** Restaurants lose orders and time when waiters walk tickets to the kitchen and bar. HSB wanted a SaaS that many restaurants could share safely.
**T:** As HSB's lead developer, design the data layer so each restaurant only sees its own data and prices cannot be tampered with from the phone.
**A:** Modeled the schema in PostgreSQL (Supabase) with `restaurant_id` on every table and Row Level Security policies; moved business rules into database functions (`place_order` recalculates prices from the menu, validates options, rejects sold-out items, and is idempotent on a client-generated id so offline retries never duplicate orders); added bcrypt PIN login with lockout and an audit log; wrote unit, database and Playwright tests. Built with Claude Code and reviewed the design choices myself.
**R:** v1 complete with waiter, station, cashier and manager screens. Pilot with a restaurant was discussed but not closed. **[confirm: number of tests, time spent]**
**Use for:** "Tell me about a database you designed", "How do you ensure data quality / integrity?", "Tell me about a project you are proud of"

### 2. Second internet link with load balancing (infrastructure, reliability)
**S:** The registry office depended on a single internet connection for its daily work. **[confirm: what problem triggered it - outages, slowness?]**
**T:** Help implement a second link and keep the office online if one link fails.
**A:** Contributed to installing the second internet link and configuring load balancing on the router. **[confirm: equipment/router model, your exact part vs. the provider's]**
**R:** The office gained connection redundancy. **[confirm: any measurable effect, e.g. fewer outages]**
**Use for:** "Tell me about improving reliability", "Describe a technical problem you solved", "Experience with networking"

### 3. CRM Jurídico with WhatsApp chatbot (integration, privacy, AI)
**S:** A law office needed to triage leads arriving through WhatsApp and keep client data compliant with LGPD.
**T:** Build an intake chatbot and an internal CRM that records consent and routes leads to the team.
**A:** Implemented a WhatsApp webhook with signature validation and deduplication, LGPD consent records, lead, case, contract and finance modules, private document storage with RLS, and an AI triage route that returns Zod-validated JSON from several model providers (including Anthropic Claude). Built with Claude Code.
**R:** In final stage, being integrated with the chatbot before launch. **[confirm: launch date]**
**Use for:** "Experience with APIs / integrations", "How do you handle sensitive data?", "Experience with AI tools"

### 4. Learning while working full-time (self-direction, growth)
**S:** Wanted to move from IT support into data engineering while working full-time and studying for a degree.
**T:** Build real data skills without paid bootcamps.
**A:** Started a structured 62-week plan in Sep 2026 (Python, SQL, Linux, Git, PostgreSQL first; AWS, Airflow, dbt, Spark later), with ~25 h/week, weekly English lessons and tracked weekly targets.
**R:** On schedule. **[update with current week, finished projects and certifications]**
**Use for:** "How do you learn new technologies?", "Why data engineering?", "Where do you see yourself in 5 years?"

## Common Tough Questions

### "Why do you want to leave the registry office?"
> I grew from intern to IT assistant there and learned to own a whole environment. But my goal is data engineering, and the role has no data work. I want a team where I can build pipelines every day.

### "You don't have professional data engineering / cloud experience."
> That's true. What I do have is hands-on PostgreSQL work: I designed schemas, RLS policies and database functions for my own products, and I'm following a structured plan toward AWS and Databricks certifications. I learn fast by building.

### "Where do you see yourself in 5 years?"
> As a solid mid-level data engineer working with cloud pipelines and AI data workflows, ideally on an international team, and helping newer people on the team.

### "What's your biggest weakness?"
> My spoken English is still intermediate. I take several lessons a week and practice technical English daily, and I make up for it with clear written communication.

### "Why this company specifically?"
> Customize per company. Must reference: specific projects, company values, market position, or team structure. Never give a generic answer.

## Questions You Should Ask Interviewers

### About the Role
- "What does a typical week look like in this role?"
- "What would success look like in the first 6 months?"
- "What's the biggest challenge the team is facing right now?"

### About the Team
- "How big is the team, and how do you divide work?"
- "What does the development/project lifecycle look like, from idea to production?"
- "How do you onboard new team members?"

### About Tech & Growth
- "What's your current tech stack for [relevant area]?"
- "Is there room to grow into more architectural or strategic decisions?"
- "How does the team stay current with new tools and methods?"

### About Culture (use these to prevent disappointment)
- "How would you describe the team culture?"
- "What does professional development look like here?"
- "Is there flexibility for remote/hybrid work?"
- "What's the balance between development/new projects and maintenance work?"
- "How would you describe the leadership style in this team?"
- "What do people who thrive here have in common?"

## Phone/Video Interview Tips
- Have STAR examples written out (use this file)
- Keep a glass of water nearby
- Smile when speaking (it changes your tone)
- Ask for clarification if a question is vague
- It's OK to take 5 seconds to think before answering
- End with: "Is there anything else you'd like to know about my background?"

## After the Application (Best Practice)

### Follow-Up Etiquette
- **Don't call to "stand out"** or to learn more about the role post-submission - this risks a negative impression
- If the employer specified a timeline, respect it and wait
- If no timeline was given and significant time has passed (2+ weeks), a brief call to ask about status is acceptable
- If you have genuinely new, relevant information to share, a short follow-up is fine

### Thank-You Notes
- When you receive any update (interview invitation, rejection, or status update), send a brief thank-you message
- Express appreciation for their time and the process
- Keep it short (2-3 sentences)

## Roleplay Guidelines
When the user asks for interview practice:
1. Ask which role/company to simulate
2. Start with easy warm-up questions ("Tell me about yourself")
3. Progress to role-specific technical questions
4. Include 1-2 behavioral questions using the competencies from the job posting
5. End with a tough question or curveball
6. After each answer, give brief feedback: what worked, what to sharpen
7. Suggest which STAR example would work best for each question
