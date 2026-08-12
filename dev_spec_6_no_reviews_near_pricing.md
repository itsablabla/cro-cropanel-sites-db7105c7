# No reviews near pricing — dev spec
Site: nomadinternet.com · Priority 6 · High · Effort: Low (0.5-2 days)

## Problem
The homepage and plans pages display prices and CTAs but the only social proof heading is 'Real Stories from Real Users' with no review content visible in the digest near the pricing sections.

## Evidence (from the live site)
> h2: Real Stories from Real Users
> prices: $99.95/month $129.95/month $99.95/Mo $99.95/month $129.95/month $99.95

## Current state
notes: Social proof heading present but no review content near pricing.

## Required change
notes: Place customer review excerpts, ratings, or testimonial snippets directly adjacent to pricing blocks and coverage CTAs.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Place customer review excerpts, ratings, or testimonial snippets directly adjacent to pricing blocks and coverage CTAs.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_no_reviews_near_pricing` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
