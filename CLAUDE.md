# sturmiusschneider.com — project notes for Claude Code

## What this is
Personal portfolio/bio site for Sturmius Schneider — mathematician, coder, works in finance
(ETF/asset management). Static site, deployed via GitHub Pages, served on the custom domain
`sturmiusschneider.com` (domain purchased via Squarespace, DNS pointed at GitHub Pages, `CNAME`
file at repo root should contain `sturmiusschneider.com`).

Sections on the page: header/intro ("mathematician · coder · finance") → About → Experience →
Skills → Contact. Nav is anchor-based (#about, #experience, #skills, #contact).

Before making changes, inspect the repo structure first (plain HTML/CSS/JS vs. a generator like
Jekyll — GitHub Pages' default). Don't assume; check for `_config.yml`, a `_layouts`/`_includes`
folder, a `package.json` with a build script, etc., and work with whatever's actually there.

## Current priorities, in order
1. **Fix broken/placeholder links** — known issues as of 2026-08-24:
   - "download cv" link has `href="#"` (goes nowhere) — needs either a real CV file linked, or
     removing the button until a CV is ready.
   - "linkedin" link is still the template URL `linkedin.com/in/yourprofile` — needs the real
     profile URL.
2. **Remove placeholder/template content** — several spots still have unfilled template text:
   - Experience entries: "Role Title", "Organisation / Company", "Brief description of what you do"
   - Education: "Your University"
   - Location: "[your city]"
   - Languages: "+ other?"
   **Do not invent real biographical content to fill these in** (job titles, employer names,
   dates, education, location). Stop and ask Sturmius for the actual details rather than guessing
   or writing placeholder-sounding filler — a wrong "fact" here is worse than an empty section.
3. **Add missing metadata**:
   - `<meta name="description">` with a real one-line summary of the site
   - a favicon
   - Open Graph tags (`og:title`, `og:description`, `og:image`) so link previews on
     LinkedIn/Slack/etc. look right
4. **Visual/design polish** — once content is real and links work, do a consistency pass:
   spacing scale, heading sizes, one button style throughout, consistent image treatment, check
   mobile at a couple of breakpoints. Keep the existing minimal/professional tone (mathematical
   symbols like ∑, `</>`, $ are part of the theme — don't strip the personality, just make it
   consistent).

## Working conventions
- After any content or link change, actually verify it: check that internal links resolve to a
  real file/anchor, and that external links (LinkedIn, GitHub, CV) point at real, working URLs —
  don't mark a link "fixed" without checking it.
- No filler/lorem-ipsum text, ever — an empty section that's honestly empty is better than one
  with invented content.
- If GitHub Pages is serving this as a project page rather than `sturmius-s.github.io` directly,
  watch for the base-path trap: absolute links like `/about.html` break under a `/repo-name/`
  prefix. Since this uses a custom domain via `CNAME`, links should be root-relative and fine —
  but double check the `CNAME` file is present and correct if anything looks off.
- Keep commits small and scoped (e.g. "fix broken cv/linkedin links", "add meta tags", "visual
  pass: spacing + buttons") rather than one giant commit — makes it easy to review/revert.
- When unsure about a design or content decision that isn't purely mechanical (wording, which
  projects to list, color choices), ask rather than guessing.