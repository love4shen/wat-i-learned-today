# wat i learned today

## 04/24/2016
* The operand of `yield*` does not have to be a generator object, it can be any iterable
* `next()` is asymmetric, but that can’t be helped: It always sends a value to the currently suspended yield, but returns the operand of the following yield.

When using a generator as an observer, it is important to note that the only purpose of the first invocation of `next()` is to start the observer. It is only ready for input afterwards, because this first invocation advances execution to the first yield. Therefore, any input you send via the first next() is ignored:

```javascript
function* gen() {
    // (A)
    while (true) {
        const input = yield; // (B)
        console.log(input);
    }
}
const obj = gen();
obj.next('a');
obj.next('b');

// Output:
// b
```

* `regex.source`
* `regex.flags`

## 04/20/2016
* `::first-letter { initial-letter: 3 2; }`[Better CSS Drop Caps With “initial-letter](http://webdesign.tutsplus.com/tutorials/better-css-drop-caps-with-initial-letter--cms-26350)

[CSS, animation] only animate transforms (translate, rotate, scale) and opacity, absolutely positioned elements: does not repaint

FLIP stands for First, Last, Invert, Play

Attribute order
HTML attributes should come in this particular order for easier reading of code.

class
id, name
data-*
src, for, type, href, value
title, alt
role, aria-*

Classes make for great reusable components, so they come first. Ids are more specific and should be used sparingly (e.g., for in-page bookmarks), so they come second.

Don't include spaces after commas within rgb(), rgba(), hsl(), hsla(), or rect() values

Don't prefix property values or color parameters with a leading zero (e.g., .5 instead of 0.5 and -.5px instead of -0.5px).

Lowercase all hex values, e.g., `#fff`

Quote attribute values in selectors, e.g., `input[type="text"]`.


Declaration order: Positioning, Box model, Typographic, Visual, e.g.

```
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

========================

.element { ... }
.element-avatar { ... }
.element-selected { ... }

@media (min-width: 480px) {
  .element { ...}
  .element-avatar { ... }
  .element-selected { ... }
}

========================

If you want to hide content from mobile and tablet users as well as assistive tech users and keyboard only users, use the title attribute.

Whenever a function is called, we must look at the immediate left side of the brackets / parentheses. If on the left side of the parentheses we can see a reference, then the value of `this` passed to the function call is exactly of which that object belongs to, otherwise it is the global object.

When call `flux.addEventListener("click", marty.timeTravel)`, a reference to `marty.timeTravel` was saved as our event handler and is being invoked, but not from the owning marty object

```
!function(){}();  // => true
~function(){}(); // => -1
+function(){}(); // => NaN
-function(){}();  // => NaN
```

NOTE: always include semicolon, or at the beginning
https://github.com/airbnb/javascript/issues/21#issuecomment-10203921

```
button.addEventListener('click', function(event) {
  form.requestAutocomplete();
  event.preventDefault();
});
```

signs are classified into three categories:
iconic: relate to the concept through resemblance
symbolic: relate to the concept through convention, and
indexical: relate to the object through causation

5 Questions Every Unit Test Must Answer:
What are you testing?
What should it do?
What is the actual output?
What is the expected output?
How can the test be reproduced?
https://medium.com/javascript-scene/what-every-unit-test-needs-f6cd34d9836d#.h3i0qbho0

```
console.table()
```

`:empty` pseudo selector: This convenient pseudo selector will match elements with no children.

<picture> requires <img> as its last child

Avoiding anonymous JavaScript functions

```
(function (window, document, undefined) {
  'use strict';
// ...
})(window, document);
```

`calc()`: There must be spaces surrounding the math operator

Prepare svg for icon

Select all
Object -> Ungroup
Path -> Union
Path -> Combine
File -> Vacuum Defs (or Clean up document)
Save as -> Plain SVG

The `:target` pseudo-class represents the unique element, if any, with an id matching the fragment identifier of the URI of the document..

IndexedDB is built on a transactional database model

indexDB: error events bubble. Error events are targeted at the request that generated the error, then the event bubbles to the transaction, and then finally to the database object

Aria tooltip w/o js:

Combined with aria-describedby:
input:focus + [role="tooltip"] {
	display: block;
	position: absolute;
	top: 100%;
}

The aria-live="assertive" attribute means that the value of the text field will be spoken whenever it changes

The aria-controls attribute just confirms that each button controls the input

both in node and in a browser using `this` in a function that is not called with new references the global scope

[[Prototype]] is an inheritance relationship between objects, while prototype is a normal property whose value is an object. The property prototype is only special w.r.t. the new operator using its value as the prototype for instances it creates.

The prototype of a subclass is the superclass

In a derived class, you must call super() before you can use this

you can override the result of a constructor by explicitly returning an object


Modules are singletons. Even if a module is imported multiple times, only a single “instance” of it exists

Module imports are hoisted

There are only two ways to combine these styles and the order in which they appear is fixed; the default export always comes first.

Combining a default import with a namespace import:
  import theDefault, * as my_lib from 'src/my_lib';
Combining a default import with named imports
  import theDefault, { name1, name2 } from 'src/my_lib';

`Array.from(arrayLike, mapFunc?, thisArg?)`

## 04/07/2016
* [CSS in JS](http://blog.vjeux.com/2014/javascript/react-css-in-js-nationjs.html)

## 03/22/2016
* a negative animation delays starts the animation immediately, as if that amount of time has already gone by

## 03/21/2016
* [clojure]
  * `(doc name)`, `(find-doc name)`, `(source name)`
  * `peek`, `pop`: list like stack
  * `asssoc`, `dissoc`: replace/append/error or remove on vector
  * `conj`, `disj`: add or remove one or more item
  * `get-in`, `assoc-in`: get or set the value of the nested map key
  * `(f1 (f2 (f3 x))) == (-> x f3 f2 f1`
* [clojure] `binding` macro gives new, thread-local values to exisitying global bindings throughout the scope's thread execution
* [clojure] coordinates: multiple pieces of shared data

`ref` | `atom` | `agents`
--- | --- | ---
sync, coord, STM | sync, non-coord | async, non-coord

* `content: attr(data-label)`
* pre-cache

```
function preCacheHeros(){
    for(i = 0; i < heroArray.length; i++){
        var url = heroArray[i],
            img = new Image();

        img.src = url;
    };
};

window.onload = preCacheHeros();
```

* `sandbox` attr of `<iframe>` to control permission
  * allow-forms allows form submission.
  * allow-popups allows popups (window.open(), showModalDialog(), target=”_blank”, etc.).
  * allow-pointer-lock allows pointer lock.
  * allow-same-origin allows the document to maintain its origin; pages loaded from https://example.com/ will retain access to that origin’s data.
  * allow-scripts allows JavaScript execution, and also allows features to trigger automatically
  * allow-top-navigation allows the document to break out of the frame by navigating the top-level window.

* events are great for things that can happen multiple times on the same object — keyup, touchstart etc. With those events you don't really care about what happened before you attached the listener; Promises are for async success/failure [JavaScript Promises](http://www.html5rocks.com/en/tutorials/es6/promises/)

* [js] `Promise.resolve` creates a promise that resolves to whatever value you give it

    * [git] delete obsolete branches: `git branch --merged | xargs git branch -d` or github pr
* [git] `grep` in all commits: `git rev-list --all | xargs git grep ${REGEX}`

## 03/16/2016
* We can apply regular typography-related styling to the `<img>` element. These styles will be applied to the alternative text, if it is displayed, and will not affect the working image.

* The `<img>` element is a replaced element. This is an element “whose appearance and dimensions are defined by an external resource” (Sitepoint). Because the element is controlled by an external source, the `:before` and `:after` pseudo-elements typically shouldn’t work with it. However, when the image is broken and not loaded, these pseudo-elements can appear. (with browser compatibility issue)

## 03/09/2016
* `getElementsByClassName` can takes multiple class names as a single string as argument

## 03/08/2016
* consider adding `humans.txt` to site by
  1. create `humans.txt` file
  2. add `<link rel="author" href="humans.txt" />`

  template for `humans.txt`:

```
/* TEAM */
Your title: Your name.
Site: email, link to a contact form, etc.
Twitter: your Twitter username.
Location: City, Country.

[...]

/* THANKS */
Name: name or url

[...]

/* SITE */
Last update: YYYY/MM/DD
Standards: HTML5, CSS3,..
Components: Modernizr, jQuery, etc.
Software: Software used for the development
```

## 03/07/2016
＊ NoSQL comes from twitter hashtag #NOSQL

## 03/06/2016
* paragraph style stolen from somewhere

```
font-size: 1 rem;
line-height: 1.75;
word-spacing: -1px;
-webkit-font-smoothing:antialiased;
color: #333;
max-width: 835px;
```

## 03/04/2016
* the first element inside the `fieldset` must be a `legend` element, suggest applying `aria-labelledby`
* prototype chain for document object: `document.createElement('p')` <- `HTMLParagraphElement.prototype` <- `HTMLElement.prototype` <- `Element.prototype` <- `Node.prototype` <- `Object.prototype` <- `null`
* difference b/w function and macro in Clojure: on a function call first the arguments of the function are evaluated then the body of the function is evaluated using the arguments; macros on the other hand describe a transformation from one piece of code to another, any evaluation takes place after the transformation [StackOverflow](http://stackoverflow.com/questions/3667403/what-is-the-difference-between-the-defn-and-defmacro)

## 03/03/2016
* ServiceWorker is event-driven and your code should aim to be __stateless__: when a ServiceWorker isn’t being used it’s shut down, losing all state [tutorial on using ServiceWorker](https://ponyfoo.com/articles/simple-offline-site-serviceworker)
* events in ServiceWorker
    * `install` event fires when a ServiceWorker is first fetched. Here is your chance to prime the ServiceWorker cache with the fundamental resources that should be available even while users are offline
    * `fetch` event fires whenever a request originates from your ServiceWorker scope, and you’ll get a chance to intercept the request and respond immediately, without going to the network
    * `activate` event fires after a successful installation. You can use it to phase out older versions of the worker – we’ll look at a basic example where we deleted stale cache entries
* difference b/w `<cite>` and `<q>`:
    * `q`: used to serve inline quotes, such as a direct quote by someone, within paragraph text.
    * `cite`: used to cite a creative work within text, such as mentioning a poem.
* Something about Angular 2 :) [Angular 2 Roadmap Update](https://www.youtube.com/watch?v=aHGmj_fqPLE)

## 03/02/2016
* only given inorder traversal and one other traversal can the binary tree be constructed

## 03/01/2016
* `const { protocol, host, hostname, port, pathname, hash, search, href, target } = window.location`
* tagged template literal (tagged template): ```tagFunction`Hello ${firstName} ${lastName}!` ``` is the same as `tagFunction(['Hello ', ' ', '!'], firstName, lastName)`, e.g. `String.raw`

## 02/29/2016
* an `element` is one specific type of `node`

## 02/28/2016
* same-origin policy: e.g. a web application using XMLHttpRequest could only make HTTP requests to its own domain
* CORS (Cross-Origin Resource Sharing): works by adding new HTTP headers that allow servers to describe the set of origins that are permitted to read that information using a web browser [HTTP access control](https://developer.mozilla.org/en-US/docs/Web/HTTP/Access_control_CORS)
* `(update-in [m [k & ks] f & args])` (Clojure): 'updates' a value in a nested associative structure, where ks is a sequence of keys and f is a function that will take the old value and any supplied args and return the new value, and returns a new nested structure. If any levels do not exist, hash-maps will be created.

```clojure
(def p {:name "James" :age 26})
(update-in p [:age] + 10)
```
* `(cons x seq)` (Clojure): returns a new seq where x is the first element and seq is the rest
`(cons [1 2] [4 5 6]) ;;=> ([1 2] 4 5 6)`
* Inside IIFE (immediate invoking function) if you use "use strict", value of this is undefined. To pass access window inside IIFE with "use strict", you have to pass this
* `window.onload` is fired when DOM is ready and all the contents including images, css, scripts, sub-frames, etc. finished loaded. This means everything is loaded; `document.onload` is fired when DOM (DOM tree built from markup code within the document)is ready which can be prior to images and other external content is loaded
* `document.readyState` returns `loading` while the Document is loading, `interactive` once it is finished parsing but still loading sub-resources, and `complete` once it has loaded; the `readystatechange` event fires on the `document` object when this value changes
* `domNode.classList.add`, `domNode.classList.remove`, `domNode.classList.toggle`, `domNode.classList.contains`
* `document.addEventListener('DOMContentLoaded', function(){});`

## 02/27/2016
* [The Life-Cycle of a Composite Component](https://github.com/facebook/react/blob/master/src/renderers/shared/reconciler/ReactCompositeComponent.js)

```javascript
/**
 * ------------------ The Life-Cycle of a Composite Component ------------------
 *
 * - constructor: Initialization of state. The instance is now retained.
 *   - componentWillMount
 *   - render
 *   - [children's constructors]
 *     - [children's componentWillMount and render]
 *     - [children's componentDidMount]
 *     - componentDidMount
 *
 *       Update Phases:
 *       - componentWillReceiveProps (only called if parent updated)
 *       - shouldComponentUpdate
 *         - componentWillUpdate
 *           - render
 *           - [children's constructors or receive props phases]
 *         - componentDidUpdate
 *
 *     - componentWillUnmount
 *     - [children's componentWillUnmount]
 *   - [children destroyed]
 * - (destroyed): The instance is now blank, released by React and ready for GC.
 *
 * -----------------------------------------------------------------------------
 */
```

## 02/26/2016
* Apache Hadoop’s jobtracker, namenode, secondary namenode, datanode, and tasktracker all generate logs

## 02/25/2016
* ![JavaScript Object Layout](./assets/IMG_3612.jpg)

## 02/24/2016
* select `tel` protocal a: `a[href^="tel:"]`
* `rel="nofollow"`: discourage links from being followed and indexed by search engine
* `<meta name="format-detection" content="telephone=no">` turn off number detection in iOS

##02/22/2016
* `Function.prototype.length`: number of args expected by the funtion, replacing `arity`
* visuallly hidden (from [H5BP](https://github.com/h5bp/html5-boilerplate/blob/master/src/css/main.css))

```css
/*
 * Hide only visually, but have it available for screen readers:
 * http://snook.ca/archives/html_and_css/hiding-content-for-accessibility
 */

.visuallyhidden {
    border: 0;
    clip: rect(0 0 0 0);
    height: 1px;
    margin: -1px;
    overflow: hidden;
    padding: 0;
    position: absolute;
    width: 1px;
}

/*
 * Extends the .visuallyhidden class to allow the element
 * to be focusable when navigated to via the keyboard:
 * https://www.drupal.org/node/897638
 */

.visuallyhidden.focusable:active,
.visuallyhidden.focusable:focus {
    clip: auto;
    height: auto;
    margin: 0;
    overflow: visible;
    position: static;
    width: auto;
}
```
* `~~3.14 = 3`, any applicable usage?
* diff document load event & document ready event: ready fires when the html load has completed and the DOM is ready; load fires when image other page content have all finished loading
* DOM event delegation: a mechanism of responding to ui-events via a single common parent rather than each child, through the magic of event "bubbling" (aka event propagation) [StackOverflow](http://stackoverflow.com/questions/1687296/what-is-dom-event-delegation)

## 02/21/2016
* to use Google Chrome Canary for debugging React Native, change `google chrome` to `google chrome cacanry` in `case 'darwin': return 'google chrome';` in `./node_modules/react-native/local-cli/server/middleware/getDevToolsMiddleware.js`
* `#(single-expression)` use `%1`(`%`), `%2` for args: syntax sugar, same as `(fn (args) expressions)`

## 02/20/2016
> "The most important thing in life will always be the people in this room. Right here, right now."
>
> Dominic Toretto

## 02/19/2016
* FOUC: flash of unstyled content, "instance where a web page appears briefly with the browser's default styles prior to loading an external CSS stylesheet, due to the web browser engine rendering the page before all information is retrieved" [Wikipedia](https://en.wikipedia.org/wiki/Flash_of_unstyled_content), solution: CSS in `<head>` with `<link>`
* HTTP keep-alive: the idea of using a single TCP connection to send and receive multiple HTTP requests/responses, specifically in HTTP 1.0 [Wikipedia](https://en.wikipedia.org/wiki/HTTP_persistent_connection)

## 02/18/2016
* Atom - find matching bracket: `^-m`
