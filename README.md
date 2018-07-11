[![Published on NPM](https://img.shields.io/npm/v/@polymer/iron-iconset.svg)](https://www.npmjs.com/package/@polymer/iron-iconset)
[![Build status](https://travis-ci.org/PolymerElements/iron-iconset.svg?branch=master)](https://travis-ci.org/PolymerElements/iron-iconset)
[![Published on webcomponents.org](https://img.shields.io/badge/webcomponents.org-published-blue.svg)](https://webcomponents.org/element/@polymer/iron-iconset)

## iron-iconset

The `iron-iconset` element allows users to define their own icon sets.  The
`src` property specifies the url of the icon image. Multiple icons may be
included in this image and they may be organized into rows.  The `icons`
property is a space separated list of names corresponding to the icons. The
names must be ordered as the icons are ordered in the icon image.  Icons are
expected to be square and are the size specified by the `size` property. The
`width` property corresponds to the width of the icon image and must be
specified if icons are arranged into multiple rows in the image.

All `iron-iconset` elements are available for use by other `iron-iconset`
elements via a database keyed by id. Typically, an element author that wants to
support a set of custom icons uses a `iron-iconset` to retrieve and use
another, user-defined iconset.

Example:

```html
<iron-iconset id="my-icons" src="my-icons.png" width="96" size="24"
    icons="location place starta stopb bus car train walk">
</iron-iconset>
```

This will automatically register the icon set "my-icons" to the iconset
database.  To use these icons from within another element, make a
`iron-iconset` element and call the `byId` method to retrieve a given iconset.
To apply a particular icon to an element, use the `applyIcon` method. For
example:

```javascript
iconset.applyIcon(iconNode, 'car');
```

Themed icon sets are also supported. The `iron-iconset` can contain child
`property` elements that specify a theme with an offsetX and offsetY of the
theme within the icon resource. For example.

```html
<iron-iconset id="my-icons" src="my-icons.png" width="96" size="24"
    icons="location place starta stopb bus car train walk">
  <property theme="special" offsetX="256" offsetY="24"></property>
</iron-iconset>
```

Then a themed icon can be applied like this:

```javascript
iconset.applyIcon(iconNode, 'car', 'special');
```

## Usage

### Installation

```
npm install --save @polymer/iron-iconset
```

### In an HTML file

```html
<html>
  <head>
    <script type="module">
      import '@polymer/iron-iconset/iron-iconset.js';
    </script>
  </head>
  <body>
    <iron-iconset id="my-icons" src="my-icons.png" width="96" size="24"
        icons="location place starta stopb bus car train walk">
    </iron-iconset>
  </body>
</html>
```

### In a Polymer 3 element

```js
import {PolymerElement} from '@polymer/polymer/polymer-element.js';
import {html} from '@polymer/polymer/lib/utils/html-tag.js';

import '@polymer/iron-iconset/iron-iconset.js';

class ExampleElement extends PolymerElement {
  static get template() {
    return html`
      <iron-iconset id="my-icons" src="my-icons.png" width="96" size="24"
          icons="location place starta stopb bus car train walk">
      </iron-iconset>
    `;
  }
}

customElements.define('example-element', ExampleElement);
```

## Contributing

If you want to send a PR to this element, here are the instructions for running
the tests and demo locally:

### Installation

```sh
git clone https://github.com/PolymerElements/iron-iconset
cd iron-iconset
npm install
npm install -g polymer-cli
```

### Running the demo locally

```sh
polymer serve --npm
open http://127.0.0.1:<port>/demo/
```

### Running the tests

```sh
polymer test --npm
```
