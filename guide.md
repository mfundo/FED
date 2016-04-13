# Front End Developer Guidelines

This is a living guide for Applogix Front End Developers to help with getting to terms with how code preferably should be structured. The guide has been divided into 3 main FE disciplines HTML, CSS & JS
 
This helps us work as a unit for team dynamism and most importantly developer confidence.
 
The guide has been forked from [TMWtech](http://tech.tmw.co.uk/code/TMW-frontend-guidelines), [Idiomatic HTML]([Nicolas Gallagher](https://github.com/necolas/idiomatic-html) and tailored to our needs.
 
## General Guidelines
 
#### Indents
 
Across all languages we will use tabs and the size is set to 4 by default. A EditorConfig will be provided.
 
#### Readability vs Compression
 
We recommend to write code for **humans and not machines**, meaning we like white space around the code and have meaningful descriptive classes and variables. Length and file-size shouldn't be a problem in development phases.
 
Code obfuscation will only happen in the build process and only in production code.
 
### Source Control
 
We going to be using **Git** and most commonly using the gitflow workflow (Where we branch by feature) read more about it [here](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) but your Team Lead / Tech Lead might decide otherwise.
 
You can use any Git GUI or the Terminal / CMD line :)
 
## HTML
 
The use of HTML5 doctype is encouraged and HTML5 elements where possible and feature detection using a customised version of [Modernizr](https://modernizr.com/download)
 
We prefer using **idiomatic HTML** written by [Nicolas Gallagher](https://github.com/necolas/idiomatic-html) which helps in code formatting and having each HTML attribute on a new line for readability / quick find and most of all code conflicts in source control. Instead of going through a whole line looking for what changed it's much easier and efficient to have one on each line.
 
Most importantly the HTML has to be semantically correct as much as possible and use [W3C](https://validator.w3.org/#validate_by_input) to validate your markup.
 
### Comments
 
Comment your code where necessary, don't overdo it. Most of our HTML will be in partials dedicated to a particular component so in most cases the markup tends to be small and straight forward, no need to indicate the start and end of code block.
 
## CSS

All our CSS should follow the BEM methodology for our modular naming conventions. (BEM breakdown to follow soon)
Targeting IDs and Elements isn't our thing as it introduces **CSS Specificity Wars**. Thanks to the use of BEM we wont have any.
 
- Class names should be all lowercase with hyphens.
- IDs are camelCased
 
We do not use !important too, the moment you need one it's a code smell. Unless you overriding a property from an external library, if that's the case make sure to also comment the !important declaration.
  
### Browser Support
 
We support 2 versions from the latest. Specifically this is a challenge in IE, in this regard we support IE 9+ as the latest is IE11.
Use feature detection and fallbacks for a graceful degrade.
 
### Frameworks
 
We recommend using either the latest Bootstrap or Foundation. It's also advised that you do need to use it, customize it to your needs instead of blindly downloading the whole library to reduce bloat.
 
### Syntax and formatting
 
CSS declarations must be on multiple lines, reasoning is the same as HTML attributes on each line as it increases readability and help with resolving conflicts in source control.
 
When using SASS keep your nesting **3 levels** deep at most.
 
**Alphabetically sort** your attributes, this also makes it easier to find attributes and just sounds right :). Alternatively group your attributes by layout, design etc. Whichever way you choose just be consistent.
 
### Reset vs Normalisation
 
We don't like resets because they are expensive and they do browser repaints, rather normalise your CSS using normalise.css by [Nicholas Gallagher](https://github.com/necolas/normalize.css/)
 
### Comments
 
Comment your code where necessary, don't overdo it. When using SASS comment/document your mixins and functions. Comments can be as descriptive as needed, they will be ignored in the build process.
 
### Conditional Stylesheets
 
Use Paul Irish's method of adding a class to the body using IE conditional tags and increase your specificity in your selectors.
 
**@Larry maybe you can add your way of doing it with SASS here?**
 
### Preprocessors
 
You are free to use whatever preprocessor you prefer. Tools like [Prepros](https://prepros.io/downloads) etc. Else use gulp and it's extensions to compile your SASS, image optimisations etc.
 
### Responsive Design
 
If you are using one the FW mentioned above then you are on track to doing the **mobile first approach**.
 
If you not using any FW make sure to follow the **mobile first approach**.(Link coming soon) As it favours progressive enhancement over graceful degradation.
 
## JS
 
- Variable names are camelCase
- Constants are uppercase
- Classes start with an Uppercase
 
We encourage the use of ES6 as much as possible, Team Lead / Tech Lead would advise otherwise.
 
Almost all scripts to be loaded before the closing body tag unless strictly specified otherwise like Modernizr and Google Tag Manager snippets.
 
### Formatting
 
Leave sensible spacing between code blocks, comparators and operators.
 
Use braces for logic evaluations. If evaluation execution is simple, keep non-braced logic on a single line.
 
Always use **===** as a comparator unless you understand the difference.
 
### Framework / Plugins
 
The Team Lead / Tech Lead will be the one advising on the FW to be used Angular, Backbone, React etc. The idea is being FW agnostic but we are Angular lovers, for **hybrid apps** we use Ionic.
 
**jQuery** is the most common library to use along with some of it's awesome plugins. Most projects will be using jQuery but it's not a must. If jQuery is used try to install as few plugins as possible, again Team Lead / Tech Lead would advise on which plugins will be added to the project.
 
We also use **Gulp** over **Grunt** for our build process and project packaging.
 
### Dependency Injection
 
If you using a FW like Angular we advised using Angular DI rather than using RequireJS etc.
 
Otherwise we encourage the use of Webpack and writing of AMD / CommonJS modules, if ES6 is used then stick to **native JS Modules**
 
### Package Manager
 
We have moved from using Bower and NPM together, we now use NPM for all our packages. If project doesnt exist on NPM keep it in the **libs / vendor** folder in your project.
 
### Build Server
 
We use **BrowserSync** to run our static files and local server.
 
Alternatively if you use **Webstorm IDE** by Jetbrains you can you use the internal server unless the project is configured to use HTML5 mode.
 
With project using Webpack, you can also run your project in **webpack dev server**
 
### Debugging
 
Please make sure to remove your **console.logs** when you done debugging even though we will remove them in our build process.

### Unit Testing

We prefer using Karma, works well with our prefered JS FW too (Angular). You can run your tests in any browser except for PhantomJS as it has issues on Continious Intergration Servers.

Our prefered testing framework is Jasmine and tests should be written for code that does any business logic or on code pieces that depend on external APIs.
