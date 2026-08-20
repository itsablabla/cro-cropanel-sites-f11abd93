# External link funnel dead end — dev spec
Site: example.com · Priority 3 · High · Effort: Medium (2-5 days)

## Problem
The only call to action navigates away from the domain to iana.org, terminating the conversion path without any return or continuation option.

## Evidence (from the live site)
> [Learn more](https://iana.org/domains/example)

## Current state
h1: Example Domain; cta: Learn more; notes: External link to iana.org

## Required change
h1: Example Domain; cta: Learn more (opens in new tab) or internal CTA; notes: Replace or supplement external link with internal destination or open in new tab with visible path back

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Replace or supplement external link with internal destination or open in new tab with visible path back
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_external_link_funnel_dead_end` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
