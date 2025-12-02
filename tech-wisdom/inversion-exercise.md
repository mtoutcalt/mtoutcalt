# Inversion Pass Questions

## Catastrophic failure
**"What would make this an absolute disaster?"**
- What could cause a P1 incident?
- What are the likely root causes?
- Which single component failure would cascade most dramatically?

## Silent degradation
**"How could this fail without us knowing?"**
- What metrics are we not monitoring?
- Which failure modes wouldn't trigger existing alerts?
- Where are the blind spots in observability and logging?
- What could degrade slowly enough that we wouldn't notice until customers complained?

## Rollback
**"What if we need to roll this back at 3am?"**
- Can this change be reversed?
- How long would rollback take?
- Is anything irreversible?
- At what point does rolling back become more dangerous than rolling forward?
- What happens if rollback doesn't work?

## Load and scale
**"What happens when real load exceeds our assumptions?"**
- What breaks at 10x the estimated load?
- Are there resources we've assumed will work that could fail?
- What happens in high traffic scenarios with extreme contention or queuing?

## Dependency failures
**"What if everything we depend on breaks?"**
- List all external services (databases, APIs, etc.)
- For each: what happens if it becomes slow or unavailable?
- Do we need retries or circuit breakers?

## Human error
**"How could we break this ourselves?"**
- Which operational steps are prone to human error?
- Do we have everything documented in playbooks?
- What if the on-call person doesn't understand the system?

## Data integrity and security
**"Is it possible to corrupt or lose data?"**
- Have we considered race conditions?
- Are we assuming transactionality that doesn't exist?
- What happens if we process the same event twice or skip one?
- How do we detect data inconsistency?
- What are the attack vectors?
- Which data are we exposing and to whom?

---

## Risk Categorization

After capturing all risks, categorize each as:

- **Showstopper** - must be addressed before launch
- **Mitigation** - needs monitoring, fallbacks, or workarounds
- **Accepted risk** - understood and moving forward regardless
