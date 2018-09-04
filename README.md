# Asyncei

<p align="center">
    <img height="257" src="https://user-images.githubusercontent.com/29531824/45020709-65f4cf80-b038-11e8-944c-5c337fb57ce4.png">
    <p align="center">Pure JS, lighweight, asynchronous content loader</p>
</p>

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

## How it works?

1. Asyncei queries page in the lookup for specified attribute;
2. Fetches all found urls asynchronously;
3. Fetches images in each loaded content block;
4. Dispatches `blockContentLoaded` event, on the load of the a block;
5. After all blocks are loaded dispatches `allBlocksLoaded` event;

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
