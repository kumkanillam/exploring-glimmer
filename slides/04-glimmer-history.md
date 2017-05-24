## Glimmer History
### The view layer in Ember

----

## What Was Glimmer?

- The rendering engine inside of Ember
- React had demonstrated the power of Virtual DOM
- Glimmer diffs values, not DOM
- Differentiates between dynamic and static areas, <br>only needing to re-render dynamic areas

----

### Built to replace the original SproutCore view engine
- built on top of HTMLBars - Ember v1.13
  - Declarative syntax differentiates between static vs dynamic areas (HandleBars)
  - Significantly improved re-render performance

----

### Glimmer v2.0 
- released with Ember v2.10
  - 30-40% decrease in file sizes
  - performance improvements - 1.5x to 1.75x