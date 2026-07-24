# The Alignment Room: the leadership workbook as an app
**Concept and build brief · Draft v1 · 22 July 2026 · Working title only**

The 90-Day Workbook (doc 06) stays the leave-behind. This is how its first section gets *filled in*: each leader answers alone through a link before the session, the system surfaces where they agree and where they collide, and the working session uses AI live in the room to turn their combined answers into the governance policy. Then each leader's boundaries become a persona the team can consult before work ever reaches the leadership table.

## What we're borrowing from Expert OS (mechanics, not content)
From the summit app: the guided step sequence with progress ("Step 4 of 10"), an agent that interviews rather than presents a form, remembered context carried between steps ("I can see from your profile..."), pick-an-option-or-write-your-own at every question, the explicit "lock it in" moment, and a polished document handed back at the end. One more pattern worth stealing: the interactive calculator (sliders recalculating live) as a moment of delight mid-sequence. The content is his IP; the interaction pattern is just good product design.

## The flow (everything happens in the room)
Jeanna's call, 22 July: no pre-work. Pre-work gets filled out badly or not at all, and answers given before anyone has explained the why are shallow answers. The capture happens live, after the framing. This also fixes a facilitation problem: silent individual capture in the room, before any group discussion of the specifics, is the classic guard against anchoring; the loudest voice can't set everyone's answers if everyone has already answered.

### 1. First: the why, and the cost of not doing it (about 30 minutes)
Jeanna presents the NIST framing in plain English (the quick-start's four questions: who decides, where do we need a human gate, how do we know it works, what's the plan for a bad day) and the cost of skipping it: the incident stories, the Notifiable Data Breaches deadlines, the free-chatbot discovery most businesses get to make exactly once. The Section stats earn their place here (52% anxious, 3% proficient). Nobody answers anything yet; this is why the answers will be honest.

### 2. Then: silent capture, live in the room (15 to 20 minutes)
QR code on the screen; each leader opens their personal link on their own device and answers alone, in silence, coffee in hand:
- The honest baseline (excites, worries, exposure, confidence 1 to 10 and why)
- Their six-area readiness scores, in pencil
- Their one-paragraph answer to "why does this business want AI at all?"
- Their cut vs create instinct
- Their personal list of decisions that must stay human

The agent probes one level deeper the way Expert OS does ("that's the category; give me the moment where it actually hurts"). Answers go to Jeanna, not to the group.

**The word cloud, played carefully.** A live word cloud building on the projector is the right theatre, in two acts:
- **Act one, during capture, warm-up only.** The capture opens with one designed one-word question ("one word for how AI makes you feel right now") and the cloud grows live on screen as answers land. Anonymous, energising, and it proves to the room that the link works. Then the screen goes dark for the real questions; a live cloud during those would put words in people's mouths, which is exactly what silent capture exists to prevent.
- **Act two, the reveal.** When the break ends, the full clouds animate in as the opening of the tension report: the worries cloud, the excites cloud, the "stays human" cloud. Same theatre, zero anchoring, and the contrast lands harder because the room hasn't seen the words accumulating.

### 3. The break that does the work (10 minutes)
While the room refills coffee, the tension report generates. This is the reveal moment, and it has to be fast, which sets the engineering bar: the report is automatic, not something Jeanna assembles. It shows:
- **Alignments:** where the team already agrees (name them fast, momentum matters)
- **Tensions:** confidence spread, conflicting AI positions, one leader's "must stay human" being another's "automate this first", readiness scores that disagree by 4+ points on the same area
- **The five-paragraphs problem, made visible:** their "why AI" paragraphs side by side. The workbook says "if five leaders would write five different paragraphs, that is the first thing the ninety days fixes"; this shows them the five paragraphs, twenty minutes after they wrote them.
Jeanna sees it first and decides what the group sees, and what gets raised without attribution.

### 4. Then: drafting the ground rules live
The discussion opens on the alignment map instead of a blank page. Then, projected live, AI drafts from their combined answers: the shared AI position (five paragraphs to one, negotiated aloud), the "decisions that stay human" list (union of lists, argued down to the absolute few), the policy template's brackets pre-filled from their answers and edited in the room. They watch their own words become their governance policy within the same half-day they wrote them. That is the "he created an app for us" moment from the summit, and it is also the product demo for everything else vooee sells.

### 5. Later, in the 1:1s: the persona layer (the part with legs)
The full boundaries interview is too rich to rush in a group session, and it deserves the same treatment as the baseline: facilitated, not homework. It runs in each leader's 1:1 slot during the 90 days (or a scheduled 30-minute call per leader), producing a personal charter: what they value, what they veto, what evidence convinces them, what they never want to see in work that reaches them, how they weigh risk against speed. Each charter becomes a **persona the team can consult**: a Claude Project per leader ("Ask the CFO-lens"), or one project holding all of them.
- A team member sense-checks work before it goes up: "score this proposal the way our COO would; what would she push back on?"
- The personas are sanctioned and visible, built from what each leader actually said, not the team's guesses. Leaders review and approve their own persona before it goes live.
- This inverts the vooee AI Boardroom skill (synthetic thought leaders): here the boardroom is the client's own C-suite.
- It keeps working after the engagement ends, which makes it the natural bridge to the fractional seat: someone has to keep the personas current as the leaders' thinking evolves.

**On Allie Miller's vault prompts (constitution etc.):** use them as inspiration for the boundaries interview, the way the concept deserves, but the prompts themselves are her paid membership IP. Write vooee's own question set from scratch (the charter fields above are that start), credit the inspiration privately, never redistribute her text. If Jeanna's membership includes commercial licensing, check the terms before leaning closer.

## Build path (all existing vooee patterns)

**MVP (a working session away):** no app at all. A structured intake (Airtable form or Tally, opened from a QR code in the room) plus a Claude Project that ingests the responses and produces the tension report and the live drafting. The warm-up word cloud can be Mentimeter off the shelf at MVP; the built version is a small self-contained display page polling the responses (the Ikigai/Netlify stack again) so it carries vooee branding and feeds the same dataset as everything else. The live flow sets one hard requirement even at MVP: the report must be a one-click generate that lands inside the coffee break, rehearsed end to end before a real client. Two boring risks to plan for because everything now happens in the room: venue wifi (phone hotspot as backup) and a leader without a device (two spare iPads or, worst case, paper cards Jeanna types in during the break).

**v1 (the product):** the Ikigai pattern grown up. Netlify page per engagement (gated link), questions served one at a time with progress, answers to Airtable via function, Claude API for the deeper-probe follow-ups and the tension report. Reuses: Ikigai's question-to-report flow, Scorecard's fulfilment runbook, the enquiry form's Netlify-to-Airtable plumbing.

**v2 (the summit feel):** fully conversational agent (type or talk; the Vee/ElevenLabs stack makes voice intake possible), remembered context across steps, the readiness sliders as a live-recalculating screen, per-client branding. Only after v1 has run with two or three real leadership teams.

**Privacy, non-negotiable from v1:** leaders' answers are sensitive personnel-adjacent data. Named data location, onshore processing posture, explicit consent line on the intake, deletion on request, and the engagement's own adopted AI policy governs the tool that helped write it. Eating our own cooking here is a selling point, say it out loud in the room.

## Where it sits commercially
- **Not a separate SKU.** It is how the Working Session and 90-Day Engagement are delivered; it makes the $1,900 session feel like technology plus judgement instead of a workshop with butcher's paper.
- The persona layer is the retainer hook (personas need a keeper).
- The lite pack (doc 07) is untouched: self-servers get documents; facilitated clients get the room, the app and the personas. The tier line from doc 07 holds exactly.
- Demo cost is near zero once v1 exists: a two-minute screen recording of the tension report appearing is a proof-of-practice social post (pillar 1) that no competitor in the AU SMB space is showing.

## The policy that installs itself (added 22 July, Jeanna's call)
The AI position and ground rules drafted in the room do double duty: the same words load into the organisation's Claude Enterprise instructions (workspace system prompt / project instructions). So the policy the staff read is the policy the AI follows. Ask Claude to do something on the stays-with-a-person list and it declines, says why, and points to a person. Hard limits become automatic; direction becomes ambient. This turns the governance deliverable from a document into configuration, and it is a natural first task of the 90-Day Engagement's build phase (and a reason the client wants Claude Enterprise/Teams, which vooee can supply and configure). Deck carries this beat on the example-statement card.

## The Sprint reskin (same engine, second product)
Jeanna's call, 22 July: reskin this for the six-week AI Enablement Sprint. The engine (framed teaching → silent capture → automatic synthesis → live reveal → 1:1 depth → closing measurement) maps onto the Sprint's existing structure almost without force:

- **Week 1, AI Foundations:** the warm-up cloud ("one word for how AI feels right now") opens the sprint; with a team cohort the anxiety cloud is Section's 52% stat made local, on their own screen. Silent capture follows the foundations teaching: confidence baseline, worries, and the honest tool discovery. Anonymity matters *more* here than with a C-suite; nobody admits shadow AI use with their manager watching, and the anonymous tool list is exactly the discovery the governance work needs.
- **Week 2, goal setting and project identification:** the tension report becomes an **opportunity map**: where the cohort's time goes, where friction repeats, candidate projects surfaced live. The Eisenhower grid from the existing workshop decks becomes the live sorting screen instead of a static card.
- **Weeks 3 to 5, 1:1 coaching:** each person's captured answers arrive as their coaching brief; personalisation without prep time.
- **Week 6, closing session:** re-capture, and the reveal is day-0 next to day-42: the clouds side by side, the confidence scores moved. That before/after IS the proficiency pulse from the alignment work (docs 02 and 05), which means the app doubles as the measurement instrument, and the post-sprint leadership report largely writes itself from the same data.

One build, two products: question sets and branding are the only fork. Working Session skin captures leaders and drafts governance; Sprint skin captures a cohort and drives projects plus measurement. Same Airtable, same report engine, same room theatre. If both skins prove out, the same engine likely reskins again for webinar-scale (Claude 101 live polls), but that is a later thought, not a commitment.

## Decisions for Jeanna
1. Run the MVP (forms + Claude Project) with the next Working Session client, before building anything?
2. Naming: "The Alignment Room" is a working title; needs the usual collision check against existing product names.
3. Persona hosting: client's own Claude workspace (they own it, cleaner) vs vooee-managed (stickier, more admin). Default suggestion: client-owned with vooee as keeper via the fractional seat.
4. Allie Miller licensing check before the boundaries interview borrows more than inspiration.
