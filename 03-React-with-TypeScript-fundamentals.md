# React with TypeScript Fundamentals

## Key

👉 Instruction  
❔ Question  
🏃 Exercise  
🏆 Tough challenge  
📄 Information  
💬 Tip  
🔗 Link to useful information

## Recap
📄 JSX is used to render React component which transpiles down to JavaScript `createElement` function calls in `react`. Babel does the transpilation  
📄 Components can be implemented using function or class components. There is a trend towards function components mainly because they allow easier code reuse  
📄 TypeScript allows us to create strongly-typed function and class components
📄 TypeScript does a great job of interring types but we can use type annotations where it can't  
📄 Custom types can be implemented using interfaces  
📄 Generics allow us to pass types into functions and classes to allow them to work internally with varied types

## Component props

📄 *Props* is short for *properties* and are parameters that are passed into a component that allows the consumer to configure it  
📄 A TypeScript interface can be used to make the props strongly-typed

👉 Create a new React+TS project in CodeSandbox  

📄 The syntax for adding strongly-typed props is:
```
interface Props 
{
  ...
}
const MyComponent: React.FC<Props> = (props) => {
  ...
}
class MyComponent extends React.Component<Props> {
  render() {
    ...
  }
}
```

📄 `React.FC` and `React.Component` are TypeScript types from React.

🔗 Components and Props from React docs: https://reactjs.org/docs/components-and-props.html

🏆 Create a new function component called `ShoppingList` that renders an unordered list from an `items` prop which is an array of shopping items. Each shopping item is a string.

💬 It is best practice in React to give each list item a `key` property that has a unique value. This is to allow React to manage updates to the list efficiently.

🔗 Rendering lists and keys in React docs: https://reactjs.org/docs/lists-and-keys.html

🏃 Reference the `ShoppingList` component from the `App` component by passing it `["Bread", "Milk", "Bananas"]`

🏃 Clean the implementation up by using the destructing syntax. Firstly, destructure `FC` from React so that it can be referenced as `FC` rather than `React.FC`. Secondly, destructure the `items` props so that it can be referenced directly within the component.

🔗 Destructing in MDN docs: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment

🏃 Make the `items` prop optional and default its value to `["Bread", "Milk"]`

🔗 Optional and default parameters in TypeScript docs: https://www.typescriptlang.org/docs/handbook/functions.html#optional-and-default-parameters

🏃 Add conditional rendering logic to each shopping list item to render "Bread" in bold.

🔗 Conditional rendering in React docs: https://reactjs.org/docs/conditional-rendering.html

🏃 Create a new class component called `ShoppingList2` that functions exactly the same as `ShoppingList`.

## Handling events

📄 We declare an event declaratively in React using a prop with the same name as the native event name with "on" in front and the prop name being in camel case.

```
<Element onEventName={(e) => { ... }}>
```

🔗 Events in React docs https://reactjs.org/docs/handling-events.html

🏃 Add a *Add* button to each item in `ShoppingList`. Output the item name to the console when the button is clicked

🏃 Implement the same in `ShoppingLists`. 

## Component state

📄 *State* allows us to implement interactive behaviour in a component. Whenever a piece of state changes, React will rerender the component.

❔ What's the difference between a local variable and a piece of state?

📄 Handling events along with using state make our components interactive

📄 The `useState` hook can be used in function components to create state

```
const [someState, setSomeState] = useState<T>(defaultValue);
```

🔗 State hook in the React docs: https://reactjs.org/docs/hooks-overview.html#state-hook

🔗 How to add a TypeScript type to `useHook` state: https://www.carlrippon.com/typed-usestate-with-typescript/

🏆 Add a piece of state in the `ShoppingList` component to track which items are in the basket. Call the state `basket` and define its type to be a list of strings. Render items that are in the basket with Strike-through. When *Add* is clicked, add the item to the `basket` state. When an item is in the basket, the button shouldn't be rendered and the item should be striked-through. 

🏃 Extract the logic for the shopping list item style into a function called `getShoppingListItemStyle` in a file called `ShoppingList.Utils.tsx`.

📄 State in class components is referenced using the `state` property from the `Component` React base class and is set using its `setState` method.

🔗 State in class components in React docs https://reactjs.org/docs/state-and-lifecycle.html#adding-local-state-to-a-class

📄 The TypeScript type for the state is defined in a 2nd generic parameter in the `Component` React base class.

```
class MyComponent extends React.Component<Props, State> {
  ...
}
```

🏃 Implement the same piece of state and interactivity in the `ShoppingList2` component.

🏃 In the `ShoppingList` component, output *"render"* to the console everytime it is rendered.   

❔ Is the `ShoppingList` component rerendered when the *Add* buttons are clicked? 

🏃 Take a safe copy of the `ShoppingList` component. Change the `basket` variable to be not state based to discover the difference between state based variables and normal variables  

❔ What is the difference between state based variable and a normal variable

🏃 Revert the changes to the `ShoppingList` component so that it works correctly with the `basket` state again.

## Controlled components

📄 A controlled component is where the component value is controlled by React state

🔗 Controlled component in React docs https://reactjs.org/docs/forms.html#controlled-components

🏃 Add a search input above the shopping list that filters the list to only render items that contain the input value. The input should be a controlled component that filters the list immediately as the user enters characters into the input. Implement this in `ShoppingList` and `ShoppingList2`

❔ Did you run into an issue with the above exercise when referencing `this` in the class component? If so, how did you resolve this?

❔ Did you strongly-type the event listener argument? If so what type did you use?

## Class component lifecycle 

📄 Class components invoke *lifecycle* methods when at various points within their lifetime. We can implement these methods to execute logic at certain points within a lifetime of a component. 

🔗 React life cycle diagram http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/

🏃 Implement the `componentDidMount`, `componentDidUpdate` and `componentWillunmount` methods in the class component that simply output the method name to the console. Observe which methods get invoked as you interact with the app.

❔ Which lifecycle method should be used to fetch data?

👉 Create a new React+TS project in CodeSandbox 

🏃 Create a component called `ToDoList` that renders the titles in a list from *to do* data at https://jsonplaceholder.typicode.com/todos in a list. Use `fetch` to get data from https://jsonplaceholder.typicode.com/todos. Reference the `ToDoList` component from the `App` component.

🏃 Create a button on the `App` component that removes the `ToDoList` component.

🏃 Add a delay of 2 seconds to the `ToDoList` component after the data has been fetched before any state is set. 

❔ What problem occurs when the `ToDoList` component is removed before the data is fetched?      
🏃 Resolve this issue

## Fetching data with useEffect

📄 Function components don't have lifecycle methods. The `useEffect` hook can be used to implement logic you would typically implement in class component lifecycle methods. `useEffect` allows logic to be executed when the component is mounted and unmounted as well as when things that the logic is dependent on changes. 

🔗 useEffect in React docs https://reactjs.org/docs/hooks-effect.html

🏆 Create a `ToDoList2` component which is a function equivalent of the class component.




