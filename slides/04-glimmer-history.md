## Glimmer History
### The view layer in Ember

----

## Glimmer Origins?

- Original rendering engine inside of Ember was Handlebars

https://gist.github.com/GavinJoyce/e6e0cc4fedbcf96d39267e59ba85472c

Note:
Handlebars = basic string concatenation

----

### Handlebars

    <h1>Hello {{environment}}</h1>

----

### Why a new rendering engine?

- Rendering Performance
- Data Down, Actions Up
- FastBoot


```
{{#each envs as |env|}} Hello {{env}} {{/each}}
```	


Note:
Ember string-based templating was slow with lots of objects
Data down, Actions up better way to describe *unidirectional data flow*
Original Sproutcore/Ember view engine: Regex string-based templating via Handlebars

----

### Pressure from React
#### Better, more performant change detection

----

### Types of change detection

- Mutation checking (Ember)
- Dirty Checking (AngularJS)
- Manual Notification (React)

Note: 
- Mutation checking: framework is told when something changed
- Dirty checking: process of looping to check every scope variable to detect the changes, update DOM as changes found, re-loop
- Manual Notification: tell framework when it should check for updates

----

### Glimmer v1.0 - HTMLBars
#### Replaced the original SproutCore view engine

- released with Ember v1.13
- Rendering engine for HTMLBars templates
  - Declarative syntax differentiates between static vs dynamic areas
  - Only needs to re-render dynamic areas
- Glimmer diffs tree of values, not (virtual) DOM tree
- Very fast for updates and re-renders

Note: 
- Not as good for initial renders
- Significantly improved re-render performance

Glimmer 1 released Summer 2015

----

### Glimmer v2.0 
- released with Ember v2.10
  - forked from HTMLBars
- much faster and smaller
  - particularly noticable for initial render
  - 30-40% decrease in file sizes
  - performance improvements - 1.5x to 1.75x

  
Note:

Glimmer 2 released November 2016

----

### Glimmer v2.0

- Templates compile to data arrays of opcodes at build time
- No JavaScript to execute, just data, faster to parse
- Built in TypeScript
- Compiler implements 2 custom virtual machines
  - DOM Appending VM
  - DOM Updating VM

Note:
Definitions

- Compiler - converts instructions into computer-executable instructions
- Virtual Machine - program that runs other programs

----


![Glimmer2 Opcodes](img/glimmer2-opcodes.png) 