# localstorage.js  

https://zymec.csb.app/ --> ToDo app con redux y localstorage persistence

localstorage contiene dos métodos: loadState y saveState,

> En store.js se importa loadState:

import { loadState } from "../localstorage";

y se pasa una instancia del método loadState() al create store:

const persistedState = loadState();
export default createStore(rootReducer, persistedState);
  
> donde se importe el store ( import store from "./redux/store"; )  

importamos el saveState() método de localstorage

se suscribe el store a saveState:

store.subscribe(() => {
  saveState({
    todos: store.getState().todos
  });
});

y listo!!

  
