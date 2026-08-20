# Single-step funnel dead end — dev spec
Site: example.com · Priority 2 · High · Effort: Medium (2-5 days)

## Problem
The page offers only one call to action that exits the site, leaving no defined next step in a conversion path.

## Evidence (from the live site)
> The only call to action on the page is “Learn more”.
> Page copy reads “# Example Domain This domain is for use in documentation examples without needing permission. Avoid use in operations. [Learn more](https://iana.org/domains/example)”.

## Current state
h1: Example Domain; cta: Learn more; notes: Single CTA links externally to iana.org

## Required change
h1: Example Domain; cta: Sign up or Explore products; notes: Add internal primary CTA and ensure Learn more leads to a page with next step

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add internal primary CTA and ensure Learn more leads to a page with next step
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_single_step_funnel_dead_end` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
