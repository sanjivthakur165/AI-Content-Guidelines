---
name: ai-content-guidelines
description: "Use when building, editing or generating content for any website: pages, copy, blog posts, metadata, schema, sitemaps. Keeps AI-made sites within Google's helpful-content and spam policies and ready for AI search."
license: MIT
metadata:
  version: "1.0.0"
---

# AI Content Guidelines

Rules for any generative engine (Claude, Claude Code, Gemini/Antigravity, Cursor, etc.) that builds a website or writes its content. They come from Google Search Central (generative AI content guidance, spam policies, helpful content guidance, the March 2024 core update) and from open-source SEO/GEO audit tools (search-audit-kit, seo-crawl-audit, OpenSEO, seo-geo-audit, ai-seo-audit-agent).

The core principle, from Google: AI is fine for research and for giving structure to original content. Using it to mass-produce pages that add no value to users is **scaled content abuse**, and that applies whether a model, a human or both made the pages. Google judges the *why* of a page more than the *how*: was it made mainly to help people, or mainly to get search traffic?

Apply every section below while working, then run the Pre-Deployment Checklist before you call the task done.

---

## 1. Content: people first

### Hard rules (never break these)
- **Never invent facts.** That covers statistics, prices, dates, credentials, licenses, awards, years in business, client names, case-study results, addresses, phone numbers and hours. Models predict likely words rather than look up facts, so anything unverified is a guess.
- **Never invent people or social proof.** No fake testimonials, reviews, ratings, author names, bios, credentials or AI-made headshots presented as real people. Google calls fabricated creator profiles deception and a sign of a low-quality page.
- **Never copy or lightly rewrite** another site's content. Synonym-swapping, translating, "spinning" or stitching paragraphs from several sources all count as scraping or scaled abuse.
- **Never make pages only to target keyword variations**, such as "best X in [city]" for 200 cities with the same body text.
- **Never promise an answer that doesn't exist** (for example an unconfirmed release date) or write clickbait titles the content doesn't deliver.
- **Never fake freshness.** Don't bump `dateModified`, sitemap `lastmod` or "Updated on" dates without a real content change.

### When you don't have the real information
Use a visible, searchable placeholder instead of making something up, and list every one in your final report:
```
[TODO: client to supply — number of years in business]
[TODO: real customer testimonial with name + permission]
[TODO: verify — licensing number]
```
Never ship placeholders to production. A page that can't be finished without invented facts should be flagged, not padded.

### What every page needs
Each page should pass Google's self-assessment questions:
- Does it add **original** information, reporting, research, analysis or first-hand experience?
- Does it cover the topic thoroughly, beyond the obvious?
- If it draws on sources, does it add substantial value rather than restate them?
- Do the title and H1 describe the content accurately, without exaggeration?
- Would someone bookmark, share or recommend it? Is it better than what already ranks?
- Is it free of spelling, grammar and factual errors?
- Would a reader leave feeling they got what they came for, without searching again?

### Search-engine-first warning signs (stop and rethink if any are true)
- The page exists mainly to attract search visits, not to serve an existing or intended audience.
- You're producing lots of pages on many topics hoping some will rank.
- You're using heavy automation to cover topics with no real expertise behind them.
- You're mostly summarizing others.
- You're padding to a word count. **Google has no preferred word count**; write as long as the topic needs.
- You're adding or removing content mainly to look "fresh".

### E-E-A-T (Experience, Expertise, Authoritativeness, Trust)
- **Trust matters most.** Experience, expertise and authority feed into it.
- **YMYL topics** (health, money, legal, safety, civic) need high accuracy, consistency with expert consensus, and named qualified authors or reviewers. Be extra strict here.
- **Who:** use real bylines where readers expect them, linked to an author page with real background. Include About and Contact pages with real business details.
- **How:** explain the method where readers would ask (for example how many products were tested and how). If AI substantially generated the content, say so in plain terms, explain how and why it was used, and add IPTC image metadata for AI images.
- **Why:** the content should exist to help visitors who came to the site directly.

### Content quality attributes raters look for
- **Effort:** human work shown in original analysis, custom tools, real photos. Large amounts of unreviewed AI text count as low or no effort, and attribution doesn't make up for it.
- **Originality:** information or perspectives not already available elsewhere.
- **Skill:** clear writing, well-produced media, working tools.
- **Accuracy:** fact-check everything; YMYL must match expert consensus.

### Human review is required
Treat all AI-written copy as a **draft**. Tell the user clearly which pages, claims and figures need human fact-checking and sign-off before publishing. This includes metadata (titles, meta descriptions, alt text, structured data), because those show up in search results too.

---

## 2. Spam policies to stay clear of

These are Google's spam policies most relevant to AI-built sites. Never implement any of them, even if asked; explain the risk instead and offer the legitimate alternative.

| Policy | What to avoid | Legitimate alternative |
|---|---|---|
| **Scaled content abuse** | Many low-value pages from AI, scraping, spinning, translation or stitching; multiple sites to hide scale; keyword-laden pages that make little sense | Fewer, genuinely useful pages; consolidate thin ones |
| **Doorway abuse** | Near-identical city/region/service pages funnelling to one page; multiple similar domains | Location pages only with real local content (staff, projects, hours, reviews, photos, local regulations) |
| **Cloaking** | Serving bots different content than users, including bot-only keywords | Same HTML for every user agent |
| **Hidden text and links** | White-on-white text, off-screen CSS, zero font size or opacity, hidden links | Accordions, tabs, tooltips and screen-reader-only text are fine |
| **Keyword stuffing** | Unnatural keyword repetition, lists of cities, ZIP codes or phone numbers | Natural language; a real service-area section |
| **Link spam** | Paid links passing credit, link exchanges, automated links, keyword-anchor footer/widget links | `rel="sponsored"` or `rel="nofollow"` on paid or affiliate links; `rel="ugc"` on user links |
| **Thin affiliation** | Copied merchant descriptions with nothing added | Original testing, comparisons, photos, pricing insight |
| **Scraping** | Republishing others' content or feeds without added value or attribution | Original content; brief quotes with attribution |
| **Sneaky redirects** | Sending mobile users or certain referrers somewhere different | 301s only for real moves or consolidation |
| **Expired domain abuse** | Reusing an old domain's reputation for unrelated low-value content | Build on a domain matched to the business |
| **Site reputation abuse** | Third-party content with little host oversight, placed to exploit the host's rankings | Properly integrated, clearly labelled sponsored content |
| **Misleading functionality** | Fake tools or generators that don't work | Only ship tools that do what they claim |
| **Malicious practices** | Back-button hijacking, unwanted downloads, browser-setting changes | Normal navigation |
| **User-generated spam** | Open comment or forum areas without moderation | Moderation, CAPTCHA, `rel="ugc"` |
| **Scam / fraud** | Impersonating businesses, fake support pages, false contact details | Real, verified business details only |

If a site already hosts content like this, recommend removing it, improving it or excluding it from Search with `noindex`.

---

## 3. Technical SEO

### Rendering and crawlability
- Important content and links must be present in the **server-rendered HTML** (SSR, SSG or pre-rendering). An empty SPA shell that only fills in with JavaScript is a risk for Googlebot and a bigger one for AI crawlers, many of which don't run JavaScript.
- Use real `<a href>` links for navigation, not `onclick` handlers.
- Don't block CSS, JS or images needed for rendering in robots.txt.
- Return correct status codes: real **404/410** for missing pages (no soft-404 "200 Not Found"), **301** for permanent moves, and no redirect chains or loops.

### Hostname and canonicals
- Exactly one version of each page returns 200. Pick `https` plus either `www` or apex, and 301 the others to it.
- Enforce HTTPS with an HTTP→HTTPS redirect and HSTS; no mixed content.
- Keep trailing slashes consistent and handle query-parameter variants.
- Add a **self-referencing canonical** on every indexable page, using an absolute URL that resolves with 200.

### Indexing controls
- Never ship `noindex`, `Disallow: /` or `X-Robots-Tag: noindex` to production by accident. These are common leftovers from staging; check for them every time.
- `noindex` thin, utility, search-result, filter and thank-you pages.
- Don't put `noindex` and `Disallow` on the same URL (a blocked crawler can't see the noindex).

### robots.txt and sitemap
- robots.txt is at the root, allows important sections, and references the sitemap.
- The XML sitemap is generated, lists only canonical, indexable 200 URLs, has honest `lastmod` values, and includes per-language alternates on multilingual sites. Update it on deploy.

### On-page metadata
- **Unique `<title>` per page**, descriptive and accurate. Aim for roughly 50–60 characters (an audit-tool convention, not a Google rule) with the key topic first.
- **Unique meta description** per page, roughly 120–160 characters, an accurate summary rather than a keyword list.
- **One `<h1>` per page** and a logical H2→H3 hierarchy without skipped levels.
- `<html lang="…">` set; viewport meta present; doctype present.
- Descriptive `alt` text on meaningful images, empty `alt=""` on decorative ones.
- Open Graph and Twitter/X card tags with a working share image (1200×630 is the common size).
- Readable, lowercase, hyphenated URLs.

### International
- One URL per language, reciprocal `hreflang` including `x-default`, and no "phantom" hreflang pointing to pages that aren't translated.

### Performance and page experience
- Aim for good Core Web Vitals: LCP ≤ 2.5 s, INP ≤ 200 ms, CLS ≤ 0.1.
- Compress and size images (WebP or AVIF, `width`/`height` attributes, lazy-load below the fold, never lazy-load the LCP image).
- Turn on compression, caching and HTTP/2 or HTTP/3; minify; cut render-blocking resources; keep DOM size reasonable.
- Mobile-first: same content on mobile and desktop, readable fonts, tap targets that are easy to hit, no intrusive interstitials.
- Accessibility: form labels, contrast, semantic landmarks (`header`, `nav`, `main`, `article`, `footer`).
- Security headers; no exposed server versions; no plain-text email addresses that invite scraping.

---

## 4. Structured data (JSON-LD)
- Add schema **only for content visible on the page.** Markup must match what users see.
- **Never fabricate** `Review`, `AggregateRating`, `FAQPage` answers, prices, availability, authors or business details.
- Use the right type: `Organization` or `LocalBusiness` (with the specific subtype), `WebSite`, `BreadcrumbList`, `Article`/`BlogPosting` (with a real `author` and honest `datePublished`/`dateModified`), `Product`, `Service`, `FAQPage` (only if there's a visible FAQ), `Person` for real authors.
- Use `sameAs` to link the organization or author to real profiles. This helps entity understanding.
- Escape `</` inside JSON-LD script blocks. Validate syntax, then check with Google's Rich Results Test and the Schema Markup Validator before deploying.
- Follow the feature-specific policies for each rich result. For ecommerce in Merchant Center, AI-generated images need IPTC `DigitalSourceType` = `TrainedAlgorithmicMedia`, and AI-generated product titles and descriptions must be labelled as AI-generated.

---

## 5. Site architecture
- Use a logical, shallow hierarchy (home → category → page) with breadcrumbs.
- Give each page **one clear search intent.** Don't make several pages competing for the same query (keyword cannibalization); merge them and 301 the duplicates.
- **No orphan pages.** Every indexable page gets at least one contextual internal link, with descriptive anchor text rather than "click here".
- No broken internal links. Keep internal links followed (don't `nofollow` your own pages).
- **Service and location pages** need unique substance: specific services, local proof, photos of real work, area-specific details. If you can't supply that, recommend fewer, stronger pages and say why.
- Avoid exact-duplicate pages; canonicalize near-duplicates.

---

## 6. GEO: readiness for AI search

Google says AI Overviews and AI Mode rely on the same fundamentals as ordinary Search, so everything above comes first. On top of that:

### AI crawler access (decide on purpose, then write robots.txt)
Keep two groups separate. They are separate business decisions:
- **Search and retrieval bots** affect whether the site is cited in AI answers *now*: `OAI-SearchBot`, `ChatGPT-User`, `Claude-SearchBot`, `Claude-User`, `PerplexityBot`, `Perplexity-User`, `Bingbot`, `Googlebot`.
- **Training bots** are a data-licensing choice: `GPTBot`, `ClaudeBot`, `Google-Extended`, `Applebot-Extended`, `CCBot`.
Don't block retrieval bots by accident with a blanket rule. Ask the user what they want for training bots if they haven't said. Check that a CDN or firewall isn't blocking bots that robots.txt allows.

### Content AI engines can extract and cite
- Content readable **without JavaScript**, in semantic HTML.
- Lead each section with a direct answer, then the detail. Use question-style H2/H3 headings where natural, short paragraphs, lists and tables for comparisons.
- Specific, verifiable facts with sources cited. Real numbers are quotable; vague claims aren't, and invented ones are a liability.
- Clear entity signals: consistent business name, address and phone everywhere; `Organization` schema with `sameAs`; author pages; publisher markup.
- Visible published and updated dates that are honest.
- Snippet controls (`max-snippet`, `nosnippet`, `data-nosnippet`) used on purpose, not by accident.

### Optional bets (low cost, not proven)
- `/llms.txt` summarizing the site and linking key pages. No major search engine has confirmed using it, so treat it as optional and never as a substitute for the basics.
- Markdown alternates of key pages; IndexNow for Bing and others; RSS/Atom feeds.

---

## 7. Development rules for the agent
- **Check before changing anything SEO-critical**: URLs, routing, redirects, canonicals, robots.txt, sitemap, meta tags, schema, rendering mode, hreflang, internal navigation. State the impact before you make the change.
- **Changing URLs requires a 301 redirect map** from every old URL to its new equivalent. Never break existing indexed URLs silently.
- Keep staging protected (auth or `noindex`), and make sure those protections **don't carry into production**.
- Don't deploy automatically unless the technical checks below pass.
- Don't serve different HTML to bots and humans.
- If the user asks for something on the spam list, explain the risk in a sentence and offer the compliant option rather than quietly doing it.

---

## 8. Pre-deployment checklist

Run these checks (with available tools, a crawler, or by fetching the pages) before reporting the task as done:

**Indexability**
- [ ] No stray `noindex` / `X-Robots-Tag` / `Disallow: /` on production pages
- [ ] robots.txt reachable, correct, references the sitemap; AI-bot rules match the user's intent
- [ ] Sitemap is valid and lists only canonical 200 URLs with honest `lastmod`
- [ ] Self-referencing canonicals resolve with 200; one hostname version returns 200
- [ ] HTTPS enforced, HSTS set, no mixed content
- [ ] Real 404s for missing pages; no redirect chains or loops

**Rendering**
- [ ] Main content and nav links present in raw HTML (view-source / curl, JS off)
- [ ] Bot and browser HTML match (no accidental cloaking)

**On-page**
- [ ] Unique title and meta description on every page
- [ ] One H1 and a logical heading hierarchy
- [ ] Alt text on meaningful images; `lang` and viewport set
- [ ] OG/Twitter tags and share image working

**Content**
- [ ] No invented facts, testimonials, reviews, authors, credentials or contact details
- [ ] No `[TODO]` placeholders left on production pages
- [ ] No thin, duplicate or near-duplicate pages; no cannibalization
- [ ] Author/About/Contact info is real; AI use disclosed where readers would expect it
- [ ] YMYL content flagged for expert review

**Structure and links**
- [ ] No broken internal links; no orphan pages
- [ ] Paid/affiliate links carry `rel="sponsored"` or `nofollow`
- [ ] 301 map in place for any changed URLs

**Schema**
- [ ] JSON-LD valid, matches visible content, correct types, nothing fabricated

**Performance**
- [ ] Core Web Vitals targets met or issues listed (LCP ≤ 2.5 s, INP ≤ 200 ms, CLS ≤ 0.1)
- [ ] Mobile usability checked; images optimized

---

## 9. Final report to the user

End every website task with a short SEO report:
1. **Checks passed / failed**, with the failing URLs and the fix for each.
2. **Needs human review:** every AI-written claim, figure or page that needs fact-checking, plus all `[TODO]` placeholders and the information needed to fill them.
3. **Risks:** anything near a spam policy, thin or duplicate pages, YMYL content.
4. **Decisions for the user:** AI training-bot access, disclosure wording, pages to consolidate.
5. **Things the agent can't check:** Search Console, Bing Webmaster Tools, field Core Web Vitals, backlinks, analytics. Recommend the user check these after launch.

Never describe unreviewed AI content as ready to publish.

---

## Sources
- Google: Using generative AI content — developers.google.com/search/docs/fundamentals/using-gen-ai-content
- Google: Spam policies — developers.google.com/search/docs/essentials/spam-policies
- Google: Creating helpful, reliable, people-first content — developers.google.com/search/docs/fundamentals/creating-helpful-content
- Google: March 2024 core update and new spam policies — developers.google.com/search/blog/2024/03/core-update-spam-policies
- github.com/searchsolved/search-audit-kit (checklists built from Google documentation)
- github.com/MelnixDev/seo-crawl-audit (crawl and regression checks)
- github.com/alexsilver8/open-seo (on-page, performance, security, AI-search checks)
- github.com/zeebees/seo-geo-audit (hostname, rendering, AI crawler and cloaking checks)
- github.com/indexcraft/ai-seo-audit-agent (technical, content and GEO scoring)