# JavaScript Development Practices and Style Guide


This is a living document and new ideas for improving the code around us are always welcome. Contribute: fork, clone, branch, commit, push, pull request.

* Lee Creasy [@prodaea](http://twitter.com/prodaea), [github](https://github.com/prodaea)
* Rich Hamburg [@ambidexterich](http://twitter.com/ambidexterich), [github](https://github.com/ambidexterich)
* Chris Hunter [@motoprog](http://twitter.com/motoprog), [github](https://github.com/hunt3r)
* Stephen Tudor [@tudorstudio](http://twitter.com/tudorstudio), [github](https://github.com/smt)




## Overview

All code in any code-base should look like a single person typed it, no matter
how many people contributed.

This document outlines the practices that we strive to use in all code that we
write; contributions to projects that we have created should follow these
guidelines.




## The Golden Rule

If an existing common style exists, it should be respected. Do not attempt to
impose style preferences upon an existing project with an established style.
This is the one absolutely mandatory rule in this document. Existing style
trumps all.


> ### "Arguments over style are pointless. There should be a style guide, and you should follow it"
> _Rebecca_ _Murphey_    

> ### "Part of being a good steward to a successful project is realizing that writing code for yourself is a Bad Idea™. If thousands of people are using your code, then write your code for maximum clarity, not your personal preference of how to get clever within the spec."
> _Idan_ _Gazit_




## Helpful Resources


### Code Quality and Testing Tools

 * [JavaScript Plugin](http://docs.codehaus.org/display/SONAR/JavaScript+Plugin) for [Sonar](http://www.sonarsource.org/)
 * [jsPerf](http://jsperf.com/)
 * [jsFiddle](http://jsfiddle.net/)
 * [jsbin](http://jsbin.com/)
 * [JavaScript Lint (JSL)](http://javascriptlint.com/)
 * [jshint](http://jshint.com/)
 * [jslint](http://jslint.org/)


### References and More

 * [MDN JavaScript Reference](https://developer.mozilla.org/en-US/docs/JavaScript)
 * [MDN DOM Reference](https://developer.mozilla.org/en-US/docs/DOM)
 * [Annotated ECMAScript 5.1](http://es5.github.com/)
 * [EcmaScript Language Specification, 5.1 Edition](http://ecma-international.org/ecma-262/5.1/)

The following should be considered 1) incomplete, and 2) *REQUIRED READING*.
I don't always agree with the style written by the authors below, but one thing
is certain: They are consistent. Furthermore, these are authorities on the
language.

 * [Baseline For Front End Developers](http://rmurphey.com/blog/2012/04/12/a-baseline-for-front-end-developers/)
 * [Eloquent JavaScript](http://eloquentjavascript.net/)
 * [JavaScript, JavaScript](http://javascriptweblog.wordpress.com/)
 * [Adventures in JavaScript Development](http://rmurphey.com/)
 * [Perfection Kills](http://perfectionkills.com/)
 * [Douglas Crockford's Wrrrld Wide Web](http://www.crockford.com)
 * [JS Assessment](https://github.com/rmurphey/js-assessment)
 * [Leveraging Code Quality Tools by Anton Kovalyov](http://anton.kovalyov.net/slides/gothamjs/)


### Build & Deployment Process

Projects should always attempt to include some generic means by which source can
be linted, tested and compressed in preparation for production use. For this
task, [grunt](https://github.com/cowboy/grunt) by Ben Alman is second to none
and has officially replaced the "kits/" directory of this repo.


### Test Facility

Projects _must_ include some form of unit, reference, implementation or
functional testing. Use case demos DO NOT QUALIFY as "tests". The following is
a list of test frameworks, none of which are endorsed more than the other.

 * [QUnit](http://github.com/jquery/qunit)
 * [Jasmine](https://github.com/pivotal/jasmine)
 * [Vows](https://github.com/cloudhead/vows)
 * [Mocha](https://github.com/visionmedia/mocha)
 * [Hiro](http://hirojs.com/)
 * [JsTestDriver](https://code.google.com/p/js-test-driver/)
 * [Buster.js](http://busterjs.org/)
 * [Sinon.js](http://sinonjs.org/)




## Table of Contents

 * [Whitespace](#whitespace)
 * [Beautiful Syntax](#spacing)
 * [Type Checking (Courtesy jQuery Core Style Guidelines)](#type)
 * [Conditional Evaluation](#cond)
 * [Practical Style](#practical)
 * [Naming](#naming)
 * [Misc](#misc)
 * [Native & Host Objects](#native)
 * [Comments](#comments)
 * [One Language Code](#language)




------------------------------------------------




## Preface

The following sections outline a _reasonable_ style guide for modern JavaScript
development and are not meant to be prescriptive. The most important take-away
is the **law of code style consistency**. Whatever you choose as the style for
your project should be considered law. Link to this document as a statement of
your project's commitment to code style consistency, readability and
maintainability.




## Style Manifesto


### 1. <a name="whitespace">Whitespace</a>

- Never mix spaces and tabs.
- When beginning a project, before you write any code, choose between soft indents (spaces) or real tabs, consider this **law**.
    - For readability, we recommend setting your editor's indent size to four characters &mdash; this means four spaces or four spaces representing a real tab.
- If your editor supports it, always work with the "show invisibles" setting turned on. The benefits of this practice are:
    - Enforced consistency
    - Eliminating end of line whitespace
    - Eliminating blank line whitespace
    - Commits and diffs that are easier to read
- Several editors support tools like [EditorConfig](http://editorconfig.org/). Using a `.editorconfig` file can help keep everyone in sync with your project's whitespace styles for different file types.


### 2. <a name="spacing">Beautiful Syntax</a>

#### 2.A. Parens, Braces, Linebreaks

`if/else/for/while/try` always have spaces, braces and span multiple lines. This
encourages readability.


###### 2.A.1

When defining a functional or block statement, observe the following
conventions:

- One space between keyword and opening parenthesis
- No inner spacing of parentheses or braces
- One space between parameters
- One space between the closing parenthesis and the opening brace of the definition block


###### 2.A.1.1 Examples of really cramped syntax

    if(condition) doSomething();

    while(condition) iterating++;

    for(var i=0;i<100;i++) someIterativeFn();


###### 2.A.1.2 Use whitespace to promote readability

    if (condition) {
        // statements
    }

    while (condition) {
        // statements
    }

    for (var i = 0; i < 100; i++) {
        // statements
    }

    // Even better:

    var i;
    var length = 100;

    for (i = 0; i < length; i++) {
        // statements
    }

Or...

    var i = 0;
    var length = 100;

    for (; i < length; i++) {
        // statements
    }

    var prop;

    for (prop in object) {
        // statements
    }

    if (true) {
        // statements
    } else {
        // statements
    }


###### 2.A.1.2 Arrays and Objects

Add inner spaces to single-line array and object definitions for readability.

    var ary = [ 1, 2, 3, 4, 5 ];

    var obj = { foo: 1, bar: 2, qux: 3 };


#### 2.B. Assignments, Declarations, Functions (Named, Expression, Constructor)

###### 2.B.1.1 Variables

    var foo = "bar";
    var num = 1;
    var undef;

    // Literal notations:
    var array = [];
    var object = {};


###### 2.B.1.2 Use separate `var` statements

Do this for a clean and more maintainable declaration list.

    // Bad
    var foo = "",
        bar = "",
        quux;

    // Good
    var foo = "";
    var bar = "";
    var qux;


Comma-separated declaration lists are OK, but assignments should be accompanied
by a `var` keyword.

    // This is OK
    var foo, bar, baz;
    var qux = 1;


For more details on this, see <http://benalman.com/news/2012/05/multiple-var-statements-javascript/>.


###### 2.B.1.3 `var` statements should always be in the beginning of their respective scope (function). Same goes for const and let from ECMAScript 6.

    // Bad
    function foo () {
        // some statements here

        var bar = "";
        var qux;
    }

    // Good
    function foo () {
        var bar = "";
        var qux;

        // all statements after the variables declarations.
    }


###### 2.B.2.1 Named Function Declaration

    function foo (arg1, argN) {

    }

    // Usage
    foo(arg1, argN);


###### 2.B.2.2 Named Function Declaration

    function square (number) {
        return number * number;
    }

    // Usage
    square(10);

    // Really contrived continuation passing style
    function square (number, callback) {
        callback(number * number);
    }

    square (10, function (square) {
        // callback statements
    });


###### 2.B.2.3 Function Expression

    var square = function (number) {
        // Return something valuable and relevant
        return number * number;
    };

    // Function Expression with Identifier
    // This preferred form has the added value of being
    // able to call itself and have an identity in stack traces:
    var factorial = function factorial (number) {
        if (number < 2) {
            return 1;
        }

        return number * factorial(number-1);
    };


###### 2.B.2.4 Constructor Declaration

    function FooBar (options) {
        this.options = options;
    }

    // Usage
    var fooBar = new FooBar({ a: "alpha" });

    fooBar.options;
    // { a: "alpha" }


#### 2.C. Consistency Always Wins (The Golden Rule)

In sections 2.A and 2.B, the whitespace rules are set forth as a recommendation with
a simpler, higher purpose: consistency.

It's important to note that formatting preferences, such as "inner whitespace"
should be considered optional, but only one style should exist across the entire
source of your project.


###### 2.C.1.1

    if (condition) {
        // statements
    }

    while (condition) {
        // statements
    }

    for (var i = 0; i < 100; i++) {
        // statements
    }

    if (true) {
        // statements
    } else {
        // statements
    }


#### 2.D. Quotes

Whether you prefer single or double shouldn't matter, there is no difference in
how JavaScript parses them. What **ABSOLUTELY MUST** be enforced is consistency.
**Never mix quotes in the same project. Pick one style and stick with it.**


#### 2.E. End of Lines and Empty Lines

Whitespace can ruin diffs and make changesets impossible to read. Consider
incorporating a pre-commit hook that removes end-of-line whitespace and blanks
spaces on empty lines automatically. Some editors, such as Vim, can be
configured to remove a file's trailing whitespace on save.




### 3. <a name="type">Type Checking (Courtesy jQuery Core Style Guidelines)</a>

#### 3.A. Actual Types

    String:

        typeof variable === "string"

    Number:

        typeof variable === "number"

    Boolean:

        typeof variable === "boolean"

    Object:

        typeof variable === "object"

    Array:

        Array.isArray(arrayLikeObject)
        (wherever possible)

    Node:

        elem.nodeType === 1

    null:

        variable === null

    null or undefined:

        variable == null

    undefined:

      Global Variables:

        typeof variable === "undefined"

      Local Variables:

        variable === undefined

      Properties:

        object.prop === undefined
        object.hasOwnProperty(prop)
        "prop" in object


#### 3.B. Coerced Types

Consider the implications of the following…

Given this HTML:

    <input type="text" id="foo-input" value="1">


###### 3.B.1.1

`foo` has been declared with the value `0` and its type is `number`

    var foo = 0;

    // typeof foo;
    // "number"
    ...


Somewhere later in your code, you need to update `foo` with a new value derived
from an input element.

    foo = document.getElementById("foo-input").value;


If you were to test `typeof foo` now, the result would be `string`. This means
that if you had logic that tested `foo` like:

    if (foo === 1) {

      importantTask();

    }


`importantTask()` would never be evaluated, even though `foo` has a value of "1"


###### 3.B.1.2

You can preempt issues by using smart coercion with unary + or - operators:

    foo = +document.getElementById("foo-input").value;
    //    ^ unary + operator will convert its right side operand to a number

    // typeof foo;
    // "number"

    if (foo === 1) {

        importantTask();

    }

    // `importantTask()` will be called


Here are some common cases along with coercions:


###### 3.B.2.1

    var number = 1;
    var string = "1";
    var bool = false;

    number;
    // 1

    number + "";
    // "1"

    string;
    // "1"

    +string;
    // 1

    +string++;
    // 1

    string;
    // 2

    bool;
    // false

    +bool;
    // 0

    bool + "";
    // "false"


###### 3.B.2.2

    var number = 1;
    var string = "1";
    var bool = true;

    string === number;
    // false

    string === number + "";
    // true

    +string === number;
    // true

    bool === number;
    // false

    +bool === number;
    // true

    bool === string;
    // false

    bool === !!string;
    // true


###### 3.B.2.3

    var array = [ "a", "b", "c" ];

    !!~array.indexOf("a");
    // true

    !!~array.indexOf("b");
    // true

    !!~array.indexOf("c");
    // true

    !!~array.indexOf("d");
    // false


Note that the above should be considered "unnecessarily clever". Prefer the
obvious approach of comparing the returned value of `indexOf`, like:

    if (array.indexOf( "a" ) >= 0) {
        // ...
    }


###### 3.B.2.4

    var num = 2.5;

    parseInt(num, 10);

    // is the same as...

    ~~num;

    num >> 0;

    num >>> 0;

    // All result in 2


Keep in mind however, that negative numbers will be treated differently...

    var neg = -2.5;

    parseInt(neg, 10);

    // is the same as...

    ~~neg;

    neg >> 0;

    // All result in -2.


However…

    neg >>> 0;

    // Will result in 4294967294




### 4. <a name="cond">Conditional Evaluation</a>

##### 4.1.1

When only evaluating that an array has length, instead of this:

    if (array.length > 0) ...


…evaluate truthiness, like this:

    if (array.length) ...


##### 4.1.2

When only evaluating that an array is empty, instead of this:

    if (array.length === 0) ...


…evaluate truthiness, like this:

    if (!array.length) ...


##### 4.1.3

When only evaluating that a string is not empty, instead of this:

    if (string !== "") ...

…evaluate truthiness, like this:

    if (string) ...


##### 4.1.4

When only evaluating that a string _is_ empty, instead of this:

    if (string === "") ...


…evaluate falsy-ness, like this:

    if (!string) ...


##### 4.1.5

When only evaluating that a reference is true, instead of this:

    if (foo === true) ...


…evaluate like you mean it, take advantage of built in capabilities:

    if (foo) ...


##### 4.1.6

When evaluating that a reference is false, instead of this:

    if (foo === false) ...


…use negation to coerce a true evaluation

    if (!foo) ...


…Be careful, this will also match: `0, "", null, undefined, NaN`

If you _MUST_ test for a boolean false, then use

    if (foo === false) ...


##### 4.1.7

When only evaluating a ref that might be `null` or `undefined`, but NOT `false`,
`""` or `0`, instead of this:

    if (foo === null || foo === undefined) ...


…take advantage of == type coercion, like this:

    if (foo == null) ...


Remember, using == will match a `null` to BOTH `null` and `undefined` but not
`false`, "" or 0

    null == undefined


ALWAYS evaluate for the best, most accurate result - the above is a guideline, not a dogma.


##### 4.2.1 Type coercion and evaluation notes

Prefer `===` over `==` (unless the case requires loose type evaluation)

`===` does not coerce type, which means that:

    "1" === 1;
    // false


`==` does coerce type, which means that:

    "1" == 1;
    // true


##### 4.2.2 Booleans, Truthies & Falsies

    // Booleans:
    true, false

    // Truthy:
    "foo", 1

    // Falsy:
    "", 0, null, undefined, NaN, void 0




### 5. <a name="practical">Practical Style</a>

##### 5.1.1 A Practical Module

    (function (global) {
        var Module = (function () {

            var data = "secret";

            return {
                // This is some boolean property
                bool: true,
                // Some string value
                string: "a string",
                // An array property
                array: [ 1, 2, 3, 4 ],
                // An object property
                object: {
                    lang: "en-Us"
                },
                getData: function () {
                    // get the current value of `data`
                    return data;
                },
                setData: function (value) {
                    // set the value of `data` and return it
                    return (data = value);
                }
            };
        })();

        // Other things might happen here

        // expose our module to the global object
        global.Module = Module;

    })(this);


##### 5.2.1 A Practical Constructor

    (function (global) {

        function Ctor (foo) {

            this.foo = foo;

            return this;
        }

        Ctor.prototype.getFoo = function () {
            return this.foo;
        };

        Ctor.prototype.setFoo = function (val) {
            return (this.foo = val);
        };

      // To call constructor's without `new`, you might do this:
        var ctor = function (foo) {
            return new Ctor(foo);
        };

        // expose our constructor to the global object
        global.ctor = ctor;

    })(this);




### 6. <a name="naming">Naming</a>

#### 6.A. You are not a human code compiler/compressor, so don't try to be one.

The following code is an example of egregious naming:


###### 6.A.1.1

Example of code with poor names

    function q (s) {
        return document.querySelectorAll(s);
    }
    var i,a=[],els=q("#foo");
    for(i=0;i<els.length;i++){a.push(els[i]);}


Without a doubt, you've written code like this - hopefully that ends today.

Here's the same piece of logic, but with kinder, more thoughtful naming (and
a readable structure):


###### 6.A.2.1

Example of code with improved names

    function query (selector) {
        return document.querySelectorAll(selector);
    }

    var idx = 0,
        elements = [],
        matches = query("#foo"),
        length = matches.length;

    for (; idx < length; idx++) {
        elements.push(matches[ idx ]);
    }


A few additional naming pointers:


###### 6.A.3.1

Naming strings

    `dog` is a string


###### 6.A.3.2

Naming arrays

    `dogs` is an array of `dog` strings


###### 6.A.3.3

Naming functions, objects, instances, etc

    camelCase; function and var declarations


###### 6.A.3.4

Naming constructors, prototypes, etc.

    PascalCase; constructor function


###### 6.A.3.5

Naming regular expressions

    rDesc = //;


###### 6.A.3.6

From the Google Closure Library Style Guide

    functionNamesLikeThis;
    variableNamesLikeThis;
    ConstructorNamesLikeThis;
    EnumNamesLikeThis;
    methodNamesLikeThis;
    SYMBOLIC_CONSTANTS_LIKE_THIS;



#### 6.B. Faces of `this`

Beyond the generally well known use cases of `call` and `apply`, always prefer
`.bind(this)` or a functional equivalent, for creating `BoundFunction`
definitions for later invocation. Only resort to aliasing when no preferable
option is available.


##### 6.B.1

    function Device (opts) {

        this.value = null;

        // open an async stream,
        // this will be called continuously
        stream.read(opts.path, function (data) {

            // Update this instance's current value
            // with the most recent value from the
            // data stream
            this.value = data;

        }.bind(this) );

        // Throttle the frequency of events emitted from
        // this Device instance
        setInterval(function () {

            // Emit a throttled event
            this.emit("event");

        }.bind(this), opts.freq || 100 );
    }

    // Just pretend we've inherited EventEmitter ;)


When unavailable, functional equivalents to `.bind` exist in many modern
JavaScript libraries.


##### 6.B.2

    // eg. lodash/underscore, _.bind()
    function Device (opts) {

        this.value = null;

        stream.read(opts.path, _.bind(function (data) {

            this.value = data;

        }, this) );

        setInterval(_.bind(function () {

            this.emit("event");

        }, this), opts.freq || 100 );
    }


    // eg. jQuery.proxy
    function Device (opts) {

        this.value = null;

        stream.read(opts.path, jQuery.proxy(function (data) {

            this.value = data;

        }, this) );

        setInterval(jQuery.proxy(function () {

            this.emit("event");

        }, this), opts.freq || 100 );
    }


    // eg. dojo.hitch
    function Device (opts) {

        this.value = null;

        stream.read(opts.path, dojo.hitch this, function (data) {

            this.value = data;

        }) );

        setInterval(dojo.hitch(this, function () {

            this.emit("event");

        }), opts.freq || 100 );
    }


As a last resort, create an alias to `this` using `self` as an Identifier. This
is extremely bug prone and should be avoided whenever possible.


##### 6.B.3

    function Device (opts) {
        var self = this;

        this.value = null;

        stream.read(opts.path, function (data) {

            self.value = data;

        });

        setInterval(function () {

            self.emit("event");

        }, opts.freq || 100 );
    }



#### 6.C. Use `thisArg`

Several prototype methods of ES 5.1 built-ins come with a special `thisArg`
signature, which should be used whenever possible


##### 6.C.1

    var obj;

    obj = { f: "foo", b: "bar", q: "qux" };

    Object.keys(obj).forEach(function (key) {

        // |this| now refers to `obj`

        console.log(this[ key ]);

    }, obj ); // <-- the last arg is `thisArg`

    // Prints...

    // "foo"
    // "bar"
    // "qux"


`thisArg` can be used with `Array.prototype.every`, `Array.prototype.forEach`,
`Array.prototype.some`, `Array.prototype.map`, `Array.prototype.filter`




### 7. <a name="misc">Misc</a>

This section will serve to illustrate ideas and concepts that should not be
considered dogma, but instead exists to encourage questioning practices in an
attempt to find better ways to do common JavaScript programming tasks.



#### 7.A. Using `switch` should be avoided

Modern method tracing will blacklist functions with switch statements.

However, there seem to be drastic improvements to the execution of `switch`
statements in latest releases of Firefox and Chrome.
<http://jsperf.com/switch-vs-object-literal-vs-module>

Notable improvements can be witnessed here as well:
<https://github.com/rwldrn/idiomatic.js/issues/13>


###### 7.A.1.1

An example switch statement

    switch (foo) {
        case "alpha":
            alpha();
            break;
        case "beta":
            beta();
            break;
        default:
            // something to default to
            break;
    }


###### 7.A.1.2

An alternate approach that supports composability and reusability is to use an
object to store "cases" and a function to delegate:

    var cases, delegator;

    // Example returns for illustration only.
    cases = {
        alpha: function () {
            // statements
            // a return
            return [ "Alpha", arguments.length ];
        },
        beta: function () {
            // statements
            // a return
            return [ "Beta", arguments.length ];
        },
        _default: function () {
            // statements
            // a return
            return [ "Default", arguments.length ];
        }
    };

    delegator = function () {
        var args, key, delegate;

        // Transform arguments list into an array
        args = [].slice.call(arguments);

        // shift the case key from the arguments
        key = args.shift();

        // Assign the default case handler
        delegate = cases._default;

        // Derive the method to delegate operation to
        if (cases.hasOwnProperty( key )) {
            delegate = cases[ key ];
        }

        // The scope arg could be set to something specific,
        // in this case, |null| will suffice
        return delegate.apply(null, args);
    };


###### 7.A.1.3

Put the API in 7.A.1.2 to work:

    delegator("alpha", 1, 2, 3, 4, 5);
    // [ "Alpha", 5 ]

    // Of course, the `case` key argument could easily be based
    // on some other arbitrary condition.

    var caseKey, someUserInput;

    // Possibly some kind of form input?
    someUserInput = 9;

    if (someUserInput > 10) {
        caseKey = "alpha";
    } else {
        caseKey = "beta";
    }

    // or...

    caseKey = someUserInput > 10 ? "alpha" : "beta";

    // And then...

    delegator(caseKey, someUserInput);
    // [ "Beta", 1 ]

    // And of course...

    delegator();
    // [ "Default", 0 ]



#### 7.B. Early returns promote code readability with negligible performance difference


###### 7.B.1.1

    // Bad:
    function returnLate (foo) {
        var ret;

        if (foo) {
            ret = "foo";
        } else {
            ret = "quux";
        }
        return ret;
    }

    // Good:

    function returnEarly (foo) {
        if (foo) {
            return "foo";
        }
        return "quux";
    }




### 8. <a name="native">Native & Host Objects</a>

The basic principle here is:

**Don't be a idiot** and everything will be ok.

To reinforce this concept, please watch the following presentation:

“Everything is Permitted: Extending Built-ins” by Andrew Dupont (JSConf2011,
Portland, Oregon)

<iframe src="http://blip.tv/play/g_Mngr6LegI.html" width="480" height="346" frameborder="0" allowfullscreen></iframe><embed type="application/x-shockwave-flash" src="http://a.blip.tv/api.swf#g_Mngr6LegI" style="display:none"></embed>

<http://blip.tv/jsconf/jsconf2011-andrew-dupont-everything-is-permitted-extending-built-ins-5211542>




### 9. <a name="comments">Comments</a>

- Single line above the code that is subject
- Multiline is good
- End of line comments are prohibited!
- JSDoc style is good, but requires a significant time investment




### 10. <a name="language">One Language Code</a>

Programs should be written in one language, whatever that language may be, as
dictated by the maintainer or maintainers.




## Appendix

### Comma First.

Any project that cites this document as its base style guide will not accept
comma first code formatting, unless explicitly specified otherwise by that
project's author.



----------




<a rel="license" href="http://creativecommons.org/licenses/by/3.0/deed.en_US"><img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by/3.0/80x15.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">Principles of Writing Consistent, Idiomatic JavaScript</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="https://github.com/rwldrn/idiomatic.js" property="cc:attributionName" rel="cc:attributionURL">Rick Waldron and Contributors</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/3.0/deed.en_US">Creative Commons Attribution 3.0 Unported License</a>.<br />Based on a work at <a xmlns:dct="http://purl.org/dc/terms/" href="https://github.com/rwldrn/idiomatic.js" rel="dct:source">github.com/rwldrn/idiomatic.js</a>.
