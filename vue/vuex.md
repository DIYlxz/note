#  Vuex



##  入门



```javascript
export default createStore({
  state: {
    loginState: true,
  },
  mutations: {
    setLoginState(state) {
      state.loginState = false;
      console.log(state.loginState);
    }
  },
  actions: {
  },
  modules: {
  }
})


//xxx.vue
this.$store.commit("setLoginState");
```



##  mutations



```
// mutation-types.js
export const SOME_MUTATION = 'SOME_MUTATION'
```

```javascript
import { createStore } from 'vuex'
import { SOME_MUTATION } from './mutation-types'

const store = createStore({
  state: { ... },
  mutations: {
    // we can use the ES2015 computed property name feature
    // to use a constant as the function name
    [SOME_MUTATION] (state) {
      // mutate state
    }
  }
})
```

```javascript
  methods: {
    ...mapMutations(["SOME_MUTATION"]),
    loginOrRegister() {
      this.SOME_MUTATION();
    }
  },
```



## action

action可以通过store.dispatch方法触发，返回一个promise



##  modules

命名模块内的方法等会根据命名而更改，具有更高封闭性



##  问题总结

vuex访问子模块state为undefind

```javascript
  computed: {
    ...mapState({
      loginState: state => state.login.loginState,
    }),
  },
```



vuex中的辅助函数mapMutations访问子模块

...mapMutations("模块名", ["模块Mutations方法名字"]),

```javascript
...mapMutations("login", ["setLoginState"]),
```

