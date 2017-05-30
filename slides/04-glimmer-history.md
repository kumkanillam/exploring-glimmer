## Glimmer History
### The view layer in Ember

----

## Glimmer Origins?

- Original templating engine inside of Ember was Handlebars
- Angular was struggling with dirty-checking
- React had demonstrated the power of Virtual DOM

Note:
Original Sproutcore/Ember view engine: Regex string-based templating via Handlebars
Dirty checking: process of looping to check every scope variable to detect the changes, update DOM as changes found, re-loop

----

### Replaced the original SproutCore view engine

- built on top of HTMLBars - Ember v1.13
  - Declarative syntax differentiates between static vs dynamic areas (HandleBars)
  - Significantly improved re-render performance
- Glimmer diffs values, not DOM
- Differentiates between dynamic and static areas, <br>only needing to re-render dynamic areas

Note: 
Glimmer 1 released Summer 2015

----

### Glimmer v2.0 
- released with Ember v2.10
  - 30-40% decrease in file sizes
  - performance improvements - 1.5x to 1.75x