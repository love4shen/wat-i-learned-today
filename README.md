# wat i learned today

## 02/18/2016
* Atom - find matching bracket: `^-m`

## 02/19/2016
* FOUC: flash of unstyled content, "instance where a web page appears briefly with the browser's default styles prior to loading an external CSS stylesheet, due to the web browser engine rendering the page before all information is retrieved" [Wikipedia](https://en.wikipedia.org/wiki/Flash_of_unstyled_content), solution: CSS in `<head>` with `<link>`
* HTTP keep-alive: the idea of using a single TCP connection to send and receive multiple HTTP requests/responses, specifically in HTTP 1.0 [Wikipedia](https://en.wikipedia.org/wiki/HTTP_persistent_connection)

## 02/20/2016
> "The most important thing in life will always be the people in this room. Right here, right now."
> 
> Dominic Toretto

## 02/21/2016
* to use Google Chrome Canary for debugging React Native, change `google chrome` to `google chrome cacanry` in `case 'darwin': return 'google chrome';` in `./node_modules/react-native/local-cli/server/middleware/getDevToolsMiddleware.js`
* `#(single-expression)` use `%1`(`%`), `%2` for args: syntax sugar, same as `(fn (args) expressions)`

##02/22/2016
* `Function.prototype.length`: number of args expected by the funtion, replacing `arity`
* visuallly hidden (from [H5BP](https://github.com/h5bp/html5-boilerplate/blob/master/src/css/main.css))

```
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

## 02/24/2016
* select `tel` protocal a: `a[href^="tel:"]`
* `rel="nofollow"`: discourage links from being followed and indexed by SE
* `<meta name="format-detection" content="telephone=no">` turn off number detection in iOS

## 02/25/2016
* ![JavaScript Object Layout](./assets/IMG_3612.jpg)

## 02/26/2016
* Apache Hadoop’s jobtracker, namenode, secondary namenode, datanode, and tasktracker all generate logs

## 02/27/2016
* [The Life-Cycle of a Composite Component](https://github.com/facebook/react/blob/master/src/renderers/shared/reconciler/ReactCompositeComponent.js)

```
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
