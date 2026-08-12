# Multiple duplicate forms — dev spec
Site: nomadinternet.com · Priority 8 · Medium · Effort: Medium (2-5 days)

## Problem
The same coverage-check form appears twice on each page, both submitting with CONTINUE, which can confuse visitors about which form to use and create redundant interaction.

## Evidence (from the live site)
> form: submit=CONTINUE (field extraction is unreliable on this site — raw HTML carries 5 field(s); do not claim fields or labels are missing)
> form: submit=CONTINUE (field extraction is unreliable on this site — raw HTML carries 5 field(s); do not claim fields or labels are missing)

## Current state
cta: CONTINUE; notes: Two identical forms per page.

## Required change
cta: CONTINUE; notes: Consolidate into a single form per page.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Consolidate into a single form per page.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_multiple_duplicate_forms` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
