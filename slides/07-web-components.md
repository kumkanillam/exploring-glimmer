## Web Components

Glimmer includes the ability to use<br>Glimmer components as web components

1. Include `<custom-component>` tag in HTML
2. Include the Glimmer JS bundle
3. Include Web Component shim (for now)

Note:
- Allows Glimmer components to be used anywhere
- Web Comp. tag could be rendered by server code

----

### Generate new app
#### as web component

```
ember new display-tile -b @glimmer/blueprint --web-component
```

```
<display-tile></display-title>
```

Note:
Currently cannot have self-closing web components

----

### Add to an existing app

```
npm install --save-dev @glimmer/web-component
```
```
yarn add --dev @glimmer/web-component
```

Add 2 lines to `src/index.ts`
```
  ...
+ import initializeCustomElements from '@glimmer/web-component';
  ...
  app.boot();
+ initializeCustomElements(app, [/* component names */]);
```

Note:
will register custom elements for each of the component names<br>
you give to initializeCustomElements,<br>
allow use as `<foo-bar></foo-bar>` anywhere in DOM, <br>
which will render Glimmer component

----

### Caveats / More Info

- Requires Web Component shim
- No self closing tags for web components
- Cannot pass arguments to top-level Glimmer components
  - Dev team is working to remove that limitation<br><br>

- More info
  - https://www.webcomponents.org/introduction
  - https://www.webcomponents.org/polyfills
  - http://jonrimmer.github.io/are-we-componentized-yet/
  
Note:
technical reasons

