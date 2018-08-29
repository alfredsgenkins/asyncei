# Asyncei

<div style="text-align: center">
<img height="257" src="https://svgshare.com/i/86T.svg">
<p>Pure JS, lighweight, asynchronous content loader</p>
</div>

## Install

```sh
npm install --save-dev asyncei
```

## Quick start

1. First, initialize Asyncei:

```javascript
import Asyncei from 'asyncei';
new Asyncei('/path/to/handler/');
```

2. Then, in your HTML do: 

```html
<div data-fetch="subpath/to/block"></div>
```

3. Watch your block loading asynchronous! 🎉

## API
### Customization

When initializing `Asyncei` three parameters may be set:

1. `handlerURL` – (required) URL for content loading handler.
2. `renderFunction` – Function to handle content rendering. 

Should take two params: `element` – DOM Element, and `text` – string of content. Default one is:

```javascript
(element, text) => {element.innerHTML = text}
```

3. `queryAttribute` – Attribute to query in search of loadable blocks. Default is `data-fetch`.

### Events

Each block load triggers custom event `blockContentLoaded`. Example:

```javascript
let example = document.getElementById('example-component');
example ? example.addEventListener('blockContentLoaded', () => onExampleLoad()) : null;
```

If all blocks queried on page are loaded, custom event `allBlocksLoaded` is triggered. Example:

```javascript
document.addEventListener('allBlocksLoaded', () => onAllLoaded());
```

## Demo

Find our demo here: [preload-demo repository](https://github.com/alfredsgenkins/preload-demo)
