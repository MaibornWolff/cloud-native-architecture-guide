---
title: "Feature Flags"
category: "glossary"
---
# Feature Flags

Feature flags (also known as feature toggles or feature switches) are a software development technique that allows teams to modify system behavior without changing and redeploying code. At its core, a feature flag is a decision point in code that determines which execution path to follow, controlled by an external configuration rather than hard-coded logic.

Feature flags enable teams to separate feature deployment from feature release, test features in production with limited user exposure, conduct A/B testing, manage risky changes with controlled rollouts, and turn off problematic features quickly without rollbacks. This capability is fundamental to modern DevOps practices as it decouples deployment from release, reducing risk and increasing deployment frequency while maintaining control over the user experience.

In practice, feature flags can be implemented in various ways, from simple to sophisticated. A basic implementation might use a conditional statement that checks a configuration value to determine which code path to execute. More advanced implementations use feature flag management services that provide targeting capabilities for progressive rollouts.

Feature flags can be categorized based on their lifespan and purpose. **Release flags** hide incomplete or untested code paths in production deployments, typically short-lived to support trunk-based development. **Experiment flags** facilitate A/B testing to gather user feedback and metrics on different implementations, allowing teams to make data-driven decisions. **Operational flags** control system aspects like enabling or disabling integrations that might impact performance, often serving as kill switches during incidents. **Permission flags** grant specific features to particular user segments or customer tiers based on attributes like subscription level or geography.

A basic feature flag implementation might look like this in code:

```python
if feature_flag_service.is_enabled("new_algorithm"):
    return new_algorithm_result()
else:
    return old_algorithm_result()
```

More sophisticated implementations use feature flag management services that provide targeting capabilities, allowing for progressive rollouts. In this approach, a feature might initially be released to internal users, then beta testers, followed by a small percentage of production users, and finally to all users. This gradual exposure minimizes risk and allows for monitoring and feedback at each stage.

Another common pattern is the kill switch, where critical systems implement feature flags that can quickly disable problematic features during incidents. This provides a safety mechanism that allows teams to respond rapidly to production issues without requiring a code deployment.

## Good Practices

- Use clear naming conventions for flags that indicate purpose, scope, and ownership.

- Document each flag's purpose, owner, and expected lifespan to prevent orphaned flags.

- Set expiration dates for temporary flags to force consideration of the flag's lifecycle.

- Regularly audit and remove flags that have served their purpose to prevent technical debt.

- Test both states of each feature flag to maintain system reliability.

## Further Reading

* [Feature Toggles (Flags)](https://martinfowler.com/articles/feature-toggles.html) - Pete Hodgson's comprehensive guide to feature flags implementation and management
* [Release It!](https://pragprog.com/titles/mnee2/release-it-second-edition/) - Michael Nygard's book on designing and deploying production-ready software
* [Managing Feature Flags at Scale](https://www.infoq.com/presentations/github-feature-flags/) - GitHub's approach to managing feature flags at scale
* [Feature Flags: The Good, the Bad, and the Ugly](https://www.youtube.com/watch?v=r7VI5x2XKXw) - Real-world lessons from implementing feature flags
* [Progressive Delivery](https://www.split.io/blog/progressive-delivery-what-it-is-and-how-to-get-started/) - How feature flags enable progressive delivery approaches
