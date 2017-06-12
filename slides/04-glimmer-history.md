## Glimmer History
### The view layer in Ember

----

## Glimmer Origins?

Original rendering engine inside of Ember was Handlebars


#### Handlebars

    <h1>Hello {{environment}}</h1>

Note:
https://gist.github.com/localpcguy/c70cbd78b40fa34310acf8ceb0718759

Handlebars = basic string concatenation

----

### Why a new rendering engine?

```
{{#each envs as |env|}} Hello {{env}} {{/each}}
```	

- Rendering Performance was bad
- Wanted Data Down, Actions Up
- Server rendering was impractical


Note:
Ember string-based templating was slow with lots of objects
Data down, Actions up better way to describe *unidirectional data flow*
Original Sproutcore/Ember view engine: Regex string-based templating via Handlebars

----

### Pressure from React
#### Better, more performant change detection

Note:
- React open-sourced 2013 (JSConf)
- React rendering was really fast
- Virtual DOM was better

----

### Types of change detection

- Mutation checking (Ember)
- Dirty Checking (AngularJS)
- Zones/Observables (Angular)
- Manual Notification (React)

<span class="small">https://auth0.com/blog/glossary-of-modern-javascript-concepts-part-2/#change-detection</span>

Note: 
- Mutation checking: framework is told when something changed
- Dirty checking: process of looping to check every scope variable to detect the changes, update DOM as changes found, re-loop
- Zones/Observables
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

- more about values vs. VirtualDOM:<br>basically Glimmer looks at values (not DOM) & <br>when they change, triggers re-render
- Not as good for initial renders
- Did significantly improved re-render performance

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