# Basic TypeScript Quiz

The following questions should take you no longer than 1 hour to answer.  

1. What would the inferred type be for the `flag` variable be in the following code?
```
const flag = false;
```

2. What would the inferred type be for the `created` variable be in the following code?
```
const created = new Date();
```

3. Create a strongly-type version of the following function
```
function multiplyBy2(numbers) {
    return numbers.map(n => n * 2);
}
```

4. What is the code for a type that represents a person containing properties for their firstname, surname and date of birth?

5. What is the code for a type that can be used for the day name of the week? i.e. the type should be able to hold "Monday" or "Tuesday" or ...

6. We have the following interface:
```
interface Dog {
    name: string;
    age: number;
}
```
How can we change the interface to make the `age` property optional?


7. What is the difference between the `height` properties in the following types?
```
interface Character1 {
    ...
    height?: number;
}

interface Character2 {
    ...
    height: number | undefined;
}
```

8. In the following `reducer` function what type will the `action` argument be narrowed to in the `"Loaded"` switch branch?
```
interface State {
    data: string[];
}
interface LoadingAction {
    name: "Loading"
}
interface LoadedAction {
    name: "Loaded"
    data: string[];
}
function reducer(state: State, action: LoadingAction | LoadedAction) {
    switch (action.name) {
        case "Loading":
            return {...state}
        case "Loaded":
             return {...state, data: action.data}
    }
}
```

9. Create a generic type called `ArrayLog` that can be used to log array items. An example use case for the type is below:
```
const arrayLog: ArrayLog<number> = (numbers: number[]) => {
    numbers.forEach(n => console.log(n));
}
```

10. What is wrong with the following code? How could this be resolved?
```
class Product {
 constructor(public name: string, public unitPrice: number) {}
}
let table = new Product();
table.name = "Table";
table.unitPrice = 700;
```

🏆🏆🏆   

Send your answers to Carl to get your score and feedback. 


