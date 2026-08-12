# Trust badges not evidenced — dev spec
Site: nomadinternet.com · Priority 4 · Medium · Effort: Medium (2-5 days)

## Problem
The pages reference being 'As Featured In' and 'America's Largest Wireless Internet Provider' but no logos, press mentions, or verification badges appear in the digest to support these credibility claims.

## Evidence (from the live site)
> h2: As Featured In:
> h2: Join America's Largest Wireless Internet Provider Featuring

## Current state
notes: Claims without visual evidence.

## Required change
notes: Display recognizable press logos, partner badges, or third-party verification seals adjacent to these claims.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Display recognizable press logos, partner badges, or third-party verification seals adjacent to these claims.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_trust_badges_not_evidenced` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
