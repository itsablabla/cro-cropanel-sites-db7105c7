# Guarantee signal absent — dev spec
Site: nomadinternet.com · Priority 9 · Medium · Effort: Low (0.5-2 days)

## Problem
The rural-internet page includes 'SHOP WITH CONFIDENCE' but no accompanying guarantee, return, or warranty text is captured in the page digest to substantiate that confidence signal.

## Evidence (from the live site)
> h2: SHOP WITH CONFIDENCE
> ctas: CHECK COVERAGE | Watch on | SEE WHAT I QUALIFY FOR | START CHAT | CHECK MY COVERAGE

## Current state
notes: Heading 'SHOP WITH CONFIDENCE' without supporting guarantee text.

## Required change
notes: Add explicit guarantee, return policy, or satisfaction promise copy under the heading.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add explicit guarantee, return policy, or satisfaction promise copy under the heading.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_guarantee_signal_absent` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
