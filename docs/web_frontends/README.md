# Web Frontends

![Cover](cover.jpg)

Here's an explanation of which tools are optimal for frontend web projects. Unlike higher level languages such as Python which allow you to be blissfully unaware of lower level implementations such as Assembly code generation, languages which compile down to JS are much more transparent. You will be required to know JS, and spend extra time (versus lesser time in truly higher level languages such as Python) when first introducing them into your project. This means that these leaky abstractions (e.g., languages which compile down to JS, frameworks such as React) quickly become dated, or worse than directly using new standards which inadvertently come up. Hence, you'll want to use fewer abstractions over vanilla HTML, CSS, and JavaScript since it ends up being overkill to configure, learn, and maintain the extra setup they require.

## Languages

JavaScript does not scale well to larger projects due to its quirks, lack of features (e.g., functional programming, immutability), slow progress (it is difficult to update a language used everywhere), and lack of static typing.

Languages such as [PureScript](https://www.purescript.org/) and [Elm](https://elm-lang.org/) are not stable yet, and progress as slow as JS does due to their lack of support. They also good implementation for powerful features in the same way that languages with less backing than Java are less battle-tested.

Languages such as [CoffeeScript](https://coffeescript.org/) are simply slightly better versions of JavaScript for short periods of time. As soon as the next version of ES comes along, such languages render useless.

[Kotlin](https://kotlinlang.org/) is an excellent language for backends. It also targets JavaScript very well with its builtin under-the-hood webpack configuration. Setting up a Kotlin project is just as easy as setting up a JavaScript project. Even without the excellent support for its other compilation targets, the Kotlin programming language is an excellent choice syntactically for just about anything. There some two major issues with using it for JS compilation at the moment though, which are explained below. Once [Dukat](https://github.com/Kotlin/dukat), it's TypeScript definition to Kotlin declaration converter, is stable, perhaps it'd be a good choice for frontend web development. But that, along with other issues, won't be addressed for at least a few years.
- The tool which converts TypeScript definitions to Kotlin ones is still in active development and hardly works.
- It doesn't compile to useable JS. It targets ES5 for now, and only compiles it prettily enough for the reader to understand enough to debug it at the time of writing it. This makes it impractical to migrate to another language such as JavaScript (TypeScript easily lets you migrate back to JS).
- Even though it has excellent DCE, it still has a rather large compilation size because of all the standard library functions it includes which don't exist in JS.
- If you're writing a library, it's best to write it in JS anyway, because you want a smaller package size, and it's better to allow non-Kotlin users to make use of the library too. This way, not only can other developers use your library, but your own team can use it regardless of the language they're using. Of course, JS users can use a library developed in Kotlin, but it won't be idiomatic at all; it'll probably be worse than calling Scala code from Java (yuck).

[Reason](https://reasonml.github.io/) is like a noticeable worse Kotlin. It lacks typings, and doesn't have good support for its other compilation targets (e.g., servers). It may compile to more readable JS than Kotlin does because more closely resembles JS, but that's more of a con than a pro. Not only do you miss out on better syntax, but the compiled JS is still unusable. For example, the data structures are compiled down to arrays (instead of objects) whose indices no one knows.

[TypeScript](http://www.typescriptlang.org/) is the best choice for the foreseeable future. It is extremely easy to learn, very quick to adopt, provides better static types and more typings than [Flow](https://flow.org/), and it trivial to eject from (i.e., move back to JS). It may not have great features such as functional programming and immutability, but you get average JS libraries which provide these features should you need them. It's also the best option to write JS libraries in. Yes, that's right, it's better to write JS libraries in TS than it is to use JS itself. This is because both JS and TS users will get autocomplete and warnings from the TypeScript definitions. Since TS _is_ JS (Babel simply strips out the types when compiling it), the final file size is _the exact same_ as it would've been if you had written it in JS.

## Frameworks

- Although they don't force you to use particular libraries, they do a great job of telling you what you might need before you hit a pain point and wonder if there's a better way.
- They give you every tool you'll practically need, regardless of whether you'll use it or not.
- They take a long time to learn.
- They get outdated every few years. The same can be said for any programming tool. It doesn't matter too much since the concepts learnt carry on to the next framework.
- Libraries take a negligible amount of time to learn in comparison to a framework, and are a lot easier to migrate to or away from. Although libraries allow for greater flexibility in how your project is built, they have less integration with the other components in your system as a whole.

I personally prefer React over all the other frameworks. React has significantly better support, and a superior ecosystem. Unlike frameworks such as Vue and Svelte, React gives you the full power of JS when templating and styling since the HTML and CSS are not in separate sections of the file. Of course Vue gives built-in support for things such as conditionals and looping in templates, but they not only require you to learn extra syntax to leverage them, but they do not cover all the cases.

## Terminology

Frameworks have components for each of the following concepts. Concepts having standalone libraries to address their pain points have the best libary linked to them.

- **Ready-made components** refer to components such as buttons which are styled out-of-the-box. You can use a library such as [Material Components](https://github.com/material-components/material-components-web-components).
- **HTML templating** refers to easily creating DOM nodes in JS. You cannot directly create HTML elements by using an expression such as `const avatar = '<button><img src="img.png"</button>'` because they are prone to injection attacks, and are difficult to maintain. There are many HTML-in-JS and CSS-in-JS solutions (e.g., JSX, TSX, kotlinx.html, Emotion). You can use a library such as [lit-html](https://lit-html.polymer-project.org/) for this.
- **Custom element creation** is the creation of web components. You can use a library such as [LitElement](https://lit-element.polymer-project.org/) to rid their creation of boilerplate, etc.
- **Data binding** is the boilerplate-free way of mirroring data between the DOM and the program. Sans data binding, you have to use the following pattern far too often whenever you're presenting dynamic data.
    ```html
    <input type="button" id="clicker">
    Clicks: <span id="clicks"></span>
    <script>
        let count = 0;
        document.querySelector('#clicker').addEventListener(
            'click', 
            () => document.querySelector('#clicks').textContent = ++clicks
        );
    </script>
    ```
    Data binding rids us of this unmaintainable code by directly embedding the variables in the template. It does this by combining individual components' template and script code in the same file. It's not just used for trivial pieces of data like the number we've seen in this example, it's also used for dynamically and efficiently rerendering lists of custom components. This means that when you simply add a to-do item in your JavaScript code for a to-do list app the view would be updated, the state would be saved, and a callback could be executed to mirror the update on the serverside (database). Since data binding requires control over multiple files (languages), it is limited to frameworks. Although there were attempts to create standalone data binding libraries, those were quickly deprecated since they ended up being really bad versions of Vue.js.
- **State management** gives you a high level way of manipulating what your web app looks like at any given point in time. You can think about _state_ as your computer's desktop - with just a glance, you can easily see the current battery level, wi-fi connectivity, and which applications are open. Libraries such as [Redux](https://redux.js.org/) help deal with this.

## Tooling

Where possible, generate code. Here are some tools.
- [Google Sites](https://sites.google.com) generates websites with embeddable JavaScript.
- [Hugo](https://gohugo.io/) is a CMS.
- [Webflow](https://webflow.com/) generates sites with static content.

Remember that there are other other tools, such as testing and routing, which frameworks provide that aren't listed here. Such tools haven't been listed since half the reason frameworks provide them in the first place is because their custom setups require custom tooling to work with existing ecosystems and concepts. That is not to say that they are without their merits. Such tools are useful in their own way as well, but their benefits are only visible in larger projects, whereas smaller projects are more likely than not to be negatively impacted under their weight.

In general, you should use fewer tools the smaller your project is. Only in larger projects do libraries such as Redux actually improve (rather than worsen) code maintainability. Larger projects will benefit from frameworks even though new standards are always coming out (e.g., built-in custom element creation via web components). This is because new standards take time to get approved, consistently implemented, and lack the support larger projects require. Although smaller projects will be benefit from directly leveraging native standards when they come out, the boilerplate they usually require is very visibly felt in larger ones, and hence the lifetime for a framework's use in larger projects is substantially longer than that of smaller projects.

Here's a table showcasing which technologies are overkill for different sized projects. ✅, ➖, and ❌ refer to should use, doesn't matter (i.e., it's worth using if you already know it, but doesn't matter enough to learn it if you don't), and shouldn't use respectively.

|Project size|Ready-made components|HTML templating|Custom element creation|Data binding|State management|Framework|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Small|➖|❌|❌|❌|❌|❌|
|Medium|✅|✅|✅|✅|❌|➖|
|Large|✅|✅|✅|✅|✅|✅|

Repetitively writing non-trivial blocks of HTML is significantly better done via JavaScript. By using a programming language you have the full power of conditionally adding elements and styles using an if-statement, and easily replacing duplicate code with a loop. Similarly, using a CSS-in-JS (e.g., Emotion) solution allows you to use variables, expressions, etc. in your CSS. This way you don't need to learn a separate language which compiles down to CSS (e.g., SASS), don't have to switch between files for editing styles (i.e., it stops you from applying inline and global styles in difficult-to-find places), and gives you more power than a styling language ever could because you get the power of both the styling and programming language.