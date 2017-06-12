
## What is GlimmerJS?

Standalone UI Library<br>Announced at EmberConf 2017 (in May)

<a class="glimmer-video" href="http://www.youtube.com/watch?feature=player_embedded&v=i2rwIApjz-4
" target="_blank"><img src="http://img.youtube.com/vi/i2rwIApjz-4/0.jpg" 
alt="Glimmer Announcement Video" width="240" height="180" border="10" /></a>

<span class="small">https://www.youtube.com/watch?v=i2rwIApjz-4</span>

----

### GlimmerJS

- Extracted from Ember's rendering layer
- Small ui-component library
- Built by the Ember team, uses EmberCLI
- Part of the Ember ecosystem

Note:
- battle-tested 
- View layer only

----

## Glimmer Strengths 

- Simple to learn to use
- Simple composable components
- Small and fast, great for mobile web
- One of the [fastest](https://glimmerjs.com/demos/uptime-boxes/) JavaScript rendering engines

----

### Glimmer Rendering Engine<br>in Ember

 vs.
  
### GlimmerJS Standalone

----

### GOODBYE TAGNAME, ATTRIBUTEBINDINGS, ETC.

No more tagname, attributebindings, etc. in component's root elements

<span class="language">Glimmer</span>
```
<input disabled type="range" />
```
<hr>
<span class="language">Ember</span>
```
import Ember from 'ember';
   
export default Ember.Component.extend({
 tagName: 'input',
 attributeBindings: ['disabled', 'type:kind'],
 disabled: true,
 kind: 'range'
});
```

----

### ES6 Classes

<span class="language">Glimmer</span>
```
<input disabled type="range" />
```
```
import Component from '@glimmer/component';

export default class extends Component {
  type = 'primary'
}
```
<hr>
<span class="language">Ember</span>
```
import Ember from 'ember';

export default Ember.Component.extend({
  tagName: 'input',
  attributeBindings: ['disabled', 'type:kind'],
  disabled: false,
  kind: 'range',
  classNameBindings: 'type',
  type: 'primary'
});
```

----

### TypeScript

- Written in TypeScript, designed for JavaScript
  - Same API in TypeScript or JavaScript
- Using TypeScript is optional<br>

<span class="language">Glimmer</span>
```
import Component from '@glimmer/component';
export default class extends Component {
  firstName: string;
  lastName: string;
}
```

Note:
TypeScript is another tool you can use, not one you have to

----

### Computed Properties

<span class="language">Glimmer</span>
```
import Component from '@glimmer/component';

export default class extends Component {
  firstName = 'Katie';
  lastName = 'Gengler';
  
  get fullName() {
    return `${this.firstName} ${this.lastName}`;
  }
}
```
<hr>
<span class="language">Ember</span>
```
import Ember from 'ember';

export default Ember.Component.extend({
  firstName: 'Katie',
  lastName: 'Gengler',
  
  fullName: Ember.computed(function() {
    return `${this.get('firstName')} ${this.get('lastName'}`;
  })
});
```

Note:
simpler than Ember computed properties
can use standard getters/setters

----

### No `this.get()` / `this.set()`

Relies on ES5 getters/setters to intercept properties

<span class="language">Glimmer</span>
```
import Component from '@glimmer/component';

export default class extends Component {
  // ...
  get fullName() {
    return `${this.firstName} ${this.lastName}`;
  }
}
```
<hr>
<span class="language">Ember</span>
```
import Ember from 'ember';

export default Ember.Component.extend({
  // ...
  fullName: Ember.computed(function() {
    return `${this.get('firstName')} ${this.get('lastName'}`;
  })
});
```

Note:
get/set common issue for new Ember users until they develop muscle memory

----

### Decorators

Declarative syntax to modify the shape of class declarations

<span class="language">Glimmer</span>
```
import Component, { tracked } from '@glimmer/component';

export default class extends Component {
  // ...
  @tracked('firstName', 'lastName')
  get fullName() {
    return `${this.firstName} ${this.lastName}`;
  }
}
```
<hr>
<span class="language">Ember</span>
```
import Ember from 'ember';

export default Ember.Component.extend({
  // ...
  fullName: Ember.computed('firstName', 'lastName', function() {
    return `${this.get('firstName')} ${this.get('lastName'}`;
  })
});
```

Note:
Decorators are Stage 2 TC39 proposal

----

### Actions

Actions are just functions

<span class="language">Glimmer</span>
```
import Component, { tracked } from '@glimmer/component';

export default class extends Component {
  @tracked name: string;

  setName(name: string) {
    this.name = name;
  }
}
```
```
<button onclick={{action setName "Zahra"}}>
  Change Name
</button>
```

----

### File Size

- Ember criticized for large file sizes<br>typical hello world app ~200KB
- Production Angular, Ember and React apps<br>often run ~400KB to ~700KB or more

----

### File Size Compared
#### Hello World App

![glimmer file size compared](img/glimmer-file-size.png)

Note:
- preact
- glimmer
- vue.js
- react
- Angular 
- Ember
