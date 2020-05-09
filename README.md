# localstorage.js  

https://zymec.csb.app/ --> ToDo app con redux y localstorage persistence

localstorage contiene dos métodos: loadState y saveState,

> En store.js se importa loadState:

import { loadState } from "../localstorage";

y se pasa una instancia del método loadState() al create store:

const persistedState = loadState();
export default createStore(rootReducer, persistedState);
  
> donde se importe el store ( i.e.  donde se encuentre : import store from "./redux/store"; )  

importamos el saveState() método de localstorage

se suscribe el store a saveState:

store.subscribe(() => {
  saveState({
    todos: store.getState().todos
  });
});

y listo!!

instalamos node-uuid por npm para error de two children.

> en redux/actions.js 

import { v4 } from "node-uuid";

y reemplazamos: id: ++nextTodoId, por v4() 

export const addTodo = content => ({
  type: ADD_TODO,
  payload: {
    // id: ++nextTodoId,
    id: v4(),
    content
  }
});


  
