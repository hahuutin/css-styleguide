# CSS/SASS coding style guide


## Table of contents

1. [CSS](#css)

    + [Whitespace](#whitespace)
    + [Comments](#comments)
    + [Naming Conventions](#naming-conventions)
    + [Formatting](#formatting)
    + [Declaration order](#declaration-order)

2. [SASS](#sass)

    + [Syntax](#syntax)
    + [Ordering](#ordering)
    + [Vendor Prefixes](#vendor-prefixes)
    + [Variables](#variables)
    + [Mixins](#mixins)
    + [Nested Selectors](#nested-selectors)

3. [References](#references)


## CSS


### Whitespace

Only one style should exist across the entire source of your code-base. Always be consistent in your use of whitespace. Use whitespace to improve readability.

+ Never mix spaces and tabs for indentation.
+ Choose between soft indents (spaces) or real tabs. Stick to your choice without fail. (Preference: spaces)
+ If using spaces, choose the number of characters used per indentation level. (Preference: 4 spaces)

_Tip: configure your editor to "show invisibles" or to automatically remove end-of-line whitespace._

_Tip: use an [EditorConfig](http://editorconfig.org/) file (or equivalent) to help maintain the basic whitespace conventions that have been agreed for your code-base._


### Comments

Prefer comments on their own line. Avoid end-of-line comments.

Code is written and maintained by people. Ensure your code is descriptive, well commented, and approachable by others. Great code comments convey context or purpose. Do not simply reiterate a component or class name.

Be sure to write in complete sentences for larger comments and succinct phrases for general notes.

``` css
/* Bad */
/* Modal header */
.modal-header {
    ...
}

.selector {
    color: #000; /* Go to comment here */
}

/* Good */
/* Wrapping element for .modal-title and .modal-close */
.modal-header {
    ...
}
```


### Naming Conventions

Keep classes or IDs lowercase and use dashes (not underscores or camelCase).

``` css
/* Bad */
.selector_name {
    ...
}
.selectorName {
    ...
}

/* Good */
.selector-name {
    ...
}
```

Besides, you can looking at the [BEM](http://bem.info/) namespaces.
The most important thing is that you pick one as a team and stick with it

### Formatting

##### Use one discrete selector per line in multi-selector rulesets.

``` css
/* Bad */
.selector-1, .selector-2 {
    ...
}

/* Good */
.selector-1,
.selector-2 {
    ...
}
```

##### Include a single space before the opening brace of a ruleset.

``` css
/* Bad */
.selector{
    ...
}

/* Good */
.selector {
    ...
}
```

##### Include one declaration per line in a declaration block.

```css
/* Bad */
.selector {
    width: 100px; height: 100px;
}

/* Good */
.selector {
    width: 100px;
    height: 100px;
}
```

##### Include a single space after the colon of a declaration.

``` css
/* Bad */
.selector {
    width:100px;
}

/* Good */
.selector {
    width: 100px;
}
```

##### Use lowercase and shorthand hex values

``` css
/* Bad */
.selector {
    color: #FFFFFF;
}

/* Good */
.selector {
    color: #fff;
}
```

##### Use single or double quotes consistently. Preference is for double quotes

``` css
/* Bad */
.selector {
    content: "";
}

.input[type='text'] {
    ...
}
/* Good */
.selector {
    content: "";
}

.input[type="text"] {
    ...
}
```

##### Quote attribute values in selectors.

``` css
/* Bad */
input[type=text] {
    ...
}

/* Good */
input[type="text"] {
    ...
}
```

##### Where allowed, avoid specifying units for zero-values. Exception, where you don't omit `transform: rotate(0deg)`

``` css
/* Bad */
.selector {
    margin: 0px;
}

/* Good */
.selector {
    margin: 0;
}
```

##### Don't prefix property values or color parameters with a leading zero

``` css
/* Bad */
.selector {
    transition: all 0.3s ease;
    color: rgba(0,0,0,0.5);
}

/* Good */
.selector {
    transition: all .3s ease;
    color: rgba(0,0,0,.5);
}
```

##### Include a space after each comma in comma-separated property or function values.

``` css
/* Bad */
.selector {
    box-shadow: 0px 1px 2px rgba(0,0,0,0.5),inset 0 1px 0 #fff;
}

/* Good */
.selector {
    box-shadow: 0px 1px 2px rgba(0, 0, 0, 0.5), inset 0 1px 0 #fff;
}
```

##### Include a semi-colon at the end of the last declaration in a declaration block.

``` css
/* Bad */
.selector {
    color: #fff
}

/* Good */
.selector {
    color: #fff;
}
```

##### Place the closing brace of a ruleset in the same column as the first character of the ruleset.

``` css
/* Bad */
.selector-1 {
    ... }

.selector-2 {
    ...
    }

/* Good */
.selector {
    ...
}
```

##### Separate each ruleset by a blank line.

``` css
/* Bad */
.selector-1 {
    ...
}
.selector-2 {
    ...
}

/* Good */
.selector-1 {
    ...
}

.selector-2 {
    ...
}
```

##### Avoid dangerous selectors

``` css
/* Bad */
header {
    ...
}
h2 {
    ...
}

/* Good */
.header {
    ...
}
.title {
    ...
}
```

##### Avoid qualifying class names with element selectors

``` css
/* Bad */
ul.list {
    ...
}
h3.title {
    ...
}

/* Good */
.list {
    ...
}
.title {
    ...
}
```

##### Avoid deep nesting. You should also try to nest your selectors maximum 3 levels deep

``` css
/* Bad */
.container .linklist li a {
    ...
}

/* Good */
.container .linklist a {
    ...
}
```

##### Avoid using the same selector for styling and JS

__Bad__

``` css
.dialog-opener {
    ...
}
```
``` javascript
$('.dialog-opener')
```

__Good__

``` css
.dialog-opener {
    ...
}
```
``` javascript
$('.js-dialog-opener')
```

##### Use shorthand properties where possible

``` css
/* Bad */
.selector {
    padding-top: 0;
    padding-right: 10px;
    padding-bottom: 20px;
    padding-left: 10px;
}

/* Good */
.selector {
    padding: 0 10px 20px;
}
```

##### Use hexadecimal color codes unless using rgba or hsl or name

``` css
/* Bad */
.selector {
    color: orange;
}

/* Good */
.selector {
    color: #ffa500;
}
```

##### Use number keywords 100–900 for font-weight

``` css
/* Bad */
.selector {
    font-weight: normal;
}

/* Good */
.selector {
    font-weight: 400;
}
```

### Declaration order

Related property declarations should be grouped together following the order:

1. Positioning
2. Box model
3. Typographic
4. Visual

``` css
.declaration-order {
    /* Positioning */
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 100;

    /* Box-model */
    display: block;
    float: right;
    width: 100px;
    height: 100px;

    /* Typography */
    font: normal 13px "Helvetica Neue", sans-serif;
    line-height: 1.5;
    color: #333;
    text-align: center;

    /* Visual */
    background-color: #f5f5f5;
    border: 1px solid #e5e5e5;
    border-radius: 3px;

    /* Misc */
    opacity: 1;
}
```


## SASS

Beside follow as style guide of css. In Sass, I have added some style guides for them.


#### Syntax

Should use SCSS-syntax because it's valid CSS and more expressive in our eyes.

``` sass
// Not prefer
.selector-parent
    color: #fff
    background-color: #000

    .selector-child
        font-size: 20px
```

``` scss
// Prefer
.selector-parent {
    color: #fff;
    background-color: #000;

    .selector-child {
        font-size: 20px;
    }
}
```


#### Ordering

+ List $variable should always appear at the top
+ List @extend(s) next
+ List @include(s) next
+ List regular style next
+ List your media queries next
+ Nested pseudo classes and pseudo elements next
+ Nested selectors last

``` scss
.block {
    $background: #fff;
    $background-hover: #f00;

    @extend %module;
    @include transition(all 0.3s ease);
    background: $background;

    @include breakpoint(phone) {
        width: 100%;
    }

    &:hover {
        background: $background-hover;
    }

    &::before {
        content: "";
        display: block;
    }

    h3 {
        @include transform(rotate(90deg));
        border-bottom: 1px solid #fff;
    }
}
```


#### Vendor Prefixes

Never Write Vendor Prefixes. You should use [Autoprefixer](https://github.com/postcss/autoprefixer) instead of. Autoprefixer parses CSS files and adds vendor prefixes to CSS rules using the Can I Use database to determine which prefixes are needed.


#### Variables

_Updating..._


#### Mixins

_Updating..._


#### Nested Selectors

Do not nest selectors more than three levels deep!

``` scss
.page-container {
    .content {
        .profile {
            // STOP!
        }
    }
}
```


### References

+ [Principles of writing consistent, idiomatic CSS.](https://github.com/necolas/idiomatic-css)
+ [Airbnb - A mostly reasonable approach to CSS and Sass.](https://github.com/airbnb/css)
+ [High-level advice and guidelines for writing sane, manageable, scalable CSS](http://cssguidelin.es/)
+ [Github Style Guide](http://primercss.io/)
+ [Google Style Guide](https://google.github.io/styleguide/htmlcssguide.xml)
+ [Code Guide by @mdo](http://codeguide.co/#html)
+ [Some HTML, CSS and JS best practices](https://github.com/bendc/frontend-guidelines)
+ [Isobar Front-end Code Standards](http://isobar-idev.github.io/code-standards/)
+ [Principles for writing consistent, clean, friendly Sass](https://github.com/anthonyshort/idiomatic-sass)
+ [CSSTricks - Sass style guide](https://css-tricks.com/sass-style-guide/)
+ [HTML/CSS coding style](http://csswizardry.com/2012/04/my-html-css-coding-style/)
+ [Improving Code Readability With CSS Styleguides](https://www.smashingmagazine.com/2008/05/improving-code-readability-with-css-styleguides/)
+ [ThinkUp - Code Style Guide CSS](https://github.com/ThinkUpLLC/ThinkUp/wiki/Code-Style-Guide%3A-CSS)