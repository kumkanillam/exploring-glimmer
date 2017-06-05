## Ember

- Started life as SproutCore
- Yehuda Katz and Tom Dale co-founded it late 2011
- [Convention over Configuration](http://johnotander.com/ember/2015/02/03/convention-over-configuration/)
- Opting into community, not just framework

Note:
Convention over configuration is a software design paradigm 

- attempt to decrease the number of decisions that a developer is required to make 
- without necessarily losing flexibility
- introduced by David Heinemeier Hansson <br> re: Ruby on Rails web framework
- aka "sensible defaults" or "the principle of least astonishment"

In Ember:
- default project structure
- auto-lookup/wiring together of related code
- code generation

----

## Ember Philosophy and Design

- Focus on ambitious web applications
- More productive for developers out of the box
- Stability without stagnation
- Future web standards foresight

Note:
Why? Apply to Glimmer as well (2-4)

##### Focus on ambitious web applications
Ember sets out to **provide a wholesale solution** to the client-side application problem. This is in 
contrast to many JavaScript frameworks that start by providing a solution to the V in MVC 
(Model–View–Controller), and attempt to grow from there.

##### More productive out of the box
Ember is one component of a set of tools that work together to provide a complete development stack. 
The aim of these tools is to make the developer productive immediately. For example **Ember CLI**, 
provides a standard application structure and build pipeline. It also has a **pluggable architecture** 
and over thirty-five hundred addons to enhance and extend it.

##### Stability without stagnation
This is the idea that **backward compatibility** is important and can be maintained while still innovating 
and evolving the framework.

##### Future web standards foresight
Ember has been an **early adopter and pioneer of many standards** around JavaScript and the web 
including promises, web components and ES6 syntax. Yehuda Katz, one of Ember's cofounders, 
is a member on TC39, which is the committee responsible for future versions of the JavaScript language.

----

Ember Ecosystem / Software Stack

- Ember CLI <span class="small">(build tools)</span>
- Ember Data <span class="small">(data persistance library)</span>
- Ember Inspector <span class="small">(dev tools, browser addon)</span>
- Fastboot <span class="small">(server rendering)</span>
- Liquid Fire <span class="small">(animations)</span>

Note:
- CLI: standard project/file structure, dev server, testing framework, dependency management, ES6/ES7 support, asset management, code generation
- Data: Maps client-side models to server-side data, allowing load/save/etc without configuration via JSON API
- Inspector: Firefox/Chrome plugin to inspect internals of Ember apps
- Fastboot: Allows Ember apps to run through Node, outputing HTML/CSS for quick initial renders, while the JS loads in the background
- Liquid Fire: Animation support, uses jQuery library Velocity for smooth animations