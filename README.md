# wat i learned today

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

*

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
* `const { protocol, host, hostname, port, pathname, hash, search, href, target } = top.location`
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
* `rel="nofollow"`: discourage links from being followed and indexed by SE
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
