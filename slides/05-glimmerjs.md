## What is GlimmerJS?

Standalone UI Library<br>Announced at EmberConf 2017 (in May)

<a class="glimmer-video" href="http://www.youtube.com/watch?feature=player_embedded&v=i2rwIApjz-4
" target="_blank"><img src="http://img.youtube.com/vi/i2rwIApjz-4/0.jpg" 
alt="Glimmer Announcement Video" width="240" height="180" border="10" /></a>

<span class="small">https://www.youtube.com/watch?v=i2rwIApjz-4</span>

----

- Extracted from Ember's battle-tested rendering layer
- Small ui-component library
- Built by the Ember team, uses EmberCLI
- Part of the Ember ecosystem

Note:
- View layer only

----

## Glimmer Strengths 

- Small and fast for mobile web
- Simple to learn to use
- One of the [fastest](https://glimmerjs.com/demos/uptime-boxes/) JavaScript rendering engines

----

### GlimmerJS Standalone

 vs.
  
### Glimmer Rendering Engine<br>in Ember

----

### GOODBYE TAGNAME, ATTRIBUTEBINDINGS, ETC.

No more tagname, attributebindings, etc. in component's root elements

```
import Ember from 'ember';
   
export default Ember.Component.extend({
 tagName: 'input',
 attributeBindings: ['disabled', 'type:kind'],
 disabled: true,
 kind: 'range'
});
```

vs

```
<input disabled type="range" />
```

----

### ES6 Classes


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

vs

```
<input disabled type="range" />
```
```
import Component from '@glimmer/component';

export default class extends Component {
  type = 'primary'
}
```

----

### TypeScript

- Written in TypeScript, designed for JavaScript
  - Same API in TypeScript or JavaScript
- Using TypeScript is optional
<br><br>

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

```
import Component from '@glimmer/component';

export default class extends Component {
  firstName = "Katie";
  lastName = "Gengler";

  get fullName() {
    return `${this.firstName} ${this.lastName}`;
  }
}
```

Note:
simpler than Ember computed properties
can use standard getters/setters

----

### Decorators

```
import Component, { tracked } from '@glimmer/component';

export default class extends Component {
  @tracked firstName;
  @tracked lastName;

  @tracked('firstName', 'lastName')
  get fullName() {
    return `${this.firstName} ${this.lastName}`;
  }
}
```

Note:
Decorators are Stage 2 TC39 proposal

----

### Actions

Actions are just functions, with optional argument currying

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

### No `.get()` / `.set()`

Relies on ES5 getters/setters to intercept properties

Note:
common issue for new Ember users until they develop muscle memory

----

### File Size

- Ember criticized for large file sizes<br>typical hello world app ~200KB
- Production Angular, Ember and React apps<br>often run ~400KB to ~700KB or more

----

### File Size Compared
#### Hello World App

![glimmer file size compared](img/glimmer-file-size.png)

