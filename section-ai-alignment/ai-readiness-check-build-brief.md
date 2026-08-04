# Build brief: The AI Readiness Check
**For a fresh Claude Code / Cursor session on Jeanna's laptop. Assume no prior context. 22 July 2026.**

## What you are building, in one paragraph
A free, self-serve online quiz at vooee.au that tells an Australian business leader how ready they are to lead AI in their business, and, the part nobody else has, how big the gap probably is between them and their fellow leaders. Instant personalised report with an archetype, email-gated, feeding the mailing list. It is the self-serve little sibling of a facilitated half-day product called the Alignment Room, and its whole job is to build an audience and walk leadership teams toward that room. First real users: the leadership team at Foundation Education Group / AIPT, as invited guinea pigs.

## Context you need (none of which this session has seen)

### The business
vooee (always lowercase) is Jeanna Manifold's solo AI advisory for Australian SMBs, at vooee.au. Site repo: **vooee-site2** (local on this machine; Netlify auto-deploys on push to main). The advisory ladder: $1,900 AI Working Session (being renamed the Alignment Room) → $15,000 90-Day Engagement → $8,500/month fractional seats. Also a six-week AI Enablement Sprint for teams, and free funnel tools that prove the patterns this build reuses: **AI Ikigai** (quiz → personalised report → email) and the **Website Scorecard** (free check → results email → paid tiers).

### The Alignment Room (what this quiz is the front door to)
A half-day facilitated session with a leadership team. Leaders silently answer the same questions on their own devices (fun anonymous animal nicknames), answers are compared live, a "tension report" surfaces where they align and where they collide, they debate, then AI drafts their governance statement from their own words, and the room edits it aloud. Signature insight, used everywhere: **ask five leaders why the business wants AI and you'll often hear five different answers; that gap is why AI plans stall.** A working single-file prototype exists: `alignment-room-app.html` (in the same folder as this brief). Open it in a browser, click "Facilitator view", press "Load demo leadership team", then "Generate the tension report". That is the product family's soul; the quiz is its self-serve, single-player version.

### The mechanic that makes this quiz different
**The perception gap.** Each person answers twice: how AI sits with YOU, and how you believe your FELLOW LEADERS would answer. The distance between those two is the product. A reference PDF in `downloads/astrology-blueprint-funnel-reference.pdf` shows the funnel pattern being borrowed (an astrology "business blueprint": identity-first personalisation, instant artefact, low-ticket ascension). We borrow its mechanics, never its content. Our identity ingredient is the perception gap plus an archetype, not a star sign. And the "why not just ask ChatGPT?" objection has a built-in answer: ChatGPT cannot tell you what your co-leaders actually think.

### Search context (SEMrush, 22 July 2026)
No SEO goldmine exists; this grows via LinkedIn and the invite loop. But the landing page should target "AI readiness assessment / check" language on-page: "ai readiness assessment" is AU 90/mo KD38, US 880/mo KD33; "ai governance assessment" US 1,000/mo KD20. Cheap to own over time, treated as a bonus channel.

## Naming
Working title: **The AI Readiness Check**. Check these before shipping: it must not collide with the existing "Website Scorecard" free check (different product, similar word shapes; the Scorecard checks your website, this checks your leadership); "readiness" language is the SEO play; Jeanna signs off the final name and the archetype names before launch.

## The product spec

### Tiers (build tier 0 now; design so tier 1 bolts on)
- **Tier 0, free: the individual check.** ~12 questions, under 5 minutes, instant report, email gate before the full report. This build.
- **Tier 1, paid later: the Leadership Alignment Snapshot** ($99-$149 + GST via Stripe): when 3+ leaders from one business complete the check under a shared invite code, an aggregated report shows real gaps vs perceived gaps. Not built now, but the data model must support it from day one (invite/org codes on every response).
- **Tier 2: the Alignment Room** ($1,900). Every report ends by pointing here.
- **Pilot mode for AIPT:** an unlisted URL parameter (e.g. `?pilot=feg`) that tags responses as pilot, skips nothing else, and adds one extra final question: "You're one of the first people to use this. What felt clunky, and what would make it better?" Their team completions under the pilot code effectively give them a free tier-1 snapshot, which Jeanna will walk through with them; that is the guinea-pig deal.

### The question flow (one question per screen, Expert OS style: progress indicator, back button, big serif question, no wrong answers)

**Part A: you (7 questions)**
1. What's your role? (chips: Owner or CEO / Sales / Marketing / Operations / Finance / People / Technology / Other)
2. One word for how AI makes you feel right now. (single word; playful hint: first word that comes to mind)
3. How confident do you feel leading AI change in your business? (slider 1-10)
4. What would you love AI to take off your plate? (short free text)
5. What worries you most about AI in your business? (chips + other: Client or customer data going somewhere it shouldn't / Wrong answers reaching customers / My team quietly using it with no rules / Spending money and seeing no return / Our brand starting to sound like a robot / Falling behind competitors)
6. Does your business have AI ground rules today? (chips: Yes, written down / Sort of, informally / No / I honestly don't know)
7. For the next ninety days, is AI here mainly to save time or mainly to grow the business? (chips: Save time / Grow the business / Genuinely torn)

**Part B: your read of the others (5 questions)**
8. How many people make the big calls in your business? (chips: Just me / 2-3 / 4-6 / 7+) — "Just me" answers skip 9-12 and get a solo variant of the report (their gap is between intention and action, not between leaders).
9. If each of them answered "why do we want AI?", how many different answers would you hear? (chips: One answer, we're aligned / Two or three versions / A different answer from everyone / I genuinely don't know)
10. Who's most enthusiastic about AI, and who's most cautious? (two role chips; same chip set as Q1, plus "Honestly, no idea")
11. Predict it: what would your leadership team's average confidence score be? (slider 1-10; their own score shown alongside for the deliberate contrast)
12. Would your leaders agree on which decisions should never be made by AI? (chips: Yes, we've discussed it / Probably, but we've never said it out loud / No / We've never talked about any of this)

**Then:** first name + email to get the full report ("Your report is ready. Where should we send your copy?" — report renders on screen immediately after submit; email is the gate, the emailed version is the same report as a link or PDF). Privacy line per site standard; no tracking cookies; details used to send the report and stored securely.

### Scoring and archetypes
Two scores, computed client-side or in the function:
- **Readiness score** (0-100): weighted from Q3 confidence, Q6 ground rules, Q5 worry type, Q7 decisiveness. Bands: Exploring (0-39) / Moving (40-69) / Leading (70-100). Exact weights are the builder's judgement; keep them in one commented function so Jeanna can tune.
- **Predicted gap score** (0-100): from Q9 (biggest driver), Q11 distance between own and predicted confidence, Q12, and Q10 certainty. Bands: Tight / Drifting / Five different answers.

**Archetypes (working set, Jeanna to sign off; assign from confidence x worry x priority):**
- **The Accelerator** — high confidence, grow-the-business. Strength: momentum. Blind spot: the team is further behind than you think.
- **The Guardian** — data or team worries lead, cautious confidence. Strength: you see the risks that are real. Blind spot: waiting for perfect rules while shadow AI spreads.
- **The Pragmatist** — save-time priority, ROI worry. Strength: you'll fund what works. Blind spot: efficiency alone never builds capability.
- **The Translator** — mid confidence, team-focused worries. Strength: you bring people with you. Blind spot: consensus can become a place to hide.
- **The Explorer** — genuinely torn, curious, low-mid confidence. Strength: honest about not knowing. Blind spot: exploration without a deadline is drift.
Every archetype description must read as flattering-but-true, in vooee's voice, and end with one practical next step. This is the shareable identity layer; it earns the giggle and the screenshot.

### The report (instant, on-screen, emailed)
Order matters; it is a rapport arc, not a data dump:
1. **Your archetype** (name, two-sentence description, strength, blind spot) — the identity moment.
2. **Your readiness** (score, band, one sentence on what the band means) with one cited national context stat (EY Australia 2025: 2 in 3 AU small businesses use AI, 35% of workers formally trained; Section 2026: 52% of employees anxious about AI, roughly 3% truly proficient. Cite by name, never invent numbers).
3. **The gap read** — the star section. "You predict [two or three different answers] to 'why AI' and a team confidence of [4] against your [8]. That gap is normal, and it is the single biggest reason AI plans stall." One insight sentence per Part B answer, written from templates.
4. **One thing to do this week** (archetype-specific, concrete, no product pitch).
5. **The invite loop:** "You think your leadership team holds [three different answers]. Find out what they actually think: invite them." Button generates a share link carrying the org/invite code (`?team=CODE`), pre-written email/message text included.
6. **The bridge, soft:** "When three or more of you have answered, we can show you the real gaps next to your predictions. And when you want the gaps resolved rather than admired, that is a half day in the Alignment Room." Link to /advisory. The free report diagnoses; it never resolves. Resolution is the paid room; protect that line absolutely.

**Report generation:** v1 ships with template-composed copy (string templates keyed by archetype, band, and answers; fully deterministic, no API dependency, works offline in the room). v1.5 adds a Claude API call to write section 3's gap read from the actual free-text answers, via a Netlify function using the current Sonnet model (`claude-sonnet-5`), with the template as automatic fallback on any error or >4s latency. Never block the report on the API.

## Design system (exact tokens; the deck and prototype in this folder use them)
- Fonts: Fraunces (serif display, weight 600, italic accents), Space Grotesk (body), Bebas Neue (the rotated lowercase "vooee" wordmark only). Google Fonts.
- Colours: background #faf7f1 (cream), linen #ede7dc, card #ffffff, foreground #1c2926, muted #58625f, rose accent #d9876d, forest #2D5F4F, garden #4f6e5f, border #ddd5c7.
- Grammar: rose uppercase eyebrow labels with a 2.5rem rule line, big Fraunces headlines with an italic garden-coloured accent word, generous whitespace, soft shadows, pill buttons (forest fill, cream text), forest cards for the big emotional moments. Mobile-first: this will be answered on phones.
- Reference files, same folder as this brief: `alignment-room-deck.html` (the session deck; canonical look), `alignment-room-app.html` (the prototype; canonical question interactions).

## Voice (non-negotiable; every string in the build follows this)
Clear. Calm. Human. Useful. Write like Jeanna: conversational, direct, warm, no jargon. **Banned:** em-dashes (use commas, full stops, colons, brackets); the words unlock, leverage, transform, disrupt, revolutionise, seamless, frictionless, turnkey, AI-powered, cutting-edge, next-generation, journey, ecosystem, holistic; antithesis constructions ("not X, but Y", "it's not about X, it's about Y"); "work out what matters" (always "figure out what matters"). Brand name always lowercase vooee. "I" for Jeanna's identity statements, "we" for collaborative process. Reports are honest, never alarmist: "that gap is normal" beats "your business is at risk".

## Tech implementation
- **Where:** vooee-site2 repo. Page at `/ai-readiness-check/` (confirm URL with Jeanna; add to sitemap.xml and llms.txt like every page). Static HTML/CSS/JS page consistent with the site's existing single-file style; no framework unless the site already has one.
- **Submission:** Netlify function (copy the pattern from `/.netlify/functions/submit-enquiry`, which posts to Airtable). New Airtable table, suggested fields: timestamp, name, email, role, feel_word, confidence, delegate_text, worry, ground_rules, priority, team_size, predicted_answers, enthusiast_role, cautious_role, predicted_confidence, human_decisions_agreement, readiness_score, gap_score, archetype, team_code, pilot_flag, feedback_text, source.
- **Email:** Brevo contact creation with attributes (archetype, scores, team_code), same pattern as the Ikigai/Scorecard funnels; the report email template comes after the build, but the function should fire the contact creation from day one. Which Brevo list: ask Jeanna (the Practical AI Brief list exists; a dedicated list may be cleaner).
- **Team codes:** every completion gets or joins a `team_code` (from `?team=` param, else generated short code shown in the invite section). This is the entire tier-1 foundation; do not skip it.
- **Privacy posture (site rules):** no tracking cookies, no analytics scripts. The site footer privacy line applies. Add the standard disclaimer: general information and an educational starting point, not legal or professional advice.
- **The Vee widget:** every public vooee page carries the ElevenLabs voice widget (three required blocks before `</body>`; copy from index.html verbatim). Include it.
- **Claude API (v1.5 only):** key handling per the site's existing Netlify env var pattern; never in client code.

## AIPT pilot (the first real users)
Jordan Albury's leadership team at Foundation Education Group / AIPT (education provider: Foundation Education + AIPT brands). They saw a Claude demo on 21 July and are warm. Jeanna's play: "would you be my guinea pigs?" before/alongside the formal training proposal. Build requirements: the `?pilot=feg` mode above, plus nothing else special. Success looks like: 3-5 of their leaders complete it, Jeanna walks them through their team snapshot by hand (facilitator-view style), collects the feedback answers, and the experience helps close the AI Enablement Sprint proposal already drafted.

## Measures (log from day one, report weekly)
Completions, completion rate by question (find the drop-off), emails captured, invites generated, invited completions (the loop metric), team codes reaching 3+, pilot feedback texts, clicks through to /advisory.

## Build order
1. Static quiz flow with all 12 questions + solo branch, mobile-first, in the design system.
2. Scoring + archetypes + template report, rendered on screen.
3. Netlify function: Airtable write + Brevo contact + team_code handling + pilot flag.
4. Email gate + report email (simple version: link back to the rendered report).
5. Invite loop (share link + prewritten invite text).
6. Pilot polish + the feedback question, then hand the pilot URL to Jeanna for AIPT.
7. Later: Claude-written gap reads (v1.5), Stripe + aggregated Snapshot (tier 1), archetype share cards.

## What NOT to do
- No "constitution" naming anywhere client-facing (IP inspiration check still open on that word's source).
- The free report never resolves tensions, only names them; resolution belongs to the paid room.
- No claims of track record ("most leadership teams we work with..."): zero paid sessions have run. Cite EY, Section and McKinsey for numbers; own claims stay hypothesis-flavoured ("often", "tends to").
- Don't invent a new visual language; this is a vooee page, same family as Ikigai and the Scorecard.
- Don't launch publicly before the AIPT pilot round and Jeanna's word-by-word copy pass.
