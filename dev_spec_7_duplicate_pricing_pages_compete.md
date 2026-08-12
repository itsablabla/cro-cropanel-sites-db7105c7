# Duplicate pricing pages compete — dev spec
Site: nomadinternet.com · Priority 7 · Medium · Effort: Medium (2-5 days)

## Problem
Two separate URLs expose the same plans content, creating competing entry points that can split traffic and confuse the funnel.

## Evidence (from the live site)
> PAGE /pages/plans
> PAGE /plans
> h2: The Fastest Rural & On-the-Go Internet in the USA
> prices: $99.95/month $129.95/month $99.95/mo $0.00 $99.95 $99.99

## Current state
notes: Two URLs with same plans content.

## Required change
notes: Consolidate to a single canonical plans URL and redirect the duplicate.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Consolidate to a single canonical plans URL and redirect the duplicate.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_duplicate_pricing_pages_compete` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
