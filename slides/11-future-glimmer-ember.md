## Is Ember Dead?
### Does Glimmer "Kill" Ember?

----

## NO


----

### GlimmerVM Extracted

- GlimmerVM extracted to be used outside of Ember
  - GlimmerVM will now have 2 consumers, Ember and Glimmer
  - Allows for quicker experimentation and iteration

----

#### Questions

1. Why release a standalone rendering framework?
2. Does Glimmer create a "brain-drain" on Ember?
3. Will there be 2 component APIs forever?

Notes:
1. Glimmer appeals to more people than Ember, easy on-ramp to Ember
2. proving ground for Ember itself, actively updating Ember to work with GlimmerVM<br>while gaining feedback in "wild"
3. Ember team focused on adding the Glimmer component API, decisions on existing API still to be made

----

#### npm your way to Ember

Goal is that Glimmer users can upgrade to Ember over time

<img class="no-border" alt="glimmer to ember" src="img/glimmer-to-ember.png" />

#### Start small, build big

----

### Experimentation

- Allows Ember team to experiment and get quick feedback 
  - Angle bracket components
  - Module Unification
  - New Dependency Injection system
  - Autotracking

Note:
Things that Ember users have been wanting for some time

autotracking - don't need to declare computed properties anymore