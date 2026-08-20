# No competing CTAs — dev spec
Site: example.com · Priority 5 · Medium · Effort: Medium (2-5 days)

## Problem
The page has exactly one call to action, so there is no ambiguity from competing options, but this also means the funnel has no alternative entry points.

## Evidence (from the live site)
> The only call to action on the page is “Learn more”.

## Current state
h1: Example Domain; cta: Learn more; notes: Only one CTA

## Required change
h1: Example Domain; cta: Learn more + secondary CTA (e.g., Contact); notes: Introduce secondary, lower-priority CTA to give choice without overwhelming

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Introduce secondary, lower-priority CTA to give choice without overwhelming
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_no_competing_ctas` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
