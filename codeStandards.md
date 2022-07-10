## Code Standards

### Code Style

Some developers feel the need to debate code style. Other engineers will use the project's style and get stuff done. We prefer engineers who get stuff done. Consistency is important, please follow these guidelines.

We use the [JavaScript Standard Style](https://standardjs.com/) in our code. This is the style used by npm, GitHub, Zeit, MongoDB, Express, Electron, and many others. Be sure to use an automatic formatter like [standard-formatter](https://atom.io/packages/standard-formatter) for Atom and [vscode-standardjs](https://marketplace.visualstudio.com/items/chenxsan.vscode-standardjs) for Visual Studio Code.

Line length should be limited to 80 characters.

### Code Principles

* Code should be as simple, explicit, and as easy to understand as possible.
* Functional style is preferred to OOP. When possible functions should be pure and not rely on shared state or side effects.
* Avoid large frameworks; use small modules that are easy to understand.
* Modules must use this order so that they can be understood quickly when skimmed:
  1. External dependencies: anything listed in `package.json`, e.g. `require('http')`
  2. Internal dependencies: any files created in the project itself, e.g. `require('./api')`
  3. Constants and other setup: this includes anything *absolutely necessary* to be defined before `module.exports`
  4. Exports: `module.exports` should be as close to the beginning of the file as possible. The module should export either a single function or a "catalog object", e.g. `module.exports = { method1, method2, ... }`
  5. Functions: these go after the above sections. Use function hoisting to control the placement of your functions so that important, high-level functions are above smaller more-general utility functions.

* Keep your functions short. If your function is over 40 lines, you should have a good reason.

* Functions should not accept more than 3 arguments. Use a single options object if you need more arguments.

* Keep nesting to a minimum. Use [early returns](https://blog.timoxley.com/post/47041269194/avoid-else-return-early), single-line conditionals, and function calls.

### Naming Convention

* Use descriptive variable names. Function names should be a verb like route() or verb combined with a noun like routeRequest().
* Use meaningful descriptive names, e.g `getUserPosts` instead of `getUserData`.
* Favor descriptive over concise names, e.g `findUserById` instead of `findUser`.
* Use consistent names per concept. In a project, function names should be like `getUsers`, `getQuestions` and `getCourses` instead of `getUsers`, `retrieveQuestions` and `returnCourses`.
* Variable names should be self-descriptive, it shouldn't need a comment for additional documentation.
* Booleans should have a prefix like is, has, or are to help engineers with identifying booleans easier, e.g `isVisible` instead of `visible`.

### Test Driven Development

* We use Test Driven Development (TDD) while adding/updating any code.
* TDD is an approach where you write tests first, then use those tests to drive the design and development of the application.
* TDD approach shines especially for pure functions and the code should include detailed tests for such functions.
* The full test coverage is expected for pure functions, but are not necessarily mandatory for UI elements such as HTML or CSS.
* A good rule is to move all the pure functions to `utils` files or folders, including tests for those functions.
* There are three steps to follow while writing code in TDD, also known as [Red-Green-Refactor](http://www.jamesshore.com/v2/blog/2005/red-green-refactor). The steps are:
  1. Create a unit test that fails.
  2. Write production code that makes that test pass.
  3. Refactor/Clean up the code (make sure the test still passes).
* Repeat these steps for each small change in code until the goals the code change are complete.
* The above steps mean, by definition, that there should be no section of code that isn't tested.

### Responsive Web Design Standards

* Use styled-components throughout the project for making RWD.

* We are using bootstrap v.4.1.3. So use pre-built classes that comes up with bootstrap v.4. We don't need to create styled-components for applying just those style properties.

    Here is the cheatsheet for that: https://hackerthemes.com/bootstrap-cheatsheet/

    ```HTML
    <span className='d-flex justify-content-between align-items-center'></span>
    ```

* We have pre-defined configuration color variables that's placed in `bootstrap-theme.css` file.

    ```JS
    --teal: #20c997;
    --dark-black: #151518;
    ```

    Use those variables instead of putting hardcoded color values everywhere.

    ```JS
    export const Footer = styled.footer`
      background-color: var(--dark-black);
    `
    ```

* Currently we are applying media-queries for the same device breakpoints in pixel values repeatedly in our codebase like `@media (min-width: 576px)`.

    Onwards, we will be using a separate configuration file that's located at `src/mediaQueries.js` for making responsive breakpoints media-templates :

    ```JS
    import { css } from 'styled-components'

    export const BREAKPOINTS = {
      mobile: 576,
      tablet: 768,
      desktop: 992,
      giant: 1200
    }

    // iterate through the sizes and create a media template
    const mediaqueries = Object.keys(BREAKPOINTS).reduce((accumulator, label) => {
      const size = BREAKPOINTS[label]
      accumulator[label] = (...args) => css`
        @media (max-width: ${size}px) {
          ${css(...args)};
        }
      `
      return accumulator
    }, {})

    export default mediaqueries
    ```

    Usage Example :

    ```javascript
    const Container = styled.div`
      ${media.desktop`padding: 0 20px;`}
      ${media.tablet`padding: 0 10px;`}
      ${media.phone`padding: 0 5px;`}
    `
    ```

* If somehow you need to slightly change some other component styling for making a new one. Do not duplicate the style properties for that. To easily make a new component that inherits the styling of another, you should just wrap it in the styled() constructor.

    Here is the code sample showing creation of a `TomatoButton` component that's extending with some color-related styling :

    ```JS
    // The Button Component
    const Button = styled.button`
    color: palevioletred;
    font-size: 1em;
    margin: 1em;
    padding: 0.25em 1em;
    border: 2px solid palevioletred;
    border-radius: 3px;
    `;

    // A new component based on Button, but with some override styles
    const TomatoButton = styled(Button)`
    color: tomato;
    border-color: tomato;
    `;

    render(
      <div>
        <Button>Normal Button</Button>
        <TomatoButton>Tomato Button</TomatoButton>
      </div>
    );
    ```
