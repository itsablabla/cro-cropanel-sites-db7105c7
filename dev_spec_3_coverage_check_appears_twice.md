# Coverage check appears twice — dev spec
Site: nomadinternet.com · Priority 3 · Medium · Effort: Low (0.5-2 days)

## Problem
The funnel repeats the same coverage-check action with different labels, potentially causing users to restart the journey.

## Evidence (from the live site)
> ctas: CHECK COVERAGE
> ctas: CHECK MY COVERAGE
> ctas: CHECK COVERAGE | Watch on | SEE WHAT I QUALIFY FOR | START CHAT | CHECK MY COVERAGE

## Current state
cta: CHECK COVERAGE and CHECK MY COVERAGE; notes: Same coverage-check action with different labels.

## Required change
cta: One consistent coverage-check label; notes: Use one consistent label and ensure it always advances to the same next step.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Use one consistent label and ensure it always advances to the same next step.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_coverage_check_appears_twice` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
