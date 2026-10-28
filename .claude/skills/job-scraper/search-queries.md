# Search Queries for Job Scraper

<!-- Populated by /setup on 2026-10-28 for Kayky Braz. Re-run /setup --section search to change. -->

## Installed portal CLIs (primary for `/scrape`)

`/scrape` discovers every portal skill under `.agents/skills/*/SKILL.md` and runs its CLI first. Shipped country-agnostic CLIs include `linkedin-search` and `freehire-search`; Danish demos and any skill you add with `/add-portal` are included the same way. You do **not** need a matching `site:` line below for those CLIs to run.

The `site:` query templates in this file are the **WebSearch fallback** — for portals without a CLI, company career pages, or when a CLI fails.

**Language scope:** write every query category in every language listed in your CLAUDE.md Languages table (typically 1-2, sometimes more). A posting requiring a language you have *not* declared, as a job condition, is excluded before scoring; a posting requiring a *higher level* than you declared in a language you *do* work in is flagged for your own judgment, not excluded — see `04-job-evaluation.md`'s Language Gate, the single source of truth for this rule. Translate each category's keywords rather than machine-translating word-for-word (e.g. "Frontend Developer" -> "Desarrollador Frontend", not a literal word-for-word translation) if you work in more than one language.

## Search Sites

Primary:
- **linkedin.com/jobs** - main source, via the `linkedin-search` CLI. Filters: Remote + United States first, then Remote worldwide / LATAM, then Brazil (São Paulo)
- **Freehire** - via the `freehire-search` CLI (country-agnostic)
- The four Danish portal skills (Jobindex, Jobbank, Jobdanmark, Jobnet) stay **disabled** (`enabled: false`); the candidate does not target Denmark

Fallback (WebSearch with `site:`), remote-friendly boards that hire from Brazil/LATAM:
- **weworkremotely.com**, **remoteok.com**, **remotive.com** - remote-first boards
- **gupy.io** and **programathor.com.br** - Brazil (Portuguese queries)
- Company career pages for the optional watchlist below

Optional company watchlist (not required, check occasionally): Google, Microsoft, Amazon, Meta, Apple, Netflix, Nubank, Mercado Livre. Entry-level remote roles at big tech are rare; do not let this list crowd out smaller remote-first companies.

## Query Categories

Queries are grouped by priority. Write **each category in every language from your Languages table** (see Language scope above). Combine each query with your location terms (e.g. your city, region, or metro area) where the site supports it.

**Organize by function, not job title.** The same underlying work carries different titles across companies and markets (a "Data Scientist" role at one employer may be posted as "Insights Analyst" or "Data Consultant" at another). Name each priority category after the function it covers, and list several plausible job titles as query variants within that category rather than betting an entire priority tier on one exact title string.

### Priority 1: Data Engineering (entry level)

Main career direction. Titles: Junior Data Engineer, Data Engineer I, Associate Data Engineer, ETL Developer, Data Engineer Intern/Trainee.

```
site:linkedin.com/jobs "junior data engineer" remote
site:linkedin.com/jobs "data engineer" (junior OR entry OR associate) remote LATAM
site:linkedin.com/jobs "ETL developer" junior remote
site:weworkremotely.com "data engineer" junior
site:gupy.io "engenheiro de dados" júnior
site:linkedin.com/jobs "engenheiro de dados" júnior São Paulo
site:linkedin.com/jobs "estágio" "engenharia de dados"
```

### Priority 2: Analytics & BI (SQL, Python)

Stepping-stone roles that build data experience. Titles: Analytics Engineer, Junior Data Analyst, BI Analyst, SQL Analyst.

```
site:linkedin.com/jobs "junior data analyst" SQL Python remote
site:linkedin.com/jobs "analytics engineer" junior remote
site:linkedin.com/jobs "BI analyst" junior remote
site:gupy.io "analista de dados" júnior SQL
site:linkedin.com/jobs "analista de BI" júnior São Paulo
```

### Priority 3: Cybersecurity (entry level)

Requested by the candidate. Titles: Junior Cybersecurity Analyst, SOC Analyst Tier 1, Junior Security Analyst, Information Security Intern.

```
site:linkedin.com/jobs "SOC analyst" (tier 1 OR junior) remote
site:linkedin.com/jobs "junior security analyst" remote
site:gupy.io "analista de segurança da informação" júnior
site:linkedin.com/jobs "analista SOC" júnior São Paulo
```

### Priority 4: IT Support / Systems Administration (plan B, ideally for foreign companies)

Uses current experience directly. Titles: IT Support Specialist, Help Desk Analyst, Junior Systems Administrator, IT Operations Analyst.

```
site:linkedin.com/jobs "IT support specialist" remote LATAM
site:linkedin.com/jobs "junior systems administrator" remote
site:weworkremotely.com "IT support"
site:linkedin.com/jobs "analista de suporte" "inglês" São Paulo
```

Key skill terms to combine with titles: SQL, Python, PostgreSQL, Supabase, ETL.

## Location Filter

Tiers, best first:
- **Ideal:** fully remote for a US company, open to candidates in Brazil/LATAM (contractor or EOR)
- **Good:** fully remote for Canada or Europe, open to Brazil
- **Acceptable:** remote in Brazil, or hybrid in São Paulo (city or nearby: Embu-Guaçu, ABC, Osasco)
- **Borderline:** on-site in São Paulo
- **Too far:** on-site or hybrid outside Greater São Paulo; "remote" roles restricted to US (or other country) residents or work authorization

## Language Filter

Your working languages and levels are in CLAUDE.md's Languages table. When filtering scraped results, apply `04-job-evaluation.md`'s Language Gate: a posting requiring a language you haven't declared at all is excluded; a posting requiring a higher level than you declared in a language you do work in is not excluded, flag it clearly instead (see `job-scraper/SKILL.md`'s Step 3 "Quick Fit Assessment" for how the flag surfaces in `/scrape` output). Postings simply *written* in a language you don't work in, that don't require it on the job, are fine.

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape [focus_area]" -> relevant category queries + custom focus-specific queries
