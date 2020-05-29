# React Rendering Quiz

The following questions should take you no longer than 1 hour to answer.  

1. Consider the `App` component below:

``` 
export default function App() {
  const [counter1, setCounter1] = React.useState(1);
  const [counter2, setCounter2] = React.useState(10);
  const handleClick = () => {
    setCounter1(c => (c >= 10 ? 10 : c + 1));
    setCounter2(c => (c <= 1 ? 1 : c - 1));
  };
  return (
    <div>
      <button onClick={handleClick}>
        {counter1}|{counter2}
      </button>
    </div>
  );
}
```

- How many times will the component rerender when the button is clicked?
- What elements of the browsers DOM will be updated when the button is clicked? The whole page? Just the div in the component and its children? Just the button? or just the button content?


2. Consider the `App` component and its child component, `Counter`, below. 

```
function Counter() {
  const [counter, setCounter] = React.useState(1);
  return <button onClick={() => setCounter(c => c + 1)}>{counter}</button>;
}
export default function App() {
  const [counter, setCounter] = React.useState(1);
  React.useEffect(() => {
    const timer = setInterval(
      () => setCounter(c => (c < 10 ? c + 1 : c)),
      1000
    );
    return () => {
      clearInterval(timer);
    };
  }, []);
  return (
    <div>
      <div>{counter}</div>
      <Counter />
    </div>
  );
}
```

- When the timer ticks in `App`, will `Counter` rerender?
- What elements, if any, in the `Counter` component, in the browsers DOM, will be updated when the timer ticks?

3. Consider a slight variation of the previous example. This time the counter is memorized. 

```
function Counter() {
  const [counter, setCounter] = React.useState(1);
  return <button onClick={() => setCounter(c => c + 1)}>{counter}</button>;
}
function MemoCounter() {
  return React.useMemo(() => <Counter />, []);
}
export default function App() {
  const [counter, setCounter] = React.useState(1);
  React.useEffect(() => {
    const timer = setInterval(
      () => setCounter(c => (c < 10 ? c + 1 : c)),
      1000
    );
    return () => {
      clearInterval(timer);
    };
  }, []);
  return (
    <div>
      <div>{counter}</div>
      <MemoCounter />
    </div>
  );
}
```
- When the timer ticks in `App`, will `Counter` rerender?
- When the button in `Counter` is clicked, will it rerender?

4. We have enhanced the `Counter` component again by adding a click event. When the timer ticks in `App`, will `Counter` rerender?

```
type CounterProps = {
  onClick: () => void;
};
function Counter({ onClick }: CounterProps) {
  const [counter, setCounter] = React.useState(1);
  return <button onClick={() => setCounter(c => c + 1)}>{counter}</button>;
}
function MemoCounter({ onClick }: CounterProps) {
  return React.useMemo(() => <Counter onClick={onClick} />, [onClick]);
}
export default function App() {
  const [counter, setCounter] = React.useState(1);
  React.useEffect(() => {
    const timer = setInterval(
      () => setCounter(c => (c < 10 ? c + 1 : c)),
      1000
    );
    return () => {
      clearInterval(timer);
    };
  }, []);
  return (
    <div>
      <div>{counter}</div>
      <MemoCounter onClick={() => console.log("click")} />
    </div>
  );
}
```

5. We have a React context that is used within `Header` and `Form` components as follows:

```
type AppContextType = {
  appName: string;
  userName: string;
  setUserName: (value: string) => void;
};
const AppContext = React.createContext<AppContextType>(undefined!);

type Props = {
  children: React.ReactNode;
};
const UserProvider = ({ children }: Props) => {
  const [appName] = React.useState("My App");
  const [userName, setUserName] = React.useState("");
  return (
    <AppContext.Provider value={{ appName, userName, setUserName }}>
      {children}
    </AppContext.Provider>
  );
};

export const useApp = () => React.useContext(AppContext);

const Header = () => {
  const { appName } = useApp();
  return (
    <header>
      <h1>{appName}</h1>
    </header>
  );
};
const Form = () => {
  const { userName, setUserName } = useApp();
  return (
    <input
      type="text"
      value={userName}
      onChange={e => setUserName(e.currentTarget.value)}
    />
  );
};
const App = () => {
  return (
    <UserProvider>
      <Header />
      <Form />
    </UserProvider>
  );
};
```

- When the user types "Bob" into the input, how many times will the `Header` component rerender?
- What elements of the browsers DOM will be updated when characters are entered into the input? 

6. Consider the component below:

```
export default function App() {
  const [items, setItems] = React.useState<string[]>([]);
  const [newItem, setNewItem] = React.useState("");

  return (
    <div>
      <input
        type="text"
        value={newItem}
        onChange={e => setNewItem(e.currentTarget.value)}
      />
      <button
        onClick={() => {
          setItems([newItem, ...items]);
          setNewItem("");
        }}
      >
        Add
      </button>
      <ul>
        {items.map(item => (
          <li>{item}</li>
        ))}
      </ul>
    </div>
  );
}
```

- After some text has been entered into the input, and the button is clicked, what elements of the browsers DOM will be updated? 
- What can we add to the component JSX to make the browsers DOM updates to be more efficient?



Question on how many times DOM updated when a component rerenders but nothing is changed
Questions on what elements are updated in the DOM
- when elements are different => element and children updated
- when elements are the same => just element attribute is updated, children are then recursed
- When list and no key and list item is added at the start => every list item is updated
- Same question as above with keys

Question on when componentDidMount and componentDidUpdate and useEffect run in commit phase

5. 

🏆🏆🏆   

Send your answers to Carl to get your score and feedback. 


