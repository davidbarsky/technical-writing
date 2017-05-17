# ReasonRe Tutorial

[Reason](https://facebook.github.io/reason/) is really cool! It allows us to write [OCaml](https://ocaml.org/), an industrially tested langauge, with a friendly and familiar syntax. OCaml brings world-class pattern matching (think `switch` statements, but statements that operate on the structural, not value level), type inference (you can write code like JavaScript or Python, but the compiler can figure out all the types without intervention), and *really* fast compile times (it doesn't even feel like you're compiling! Things just happen as you type). Beside writing OCaml, Reason allows us to compile our programs to JavaScript and interact with libraries like React and Jest through [Bucklescript](https://github.com/bloomberg/bucklescript), a backend for OCaml that emits JavaScript.

This tutorial will assume some familarity with Reason's syntax and React.js. If you don't know these, use React in JavaScript first. 

We'll be using Mateusz Zatorski's [Create Reason React App](https://github.com/knowbody/crra) as a starter template. To get started:

0. Be sure that you have a recent version of [Node.js](https://nodejs.org/en/) installed!
1. `git clone https://github.com/knowbody/crra`
2. `cd crra`
3. `yarn` or `npm install`
4. `yarn start` or `npm start`. (This step might take some time! Don't worry. We're creating an project-local instance of the Reason toolset. This gives us easy setup and project isolation.)
5. Open your browser and navigate to: http://localhost:8080/

This tutorial will roughly follow [React's tutorial](https://facebook.github.io/react/tutorial/tutorial.html). The first component we see is a Shopping List using JavaScripts's classes:

```jsx
class ShoppingList extends React.Component {
  render() {
    return (
      <div className="shopping-list">
        <h1>Shopping List</h1>
        <ul>
          <li>Instagram</li>
          <li>WhatsApp</li>
          <li>Oculus</li>
        </ul>
      </div>
    );
  }
}
```

Reason's implentation is similar to the JavaScript version. It's almost a direct translation! You'll notice, however, that Reason doesn't have the concept of classees

```OCaml
module ShoppingList = {
  include ReactRe.Component;
  let render _ =>
    <div className="shopping-list">
      <h1> (ReactRe.stringToElement "Shopping List") </h1>
      <ul>
        <li> (ReactRe.stringToElement "Rice") </li>
        <li> (ReactRe.stringToElement "Apples") </li>
        <li> (ReactRe.stringToElement "Tofu") </li>
      </ul>
    </div>;
};
```