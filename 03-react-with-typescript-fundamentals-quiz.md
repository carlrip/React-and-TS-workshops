# React with TypeScript Fundamentals Quiz

The following questions should take you no longer than 3 hours to answer.  

1. Change the `Heading` component below to have its font colour configurable. The colour can only be red, blue or green
```
interface Props {
}
export const Heading: FC<Props> = ({ children }) => {
  return <h1>{children}</h1>;
};
```

2. A component called `Button` needs to be created that can have 3 different sizes `small`, `medium` and `large`. This size remains static within the lifetime of the component. Would we use props or state to specify the size? Define the TypeScript type for the props / state as well

3. Change the `Button` component below to have its `kind` prop optional and default to `"normal"`.
```
interface Props {
  kind: "normal" | "primary" | "deemphasized";
}
export const Button: FC<Props> = ({ kind, children }) => (
  <button>{children}</button>
);
```
4. Create a component called `Text` which will render a text element. The component should have a prop called `type` which will determine the HTML tag the text is rendered in. The `type` can be `h1`, `h2`, `h3`, `p` or `span`. The text to render should be defined in the child of the component 

5. Is it possible to define the type for a components props and state using a type alias?

6. Implement a function component that renders a checkbox with label. The label should be configurable and consumers should be able to listen to when the checkbox is ticked and unticked via a prop.

7. Create a function component that renders a list of strings that the consumer can pass in. Above the list should be a search input. Items in the list that match the search text entered should be rendered in bold. 

8. Create a class component called `StarWarsPeople1` that gets the first page of data from `https://swapi.co/api/people/` and lists the names in an unordered list

9. Create a function component called `StarWarsPeople2` that gets the second page of data from `https://swapi.co/api/people/` and lists the names in an unordered list

10. We need to implement a function component that counts down from a configurable number of seconds. The current number of seconds in the countdown is rendered by the component. Should the number of seconds be implemented as props or state? Implement the `CountDown` component.


🏆🏆🏆   

Send your answers to Carl to get your score and feedback. 


