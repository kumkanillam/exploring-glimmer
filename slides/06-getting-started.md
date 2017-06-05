## Getting Started

Note: 
https://glimmerjs.com/guides

----

### Prerequisites
- Git
- Node.js / npm
- Yarn 

Note:
yarn - offers deterministic builds 
  - curious how npm 5.0 being released affects this?

----

### Installing EmberCLI Beta

```
yarn global add ember-cli@2.14.0-beta.1
```
```
npm install -g ember-cli@2.14.0-beta.1
```
<span class="small">Recommend using npm to install Ember CLI</span>

Verify the version, make sure it says `beta`
```
ember -v
```

Note: 
https://glimmerjs.com/guides/installing

- there have been issues with yarn global for EmberCLI install
- npm worked fine (maybe related to using NVM)

----

### Creating a New App

```
ember new my-app -b @glimmer/blueprint
```

![Glimmer install](img/glimmer-installation.png)

Note:
Can point at Glimmer Blueprint locally:
- clone https://github.com/glimmerjs/glimmer-blueprint 
- install glimmer blueprint dependencies (yarn/npm)
- ember new my-app -b [filepath to glimmer blueprint]

----

### Starting app

- `cd my-app`
- `ember serve`

----

### Filesystem Layout

![Glimmer install](img/glimmer-filesystem.png)

----

### Files

```
my-app/config/environment.js: the base Glimmer config file
my-app/config/*.ts: configuration files to keep Typescript happy 
    (ES2015 support coming) 
my-app/dist: your built files end up here
my-app/src/index.ts: used to do initial app config before our Glimmer app 
    boots (the div ID Glimmer renders into is set here (see the 
    containerElement variable))
my-app/ember-cli-build.js: used to configure Ember-CLI in various ways 
    (importing vendor files, Broccoli options, etc.)
```

----

### UI folder

Glimmer puts all folders in the<br>`my-app/src/ui/components` folder

- Main component: `my-app/`
  - JavaScript/Typescript: `my-app/components.ts`
  - Template: `template.hbs`
- Components can be nested

----

### Adding a Component

```
ember g glimmer-component hello-glimmer
```

![new glimmer compoment](/img/glimmer-component.png)

----

![filesystem after new compoment](/img/glimmer-filesystem-new-component.png)

----

### Nested Sub-Component

```
ember g glimmer-component conference-speakers
ember g glimmer-component conference-speakers/conference-speaker
```

- component-lookup uses local resolution
- conference speaker is only usable inside<br>conference-speakers template
- not available at the top level

----

![filesystem nested compoment](/img/glimmer-filesystem-nested.png)

----

### Styles

- Works with both CSS or SCSS file
  - Main app styles file generated:<br>`src/ui/styles/app.scss`

Note:
Would personally put each component's styles in the component folder
and reference it from the main `app.scss` file

----

### Templates and Helpers

- Templates use Handlebars syntax
- loops, conditionals and event handlers

```
import Component from "@glimmer/component";

export default class ConferenceSpeakers extends Component {
  speakers = ['Tom', 'Yehuda', 'Ed'];
}
```

```
<ul>
  {{#each speakers key="@index" as |speaker|}}
    <li>{{speaker}}</li>
  {{/each}}
</ul>
```

Note:
@index is a special case, not a component argument, is 
something that is being discussed

----

### Components

- Components use angle-bracket notation in templates

```
<hello-glimmer />
<conference-speakers></conference-speakers>
```

Note:
Ember uses {{ }} (double curly braces) for components

----

### Data in Templates

- Arguments
- Properties

Note:
Arguments are data that are passed in
Properties are internal to the component, declared in the class

----

### Argument Syntax
#### Data passed into a component

In another component
```
<conference-speaker @name="Mike" @status="Speaking" />
```

Inside the template
````
{{@name}} is {{@status}}
````

In the component code
```
console.log(this.args.name); // prints "Mike"
```

----

### Properties Syntax
### Data internal to component

In component
```
import Component from '@glimmer/component';

export default class ConferenceSpeaker extends Component {
  user = {
    name: 'Robbie'
  };
}
```

In template or passed to another component
```
Hello, {{user.name}}!

<conference-speaker @name={{user.name}} />
```

----

#### Arguments vs. Properties

- Can always tell the difference
- Always know at a glance where data is from
- Arguments will always start with an `@`

```
{{@name}}
```

vs.

```
{{firstName}}
```

----

### Components and Actions

![component templates](/img/component-template.png)

Note:
- {{if}}/{{else}} and {{action}} helpers
- {{action}} helper to call our next() method/event handler
- `get` in front of `currentlySpeaking()` defines a property for template
- @tracked - functions will re-run when `current` changes

----

### Lifecycle Hooks

- didInsertElement
- didRender
- didUpdate
- willDestroy

```
import Component from '@glimmer/component';

export default class extends Component {
  didInsertElement() {
    $(this.element).pickadate();
  }
}
```

Note:
Only `didInsertElement` currently implemented

----

### Tracked Properties
#### Change Tracking

- **Rule #1**
  - Tracked Properties are immutable by default
  - Allows Glimmer to skip expensive change tracking

- **Rule #2**
  - Any component property that changes after render<br>must be marked with `@tracked` decorator

----

### Immutable Pattern

1. Save component state object in a tracked property
2. To change state, replace the state object with a new copy

```
import Component, { tracked } from "@glimmer/component";

export default class extends Component {
  @tracked state = {
    firstName: "Lady",
    lastName: "Zahra"
  }

  setUserFirstName(firstName) {
    this.state = {
      ...this.state,
      firstName
    }
  }
}
```
  
----

### Change Detection: Why Tracked Properties

- Approaches
  - Property Observation (i.e. Ember 1.x)
  - Virtual DOM diffing (i.e. React)

- Optimizing Virtual DOM
  - As virtual DOM app grows, will take more work to stay performant
  - React uses `shouldComponentUpdate` hook
  
Note:
- prop observation - usually **slow initial render** performance
- Virtual DO - prioritize **raw render speed**
  
----

### Change Detection: Glimmer

- rendering primitive is the value, not component
- allows Glimmer to construct<br>`shouldComponentUpdate` hook automatically

<span class="small">More info:</span><br>
<span class="small">[Tracked Properties](https://glimmerjs.com/guides/tracked-properties)</span>





