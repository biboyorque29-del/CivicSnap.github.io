<!doctype html><html><head><meta charset=utf8><meta name=viewport content="width=device-width,initial-scale=1,viewport-fit=cover"><style>:root{color-scheme:light;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}html{scroll-padding-top:env(safe-area-inset-top,0px)}body{margin:0;padding:0;font:14px -apple-system,BlinkMacSystemFont,sans-serif;background:#fff;color:#000}img{max-width:100%}[hidden]:not([hidden=until-found i]){display:none!important}</style></head><body>
<title>Civic Snap</title>
<meta name="claude:viewport-fit-sides" content="cover">
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:wght@600;700&family=IBM+Plex+Mono:wght@500&family=Inter:wght@400;500;600&display=swap">
<style>
/* Layout: one centered column. Report = viewfinder photo frame beside a short form. Track = filterable list that opens into a status stepper and update timeline. Status colors borrow utility marking-paint flags. */
:root {
  --font-display: "Bricolage Grotesque", "Trebuchet MS", system-ui, sans-serif;
  --font-body: Inter, system-ui, -apple-system, "Segoe UI", Roboto, sans-serif;
  --font-mono: "IBM Plex Mono", ui-monospace, Menlo, Consolas, monospace;
  --bg: #EFF3F2;
  --surface: #FFFFFF;
  --surface-2: #E3EAE9;
  --ink: #10201F;
  --muted: #4F6463;
  --line: #C9D5D4;
  --accent: #0B6E6D;
  --accent-ink: #FFFFFF;
  --danger: #B3261E;
  --st-received: #C2255C;
  --st-review: #9A5700;
  --st-progress: #2158D6;
  --st-resolved: #217A3B;
}
@media (prefers-color-scheme: dark) {
  :root:not([data-theme="light"]) {
    --bg: #0D1817;
    --surface: #14211F;
    --surface-2: #1B2C2A;
    --ink: #E7F0EE;
    --muted: #93AAA7;
    --line: #2A3F3C;
    --accent: #5CCFC9;
    --accent-ink: #05201F;
    --danger: #FF8A80;
    --st-received: #FF7AA8;
    --st-review: #F2B04A;
    --st-progress: #7FA6FF;
    --st-resolved: #5CCB7D;
    color-scheme: dark;
  }
}
:root[data-theme="dark"] {
  --bg: #0D1817;
  --surface: #14211F;
  --surface-2: #1B2C2A;
  --ink: #E7F0EE;
  --muted: #93AAA7;
  --line: #2A3F3C;
  --accent: #5CCFC9;
  --accent-ink: #05201F;
  --danger: #FF8A80;
  --st-received: #FF7AA8;
  --st-review: #F2B04A;
  --st-progress: #7FA6FF;
  --st-resolved: #5CCB7D;
  color-scheme: dark;
}

*, *::before, *::after { box-sizing: border-box; }
body {
  background: var(--bg);
  color: var(--ink);
  font-family: var(--font-body);
  font-size: 16px;
  line-height: 1.5;
  padding-block: 0 56px;
  padding-left: max(16px, env(safe-area-inset-left, 0px));
  padding-right: max(16px, env(safe-area-inset-right, 0px));
}
.wrap { max-width: 1040px; margin: 0 auto; }
h1, h2 { text-wrap: balance; }
button { font: inherit; }
:focus-visible { outline: 2px solid var(--accent); outline-offset: 2px; }
.sr-only { position: absolute; width: 1px; height: 1px; margin: -1px; padding: 0; overflow: hidden; clip: rect(0 0 0 0); white-space: nowrap; border: 0; }

/* Header */
.top { display: flex; flex-wrap: wrap; align-items: center; justify-content: space-between; gap: 12px 24px; padding-block: 20px; }
.brand { display: flex; align-items: center; gap: 10px; font-family: var(--font-display); font-weight: 700; font-size: 1.3rem; letter-spacing: -0.01em; }
.brand svg { color: var(--accent); flex: none; }
.tag { font-size: 0.72rem; font-weight: 600; letter-spacing: 0.06em; text-transform: uppercase; color: var(--accent); border: 1px solid var(--accent); border-radius: 999px; padding: 2px 8px; }
.tabs { display: flex; gap: 4px; background: var(--surface-2); padding: 4px; border-radius: 10px; }
.tabs a { padding: 8px 14px; border-radius: 7px; color: var(--muted); text-decoration: none; font-weight: 600; font-size: 0.93rem; }
.tabs a[aria-current="page"] { background: var(--surface); color: var(--ink); box-shadow: 0 1px 0 var(--line); }

.h1 { font-family: var(--font-display); font-weight: 700; font-size: clamp(1.7rem, 4.4vw, 2.5rem); line-height: 1.1; letter-spacing: -0.02em; margin: 12px 0 8px; }
.h2 { font-family: var(--font-display); font-weight: 700; font-size: 1.2rem; letter-spacing: -0.01em; margin: 28px 0 12px; }
.lead { max-width: 58ch; color: var(--muted); margin: 0; }

/* Report */
.report { display: grid; grid-template-columns: minmax(0, 1fr); gap: 24px; margin-top: 24px; }
@media (min-width: 800px) { .report { grid-template-columns: minmax(0, 5fr) minmax(0, 6fr); align-items: start; } }
.photo-col { display: grid; gap: 10px; min-width: 0; }
.frame { position: relative; display: grid; place-items: center; aspect-ratio: 4 / 3; max-width: 100%; background: var(--surface-2); border-radius: 12px; overflow: hidden; cursor: pointer; text-align: center; }
.frame:focus-within { outline: 2px solid var(--accent); outline-offset: 2px; }
.frame .c { position: absolute; width: 26px; height: 26px; border: 3px solid var(--accent); pointer-events: none; z-index: 2; }
.c.tl { top: 12px; left: 12px; border-right: 0; border-bottom: 0; border-top-left-radius: 6px; }
.c.tr { top: 12px; right: 12px; border-left: 0; border-bottom: 0; border-top-right-radius: 6px; }
.c.bl { bottom: 12px; left: 12px; border-right: 0; border-top: 0; border-bottom-left-radius: 6px; }
.c.br { bottom: 12px; right: 12px; border-left: 0; border-top: 0; border-bottom-right-radius: 6px; }
.frame-empty { display: grid; gap: 6px; justify-items: center; padding: 28px; color: var(--muted); max-width: 30ch; }
.frame-empty strong { color: var(--ink); font-family: var(--font-display); font-size: 1.1rem; }
.frame-empty .ico { color: var(--accent); }
.frame img { position: absolute; inset: 0; width: 100%; height: 100%; object-fit: cover; }

.form { display: grid; gap: 16px; min-width: 0; }
.field { display: grid; gap: 6px; min-width: 0; }
.lab { font-weight: 600; font-size: 0.9rem; }
.hint { font-size: 0.82rem; color: var(--muted); }
.in { width: 100%; font: inherit; color: var(--ink); background: var(--surface); border: 1px solid var(--line); border-radius: 8px; padding: 10px 12px; }
textarea.in { min-height: 96px; resize: vertical; }
.in::placeholder { color: var(--muted); opacity: 0.8; }
.btn { display: inline-flex; align-items: center; justify-content: center; gap: 8px; font-weight: 600; background: var(--accent); color: var(--accent-ink); border: 1px solid var(--accent); border-radius: 8px; padding: 11px 18px; cursor: pointer; }
.btn:disabled { opacity: 0.55; cursor: not-allowed; }
.btn.ghost { background: transparent; color: var(--ink); border-color: var(--line); }
.btn.small { padding: 7px 12px; font-size: 0.88rem; }
.actions { display: flex; flex-wrap: wrap; align-items: center; gap: 12px; }
.msg { font-size: 0.9rem; min-height: 1.4em; margin: 0; }
.msg.err { color: var(--danger); }

.done { background: var(--surface); border: 1px solid var(--line); border-radius: 12px; padding: 24px; display: grid; gap: 14px; max-width: 560px; margin-top: 24px; }
.done h2 { font-family: var(--font-display); font-size: 1.5rem; margin: 0; letter-spacing: -0.01em; }
.code { font-family: var(--font-mono); font-weight: 500; font-size: 1.6rem; letter-spacing: 0.06em; padding: 8px 14px; background: var(--surface-2); border-radius: 8px; display: inline-block; user-select: all; }

/* Status system */
[data-s="received"] { --st: var(--st-received); }
[data-s="review"] { --st: var(--st-review); }
[data-s="progress"] { --st: var(--st-progress); }
[data-s="resolved"] { --st: var(--st-resolved); }
.pill { --st: var(--ink); display: inline-flex; align-items: center; gap: 6px; font-size: 0.78rem; font-weight: 600; padding: 3px 10px 3px 8px; border-radius: 999px; color: var(--st); background: color-mix(in srgb, var(--st) 13%, var(--surface)); white-space: nowrap; }
.pill::before { content: ""; width: 8px; height: 8px; border-radius: 50%; background: var(--st); }

.steps { list-style: none; display: grid; grid-template-columns: repeat(4, minmax(0, 1fr)); gap: 0; margin: 0; padding: 0; }
.steps li { --st: var(--line); position: relative; padding: 24px 8px 0 0; font-size: 0.82rem; color: var(--muted); }
.steps li::before { content: ""; position: absolute; top: 5px; left: 0; right: 0; height: 3px; background: var(--line); }
.steps li::after { content: ""; position: absolute; top: 0; left: 0; width: 13px; height: 13px; border-radius: 50%; background: var(--surface); border: 3px solid var(--line); }
.steps li.done { --st: var(--st); }
.steps li.done::before { background: var(--st); }
.steps li.done::after { background: var(--st); border-color: var(--st); }
.steps li.current { color: var(--ink); font-weight: 600; }
.flow { margin-top: 36px; }
.flow li { color: var(--ink); }
.flow li::before { background: var(--st); }
.flow li::after { background: var(--st); border-color: var(--st); }
.flow b { display: block; font-family: var(--font-display); font-size: 0.98rem; }
.flow span { display: block; color: var(--muted); }
@media (max-width: 560px) { .flow { grid-template-columns: repeat(2, minmax(0, 1fr)); row-gap: 18px; } }
.steps[aria-label="Progress"] { margin-top: 22px; }

/* Track */
.note { margin-top: 16px; padding: 10px 14px; border: 1px solid var(--line); border-radius: 8px; background: var(--surface); color: var(--muted); font-size: 0.9rem; }
.toolbar { display: flex; flex-wrap: wrap; align-items: center; gap: 12px 18px; margin-top: 22px; }
.toolbar .grow { flex: 1 1 260px; }
.check { display: inline-flex; align-items: center; gap: 8px; font-weight: 600; font-size: 0.92rem; cursor: pointer; }
.check input { width: 18px; height: 18px; accent-color: var(--accent); }
.chips { display: flex; flex-wrap: wrap; gap: 8px; margin: 14px 0 18px; }
.chip { display: inline-flex; align-items: center; gap: 8px; border: 1px solid var(--line); border-radius: 999px; padding: 6px 12px; background: var(--surface); color: var(--ink); font-size: 0.88rem; font-weight: 600; cursor: pointer; }
.chip i { font-style: normal; font-family: var(--font-mono); font-size: 0.8rem; color: var(--muted); }
.chip[aria-pressed="true"] { background: var(--accent); border-color: var(--accent); color: var(--accent-ink); }
.chip[aria-pressed="true"] i { color: inherit; }
.list { display: grid; gap: 10px; }
.empty { color: var(--muted); margin: 8px 0; max-width: 56ch; }
.empty-box { background: var(--surface); border: 1px dashed var(--line); border-radius: 12px; padding: 28px; display: grid; gap: 12px; justify-items: start; }
.empty-box strong { font-family: var(--font-display); font-size: 1.15rem; }
.row { display: grid; grid-template-columns: 72px minmax(0, 1fr) auto; gap: 14px; align-items: center; width: 100%; text-align: left; background: var(--surface); border: 1px solid var(--line); border-radius: 12px; padding: 10px; color: inherit; cursor: pointer; }
.row:hover { border-color: var(--accent); }
.thumb { width: 72px; height: 72px; border-radius: 8px; overflow: hidden; background: var(--surface-2); display: grid; place-items: center; color: var(--muted); }
.thumb img { width: 100%; height: 100%; object-fit: cover; display: block; }
.row .t { font-weight: 600; overflow-wrap: anywhere; }
.row .m { color: var(--muted); font-size: 0.88rem; overflow-wrap: anywhere; }
.mono { font-family: var(--font-mono); font-size: 0.82rem; letter-spacing: 0.04em; color: var(--muted); }
.side { display: grid; gap: 6px; justify-items: end; font-size: 0.82rem; color: var(--muted); }
@media (max-width: 560px) {
  .row { grid-template-columns: 64px minmax(0, 1fr); }
  .thumb { width: 64px; height: 64px; }
  .side { grid-column: 1 / -1; display: flex; justify-content: space-between; align-items: center; }
}

.d-head { display: grid; gap: 20px; margin-top: 16px; }
@media (min-width: 800px) { .d-head { grid-template-columns: minmax(0, 5fr) minmax(0, 6fr); align-items: start; } }
.d-photo { aspect-ratio: 4 / 3; max-width: 100%; border-radius: 12px; overflow: hidden; background: var(--surface-2); display: grid; place-items: center; color: var(--muted); }
.d-photo img { width: 100%; height: 100%; object-fit: cover; display: block; }
.ph { display: grid; gap: 6px; justify-items: center; font-size: 0.88rem; }
.d-info { display: grid; gap: 12px; min-width: 0; align-content: start; justify-items: start; }
.d-info h2 { font-family: var(--font-display); font-size: clamp(1.4rem, 3.4vw, 1.9rem); line-height: 1.15; letter-spacing: -0.015em; margin: 0; overflow-wrap: anywhere; }
.facts { display: grid; grid-template-columns: auto minmax(0, 1fr); gap: 6px 16px; margin: 0; font-size: 0.93rem; }
.facts dt { color: var(--muted); }
.facts dd { margin: 0; overflow-wrap: anywhere; }
.desc { margin: 0; white-space: pre-wrap; overflow-wrap: anywhere; max-width: 60ch; }

.staff { background: var(--surface); border: 1px solid var(--line); border-radius: 12px; padding: 16px; display: grid; gap: 14px; margin-top: 26px; max-width: 640px; }
.staff-h { display: flex; align-items: center; justify-content: space-between; gap: 10px; }
.staff select { max-width: 260px; }

.tl { list-style: none; margin: 0; padding: 0; max-width: 680px; }
.tl li { --st: var(--line); position: relative; padding: 0 0 20px 24px; margin-left: 6px; border-left: 2px solid var(--line); }
.tl li:last-child { border-left-color: transparent; padding-bottom: 0; }
.tl li::before { content: ""; position: absolute; left: -7px; top: 4px; width: 12px; height: 12px; border-radius: 50%; background: var(--st); }
.tl .when { color: var(--muted); font-size: 0.82rem; }
.tl .what { font-weight: 600; }
.tl p { margin: 4px 0 0; overflow-wrap: anywhere; white-space: pre-wrap; }

@media (prefers-reduced-motion: reduce) { * { transition: none !important; animation: none !important; } }
</style>

<div class="wrap">
  <header class="top">
    <div class="brand">
      <svg width="30" height="30" viewBox="0 0 30 30" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M4 11V5h6M20 5h6v6M26 19v6h-6M10 25H4v-6"/><circle cx="15" cy="15" r="3.6" fill="currentColor" stroke="none"/></svg>
      <span>Civic Snap</span>
      <span class="tag" id="staffBadge" hidden>Staff</span>
    </div>
    <nav class="tabs" aria-label="Sections">
      <a href="#report" data-tab="report">Report a concern</a>
      <a href="#track" data-tab="track">Track concerns</a>
    </nav>
  </header>

  <main>
    <section id="view-report">
      <h1 class="h1">See something on campus? Snap it.</h1>
      <p class="lead">Send a photo and a few details. You get a reference code, then follow each update from staff until the concern is resolved.</p>

      <div class="report" id="reportGrid">
        <div class="photo-col">
          <label class="frame" for="photo">
            <span class="c tl"></span><span class="c tr"></span><span class="c bl"></span><span class="c br"></span>
            <span class="frame-empty" id="frameEmpty">
              <svg class="ico" viewBox="0 0 24 24" width="34" height="34" fill="none" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M4 8.5h3l1.6-2.5h6.8L17 8.5h3a1 1 0 0 1 1 1V18a1 1 0 0 1-1 1H4a1 1 0 0 1-1-1V9.5a1 1 0 0 1 1-1z"/><circle cx="12" cy="13.5" r="3.6"/></svg>
              <strong>Take or choose a photo</strong>
              <span>Optional, and it helps staff find the problem faster.</span>
            </span>
            <img id="preview" alt="Preview of the photo you selected" hidden>
            <input id="photo" class="sr-only" type="file" accept="image/*">
          </label>
          <p class="hint">Photos are visible to everyone who can open this site, so keep faces and license plates out of the frame.</p>
          <div><button type="button" id="rmPhoto" class="btn ghost small" hidden>Remove photo</button></div>
        </div>

        <form id="reportForm" class="form" novalidate>
          <div class="field">
            <label class="lab" for="title">What is the concern?</label>
            <input id="title" class="in" type="text" maxlength="140" autocomplete="off" placeholder="e.g. Broken light in the library stairwell" required>
          </div>
          <div class="field">
            <label class="lab" for="category">Category</label>
            <select id="category" class="in"></select>
          </div>
          <div class="field">
            <label class="lab" for="place">Where on campus?</label>
            <input id="place" class="in" type="text" maxlength="140" autocomplete="off" placeholder="Building, floor or landmark" required>
          </div>
          <div class="field">
            <label class="lab" for="details">Details <span class="hint">(optional)</span></label>
            <textarea id="details" class="in" maxlength="2000" placeholder="When did you notice it? Is anyone at risk?"></textarea>
          </div>
          <div class="field">
            <label class="lab" for="who">Your name <span class="hint">(optional)</span></label>
            <input id="who" class="in" type="text" maxlength="60" autocomplete="name" placeholder="Leave blank to appear as Anonymous">
          </div>
          <div class="actions">
            <button type="submit" class="btn" id="sendBtn">Send concern</button>
            <p class="msg" id="formMsg" role="status"></p>
          </div>
        </form>
      </div>

      <div class="done" id="done" hidden>
        <h2>Concern sent</h2>
        <p class="lead">Keep this reference code. You can search for it on the Track page at any time.</p>
        <div><span class="code" id="doneCode"></span></div>
        <div class="actions">
          <button type="button" class="btn" id="viewBtn">View progress</button>
          <button type="button" class="btn ghost" id="copyBtn">Copy code</button>
          <button type="button" class="btn ghost" id="againBtn">File another</button>
        </div>
      </div>

      <h2 class="h2">What happens after you send it</h2>
      <ol class="steps flow" style="margin-top:0">
        <li data-s="received"><b>Received</b><span>Your concern is logged with its photo and location.</span></li>
        <li data-s="review"><b>Under review</b><span>Staff check it and decide who should handle it.</span></li>
        <li data-s="progress"><b>In progress</b><span>Work has started or is scheduled.</span></li>
        <li data-s="resolved"><b>Resolved</b><span>The fix is done and the concern is closed.</span></li>
      </ol>
    </section>

    <section id="view-track" hidden>
      <h1 class="h1">Track concerns</h1>
      <p class="lead">Every concern filed around campus, with the latest update from staff. Search by reference code, title or place.</p>
      <div id="note" class="note" hidden></div>

      <div id="listPane">
        <div class="toolbar">
          <div class="field grow">
            <label class="sr-only" for="q">Search concerns</label>
            <input id="q" class="in" type="search" placeholder="Search by code, title or place" autocomplete="off">
          </div>
          <label class="check" id="mineWrap" hidden><input id="mine" type="checkbox"> Only mine</label>
        </div>
        <div id="chips" class="chips" role="group" aria-label="Filter by status"></div>
        <div id="list" class="list" aria-live="polite"><p class="empty">Loading concerns…</p></div>
      </div>

      <div id="detail" hidden>
        <div style="margin-top:22px"><button type="button" id="backBtn" class="btn ghost small">← All concerns</button></div>
        <div id="dHead" class="d-head"></div>
        <ol id="dSteps" class="steps" aria-label="Progress"></ol>
        <form id="staffForm" class="staff" hidden>
          <div class="staff-h"><strong>Post an update</strong><span class="tag">Staff only</span></div>
          <div class="field">
            <label class="lab" for="sStatus">Status</label>
            <select id="sStatus" class="in"></select>
          </div>
          <div class="field">
            <label class="lab" for="sNote">Note for the reporter</label>
            <textarea id="sNote" class="in" rows="3" maxlength="1000" placeholder="e.g. An electrician is scheduled for Thursday morning."></textarea>
          </div>
          <div class="actions">
            <button type="submit" class="btn" id="sBtn">Post update</button>
            <p class="msg" id="sMsg" role="status"></p>
          </div>
        </form>
        <h2 class="h2">Updates</h2>
        <ol id="dTimeline" class="tl"></ol>
      </div>
    </section>
  </main>
</div>

<script>
(function () {
  "use strict";
  var $ = function (s, r) { return (r || document).querySelector(s); };
  var $$ = function (s, r) { return Array.prototype.slice.call((r || document).querySelectorAll(s)); };

  var STATUS = [
    { key: "received", label: "Received" },
    { key: "review", label: "Under review" },
    { key: "progress", label: "In progress" },
    { key: "resolved", label: "Resolved" }
  ];
  var SKEY = STATUS.map(function (s) { return s.key; });
  var CATS = ["Broken or damaged facility", "Lighting", "Cleanliness and waste", "Safety hazard", "Accessibility", "Flooding or drainage", "Noise or disturbance", "Other"];

  var S = {
    db: null, assets: null, myId: null, isStaff: false, canWrite: null,
    concerns: [], updates: [], got: { c: false, u: false }, slow: false, failed: false, ready: false,
    view: "report", openId: null, filter: "all", q: "", mine: false,
    file: null, blob: null, busy: false, lastId: null, primed: false, photoCache: {}, photoAsked: {}
  };

  function slabel(k) { for (var i = 0; i < STATUS.length; i++) if (STATUS[i].key === k) return STATUS[i].label; return STATUS[0].label; }
  function str(v, n) { return typeof v === "string" ? v.slice(0, n) : ""; }

  function el(tag, props) {
    var n = document.createElement(tag);
    var p = props || {};
    Object.keys(p).forEach(function (k) {
      var v = p[k];
      if (v == null || v === false) return;
      if (k === "class") n.className = v;
      else if (k === "text") n.textContent = v;
      else if (k.indexOf("on") === 0) n.addEventListener(k.slice(2), v);
      else n.setAttribute(k, v === true ? "" : v);
    });
    for (var i = 2; i < arguments.length; i++) {
      var kid = arguments[i];
      if (kid == null || kid === false) continue;
      n.append(kid.nodeType ? kid : document.createTextNode(String(kid)));
    }
    return n;
  }
  var CAMERA = '<svg viewBox="0 0 24 24" width="28" height="28" fill="none" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M4 8.5h3l1.6-2.5h6.8L17 8.5h3a1 1 0 0 1 1 1V18a1 1 0 0 1-1 1H4a1 1 0 0 1-1-1V9.5a1 1 0 0 1 1-1z"/><circle cx="12" cy="13.5" r="3.6"/></svg>';
  function camera() { var s = document.createElement("span"); s.innerHTML = CAMERA; return s; }
  function placeholder(label) { return el("div", { class: "ph" }, camera(), label ? el("span", { text: label }) : null); }

  function fmtFull(iso) {
    var d = new Date(iso);
    if (isNaN(d)) return "";
    return d.toLocaleString(undefined, { month: "short", day: "numeric", year: "numeric", hour: "numeric", minute: "2-digit" });
  }
  function ago(iso) {
    var d = new Date(iso);
    if (isNaN(d)) return "";
    var s = (Date.now() - d.getTime()) / 1000;
    if (s < 60) return "just now";
    var m = s / 60; if (m < 60) return Math.floor(m) + " min ago";
    var h = m / 60; if (h < 24) return Math.floor(h) + " h ago";
    var dd = h / 24; if (dd < 7) return Math.floor(dd) + " d ago";
    return d.toLocaleDateString(undefined, { month: "short", day: "numeric" });
  }

  /* ---------- data ---------- */
  function derive() {
    var byC = {};
    S.updates.forEach(function (u) {
      var id = str(u.concernId, 80);
      if (!id) return;
      (byC[id] = byC[id] || []).push({
        id: u.id, status: SKEY.indexOf(u.status) >= 0 ? u.status : "received",
        note: str(u.note, 1000), at: str(u.at, 40)
      });
    });
    Object.keys(byC).forEach(function (k) { byC[k].sort(function (a, b) { return b.at.localeCompare(a.at); }); });
    return S.concerns.map(function (c) {
      var ups = byC[c.id] || [];
      var created = str(c.createdAt, 40);
      return {
        id: c.id,
        refCode: str(c.ref, 12),
        title: str(c.title, 140) || "Untitled concern",
        category: str(c.category, 60),
        place: str(c.place, 140),
        details: str(c.details, 2000),
        who: str(c.reporterLabel, 60),
        reporterId: typeof c.reporterId === "string" ? c.reporterId : null,
        photoId: typeof c.photoId === "string" && /^[0-9a-f]{32}$/.test(c.photoId) ? c.photoId : null,
        hasPhotoDoc: c.hasPhotoDoc === true,
        createdAt: created,
        ups: ups,
        status: ups.length ? ups[0].status : "received",
        activity: ups.length ? ups[0].at : created
      };
    }).sort(function (a, b) { return b.activity.localeCompare(a.activity); });
  }

  function listen(query, key, assign) {
    var timer = setTimeout(function () { S.slow = true; render(); }, 10000);
    query.onSnapshot(function (snap) {
      if (!snap.metadata.fromCache) { clearTimeout(timer); S.slow = false; }
      assign(snap.docs.map(function (d) { return Object.assign({}, d.data(), { id: d.id }); }));
      S.got[key] = true;
      render();
    }, function () {
      clearTimeout(timer); S.failed = true; render();
    });
  }

  /* ---------- rendering ---------- */
  function render() {
    $$("[data-tab]").forEach(function (a) {
      if (a.getAttribute("data-tab") === S.view) a.setAttribute("aria-current", "page"); else a.removeAttribute("aria-current");
    });
    $("#view-report").hidden = S.view !== "report";
    $("#view-track").hidden = S.view !== "track";
    $("#staffBadge").hidden = !S.isStaff;
    $("#mineWrap").hidden = !S.myId;
    if (S.view === "track") renderTrack();
  }

  function renderNote() {
    var n = $("#note"), t = "";
    if (S.ready && !S.db) t = "Concerns can't load in this view. Open the page while signed in to see and file them.";
    else if (S.failed) t = "The concern list stopped updating. Reload the page to try again.";
    else if (S.slow) t = "Still waiting on the concern list. What you see may be out of date.";
    n.hidden = !t; n.textContent = t;
  }

  function renderTrack() {
    renderNote();
    var detail = S.openId != null;
    $("#listPane").hidden = detail;
    $("#detail").hidden = !detail;
    if (detail) renderDetail(); else renderList();
  }

  function renderList() {
    var all = derive();
    var counts = { all: all.length };
    STATUS.forEach(function (s) { counts[s.key] = 0; });
    all.forEach(function (c) { counts[c.status]++; });

    var chips = $("#chips"); chips.replaceChildren();
    [{ key: "all", label: "All" }].concat(STATUS).forEach(function (s) {
      chips.append(el("button", {
        type: "button", class: "chip", "aria-pressed": String(S.filter === s.key),
        onclick: function () { S.filter = s.key; renderList(); }
      }, s.label, el("i", { text: String(counts[s.key]) })));
    });

    var q = S.q.trim().toLowerCase();
    var rows = all.filter(function (c) {
      if (S.filter !== "all" && c.status !== S.filter) return false;
      if (S.mine && (!S.myId || c.reporterId !== S.myId)) return false;
      if (q && (c.title + " " + c.place + " " + c.refCode + " " + c.category).toLowerCase().indexOf(q) < 0) return false;
      return true;
    });

    var list = $("#list"); list.replaceChildren();
    if (!S.db) {
      list.append(el("p", { class: "empty", text: S.ready ? "Nothing to show here yet." : "Loading concerns…" }));
      return;
    }
    if (!(S.got.c && S.got.u)) { list.append(el("p", { class: "empty", text: "Loading concerns…" })); return; }
    if (!all.length) {
      list.append(el("div", { class: "empty-box" },
        el("strong", { text: "No concerns have been filed yet" }),
        el("span", { class: "empty", text: "When someone reports a concern it shows up here with its photo, location and every status update from staff." }),
        el("a", { class: "btn", href: "#report", text: "File the first concern", style: "text-decoration:none" })));
      return;
    }
    if (!rows.length) {
      list.append(el("div", { class: "empty-box" },
        el("strong", { text: "No concerns match" }),
        el("button", { type: "button", class: "btn ghost small", text: "Clear filters", onclick: function () { S.filter = "all"; S.q = ""; S.mine = false; $("#q").value = ""; $("#mine").checked = false; renderList(); } })));
      return;
    }
    rows.forEach(function (c) {
      var thumb = el("div", { class: "thumb" });
      if (c.photoId) {
        thumb.append(el("img", { src: "/_blob/" + c.photoId, alt: "", loading: "lazy", onerror: function () { thumb.replaceChildren(camera()); } }));
      } else thumb.append(camera());
      list.append(el("button", { type: "button", class: "row", onclick: function () { openConcern(c.id); } },
        thumb,
        el("div", {},
          el("div", { class: "t", text: c.title }),
          el("div", { class: "m", text: [c.place, c.category].filter(Boolean).join(" · ") }),
          el("div", { class: "mono", text: c.refCode })),
        el("div", { class: "side" },
          el("span", { class: "pill", "data-s": c.status, text: slabel(c.status) }),
          el("span", { text: ago(c.activity) }))));
    });
  }

  function openConcern(id) { S.openId = id; S.primed = false; $("#sMsg").textContent = ""; renderTrack(); window.scrollTo(0, 0); }

  function photoNode(c) {
    var box = el("div", { class: "d-photo" });
    if (c.photoId) {
      box.append(el("img", { src: "/_blob/" + c.photoId, alt: "Photo of the concern", onerror: function () { box.replaceChildren(placeholder("Photo isn't available to you")); } }));
    } else if (c.hasPhotoDoc) {
      var cached = S.photoCache[c.id];
      if (cached) box.append(el("img", { src: cached, alt: "Photo of the concern" }));
      else {
        box.append(placeholder("Loading photo…"));
        if (S.db && !S.photoAsked[c.id]) {
          S.photoAsked[c.id] = true;
          S.db.doc("photos/" + c.id).get().then(function (snap) {
            var d = snap.exists ? snap.data() : null;
            if (d && typeof d.data === "string" && d.data.indexOf("data:image/jpeg;base64,") === 0) { S.photoCache[c.id] = d.data; if (S.openId === c.id) renderDetail(); }
          }).catch(function () {});
        }
      }
    } else box.append(placeholder("No photo with this concern"));
    return box;
  }

  function renderDetail() {
    var c = derive().filter(function (x) { return x.id === S.openId; })[0];
    var head = $("#dHead"), steps = $("#dSteps"), tl = $("#dTimeline");
    head.replaceChildren(); steps.replaceChildren(); tl.replaceChildren();
    var staff = $("#staffForm");
    if (!c) {
      staff.hidden = true;
      head.append(el("p", { class: "empty", text: S.got.c ? "That concern isn't in the list yet. Go back and check again in a moment." : "Loading concern…" }));
      return;
    }

    var facts = el("dl", { class: "facts" });
    [["Reference", c.refCode], ["Where", c.place], ["Category", c.category], ["Filed", fmtFull(c.createdAt)], ["Reported by", c.who || "Anonymous"]].forEach(function (f) {
      if (!f[1]) return;
      facts.append(el("dt", { text: f[0] }), el("dd", { class: f[0] === "Reference" ? "mono" : null, text: f[1] }));
    });
    head.append(photoNode(c), el("div", { class: "d-info" },
      el("span", { class: "pill", "data-s": c.status, text: slabel(c.status) }),
      el("h2", { text: c.title }),
      facts,
      c.details ? el("p", { class: "desc", text: c.details }) : null));

    var idx = SKEY.indexOf(c.status);
    STATUS.forEach(function (s, i) {
      steps.append(el("li", { "data-s": s.key, class: (i <= idx ? "done" : "") + (i === idx ? " current" : ""), "aria-current": i === idx ? "step" : null, text: s.label }));
    });

    c.ups.forEach(function (u) {
      tl.append(el("li", { "data-s": u.status },
        el("div", { class: "what", text: slabel(u.status) }),
        el("div", { class: "when", text: fmtFull(u.at) }),
        u.note ? el("p", { text: u.note }) : null));
    });
    tl.append(el("li", {},
      el("div", { class: "what", text: "Concern filed" }),
      el("div", { class: "when", text: fmtFull(c.createdAt) })));

    staff.hidden = !S.isStaff;
    if (S.isStaff && !S.primed) { $("#sStatus").value = SKEY[Math.min(idx + 1, SKEY.length - 1)]; S.primed = true; }
  }

  /* ---------- photo handling ---------- */
  function loadImg(file) {
    return new Promise(function (res, rej) {
      var url = URL.createObjectURL(file), img = new Image();
      img.onload = function () { URL.revokeObjectURL(url); res(img); };
      img.onerror = function () { URL.revokeObjectURL(url); rej(new Error("read")); };
      img.src = url;
    });
  }
  function shrink(file, max, q) {
    var get = typeof createImageBitmap === "function"
      ? createImageBitmap(file).catch(function () { return loadImg(file); })
      : loadImg(file);
    return get.then(function (bmp) {
      var w0 = bmp.width, h0 = bmp.height;
      var k = Math.min(1, max / Math.max(w0, h0));
      var cv = document.createElement("canvas");
      cv.width = Math.max(1, Math.round(w0 * k)); cv.height = Math.max(1, Math.round(h0 * k));
      cv.getContext("2d").drawImage(bmp, 0, 0, cv.width, cv.height);
      return new Promise(function (res) { cv.toBlob(res, "image/jpeg", q); });
    });
  }
  function toDataUrl(blob) {
    return new Promise(function (res, rej) {
      var r = new FileReader();
      r.onload = function () { res(String(r.result)); };
      r.onerror = function () { rej(new Error("read")); };
      r.readAsDataURL(blob);
    });
  }
  var previewUrl = null;
  function setMsg(t, err) { var m = $("#formMsg"); m.textContent = t || ""; m.className = "msg" + (err ? " err" : ""); }
  function clearPhoto() {
    S.file = null; S.blob = null;
    $("#photo").value = "";
    if (previewUrl) { URL.revokeObjectURL(previewUrl); previewUrl = null; }
    $("#preview").hidden = true; $("#preview").removeAttribute("src");
    $("#frameEmpty").hidden = false; $("#rmPhoto").hidden = true;
  }
  $("#photo").addEventListener("change", function (e) {
    var f = e.target.files && e.target.files[0];
    if (!f) return;
    setMsg("");
    shrink(f, 1280, 0.8).then(function (blob) {
      if (!blob) throw new Error("blob");
      if (previewUrl) URL.revokeObjectURL(previewUrl);
      S.file = f; S.blob = blob; previewUrl = URL.createObjectURL(blob);
      $("#preview").src = previewUrl; $("#preview").hidden = false;
      $("#frameEmpty").hidden = true; $("#rmPhoto").hidden = false;
    }).catch(function () { clearPhoto(); setMsg("That file couldn't be read as a photo. Try a JPEG or PNG.", true); });
  });
  $("#rmPhoto").addEventListener("click", clearPhoto);

  /* ---------- report form ---------- */
  CATS.forEach(function (c) { $("#category").append(el("option", { value: c, text: c })); });
  STATUS.forEach(function (s) { $("#sStatus").append(el("option", { value: s.key, text: s.label })); });

  function refCode() {
    var a = "ABCDEFGHJKMNPQRSTUVWXYZ23456789", out = "";
    var buf = new Uint32Array(4);
    (window.crypto || window.msCrypto).getRandomValues(buf);
    for (var i = 0; i < 4; i++) out += a[buf[i] % a.length];
    return "CS-" + out;
  }
  function writeError(err) {
    var c = err && err.code;
    if (c === "invalid_argument") return "Your account can view concerns but can't file new ones. Ask the site owner for contributor access.";
    if (c === "quota_exceeded" || c === "quota_or_state") return "The site's storage is full right now. Tell the site owner so they can free some space.";
    if (c === "too_large") return "That photo is too large. Try a smaller one.";
    if (c === "rate_limited" || c === "resource_exhausted") return "Too many requests at once. Wait a moment and send it again.";
    return "Couldn't send your concern. Check your connection and try again.";
  }

  $("#reportForm").addEventListener("submit", function (e) {
    e.preventDefault();
    if (S.busy) return;
    var title = $("#title").value.trim(), place = $("#place").value.trim();
    if (!title) { setMsg("Add a short title for the concern.", true); $("#title").focus(); return; }
    if (!place) { setMsg("Tell us where on campus it is.", true); $("#place").focus(); return; }
    if (!S.db) { setMsg("Concerns can't be saved in this view. Open the page while signed in.", true); return; }

    S.busy = true; $("#sendBtn").disabled = true; setMsg("Sending…");
    var docRef = S.db.collection("concerns").doc();
    var rec = {
      ref: refCode(), title: title, category: $("#category").value, place: place,
      details: $("#details").value.trim(), reporterLabel: $("#who").value.trim(),
      reporterId: S.myId || null, createdAt: new Date().toISOString()
    };
    var photoStep = Promise.resolve();
    if (S.blob) {
      if (S.assets) {
        photoStep = S.assets.upload(S.blob, { type: "image/jpeg" }).then(function (up) { rec.photoId = up.id; });
      } else {
        var tries = [[1280, 0.75], [1000, 0.62], [800, 0.5], [640, 0.45]];
        photoStep = tries.reduce(function (p, t) {
          return p.then(function (found) {
            if (found) return found;
            return shrink(S.file, t[0], t[1]).then(toDataUrl).then(function (u) { return u.length <= 230000 ? u : null; });
          });
        }, Promise.resolve(null)).then(function (url) {
          if (!url) throw { code: "too_large" };
          return S.db.doc("photos/" + docRef.id).set({ data: url }).then(function () { rec.hasPhotoDoc = true; });
        });
      }
    }
    photoStep.then(function () { return docRef.set(rec); }).then(function () {
      S.lastId = docRef.id;
      $("#doneCode").textContent = rec.ref;
      $("#reportGrid").hidden = true; $("#done").hidden = false;
      setMsg("");
    }).catch(function (err) {
      setMsg(writeError(err), true);
    }).then(function () { S.busy = false; $("#sendBtn").disabled = false; });
  });

  $("#againBtn").addEventListener("click", function () {
    $("#reportForm").reset(); clearPhoto(); setMsg("");
    $("#done").hidden = true; $("#reportGrid").hidden = false;
    $("#title").focus();
  });
  $("#viewBtn").addEventListener("click", function () {
    S.filter = "all"; S.q = ""; S.mine = false; $("#q").value = ""; $("#mine").checked = false;
    S.openId = S.lastId; S.primed = false;
    if (location.hash === "#track") route(); else location.hash = "#track";
  });
  $("#copyBtn").addEventListener("click", function () {
    var b = $("#copyBtn"), code = $("#doneCode").textContent;
    function selectIt() {
      var r = document.createRange(); r.selectNodeContents($("#doneCode"));
      var s = window.getSelection(); s.removeAllRanges(); s.addRange(r);
      b.textContent = "Code selected";
    }
    try {
      navigator.clipboard.writeText(code).then(function () {
        b.textContent = "Copied"; setTimeout(function () { b.textContent = "Copy code"; }, 1800);
      }, selectIt);
    } catch (err) { selectIt(); }
  });

  /* ---------- track controls ---------- */
  $("#q").addEventListener("input", function (e) { S.q = e.target.value; renderList(); });
  $("#mine").addEventListener("change", function (e) { S.mine = e.target.checked; renderList(); });
  $("#backBtn").addEventListener("click", function () { S.openId = null; renderTrack(); });

  $("#staffForm").addEventListener("submit", function (e) {
    e.preventDefault();
    if (S.busy || !S.db || S.openId == null) return;
    var status = $("#sStatus").value, note = $("#sNote").value.trim();
    var cur = derive().filter(function (x) { return x.id === S.openId; })[0];
    function msg(t, err) { var m = $("#sMsg"); m.textContent = t; m.className = "msg" + (err ? " err" : ""); }
    if (SKEY.indexOf(status) < 0) return;
    if (!note && cur && cur.status === status) { msg("Choose a new status or write a note.", true); return; }
    S.busy = true; $("#sBtn").disabled = true; msg("Posting…");
    S.db.collection("updates").add({ concernId: S.openId, status: status, note: note.slice(0, 1000), at: new Date().toISOString(), by: S.myId || null })
      .then(function () { $("#sNote").value = ""; msg("Update posted.", false); })
      .catch(function (err) { msg(err && err.code === "invalid_argument" ? "Only staff with edit access can post updates." : "Couldn't post the update. Try again.", true); })
      .then(function () { S.busy = false; $("#sBtn").disabled = false; });
  });

  /* ---------- routing and startup ---------- */
  function route() { S.view = location.hash === "#track" ? "track" : "report"; render(); }
  window.addEventListener("hashchange", route);
  $$("[data-tab]").forEach(function (a) {
    a.addEventListener("click", function () { S.openId = null; render(); });
  });
  route();

  function use(name) {
    try {
      if (window.claude && window.claude.use) return Promise.resolve(window.claude.use(name)).catch(function () { return null; });
    } catch (e) { /* fall through */ }
    return Promise.resolve(null);
  }

  Promise.all([use("db"), use("user"), use("assets")]).then(function (r) {
    S.db = r[0]; S.assets = r[2]; S.ready = true;
    var user = r[1];
    var info = user
      ? Promise.all([user.id(), user.canEdit(), user.can("data.write")]).then(function (v) { S.myId = v[0]; S.isStaff = v[1]; S.canWrite = v[2]; }).catch(function () {})
      : Promise.resolve();
    return info;
  }).then(function () {
    if (S.canWrite === false) setMsg("You can follow concerns here, but your account can't file new ones yet. Ask the site owner for contributor access.", true);
    render();
    if (S.db) {
      listen(S.db.collection("concerns").limit(500), "c", function (rows) { S.concerns = rows; });
      listen(S.db.collection("updates").limit(1000), "u", function (rows) { S.updates = rows; });
    }
  });
})();
</script>

</body></html>
