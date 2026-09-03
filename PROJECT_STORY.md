# Building a Clinic Scheduling Model for Pediatric Gastroenterology

*A spreadsheet that became a tool leadership can actually use — and a few
things it taught me along the way.*

## Purpose

Our pediatric gastroenterology division recently adopted a new practice
plan, which changes how physician effort and clinic time translate into
financial outcomes for the department. I wanted to understand, in concrete
terms, how our clinic schedule affects that math — not to chase revenue
for its own sake, but so that leadership could make informed, deliberate
choices about how we structure our two clinic types: general GI visits,
and a specialty clinic (motility) that runs longer, more complex follow-up
visits. Rather than debating this with gut feel and anecdotes, I wanted a
tool that could answer "what if we ran it differently?" honestly, with
real numbers.

## The Process

I started small: a spreadsheet. Medicare's time-based billing rules assign
a specific "work RVU" — a standardized unit representing physician effort
— to each visit-complexity billing code, along with a required minimum
number of minutes to bill at that level. Using those actual rules, I built
a model of exactly how much production a clinic session could generate,
given our real slot lengths and patient mix.

That first version was intentionally rough — a placeholder 50/50 split
between two common billing levels, just to get the structure right. Once
the foundation worked, I kept making it more honest, one layer at a time:

- Replaced the placeholder billing-level split with the ability to enter
  our *actual* distribution across all five visit-complexity levels, once
  that data was available.
- Added our historical no-show rate, since a slot on the calendar isn't
  the same as a completed, billable visit.
- Turned the static spreadsheet into an interactive web tool, so
  department leadership could adjust assumptions themselves and watch the
  numbers respond, instead of asking me to re-run a spreadsheet every time
  a question came up.
- Generalized the "motility" clinic into a flexible "specialty clinic"
  concept, since the same structure could describe any second clinic
  type, not just this one.
- Added the ability to export a clean Excel file or a one-page PDF
  summary, so results could be shared in a meeting without anyone needing
  to touch the live tool.
- Solved a practical problem: how do you let someone save their specific
  set of assumptions without standing up a server or database? The answer
  was to encode everything directly into a web link. Open the link, and
  your exact inputs are right there — no account, no login, and no way for
  one person's data to ever be visible to another.

## Barriers Along the Way

The most interesting obstacle wasn't technical — it was a discovery the
model itself surfaced. Medicare's time-based billing rules require a
minimum number of minutes to bill at a given complexity level. When I
checked our shorter clinic template against those minimums, I found that
some higher-complexity visits simply don't fit inside the scheduled time,
at least not without work happening outside the visit itself. That's not
a hypothetical concern — it has real implications for both compliance and
revenue, and it only became visible once the numbers were laid out
precisely.

There was also a more values-based tension. The model can reliably show
that one clinic type produces more revenue per hour than the other. But a
good tool shouldn't quietly nudge someone toward cutting a clinical
service just because it scores lower on one financial metric — access to
specialty care matters too. I made a point of keeping that tension visible
rather than letting the tool resolve it silently.

A few more ordinary obstacles came up along the way: a data gap around
facility billing that I couldn't responsibly model without more
information from our hospital's billing office, so I flagged it
explicitly as unknown rather than guessing at a number. And, while adding
a new export feature, I introduced — and later caught — a small bug where
certain punctuation displayed incorrectly in one view. A good reminder
that even a fairly simple tool needs to be checked carefully, not trusted
just because it runs.

## What I Learned

Turning an assumption into a number is a forcing function. Saying a
clinic's visits are "usually a level 3 or 4" feels precise enough in
conversation, but building that into an actual calculation exposes
exactly how much that vagueness was hiding — in this case, a real
structural mismatch in our clinic template that no one had flagged
before.

I also learned that financial and clinical priorities don't have to be
reconciled by the tool itself. A model's job is to make trade-offs
visible and honest, not to make the decision for you.

Finally, this project changed my sense of what's possible to build
without a traditional engineering background. Using AI-assisted coding
tools, I went from a spreadsheet to a working, shareable web application,
iterating in the same conversation as the underlying clinical and
financial questions themselves. That said, a tool is only as trustworthy
as the verification behind it — I cross-checked the math by hand and
against a second, independent model at every step, and I'd encourage
anyone doing something similar to do the same.

---

[View the project →](#) *(replace with your repo link)*
