# Introduction to React

## Key

👉 Instruction  
❔ Question  
🏃 Exercise  
🏆 Tough challenge  
📄 Information  
💡 Tip  
🔗 Link to useful information

## Understanding how React is injected into a HTML page

👉 Create a new React project in https://codesandbox.io

❔ Where is the root html file that is served by the web server?  
❔ What element on the html page is the React app injected into?  
❔ What is the root React component called?  
🏆Remove the root element from the root html file and instead create this dynamically

## Understanding JSX

📄 JSX is used in React to define what elements are output to the DOM. It is special syntax where JavaScript is mixed with HTML. JavaScript allows us to implement conditional and looping logic when elements are output.

❔ Is JSX valid JavaScript?

👉 Go to https://babeljs.io/repl  
👉 Understand what `<a href="mailto:your.email@somewhere.com">your.email@somewhere.com</a>` transpiles down to

❔ Why do you think CSS classes are added to elements using `className` rather than `class` in JSX?

👉 Understand what `<div><a href="mailto:your.email@somewhere.com">your.email@somewhere.com</a></div>` transpiles down to

🏃 Put `your.email@somewhere.com` into a variable and use this variable in the JSX

🏆 Write JSX that uses an array of email addresses to output a list of email links

🔗[JSX in the React docs](https://reactjs.org/docs/introducing-jsx.html)

## Creating a function component

📄 A function React component is a regular JavaScript function that returns JSX.

👉 Create a new React project in https://codesandbox.io. 

❔ Is the `App` component a function React component? 🏃 If not change it into a function component  
❔ Can arrow functions be used for function React components? 🏃 If so, change the `App` component into an arrow function

🏃 Change the `App` component to render the current date 

🏃 Create a new component called `Hello` which renders the following message:

Hello, welcome to React!

🏃 Use the `Hello` in `App` to render the hello message above the current date

## Creating a class component

📄 A class React component is a JavaScript class that contains a `render` method that returns JSX. 

🏃 Change the `App` component to be a class component  

📄 Before React 16.8 class components had far more capabilities than function React components. Now both function and class components can be used to create complex React components. 

🔗 [Function and class components in the React docs](https://reactjs.org/docs/components-and-props.html#function-and-class-components)

📄 Advantages of function components over class components
- More succinct 
- Easy to reuse code 
- No `this` problem
- No confusing life cycle methods
- Harder to test
- Smaller compiled code size

## React with TypeScript components

📄 Using TypeScript with React allows us to create strongly-typed components which helps us to catch problems earlier. TypeScript also allows editors such as VS code to provide accurate IntelliSense, robust refactoring feature and great code navigation.

👉 Create a new React + TS in https://codesandbox.io

❔ What is the file extension for React+TS components?  
❔ Do React+TS projects support both function and class components?