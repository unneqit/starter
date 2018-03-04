### Install steps :

##### Basic configuration

```bash
cd dev
mkdir parcel-boilerplate
cd parcel-boilerplate
npm init
...
npm install -g parcel-bundler
mkdir -p src/styles/{components,global,mixins} && touch src/{index.html,index.js}
touch src/styles/styles.scss && touch src/styles/global/{_reset.scss,_variables.scss} && touch src/styles/mixins/_forsize.scss
#Close all instances of atom
atom .
#Edit package.json, index.html, index.js and the scss files
npm install
npm run start
```

##### Optional : install PostCSS and Babel

```bash
touch .postcssrc
npm install autoprefixer
npm install -D babel-preset-env
touch .babelrc
#Edit .postcssrc & .babelrc
```

##### Optional : install npm packages

```bash
npm install <package-name>
#Add import '<package-name>'; at the top of index.js
```

##### Optional : Create a github repository

```bash
git init
touch .gitignore
#Files to ignore :
#node_modules
#dist
#.DS_Store
git add .
git commit -m "Init starter"
git remote add origin <git-repository-link>
git push --set-upstream origin master
```

#### Files to edit

##### package.json

```json
{
  "name": "parcel-boilerplate",
  "version": "1.0.0",
  "description": "",
  "main": "src/index.js",
  "scripts": {
    "start": "parcel src/index.html",
    "build": "parcel src/index.js"
  },
  "author": "Quentin L.",
  "license": "ISC",
  "dependencies": {
    "autoprefixer": "^8.0.0",
    "flexboxgrid": "^6.3.1",
    "node-sass": "^4.7.2",
    "parcel-bundler": "1.6.2"
  },
  "devDependencies": {
    "babel-preset-env": "^1.6.1"
  }
}
```

###### index.html

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title></title>
</head>
<body>
  <script src="index.js"></script>
</body>
</html>
```

##### index.js

```javascript
import './styles/styles.scss';
```

##### styles.scss

```css
@import './global/reset';
@import './global/variables';
@import './mixins/forsize';
```

##### \_reset.scss

```scss
/* http://meyerweb.com/eric/tools/css/reset/
   v2.0 | 20110126
   License: none (public domain)
*/

html, body, div, span, applet, object, iframe, h1, h2, h3, h4, h5, h6, p, blockquote, pre, a, abbr, acronym, address, big, cite, code, del, dfn, em, img, ins, kbd, q, s, samp, small, strike, strong, sub, sup, tt, var, b, u, i, center, dl, dt, dd, ol, ul, li, fieldset, form, label, legend, table, caption, tbody, tfoot, thead, tr, th, td, article, aside, canvas, details, embed, figure, figcaption, footer, header, hgroup, menu, nav, output, ruby, section, summary, time, mark, audio, video {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  font: inherit;
  vertical-align: baseline; }

/* HTML5 display-role reset for older browsers */

article, aside, details, figcaption, figure, footer, header, hgroup, menu, nav, section {
  display: block; }

body {
  line-height: 1; }

ol, ul {
  list-style: none; }

blockquote, q {
  quotes: none; }

blockquote {
  &:before, &:after {
    content: '';
    content: none; } }

q {
  &:before, &:after {
    content: '';
    content: none; } }

table {
  border-collapse: collapse;
  border-spacing: 0; }
```

##### \_forsize.scss

```scss
@mixin for-size($range) {
  $phone-upper-boundary: $bp-tablet;
  $tablet-portrait-upper-boundary: $bp-desktop;
  $tablet-landscape-upper-boundary: $bp-desktop-large;
  $desktop-upper-boundary: $bp-desktop-x-large;

  @if $range == phone-only {
    @media (max-width: #{$phone-upper-boundary - 1}) { @content; }
  } @else if $range == tablet-portrait-up {
    @media (min-width: $phone-upper-boundary) { @content; }
  } @else if $range == tablet-landscape-up {
    @media (min-width: $tablet-portrait-upper-boundary) { @content; }
  } @else if $range == desktop-up {
    @media (min-width: $tablet-landscape-upper-boundary) { @content; }
  } @else if $range == big-desktop-up {
    @media (min-width: $desktop-upper-boundary) { @content; }
  }
}
```

##### \_styles.scss

```scss
@import './global/reset';
@import './global/variables';

@import './mixins/forsize';

@import './components/<filename>';
```

##### .postcssrc

```
{
  "plugins": {
    "autoprefixer": {
      "browsers": [">1%", "last 4 versions", "Firefox ESR", "not ie < 9"],
      "flexbox": "no-2009",
      "grid": true
    }
  }
}
```

##### .babelrc

```
{
  "presets": [
    ["env", {
      "targets": {
        "browers": ["last 2 versions", "safari >= 7"]
      }
    }]]
}

```
