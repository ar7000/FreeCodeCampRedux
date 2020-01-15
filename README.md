Working through Redux via FreeCodeCamp resources and copying passed code to Git repo as I go through each task. Documenting below anything new I learn.

- Learned to create Redux store. Done by passing a reducer function into Redux.createStore(). Example:

```
const reducer = (state = 0){
    return state;
}

Redux.createStore(reducer)
```

Value of state in above store would be 0. Can be accessed with store.getState().

- Learned to define an action and action creator. Action defines an object, creator returns it. These actions can then be 'dispatched' to store in order to update state. Example:

```
const reducer = (state = 0, action){
    switch(action.type){
        case "increment":
        return (state + 1)
        default:
        return state
    }
}

Redux.createStore(reducer);

const myAction = {
    type:"increment"
}

const creator = () => {
    return myAction
}

store.dispatch(creator);

```

Increments state by 1.

    - Action and creator can be defined as one:
    ```
    const myAction = () => {
        return {type:"increment"}
    }
    ```

    - Action types can be defined as variables:
    ```
    const INCREMENT = "increment"
    
    const reducer = (state = 0, action){
        switch(action.type){
                case INCREMENT:
                return (state + 1)
                default:
                return state
            }
    }

    ```

    - It is best practice not to mutate state. This is not enforced by Redux so is the responsibility of the coder. Becomes a more pertinent issue when dealing with arrays or objects as state.

- Learned to register store listener with store.subscribe(). Accepts a function and executes whenever an action is implemented on the store. Example:

```
let count = 0;

let actionsCount = {
    count++;
    return count + " actions have been made against store.";
}

console.log(actionsCount); //Logs "0 actions have been made against store." to console.

store.dispatch(someAction);

store.dispatch(anotherAction);

console.log(actionsCount); //Logs "1 actions have been made against store." to console.
```